---
title: Sabit boyutlu arabellekler-C# Programlama Kılavuzu
description: Sabit boyutlu arabellekler hakkında bilgi edinin. Sabit boyutlu arabellekler, diğer dillerdeki veri kaynaklarıyla birlikte bulunan yöntemleri yazmak için kullanılır.
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 1d4f5068121cdc98976954f2d99f4ac020c3b2a8
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381248"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)

C# ' de, bir veri yapısında sabit boyutlu bir diziye sahip bir arabellek oluşturmak için [fixed](../../language-reference/keywords/fixed-statement.md) ifadesini kullanabilirsiniz. Sabit boyutlu arabellekler, diğer dillerdeki veya platformlardaki veri kaynaklarıyla birlikte bulunan Yöntemler yazdığınızda faydalıdır. Sabit dizi, normal yapı üyeleri için izin verilen herhangi bir özniteliği veya değiştiricilerini alabilir. Tek kısıtlama, dizi türünün,,,,,,,, `bool` `byte` `char` `short` `int` `long` `sbyte` `ushort` `uint` , `ulong` ,, `float` veya `double` olması olabilir.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Açıklamalar

Güvenli kodda, bir dizi içeren bir C# yapısı dizi öğelerini içermez. Bunun yerine, yapı öğelerine bir başvuru içerir. [Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıda](../../language-reference/builtin-types/struct.md) sabit boyutlu bir dizi ekleyebilirsiniz.

Aşağıdaki boyut, `struct` başvuru olduğundan dizideki öğelerin sayısına bağlı değildir `pathName` :

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

`struct`, Güvenli olmayan kodda gömülü bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizisinin sabit bir boyutu vardır. `fixed`İlk öğe için bir işaretçi oluşturmak üzere bir ifade kullanırsınız. Bu işaretçi aracılığıyla dizinin öğelerine erişirsiniz. `fixed`İfade, `fixedBuffer` örnek alanını bellekte belirli bir konuma sabitsabitler.

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

128 öğe `char` dizisinin boyutu 256 bayttır. Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır. Bu, karakter arabellekleri API yöntemlerine veya ya da yapıları için Sıralansa bile geçerlidir `CharSet = CharSet.Auto` `CharSet = CharSet.Ansi` . Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Yukarıdaki örnekte `fixed` , C# 7,3 ile başlayarak kullanılabilir olan sabitleme olmadan alanlara erişme gösterilmektedir.

Diğer bir yaygın sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizidir. Bir `bool` dizideki öğeler her zaman boyuttaki bir bayttır. `bool`diziler, bit dizileri veya arabellekleri oluşturmak için uygun değildir.

Sabit boyutlu arabellekler ile derlenir ve <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> Bu, ortak dil çalışma zamanına (CLR) bir türün, bulunabilecek bir yönetilmeyen dizi içerdiğini söyler. Bu, CLR 'de arabellek taşması algılama özelliklerini otomatik olarak sağlayan [stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan belleğe benzerdir. Önceki örnekte, bir sabit boyut arabelleğinin bir içinde nasıl yer aldığı gösterilmektedir `unsafe struct` .

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

Için C# tarafından oluşturulan derleyici `Buffer` , aşağıdaki gibidir:

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

Sabit boyutlu arabellekler aşağıdaki yollarla normal dizilerden farklıdır:

- Yalnızca [güvenli olmayan](../../language-reference/keywords/unsafe.md) bir bağlamda kullanılabilir.
- Yalnızca yapıların örnek alanları olabilir.
- Bunlar her zaman vektörleridir veya tek boyutlu dizilerdir.
- Bildirimin uzunluğu içermesi gerekir, örneğin `fixed char id[8]` . Kullanamazsınız `fixed char id[]` .

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli olmayan kod ve Işaretçiler](index.md)
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)
- [Birlikte çalışabilirlik](../interop/index.md)
