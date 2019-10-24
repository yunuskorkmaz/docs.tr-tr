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
ms.openlocfilehash: 417f02ce9e8ee88edeb2a4dab88111cae39a8a4b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771860"
---
# <a name="enum-c-reference"></a>enum (C# Başvurusu)

`enum` anahtar sözcüğü, Numaralandırıcı listesi olarak adlandırılan bir adlandırılmış sabitler kümesinden oluşan ayrı bir tür olan bir sabit listesi bildirmek için kullanılır.

Genellikle, ad alanındaki tüm sınıfların eşit kolaylık olmadan erişebilmesi için doğrudan bir ad alanı içinde bir numaralandırma tanımlamanız en iyisidir. Ancak, bir numaralandırma bir sınıf veya yapı içinde de iç içe olabilir.

Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahiptir ve art arda her bir Numaralandırıcı değeri 1 artırılır. Örneğin, aşağıdaki numaralandırmada `Sat` `0`, `Sun` `1`, `Mon` `2`ve benzeri.

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

Numaralandırıcılar, aşağıdaki örnekte gösterildiği gibi varsayılan değerleri geçersiz kılmak için başlatıcıları kullanabilir.

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Bu numaralandırmada, öğelerin sırası `0`yerine `1` başlatmaya zorlanır. Ancak, 0 değeri olan bir sabit kullanılması önerilir. Daha fazla bilgi için bkz. [numaralandırma türleri](../../programming-guide/enumeration-types.md).

Her numaralandırma türünün bir temel türü vardır ve bu her türlü [integral sayısal tür](../builtin-types/integral-numeric-types.md)olabilir. [Char](char.md) türü bir sabit listesinin temel alınan türü olamaz. Enumeration öğelerinin temel alınan varsayılan türü [int](../builtin-types/integral-numeric-types.md)'tir. [Byte](../builtin-types/integral-numeric-types.md)gibi başka bir integral türünün bir sabit listesini bildirmek için, aşağıdaki örnekte gösterildiği gibi, tanımlayıcıdan sonra türün ardından bir iki nokta üst üste kullanın.

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

Sabit listesi türünün değişkenine, temel alınan türün aralığında herhangi bir değer atanabilir; değerler, adlandırılmış sabitler ile sınırlı değildir.

`enum E` varsayılan değeri, ifade `(E)0`tarafından üretilen değerdir.

> [!NOTE]
> Numaralandırıcı, adında boşluk içeremez.

Temel alınan tür, her Numaralandırıcı için ne kadar depolama ayrılacağını belirtir. Ancak, `enum` türünden integral türüne dönüştürmek için açık bir dönüştürme gerekir. Örneğin, aşağıdaki ifade, `enum` `int`'e dönüştürmek için bir cast kullanarak, Numaralandırıcı `Sun` [int](../builtin-types/integral-numeric-types.md) türünde bir değişkene atar.

```csharp
int x = (int)Day.Sun;
```

Bit düzeyinde `OR` işlemle birleştirilebilecek öğeleri içeren bir numaralandırmaya <xref:System.FlagsAttribute?displayProperty=nameWithType> uyguladığınızda, öznitelik bazı araçlarla kullanıldığında `enum` davranışını etkiler. <xref:System.Console> sınıfı yöntemleri ve Ifade Değerlendiricisi gibi araçları kullandığınızda bu değişiklikleri fark edebilirsiniz. (Bkz. üçüncü örnek.)

## <a name="robust-programming"></a>Güçlü programlama

Her türlü Sabitte olduğu gibi, bir numaralandırmanın tek tek değerlerine yapılan tüm başvurular, derleme zamanında sayısal değişmez değerlere dönüştürülür. Bu, [sabitler](../../programming-guide/classes-and-structs/constants.md)bölümünde açıklandığı gibi olası sürüm oluşturma sorunları oluşturabilir.

Yeni Numaralandırmaların yeni sürümlerine ek değerler atama veya yeni sürümde enum üyelerinin değerlerini değiştirme, bağımlı kaynak kodu sorunlarına neden olabilir. Numaralandırma değerleri genellikle [Switch](switch.md) deyimlerinde kullanılır. `enum` türüne ek öğeler eklendiyse, switch ifadesinin varsayılan bölümü beklenmedik şekilde seçilebilir.

Diğer geliştiriciler kodunuzu kullanıyorsa, yeni öğeler `enum` türlerine eklenirse kodun nasıl tepki vermesi hakkında yönergeler sağlamalısınız.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `Day`bir sabit listesi bildirilmiştir. İki Numaralandırıcı açıkça tam sayıya dönüştürülür ve tamsayı değişkenlerine atanır.

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a>Örnek

Aşağıdaki örnekte, üyeleri `long`türünde olan bir `enum` bildirmek için temel tür seçeneği kullanılır. Sabit listesinin temel alınan türü `long`olsa da, numaralandırma üyelerinin bir cast kullanılarak `long` türüne açıkça dönüştürülmesi gerekir.

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, `enum` bildiriminde <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliğinin kullanımını ve etkisini gösterir.

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a>Açıklamalar

`Flags`kaldırırsanız, örnek aşağıdaki değerleri görüntüler:

`5`

`5`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [Sabit Listesi Türleri](../../programming-guide/enumeration-types.md)
- [C# Anahtar Sözcükleri](index.md)
- [Integral türleri](../builtin-types/integral-numeric-types.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Sabit Listesi adlandırma kuralları](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
