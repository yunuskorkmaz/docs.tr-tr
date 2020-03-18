---
title: C# İfadeler - C# dilinde bir tur
description: İfadeler, operandlar ve işleçler C# dilinin yapı taşlarıdır
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159162"
---
# <a name="expressions"></a>İfadeler

*İfadeler* *operands* ve *işleçler*inşa edilmiştir. Bir ifadenin işleçleri operandlara hangi işlemleri uygulayacaklarını gösterir. İşleçlerin `+` `-`örnekleri `*` `/`arasında `new`, , , , ve . Operands örnekleri edebi, alanlar, yerel değişkenler ve ifadeler içerir.

Bir ifade birden çok işleç içeriyorsa, işleçlerin *önceliği* tek tek işleçlerin değerlendirildiği sırayı denetler. Örneğin, `*` işleç `+` işleci `x + (y * z)` işleç daha yüksek önceliğe sahip olduğu için ifade `x + y * z` olarak değerlendirilir.

Aynı önceliğe sahip iki işleç arasında bir operand oluştuğunda, işleçlerin *bağlantısı* işlemlerin gerçekleştirilme sırasını kontrol eder:

* Atama ve null-coalescing işleçleri dışında, tüm ikili işleçler *sol-bağşdırıcıdır,* yani işlemler soldan sağa doğru gerçekleştirilir. Örneğin, `x + y + z` olarak `(x + y) + z`değerlendirilir.
* Atama `??` işleçleri, null-coalescing ve `??=` operatörler `?:` ve koşullu işleç *sağ-associative*, yani işlemler sağdan sola yapılır. Örneğin, `x = y = z` olarak `x = (y = z)`değerlendirilir.

Öncelik ve bağlanabilirlik parantez kullanılarak kontrol edilebilir. Örneğin, `x + y * z` önce sonucu `y` `z` çarpar, sonra `x`sonucu `(x + y) * z` ekler, `x` `y` ancak önce ekler ve `z`sonra sonucu .

Çoğu operatör [*aşırı yüklenebilir.*](../language-reference/operators/operator-overloading.md) İşletici aşırı yükleme, operandların bir veya her ikisinin kullanıcı tarafından tanımlanan bir sınıf veya yapı türüne ait olduğu işlemler için kullanıcı tarafından tanımlanan operatör uygulamalarının belirtilmesine izin verir.

C# [aritmetik,](../language-reference/operators/arithmetic-operators.md) [mantıksal,](../language-reference/operators/boolean-logical-operators.md) [bitwise ve shift](../language-reference/operators/bitwise-and-shift-operators.md) işlemleri ve [eşitlik](../language-reference/operators/equality-operators.md) ve [sipariş](../language-reference/operators/comparison-operators.md) karşılaştırmaları gerçekleştirmek için işleçleri bir dizi sağlar.

Öncelik düzeyine göre sıralanan C# işleçlerinin tam listesi için [Bkz. C# işleçleri.](../language-reference/operators/index.md)

> [!div class="step-by-step"]
> [Önceki](types-and-variables.md)
> [Sonraki](statements.md)
