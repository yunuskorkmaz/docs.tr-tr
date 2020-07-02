---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617274"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Foreach Yineleyici değişkeni artık yineleme içinde kapsamlandırılır, bu nedenle kapatma yakalama semantiği farklıdır (C# 5 ' te)

#### <a name="details"></a>Ayrıntılar

C# 5 ' ten itibaren (Visual Studio 2012), `foreach` Yineleyici değişkenleri yineleme içinde kapsamlandırılır. Bu, kodun daha önce kendi kapanışına dahil edilmez olan değişkenlere bağlı olması durumunda kesintiler oluşmasına neden olabilir `foreach` . Bu değişikliğin belirtisi, bir temsilciye geçirilen bir yineleyici değişkeninin, temsilcinin çağrıldığı zaman değeri yerine temsilci oluşturulduğu sırada sahip olduğu değer olarak değerlendirilmesidir.

#### <a name="suggestion"></a>Öneri

İdeal olarak, kodun yeni derleyici davranışını beklediği için güncelleştirilmeleri gerekir. Eski semantikler gerekliyse, yineleyici değişkeni, açıkça döngünün kapsamının dışına yerleştirilmiş olan ayrı bir değişkenle değiştirilebilir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4,5         |
| Tür    | Yeniden Hedefleme |
