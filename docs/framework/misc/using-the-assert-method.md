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
# <a name="using-the-assert-method"></a><span data-ttu-id="48906-103">Onay Yöntemini Kullanma</span><span class="sxs-lookup"><span data-stu-id="48906-103">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="48906-104"><xref:System.Security.CodeAccessPermission.Assert%2A>, kod erişimi izin sınıflarında ve sınıfında çağrılabilecek bir yöntemdir <xref:System.Security.PermissionSet> .</span><span class="sxs-lookup"><span data-stu-id="48906-104"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="48906-105">Kodunuzun (ve aşağı akış çağıranlarının), kodunuzun gerçekleştirme iznine sahip olduğu, ancak çağıranlarının yapma izni olmayan eylemleri **gerçekleştirmesini sağlamak için onay kullanabilirsiniz.**</span><span class="sxs-lookup"><span data-stu-id="48906-105">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="48906-106">Güvenlik onayı, çalışma zamanının güvenlik denetimi sırasında gerçekleştirdiği normal işlemi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="48906-106">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="48906-107">Bir izin belirttiğinizde, güvenlik sistemine, onaylanan izin için kodunuzun çağıranlarını denetvermediğini söyler.</span><span class="sxs-lookup"><span data-stu-id="48906-107">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="48906-108">Güvenlik boşluklarını açabildiklerinden ve güvenlik kısıtlamalarını uygulamak için çalışma zamanının mekanizmasından daha az yer olabileceğinden onayları dikkatle kullanın.</span><span class="sxs-lookup"><span data-stu-id="48906-108">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="48906-109">Onaylamalar, kitaplığın yönetilmeyen koda çağrı yaptığı veya kitaplığın amaçlanan kullanımı için açıkça ilgili olmayan bir izin gerektiren bir çağrı yaptığı durumlarda faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="48906-109">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="48906-110">Örneğin, yönetilmeyen koda çağrı yapan tüm yönetilen kodların **UnmanagedCode** bayrağıyla **SecurityPermission** değeri olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="48906-110">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="48906-111">Yerel intranetten indirilen kod gibi yerel bilgisayardan kaynaklanmayan koda bu izin varsayılan olarak verilmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="48906-111">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="48906-112">Bu nedenle, yerel intranetten indirilen kodun yönetilmeyen kod kullanan bir kitaplığı çağırabilmesi için, kitaplık tarafından onaylanan izne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48906-112">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="48906-113">Ayrıca, bazı kitaplıklar arayanlara görünmeyen ve özel izinler gerektiren çağrılar yapabilir.</span><span class="sxs-lookup"><span data-stu-id="48906-113">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="48906-114">Ayrıca, kodunuzun bir kaynağa, çağıranlardan tamamen gizlenmiş bir şekilde eriştiği durumlarda onayları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48906-114">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="48906-115">Örneğin, kitaplığınızın bir veritabanından bilgi edindiğini varsayalım, ancak işlem içinde bilgisayar kayıt defterindeki bilgiler de okur.</span><span class="sxs-lookup"><span data-stu-id="48906-115">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="48906-116">Kitaplığınızı kullanan geliştiricilerin kaynağınıza erişimi olmadığından, kodunuzun kullanılabilmesi için kodunun **RegistryPermission** gerektirdiğini bilmenin bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="48906-116">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="48906-117">Bu durumda, kodunuzun çağıranlarının kayıt defterine erişim izni olmasını gerektirmek için makul veya gerekli olmadığına karar verirseniz, kayıt defterini okumak için izin onayı verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48906-117">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="48906-118">Bu durumda, kitaplığın, **RegistryPermission** olmayan çağıranların kitaplığı kullanabilmesi için izni onayı için uygun olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="48906-118">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="48906-119">Onaylama işlemi, yalnızca onaylanan izin ve bir aşağı akış çağıranı tarafından talep edilen izin aynı türde ise ve istenen izin, onaylanan iznin bir alt kümesi ise, yığın ilerleme durumunu etkiler.</span><span class="sxs-lookup"><span data-stu-id="48906-119">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="48906-120">Örneğin, C sürücüsündeki tüm dosyaları okumak için **Dosyaıişle görev** seçeneğini belirlerseniz ve C:\Temp dosyasındaki dosyaları **okumak için bir** aşağı akış talebi yapılırsa, onaylama işlemi yığın yürüme işlemini etkileyebilir; Ancak talep, C sürücüsüne yazmak üzere **Dosya** için gerekliyse, onay etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="48906-120">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="48906-121">Onaylama işlemleri gerçekleştirmek için, kodunuzun hem gerçekleştirdiğiniz izin hem de <xref:System.Security.Permissions.SecurityPermission> onaylama yapma hakkını temsil eden bir izni verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="48906-121">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="48906-122">Kodunuzun verilmemesine izin verseniz de, onaylama işleminin başarılı olabilmesi için güvenlik denetimi başarısız olacağından onaylama işlemi daha az olabilir.</span><span class="sxs-lookup"><span data-stu-id="48906-122">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="48906-123">Aşağıdaki çizimde, **onaylama**kullandığınızda ne olacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48906-123">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="48906-124">Aşağıdaki deyimlerin A, B, C, E ve F derlemeleri ve iki izin, P1 ve P1A için doğru olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="48906-124">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
- <span data-ttu-id="48906-125">P1A, C sürücüsündeki. txt dosyalarını okuma hakkını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48906-125">P1A represents the right to read .txt files on the C drive.</span></span>  
  
