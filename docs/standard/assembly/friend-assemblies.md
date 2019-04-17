---
title: Arkadaş derlemeler (C#)
ms.date: 03/03/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: 770eb70a5350d7d26e03cb4e605b442100da2a53
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59614031"
---
# <a name="friend-assemblies"></a>Arkadaş derlemeleri

A *arkadaş derleme* başka bir derlemenin erişebilen bir derleme [iç](../../csharp/language-reference/keywords/internal.md) (içinde C# veya [arkadaş](../../visual-basic/language-reference/modifiers/friend.md) Visual Basic'te) türler ve üyeler. Derleme arkadaş derleme olarak belirlerseniz, artık türleri ve üyeleri edebilmeleri genel olarak diğer derlemeler tarafından erişilecek işareti yok. Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:

- Birim testi sırasında test kod çalıştığında ayrı bir derleme ancak olarak işaretlenmiş test edilen derleme üyelerine erişim gerektirir. `internal` içinde C# veya `Friend` Visual Basic'te.

- Ne zaman bir sınıf kitaplığı geliştiriyorsanız ve kitaplığı eklemeleri ayrı derlemelerinde toplanır, ancak üye olarak işaretlenmiş var olan derlemelerde erişmesi `internal` içinde C# veya `Friend` Visual Basic'te.

## <a name="remarks"></a>Açıklamalar

Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> belirli bir derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik. Aşağıdaki örnekte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik bir derlemede ve derleme belirtir `AssemblyB` arkadaş derleme olarak. Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derleme erişim `internal` içinde C# veya `Friend` Visual Basic'te.

> [!NOTE]
> Derleme yaparken bir derleme (derleme `AssemblyB`) iç türleri veya başka bir derlemenin iç üyeleri erişir (derleme *A*), çıktı dosyası (.exe veya .dll) adı kullanarakaçıkçabelirtmenizgerekir **/out** derleyici seçeneği. Bu, derleyicinin onu dış başvuruları bağlayarak zaman oluşturma derleme adı henüz oluşturmamıştır çünkü gereklidir. Daha fazla bilgi için [/out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) veya [/out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

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

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

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

---

Arkadaş erişebilir, açıkça belirttiğiniz derlemeleri `internal` (içinde C# veya `Friend` Visual Basic'te) türler ve üyeler. Derleme B C derleme başvuruları derleme B derleme A'ya ve arkadaş ise, örneğin, C erişimi yok `internal` (içinde C# veya `Friend` Visual Basic'te) A'daki türleri

Derleyici geçirilen friend derleme adı, bazı temel doğrulama gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Derleme *A* bildirir *B* arkadaş derleme, doğrulama kuralları aşağıdaki gibidir:

- Derleme *A* adlı derleme güçlü olduğunu *B* ayrıca strong adlandırılmalıdır. Özniteliğe geçirilir friend derleme adı, derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtarı ortak anahtarını oluşmalıdır *B*.

     Geçirilen friend derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme tanımlayıcı adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.

- Derleme *A* adlı friend derleme adı yalnızca derleme adını oluşmalıdır sağlam değil. Daha fazla bilgi için [nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) veya [nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).

- Derleme *B* adındaki, derlemenin tanımlayıcı ad anahtarı belirtmeniz gerekir güçlü olduğunu *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği. Daha fazla bilgi için [nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) veya [nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).

 <xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıf türleri ile aşağıdaki farklar paylaşma olanağı da sağlar:

- <xref:System.Security.Permissions.StrongNameIdentityPermission> arkadaş derleme tüm derleme için geçerli olsa da tek tek bir tür için geçerlidir.

- Bütünleştirilmiş kodundaki türler yüzlerce varsa *A* derleme ile paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne. Arkadaş derleme kullanıyorsanız, yalnızca arkadaş ilişki bildirmek üzere gerekir.

- Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir. Arkadaş derleme kullanırsanız, paylaşılan türü olarak bildirilmiş olan `internal` (içinde C# veya `Friend` Visual Basic'te).

Bir derlemenin erişim hakkında daha fazla bilgi için `internal` (içinde C# veya `Friend` Visual Basic'te) türleri ve yöntemleri bir modül dosyası (bir .netmodule uzantılı), bkz. [/moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) veya [/moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Nasıl yapılır: (Visual Basic) imzasız arkadaş derlemeleri oluşturma](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)
- [Nasıl yapılır: İmzalı arkadaş derlemeleri oluşturma (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [Nasıl yapılır: (Visual Basic) imzalı arkadaş derlemeleri oluşturma](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)
- [.NET’te bütünleştirilmiş kodlar](index.md)
- [C# Programlama Kılavuzu](../../csharp/programming-guide/index.md)
- [Programlama Kavramları](../../visual-basic/programming-guide/concepts/index.md)
