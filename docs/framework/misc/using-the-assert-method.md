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
# <a name="using-the-assert-method"></a><span data-ttu-id="58a6d-102">Onay Yöntemini Kullanma</span><span class="sxs-lookup"><span data-stu-id="58a6d-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="58a6d-103"><xref:System.Security.CodeAccessPermission.Assert%2A>kod erişim izni sınıflarında ve sınıfta çağrılabilen bir yöntemdir. <xref:System.Security.PermissionSet></span><span class="sxs-lookup"><span data-stu-id="58a6d-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="58a6d-104">Kodunuzun (ve alt akış arayanların) kodunuzun yapmasına izin verdiği ancak arayanların yapma izni olmayan eylemleri gerçekleştirmesini etkinleştirmek için **Assert'ı** kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="58a6d-105">Güvenlik iddiası, çalışma zamanının güvenlik denetimi sırasında gerçekleştirdiği normal işlemi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="58a6d-106">İzin aldığınızda, güvenlik sistemine, öne edilen izin için kodunuzu arayanlara denetlememelerini söyler.</span><span class="sxs-lookup"><span data-stu-id="58a6d-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="58a6d-107">Güvenlik açıklarını açabildikleri ve güvenlik kısıtlamalarını zorlamak için çalışma zamanı mekanizmasını zayıflatabilecekleri için iddiaları dikkatle kullanın.</span><span class="sxs-lookup"><span data-stu-id="58a6d-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="58a6d-108">İddialar, kitaplığın yönetilmeyen koda çağrı yaptığı veya kitaplığın kullanım amacıyla açıkça ilişkili olmayan bir izin gerektiren bir arama yaptığı durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="58a6d-109">Örneğin, yönetilmeyen koda çağıran tüm yönetilen kod, **Yönetilmeyen Kod** bayrağı belirtilen **SecurityPermission'a** sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="58a6d-110">Yerel intranetten indirilen kod gibi yerel bilgisayardan kaynaklanamayan kod, varsayılan olarak bu izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="58a6d-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="58a6d-111">Bu nedenle, yerel intranetten indirilen kodun yönetilmeyen kod kullanan bir kitaplığı arayabilmesi için, kitaplık tarafından öne edilen izne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="58a6d-112">Ayrıca, bazı kitaplıklar arayanlar için görünmeyen ve özel izinler gerektiren aramalar yapabilir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="58a6d-113">Ayrıca, kodunuzun bir kaynağa arayanlardan tamamen gizli bir şekilde eriştiği durumlarda da iddiaları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="58a6d-114">Örneğin, kitaplığınizin bir veritabanından bilgi edindiğini, ancak işlemde bilgisayar kayıt defterindeki bilgileri de okuduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="58a6d-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="58a6d-115">Kitaplığınızı kullanan geliştiricilerin kaynağınıza erişimi olmadığından, kodlarınızı kullanmak için **Registry Permission** gerektirdiğini bilmelerinin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="58a6d-116">Bu durumda, kodunuzu arayanların kayıt defterine erişim iznine sahip olmasını gerektirmenin makul veya gerekli olmadığına karar verirseniz, kayıt defterini okumak için izin verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="58a6d-117">Bu durumda, **Kayıt Defteri İzni** olmayan arayanların kitaplığı kullanabilmesi için kitaplığın izin belgesini belirlemesi uygundur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="58a6d-118">İddia, yalnızca ileri edilen izin ve alt akım arayan tarafından talep edilen izin aynı türdeyse ve istenen izin talep edilen iznin bir alt kümesiyse yığın yürüyüşünü etkiler.</span><span class="sxs-lookup"><span data-stu-id="58a6d-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="58a6d-119">Örneğin, C sürücüsündeki tüm dosyaları okumak için **FileIOPermission'u** iddia ederseniz ve **FileIOPermission'un** C:\Temp'taki dosyaları okuması için bir aşağı akış talebi yapılırsa, öne etme yığın yürüyüşünü etkileyebilir; ancak, talep **FileIOPermission** C sürücüsüne yazmak için olsaydı, iddia hiçbir etkisi olurdu.</span><span class="sxs-lookup"><span data-stu-id="58a6d-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="58a6d-120">İddiaları gerçekleştirmek için, kodunuz hem iddia ettiğiniz izin hem <xref:System.Security.Permissions.SecurityPermission> de öne etme hakkını temsil eden izni verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="58a6d-121">Kodunuzu verilmediği ne kadar izin verebilirsiniz, ancak iddia başarılı olmasına neden olabilir önce güvenlik denetimi başarısız olacağını, çünkü iddia anlamsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="58a6d-122">Aşağıdaki **resimde, Assert'ı**kullandığınızda neler olduğunu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="58a6d-123">A, B, C, E ve F derlemeleri ve P1 ve P1A olmak üzere iki izin hakkında aşağıdaki ifadelerin doğru olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="58a6d-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="58a6d-124">P1A, C sürücüsünde .txt dosyalarını okuma hakkını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58a6d-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="58a6d-125">P1, C sürücüsündeki tüm dosyaları okuma hakkını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58a6d-125">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="58a6d-126">P1A ve P1 her ikisi de **FileIOPermission** türleridir ve P1A P1'in bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="58a6d-127">E ve F derlemelerine P1A izni verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="58a6d-128">C derlemesi P1 izni almıştır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-128">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="58a6d-129">A ve B derlemelerine ne P1 ne de P1A izinleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="58a6d-130">Yöntem A derlemesinde, B metodu B derlemesinde ve benzeri şekillerde bulunur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Assert yöntemi derlemelerini gösteren diyagram.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="58a6d-132">Bu senaryoda, Yöntem A Çağrıları B, B C, C çağrıları E çağırır ve E F. Yöntem C çağırır C sürücüsü (izin P1) dosyaları okumak için izin iddia ve yöntem E C sürücü (izin P1A) üzerinde .txt dosyaları okumak için izin ister.</span><span class="sxs-lookup"><span data-stu-id="58a6d-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="58a6d-133">Çalışma zamanında F'de taleple karşılaşıldığında, E. E ile başlayan F'nin tüm arayanların izinlerini kontrol etmek için bir yığın yürüyüşü gerçekleştirilir, bu nedenle yığın yürümesi C'nin iddiasının bulunduğu C izinlerini incelemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="58a6d-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="58a6d-134">İstenen izin (P1A) iddia edilen iznin (P1) bir alt kümesi olduğundan, yığın yürümesi durur ve güvenlik denetimi otomatik olarak başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="58a6d-135">A ve B derlemelerine P1A izni verilmemesi önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="58a6d-136">P1'i öne sürerek, Yöntem C, arayanlara bu kaynağa erişim izni verilmese bile, arayanların P1 tarafından korunan kaynağa erişebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="58a6d-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="58a6d-137">Bir sınıf kitaplığı tasarlarsanız ve bir sınıf korumalı bir kaynağa erişiyorsa, çoğu durumda sınıfın arayanların uygun izne sahip olması gereken bir güvenlik talebi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="58a6d-138">Sınıf daha sonra arayanların çoğunun izni olmayacağını bildiğiniz bir işlem gerçekleştirirse ve bu arayanların kodunuzu aramasına izin verme sorumluluğunu üstlenmek istiyorsanız, kodun gerçekleştirdiği işlemi temsil eden bir izin nesnesi üzerinde **Assert** yöntemini çağırarak izni nizi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="58a6d-139">**Assert'ı** bu şekilde kullanmak, normalde bunu yapamayan arayanların kodunuzu aramasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="58a6d-140">Bu nedenle, bir izin verirseniz, bileşeninizin kötüye kullanılmasını önlemek için önceden uygun güvenlik denetimlerini yaptığınızdan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="58a6d-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="58a6d-141">Örneğin, çok güvenilen kitaplık sınıfınızın dosyaları silen bir yöntemi olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="58a6d-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="58a6d-142">Yönetilmeyen bir Win32 işlevini çağırarak dosyaya erişir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="58a6d-143">Arayan, silinecek dosyanın adını geçerek kodunuzun **Sil** yöntemini çağırır, C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="58a6d-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="58a6d-144">**Sil** yöntemi içinde, kodunuz <xref:System.Security.Permissions.FileIOPermission> C:\Test.txt'ye yazma erişimini temsil eden bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="58a6d-145">(Bir dosyayı silmek için yazma erişimi gereklidir.) Ardından **kodunuz, FileIOPermission** nesnesinin **Talep** yöntemini arayarak zorunlu bir güvenlik denetimi çağırır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="58a6d-146">Arama yığınındaki arayanlardan biri bu izne sahip <xref:System.Security.SecurityException> değilse, bir atılmıştır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="58a6d-147">Özel durum atılırsa, tüm arayanların C:\Test.txt'ye erişme hakkına sahip olduğunu bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="58a6d-148">Arayanlarınızın çoğunun yönetilmeyen koda erişmek için izni olmayacağını düşünüyorsanız, kodunuz <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kodu arama hakkını temsil eden bir nesne oluşturur ve nesnenin **Assert** yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="58a6d-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="58a6d-149">Son olarak, C:\Text.txt'yi silmek için yönetilmeyen Win32 işlevini çağırır ve denetimi arayana döndürür.</span><span class="sxs-lookup"><span data-stu-id="58a6d-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="58a6d-150">Kodunuzu iddia ettiğiniz izinle korunan bir kaynağa erişmek için başka kod tarafından kullanılabildiği durumlarda kodunuzu öne etme dekullanmadığından emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="58a6d-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="58a6d-151">Örneğin, adı arayan tarafından parametre olarak belirtilen bir dosyaya yazan kodda, kodunuz üçüncü bir tarafça kötüye kullanılmaya açık olduğundan Dosyalara yazma için **FileIOPermission'u** öne sürmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="58a6d-152">Zorunlu güvenlik sözdizimini kullandığınızda, aynı yöntemde birden çok izinde **Assert** yöntemini çağırmak bir güvenlik özel durum atılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="58a6d-153">Bunun yerine, bir **PermissionSet** nesnesi oluşturmalı, çağırmak istediğiniz tek tek izinleri geçirmeli ve ardından **PermissionSet** nesnesindeki **Assert** yöntemini aramalısınız.</span><span class="sxs-lookup"><span data-stu-id="58a6d-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="58a6d-154">Bildirimsel güvenlik sözdizimini **kullandığınızda, Assert** yöntemini birden çok kez arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="58a6d-155">Aşağıdaki örnek, **Assert** yöntemini kullanarak güvenlik denetimlerini geçersiz kılmak için bildirimsel sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="58a6d-156">**FileIOPermissionAttribute** sözdiziminin iki değer <xref:System.Security.Permissions.SecurityAction> aldığına dikkat edin: numaralandırma ve dosyanın veya iznin bulunduğu yer ve izin verilecek.</span><span class="sxs-lookup"><span data-stu-id="58a6d-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="58a6d-157">İsteklilerin **Assert** dosyaya erişmek `C:\Log.txt` için izin için denetlenmemesine rağmen, Assert araması erişim taleplerinin başarılı olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="58a6d-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="58a6d-158">Aşağıdaki kod **parçaları, Assert** yöntemini kullanarak güvenlik denetimlerini geçersiz kılmak için zorunlu sözdizimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="58a6d-159">Bu örnekte, **FileIOPermission** nesnesinin bir örneği bildirilir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="58a6d-160">Onun oluşturucu **fileioPermissionAccess.AllAccess** izin verilen erişim türünü tanımlamak için geçilir, ardından dosyanın konumunu açıklayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="58a6d-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="58a6d-161">**FileIOPermission** nesnesi tanımlandıktan sonra, güvenlik denetimini geçersiz kılmak için yalnızca **Assert** yöntemini aramanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="58a6d-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="58a6d-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58a6d-162">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="58a6d-163">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="58a6d-163">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="58a6d-164">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="58a6d-164">Code Access Security</span></span>](code-access-security.md)
