---
title: Arkadaş derlemeleri
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348174"
---
# <a name="friend-assemblies"></a>Arkadaş derlemeleri

*Arkadaş derlemesi,* başka bir derlemenin [dahili](../../csharp/language-reference/keywords/internal.md) (C#) veya [Arkadaş](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) türlerine ve üyelerine erişebilen bir derlemedir. Bir derlemeyi arkadaş derlemesi olarak tanımlarsanız, diğer derlemeler tarafından erişilebilmesi için türleri ve üyeleri artık herkese açık olarak işaretlemeniz gerekir. Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:

- Birim testi sırasında, test kodu ayrı bir derlemede çalıştığında, ancak c# `internal` veya `Friend` Visual Basic olarak işaretlenmiş olarak sınanan derlemedeki üyelere erişim gerekir.

- Bir sınıf kitaplığı geliştirirken ve kitaplık eklemeleri ayrı derlemelerde bulunur, ancak C# veya `internal` `Friend` Visual Basic olarak işaretlenmiş varolan derlemelerde üyelere erişim gerekir.

## <a name="remarks"></a>Açıklamalar

Belirli bir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> derleme için bir veya daha fazla arkadaş derlemesi tanımlamak için özniteliği kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> A Derlemesi'ndeki özniteliği kullanır ve *Derleme B'yi* arkadaş derlemesi olarak belirtir. *Assembly A* Bu, *AssemblyB'nin* A Derlemesi'nde C# `internal` veya `Friend` Visual Basic olarak işaretlenmiş tüm tür ve üyelere erişim sağlar. *Assembly A*

> [!NOTE]
> *AssemblyB* *gibi, Assembly A*gibi başka bir derlemenin iç türlerine veya iç üyelerine erişecek bir derleme derlediğinizde, **-out** derleyici seçeneğini kullanarak çıktı dosyasının *(.exe* veya *.dll)* adını açıkça belirtmeniz gerekir. Derleyici, dış başvurulara bağlandığı anda oluşturduğu derlemenin adını henüz oluşturmadığından bu gereklidir. Daha fazla bilgi için bkz: [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) [veya-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

Yalnızca açıkça arkadaş olarak belirttiğiniz derlemeler (C#) veya `internal` `Friend` (Visual Basic) türlerine ve üyelerine erişebilir. Örneğin, *AssemblyB Assembly* *A'nın* arkadaşıysa ve *C Derlemesi* *AssemblyB'ye*başvuruyorsa, *Derleme C'nin* A `internal` *Derlemesi'ndeki*(C#) veya `Friend` (Visual Basic) türlerine erişimi yoktur.

Derleyici öznitelik geçirilen <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> arkadaş derleme adının bazı temel doğrulama gerçekleştirir. *A Derlemesi* *AssemblyB'yi* arkadaş derlemesi olarak bildirirse, doğrulama kuralları aşağıdaki gibidir:

- *A Derlemesi* güçlü adlandırılmışsa, *AssemblyB* de güçlü adlandırılmış olmalıdır. Öznitelik geçirilen arkadaş derleme adı derleme adı ve *AssemblyB*imzalamak için kullanılan güçlü ad anahtarının ortak anahtarı ndan oluşmalıdır.

     Özniteliğe <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> geçirilen arkadaş derleme adı *AssemblyB'nin*güçlü adı olamaz. Derleme sürümünü, kültürü, mimariyi veya ortak anahtar belirteci eklemeyin.

- *A Derlemesi* güçlü adlandırılmış değilse, arkadaş derleme adı yalnızca derleme adından oluşmalıdır. Daha fazla bilgi için [bkz: İmzalanmamış arkadaş derlemeleri oluşturun.](create-unsigned-friend.md)

- *AssemblyB* güçlü adlandırılmışsa, proje ayarını veya komut satırı `/keyfile` derleyicisi seçeneğini kullanarak *AssemblyB* için güçlü ad anahtarını belirtmeniz gerekir. Daha fazla bilgi için [bkz: İmzalı arkadaş derlemeleri oluşturun.](create-signed-friend.md)

 Sınıf <xref:System.Security.Permissions.StrongNameIdentityPermission> ayrıca, aşağıdaki farklılıklarla türleri paylaşma olanağı da sağlar:

- <xref:System.Security.Permissions.StrongNameIdentityPermission>tek bir tür için geçerlidir, bir arkadaş derlemesi ise tüm derleme için geçerlidir.

- *Assembly A'da* *AssemblyB*ile paylaşmak istediğiniz yüzlerce tür varsa, <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne eklemeniz gerekir. Bir arkadaş derlemesi kullanıyorsanız, arkadaş ilişkisini yalnızca bir kez bildirmeniz gerekir.

- <xref:System.Security.Permissions.StrongNameIdentityPermission>Kullanıyorsanız, paylaşmak istediğiniz türlerin herkese açık olarak bildirilmesi gerekir. Bir arkadaş derlemesi kullanıyorsanız, paylaşılan `internal` türler (C#) veya `Friend` (Visual Basic) olarak bildirilir.

Bir derlemenin `internal` (C#) veya (Visual `Friend` Basic) türlerine ve yöntemlerine bir modül dosyasından *(.netmodule* uzantılı bir [dosya)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) nasıl erişilir hakkında bilgi için [bkz.](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Nasıl yapilir: İmzalanmamış arkadaş derlemeleri oluşturma](create-unsigned-friend.md)
- [Nasıl yapılsın: İmzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
