---
title: "Arkadaş derlemeler (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d3a37629582e4fc2606afaf606735464c0d247a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assemblies-visual-basic"></a>Arkadaş derlemeler (Visual Basic)
A *derlemeyi* başka bir derlemenin erişebileceği bir derleme [arkadaş](../../../../visual-basic/language-reference/modifiers/friend.md) türleri ve üyeleri. Derleme bir derlemeyi olarak belirlerseniz, artık işareti türleri ve bunları sırayla genel olarak üyeleri diğer derlemelerden tarafından erişilecek yok. Bu özellikle aşağıdaki senaryolarda kullanışlıdır:  
  
-   Birim testi sırasında test kodu çalıştırdığında, ayrı bir derleme ancak olarak işaretlenmiş sınanan derlemesindeki üyelerine erişimi gerektirir. `Friend`.  
  
-   Ne zaman bir sınıf kitaplığı geliştirdiğiniz ve kitaplık eklemeler ayrı derlemelerde bulunan ancak olarak işaretlenmiş mevcut derlemeleri üyeler erişim gerektiren `Friend`.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> verilen derleme için bir veya daha fazla arkadaş derlemeleri tanımlamak için öznitelik. Aşağıdaki örnek kullanır <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği bir derlemede ve derleme belirten `AssemblyB` Arkadaş derlemesi olarak. Bu derleme verir `AssemblyB` tüm türleri ve üyeleri bir olarak işaretlenmiş derlemede erişim `Friend`.  
  
> [!NOTE]
>  Derleme zaman derleme (derleme `AssemblyB`) iç türleri veya başka bir derleme iç üyeleri erişecek (derleme *A*), kullanarakaçıkça(.exeveya.dll)çıkışdosyasınınadıbelirtmelisiniz**/out** derleyici seçeneği. Derleyici henüz dış başvuruları bağlama zamanında oluşturma derleme adı üretti değil çünkü bu gereklidir. Daha fazla bilgi için bkz: [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
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
  
 Arkadaş erişebileceği, açıkça belirttiğiniz derlemeleri `Friend` türleri ve üyeleri. Derleme B Arkadaş derlemesi ve C derleme başvurularını derleme B ise, örneğin, C erişimi yok `Friend` A'daki türleri  
  
 Bazı temel doğrulama geçirilen arkadaş derleme adının derleyici gerçekleştirir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği. Derleme *A* bildirir *B* arkadaş derleme olarak doğrulama kuralları aşağıdaki gibidir:  
  
-   Derleme *A* adlı, derleme güçlü olan *B* de strong adlandırılmalıdır. Özniteliğe geçirilen arkadaş derleme adı derleme adı ve derlemeyi imzalamak için kullanılan tanımlayıcı ad anahtar ortak anahtarını oluşmalıdır *B*.  
  
     Geçirilir arkadaş derleme adı <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği olamaz derleme güçlü adı *B*: derleme sürüm, kültür, mimari veya ortak anahtar belirteci içermez.  
  
-   Derleme *A* adlı arkadaş derleme adı yalnızca derleme adını oluşması sağlam değil. Daha fazla bilgi için bkz: [nasıl yapılır: oluşturmak imzasız arkadaş derlemeler (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Derleme *B* adlı, derleme için güçlü ad anahtar belirtmelisiniz güçlü olan *B* proje ayarı veya komut satırı kullanarak `/keyfile` derleyici seçeneği. Daha fazla bilgi için bkz: [nasıl yapılır: imzalı arkadaş derlemeleri oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Sınıfı türleri, aşağıdaki farklarla paylaşma olanağı sağlar:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>bir derlemeyi tüm derlemeye uygularken tek tek bir türü için geçerlidir.  
  
-   Derlemedeki türleri yüzlerce varsa *A* derleme paylaşmak istediğiniz *B*, eklemek zorunda <xref:System.Security.Permissions.StrongNameIdentityPermission> bunların tümüne. Bir derlemeyi kullanırsanız, yalnızca arkadaş ilişki kez bildirme gerekir.  
  
-   Kullanırsanız <xref:System.Security.Permissions.StrongNameIdentityPermission>, paylaşmak istediğiniz türleri genel olarak bildirilmesi gerekir. Bir derlemeyi kullanırsanız, paylaşılan türleri olarak bildirilen `Friend`.  
  
 Bir derlemenin erişim hakkında bilgi için `Friend` türleri ve yöntemleri modülü dosyasından (uzantılı bir dosya .netmodule), bkz: [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [Nasıl yapılır: İmzasız arkadaş derlemeleri (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [Nasıl yapılır: imzalı arkadaş derlemeleri (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Derlemeler ve Genel Derleme Önbelleği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Programlama Kavramları](../../../../visual-basic/programming-guide/concepts/index.md)
