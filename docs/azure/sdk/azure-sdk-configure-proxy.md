---
title: .NET için Azure SDK kullanırken bir proxy sunucu yapılandırma
description: .NET için Azure SDK için bir proxy tanımlamak üzere HTTP [S] _PROXY ortam değişkenlerini kullanın
ms.date: 12/10/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.openlocfilehash: 64d525f8a6c277a5ac383dfded828f2fd3cfd744
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701184"
---
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a><span data-ttu-id="83ac8-103">.NET için Azure SDK kullanırken bir proxy sunucu yapılandırma</span><span class="sxs-lookup"><span data-stu-id="83ac8-103">Configure a proxy server when using the Azure SDK for .NET</span></span>

<span data-ttu-id="83ac8-104">Kuruluşunuz internet kaynaklarına erişmek için bir proxy sunucusu kullanılmasını gerektiriyorsa, .NET için Azure SDK 'sını kullanmak üzere proxy sunucu bilgilerini içeren bir ortam değişkeni ayarlamanız gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="83ac8-104">If your organization requires the use of a proxy server to access internet resources, you will need to set an environment variable with the proxy server information to use the Azure SDK for .NET.</span></span>  

## <a name="configuration-using-environment-variables"></a><span data-ttu-id="83ac8-105">Ortam değişkenlerini kullanan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="83ac8-105">Configuration using environment variables</span></span>

<span data-ttu-id="83ac8-106">Proxy sunucunuz HTTP veya HTTPS kullanıyorsa bağlı olarak, ortam değişkenini ya da `HTTP_PROXY` `HTTPS_PROXY` sırasıyla ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="83ac8-106">Depending on if your proxy server uses HTTP or HTTPS, you will set either the environment variable `HTTP_PROXY` or `HTTPS_PROXY` respectively.</span></span> <span data-ttu-id="83ac8-107">Proxy sunucusu URL 'SI, `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` `username:password` birleşiminin isteğe bağlı olduğu biçimde olur.</span><span class="sxs-lookup"><span data-stu-id="83ac8-107">The proxy server URL has the form `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` where the `username:password` combination is optional.</span></span> <span data-ttu-id="83ac8-108">Proxy sunucunuzun IP adresini veya ana bilgisayar adını, bağlantı noktasını ve kimlik bilgilerini almak için ağ yöneticinize başvurun.</span><span class="sxs-lookup"><span data-stu-id="83ac8-108">To get the IP address or hostname, port and credentials for your proxy server, consult your network administrator.</span></span>

<span data-ttu-id="83ac8-109">Aşağıdaki örneklerde, komut kabuğu (Windows) ve Bash (Linux/Mac) ortamlarında uygun ortam değişkenlerinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="83ac8-109">The following examples show how to set the appropriate environment variables in command shell (Windows) and bash (Linux/Mac) environments.</span></span>  <span data-ttu-id="83ac8-110">Uygun ortam değişkeninin ayarlanması, .NET için Azure SDK 'sının çalışma zamanında proxy sunucusunu kullanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="83ac8-110">Setting the appropriate environment variable will then cause the Azure SDK for .NET to use the proxy server at runtime.</span></span>

### <a name="cmd"></a>[<span data-ttu-id="83ac8-111">cmd</span><span class="sxs-lookup"><span data-stu-id="83ac8-111">cmd</span></span>](#tab/cmd)

```cmd
rem Non-authenticated HTTP server:
set HTTP_PROXY=http://10.10.1.10:1180

rem Authenticated HTTP server:
set HTTP_PROXY=http://username:password@10.10.1.10:1180

rem Non-authenticated HTTPS server:
set HTTPS_PROXY=http://10.10.1.10:1180

rem Authenticated HTTPS server:
set HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

### <a name="bash"></a>[<span data-ttu-id="83ac8-112">Bash</span><span class="sxs-lookup"><span data-stu-id="83ac8-112">bash</span></span>](#tab/bash)

```bash
# Non-authenticated HTTP server:
HTTP_PROXY=http://10.10.1.10:1180

# Authenticated HTTP server:
HTTP_PROXY=http://username:password@10.10.1.10:1180

# Non-authenticated HTTPS server:
HTTPS_PROXY=http://10.10.1.10:1180

# Authenticated HTTPS server:
HTTPS_PROXY=http://username:password@10.10.1.10:1180
```

---
