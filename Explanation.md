## What was the bug?

The Client.request() method allowed oauth2_token to be either an OAuth2Token object or a dictionary. However, the refresh logic only handled missing tokens or expired OAuth2Token instances.

When the token was a dictionary, the client neither refreshed the token nor attached the Authorization header.

## Why did it happen?

The condition used isinstance(self.oauth2_token, OAuth2Token) inside the refresh check. If the token was a dictionary, this condition evaluated to false, preventing token refresh.

## Why does your fix solve it?

The fix ensures the token is refreshed whenever it is not a valid OAuth2Token instance. This guarantees that the Authorization header is always created from a valid token.

## Edge case not covered

The tests do not verify behavior when the token expires exactly at the current timestamp boundary.
