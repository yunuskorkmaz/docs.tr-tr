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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 08b46d96f9fb950602766639559a375a25747010
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073734"
---
# <a name="using-the-assert-method"></a>Onay Yöntemini Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> kod erişim izni sınıflarında çağrılabilen ve üzerinde bir yöntem <xref:System.Security.PermissionSet> sınıfı. Kullanabileceğiniz **Assert** kodunuzu uygun izinlere sahip eylemler ancak çağıranlarını gerçekleştirmek, kodu (ve aşağı akış arayanlar) etkinleştirmek için izniniz olmayabilir. Güvenlik onaylama işlemi, bir güvenlik denetimi sırasında çalışma zamanı yapar normal işlem değiştirir. İzin onayı, kodunuzun olarak onaylanan izin için çağıranlar denetlemek için güvenlik sistemi söyler.  
  
> [!CAUTION]
>  Güvenlik açıkları açın ve güvenlik kısıtlamaları zorunlu tutmak için çalışma zamanının mekanizması olumsuz onaylar dikkatle kullanın.  
  
 Onaylar, Kitaplık'ın yönetilmeyen koda çağıran veya kitaplığın kullanım amacını açıkça ilgili olmayan bir izni gerektiren çağrıda durumlarda kullanışlıdır. Örneğin, tüm yönetilen yönetilmeyen koda çağrı olmalıdır kod **SecurityPermission** ile **UnmanagedCode** bayrağı belirtilmiş. Varsayılan olarak yerel bilgisayardan, yerel intranet üzerinden indirilen kod gibi kaynaklanmayan kod bu izin verilmez. Bu nedenle, çağırma kullanan yönetilmeyen kod kitaplığı için yerel intranet üzerinden indirilen kod için sırada bu kitaplığı tarafından onaylanan iznine sahip olmalıdır. Ayrıca, bazı kitaplıklar arayanlara görünmeyen ve özel izinleri gerektiren çağrıları neden olabilir.  
  
 Onaylamalar içinde ve kodunuzu tamamen gizli bir şekilde bir kaynak çağrı yapanlardan eriştiği durumlarda de kullanabilirsiniz. Örneğin, kitaplığınızı veritabanından bilgi edinme, ancak işlem sırasında ayrıca bilgisayar kayıt defterinden bilgilerini okur varsayalım. Kitaplığınızı kullanan geliştiriciler kaynağınıza erişimi olmadığından, kodlarını gerektirdiğini olduğunu bilmesinin imkanı sahiptirler **RegistryPermission** kodunuzu kullanmak için. Bu durumda, makul veya kodunuzun çağıranlar kayıt defterine erişim izni olmasını gerektiren için gerekli olmadığını karar verirseniz, kayıt defterini okuma izni onay. Bu durumda, Arayanların olmadan bunu izin onay kitaplık için uygun olan **RegistryPermission** kitaplığını kullanabilirsiniz.  
  
 Onaylama işlemi, yalnızca aynı tür olarak onaylanan ve bir aşağı akış çağıran tarafından talep edilen bir izninizin olması durumunda ve talep edilen izni olarak onaylanan izin kümesini ise yığın ilerlemesi etkiler. Örneğin, onaylama, **FileIOPermission** C sürücüsü ve aşağı akış isteğe bağlı tüm dosyaları okumak için yapıldığı **FileIOPermission** C:\Temp klasöründeki dosyaları okumak için yığın ilerlemesi; onaylama işlemi etkileyebilir Ancak, talep için ise **FileIOPermission** C sürücüsüne yazmak için onay hiçbir etkisi yoktur.  
  
 Onaylamalar gerçekleştirmek için kodunuzu sunduğundan hem iznine sahip olmanız gerekir ve <xref:System.Security.Permissions.SecurityPermission> onaylar yapma hakkı temsil eder. Kodunuzu verilmedi bir izin onay olsa da, onaylama işlemi başarılı olması için neden olabilecek önce güvenlik denetimi başarısız olacağı için onaylama anlamsız olacaktır.  
  
 Aşağıdaki gösterimde kullandığınızda neler **Assert**. Aşağıdaki deyimleri derlemeleri A, B, C, E ve F ve P1 ve P1A iki izinleri hakkında doğru olduğunu varsayalım:  
  
-   P1A C sürücüsündeki .txt dosyaları okuma hakkı temsil eder.  
  
-   P1 C sürücüsündeki tüm dosyaları okuma hakkı temsil eder.  
  
-   P1A ve P1 olan hem de **FileIOPermission** türleri ve P1A P1 özelliklerinin bir alt kümesidir.  
  
-   Derlemeleri E ve F P1A izin vermiş olmalıdır.  
  
-   Derleme C P1 izin verildi.  
  
-   A ve B derlemeleri P1 ne P1A izinleri verilmiş.  
  
