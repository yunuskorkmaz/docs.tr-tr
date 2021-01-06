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
# <a name="configure-a-proxy-server-when-using-the-azure-sdk-for-net"></a>.NET için Azure SDK kullanırken bir proxy sunucu yapılandırma

Kuruluşunuz internet kaynaklarına erişmek için bir proxy sunucusu kullanılmasını gerektiriyorsa, .NET için Azure SDK 'sını kullanmak üzere proxy sunucu bilgilerini içeren bir ortam değişkeni ayarlamanız gerekecektir.  

## <a name="configuration-using-environment-variables"></a>Ortam değişkenlerini kullanan yapılandırma

Proxy sunucunuz HTTP veya HTTPS kullanıyorsa bağlı olarak, ortam değişkenini ya da `HTTP_PROXY` `HTTPS_PROXY` sırasıyla ayarlarsınız. Proxy sunucusu URL 'SI, `http[s]://[username:password@]<ip_address_or_hostname>:<port>/` `username:password` birleşiminin isteğe bağlı olduğu biçimde olur. Proxy sunucunuzun IP adresini veya ana bilgisayar adını, bağlantı noktasını ve kimlik bilgilerini almak için ağ yöneticinize başvurun.

Aşağıdaki örneklerde, komut kabuğu (Windows) ve Bash (Linux/Mac) ortamlarında uygun ortam değişkenlerinin nasıl ayarlanacağı gösterilmektedir.  Uygun ortam değişkeninin ayarlanması, .NET için Azure SDK 'sının çalışma zamanında proxy sunucusunu kullanmasına neden olur.

### <a name="cmd"></a>[cmd](#tab/cmd)

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

### <a name="bash"></a>[Bash](#tab/bash)

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
