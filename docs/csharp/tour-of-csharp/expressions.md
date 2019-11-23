---
title: C#İfadeler- C# dilin turu
description: İfadeler, işlenenler ve işleçler, C# dilin yapı taşları
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4866d12118518827c1f7032ac09933927f0f3c52
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395669"
---
# <a name="expressions"></a>{1&gt;İfadeler&lt;1}

*İfadeler* , *işlenenler* ve *işleçlerden*oluşturulur. Bir ifadenin işleçleri, işlenenlerin hangi işlemleri uygulanacağını gösterir. Operatör örnekleri arasında `+`, `-`, `*`, `/`ve `new`sayılabilir. İşlenenlerin örnekleri, sabit değerleri, alanları, yerel değişkenleri ve ifadeleri içerir.

Bir ifade birden çok işleç içerdiğinde, işleçlerin *önceliği* ayrı işleçlerin değerlendirilme sırasını denetler. Örneğin, `*` işleci `+` işlecinden daha yüksek önceliğe sahip olduğu için `x + y * z` ifade `x + (y * z)` olarak değerlendirilir.

Aynı önceliğe sahip iki işleç arasında bir işlenen gerçekleştiğinde, işleçlerin *ilişkilendirilebilirliği* , işlemlerin gerçekleştirileceği sırayı denetler:

* Atama ve null birleşim işleçleri hariç olmak üzere tüm ikili işleçler *sola ilişkilendirilebilir*, yani işlemler soldan sağa yapılır. Örneğin, `x + y + z` `(x + y) + z`olarak değerlendirilir.
* Atama işleçleri, null birleştirme `??` ve `??=` işleçleri ve koşullu işleç `?:`, *doğru ilişkilendirilebilir*, yani işlemler sağdan sola yapılır. Örneğin, `x = y = z` `x = (y = z)`olarak değerlendirilir.

Öncelik ve ilişkilendirilebilirlik, parantezler kullanılarak denetlenebilir. Örneğin, `x + y * z` önce `y` `z` ile çarpar ve sonucu `x`ekler, ancak `(x + y) * z` önce `x` ve `y` ekler ve sonra sonucu `z`ile çarpar.

Çoğu işleç [*aşırı*](../language-reference/operators/operator-overloading.md)yüklenebilir. İşleç aşırı yüklemesi, Kullanıcı tanımlı operatör uygulamalarının bir veya her ikisinin de Kullanıcı tanımlı sınıf veya yapı türünde olduğu işlemler için belirtilmesine izin verir.

C#[Aritmetik](../language-reference/operators/arithmetic-operators.md), [mantıksal](../language-reference/operators/boolean-logical-operators.md), [bit düzeyinde ve vardiya](../language-reference/operators/bitwise-and-shift-operators.md) işlemleri ile [eşitlik](../language-reference/operators/equality-operators.md) ve [sıra](../language-reference/operators/comparison-operators.md) karşılaştırmaları gerçekleştirmeye yönelik bir dizi işleç sağlar.

Öncelik düzeyine göre sıralanan C# işleçlerin tüm listesi için bkz [ C# . işleçler](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Önceki](types-and-variables.md)
> [İleri](statements.md)
