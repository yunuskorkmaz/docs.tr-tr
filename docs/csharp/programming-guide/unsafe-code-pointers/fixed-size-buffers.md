---
title: Sabit boyutlu arabellekler- C# Programlama Kılavuzu
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 9005c425badc5a4ed74e6af3447e563daf61229e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627805"
---
# <a name="fixed-size-buffers-c-programming-guide"></a>Sabit Boyutlu Arabellekler (C# Programlama Kılavuzu)

İçinde C#, bir veri yapısında sabit boyutlu bir diziye sahip bir arabellek oluşturmak için [fixed](../../language-reference/keywords/fixed-statement.md) ifadesini kullanabilirsiniz. Sabit boyutlu arabellekler, diğer dillerdeki veya platformlardaki veri kaynaklarıyla birlikte bulunan Yöntemler yazdığınızda faydalıdır. Sabit dizi, normal yapı üyeleri için izin verilen herhangi bir özniteliği veya değiştiricilerini alabilir. Tek kısıtlama, dizi türünün `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`veya `double`olması gerekir.

```csharp
private fixed char name[30];
```

## <a name="remarks"></a>Açıklamalar

Güvenli kodda, dizi içeren C# bir struct dizi öğelerini içermez. Bunun yerine, yapı öğelerine bir başvuru içerir. [Güvenli olmayan](../../language-reference/keywords/unsafe.md) bir kod bloğunda kullanıldığında bir [yapıda](../../language-reference/builtin-types/struct.md) sabit boyutlu bir dizi ekleyebilirsiniz.

Aşağıdaki `struct` boyutu 8 bayttır. `pathName` dizi bir başvurudur:

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

`struct`, güvenli olmayan kodda gömülü bir dizi içerebilir. Aşağıdaki örnekte, `fixedBuffer` dizisinin sabit bir boyutu vardır. İlk öğe için bir işaretçi oluşturmak üzere bir `fixed` ifadesini kullanın. Bu işaretçi aracılığıyla dizinin öğelerine erişirsiniz. `fixed` ifade `fixedBuffer` örneği alanını bellekte belirli bir konuma sabitsabitler.

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

128 öğesi `char` dizi boyutu 256 bayttır. Sabit boyutlu [char](../../language-reference/builtin-types/char.md) arabellekleri, kodlamadan bağımsız olarak her zaman karakter başına iki bayt alır. Bu, karakter arabellekleri API yöntemlerine veya `CharSet = CharSet.Auto` ya da `CharSet = CharSet.Ansi`yapılar halinde Sıralansa bile geçerlidir. Daha fazla bilgi için bkz. <xref:System.Runtime.InteropServices.CharSet>.

Yukarıdaki örnekte, 7,3 ile C# başlayarak kullanılabilir olan sabitleme olmadan `fixed` alanlarına erişim gösterilmektedir.

Diğer bir yaygın sabit boyutlu dizi [bool](../../language-reference/builtin-types/bool.md) dizidir. Bir `bool` dizisindeki öğeler her zaman boyuttaki bir bayttır. `bool` diziler, bit dizileri veya arabellekleri oluşturmak için uygun değildir.

> [!NOTE]
> [Stackalloc](../../language-reference/operators/stackalloc.md)kullanılarak oluşturulan bellek dışında, C# derleyici ve ortak DIL çalışma zamanı (CLR) herhangi bir güvenlik arabelleği taşma denetimi gerçekleştirmez. Tüm güvenli olmayan kodlarda olduğu gibi dikkatli olun.

Güvenli olmayan arabellekler aşağıdaki yollarla normal dizilerden farklıdır:

- Güvenli olmayan arabellekleri yalnızca güvenli olmayan bir bağlamda kullanabilirsiniz.
- Güvenli olmayan arabellekler her zaman vektörlerdir veya tek boyutlu dizilerdir.
- Dizi bildirimi, `char id[8]`gibi bir sayı içermelidir. `char id[]`kullanamazsınız.
- Güvenli olmayan arabellekler yalnızca güvenli olmayan bağlamdaki yapıların örnek alanları olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli Olmayan Kod ve İşaretçiler](index.md)
- [fixed Deyimi](../../language-reference/keywords/fixed-statement.md)
- [Birlikte çalışabilirlik](../interop/index.md)
