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
ms.openlocfilehash: e642f6507016dd1d62b4889f8a8dbcf0470a2202
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168174"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="e563d-102">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e563d-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="e563d-103">Bu konu, yönetilmeyen işlevleri nasıl açıklar ve yönetilen kod yöntem tanımında açıklama birkaç öznitelik alanları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e563d-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="e563d-104">Nasıl oluşturulacağını gösteren örnekler için. NET tabanlı bildirimler platformuyla kullanılacak çağırmak için bkz: [Platform Çağırma ile veri hazırlama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="e563d-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="e563d-105">Yönetilen koddan yönetilmeyen bir DLL işlevini erişmeden önce işlevin adını ve bunu aktarır DLL adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e563d-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="e563d-106">Bu bilgileri kullanarak yönetilen bir DLL içinde uygulanır, yönetilmeyen bir işlev tanımı yazmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e563d-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="e563d-107">Ayrıca, biçimini ayarlayabilirsiniz. Bu platform çağırma işlev oluşturur ve işlev veri sürekliliğe devreder.</span><span class="sxs-lookup"><span data-stu-id="e563d-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e563d-108">Bir dize tahsis Windows API işlevlerinde dize gibi bir yöntem kullanarak ücretsiz etkinleştirme `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="e563d-108">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="e563d-109">Platform çağırma tür parametreleri farklı işler.</span><span class="sxs-lookup"><span data-stu-id="e563d-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="e563d-110">Çağrıları için platform çağırma, parametre olun bir `IntPtr` türü yerine bir `String` türü.</span><span class="sxs-lookup"><span data-stu-id="e563d-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="e563d-111">Tarafından sağlanan yöntemleri kullanın <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> türü el ile bir dizeye Dönüştür ve el ile ücretsiz sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e563d-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="e563d-112">Bildirim temelleri</span><span class="sxs-lookup"><span data-stu-id="e563d-112">Declaration Basics</span></span>  
 <span data-ttu-id="e563d-113">Aşağıdaki örneklerde görüldüğü gibi yönetilen tanımları yönetilmeyen işlevlerle dile bağlı.</span><span class="sxs-lookup"><span data-stu-id="e563d-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="e563d-114">Tam kod örnekleri için bkz: [Platform çağırma örnekleri](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="e563d-114">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Imports System

Friend Class WindowsAPI
    Friend Shared Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="e563d-115">Uygulanacak <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, veya <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> alanlarını bir [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] bildirimi kullanmalıdır <xref:System.Runtime.InteropServices.DllImportAttribute> özniteliği yerine `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="e563d-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System
Imports System.Runtime.InteropServices

Friend Class WindowsAPI
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

