---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700872"
---
### <a name="include-specific-api-surfaces"></a><span data-ttu-id="ec5d7-101">Belirli API yüzeylerini dahil et</span><span class="sxs-lookup"><span data-stu-id="ec5d7-101">Include specific API surfaces</span></span>

<span data-ttu-id="ec5d7-102">Kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec5d7-102">You can configure which parts of your codebase to run this rule on, based on their accessibility.</span></span> <span data-ttu-id="ec5d7-103">Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir *. editorconfig* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="ec5d7-103">For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
