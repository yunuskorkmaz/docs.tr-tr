---
title: sizeof C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: e77076d022051cdf7d5545cc5204b3c74959d0ad
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433878"
---
# <a name="sizeof-c-reference"></a>sizeof (C# Başvurusu)

[Yönetilmeyen bir türün](../builtin-types/unmanaged-types.md)boyutunu bayt olarak almak için kullanılır.

Yönetilmeyen türler şunlardır:

- Aşağıdaki tabloda listelenen basit türler:

   |İfade|Sabit değer|
   |----------------|--------------------|
   |`sizeof(sbyte)`|1\.|
   |`sizeof(byte)`|1\.|
   |`sizeof(short)`|2|
   |`sizeof(ushort)`|2|
   |`sizeof(int)`|4|
   |`sizeof(uint)`|4|
   |`sizeof(long)`|8|
   |`sizeof(ulong)`|8|
   |`sizeof(char)`|2 (Unicode)|
   |`sizeof(float)`|4|
   |`sizeof(double)`|8|
   |`sizeof(decimal)`|16|
   |`sizeof(bool)`|1\.|

- Sabit listesi türleri.

- İşaretçi türleri.

- Başvuru türleri veya oluşturulmuş türler olan herhangi bir örnek alanı veya otomatik uygulanmış örnek özellikleri içermeyen Kullanıcı tanımlı yapılar.

Aşağıdaki örnek, öğesinin `int`boyutunun nasıl alınacağını gösterir:

```csharp
// Constant value 4:
int intSize = sizeof(int);
```

## <a name="remarks"></a>Açıklamalar

Sürüm 2,0 C#' den başlayarak, basit `sizeof` veya Enum türlerine uygulamak artık kodun [güvenli olmayan](unsafe.md) bir bağlamda derlenmesine gerek yoktur.

`sizeof` İşleç aşırı yüklenemez. `sizeof` İşleci tarafından döndürülen değerler türündedir `int`. Önceki tabloda, belirli basit türleri işlenen olarak bulunan ifadeler için `sizeof` değiştirilen sabit değerler gösterilir.

Yapılar dahil tüm diğer türler için, `sizeof` işleci yalnızca güvenli olmayan kod bloklarda kullanılabilir. Yöntemini kullanabilseniz de, bu yöntemin döndürdüğü değer her zaman tarafından `sizeof`döndürülen değerle aynı değildir. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>tür sıralandıktan sonra boyutu döndürür, ancak `sizeof` herhangi bir doldurma dahil olmak üzere ortak dil çalışma zamanı tarafından ayrılan boyutu döndürür.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsOperator#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#11)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [enum](enum.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
- [Yapılar](../../programming-guide/classes-and-structs/structs.md)
- [Sabitler](../../programming-guide/classes-and-structs/constants.md)
