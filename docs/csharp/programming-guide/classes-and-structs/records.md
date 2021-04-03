---
title: Kayıtlar-C# Programlama Kılavuzu
description: Kayıt türleri ve bunların nasıl oluşturulacağı hakkında bilgi edinin
ms.date: 02/26/2021
helpviewer_keywords:
- records [C#]
- C# language, records
ms.openlocfilehash: 99370e398d5e607def58334b33ae20aa59e21962
ms.sourcegitcommit: 872ca41d1c26f39d0aef57cc365d09503bac780d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2021
ms.locfileid: "106288036"
---
# <a name="records-c-programming-guide"></a>Kayıtlar (C# Programlama Kılavuzu)

[Kayıt](../../language-reference/builtin-types/record.md) , veri modelleriyle çalışma için özel sözdizimi ve davranış sağlayan bir [sınıftır](../../language-reference/keywords/class.md) . Sınıflar hakkında daha fazla bilgi için bkz. [sınıflar (C# Programlama Kılavuzu)](classes.md).

## <a name="when-to-use-records"></a>Kayıtlar ne zaman kullanılır?

Aşağıdaki senaryolarda bir sınıfın yerine bir kayıt kullanmayı düşünün:

* Nesnelerin sabit olduğu bir başvuru türü tanımlamak istiyorsunuz.
* [Değer eşitliğine](../statements-expressions-operators/equality-comparisons.md#value-equality)bağlı bir veri modeli tanımlamak istiyorsunuz.

### <a name="immutability"></a>Değiştirilemezlik

Sabit bir tür, bir nesnenin örneği oluşturulduktan sonra herhangi bir özellik veya alan değerini değiştirmenize engel olur. Bir tür iş parçacığı açısından güvenli olması gerektiğinde veya karma koda bir karma tabloya bağlı olduğunuzda, dengesde bilirlik yararlı olabilir. Kayıtlar, sabit türler oluşturmak ve bunlarla çalışmak için kısa bir sözdizimi sağlar.

Tüm veri senaryoları için imlebilirlik kullanılabilirliği uygun değildir. Örneğin, [Entity Framework Core](/ef/core/), sabit varlık türleriyle güncellemeyi desteklemez.

### <a name="value-equality"></a>Değer eşitlik

Kayıtlar için, değer eşitliği, türlerin eşleşmesi ve tüm özellik ve alan değerleri eşleşiyorsa bir kayıt türünün iki değişkeninin eşit olduğu anlamına gelir. Sınıflar gibi diğer başvuru türleri için eşitlik, [başvuru eşitlik](../statements-expressions-operators/equality-comparisons.md#reference-equality)anlamına gelir. Diğer bir deyişle, bir sınıf türünün iki değişkeni aynı nesneye başvurduklarında eşittir. İki kayıt örneğinin eşitlik düzeyini belirten Yöntemler ve işleçler değer eşitlik kullanır.

Tüm veri modelleri değer eşitliği ile iyi çalışmaz. Örneğin, [Entity Framework Core](/ef/core/) kavramsal bir varlık olan varlık türünün yalnızca bir örneğini kullandığından emin olmak için başvuru eşitliğine bağlıdır. Bu nedenle, kayıt türleri Entity Framework Core varlık türleri olarak kullanım için uygun değildir.

## <a name="how-records-differ-from-classes"></a>Kayıtların sınıflardan farkı

Sınıfları [bildiren](classes.md#declaring-classes) ve [örnekleyen](classes.md#creating-objects) sözdizimi, kayıtlarla birlikte kullanılabilir. Anahtar sözcüğünün anahtar sözcüğünü yerine koyun `record` `class` . Benzer şekilde, devralma ilişkilerini ifade etmek için de aynı söz dizimi kayıtlar tarafından desteklenir. Kayıtlar sınıflardan aşağıdaki yollarla farklılık gösterir:

* Sabit özelliklerle bir tür oluşturmak ve başlatmak için [konumsal parametreleri](../../language-reference/builtin-types/record.md#positional-syntax-for-property-definition) kullanabilirsiniz.
* Sınıflarda başvuru eşitlik veya eşitsizlik belirten Yöntemler ve işleçler ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> ve gibi `==` ), kayıtlardaki [değer eşitlik veya eşitsizlik](../../language-reference/builtin-types/record.md#value-equality) olduğunu gösterir.
* Seçili özelliklerde yeni değerleri olan bir sabit nesnenin kopyasını oluşturmak için bir [ `with` ifade](../../language-reference/builtin-types/record.md#nondestructive-mutation) kullanabilirsiniz.
* Bir kaydın `ToString` yöntemi, bir nesnenin tür adını ve tüm ortak özelliklerinin adlarını ve değerlerini gösteren biçimli bir dize oluşturur.
* Bir kayıt, [başka bir kayıttan devralınabilir](../../language-reference/builtin-types/record.md#inheritance). Bir kayıt bir sınıftan devralınabilir ve bir sınıf bir kayıttan devralınabilir.

## <a name="examples"></a>Örnekler

Aşağıdaki örnek, bir kaydı bildirmek ve oluşturmak için Konumsal parametreleri kullanan bir ortak kayıt tanımlar. Daha sonra tür adı ve özellik değerlerini yazdırır:

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="InstantiatePositional":::

Aşağıdaki örnek kayıtlardaki değer eşitliğini gösterir:

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="Equality":::

Aşağıdaki örnek, `with` değişmez bir nesneyi kopyalamak ve özelliklerden birini değiştirmek için bir ifadenin kullanımını gösterir:

:::code language="csharp" source="../../language-reference/builtin-types/snippets/shared/RecordType.cs" id="WithExpressions":::

Daha fazla bilgi için bkz. [kayıtlar (C# Başvurusu)](../../language-reference/builtin-types/record.md).
  
## <a name="c-language-specification"></a>C# Dil Belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sınıflar (C# Programlama Kılavuzu)](classes.md)
- [Kayıtlar (C# Başvurusu)](../../language-reference/builtin-types/record.md)
- [C# Programlama Kılavuzu](../index.md)
- [Nesne odaklı programlama](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [Çok biçimlilik](polymorphism.md)
- [Tanımlayıcı adları](../inside-a-program/identifier-names.md)
- [Üyeler](members.md)
- [Yöntemler](methods.md)
- [Oluşturucular](constructors.md)
- [Sonlandırıcılar](destructors.md)
- [Nesneler](objects.md)
