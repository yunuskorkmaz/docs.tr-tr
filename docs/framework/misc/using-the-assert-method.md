---
title: Onay Yöntemini Kullanma
ms.date: 03/30/2017
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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181100"
---
# <a name="using-the-assert-method"></a>Onay Yöntemini Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>kod erişim izni sınıflarında ve sınıfta çağrılabilen bir yöntemdir. <xref:System.Security.PermissionSet> Kodunuzun (ve alt akış arayanların) kodunuzun yapmasına izin verdiği ancak arayanların yapma izni olmayan eylemleri gerçekleştirmesini etkinleştirmek için **Assert'ı** kullanabilirsiniz. Güvenlik iddiası, çalışma zamanının güvenlik denetimi sırasında gerçekleştirdiği normal işlemi değiştirir. İzin aldığınızda, güvenlik sistemine, öne edilen izin için kodunuzu arayanlara denetlememelerini söyler.  
  
> [!CAUTION]
> Güvenlik açıklarını açabildikleri ve güvenlik kısıtlamalarını zorlamak için çalışma zamanı mekanizmasını zayıflatabilecekleri için iddiaları dikkatle kullanın.  
  
 İddialar, kitaplığın yönetilmeyen koda çağrı yaptığı veya kitaplığın kullanım amacıyla açıkça ilişkili olmayan bir izin gerektiren bir arama yaptığı durumlarda yararlıdır. Örneğin, yönetilmeyen koda çağıran tüm yönetilen kod, **Yönetilmeyen Kod** bayrağı belirtilen **SecurityPermission'a** sahip olmalıdır. Yerel intranetten indirilen kod gibi yerel bilgisayardan kaynaklanamayan kod, varsayılan olarak bu izin verilmez. Bu nedenle, yerel intranetten indirilen kodun yönetilmeyen kod kullanan bir kitaplığı arayabilmesi için, kitaplık tarafından öne edilen izne sahip olması gerekir. Ayrıca, bazı kitaplıklar arayanlar için görünmeyen ve özel izinler gerektiren aramalar yapabilir.  
  
 Ayrıca, kodunuzun bir kaynağa arayanlardan tamamen gizli bir şekilde eriştiği durumlarda da iddiaları kullanabilirsiniz. Örneğin, kitaplığınizin bir veritabanından bilgi edindiğini, ancak işlemde bilgisayar kayıt defterindeki bilgileri de okuduğunu varsayalım. Kitaplığınızı kullanan geliştiricilerin kaynağınıza erişimi olmadığından, kodlarınızı kullanmak için **Registry Permission** gerektirdiğini bilmelerinin bir yolu yoktur. Bu durumda, kodunuzu arayanların kayıt defterine erişim iznine sahip olmasını gerektirmenin makul veya gerekli olmadığına karar verirseniz, kayıt defterini okumak için izin verebilirsiniz. Bu durumda, **Kayıt Defteri İzni** olmayan arayanların kitaplığı kullanabilmesi için kitaplığın izin belgesini belirlemesi uygundur.  
  
 İddia, yalnızca ileri edilen izin ve alt akım arayan tarafından talep edilen izin aynı türdeyse ve istenen izin talep edilen iznin bir alt kümesiyse yığın yürüyüşünü etkiler. Örneğin, C sürücüsündeki tüm dosyaları okumak için **FileIOPermission'u** iddia ederseniz ve **FileIOPermission'un** C:\Temp'taki dosyaları okuması için bir aşağı akış talebi yapılırsa, öne etme yığın yürüyüşünü etkileyebilir; ancak, talep **FileIOPermission** C sürücüsüne yazmak için olsaydı, iddia hiçbir etkisi olurdu.  
  
 İddiaları gerçekleştirmek için, kodunuz hem iddia ettiğiniz izin hem <xref:System.Security.Permissions.SecurityPermission> de öne etme hakkını temsil eden izni verilmelidir. Kodunuzu verilmediği ne kadar izin verebilirsiniz, ancak iddia başarılı olmasına neden olabilir önce güvenlik denetimi başarısız olacağını, çünkü iddia anlamsız olacaktır.  
  
 Aşağıdaki **resimde, Assert'ı**kullandığınızda neler olduğunu gösterilmektedir. A, B, C, E ve F derlemeleri ve P1 ve P1A olmak üzere iki izin hakkında aşağıdaki ifadelerin doğru olduğunu varsayalım:  
  
- P1A, C sürücüsünde .txt dosyalarını okuma hakkını temsil eder.  
  
- P1, C sürücüsündeki tüm dosyaları okuma hakkını temsil eder.  
  
- P1A ve P1 her ikisi de **FileIOPermission** türleridir ve P1A P1'in bir alt kümesidir.  
  
- E ve F derlemelerine P1A izni verilmiştir.  
  
- C derlemesi P1 izni almıştır.  
  
- A ve B derlemelerine ne P1 ne de P1A izinleri verilmiştir.  
  
