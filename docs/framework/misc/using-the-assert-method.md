---
title: "Onay Yöntemini Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a1627af9dd968a8a183a251d5352c62457f71e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-assert-method"></a>Onay Yöntemini Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>kod erişim izni sınıflarında çağrılabilen ve açık bir yöntem <xref:System.Security.PermissionSet> sınıfı. Kullanabileceğiniz **Assert** kodunuzu uygun izinlere sahip eylemler ancak kendi arayanlar gerçekleştirmek, kodunu (ve aşağı akış arayanlar) etkinleştirmek için izniniz olmayabilir. Güvenlik onaylama işlemi çalışma zamanı sırasında bir güvenlik denetimi gerçekleştirir normal işlem değiştirir. Bir izin assert, kodunuzu sürülen izni arayanlar denetlemek için güvenlik sistemi söyler.  
  
> [!CAUTION]
>  Güvenlik açıklarını açın ve güvenlik kısıtlamaları zorlama zamanının mekanizması olumsuz olduğundan onaylar dikkatli kullanın.  
  
 Onaylar kitaplığı yönetilmeyen koda çağrı veya kitaplığın kullanıma açıktır ilgili olmayan bir izni gerektiren çağrıda durumlarda faydalıdır. Örneğin, tüm yönetilen yönetilmeyen koda çağrı olmalıdır kodu **SecurityPermission** ile **UnmanagedCode** bayrağı belirtilmiş. Yerel bilgisayardan yerel intranetten indirilen kod gibi kaynaklanmayan kod varsayılan olarak bu izin verilmez. Bu nedenle, yönetilmeyen kod kullandığı bir kitaplık çağırmak yerel bir intranet bağlantısı indirilen kodu için sırayla kitaplığı tarafından uygulanan izni olmalıdır. Ayrıca, bazı kitaplıklar arayanlara görünmeyen ve özel izinleri gerektiren aramaları yapabilir.  
  
 İçinde ve kodunuzu tamamen gizli bir şekilde bir kaynak arayanlar erişen durumlarda onaylar de kullanabilirsiniz. Örneğin, kitaplık bir veritabanından bilgi edinme, ancak işleminde, bilgileri de bilgisayar kayıt defterinden okur. varsayalım. Kitaplığınızı kullanan geliştiriciler kaynağınıza erişimi yoktur çünkü bunlar kendi kodlarını gerektirdiğini bilerek bir yolu yoktur **RegistryPermission** kodunuzu kullanmak için. Bu durumda, makul ya da kodunuzu arayanlar kayıt defterine erişim iznine sahip gerektirecek şekilde gerekli olmadığını karar verirseniz, kayıt defterini okuma iznine assert. Bu durumda, bu arayanlar olmadan izni bunu onaylanacak kitaplığı için uygun olan **RegistryPermission** kitaplığını kullanabilirsiniz.  
  
 Onaylama işlemi, yalnızca aynı türde sürülen ve bir aşağı akış çağıran tarafından talep izninizin olup olmadığını ve istenilen izni sürülen izin kümesini ise yığın ilerlemesi etkiler. Örneğin, assert, **FileIOPermission** C sürücüsünde ve bir aşağı akış isteğe bağlı tüm dosyaları okumak için yapılan **FileIOPermission** C:\Temp klasöründeki dosyaları okumak için onaylama yığın ilerlemesi; etkileyebilir Ancak, talep için ise **FileIOPermission** C sürücüsü yazmak için onay hiçbir etkisi yoktur.  
  
 Onaylar gerçekleştirmek için kodunuzu sunduğundan hem iznine sahip olmanız ve <xref:System.Security.Permissions.SecurityPermission> onaylar yapma hakkı temsil eder. Kodunuzu verilmediği bir izin assert rağmen onaylama işlemi başarılı şekilde neden olabilecek önce güvenlik denetimi başarısız olacağı için onaylama durum olacaktır.  
  
 Aşağıdaki çizimde kullandığınızda ne olacağını gösterir **Assert**. Aşağıdaki deyimleri derlemeler A, B, C, E ve F ve P1 ve P1A iki izinleri hakkında doğru olduğunu varsayın:  
  
-   P1A C sürücüsünde .txt dosyaları okuma hakkı temsil eder.  
  
-   P1 C sürücüsündeki tüm dosyaları okuma hakkı temsil eder.  
  
-   P1A ve P1 olan her ikisi de **FileIOPermission** türleri ve P1A P1, bir alt kümesidir.  
  
-   Derlemeleri E ve F P1A izin verildi.  
  
-   Derleme C P1 izin verildi.  
  
-   Derlemeleri A ve B P1 ne P1A izinleri verildi.  
  
-   Yöntemi bir A derlemesinde bulunan, Yöntem B derleme B ve benzeri yer alır.  
  
 ![](../../../docs/framework/misc/media/assert.gif "Assert")  
