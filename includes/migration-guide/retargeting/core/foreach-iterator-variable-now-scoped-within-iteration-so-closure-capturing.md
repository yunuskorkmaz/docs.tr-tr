---
ms.openlocfilehash: 1805c26f1eff46719f30de8a14ca6d35f01948a6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234855"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Kapanış yakalama semantiği (C# 5'te) farklı olduğundan Foreach yineleyici değişkeni artık yineleme içinde kapsamı

|   |   |
|---|---|
|Ayrıntılar|C# 5 (Visual Studio 2012),'ten itibaren <code>foreach</code> yineleyici değişkenleri yineleme içinde kapsanır. Kod içinde dahil edilmemesi için değişkenleri daha önce bağlı, bunu sonu neden olabilir <code>foreach</code>kullanıcının thisanahtar. Bu değişikliğin bir temsilciye iletilen bir yineleyici değişkeni temsilci çağrıldığı zaman sahip değer yerine temsilci zaman sahip değer oluşturulur olarak kabul edilir belirtisidir.|
|Öneri|İdeal olarak, kodu yeni derleyici davranışı beklediğiniz şekilde güncelleştirilmesi gerekir. Eski semantiği gerekiyorsa, yineleyici değişkeni döngü kapsamı dışında açıkça yerleştirilir, ayrı bir değişken ile değiştirilebilir.|
|Kapsam|Ana|
|Sürüm|4,5|
|Tür|Yeniden Hedefleme|
