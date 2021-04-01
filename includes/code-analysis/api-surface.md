---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "97700872"
---
### <a name="include-specific-api-surfaces"></a>Belirli API yüzeylerini dahil et

Kod tabanınızın hangi bölümlerinin bu kuralı çalıştırmak için erişilebilirliğini temel alarak yapılandırabilirsiniz. Örneğin, kuralın yalnızca genel olmayan API yüzeyine karşı çalışması gerektiğini belirtmek için, aşağıdaki anahtar-değer çiftini projenizdeki bir *. editorconfig* dosyasına ekleyin:

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
