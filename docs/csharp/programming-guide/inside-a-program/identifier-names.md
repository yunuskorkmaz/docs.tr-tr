---
title: Tanımlayıcı adları
description: C# Programlama dilinde geçerli tanımlayıcı adları için kuralları öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: f8a27ddae0437ed037b59f76d60dc7e420ddc2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589345"
---
# <a name="identifier-names"></a>Tanımlayıcı adları

**Tanımlayıcı** , bir türe atadığınız addır (sınıf, arabirim, yapı, temsilci veya Enum), üye, değişken veya ad alanı. Geçerli tanımlayıcılar şu kurallara uymalıdır:

- Tanımlayıcılar bir harfle başlamalı veya `_`.
- Tanımlayıcılar Unicode harf karakterleri, ondalık basamak karakterleri, Unicode bağlantı karakterleri, Unicode birleştiren karakterler veya Unicode biçimlendirme karakterlerini içerebilir. Unicode kategorileri hakkında daha fazla bilgi için bkz. [Unicode kategori veritabanı](https://www.unicode.org/reports/tr44/).
Tanımlayıcıda `@` öneki kullanarak, anahtar C# sözcüklerle eşleşen tanımlayıcılar bildirebilirsiniz. `@` Tanımlayıcı adının bir parçası değil. Örneğin, `@if` adlı `if`bir tanımlayıcı bildirir. Bu tam [tanımlayıcılar](../../language-reference/tokens/verbatim.md) öncelikle diğer dillerde belirtilen tanımlayıcılarla birlikte çalışabilirlik içindir.

Geçerli tanımlayıcıların tamamen tanımı için, [ C# dil belirtiminde tanımlayıcılar konusuna](../../../../_csharplang/spec/lexical-structure.md#identifiers)bakın.

## <a name="naming-conventions"></a>Adlandırma kuralları

Kuralların yanı sıra, .NET API 'Lerinde kullanılan bir dizi tanımlayıcı [adlandırma kuralı](../../../standard/design-guidelines/naming-guidelines.md) vardır. Kural gereği, C# programlar tür `PascalCase` adları, ad alanları ve tüm genel Üyeler için kullanır. Ayrıca, aşağıdaki kurallar ortaktır:

- Arabirim adları sermaye `I`ile başlar.
- Öznitelik türleri kelimeyle `Attribute`biter.
- Sabit listesi türleri, bayraklar için tekil bir ad ve bayraklar için bir çoğul ad kullanır.
- Tanımlayıcılar iki ardışık `_` karakter içermemelidir. Bu adlar derleyicinin ürettiği tanımlayıcılar için ayrılmıştır.

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# Programı İçinde](./index.md)
- [C#Başvurunun](../../language-reference/index.md)
- [Sınıflar](../classes-and-structs/classes.md)
- [Yapılar](../classes-and-structs/structs.md)
- [Ad Alanları](../namespaces/index.md)
- [Arabirimler](../interfaces/index.md)
- [Temsilciler](../delegates/index.md)
