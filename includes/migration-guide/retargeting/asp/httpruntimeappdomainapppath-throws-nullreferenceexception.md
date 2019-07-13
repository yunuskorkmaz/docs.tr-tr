---
ms.openlocfilehash: d6c658f306dd4792e3cb5dbdc9471043ca95a071
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859137"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>NullReferenceException HttpRuntime.AppDomainAppPath oluşturur

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2, çalışma zamanı oluşturur bir <code>T:System.NullReferenceException</code> alınırken bir <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> null karakterleri içeren bir değer. .NET Framework 4.6.1 ve önceki sürümlerinde, çalışma zamanı oluşturur bir <code>T:System.ArgumentNullException</code>.|
|Öneri|Bu değişiklik yanıt vermek için izleme birini yapabilirsiniz:<ul><li>Tanıtıcı <code>T:System.NullReferenceException</code> uygulamanız .NET Framework 4.6.2 çalışıyorsa.</li><li>Önceki davranış geri yükler ve oluşturur .NET Framework 4.7, yükseltme bir <code>T:System.ArgumentNullException</code>.</li></ul>|
|`Scope`|Kenar|
|Version|4.6.2|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

