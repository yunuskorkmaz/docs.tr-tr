---
title: Sabit Boyut Arabellekleri - C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 6770497b23212f1786b4f4a620ed2b650079c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157032"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)

C#'da, veri yapısında sabit boyut dizilimi olan bir arabellek oluşturmak için [sabit](../../language-reference/keywords/fixed-statement.md) ifadeyi kullanabilirsiniz. Sabit boyut arabellekleri, diğer dillerden veya platformlardan gelen veri kaynaklarıyla kesişen yöntemler yazarken yararlıdır. Sabit dizi, normal yapı üyeleri için izin verilen öznitelikleri veya değiştiriciler alabilir. Tek kısıtlama, dizi türünün `bool`, `byte` `char`, `short` `int`, `long` `sbyte` `ushort` `uint` `ulong`, , `float`, `double`, , , veya .

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Açıklamalar

Güvenli kodda, dizi içeren bir C# struct dizi öğelerini içermez. Bunun yerine, yapı öğeleri için bir başvuru içerir. [Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıya](../../language-reference/builtin-types/struct.md) sabit boyut dizisini katıştırabilirsiniz.

Aşağıdakilerin `struct` boyutu dizideki öğe sayısına bağlı değildir, `pathName` çünkü bir başvurudur:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

A, `struct` güvenli olmayan kodda gömülü bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizi sabit bir boyuta sahiptir. İlk öğeye işaretçi oluşturmak için bir `fixed` deyim kullanırsınız. Bu işaretçi aracılığıyla dizinin öğelerine erişin. İfade, `fixed` `fixedBuffer` örnek alanını bellekte belirli bir konuma sabitler.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 öğe `char` dizisinin boyutu 256 bayttır. Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır. Bu, char arabellekleri API yöntemlerine veya structs'a marshaled olduğunda bile `CharSet = CharSet.Auto` geçerlidir. `CharSet = CharSet.Ansi` Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Önceki örnek, C# `fixed` 7.3'ten başlayarak kullanılabilen sabitleme olmadan alanlara erişmelerini gösterir.

Başka bir ortak sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizisidir. Dizideki `bool` öğeler her zaman bir bayt boyutundadır. `bool`diziler bit dizileri veya arabellekoluşturmak için uygun değildir.

> [!NOTE]
> [Stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan bellek dışında, C# derleyicisi ve ortak dil çalışma süresi (CLR) herhangi bir güvenlik arabellek taşma denetimleri gerçekleştirmez. Tüm güvenli olmayan kodda olduğu gibi dikkatli olun.

Güvenli olmayan arabellekler aşağıdaki şekillerde normal dizilerden farklıdır:

- Yalnızca güvenli olmayan bir bağlamda güvenli olmayan arabellekler kullanabilirsiniz.
- Güvenli olmayan arabellekler her zaman vektörveya tek boyutlu dizilerdir.
- Dizinin bildirimi, `char id[8]`'. Bunu kullanamazsınız. `char id[]`
- Güvenli olmayan arabellekler yalnızca güvenli olmayan bir bağlamda yapı alanları olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)
- [Birlikte çalışabilirlik](../interop/index.md)