-   Yöntemi bir bir derlemede yer alan, Yöntem B derleme B ve benzeri yer alır.  
  
 ![Assert yöntemi derlemeleri gösteren diyagram.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 Bu senaryo, yöntemi bir çağrıları B, C B çağrıları, C çağrı E ve E çağrılar F. yöntemi C (izin P1) C sürücüsündeki dosyaları okuma izni ve (izni P1A) C sürücüsündeki .txt dosyaları okumak için yöntem E taleplerini izni onaylar. Talep f çalışma zamanında karşılaşıldığında, C, C'ın onaylama nerede bulunduğundan izinlerini incelemek için yığın ilerlemesi geçer şekilde yığın ilerlemesi f, tüm çağıranların izinlerini kontrol etmek için gerçekleştirilir E. E başlangıç P1A izin verildi. Talep edilen izni (P1A) olarak onaylanan izni (P1) bir alt kümesi olduğundan, otomatik olarak yığın ilerlemesi durur ve güvenlik denetimi başarılı. A ve B P1A izni verilmemiş bu derlemeler önemli değildir. P1 sunduğundan tarafından C yöntemi çağıranlar, bu kaynağa erişim izni verilmemiş bile çağıranlarını P1 tarafından korunan kaynak erişebilmesini sağlar.  
  
 Bir sınıf kitaplığı tasarlayın ve bir sınıf, korunan bir kaynağa erişir, çoğu durumda, sınıfın çağıranlar uygun izinlere sahip gerektiren bir güvenlik talebi oluşturmanız gerekir. Sınıfı için bir işlem gerçekleştirir, hangi çağıranlarını çoğunu tanıdığınız izni olmaz ve kodunuzun çağrı bu arayanlara izin vererek sorumluluğunu yararlanmak istekliyse çağırarak izin onay **Assert** işlemini temsil eden bir izin nesnesi üzerinde yöntemi, şu kod gerçekleştiriyor. Kullanarak **Assert** bu yolla bunu normal olarak yapamadı sağlar çağıranlar kodunuzu çağırın. Bu nedenle, bir izin assert, bileşeninizin kötüye kullanımını engeller önlemek için önceden uygun güvenlik denetimleri gerçekleştirmek emin olmalısınız.  
  
 Örneğin, yüksek derecede güvenilen kitaplığı sınıfınıza dosyaları silen bir yöntem olduğunu varsayalım. Dosya, yönetilmeyen bir Win32 işlevini çağırarak erişir. Çağıran kod çağırır **Sil** silinecek dosyanın adını geçirerek yöntemini C:\Test.txt. İçinde **Sil** yöntemi, kod oluşturur bir <xref:System.Security.Permissions.FileIOPermission> yazma erişimi için C:\Test.txt temsil eden nesne. (Bir dosyayı silmek için yazma erişimi gereklidir.) Sonra kodunuzu çağırarak zorunlu güvenlik denetimi çağırır **FileIOPermission** nesnenin **isteğe** yöntemi. Çağrı yığınında çağıranlar birini bu izne sahip değilse bir <xref:System.Security.SecurityException> oluşturulur. Hiçbir özel durum varsa, tüm çağıranların C:\Test.txt erişim hakkı olduğunu bilirsiniz. Olduğuna inanıyorsanız, Arayanların çoğunu yönetilmeyen koda erişim iznine sahip olmaz, kodunuzu daha sonra oluşturur çünkü bir <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kod çağırmak için sağ temsil eder ve çağıran nesne **Assert** yöntemi. Son olarak, C:\Text.txt silmek için yönetilmeyen Win32 işlevini çağırır ve denetim çağırana döner.  
  
> [!CAUTION]
>  Kodunuzu onaylar burada kodunuzu başka kod tarafından sunduğundan izni tarafından korunan bir kaynağa erişmek için kullanılabilir durumda kullanmadığından emin olmanız gerekir. Örneğin, adında bir parametre olarak çağıran tarafından belirtilen bir dosyaya yazar kodunda, yok assert **FileIOPermission** kodunuzu bir üçüncü taraf tarafından kötüye açık olacağından, dosyalara yazma için.  
  
 Kesinlik temelli güvenlik sözdizimi kullandığınızda, çağırma **Assert** aynı yöntemi içinde birden fazla izinleri yöntemi, bir güvenlik özel durum oluşturulmasına neden olur. Bunun yerine, oluşturacağınız bir **PermissionSet** nesne, istediğiniz çağırır ve ardından çağırmak için ayrı ayrı izinler geçirmek **Assert** yöntemi **PermissionSet** nesne. Çağırabilirsiniz **Assert** yöntemi daha fazla kez bildirim temelli güvenlik sözdizimi kullandığınızda.  
  
 Kullanarak geçersiz kılma güvenlik denetimleri için aşağıdaki örnek, bildirim temelli söz dizimini gösterir. **Assert** yöntemi. Dikkat **FileIOPermissionAttribute** söz dizimi iki değer alır: bir <xref:System.Security.Permissions.SecurityAction> numaralandırma ve dosya veya dizin izni olduğu verilecek konumu. Çağrı **Assert** erişmek için talepleri neden `C:\Log.txt` dosyaya erişim izni için çağıranlar alınmamış olsa da, başarılı olması için.  
  
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
  
 Kullanarak geçersiz kılma güvenlik denetimleri için aşağıdaki kod parçası kesinlik temelli sözdizimi show **Assert** yöntemi. Bu örnekte, bir örneğini **FileIOPermission** nesne bildirilir. Oluşturucusuna geçirilen **FileIOPermissionAccess.AllAccess** izin, erişim türünü tanımlamak için dosyanın konumunu tanımlayan bir dize tarafından izlenen. Bir kez **FileIOPermission** nesne tanımlanır, yalnızca çağırmanız gerekir, **Assert** güvenlik denetimi geçersiz kılmak için yöntemi.  
  
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
- [Öznitelikler](../../../docs/standard/attributes/index.md)
- [Kod Erişimi Güvenliği](../../../docs/framework/misc/code-access-security.md)