internal static class WindowsAPI
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
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="e563d-116">Tanım'ı ayarlama</span><span class="sxs-lookup"><span data-stu-id="e563d-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="e563d-117">Bunları açıkça ayarlanıp olsun, öznitelik alanları yönetilen kodun davranışını tanımlayan İşte.</span><span class="sxs-lookup"><span data-stu-id="e563d-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="e563d-118">Platform çağırma bir derlemenin meta verilerde mevcut çeşitli alanları ayarlamak varsayılan değerlere göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="e563d-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="e563d-119">Bir veya daha fazla alan değerleri ayarlayarak bu varsayılan davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e563d-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="e563d-120">Çoğu durumda, kullandığınız <xref:System.Runtime.InteropServices.DllImportAttribute> bir değer ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="e563d-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="e563d-121">Aşağıdaki tabloda, tam bir set çağırmada platforma ait alanları özniteliğinin listeler.</span><span class="sxs-lookup"><span data-stu-id="e563d-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="e563d-122">Tablo, her alan için varsayılan değer ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanları kullanmak hakkında bilgi için bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="e563d-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="e563d-123">Alan</span><span class="sxs-lookup"><span data-stu-id="e563d-123">Field</span></span>|<span data-ttu-id="e563d-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e563d-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="e563d-125">Etkinleştirir veya en iyi uyan eşlemeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="e563d-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="e563d-126">Yöntem bağımsız değişkenleri geçirirken kullanmak için çağırma kuralını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e563d-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="e563d-127">Varsayılan değer `WinAPI`, karşılık gelen `__stdcall` 32-bit Intel tabanlı platformlar için.</span><span class="sxs-lookup"><span data-stu-id="e563d-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="e563d-128">Denetimleri ad değiştirmeyi ve bağımsız değişkenleri dize şekilde işleve sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e563d-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="e563d-129">Varsayılan, `CharSet.Ansi` değeridir.</span><span class="sxs-lookup"><span data-stu-id="e563d-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="e563d-130">Çağrılacak DLL giriş noktası belirtir.</span><span class="sxs-lookup"><span data-stu-id="e563d-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="e563d-131">Bir giriş noktası karakter kümesine karşılık gelen değişiklik olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e563d-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="e563d-132">Varsayılan değer programlama dili olarak değişiklik gösterir.</span><span class="sxs-lookup"><span data-stu-id="e563d-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="e563d-133">Yönetilen yöntem imzası bir HRESULT döndürür ve döndürülen değer [out, retval] ek bağımsız değişken olan yönetilmeyen bir imza içine dönüştürülür olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e563d-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="e563d-134">Varsayılan değer `true` (imza değil dönüştürülmesi).</span><span class="sxs-lookup"><span data-stu-id="e563d-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="e563d-135">Kullanılacak çağıran sağlar `Marshal.GetLastWin32Error` metodu yürütülürken bir hata oluştu olup olmadığını belirlemek için API işlevi.</span><span class="sxs-lookup"><span data-stu-id="e563d-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="e563d-136">Visual Basic'te varsayılandır `true`; C# ve C++ varsayılan `false`.</span><span class="sxs-lookup"><span data-stu-id="e563d-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="e563d-137">Denetimleri için ANSI dönüştürülür eşlenemez bir Unicode karakter üzerinde bir özel durum atma "?" karakter.</span><span class="sxs-lookup"><span data-stu-id="e563d-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="e563d-138">Ayrıntılı başvuru bilgileri için bkz. <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e563d-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="e563d-139">Platform çağırmayla ilgili güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="e563d-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="e563d-140">`Assert`, `Deny`, Ve `PermitOnly` üyeleri <xref:System.Security.Permissions.SecurityAction> sabit listesi denir *yığın ilerlemesi değiştiriciler*.</span><span class="sxs-lookup"><span data-stu-id="e563d-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="e563d-141">Bildirim temelli öznitelikleri platformunda bildirimleri ve COM arabirimi tanım dili (IDL) ifadeleri çağırma kullanılıyorsa, bu üyeler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="e563d-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="e563d-142">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e563d-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="e563d-143">Platform çağırma örnekleri bu bölümde kullanımını gösteren `RegistryPermission` yığın ilerlemesi değiştiricileri ile özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e563d-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="e563d-144">Aşağıdaki kod örneğinde, <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, ve `PermitOnly` değiştiricileri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e563d-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```  
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
  
 <span data-ttu-id="e563d-145">Ancak, `Demand` değiştiricisi aşağıdaki örnekte kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="e563d-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="e563d-146"><xref:System.Security.Permissions.SecurityAction> değiştiriciler çalışma doğru Platformu (sarar) içeren bir sınıf üzerinde yerleştirdiyseniz çağrısı başlatılacak.</span><span class="sxs-lookup"><span data-stu-id="e563d-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
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
  
 <span data-ttu-id="e563d-147"><xref:System.Security.Permissions.SecurityAction> değiştiriciler doğru platformun çağrı üzerinde nereye yerleştirileceğini iç içe geçmiş senaryosunda ayrıca iş çağrısı başlatılacak:</span><span class="sxs-lookup"><span data-stu-id="e563d-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
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
  
#### <a name="com-interop-examples"></a><span data-ttu-id="e563d-148">COM birlikte çalışma örnekleri</span><span class="sxs-lookup"><span data-stu-id="e563d-148">COM Interop Examples</span></span>  
 <span data-ttu-id="e563d-149">Bu bölümdeki COM birlikte çalışma örnekleri kullanımını gösteren `RegistryPermission` yığın ilerlemesi değiştiricileri ile özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e563d-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="e563d-150">Aşağıdaki COM birlikte çalışma arabirimi bildirimleri Yoksay `Assert`, `Deny`, ve `PermitOnly` değiştiriciler, benzer şekilde platform çağırma örnekleri önceki bölümde.</span><span class="sxs-lookup"><span data-stu-id="e563d-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
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
  
 <span data-ttu-id="e563d-151">Ayrıca, `Demand` aşağıdaki örnekte gösterildiği gibi değiştirici COM birlikte çalışma arabirimi bildirimi senaryolarda değil kabul.</span><span class="sxs-lookup"><span data-stu-id="e563d-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e563d-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e563d-152">See also</span></span>

- [<span data-ttu-id="e563d-153">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="e563d-153">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="e563d-154">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="e563d-154">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="e563d-155">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="e563d-155">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="e563d-156">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="e563d-156">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="e563d-157">[Platform çağırmayla ilgili güvenlik konuları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e563d-157">[Platform Invoke Security Considerations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="e563d-158">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="e563d-158">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="e563d-159">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e563d-159">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="e563d-160">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="e563d-160">Calling a DLL Function</span></span>](calling-a-dll-function.md)
