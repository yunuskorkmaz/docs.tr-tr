---
title: Sabit boyutlu arabellekler-C# Programlama Kılavuzu
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140553"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)

C# ' de, bir veri yapısında sabit boyutlu bir diziye sahip bir arabellek oluşturmak için [fixed](../../language-reference/keywords/fixed-statement.md) ifadesini kullanabilirsiniz. Sabit boyutlu arabellekler, diğer dillerdeki veya platformlardaki veri kaynaklarıyla birlikte bulunan Yöntemler yazdığınızda faydalıdır. Sabit dizi, normal yapı üyeleri için izin verilen herhangi bir özniteliği veya değiştiricilerini alabilir. Tek kısıtlama `bool`, dizi türünün, `byte` `char` `short` `int` `long` `sbyte` `uint` `ulong` `float` `double`,,,,,,,,,, veya olması olabilir. `ushort`

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Açıklamalar

Güvenli kodda, bir dizi içeren bir C# yapısı dizi öğelerini içermez. Bunun yerine, yapı öğelerine bir başvuru içerir. [Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıda](../../language-reference/builtin-types/struct.md) sabit boyutlu bir dizi ekleyebilirsiniz.

Aşağıdaki `struct` boyut, başvuru `pathName` olduğundan dizideki öğelerin sayısına bağlı değildir:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

`struct` , Güvenli olmayan kodda gömülü bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizisinin sabit bir boyutu vardır. İlk öğe için `fixed` bir işaretçi oluşturmak üzere bir ifade kullanırsınız. Bu işaretçi aracılığıyla dizinin öğelerine erişirsiniz. `fixed` İfade, `fixedBuffer` örnek alanını bellekte belirli bir konuma sabitsabitler.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 öğe `char` dizisinin boyutu 256 bayttır. Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır. Bu, karakter arabellekleri API yöntemlerine veya `CharSet = CharSet.Auto` ya da `CharSet = CharSet.Ansi`yapıları için Sıralansa bile geçerlidir. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Yukarıdaki örnekte, C# 7,3 `fixed` ile başlayarak kullanılabilir olan sabitleme olmadan alanlara erişme gösterilmektedir.

Diğer bir yaygın sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizidir. Bir `bool` dizideki öğeler her zaman boyuttaki bir bayttır. `bool`diziler, bit dizileri veya arabellekleri oluşturmak için uygun değildir.

Sabit boyutlu arabellekler ile <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>derlenir ve bu, ortak dil çalışma zamanına (CLR) bir türün, bulunabilecek bir yönetilmeyen dizi içerdiğini söyler. Bu, CLR 'de arabellek taşması algılama özelliklerini otomatik olarak sağlayan [stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan belleğe benzerdir. Önceki örnekte, bir sabit boyut arabelleğinin bir `unsafe struct`içinde nasıl yer aldığı gösterilmektedir.

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

Için `Buffer`C# tarafından oluşturulan derleyici, aşağıdaki gibidir:

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
- Bildirimin uzunluğu içermesi gerekir, örneğin `fixed char id[8]`. Kullanamazsınız `fixed char id[]`.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)
- [Birlikte Çalışabilirlik](../interop/index.md)
