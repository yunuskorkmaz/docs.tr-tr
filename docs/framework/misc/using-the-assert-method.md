---
title: Onay Yöntemini Kullanma
description: Kodunuzun çağıranlarını değil, kodunuzun (ve aşağı akış çağıranlarının) izin aldığı şeyleri yapması için bkz. onay yöntemini nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: 096e0375a94c92a835cccb4d1b3297783b4120e9
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309813"
---
# <a name="using-the-assert-method"></a>Onay Yöntemini Kullanma
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>, kod erişimi izin sınıflarında ve sınıfında çağrılabilecek bir yöntemdir <xref:System.Security.PermissionSet> . Kodunuzun (ve aşağı akış çağıranlarının), kodunuzun gerçekleştirme iznine sahip olduğu, ancak çağıranlarının yapma izni olmayan eylemleri **gerçekleştirmesini sağlamak için onay kullanabilirsiniz.** Güvenlik onayı, çalışma zamanının güvenlik denetimi sırasında gerçekleştirdiği normal işlemi değiştirir. Bir izin belirttiğinizde, güvenlik sistemine, onaylanan izin için kodunuzun çağıranlarını denetvermediğini söyler.  
  
> [!CAUTION]
> Güvenlik boşluklarını açabildiklerinden ve güvenlik kısıtlamalarını uygulamak için çalışma zamanının mekanizmasından daha az yer olabileceğinden onayları dikkatle kullanın.  
  
 Onaylamalar, kitaplığın yönetilmeyen koda çağrı yaptığı veya kitaplığın amaçlanan kullanımı için açıkça ilgili olmayan bir izin gerektiren bir çağrı yaptığı durumlarda faydalıdır. Örneğin, yönetilmeyen koda çağrı yapan tüm yönetilen kodların **UnmanagedCode** bayrağıyla **SecurityPermission** değeri olmalıdır. Yerel intranetten indirilen kod gibi yerel bilgisayardan kaynaklanmayan koda bu izin varsayılan olarak verilmeyecektir. Bu nedenle, yerel intranetten indirilen kodun yönetilmeyen kod kullanan bir kitaplığı çağırabilmesi için, kitaplık tarafından onaylanan izne sahip olması gerekir. Ayrıca, bazı kitaplıklar arayanlara görünmeyen ve özel izinler gerektiren çağrılar yapabilir.  
  
 Ayrıca, kodunuzun bir kaynağa, çağıranlardan tamamen gizlenmiş bir şekilde eriştiği durumlarda onayları kullanabilirsiniz. Örneğin, kitaplığınızın bir veritabanından bilgi edindiğini varsayalım, ancak işlem içinde bilgisayar kayıt defterindeki bilgiler de okur. Kitaplığınızı kullanan geliştiricilerin kaynağınıza erişimi olmadığından, kodunuzun kullanılabilmesi için kodunun **RegistryPermission** gerektirdiğini bilmenin bir yolu yoktur. Bu durumda, kodunuzun çağıranlarının kayıt defterine erişim izni olmasını gerektirmek için makul veya gerekli olmadığına karar verirseniz, kayıt defterini okumak için izin onayı verebilirsiniz. Bu durumda, kitaplığın, **RegistryPermission** olmayan çağıranların kitaplığı kullanabilmesi için izni onayı için uygun olması gerekir.  
  
 Onaylama işlemi, yalnızca onaylanan izin ve bir aşağı akış çağıranı tarafından talep edilen izin aynı türde ise ve istenen izin, onaylanan iznin bir alt kümesi ise, yığın ilerleme durumunu etkiler. Örneğin, C sürücüsündeki tüm dosyaları okumak için **Dosyaıişle görev** seçeneğini belirlerseniz ve C:\Temp dosyasındaki dosyaları **okumak için bir** aşağı akış talebi yapılırsa, onaylama işlemi yığın yürüme işlemini etkileyebilir; Ancak talep, C sürücüsüne yazmak üzere **Dosya** için gerekliyse, onay etkisi olmaz.  
  
 Onaylama işlemleri gerçekleştirmek için, kodunuzun hem gerçekleştirdiğiniz izin hem de <xref:System.Security.Permissions.SecurityPermission> onaylama yapma hakkını temsil eden bir izni verilmelidir. Kodunuzun verilmemesine izin verseniz de, onaylama işleminin başarılı olabilmesi için güvenlik denetimi başarısız olacağından onaylama işlemi daha az olabilir.  
  
 Aşağıdaki çizimde, **onaylama**kullandığınızda ne olacağı gösterilmektedir. Aşağıdaki deyimlerin A, B, C, E ve F derlemeleri ve iki izin, P1 ve P1A için doğru olduğunu varsayalım:  
  
- P1A, C sürücüsündeki. txt dosyalarını okuma hakkını temsil eder.  
  
- P1, C sürücüsündeki tüm dosyaları okuma hakkını temsil eder.  
  
- P1A ve P1 her ikisi de **Dosya** türü ve P1A P1 'in bir alt kümesidir.  
  
- E ve F derlemelerinin P1A izni verildi.  
  
- C derlemesine P1 izni verildi.  
  
- A ve B bütünleştirilmiş kodlarına ne P1 ne de P1A izinleri verildi.  
  
