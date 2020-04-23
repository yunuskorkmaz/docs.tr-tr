---
ms.service: multiple
ms.date: 9/20/2018
ms.topic: include
ms.openlocfilehash: bfa7bcefff45bc325d7bba3aa2b9b3a8f0d439fa
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2020
ms.locfileid: "82071936"
---
'li bir `azureauth.json`metin dosyası oluşturun. Hizmet ilkesini oluşturduğunuz dan JSON çıktısını yapıştırın.

Bu dosyayı sisteminizde güvenli ve kodunuzun okuyabileceği bir konuma kaydedin. Örneğin, dosyaya tam yol `AZURE_AUTH_LOCATION` ile adlandırılan bir ortam değişkeni ayarlamak için PowerShell'i kullanın:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
