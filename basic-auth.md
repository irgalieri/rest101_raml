The **basic** authentication scheme is based on the model that the user
agent must authenticate itself with a user-ID and a password for each
realm. The realm value should be considered an opaque string which
can only be compared for equality with other realms on that server.
The server will authorize the request only if it can validate the
user-ID and password for the protection space of the Request-URI.
There are no optional authentication parameters.

Upon receipt of an unauthorized request for a URI within the
protection space, the server should respond with a challenge like the
following:

    WWW-Authenticate: Basic realm="SNMP Gateway API"

where "SNMP Gateway API" is the string assigned by the server to identify
the protection space of the Request-URI.

To receive authorization, the client sends the user-ID and password,
separated by a single colon (":") character, within a base64
encoded string in the credentials.

* **basic-credentials** = "Basic" SP basic-cookie
* **basic-cookie**      = base64 encoding of userid-password, except not limited to 76 char/line
* **userid-password**   = [ token ] ":" *TEXT

If the user agent wishes to send the user-ID "Aladdin" and password
"open sesame", it would use the following header field:

    Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==

The basic authentication scheme is a non-secure method of filtering
unauthorized access to resources on an HTTP server. It is based on
the assumption that the connection between the client and the server
can be regarded as a trusted carrier. As this is not generally true
on an open network, the basic authentication scheme should be used
accordingly. In spite of this, clients should implement the scheme in
order to communicate with servers that use it.