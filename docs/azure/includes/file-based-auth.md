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
<span data-ttu-id="f88ee-101">'li bir `azureauth.json`metin dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f88ee-101">Create a text file named `azureauth.json`.</span></span> <span data-ttu-id="f88ee-102">Hizmet ilkesini oluşturduğunuz dan JSON çıktısını yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="f88ee-102">Paste the JSON output from when you created the service principal.</span></span>

<span data-ttu-id="f88ee-103">Bu dosyayı sisteminizde güvenli ve kodunuzun okuyabileceği bir konuma kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f88ee-103">Save this file in a secure location on your system where your code can read it.</span></span> <span data-ttu-id="f88ee-104">Örneğin, dosyaya tam yol `AZURE_AUTH_LOCATION` ile adlandırılan bir ortam değişkeni ayarlamak için PowerShell'i kullanın:</span><span class="sxs-lookup"><span data-stu-id="f88ee-104">Use PowerShell to set an environment variable named `AZURE_AUTH_LOCATION` with the full path to the file, for example:</span></span>

```powershell
[Environment]::SetEnvironmentVariable("AZURE_AUTH_LOCATION", "C:\src\azureauth.json", "User")
```
