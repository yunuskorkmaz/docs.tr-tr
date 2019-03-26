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
ms.openlocfilehash: 5799ab8e827305fca565064a0ae7290c6c19eb01
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463013"
---
# <a name="using-the-assert-method"></a><span data-ttu-id="efd34-102">Onay Yöntemini Kullanma</span><span class="sxs-lookup"><span data-stu-id="efd34-102">Using the Assert Method</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <span data-ttu-id="efd34-103"><xref:System.Security.CodeAccessPermission.Assert%2A> kod erişim izni sınıflarında çağrılabilen ve üzerinde bir yöntem <xref:System.Security.PermissionSet> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="efd34-103"><xref:System.Security.CodeAccessPermission.Assert%2A> is a method that can be called on code access permission classes and on the <xref:System.Security.PermissionSet> class.</span></span> <span data-ttu-id="efd34-104">Kullanabileceğiniz **Assert** kodunuzu uygun izinlere sahip eylemler ancak çağıranlarını gerçekleştirmek, kodu (ve aşağı akış arayanlar) etkinleştirmek için izniniz olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="efd34-104">You can use **Assert** to enable your code (and downstream callers) to perform actions that your code has permission to do but its callers might not have permission to do.</span></span> <span data-ttu-id="efd34-105">Güvenlik onaylama işlemi, bir güvenlik denetimi sırasında çalışma zamanı yapar normal işlem değiştirir.</span><span class="sxs-lookup"><span data-stu-id="efd34-105">A security assertion changes the normal process that the runtime performs during a security check.</span></span> <span data-ttu-id="efd34-106">İzin onayı, kodunuzun olarak onaylanan izin için çağıranlar denetlemek için güvenlik sistemi söyler.</span><span class="sxs-lookup"><span data-stu-id="efd34-106">When you assert a permission, it tells the security system not to check the callers of your code for the asserted permission.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="efd34-107">Güvenlik açıkları açın ve güvenlik kısıtlamaları zorunlu tutmak için çalışma zamanının mekanizması olumsuz onaylar dikkatle kullanın.</span><span class="sxs-lookup"><span data-stu-id="efd34-107">Use assertions carefully because they can open security holes and undermine the runtime's mechanism for enforcing security restrictions.</span></span>  
  
 <span data-ttu-id="efd34-108">Onaylar, Kitaplık'ın yönetilmeyen koda çağıran veya kitaplığın kullanım amacını açıkça ilgili olmayan bir izni gerektiren çağrıda durumlarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="efd34-108">Assertions are useful in situations in which a library calls into unmanaged code or makes a call that requires a permission that is not obviously related to the library's intended use.</span></span> <span data-ttu-id="efd34-109">Örneğin, tüm yönetilen yönetilmeyen koda çağrı olmalıdır kod **SecurityPermission** ile **UnmanagedCode** bayrağı belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="efd34-109">For example, all managed code that calls into unmanaged code must have **SecurityPermission** with the **UnmanagedCode** flag specified.</span></span> <span data-ttu-id="efd34-110">Varsayılan olarak yerel bilgisayardan, yerel intranet üzerinden indirilen kod gibi kaynaklanmayan kod bu izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="efd34-110">Code that does not originate from the local computer, such as code that is downloaded from the local intranet, will not be granted this permission by default.</span></span> <span data-ttu-id="efd34-111">Bu nedenle, çağırma kullanan yönetilmeyen kod kitaplığı için yerel intranet üzerinden indirilen kod için sırada bu kitaplığı tarafından onaylanan iznine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efd34-111">Therefore, in order for code that is downloaded from the local intranet to be able to call a library that uses unmanaged code, it must have the permission asserted by the library.</span></span> <span data-ttu-id="efd34-112">Ayrıca, bazı kitaplıklar arayanlara görünmeyen ve özel izinleri gerektiren çağrıları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="efd34-112">Additionally, some libraries might make calls that are unseen to callers and require special permissions.</span></span>  
  
 <span data-ttu-id="efd34-113">Onaylamalar içinde ve kodunuzu tamamen gizli bir şekilde bir kaynak çağrı yapanlardan eriştiği durumlarda de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efd34-113">You can also use assertions in situations in which your code accesses a resource in a way that is completely hidden from callers.</span></span> <span data-ttu-id="efd34-114">Örneğin, kitaplığınızı veritabanından bilgi edinme, ancak işlem sırasında ayrıca bilgisayar kayıt defterinden bilgilerini okur varsayalım.</span><span class="sxs-lookup"><span data-stu-id="efd34-114">For example, suppose your library acquires information from a database, but in the process also reads information from the computer registry.</span></span> <span data-ttu-id="efd34-115">Kitaplığınızı kullanan geliştiriciler kaynağınıza erişimi olmadığından, kodlarını gerektirdiğini olduğunu bilmesinin imkanı sahiptirler **RegistryPermission** kodunuzu kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="efd34-115">Because developers using your library do not have access to your source, they have no way of knowing that their code requires **RegistryPermission** in order to use your code.</span></span> <span data-ttu-id="efd34-116">Bu durumda, makul veya kodunuzun çağıranlar kayıt defterine erişim izni olmasını gerektiren için gerekli olmadığını karar verirseniz, kayıt defterini okuma izni onay.</span><span class="sxs-lookup"><span data-stu-id="efd34-116">In this case, if you decide that it is not reasonable or necessary to require that callers of your code have permission to access the registry, you can assert permission for reading the registry.</span></span> <span data-ttu-id="efd34-117">Bu durumda, Arayanların olmadan bunu izin onay kitaplık için uygun olan **RegistryPermission** kitaplığını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efd34-117">In this situation, it is appropriate for the library to assert the permission so that callers without **RegistryPermission** can use the library.</span></span>  
  
 <span data-ttu-id="efd34-118">Onaylama işlemi, yalnızca aynı tür olarak onaylanan ve bir aşağı akış çağıran tarafından talep edilen bir izninizin olması durumunda ve talep edilen izni olarak onaylanan izin kümesini ise yığın ilerlemesi etkiler.</span><span class="sxs-lookup"><span data-stu-id="efd34-118">The assertion affects the stack walk only if the asserted permission and a permission demanded by a downstream caller are of the same type and if the demanded permission is a subset of the asserted permission.</span></span> <span data-ttu-id="efd34-119">Örneğin, onaylama, **FileIOPermission** C sürücüsü ve aşağı akış isteğe bağlı tüm dosyaları okumak için yapıldığı **FileIOPermission** C:\Temp klasöründeki dosyaları okumak için yığın ilerlemesi; onaylama işlemi etkileyebilir Ancak, talep için ise **FileIOPermission** C sürücüsüne yazmak için onay hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="efd34-119">For example, if you assert **FileIOPermission** to read all files on the C drive, and a downstream demand is made for **FileIOPermission** to read files in C:\Temp, the assertion could affect the stack walk; however, if the demand was for **FileIOPermission** to write to the C drive, the assertion would have no effect.</span></span>  
  
 <span data-ttu-id="efd34-120">Onaylamalar gerçekleştirmek için kodunuzu sunduğundan hem iznine sahip olmanız gerekir ve <xref:System.Security.Permissions.SecurityPermission> onaylar yapma hakkı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="efd34-120">To perform assertions, your code must be granted both the permission you are asserting and the <xref:System.Security.Permissions.SecurityPermission> that represents the right to make assertions.</span></span> <span data-ttu-id="efd34-121">Kodunuzu verilmedi bir izin onay olsa da, onaylama işlemi başarılı olması için neden olabilecek önce güvenlik denetimi başarısız olacağı için onaylama anlamsız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="efd34-121">Although you could assert a permission that your code has not been granted, the assertion would be pointless because the security check would fail before the assertion could cause it to succeed.</span></span>  
  
 <span data-ttu-id="efd34-122">Aşağıdaki gösterimde kullandığınızda neler **Assert**.</span><span class="sxs-lookup"><span data-stu-id="efd34-122">The following illustration shows what happens when you use **Assert**.</span></span> <span data-ttu-id="efd34-123">Aşağıdaki deyimleri derlemeleri A, B, C, E ve F ve P1 ve P1A iki izinleri hakkında doğru olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="efd34-123">Assume that the following statements are true about assemblies A, B, C, E, and F, and two permissions, P1 and P1A:</span></span>  
  