- A yöntemi a derlemesinde bulunur, B yöntemi B derlemesinde bulunur ve bu şekilde devam eder.  
  
 ![Onaylama yöntemi derlemelerini gösteren diyagram.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 Bu senaryoda, A çağrısı B, B çağrı C, c ve d çağırır. Yöntem C, c sürücüsündeki (izin P1) dosyaları okumak için izin ve C sürücüsündeki. txt dosyalarını okumak için izin ister (izin P1A). F 'deki talebe çalışma zamanında karşılaşıldığında, E. E ile başlayan tüm F çağıranlarının izinlerini denetlemek için bir yığın yürüme işlemi, P1A izni verdi ve bu sayede yığın ilerlemenizin, c 'nin onaylama işlemi nerede bulunur. Talep edilen izin (P1A), onaylanan iznin (P1) bir alt kümesi olduğundan, yığın ilerleme durumunu ve güvenlik denetimi otomatik olarak başarılı olur. A ve B derlemelerinin izin P1A verilmediğinden bağımsız değildir. , P1, bu kaynağa erişim izni verilmese bile, C yöntemi,, çağıranların P1 tarafından korunan kaynağa erişmesine olanak sağlar.  
  
 Bir sınıf kitaplığı tasarlarsanız ve bir sınıf korunan kaynağa eriştiğinde, çoğu durumda, sınıfın çağıranlarının uygun izne sahip olmasını gerektiren bir güvenlik talebi oluşturmanız gerekir. Sınıf daha sonra, arayanların çoğunu bildiğiniz bir işlem gerçekleştiriyorsa ve bu çağıranların kodunuzun çağrılmasını sağlamak için sorumluluğu almak istiyorsanız, kodun gerçekleştirdiği işlemi temsil eden bir izin nesnesi üzerinde **onaylama** yöntemini çağırarak izni belirtebilirsiniz. Bu şekilde **onay kullanılması,** normalde, kodunuzu çağrı yapamayan çağıranlara izin verir. Bu nedenle, bir izin belirtirseniz, bileşenin kötüye kullanılmasını engellemek için, önceden uygun güvenlik denetimleri gerçekleştirdiğinizden emin olmanız gerekir.  
  
 Örneğin, yüksek oranda güvenilen kitaplık sınıfınızın dosyaları silen bir yöntemi olduğunu varsayalım. Yönetilmeyen bir Win32 işlevini çağırarak dosyaya erişir. Bir çağıran, kodunuzun **silme** yöntemini çağırır ve Silinecek dosyanın adını geçirerek C:\Test.txt. **Delete** yöntemi içinde, kodunuz <xref:System.Security.Permissions.FileIOPermission> C:\Test.txt yazma erişimini temsil eden bir nesne oluşturur. (Bir dosyayı silmek için yazma erişimi gereklidir.) Kodunuz daha sonra, **Fileıişle görev** nesnesinin **talep** yöntemini çağırarak bir kesinlik güvenlik denetimini çağırır. Çağrı yığınındaki çağıranların birinde bu izin yoksa, bir <xref:System.Security.SecurityException> oluşturulur. Hiçbir özel durum oluşursa, tüm Arayanların C:\Test.txt erişim hakkına sahip olduğunu bilirsiniz. Çağıranlarınızın çoğunun yönetilmeyen koda erişim izni olmadığından eminseniz, kodunuz, <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kodu çağırma ve nesnenin **onaylama** yöntemini çağırma hakkını temsil eden bir nesne oluşturur. Son olarak, C:\Text.txt silmek için yönetilmeyen Win32 işlevini çağırır ve denetimi çağırana döndürür.  
  
> [!CAUTION]
> Kodunuzun, yaptığınız izinlerle korunan bir kaynağa erişmek için kodunuzun diğer kod tarafından kullanılabileceği durumlarda onay kullanılmadığından emin olmanız gerekir. Örneğin, adı çağıran tarafından bir parametre olarak belirtilen bir dosyaya yazan kodda, kodunuzun bir üçüncü taraf tarafından kötüye kullanılmasına açık olması nedeniyle dosyalara yazmak **için dosya** yazma işlemi yapmamalıdır.  
  
 Zorunlu güvenlik sözdizimini kullandığınızda, aynı yöntemde birden çok izin üzerinde **onay yöntemi çağırmak** bir güvenlik özel durumunun oluşturulmasına neden olur. Bunun yerine, bir **PermissionSet** nesnesi oluşturmalı, çağırmak istediğiniz bireysel izinleri geçitirsiniz ve ardından **PermissionSet** nesnesi üzerinde **onaylama** yöntemini çağırmalısınız. Bildirim temelli güvenlik sözdizimini kullandığınızda **onay yöntemini birden** çok kez çağırabilirsiniz.  
  
 Aşağıdaki **örnekte, onay yöntemi kullanılarak** güvenlik denetimlerinin geçersiz kılınması için bildirime dayalı sözdizimi gösterilmektedir. **Filei, Missionattribute** sözdiziminin iki değer aldığını unutmayın: bir <xref:System.Security.Permissions.SecurityAction> numaralandırma ve izin verilecek dosyanın veya dizinin konumu. Çağrıya **yapılan çağrı** , `C:\Log.txt` çağıranlar dosyaya erişmek için izin verilmediği halde, erişim taleplerini başarılı olmasına neden olur.  
  
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
  
 Aşağıdaki kod **parçaları, onay yöntemini kullanarak** güvenlik denetimlerini geçersiz kılmak için zorunlu sözdizimi gösterir. Bu örnekte, **Fileıse görev** nesnesinin bir örneği bildirilmiştir. Oluşturucusunun, izin verilen erişim türünü ve ardından dosyanın konumunu açıklayan bir dize tarafından tanımlanması için **Fileımanmissionaccess. AllAccess** geçildi. **Dosya görev** nesnesi tanımlandıktan sonra, güvenlik denetimini geçersiz kılmak Için yalnızca **onaylama** yöntemini çağırmanız gerekir.  
  
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
