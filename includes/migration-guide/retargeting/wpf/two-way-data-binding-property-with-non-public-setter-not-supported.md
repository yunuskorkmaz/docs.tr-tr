---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616128"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>Ortak olmayan bir ayarlayıcıya sahip bir özelliğe iki yönlü veri bağlama desteklenmez

#### <a name="details"></a>Ayrıntılar

Ortak bir ayarlayıcı olmadan bir özelliğe veri bağlama girişimi hiçbir şekilde desteklenmeyen bir senaryoya sahip değildir. .NET Framework 4.5.1 başlayarak, bu senaryo bir oluşturur <xref:System.InvalidOperationException?displayProperty=fullName> . Bu yeni özel durumun yalnızca, özellikle .NET Framework 4.5.1 hedefleyen uygulamalar için oluşturulur. Bir uygulama .NET Framework 4,5 ' i hedefliyorsa, çağrıya izin verilir. Uygulama belirli bir .NET Framework sürümünü hedeflemez, bağlama tek yönlü olarak kabul edilir.

#### <a name="suggestion"></a>Öneri

Uygulama tek yönlü bağlama kullanacak şekilde veya özelliğin ayarlayıcısı genel olarak kullanıma sunulmalıdır. Alternatif olarak, 4,5 .NET Framework hedeflemek uygulamanın eski davranışı sergilemesine neden olur.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.5.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
