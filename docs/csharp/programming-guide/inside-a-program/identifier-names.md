---
title: Tanımlayıcı adları
description: C# Programlama dilinde geçerli tanımlayıcı adları için kuralları öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673374"
---
# <a name="identifier-names"></a>Tanımlayıcı adları

**Tanımlayıcı** , bir türe atadığınız addır (sınıf, arabirim, yapı, temsilci veya Enum), üye, değişken veya ad alanı. Geçerli tanımlayıcılar şu kurallara uymalıdır:

- Tanımlayıcılar bir harfle başlamalı veya `_`.
- Tanımlayıcılar Unicode harf karakterleri, ondalık basamak karakterleri, Unicode bağlantı karakterleri, Unicode birleştiren karakterler veya Unicode biçimlendirme karakterlerini içerebilir. Unicode kategorileri hakkında daha fazla bilgi için bkz. [Unicode kategori veritabanı](https://www.unicode.org/reports/tr44/).
Tanımlayıcıda `@` önekini kullanarak, C# anahtar sözcüklerle eşleşen tanımlayıcılar bildirebilirsiniz. `@` tanımlayıcı adının bir parçası değil. Örneğin, `@if` `if`adlı bir tanımlayıcı bildirir. Bu tam [tanımlayıcılar](../../language-reference/tokens/verbatim.md) öncelikle diğer dillerde belirtilen tanımlayıcılarla birlikte çalışabilirlik içindir.

Geçerli tanımlayıcıların tamamen tanımı için, [ C# dil belirtiminde tanımlayıcılar konusuna](../../../../_csharplang/spec/lexical-structure.md#identifiers)bakın.

## <a name="naming-conventions"></a>Adlandırma kuralları

Kuralların yanı sıra, .NET API 'Lerinde kullanılan bir dizi tanımlayıcı [adlandırma kuralı](../../../standard/design-guidelines/naming-guidelines.md) vardır. Kural gereği, C# programlar tür adları, ad alanları ve tüm genel üyeler için `PascalCase` kullanır. Ayrıca, aşağıdaki kurallar ortaktır:

- Arabirim adları, büyük bir `I`başlar.
- Öznitelik türleri `Attribute`sözcüğüyle biter.
- Sabit listesi türleri, bayraklar için tekil bir ad ve bayraklar için bir çoğul ad kullanır.
- Tanımlayıcılar iki ardışık `_` karakter içermemelidir. Bu adlar derleyicinin ürettiği tanımlayıcılar için ayrılmıştır.

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# Programı İçinde](./index.md)
- [C#Başvurunun](../../language-reference/index.md)
- [Sınıflar](../classes-and-structs/classes.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [Ad Alanları](../namespaces/index.md)
- [Arabirimler](../interfaces/index.md)
- [Temsilciler](../delegates/index.md)