- <span data-ttu-id="48906-126">P1, C sürücüsündeki tüm dosyaları okuma hakkını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48906-126">P1 represents the right to read all files on the C drive.</span></span>  
  
- <span data-ttu-id="48906-127">P1A ve P1 her ikisi de **Dosya** türü ve P1A P1 'in bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="48906-127">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
- <span data-ttu-id="48906-128">E ve F derlemelerinin P1A izni verildi.</span><span class="sxs-lookup"><span data-stu-id="48906-128">Assemblies E and F have been granted P1A permission.</span></span>  
  
- <span data-ttu-id="48906-129">C derlemesine P1 izni verildi.</span><span class="sxs-lookup"><span data-stu-id="48906-129">Assembly C has been granted P1 permission.</span></span>  
  
- <span data-ttu-id="48906-130">A ve B bütünleştirilmiş kodlarına ne P1 ne de P1A izinleri verildi.</span><span class="sxs-lookup"><span data-stu-id="48906-130">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
- <span data-ttu-id="48906-131">A yöntemi a derlemesinde bulunur, B yöntemi B derlemesinde bulunur ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="48906-131">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Onaylama yöntemi derlemelerini gösteren diyagram.](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 <span data-ttu-id="48906-133">Bu senaryoda, A çağrısı B, B çağrı C, c ve d çağırır. Yöntem C, c sürücüsündeki (izin P1) dosyaları okumak için izin ve C sürücüsündeki. txt dosyalarını okumak için izin ister (izin P1A).</span><span class="sxs-lookup"><span data-stu-id="48906-133">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="48906-134">F 'deki talebe çalışma zamanında karşılaşıldığında, E. E ile başlayan tüm F çağıranlarının izinlerini denetlemek için bir yığın yürüme işlemi, P1A izni verdi ve bu sayede yığın ilerlemenizin, c 'nin onaylama işlemi nerede bulunur.</span><span class="sxs-lookup"><span data-stu-id="48906-134">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="48906-135">Talep edilen izin (P1A), onaylanan iznin (P1) bir alt kümesi olduğundan, yığın ilerleme durumunu ve güvenlik denetimi otomatik olarak başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="48906-135">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="48906-136">A ve B derlemelerinin izin P1A verilmediğinden bağımsız değildir.</span><span class="sxs-lookup"><span data-stu-id="48906-136">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="48906-137">, P1, bu kaynağa erişim izni verilmese bile, C yöntemi,, çağıranların P1 tarafından korunan kaynağa erişmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="48906-137">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="48906-138">Bir sınıf kitaplığı tasarlarsanız ve bir sınıf korunan kaynağa eriştiğinde, çoğu durumda, sınıfın çağıranlarının uygun izne sahip olmasını gerektiren bir güvenlik talebi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48906-138">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="48906-139">Sınıf daha sonra, arayanların çoğunu bildiğiniz bir işlem gerçekleştiriyorsa ve bu çağıranların kodunuzun çağrılmasını sağlamak için sorumluluğu almak istiyorsanız, kodun gerçekleştirdiği işlemi temsil eden bir izin nesnesi üzerinde **onaylama** yöntemini çağırarak izni belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48906-139">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="48906-140">Bu şekilde **onay kullanılması,** normalde, kodunuzu çağrı yapamayan çağıranlara izin verir.</span><span class="sxs-lookup"><span data-stu-id="48906-140">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="48906-141">Bu nedenle, bir izin belirtirseniz, bileşenin kötüye kullanılmasını engellemek için, önceden uygun güvenlik denetimleri gerçekleştirdiğinizden emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48906-141">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="48906-142">Örneğin, yüksek oranda güvenilen kitaplık sınıfınızın dosyaları silen bir yöntemi olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="48906-142">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="48906-143">Yönetilmeyen bir Win32 işlevini çağırarak dosyaya erişir.</span><span class="sxs-lookup"><span data-stu-id="48906-143">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="48906-144">Bir çağıran, kodunuzun **silme** yöntemini çağırır ve Silinecek dosyanın adını geçirerek C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="48906-144">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="48906-145">**Delete** yöntemi içinde, kodunuz <xref:System.Security.Permissions.FileIOPermission> C:\Test.txt yazma erişimini temsil eden bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48906-145">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="48906-146">(Bir dosyayı silmek için yazma erişimi gereklidir.) Kodunuz daha sonra, **Fileıişle görev** nesnesinin **talep** yöntemini çağırarak bir kesinlik güvenlik denetimini çağırır.</span><span class="sxs-lookup"><span data-stu-id="48906-146">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="48906-147">Çağrı yığınındaki çağıranların birinde bu izin yoksa, bir <xref:System.Security.SecurityException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="48906-147">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="48906-148">Hiçbir özel durum oluşursa, tüm Arayanların C:\Test.txt erişim hakkına sahip olduğunu bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48906-148">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="48906-149">Çağıranlarınızın çoğunun yönetilmeyen koda erişim izni olmadığından eminseniz, kodunuz, <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kodu çağırma ve nesnenin **onaylama** yöntemini çağırma hakkını temsil eden bir nesne oluşturur.</span><span class="sxs-lookup"><span data-stu-id="48906-149">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="48906-150">Son olarak, C:\Text.txt silmek için yönetilmeyen Win32 işlevini çağırır ve denetimi çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="48906-150">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="48906-151">Kodunuzun, yaptığınız izinlerle korunan bir kaynağa erişmek için kodunuzun diğer kod tarafından kullanılabileceği durumlarda onay kullanılmadığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48906-151">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="48906-152">Örneğin, adı çağıran tarafından bir parametre olarak belirtilen bir dosyaya yazan kodda, kodunuzun bir üçüncü taraf tarafından kötüye kullanılmasına açık olması nedeniyle dosyalara yazmak **için dosya** yazma işlemi yapmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="48906-152">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="48906-153">Zorunlu güvenlik sözdizimini kullandığınızda, aynı yöntemde birden çok izin üzerinde **onay yöntemi çağırmak** bir güvenlik özel durumunun oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="48906-153">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="48906-154">Bunun yerine, bir **PermissionSet** nesnesi oluşturmalı, çağırmak istediğiniz bireysel izinleri geçitirsiniz ve ardından **PermissionSet** nesnesi üzerinde **onaylama** yöntemini çağırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="48906-154">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="48906-155">Bildirim temelli güvenlik sözdizimini kullandığınızda **onay yöntemini birden** çok kez çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48906-155">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="48906-156">Aşağıdaki **örnekte, onay yöntemi kullanılarak** güvenlik denetimlerinin geçersiz kılınması için bildirime dayalı sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="48906-156">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="48906-157">**Filei, Missionattribute** sözdiziminin iki değer aldığını unutmayın: bir <xref:System.Security.Permissions.SecurityAction> numaralandırma ve izin verilecek dosyanın veya dizinin konumu.</span><span class="sxs-lookup"><span data-stu-id="48906-157">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="48906-158">Çağrıya **yapılan çağrı** , `C:\Log.txt` çağıranlar dosyaya erişmek için izin verilmediği halde, erişim taleplerini başarılı olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="48906-158">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="48906-159">Aşağıdaki kod **parçaları, onay yöntemini kullanarak** güvenlik denetimlerini geçersiz kılmak için zorunlu sözdizimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="48906-159">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="48906-160">Bu örnekte, **Fileıse görev** nesnesinin bir örneği bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="48906-160">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="48906-161">Oluşturucusunun, izin verilen erişim türünü ve ardından dosyanın konumunu açıklayan bir dize tarafından tanımlanması için **Fileımanmissionaccess. AllAccess** geçildi.</span><span class="sxs-lookup"><span data-stu-id="48906-161">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="48906-162">**Dosya görev** nesnesi tanımlandıktan sonra, güvenlik denetimini geçersiz kılmak Için yalnızca **onaylama** yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="48906-162">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48906-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48906-163">See also</span></span>

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="48906-164">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="48906-164">Attributes</span></span>](../../standard/attributes/index.md)
- [<span data-ttu-id="48906-165">Kod Erişimi Güvenliği</span><span class="sxs-lookup"><span data-stu-id="48906-165">Code Access Security</span></span>](code-access-security.md)
