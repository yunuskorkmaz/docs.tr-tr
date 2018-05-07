---
title: Arkadaş derlemeler (C#)
ms.date: 07/20/2015
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
ms.openlocfilehash: c9265a6ce53d97f1d0b8aaeb0f1aae3b7b75f2cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="friend-assemblies-c"></a>Arkadaş derlemeler (C#)
A *derlemeyi* başka bir derlemenin erişebileceği bir derleme [iç](../../../../csharp/language-reference/keywords/internal.md) türleri ve üyeleri. Derleme bir derlemeyi olarak belirlerseniz, artık işareti türleri ve bunları sırayla genel olarak üyeleri diğer derlemelerden tarafından erişilecek yok. Bu özellikle aşağıdaki senaryolarda kullanışlıdır:  
  
-   Birim testi sırasında test kodu çalıştırdığında, ayrı bir derleme ancak olarak işaretlenmiş sınanan derlemesindeki üyelerine erişimi gerektirir. `internal` .  
  
-   Ne zaman bir sınıf kitaplığı geliştirdiğiniz ve kitaplık eklemeler ayrı derlemelerde bulunan ancak olarak işaretlenmiş mevcut derlemeleri üyeler erişim gerektiren `internal` .  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> verilen derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik. Aşağıdaki örnek kullanır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği bir derlemede ve derleme belirten `AssemblyB` Arkadaş derlemesi olarak. Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derlemede erişim `internal`.  
  
> [!NOTE]
>  Derleme zaman derleme (derleme `AssemblyB`) iç türleri veya başka bir derleme iç üyeleri erişecek (derleme *A*), kullanarakaçıkça(.exeveya.dll)çıkışdosyasınınadıbelirtmelisiniz **/out** derleyici seçeneği. Derleyici henüz dış başvuruları bağlama zamanında oluşturma derleme adı üretti değil çünkü bu gereklidir. Daha fazla bilgi için bkz: [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .  
  
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
  
 Arkadaş erişebileceği, açıkça belirttiğiniz derlemeleri `internal` türleri ve üyeleri. Derleme B Arkadaş derlemesi ve C derleme başvurularını derleme B ise, örneğin, C erişimi yok `internal` A'daki türleri  
  
 Bazı temel doğrulama geçirilen arkadaş derleme adının derleyici gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Derleme *A* bildirir *B* arkadaş derleme olarak doğrulama kuralları aşağıdaki gibidir:  
  
-   Derleme *A* adlı, derleme güçlü olan *B* de strong adlandırılmalıdır. Özniteliğe geçirilen arkadaş derleme adı derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtar ortak anahtarını oluşmalıdır *B*.  
  
     Geçirilir arkadaş derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme güçlü adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.  
  
-   Derleme *A* adlı arkadaş derleme adı yalnızca derleme adını oluşması sağlam değil. Daha fazla bilgi için bkz: [nasıl yapılır: İmzasız arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Derleme *B* adlı, derleme için güçlü ad anahtar belirtmelisiniz güçlü olan *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği. Daha fazla bilgi için bkz: [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıfı türleri, aşağıdaki farklarla paylaşma olanağı sağlar:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> bir derlemeyi tüm derlemeye uygularken tek tek bir türü için geçerlidir.  
  
-   Derlemedeki türleri yüzlerce varsa *A* derleme paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne. Bir derlemeyi kullanırsanız, yalnızca arkadaş ilişki kez bildirme gerekir.  
  
-   Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir. Bir derlemeyi kullanırsanız, paylaşılan türleri olarak bildirilen `internal`.  
  
 Bir derlemenin erişim hakkında bilgi için `internal` türleri ve yöntemleri modülü dosyasından (uzantılı bir dosya .netmodule), bkz: [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [Nasıl yapılır: İmzasız arkadaş derlemeleri (C#) oluşturma](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [Nasıl yapılır: imzalı arkadaş derlemeleri (C#) oluşturma](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Derlemeler ve Genel Derleme Önbelleği (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)
