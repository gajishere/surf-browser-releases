# Third-party notices

Surf Browser includes the following third-party software. Each component keeps its own license.

## Dark Reader 4.9.133

- Upstream: https://github.com/darkreader/darkreader
- License: MIT
- Used for: the optional **Force dark mode** setting. The unmodified page-script bundle is embedded in Surf and is injected into pages only while that setting is on.

### License text

    MIT License

    Copyright (c) 2026 Dark Reader Ltd.

    All rights reserved.

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.

## uBlock Origin Lite 2026.1026.1812

- Upstream: https://github.com/uBlockOrigin/uBOL-home (release `2026.1026.1812`, asset `uBOLite_2026.1026.1812.edge.zip`, SHA-256 `12a3be6e4c24c932677208bd0b8fff0689676ef2b0db689cfe794b02e0ed69fc`)
- Source code: https://github.com/gorhill/uBlock (the `platform/mv3` part builds uBlock Origin Lite)
- Copyright: Raymond Hill and contributors
- License: GNU General Public License version 3 (GPLv3)
- Used for: the **Block ads** setting. The release zip is embedded in Surf unmodified, unpacked to `%LOCALAPPDATA%\SurfBrowser\Extensions\uBOLite\<version>\` and loaded as a browser extension. It is a separate program shipped alongside Surf (an aggregate); Surf does not link to it or change it. While **Block ads** is on, Surf replaces it with newer unmodified releases from the upstream page above, after checking each one against its published SHA-256.

### License text

The full GPLv3 text ships with the extension as `LICENSE.txt` (inside the zip, and in the unpacked folder above). It is also at https://www.gnu.org/licenses/gpl-3.0.txt.

## Microsoft.Web.WebView2 1.0.4314.35

- Upstream: https://www.nuget.org/packages/Microsoft.Web.WebView2
- License: BSD-3-Clause-style license from Microsoft Corporation
- Used for: hosting the Microsoft Edge WebView2 Runtime, which draws every page. The SDK's managed libraries and its loader are included in Surf. The WebView2 Runtime itself is installed separately on Windows and is not distributed with Surf.

### License text

    Copyright (C) Microsoft Corporation. All rights reserved.

    Redistribution and use in source and binary forms, with or without
    modification, are permitted provided that the following conditions are
    met:

       * Redistributions of source code must retain the above copyright
    notice, this list of conditions and the following disclaimer.
       * Redistributions in binary form must reproduce the above
    copyright notice, this list of conditions and the following disclaimer
    in the documentation and/or other materials provided with the
    distribution.
       * The name of Microsoft Corporation, or the names of its contributors
    may not be used to endorse or promote products derived from this
    software without specific prior written permission.

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
    "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
    LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
    A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
    OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
    SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
    LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
    DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
    THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
    (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
    OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## .NET 10

- Upstream: https://github.com/dotnet/runtime and https://github.com/dotnet/wpf
- License: MIT
- Used for: the portable download includes the .NET 10 runtime and the Windows Desktop runtime (WPF). The small download uses the copy installed on your PC. The .NET runtime's own third-party notices are at https://github.com/dotnet/runtime/blob/main/THIRD-PARTY-NOTICES.TXT

### License text

    The MIT License (MIT)

    Copyright (c) .NET Foundation and Contributors

    All rights reserved.

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.
