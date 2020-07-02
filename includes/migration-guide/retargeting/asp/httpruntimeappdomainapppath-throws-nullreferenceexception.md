---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617553"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime. AppDomainAppPath bir NullReferenceException oluşturur

#### <a name="details"></a>Ayrıntılar

.NET Framework 4.6.2, çalışma zamanı null karakterler içeren bir `T:System.NullReferenceException` değer alınırken bir oluşturur `P:System.Web.HttpRuntime.AppDomainAppPath` . .NET Framework 4.6.1 ve önceki sürümlerde, çalışma zamanı bir oluşturur `T:System.ArgumentNullException` .

#### <a name="suggestion"></a>Öneri

Bu değişikliğe yanıt vermek için şu iki seçenekten birini yapabilirsiniz:

- `T:System.NullReferenceException`Uygulama .NET Framework 4.6.2 üzerinde çalışıyorsa işleyin.
- Önceki davranışı geri yükleyen ve bir oluşturan .NET Framework 4,7 ' a yükseltin `T:System.ArgumentNullException` .

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4.6.2       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
