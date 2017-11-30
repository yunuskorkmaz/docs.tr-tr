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
# <a name="using-the-assert-method"></a><span data-ttu-id="ee3ec-102">Onay Yöntemini Kullanma</span><span class="sxs-lookup"><span data-stu-id="ee3ec-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="ee3ec-103"><xref:System.Security.CodeAccessPermission.Assert%2A>kod erişim izni sınıflarında çağrılabilen ve açık bir yöntem <xref:System.Security.PermissionSet> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="ee3ec-104">Kullanabileceğiniz **Assert** kodunuzu uygun izinlere sahip eylemler ancak kendi arayanlar gerçekleştirmek, kodunu (ve aşağı akış arayanlar) etkinleştirmek için izniniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="ee3ec-105">Güvenlik onaylama işlemi çalışma zamanı sırasında bir güvenlik denetimi gerçekleştirir normal işlem değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="ee3ec-106">Bir izin assert, kodunuzu sürülen izni arayanlar denetlemek için güvenlik sistemi söyler.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ee3ec-107">Güvenlik açıklarını açın ve güvenlik kısıtlamaları zorlama zamanının mekanizması olumsuz olduğundan onaylar dikkatli kullanın.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="ee3ec-108">Onaylar kitaplığı yönetilmeyen koda çağrı veya kitaplığın kullanıma açıktır ilgili olmayan bir izni gerektiren çağrıda durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="ee3ec-109">Örneğin, tüm yönetilen yönetilmeyen koda çağrı olmalıdır kodu **SecurityPermission** ile **UnmanagedCode** bayrağı belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="ee3ec-110">Yerel bilgisayardan yerel intranetten indirilen kod gibi kaynaklanmayan kod varsayılan olarak bu izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="ee3ec-111">Bu nedenle, yönetilmeyen kod kullandığı bir kitaplık çağırmak yerel bir intranet bağlantısı indirilen kodu için sırayla kitaplığı tarafından uygulanan izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="ee3ec-112">Ayrıca, bazı kitaplıklar arayanlara görünmeyen ve özel izinleri gerektiren aramaları yapabilir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="ee3ec-113">İçinde ve kodunuzu tamamen gizli bir şekilde bir kaynak arayanlar erişen durumlarda onaylar de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="ee3ec-114">Örneğin, kitaplık bir veritabanından bilgi edinme, ancak işleminde, bilgileri de bilgisayar kayıt defterinden okur. varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="ee3ec-115">Kitaplığınızı kullanan geliştiriciler kaynağınıza erişimi yoktur çünkü bunlar kendi kodlarını gerektirdiğini bilerek bir yolu yoktur **RegistryPermission** kodunuzu kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="ee3ec-116">Bu durumda, makul ya da kodunuzu arayanlar kayıt defterine erişim iznine sahip gerektirecek şekilde gerekli olmadığını karar verirseniz, kayıt defterini okuma iznine assert.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="ee3ec-117">Bu durumda, bu arayanlar olmadan izni bunu onaylanacak kitaplığı için uygun olan **RegistryPermission** kitaplığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="ee3ec-118">Onaylama işlemi, yalnızca aynı türde sürülen ve bir aşağı akış çağıran tarafından talep izninizin olup olmadığını ve istenilen izni sürülen izin kümesini ise yığın ilerlemesi etkiler.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="ee3ec-119">Örneğin, assert, **FileIOPermission** C sürücüsünde ve bir aşağı akış isteğe bağlı tüm dosyaları okumak için yapılan **FileIOPermission** C:\Temp klasöründeki dosyaları okumak için onaylama yığın ilerlemesi; etkileyebilir Ancak, talep için ise **FileIOPermission** C sürücüsü yazmak için onay hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="ee3ec-120">Onaylar gerçekleştirmek için kodunuzu sunduğundan hem iznine sahip olmanız ve <xref:System.Security.Permissions.SecurityPermission> onaylar yapma hakkı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="ee3ec-121">Kodunuzu verilmediği bir izin assert rağmen onaylama işlemi başarılı şekilde neden olabilecek önce güvenlik denetimi başarısız olacağı için onaylama durum olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="ee3ec-122">Aşağıdaki çizimde kullandığınızda ne olacağını gösterir **Assert**.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="ee3ec-123">Aşağıdaki deyimleri derlemeler A, B, C, E ve F ve P1 ve P1A iki izinleri hakkında doğru olduğunu varsayın:</span><span class="sxs-lookup"><span data-stu-id="ee3ec-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="ee3ec-124">P1A C sürücüsünde .txt dosyaları okuma hakkı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="ee3ec-125">P1 C sürücüsündeki tüm dosyaları okuma hakkı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="ee3ec-126">P1A ve P1 olan her ikisi de **FileIOPermission** türleri ve P1A P1, bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="ee3ec-127">Derlemeleri E ve F P1A izin verildi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="ee3ec-128">Derleme C P1 izin verildi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="ee3ec-129">Derlemeleri A ve B P1 ne P1A izinleri verildi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="ee3ec-130">Yöntemi bir A derlemesinde bulunan, Yöntem B derleme B ve benzeri yer alır.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 <span data-ttu-id="ee3ec-131">![](../../../docs/framework/misc/media/assert.gif "Assert")</span><span class="sxs-lookup"><span data-stu-id="ee3ec-131">![](../../../docs/framework/misc/media/assert.gif "assert")</span></span>  
<span data-ttu-id="ee3ec-132">Assert kullanma</span><span class="sxs-lookup"><span data-stu-id="ee3ec-132">Using Assert</span></span>  
  
 <span data-ttu-id="ee3ec-133">Bu senaryo, yöntem A çağrıları B, B çağrıları C, C çağrıları E ve E çağrıları F'ye yöntemi C C sürücüsü (izni P1) dosyalarda okuma izni ve .txt dosyaları (izin P1A) C sürücüsünde okuma yöntemi E taleplerini izni onaylar.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="ee3ec-134">F'nde isteğe çalışma zamanında karşılaşıldığında, C C'ın onaylama nerede bulunduğundan, izinlerini incelemek için yığın ilerlemesi geçer şekilde yığın ilerlemesi F, tüm arayanlar izinlerini denetlemek için gerçekleştirilen E. E ile başlayan P1A izin verildi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="ee3ec-135">Talep edilen izni (P1A) bir alt kümesini sürülen izni (P1) olduğundan, yığın ilerlemesi durur ve güvenlik denetimi otomatik olarak başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="ee3ec-136">A ve B P1A izni verilmemiş bu derlemeler önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="ee3ec-137">P1 sunduğundan tarafından yöntemi C arayanlar bu kaynağa erişim izni verilmemiş olsa bile onun arayanlar P1 tarafından korunan kaynak erişebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="ee3ec-138">Bir sınıf kitaplığı tasarlayın ve bir sınıf korunan bir kaynağa erişir, çoğu durumda, sınıfın Arayanların uygun izinlere sahip gerektiren bir güvenlik isteğe bağlı oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="ee3ec-139">Sınıfı için bir işlem ardından gerçekleştirirse, kendi arayanlar çoğunu bildiğiniz izni olmaz ve kodunuzun çağırması bu arayanlara izin vererek sorumluluğunu yapılacak istekli olup olmadığını çağırarak izin assert **Assert** kodu işlemini temsil eden bir izni nesnesi üzerinde yöntemi gerçekleştirme.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="ee3ec-140">Kullanarak **Assert** bu yolla bunu normal olarak yapamadı sağlar arayanlar kodunuzu çağırın.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="ee3ec-141">Bu nedenle, bir izin assert, bileşeniniz kötüye kullanımını önlemek için önceden uygun güvenlik denetimleri gerçekleştirmek üzere emin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="ee3ec-142">Örneğin, yüksek oranda güvenilir kitaplığı sınıfınız dosyalarını siler bir yöntem olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="ee3ec-143">Dosya bir yönetilmeyen Win32 işlevini çağırarak erişir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="ee3ec-144">Çağıran, kodun çağırır **silmek** silinecek, dosya adına geçirerek yöntemini C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="ee3ec-145">İçinde **silmek** yöntemi, kodunuzu oluşturur bir <xref:System.Security.Permissions.FileIOPermission> yazma erişimi için C:\Test.txt temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="ee3ec-146">(Yazma erişimi bir dosyayı silmek için gereklidir.) Sonra kodunuzu çağırarak kesinlik temelli güvenliği onay çağırır **FileIOPermission** nesnenin **talep** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="ee3ec-147">Çağrı yığınında arayanlar biri bu izne sahip değilse bir <xref:System.Security.SecurityException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="ee3ec-148">Hiçbir özel durum varsa, tüm arayanlar C:\Test.txt erişim hakkı olduğunu bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="ee3ec-149">Düşündüğünüz olduğundan, arayanlar çoğunu yönetilmeyen kod erişim iznine sahip olmaz, kodunuzu daha sonra oluşturur bir <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kodu çağırma hakkı temsil eder ve nesnenin çağrıları nesne **Assert** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="ee3ec-150">Son olarak, C:\Text.txt silmek için yönetilmeyen Win32 işlevini çağırır ve çağırana denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ee3ec-151">Kodunuzu onaylar kodunuzun başka bir kodla ettiği taraf olduğunu izni tarafından korunan bir kaynağa erişmek için kullanıldığı durumlarda kullanmadığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="ee3ec-152">Örneğin, adında bir parametre olarak çağıran tarafından belirtilen bir dosyaya yazar kodda, değil assert **FileIOPermission** kodunuzu bir üçüncü taraf tarafından kötüye açık olduğundan dosyalara yazma için.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="ee3ec-153">Kesinlik temelli güvenliği sözdizimini kullandığınızda çağırma **Assert** yöntemi aynı yöntemi birden çok izinlerde durum bir güvenlik özel durumu neden olur.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="ee3ec-154">Bunun yerine, oluşturmalısınız bir **PermissionSet** nesne, istediğiniz çağırma ve ardından çağırmak için tek tek izinleri geçirmek **Assert** yöntemi **PermissionSet** nesne.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="ee3ec-155">Çağırabilirsiniz **Assert** yöntemi kez bildirimsel güvenliği sözdizimini kullandığınızda'den fazla.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="ee3ec-156">Aşağıdaki örnek, bildirim temelli söz dizimini gösterir, kullanarak geçersiz kılma güvenlik denetimleri için **Assert** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="ee3ec-157">Dikkat **FileIOPermissionAttribute** sözdizimi iki değerleri alır: bir <xref:System.Security.Permissions.SecurityAction> numaralandırma ve dosya veya iznine sahip olduğu verilebilmesi için dizin konumu.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="ee3ec-158">Çağrı **Assert** erişmek için talepleri neden `C:\Log.txt` arayanlar dosyaya erişim izni için denetlenmez olsa bile, başarılı olması için.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="ee3ec-159">Kullanarak geçersiz kılma güvenlik denetimleri için aşağıdaki kod parçası kesinlik temelli sözdizimi show **Assert** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="ee3ec-160">Bu örnekte, bir örneğini **FileIOPermission** nesne bildirildi.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="ee3ec-161">Kurucusu geçirilen **FileIOPermissionAccess.AllAccess** erişimine izin verilir, türünü tanımlamak için dosyanın konumunu tanımlayan bir dize tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="ee3ec-162">Bir kez **FileIOPermission** nesne tanımlanır, yalnızca çağırmanız gerekir, **Assert** güvenlik denetimi geçersiz kılmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ee3ec-163">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ee3ec-163">See Also</span></span>  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [<span data-ttu-id="ee3ec-164">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ee3ec-164">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="ee3ec-165">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="ee3ec-165">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
