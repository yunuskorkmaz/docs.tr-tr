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
Adlı `azureauth.json`bir metin dosyası oluşturun. Hizmet sorumlusunu oluştururken JSON çıkışını yapıştırın.

Bu dosyayı sisteminizde güvenli ve kodunuzun okuyabileceği bir konuma kaydedin. Dosyanın tam yolu ile adlı `AZURE_AUTH_LOCATION` bir ortam değişkenini ayarlamak için PowerShell kullanın, örneğin:

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