-   <span data-ttu-id="efd34-124">P1A C sürücüsündeki .txt dosyaları okuma hakkı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="efd34-124">P1A represents the right to read .txt files on the C drive.</span></span>  
  
-   <span data-ttu-id="efd34-125">P1 C sürücüsündeki tüm dosyaları okuma hakkı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="efd34-125">P1 represents the right to read all files on the C drive.</span></span>  
  
-   <span data-ttu-id="efd34-126">P1A ve P1 olan hem de **FileIOPermission** türleri ve P1A P1 özelliklerinin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="efd34-126">P1A and P1 are both **FileIOPermission** types, and P1A is a subset of P1.</span></span>  
  
-   <span data-ttu-id="efd34-127">Derlemeleri E ve F P1A izin vermiş olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="efd34-127">Assemblies E and F have been granted P1A permission.</span></span>  
  
-   <span data-ttu-id="efd34-128">Derleme C P1 izin verildi.</span><span class="sxs-lookup"><span data-stu-id="efd34-128">Assembly C has been granted P1 permission.</span></span>  
  
-   <span data-ttu-id="efd34-129">A ve B derlemeleri P1 ne P1A izinleri verilmiş.</span><span class="sxs-lookup"><span data-stu-id="efd34-129">Assemblies A and B have been granted neither P1 nor P1A permissions.</span></span>  
  