Assert kullanma  
  
 Bu senaryo, yöntem A çağrıları B, B çağrıları C, C çağrıları E ve E çağrıları F'ye yöntemi C C sürücüsü (izni P1) dosyalarda okuma izni ve .txt dosyaları (izin P1A) C sürücüsünde okuma yöntemi E taleplerini izni onaylar. F'nde isteğe çalışma zamanında karşılaşıldığında, C C'ın onaylama nerede bulunduğundan, izinlerini incelemek için yığın ilerlemesi geçer şekilde yığın ilerlemesi F, tüm arayanlar izinlerini denetlemek için gerçekleştirilen E. E ile başlayan P1A izin verildi. Talep edilen izni (P1A) bir alt kümesini sürülen izni (P1) olduğundan, yığın ilerlemesi durur ve güvenlik denetimi otomatik olarak başarılı olur. A ve B P1A izni verilmemiş bu derlemeler önemli değildir. P1 sunduğundan tarafından yöntemi C arayanlar bu kaynağa erişim izni verilmemiş olsa bile onun arayanlar P1 tarafından korunan kaynak erişebilmesini sağlar.  
  
 Bir sınıf kitaplığı tasarlayın ve bir sınıf korunan bir kaynağa erişir, çoğu durumda, sınıfın Arayanların uygun izinlere sahip gerektiren bir güvenlik isteğe bağlı oluşturmanız gerekir. Sınıfı için bir işlem ardından gerçekleştirirse, kendi arayanlar çoğunu bildiğiniz izni olmaz ve kodunuzun çağırması bu arayanlara izin vererek sorumluluğunu yapılacak istekli olup olmadığını çağırarak izin assert **Assert** kodu işlemini temsil eden bir izni nesnesi üzerinde yöntemi gerçekleştirme. Kullanarak **Assert** bu yolla bunu normal olarak yapamadı sağlar arayanlar kodunuzu çağırın. Bu nedenle, bir izin assert, bileşeniniz kötüye kullanımını önlemek için önceden uygun güvenlik denetimleri gerçekleştirmek üzere emin olmalıdır.  
  
 Örneğin, yüksek oranda güvenilir kitaplığı sınıfınız dosyalarını siler bir yöntem olduğunu varsayalım. Dosya bir yönetilmeyen Win32 işlevini çağırarak erişir. Çağıran, kodun çağırır **silmek** silinecek, dosya adına geçirerek yöntemini C:\Test.txt. İçinde **silmek** yöntemi, kodunuzu oluşturur bir <xref:System.Security.Permissions.FileIOPermission> yazma erişimi için C:\Test.txt temsil eden nesne. (Yazma erişimi bir dosyayı silmek için gereklidir.) Sonra kodunuzu çağırarak kesinlik temelli güvenliği onay çağırır **FileIOPermission** nesnenin **talep** yöntemi. Çağrı yığınında arayanlar biri bu izne sahip değilse bir <xref:System.Security.SecurityException> oluşturulur. Hiçbir özel durum varsa, tüm arayanlar C:\Test.txt erişim hakkı olduğunu bilirsiniz. Düşündüğünüz olduğundan, arayanlar çoğunu yönetilmeyen kod erişim iznine sahip olmaz, kodunuzu daha sonra oluşturur bir <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kodu çağırma hakkı temsil eder ve nesnenin çağrıları nesne **Assert** yöntemi. Son olarak, C:\Text.txt silmek için yönetilmeyen Win32 işlevini çağırır ve çağırana denetimini döndürür.  
  
> [!CAUTION]
>  Kodunuzu onaylar kodunuzun başka bir kodla ettiği taraf olduğunu izni tarafından korunan bir kaynağa erişmek için kullanıldığı durumlarda kullanmadığından emin olmanız gerekir. Örneğin, adında bir parametre olarak çağıran tarafından belirtilen bir dosyaya yazar kodda, değil assert **FileIOPermission** kodunuzu bir üçüncü taraf tarafından kötüye açık olduğundan dosyalara yazma için.  
  
 Kesinlik temelli güvenliği sözdizimini kullandığınızda çağırma **Assert** yöntemi aynı yöntemi birden çok izinlerde durum bir güvenlik özel durumu neden olur. Bunun yerine, oluşturmalısınız bir **PermissionSet** nesne, istediğiniz çağırma ve ardından çağırmak için tek tek izinleri geçirmek **Assert** yöntemi **PermissionSet** nesne. Çağırabilirsiniz **Assert** yöntemi kez bildirimsel güvenliği sözdizimini kullandığınızda'den fazla.  
  
 Aşağıdaki örnek, bildirim temelli söz dizimini gösterir, kullanarak geçersiz kılma güvenlik denetimleri için **Assert** yöntemi. Dikkat **FileIOPermissionAttribute** sözdizimi iki değerleri alır: bir <xref:System.Security.Permissions.SecurityAction> numaralandırma ve dosya veya iznine sahip olduğu verilebilmesi için dizin konumu. Çağrı **Assert** erişmek için talepleri neden `C:\Log.txt` arayanlar dosyaya erişim izni için denetlenmez olsa bile, başarılı olması için.  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 Kullanarak geçersiz kılma güvenlik denetimleri için aşağıdaki kod parçası kesinlik temelli sözdizimi show **Assert** yöntemi. Bu örnekte, bir örneğini **FileIOPermission** nesne bildirildi. Kurucusu geçirilen **FileIOPermissionAccess.AllAccess** erişimine izin verilir, türünü tanımlamak için dosyanın konumunu tanımlayan bir dize tarafından izlenen. Bir kez **FileIOPermission** nesne tanımlanır, yalnızca çağırmanız gerekir, **Assert** güvenlik denetimi geçersiz kılmak için yöntem.  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [Öznitelikleri](../../../docs/standard/attributes/index.md)  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)
