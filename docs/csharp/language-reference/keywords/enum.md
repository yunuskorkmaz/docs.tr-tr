---
title: enum anahtar sözcüğü C# -başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: e33877d2a5e79866bbef12cd9fec5cb11b044240
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433861"
---
# <a name="enum-c-reference"></a>enum (C# Başvurusu)

`enum` Anahtar sözcüğü, Numaralandırıcı listesi olarak adlandırılan bir adlandırılmış sabitler kümesinden oluşan ayrı bir tür olan sabit listesini bildirmek için kullanılır.

Genellikle, ad alanındaki tüm sınıfların eşit kolaylık olmadan erişebilmesi için doğrudan bir ad alanı içinde bir numaralandırma tanımlamanız en iyisidir. Ancak, bir numaralandırma bir sınıf veya yapı içinde de iç içe olabilir.

Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahiptir ve art arda her bir Numaralandırıcı değeri 1 artırılır. Örneğin, aşağıdaki `Sat` numaralandırmada,,, vb. `Sun` olur. `Mon` `0` `1` `2`

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Numaralandırıcılar, aşağıdaki örnekte gösterildiği gibi varsayılan değerleri geçersiz kılmak için başlatıcıları kullanabilir.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Bu numaralandırmada, öğelerin sırası `1` `0`yerine başlangıç olarak zorlanır. Ancak, 0 değeri olan bir sabit kullanılması önerilir. Daha fazla bilgi için bkz. [numaralandırma türleri](../../programming-guide/enumeration-types.md).

Her numaralandırma türünün bir temel türü vardır ve bu her türlü [integral sayısal tür](../builtin-types/integral-numeric-types.md)olabilir. [Char](char.md) türü bir sabit listesinin temel alınan türü olamaz. Enumeration öğelerinin temel alınan varsayılan türü [int](../builtin-types/integral-numeric-types.md)'tir. [Byte](../builtin-types/integral-numeric-types.md)gibi başka bir integral türünün bir sabit listesini bildirmek için, aşağıdaki örnekte gösterildiği gibi, tanımlayıcıdan sonra türün ardından bir iki nokta üst üste kullanın.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Sabit listesi türünün değişkenine, temel alınan türün aralığında herhangi bir değer atanabilir; değerler, adlandırılmış sabitler ile sınırlı değildir.

Varsayılan değeri `enum E` , ifadesi `(E)0`tarafından üretilen değerdir.

> [!NOTE]
> Numaralandırıcı, adında boşluk içeremez.

Temel alınan tür, her Numaralandırıcı için ne kadar depolama ayrılacağını belirtir. Ancak, `enum` türden bir integral türüne dönüştürmek için açık bir dönüştürme gerekir. Örneğin, aşağıdaki ifade, ' den `Sun` `enum` ' a dönüştürmek `int`için bir cast kullanarak, numaralandırıcıyı [int](../builtin-types/integral-numeric-types.md) türünde bir değişkene atar.

```csharp
int x = (int)Day.Sun;
```

Bit düzeyinde <xref:System.FlagsAttribute?displayProperty=nameWithType> `OR` işlemle birleştirilebilecek öğeleri içeren bir sabit listesi için uyguladığınızda, özniteliği bazı araçlarla kullanıldığında öğesinin `enum` davranışını etkiler. <xref:System.Console> Sınıf yöntemleri ve ifade değerlendiricisi gibi araçları kullandığınızda bu değişiklikleri fark edebilirsiniz. (Bkz. üçüncü örnek.)

## <a name="robust-programming"></a>Güçlü programlama

Her türlü Sabitte olduğu gibi, bir numaralandırmanın tek tek değerlerine yapılan tüm başvurular, derleme zamanında sayısal değişmez değerlere dönüştürülür. Bu, [sabitler](../../programming-guide/classes-and-structs/constants.md)bölümünde açıklandığı gibi olası sürüm oluşturma sorunları oluşturabilir.

Yeni Numaralandırmaların yeni sürümlerine ek değerler atama veya yeni sürümde enum üyelerinin değerlerini değiştirme, bağımlı kaynak kodu sorunlarına neden olabilir. Numaralandırma değerleri genellikle [Switch](switch.md) deyimlerinde kullanılır. `enum` Türe ek öğeler eklendiyse, switch ifadesinin varsayılan bölümü beklenmedik şekilde seçilebilir.

Diğer geliştiriciler kodunuzu kullanıyorsa, herhangi bir `enum` türe yeni öğe eklenirse kodun nasıl tepki vermesi hakkında yönergeler sağlamalısınız.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir sabit listesi `Day`bildirilmiştir. İki Numaralandırıcı açıkça tam sayıya dönüştürülür ve tamsayı değişkenlerine atanır.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, üyeleri türünde `enum` `long`olan bir öğesini bildirmek için temel tür seçeneği kullanılır. Numaralandırmanın `long`temel alınan türü olsa da, sabit listesi üyelerinin bir tür dönüştürme kullanılarak açıkça türe `long` dönüştürülmesi gerekir.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir <xref:System.FlagsAttribute?displayProperty=nameWithType> `enum` bildirimde özniteliğin kullanımını ve etkisini gösterir.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Açıklamalar

' I kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:

`5`

`5`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [Sabit Listesi Türleri](../../programming-guide/enumeration-types.md)
- [C# Anahtar Sözcükleri](index.md)
- [Integral türleri](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)
- [Sabit Listesi adlandırma kuralları](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