- Yöntem A derlemesinde, B metodu B derlemesinde ve benzeri şekillerde bulunur.  
  
 ![Assert yöntemi derlemelerini gösteren diyagram.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 Bu senaryoda, Yöntem A Çağrıları B, B C, C çağrıları E çağırır ve E F. Yöntem C çağırır C sürücüsü (izin P1) dosyaları okumak için izin iddia ve yöntem E C sürücü (izin P1A) üzerinde .txt dosyaları okumak için izin ister. Çalışma zamanında F'de taleple karşılaşıldığında, E. E ile başlayan F'nin tüm arayanların izinlerini kontrol etmek için bir yığın yürüyüşü gerçekleştirilir, bu nedenle yığın yürümesi C'nin iddiasının bulunduğu C izinlerini incelemeye devam eder. İstenen izin (P1A) iddia edilen iznin (P1) bir alt kümesi olduğundan, yığın yürümesi durur ve güvenlik denetimi otomatik olarak başarılı olur. A ve B derlemelerine P1A izni verilmemesi önemli değildir. P1'i öne sürerek, Yöntem C, arayanlara bu kaynağa erişim izni verilmese bile, arayanların P1 tarafından korunan kaynağa erişebilmesini sağlar.  
  
 Bir sınıf kitaplığı tasarlarsanız ve bir sınıf korumalı bir kaynağa erişiyorsa, çoğu durumda sınıfın arayanların uygun izne sahip olması gereken bir güvenlik talebi oluşturmanız gerekir. Sınıf daha sonra arayanların çoğunun izni olmayacağını bildiğiniz bir işlem gerçekleştirirse ve bu arayanların kodunuzu aramasına izin verme sorumluluğunu üstlenmek istiyorsanız, kodun gerçekleştirdiği işlemi temsil eden bir izin nesnesi üzerinde **Assert** yöntemini çağırarak izni nizi belirtebilirsiniz. **Assert'ı** bu şekilde kullanmak, normalde bunu yapamayan arayanların kodunuzu aramasına olanak tanır. Bu nedenle, bir izin verirseniz, bileşeninizin kötüye kullanılmasını önlemek için önceden uygun güvenlik denetimlerini yaptığınızdan emin olmalısınız.  
  
 Örneğin, çok güvenilen kitaplık sınıfınızın dosyaları silen bir yöntemi olduğunu varsayalım. Yönetilmeyen bir Win32 işlevini çağırarak dosyaya erişir. Arayan, silinecek dosyanın adını geçerek kodunuzun **Sil** yöntemini çağırır, C:\Test.txt. **Sil** yöntemi içinde, kodunuz <xref:System.Security.Permissions.FileIOPermission> C:\Test.txt'ye yazma erişimini temsil eden bir nesne oluşturur. (Bir dosyayı silmek için yazma erişimi gereklidir.) Ardından **kodunuz, FileIOPermission** nesnesinin **Talep** yöntemini arayarak zorunlu bir güvenlik denetimi çağırır. Arama yığınındaki arayanlardan biri bu izne sahip <xref:System.Security.SecurityException> değilse, bir atılmıştır. Özel durum atılırsa, tüm arayanların C:\Test.txt'ye erişme hakkına sahip olduğunu bilirsiniz. Arayanlarınızın çoğunun yönetilmeyen koda erişmek için izni olmayacağını düşünüyorsanız, kodunuz <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kodu arama hakkını temsil eden bir nesne oluşturur ve nesnenin **Assert** yöntemini çağırır. Son olarak, C:\Text.txt'yi silmek için yönetilmeyen Win32 işlevini çağırır ve denetimi arayana döndürür.  
  
> [!CAUTION]
> Kodunuzu iddia ettiğiniz izinle korunan bir kaynağa erişmek için başka kod tarafından kullanılabildiği durumlarda kodunuzu öne etme dekullanmadığından emin olmalısınız. Örneğin, adı arayan tarafından parametre olarak belirtilen bir dosyaya yazan kodda, kodunuz üçüncü bir tarafça kötüye kullanılmaya açık olduğundan Dosyalara yazma için **FileIOPermission'u** öne sürmezsiniz.  
  
 Zorunlu güvenlik sözdizimini kullandığınızda, aynı yöntemde birden çok izinde **Assert** yöntemini çağırmak bir güvenlik özel durum atılmasına neden olur. Bunun yerine, bir **PermissionSet** nesnesi oluşturmalı, çağırmak istediğiniz tek tek izinleri geçirmeli ve ardından **PermissionSet** nesnesindeki **Assert** yöntemini aramalısınız. Bildirimsel güvenlik sözdizimini **kullandığınızda, Assert** yöntemini birden çok kez arayabilirsiniz.  
  
 Aşağıdaki örnek, **Assert** yöntemini kullanarak güvenlik denetimlerini geçersiz kılmak için bildirimsel sözdizimini gösterir. **FileIOPermissionAttribute** sözdiziminin iki değer <xref:System.Security.Permissions.SecurityAction> aldığına dikkat edin: numaralandırma ve dosyanın veya iznin bulunduğu yer ve izin verilecek. İsteklilerin **Assert** dosyaya erişmek `C:\Log.txt` için izin için denetlenmemesine rağmen, Assert araması erişim taleplerinin başarılı olmasına neden olur.  
  
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
  
 Aşağıdaki kod **parçaları, Assert** yöntemini kullanarak güvenlik denetimlerini geçersiz kılmak için zorunlu sözdizimini gösterir. Bu örnekte, **FileIOPermission** nesnesinin bir örneği bildirilir. Onun oluşturucu **fileioPermissionAccess.AllAccess** izin verilen erişim türünü tanımlamak için geçilir, ardından dosyanın konumunu açıklayan bir dize. **FileIOPermission** nesnesi tanımlandıktan sonra, güvenlik denetimini geçersiz kılmak için yalnızca **Assert** yöntemini aramanız gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [Öznitelikler](../../standard/attributes/index.md)
- [Kod Erişimi Güvenliği](code-access-security.md)
