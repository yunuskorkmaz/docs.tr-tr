---
title: Arkadaş derlemeleri
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: bf1cb28a6e3096a42aae1c777f6d2d6f9cc16c49
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774339"
---
# <a name="friend-assemblies"></a>Arkadaş derlemeleri

*Arkadaş derlemesi* , başka bir derlemenin [iç](../../csharp/language-reference/keywords/internal.md) (C#) veya [arkadaş](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) türlerine ve üyelerine erişebilen bir derlemedir. Bir derlemeyi arkadaş derleme olarak belirlerseniz, diğer derlemeler tarafından erişilebilmesi için artık türleri ve üyeleri ortak olarak işaretlemeniz gerekmez. Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:

- Birim testi sırasında, test kodu ayrı bir derlemede çalışırken, ancak test edilen derlemede `internal` olarak işaretlenmiş C# veya Visual Basic içinde `Friend` olarak işaretlenen üyelere erişim gerektirir.

- Bir sınıf kitaplığı geliştirirken ve kitaplığa eklemeler ayrı derlemelerde yer alır, ancak Visual Basic içinde C# veya `Friend` `internal` olarak işaretlenen mevcut derlemelerde üyelere erişim gerektirir.

## <a name="remarks"></a>Açıklamalar

Belirli bir derleme için bir veya daha fazla Friend derlemesini belirlemek üzere <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini kullanabilirsiniz. Aşağıdaki örnek, *derleme a* 'daki <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğini kullanır ve bir Friend derlemesi olarak bir derlemeyi *AssemblyB* olarak belirtir. Bu, *bütünleştirilmiş kod '* de `internal` olarak işaretlenen C# veya Visual Basic ' de `Friend` olarak işaretlenen tüm tür ve üyelere derleme *AssemblyB* erişimi sağlar.

> [!NOTE]
> *Derleme A*gibi başka bir derlemenin iç türlerine veya iç üyelerine erişecek *AssemblyB* gibi bir derlemeyi derlerken,-Out kullanarak çıkış dosyasının ( *. exe* veya *. dll*) adını açıkça belirtmeniz gerekirderleyici seçeneği. Bu gereklidir çünkü derleyici, dış başvurulara bağlama sırasında oluşturmakta olduğu derlemenin adını henüz üretmemiştir. Daha fazla bilgi için bkz. [-OutC#()](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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
Imports System
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

Yalnızca arkadaş olarak açıkça belirttiğiniz derlemeler, `internal` (C#) veya `Friend` (Visual Basic) türlerine ve üyelerine erişebilir. Örneğin, *AssemblyB* , *derleme a* 'Nın arkadaşınız ve *derleme c* , *AssemblyB*'ye başvuruyorsa, *derleme c* ,C# *a derlemesinde*`internal` () veya `Friend` (Visual Basic) türlerine erişim sahibi olmaz.

Derleyici, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliğine geçirilen arkadaş derleme adının bazı temel doğrulamasını gerçekleştirir. Eğer *derlemesi bir* Friend derlemesi olarak *AssemblyB* bildirirse, doğrulama kuralları aşağıdaki gibidir:

- *Derleme A* tanımlayıcı olarak adlandırılmışsa, *AssemblyB* de tanımlayıcı adlandırılmış olmalıdır. Özniteliğine geçirilen arkadaş derleme adı, *AssemblyB*imzalamak için kullanılan tanımlayıcı ad anahtarının derleme adından ve ortak anahtarından oluşmalıdır.

     @No__t_0 özniteliğine geçirilen arkadaş derleme adı *AssemblyB*'nin tanımlayıcı adı olamaz. Bütünleştirilmiş kod sürümü, kültür, mimari veya ortak anahtar belirtecini eklemeyin.

- *Derleme A* tanımlayıcı adlandırılmış değilse, arkadaş derleme adı yalnızca derleme adından oluşmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: imzasız arkadaş derlemeleri oluşturma](create-unsigned-friend.md).

- *AssemblyB* tanımlayıcı adlandırılmış ise, proje ayarını veya komut satırı `/keyfile` derleyici seçeneğini kullanarak *AssemblyB* için tanımlayıcı ad anahtarını belirtmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md).

 @No__t_0 sınıfı, aşağıdaki farklılıklarla türleri paylaşma özelliği de sağlar:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> tek bir tür için geçerlidir, ancak bir arkadaş derleme tüm derleme için geçerlidir.

- *Bir derlemede* *AssemblyB*ile paylaşmak istediğiniz yüzlerce tür varsa, tümüne <xref:System.Security.Permissions.StrongNameIdentityPermission> eklemeniz gerekir. Bir arkadaş derleme kullanıyorsanız, yalnızca bir defa arkadaş ilişki bildirmeniz gerekir.

- @No__t_0 kullanıyorsanız, paylaşmak istediğiniz türlerin ortak olarak bildirilmesini gerekir. Bir arkadaş derleme kullanıyorsanız, paylaşılan türler `internal` (C#) veya `Friend` (Visual Basic) olarak belirtilir.

Bir modül dosyasından ( *. netmodule* uzantılı bir dosya) birC#derlemenin `internal` () veya `Friend` (Visual Basic) türlerine ve yöntemlerine erişme hakkında daha fazla bilgi için, bkz: [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) veya [-moduleassemblyname ( Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma](create-unsigned-friend.md)
- [Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [C#Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
