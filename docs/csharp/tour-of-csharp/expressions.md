---
title: C#İfadeleri - Turu C# dil
description: ifadeleri ve işlenenleri işleçleri olan yapı taşları C# dil
ms.date: 04/25/2019
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 2553730d495942730c53d3646f35e80759a4d168
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609327"
---
# <a name="expressions"></a>İfadeler

*İfadeleri* oluşturulan *işlenenler* ve *işleçleri*. İfade işleçleri işlenenlere uygulamak için hangi işlemleri gösterir. İşleçler örnekler `+`, `-`, `*`, `/`, ve `new`. Değişmez değerler, alanlar, yerel değişkenleri ve ifadeleri işlenenler örnekleridir.

Bir ifade birden çok işleç içeren *öncelik* işleçleri tek tek işleçler değerlendirilme sırası denetler. Örneğin, ifade `x + y * z` değerlendirmesinde `x + (y * z)` çünkü `*` işleci daha yüksek önceliğe sahip `+` işleci.

Bir işlenen aynı önceliğe sahip iki işleç arasında gerçekleştiğinde *ilişkilendirilebilirliği* operatörleri işlemleri gerçekleştirilir sırasını denetler:

* Atama işleçleri hariç tüm ikili işleçler şunlardır *ilişkilendirilebilir*, yani işlemler soldan sağa doğru gerçekleştirilir. Örneğin, `x + y + z` değerlendirmesinde `(x + y) + z`.
* Atama işleçleri ve koşullu işleç (`?:`) olan *sağla ilişkilendirilebilir*, sağdan sola işlemler gerçekleştirilir anlamına gelir. Örneğin, `x = y = z` değerlendirmesinde `x = (y = z)`.

Öncelik ve ilişkisellik parantez kullanılarak denetlenebilir. Örneğin, `x + y * z` ilk çarpar `y` tarafından `z` ve ardından sonuca ekler `x`, ancak `(x + y) * z` ilk ekler `x` ve `y` ve sonucu çarpan `z`.

Çoğu işleçleri olabilir [ *aşırı*](../language-reference/operators/operator-overloading.md). İşleç aşırı yüklemesi, aşağıdakilerden birini veya her iki işlenen kullanıcı tanımlı sınıf veya yapı türü olduğu işlemlerinde belirtilmesi için kullanıcı tanımlı işleç uygulamalarına izin verir.

C#birkaç gerçekleştirmek için işleçleri sağlar [aritmetik](../language-reference/operators/arithmetic-operators.md), [mantıksal](../language-reference/operators/boolean-logical-operators.md), [bit düzeyinde and -shift ile](../language-reference/operators/bitwise-and-shift-operators.md) işlemleri ve [eşitlik](../language-reference/operators/equality-operators.md) ve [sipariş](../language-reference/operators/comparison-operators.md) karşılaştırmalar.

Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](../language-reference/operators/index.md).

> [!div class="step-by-step"]
> [Önceki](types-and-variables.md)
> [İleri](statements.md)
