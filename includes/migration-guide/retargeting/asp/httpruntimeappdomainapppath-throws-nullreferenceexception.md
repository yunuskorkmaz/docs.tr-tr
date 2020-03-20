---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859137"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>httpRuntime.AppDomainAppPath NullReferenceException atar

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'de, null karakterleri <code>T:System.NullReferenceException</code> içeren bir <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> değer alırken çalışma zamanı bir değer atar. .NET Framework 4.6.1 ve önceki sürümlerinde, çalışma <code>T:System.ArgumentNullException</code>zamanı .|
|Öneri|Bu değişikliğe yanıt vermek için aşağıdakilerden birini yapabilirsiniz:<ul><li><code>T:System.NullReferenceException</code> .NET Framework 4.6.2 üzerinde çalışan uygulama varsa ele alın.</li><li>Önceki davranışı geri yükleyen ve bir <code>T:System.ArgumentNullException</code>.</li></ul>|
|Kapsam|Edge|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
