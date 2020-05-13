---
title: Arkadaş derlemeleri
description: Arkadaş derlemesi, başka bir derlemenin iç (C#) veya arkadaş (Visual Basic) türlerine ve üyelerine erişebilen bir .NET derlemesidir.
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378928"
---
# <a name="friend-assemblies"></a>Arkadaş derlemeleri

*Arkadaş derlemesi* , başka bir derlemenin [iç](../../csharp/language-reference/keywords/internal.md) (C#) veya [arkadaş](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) türlerine ve üyelerine erişebilen bir derlemedir. Bir derlemeyi arkadaş derleme olarak belirlerseniz, diğer derlemeler tarafından erişilebilmesi için artık türleri ve üyeleri ortak olarak işaretlemeniz gerekmez. Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:

- Birim testi sırasında, test kodu ayrı bir derlemede çalışırken, ancak test edilen derlemede C# veya Visual Basic olarak işaretlenen üyelere erişim gerektirir `internal` `Friend` .

- Bir sınıf kitaplığı geliştirirken ve kitaplığa eklemeler ayrı derlemelerde bulunur, ancak `internal` C# dilinde veya Visual Basic olarak işaretlenen mevcut derlemelerdeki üyelere erişim gerektirir `Friend` .

## <a name="remarks"></a>Açıklamalar

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>Belirli bir derleme için bir veya daha fazla Friend derlemesini tanımlamak üzere özniteliğini kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *derleme a* içindeki özniteliğini kullanır ve bir Friend derlemesi olarak bir derlemeyi *AssemblyB* olarak belirtir. Bu, bütünleştirilmiş kod, C# ' de veya Visual Basic olarak işaretlenen *derleme A* 'daki tüm türlere ve üyelere derleme Için *AssemblyB* erişimi sağlar `internal` `Friend` .

> [!NOTE]
> *Derleme A*gibi başka bir derlemenin iç türlerine veya iç üyelerine erişecek *AssemblyB* gibi bir derlemeyi derlerken, **-Out** derleyici seçeneğini kullanarak çıkış dosyasının (*. exe* veya *. dll*) adını açıkça belirtmeniz gerekir. Bu gereklidir çünkü derleyici, dış başvurulara bağlama sırasında oluşturmakta olduğu derlemenin adını henüz üretmemiştir. Daha fazla bilgi için bkz. [-Out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [-Out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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

Yalnızca arkadaş olarak açıkça belirttiğiniz derlemeler `internal` (C#) veya `Friend` (Visual Basic) türlerine ve üyelerine erişebilir. Örneğin, *AssemblyB* , *derleme a* 'Nın arkadaşınız ve *derleme c* , *AssemblyB*'ye başvuruyorsa, *derleme c* 'nin `internal` a derlemesinde (C#) veya `Friend` (Visual Basic) türlerine erişimi yoktur. *Assembly A*

Derleyici, özniteliğe geçirilen arkadaş derleme adının bazı temel doğrulamasını gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> . Eğer *derlemesi bir* Friend derlemesi olarak *AssemblyB* bildirirse, doğrulama kuralları aşağıdaki gibidir:

- *Derleme A* tanımlayıcı olarak adlandırılmışsa, *AssemblyB* de tanımlayıcı adlandırılmış olmalıdır. Özniteliğine geçirilen arkadaş derleme adı, *AssemblyB*imzalamak için kullanılan tanımlayıcı ad anahtarının derleme adından ve ortak anahtarından oluşmalıdır.

     Özniteliğe geçirilen arkadaş derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> *AssemblyB*'nin tanımlayıcı adı olamaz. Bütünleştirilmiş kod sürümü, kültür, mimari veya ortak anahtar belirtecini eklemeyin.

- *Derleme A* tanımlayıcı adlandırılmış değilse, arkadaş derleme adı yalnızca derleme adından oluşmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: imzasız arkadaş derlemeleri oluşturma](create-unsigned-friend.md).

- *AssemblyB* tanımlayıcı adlandırılmış ise, proje ayarını veya komut satırı derleyici seçeneğini kullanarak *AssemblyB* için tanımlayıcı ad anahtarını belirtmeniz gerekir `/keyfile` . Daha fazla bilgi için bkz. [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md).

 <xref:System.Security.Permissions.StrongNameIdentityPermission>Sınıfı, aşağıdaki farklılıklarla türleri paylaşma özelliği de sağlar:

- <xref:System.Security.Permissions.StrongNameIdentityPermission>tek bir tür için geçerlidir, ancak bir arkadaş derleme tüm derleme için geçerlidir.

- *Bir derlemede* *AssemblyB*ile paylaşmak istediğiniz yüzlerce tür varsa, tümüne eklemeniz gerekir <xref:System.Security.Permissions.StrongNameIdentityPermission> . Bir arkadaş derleme kullanıyorsanız, yalnızca bir defa arkadaş ilişki bildirmeniz gerekir.

- Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission> , paylaşmak istediğiniz türlerin ortak olarak bildirilmesini gerekir. Bir arkadaş derleme kullanıyorsanız, paylaşılan türler `internal` (C#) veya `Friend` (Visual Basic) olarak belirtilir.

Bir `internal` `Friend` Modül dosyasından ( *. netmodule* uzantılı bir dosya) bir derlemenin (C#) veya (Visual Basic) türlerine ve yöntemlerine erişme hakkında daha fazla bilgi için, bkz: [-moduleassemblyname (c#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) veya [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Nasıl yapılır: imzasız arkadaş derlemeleri oluşturma](create-unsigned-friend.md)
- [Nasıl yapılır: imzalı arkadaş derlemeleri oluşturma](create-signed-friend.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [C# programlama kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama kavramları (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
