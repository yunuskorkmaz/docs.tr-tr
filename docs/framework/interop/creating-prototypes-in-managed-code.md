---
title: Yönetilen Kodda Prototipler Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8d51149c01b4c8018609ca9313cc4eea2afbb5a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946568"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="c9557-102">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9557-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="c9557-103">Bu konu, yönetilmeyen işlevlere nasıl erişmekte olduğunu ve yönetilen kodda Yöntem tanımına açıklama eklenen çeşitli öznitelik alanlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="c9557-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="c9557-104">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="c9557-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="c9557-105">Yönetilen koddan yönetilmeyen bir DLL işlevine erişebilmek için önce işlevin adını ve onu dışarı aktaran DLL 'nin adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c9557-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="c9557-106">Bu bilgilerle, DLL 'de uygulanan yönetilmeyen bir işlev için yönetilen tanımı yazmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9557-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="c9557-107">Ayrıca, platform çağırma işlevinin işlevi nasıl oluşturduğunu ve işlevden veri sıraladığı yöntemi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9557-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9557-108">Bir dize ayıran Windows API işlevleri, gibi bir yöntemi `LocalFree`kullanarak dizeyi boşaltmaya olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9557-108">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="c9557-109">Platform çağırma, bu tür parametreleri farklı işler.</span><span class="sxs-lookup"><span data-stu-id="c9557-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="c9557-110">Platform çağırma çağrıları için parametreyi `IntPtr` `String` tür yerine bir tür yapın.</span><span class="sxs-lookup"><span data-stu-id="c9557-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="c9557-111">Türü bir dizeye el ile dönüştürmek için <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> sınıfı tarafından sunulan yöntemleri kullanın ve el ile boşaltın.</span><span class="sxs-lookup"><span data-stu-id="c9557-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="c9557-112">Bildirim temelleri</span><span class="sxs-lookup"><span data-stu-id="c9557-112">Declaration Basics</span></span>  
 <span data-ttu-id="c9557-113">Yönetilmeyen işlevlere yönetilen tanımlar, aşağıdaki örneklerde görebileceğiniz gibi dile bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="c9557-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="c9557-114">Daha kapsamlı kod örnekleri için bkz. [Platform çağırma örnekleri](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="c9557-114">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="c9557-115"><xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType> ,<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute> `Declare` ,,,, Veya<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> alanlarını bir Visual Basic bildirimine uygulamak için, ifadesini kullanarak özniteliğini kullanmanız gerekir. <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c9557-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="c9557-116">Tanımı ayarlama</span><span class="sxs-lookup"><span data-stu-id="c9557-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="c9557-117">Onları açıkça ayarlayıp ayarlamazsanız, öznitelik alanları yönetilen kodun davranışını tanımlayan çalışmalardır.</span><span class="sxs-lookup"><span data-stu-id="c9557-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="c9557-118">Platform çağırma, bir derlemede meta veriler olarak var olan çeşitli alanlarda ayarlanan varsayılan değerlere göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="c9557-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="c9557-119">Bir veya daha fazla alanın değerlerini ayarlayarak bu varsayılan davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9557-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="c9557-120">Çoğu durumda, bir değer ayarlamak <xref:System.Runtime.InteropServices.DllImportAttribute> için öğesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c9557-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="c9557-121">Aşağıdaki tablo, platform Invoke ile ilgili olan öznitelik alanlarının tamamını listeler.</span><span class="sxs-lookup"><span data-stu-id="c9557-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="c9557-122">Her alan için tablo, varsayılan değeri ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanların nasıl kullanılacağına ilişkin bilgilere bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="c9557-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="c9557-123">Alan</span><span class="sxs-lookup"><span data-stu-id="c9557-123">Field</span></span>|<span data-ttu-id="c9557-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9557-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="c9557-125">En uygun eşlemeyi etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c9557-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="c9557-126">Yöntem bağımsız değişkenlerini geçirilerek kullanılacak çağırma kuralını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9557-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="c9557-127">Varsayılan `WinAPI`değer, 32 bit Intel tabanlı `__stdcall` platformlar için karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="c9557-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="c9557-128">Denetim adı değiştirmeyi ve dize bağımsız değişkenlerinin işleve sıralanması gereken yolu.</span><span class="sxs-lookup"><span data-stu-id="c9557-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="c9557-129">Varsayılan, `CharSet.Ansi` değeridir.</span><span class="sxs-lookup"><span data-stu-id="c9557-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="c9557-130">Çağrılacak DLL giriş noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9557-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="c9557-131">Bir giriş noktasının karakter kümesine karşılık olarak değiştirilmesi gerekip gerekmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="c9557-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="c9557-132">Varsayılan değer programlama diline göre değişir.</span><span class="sxs-lookup"><span data-stu-id="c9557-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="c9557-133">Yönetilen yöntem imzasının bir HRESULT döndüren yönetilmeyen imzaya dönüştürülmesi gerekip gerekmediğini ve dönüş değeri için ek bir [Out, retval] bağımsız değişkenine sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="c9557-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="c9557-134">Varsayılan `true` değer (imza dönüştürülmemelidir).</span><span class="sxs-lookup"><span data-stu-id="c9557-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="c9557-135">Çağıran, metodu yürütürken bir hata `Marshal.GetLastWin32Error` oluşup oluşmadığını anlamak için API işlevini kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9557-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="c9557-136">Visual Basic `true`, varsayılan, ve C# C++' de varsayılan ' dir `false`.</span><span class="sxs-lookup"><span data-stu-id="c9557-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="c9557-137">Bir ANSI "?" karakterine dönüştürülmüş, eşlenebilir bir Unicode karakter üzerinde özel durum üretilmesini denetler.</span><span class="sxs-lookup"><span data-stu-id="c9557-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="c9557-138">Ayrıntılı başvuru bilgileri için bkz <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c9557-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="c9557-139">Platform çağırma güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="c9557-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="c9557-140">`Assert`, `Deny`Ve numaralandırmanınüyeleri<xref:System.Security.Permissions.SecurityAction> *Yığın ilerleme değiştiricileri*olarak adlandırılır. `PermitOnly`</span><span class="sxs-lookup"><span data-stu-id="c9557-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="c9557-141">Bu Üyeler platform çağırma bildirimleri ve COM arabirim tanım dili (IDL) deyimlerinde bildirime dayalı öznitelikler olarak kullanılıyorsa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="c9557-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="c9557-142">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c9557-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="c9557-143">Bu bölümdeki platform çağırma örnekleri, yığın yürüme değiştiricilerine sahip `RegistryPermission` özniteliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9557-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="c9557-144"><xref:System.Security.Permissions.SecurityAction>Aşağıdaki örnekte `Assert` ,,`PermitOnly` ve değiştiricileri yok sayılır. `Deny`</span><span class="sxs-lookup"><span data-stu-id="c9557-144">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```csharp  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="c9557-145">Ancak, `Demand` aşağıdaki örnekteki değiştirici kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c9557-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="c9557-146"><xref:System.Security.Permissions.SecurityAction>değiştiriciler, platform çağırma çağrısını içeren (sarmalanmış) bir sınıfa yerleştirilirse doğru çalışır.</span><span class="sxs-lookup"><span data-stu-id="c9557-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="c9557-147"><xref:System.Security.Permissions.SecurityAction>değiştiriciler, platform çağırma çağrısının çağıranına yerleştirildikleri iç içe geçmiş bir senaryoda da doğru çalışır:</span><span class="sxs-lookup"><span data-stu-id="c9557-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="c9557-148">COM birlikte çalışabilirlik örnekleri</span><span class="sxs-lookup"><span data-stu-id="c9557-148">COM Interop Examples</span></span>  
 <span data-ttu-id="c9557-149">Bu bölümdeki com birlikte çalışabilirlik örnekleri, yığın yürüme değiştiricilerine `RegistryPermission` sahip özniteliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9557-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="c9557-150">Aşağıdaki com birlikte çalışma arabirimi bildirimleri, önceki `Assert`bölümde `Deny`bulunan Platform `PermitOnly` çağırma örneklerine benzer şekilde,, ve değiştiricilerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="c9557-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="c9557-151">Ek olarak, `Demand` aşağıdaki örnekte gösterildiği gibi, değiştirici com birlikte çalışma arabirimi bildirim senaryolarında kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="c9557-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9557-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9557-152">See also</span></span>

- [<span data-ttu-id="c9557-153">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="c9557-153">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="c9557-154">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="c9557-154">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="c9557-155">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="c9557-155">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="c9557-156">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="c9557-156">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="c9557-157">[Platform çağırma güvenlik konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c9557-157">[Platform Invoke Security Considerations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="c9557-158">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c9557-158">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="c9557-159">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c9557-159">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="c9557-160">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="c9557-160">Calling a DLL Function</span></span>](calling-a-dll-function.md)
