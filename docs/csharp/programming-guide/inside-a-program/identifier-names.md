---
title: Tanımlayıcı adları
description: C# programlama dilinin geçerli tanımlayıcı adları kurallarını öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: e5ff83661c9a86273760f32a795f7de6dbc7bf1d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877889"
---
# <a name="identifier-names"></a>Tanımlayıcı adları

Bir **tanımlayıcı** atama türü (sınıf, arabirim, yapı, temsilci veya enum), üye, değişken veya ad alanı adı. Geçerli tanımlayıcıları şu kurallara uymalıdır:

- Tanımlayıcılar, bir harf ile başlamalı veya `_`.
- Tanımlayıcılar, Unicode harf karakterler, ondalık basamak karakteri, Unicode karakter bağlanma, Unicode karakter birleştirme veya Unicode karakter biçimlendirme içerebilir. Unicode kategorileri hakkında daha fazla bilgi için bkz. [Unicode kategorisi veritabanı](https://www.unicode.org/reports/tr44/).
C# anahtar sözcüklerini kullanarak eşleşen tanımlayıcıları bildirebilirsiniz `@` tanımlayıcısını öneke. `@` Tanımlayıcı adı bir parçası değil. Örneğin, `@if` bildirir adlandırılmış bir tanımlayıcı `if`. Bunlar [verbatim tanımlayıcıları](../../language-reference/tokens/verbatim.md) öncelikli olarak birlikte çalışabilirlik için diğer dillerde bildirilen tanımlayıcılarına sahip olan.

Geçerli tanımlayıcıları eksiksiz bir açıklaması için bkz. [tanımlayıcıları C# dil belirtimi konudaki](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Adlandırma kuralları

Kurallarının yanı sıra, kullanılabilen birkaç tanımlayıcısının [adlandırma kuralları](../../../standard/design-guidelines/naming-guidelines.md) .NET API'lerini kullanılır. Kural gereği, C# programları kullanım `PascalCase` tür adları ad alanları ve tüm genel üyeler için. Ayrıca, aşağıdaki kurallar ortaktır:

- Büyük harfle adları başlangıç arabirim `I`.
- Öznitelik türlerini uç sözcüğünün `Attribute`.
- Numaralandırma türleri için bayrakları olmayan bayrakları için tekil bir isim ve çoğul bir isim kullanın.
- Tanımlayıcılar, bu iki ardışık içermemelidir `_` karakter. Bu adlar, derleyicinin ürettiği tanımlayıcıları için ayrılmıştır.

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# Programı İçinde](../inside-a-program/index.md)
- [C# başvurusu](../../language-reference/index.md)
- [Sınıflar](../classes-and-structs/classes.md)
- [Yapılar](../classes-and-structs/structs.md)
- [Ad Alanları](../namespaces/index.md)
- [Arabirimler](../interfaces/index.md)
- [Temsilciler](../delegates/index.md)
