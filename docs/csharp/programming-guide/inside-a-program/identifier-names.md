---
title: Tanımlayıcı adları
description: C# programlama dilinde geçerli tanımlayıcı adlarının kurallarını öğrenin.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77673374"
---
# <a name="identifier-names"></a>Tanımlayıcı adları

**Tanımlayıcı,** bir türe (sınıf, arabirim, yapı, temsilci veya enum), üye, değişken veya ad alanına atadığınız addır. Geçerli tanımlayıcılar aşağıdaki kurallara uymalıdır:

- Tanımlayıcılar bir harfle başlamalı, ya `_`da.
- Tanımlayıcılar Unicode harf karakterleri, ondalık basamak karakterleri, Unicode bağlama karakterleri, Unicode birleştiren karakterler veya Unicode biçimlendirme karakterleri içerebilir. Unicode kategorileri hakkında daha fazla bilgi için [Unicode Kategori Veritabanı'na](https://www.unicode.org/reports/tr44/)bakın.
Tanımlayıcıdaki `@` öneki kullanarak C# anahtar kelimeleriyle eşleşen tanımlayıcıları bildirebilirsiniz. Tanımlayıcı `@` adının bir parçası değildir. Örneğin, `@if` adlı `if`bir tanımlayıcı bildirir. Bu [kelime tanımlayıcıları](../../language-reference/tokens/verbatim.md) öncelikle diğer dillerde bildirilen tanımlayıcılarla birlikte çalışabilirlik içindir.

Geçerli tanımlayıcıların tam bir tanımı için [C# Dil Belirtiminde tanımlayıcılar konusuna](../../../../_csharplang/spec/lexical-structure.md#identifiers)bakın.

## <a name="naming-conventions"></a>Adlandırma kuralları

Kurallara ek olarak, .NET API'leri boyunca kullanılan bir dizi tanımlayıcı [adlandırma kuralı](../../../standard/design-guidelines/naming-guidelines.md) vardır. C# programları, kural `PascalCase` kuralına göre tür adları, ad alanları ve tüm ortak üyeler için kullanılır. Buna ek olarak, aşağıdaki sözleşmeler yaygındır:

- Arabirim adları büyük `I`harfle başlar.
- Öznitelik türleri sözcüğüyle `Attribute`birlikte sona erer.
- Enum türleri, bayrak olmayanlar için tekil bir ad ve bayraklar için çoğul bir ad kullanır.
- Tanımlayıcılar iki ardışık `_` karakter içermemelidir. Bu adlar derleyici oluşturulan tanımlayıcılar için ayrılmıştır.

## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [C# Programı İçinde](./index.md)
- [C# Referans](../../language-reference/index.md)
- [Sınıflar](../classes-and-structs/classes.md)
- [Yapı türleri](../../language-reference/builtin-types/struct.md)
- [Ad Alanları](../namespaces/index.md)
- [Arabirimler](../interfaces/index.md)
- [Temsilciler](../delegates/index.md)