-   <span data-ttu-id="efd34-130">Yöntemi bir bir derlemede yer alan, Yöntem B derleme B ve benzeri yer alır.</span><span class="sxs-lookup"><span data-stu-id="efd34-130">Method A is contained in assembly A, method B is contained in assembly B, and so on.</span></span>  
  
 ![Assert yöntemi derlemeleri gösteren diyagram.](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 <span data-ttu-id="efd34-132">Bu senaryo, yöntemi bir çağrıları B, C B çağrıları, C çağrı E ve E çağrılar F. yöntemi C (izin P1) C sürücüsündeki dosyaları okuma izni ve (izni P1A) C sürücüsündeki .txt dosyaları okumak için yöntem E taleplerini izni onaylar.</span><span class="sxs-lookup"><span data-stu-id="efd34-132">In this scenario, method A calls B, B calls C, C calls E, and E calls F. Method C asserts permission to read files on the C drive (permission P1), and method E demands permission to read .txt files on the C drive (permission P1A).</span></span> <span data-ttu-id="efd34-133">Talep f çalışma zamanında karşılaşıldığında, C, C'ın onaylama nerede bulunduğundan izinlerini incelemek için yığın ilerlemesi geçer şekilde yığın ilerlemesi f, tüm çağıranların izinlerini kontrol etmek için gerçekleştirilir E. E başlangıç P1A izin verildi.</span><span class="sxs-lookup"><span data-stu-id="efd34-133">When the demand in F is encountered at run time, a stack walk is performed to check the permissions of all callers of F, starting with E. E has been granted P1A permission, so the stack walk proceeds to examine the permissions of C, where C's assertion is discovered.</span></span> <span data-ttu-id="efd34-134">Talep edilen izni (P1A) olarak onaylanan izni (P1) bir alt kümesi olduğundan, otomatik olarak yığın ilerlemesi durur ve güvenlik denetimi başarılı.</span><span class="sxs-lookup"><span data-stu-id="efd34-134">Because the demanded permission (P1A) is a subset of the asserted permission (P1), the stack walk stops and the security check automatically succeeds.</span></span> <span data-ttu-id="efd34-135">A ve B P1A izni verilmemiş bu derlemeler önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="efd34-135">It does not matter that assemblies A and B have not been granted permission P1A.</span></span> <span data-ttu-id="efd34-136">P1 sunduğundan tarafından C yöntemi çağıranlar, bu kaynağa erişim izni verilmemiş bile çağıranlarını P1 tarafından korunan kaynak erişebilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="efd34-136">By asserting P1, method C ensures that its callers can access the resource protected by P1, even if the callers have not been granted permission to access that resource.</span></span>  
  
 <span data-ttu-id="efd34-137">Bir sınıf kitaplığı tasarlayın ve bir sınıf, korunan bir kaynağa erişir, çoğu durumda, sınıfın çağıranlar uygun izinlere sahip gerektiren bir güvenlik talebi oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="efd34-137">If you design a class library and a class accesses a protected resource, you should, in most cases, make a security demand requiring that the callers of the class have the appropriate permission.</span></span> <span data-ttu-id="efd34-138">Sınıfı için bir işlem gerçekleştirir, hangi çağıranlarını çoğunu tanıdığınız izni olmaz ve kodunuzun çağrı bu arayanlara izin vererek sorumluluğunu yararlanmak istekliyse çağırarak izin onay **Assert** işlemini temsil eden bir izin nesnesi üzerinde yöntemi, şu kod gerçekleştiriyor.</span><span class="sxs-lookup"><span data-stu-id="efd34-138">If the class then performs an operation for which you know most of its callers will not have permission, and if you are willing to take the responsibility for letting these callers call your code, you can assert the permission by calling the **Assert** method on a permission object that represents the operation the code is performing.</span></span> <span data-ttu-id="efd34-139">Kullanarak **Assert** bu yolla bunu normal olarak yapamadı sağlar çağıranlar kodunuzu çağırın.</span><span class="sxs-lookup"><span data-stu-id="efd34-139">Using **Assert** in this way lets callers that normally could not do so call your code.</span></span> <span data-ttu-id="efd34-140">Bu nedenle, bir izin assert, bileşeninizin kötüye kullanımını engeller önlemek için önceden uygun güvenlik denetimleri gerçekleştirmek emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="efd34-140">Therefore, if you assert a permission, you should be sure to perform appropriate security checks beforehand to prevent your component from being misused.</span></span>  
  
 <span data-ttu-id="efd34-141">Örneğin, yüksek derecede güvenilen kitaplığı sınıfınıza dosyaları silen bir yöntem olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="efd34-141">For example, suppose your highly trusted library class has a method that deletes files.</span></span> <span data-ttu-id="efd34-142">Dosya, yönetilmeyen bir Win32 işlevini çağırarak erişir.</span><span class="sxs-lookup"><span data-stu-id="efd34-142">It accesses the file by calling an unmanaged Win32 function.</span></span> <span data-ttu-id="efd34-143">Çağıran kod çağırır **Sil** silinecek dosyanın adını geçirerek yöntemini C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="efd34-143">A caller invokes your code's **Delete** method, passing in the name of the file to be deleted, C:\Test.txt.</span></span> <span data-ttu-id="efd34-144">İçinde **Sil** yöntemi, kod oluşturur bir <xref:System.Security.Permissions.FileIOPermission> yazma erişimi için C:\Test.txt temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="efd34-144">Within the **Delete** method, your code creates a <xref:System.Security.Permissions.FileIOPermission> object representing write access to C:\Test.txt.</span></span> <span data-ttu-id="efd34-145">(Bir dosyayı silmek için yazma erişimi gereklidir.) Sonra kodunuzu çağırarak zorunlu güvenlik denetimi çağırır **FileIOPermission** nesnenin **isteğe** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efd34-145">(Write access is required to delete a file.) Your code then invokes an imperative security check by calling the **FileIOPermission** object's **Demand** method.</span></span> <span data-ttu-id="efd34-146">Çağrı yığınında çağıranlar birini bu izne sahip değilse bir <xref:System.Security.SecurityException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="efd34-146">If one of the callers in the call stack does not have this permission, a <xref:System.Security.SecurityException> is thrown.</span></span> <span data-ttu-id="efd34-147">Hiçbir özel durum varsa, tüm çağıranların C:\Test.txt erişim hakkı olduğunu bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="efd34-147">If no exception is thrown, you know that all callers have the right to access C:\Test.txt.</span></span> <span data-ttu-id="efd34-148">Olduğuna inanıyorsanız, Arayanların çoğunu yönetilmeyen koda erişim iznine sahip olmaz, kodunuzu daha sonra oluşturur çünkü bir <xref:System.Security.Permissions.SecurityPermission> yönetilmeyen kod çağırmak için sağ temsil eder ve çağıran nesne **Assert** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efd34-148">Because you believe that most of your callers will not have permission to access unmanaged code, your code then creates a <xref:System.Security.Permissions.SecurityPermission> object that represents the right to call unmanaged code and calls the object's **Assert** method.</span></span> <span data-ttu-id="efd34-149">Son olarak, C:\Text.txt silmek için yönetilmeyen Win32 işlevini çağırır ve denetim çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="efd34-149">Finally, it calls the unmanaged Win32 function to delete C:\Text.txt and returns control to the caller.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="efd34-150">Kodunuzu onaylar burada kodunuzu başka kod tarafından sunduğundan izni tarafından korunan bir kaynağa erişmek için kullanılabilir durumda kullanmadığından emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="efd34-150">You must be sure that your code does not use assertions in situations where your code can be used by other code to access a resource that is protected by the permission you are asserting.</span></span> <span data-ttu-id="efd34-151">Örneğin, adında bir parametre olarak çağıran tarafından belirtilen bir dosyaya yazar kodunda, yok assert **FileIOPermission** kodunuzu bir üçüncü taraf tarafından kötüye açık olacağından, dosyalara yazma için.</span><span class="sxs-lookup"><span data-stu-id="efd34-151">For example, in code that writes to a file whose name is specified by the caller as a parameter, you would not assert the **FileIOPermission** for writing to files because your code would be open to misuse by a third party.</span></span>  
  
 <span data-ttu-id="efd34-152">Kesinlik temelli güvenlik sözdizimi kullandığınızda, çağırma **Assert** aynı yöntemi içinde birden fazla izinleri yöntemi, bir güvenlik özel durum oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="efd34-152">When you use the imperative security syntax, calling the **Assert** method on multiple permissions in the same method causes a security exception to be thrown.</span></span> <span data-ttu-id="efd34-153">Bunun yerine, oluşturacağınız bir **PermissionSet** nesne, istediğiniz çağırır ve ardından çağırmak için ayrı ayrı izinler geçirmek **Assert** yöntemi **PermissionSet** nesne.</span><span class="sxs-lookup"><span data-stu-id="efd34-153">Instead, you should create a **PermissionSet** object, pass it the individual permissions you want to invoke, and then call the **Assert** method on the **PermissionSet** object.</span></span> <span data-ttu-id="efd34-154">Çağırabilirsiniz **Assert** yöntemi daha fazla kez bildirim temelli güvenlik sözdizimi kullandığınızda.</span><span class="sxs-lookup"><span data-stu-id="efd34-154">You can call the **Assert** method more than once when you use the declarative security syntax.</span></span>  
  
 <span data-ttu-id="efd34-155">Kullanarak geçersiz kılma güvenlik denetimleri için aşağıdaki örnek, bildirim temelli söz dizimini gösterir. **Assert** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efd34-155">The following example shows declarative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="efd34-156">Dikkat **FileIOPermissionAttribute** söz dizimi iki değer alır: bir <xref:System.Security.Permissions.SecurityAction> numaralandırma ve dosya veya dizin izni olduğu verilecek konumu.</span><span class="sxs-lookup"><span data-stu-id="efd34-156">Notice that the **FileIOPermissionAttribute** syntax takes two values: a <xref:System.Security.Permissions.SecurityAction> enumeration and the location of the file or directory to which permission is to be granted.</span></span> <span data-ttu-id="efd34-157">Çağrı **Assert** erişmek için talepleri neden `C:\Log.txt` dosyaya erişim izni için çağıranlar alınmamış olsa da, başarılı olması için.</span><span class="sxs-lookup"><span data-stu-id="efd34-157">The call to **Assert** causes demands for access to `C:\Log.txt` to succeed, even though callers are not checked for permission to access the file.</span></span>  
  
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
  
 <span data-ttu-id="efd34-158">Kullanarak geçersiz kılma güvenlik denetimleri için aşağıdaki kod parçası kesinlik temelli sözdizimi show **Assert** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efd34-158">The following code fragments show imperative syntax for overriding security checks using the **Assert** method.</span></span> <span data-ttu-id="efd34-159">Bu örnekte, bir örneğini **FileIOPermission** nesne bildirilir.</span><span class="sxs-lookup"><span data-stu-id="efd34-159">In this example, an instance of the **FileIOPermission** object is declared.</span></span> <span data-ttu-id="efd34-160">Oluşturucusuna geçirilen **FileIOPermissionAccess.AllAccess** izin, erişim türünü tanımlamak için dosyanın konumunu tanımlayan bir dize tarafından izlenen.</span><span class="sxs-lookup"><span data-stu-id="efd34-160">Its constructor is passed **FileIOPermissionAccess.AllAccess** to define the type of access allowed, followed by a string describing the file's location.</span></span> <span data-ttu-id="efd34-161">Bir kez **FileIOPermission** nesne tanımlanır, yalnızca çağırmanız gerekir, **Assert** güvenlik denetimi geçersiz kılmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="efd34-161">Once the **FileIOPermission** object is defined, you only need to call its **Assert** method to override the security check.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="efd34-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="efd34-162">See also</span></span>
- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [<span data-ttu-id="efd34-163">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="efd34-163">Attributes</span></span>](../../../docs/standard/attributes/index.md)
- [<span data-ttu-id="efd34-164">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="efd34-164">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
