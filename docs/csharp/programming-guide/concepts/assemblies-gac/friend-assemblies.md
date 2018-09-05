---
title: Arkadaş derlemeler (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: e8c295fe23685e39e20a14ff23139339f24564c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510091"
---
# <a name="friend-assemblies-c"></a>Arkadaş derlemeler (C#)
A *arkadaş derleme* başka bir derlemenin erişebilen bir derleme [iç](../../../../csharp/language-reference/keywords/internal.md) türler ve üyeler. Derleme arkadaş derleme olarak belirlerseniz, artık türleri ve üyeleri edebilmeleri genel olarak diğer derlemeler tarafından erişilecek işareti yok. Bu, özellikle aşağıdaki senaryolarda kullanışlıdır:  
  
-   Birim testi sırasında test kod çalıştığında ayrı bir derleme ancak test edilen derleme üyeleri olarak işaretlenmiş erişim gerektirir. `internal` .  
  
-   Ne zaman bir sınıf kitaplığı geliştiriyorsanız ve kitaplığı eklemeleri ayrı derlemelerinde toplanır, ancak üye olarak işaretlenmiş var olan derlemelerde erişmesi `internal` .  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> belirli bir derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik. Aşağıdaki örnekte <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> öznitelik bir derlemede ve derleme belirtir `AssemblyB` arkadaş derleme olarak. Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derleme erişimi `internal`.  
  
> [!NOTE]
>  Derleme yaparken bir derleme (derleme `AssemblyB`) iç türleri veya başka bir derlemenin iç üyeleri erişir (derleme *A*), çıktı dosyası (.exe veya .dll) adı kullanarakaçıkçabelirtmenizgerekir **/out** derleyici seçeneği. Bu, derleyicinin onu dış başvuruları bağlayarak zaman oluşturma derleme adı henüz oluşturmamıştır çünkü gereklidir. Daha fazla bilgi için [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
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
  
 Arkadaş erişebilir, açıkça belirttiğiniz derlemeleri `internal` türler ve üyeler. Derleme B C derleme başvuruları derleme B derleme A'ya ve arkadaş ise, örneğin, C erişimi yok `internal` A'daki türleri  
  
 Derleyici geçirilen friend derleme adı, bazı temel doğrulama gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Derleme *A* bildirir *B* arkadaş derleme, doğrulama kuralları aşağıdaki gibidir:  
  
-   Derleme *A* adlı derleme güçlü olduğunu *B* ayrıca strong adlandırılmalıdır. Özniteliğe geçirilir friend derleme adı, derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtarı ortak anahtarını oluşmalıdır *B*.  
  
     Geçirilen friend derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme tanımlayıcı adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.  
  
-   Derleme *A* adlı friend derleme adı yalnızca derleme adını oluşmalıdır sağlam değil. Daha fazla bilgi için [nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Derleme *B* adındaki, derlemenin tanımlayıcı ad anahtarı belirtmeniz gerekir güçlü olduğunu *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği. Daha fazla bilgi için [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıf türleri ile aşağıdaki farklar paylaşma olanağı da sağlar:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> arkadaş derleme tüm derleme için geçerli olsa da tek tek bir tür için geçerlidir.  
  
-   Bütünleştirilmiş kodundaki türler yüzlerce varsa *A* derleme ile paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne. Arkadaş derleme kullanıyorsanız, yalnızca arkadaş ilişki bildirmek üzere gerekir.  
  
-   Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir. Arkadaş derleme kullanırsanız, paylaşılan türü olarak bildirilmiş olan `internal`.  
  
 Bir derlemenin erişim hakkında daha fazla bilgi için `internal` türleri ve yöntemleri bir modül dosyası (bir .netmodule uzantılı), bkz. [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
- <xref:System.Security.Permissions.StrongNameIdentityPermission>  
- [Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
- [Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
- [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
