---
title: Yönetilen Kodda Prototipler Oluşturma
description: .NET tarafından yönetilen kodda prototipler oluşturun, bu sayede yönetilmeyen işlevlere erişebilir ve yönetilen kodda Yöntem tanımına açıklama eklemek için öznitelik alanlarını kullanabilirsiniz.
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
ms.openlocfilehash: e83979e5843c52fc3a446a5b669ae8822b32ddad
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555594"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="fec55-103">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fec55-103">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="fec55-104">Bu konu, yönetilmeyen işlevlere nasıl erişmekte olduğunu ve yönetilen kodda Yöntem tanımına açıklama eklenen çeşitli öznitelik alanlarını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="fec55-104">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="fec55-105">Nasıl oluşturulacağını gösteren örnekler için. Platform çağırma ile kullanılacak NET tabanlı bildirimler, bkz. [Platform çağırma Ile verileri sıralama](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="fec55-105">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="fec55-106">Yönetilen koddan yönetilmeyen bir DLL işlevine erişebilmek için önce işlevin adını ve onu dışarı aktaran DLL 'nin adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fec55-106">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="fec55-107">Bu bilgilerle, DLL 'de uygulanan yönetilmeyen bir işlev için yönetilen tanımı yazmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fec55-107">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="fec55-108">Ayrıca, platform çağırma işlevinin işlevi nasıl oluşturduğunu ve işlevden veri sıraladığı yöntemi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fec55-108">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fec55-109">Bir dize ayıran Windows API işlevleri, gibi bir yöntemi kullanarak dizeyi boşaltmaya olanak sağlar `LocalFree` .</span><span class="sxs-lookup"><span data-stu-id="fec55-109">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="fec55-110">Platform çağırma, bu tür parametreleri farklı işler.</span><span class="sxs-lookup"><span data-stu-id="fec55-110">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="fec55-111">Platform çağırma çağrıları için parametreyi `IntPtr` tür yerine bir tür yapın `String` .</span><span class="sxs-lookup"><span data-stu-id="fec55-111">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="fec55-112"><xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>Türü bir dizeye el ile dönüştürmek için sınıfı tarafından sunulan yöntemleri kullanın ve el ile boşaltın.</span><span class="sxs-lookup"><span data-stu-id="fec55-112">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="fec55-113">Bildirim temelleri</span><span class="sxs-lookup"><span data-stu-id="fec55-113">Declaration Basics</span></span>  
 <span data-ttu-id="fec55-114">Yönetilmeyen işlevlere yönetilen tanımlar, aşağıdaki örneklerde görebileceğiniz gibi dile bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="fec55-114">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="fec55-115">Daha kapsamlı kod örnekleri için bkz. [Platform çağırma örnekleri](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="fec55-115">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="fec55-116">,,,,, <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> Veya <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> alanlarını bir Visual Basic bildirimine uygulamak için, ifadesini kullanarak özniteliğini kullanmanız gerekir <xref:System.Runtime.InteropServices.DllImportAttribute> `Declare` .</span><span class="sxs-lookup"><span data-stu-id="fec55-116">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
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
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="fec55-117">Tanımı ayarlama</span><span class="sxs-lookup"><span data-stu-id="fec55-117">Adjusting the Definition</span></span>  
 <span data-ttu-id="fec55-118">Onları açıkça ayarlayıp ayarlamazsanız, öznitelik alanları yönetilen kodun davranışını tanımlayan çalışmalardır.</span><span class="sxs-lookup"><span data-stu-id="fec55-118">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="fec55-119">Platform çağırma, bir derlemede meta veriler olarak var olan çeşitli alanlarda ayarlanan varsayılan değerlere göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="fec55-119">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="fec55-120">Bir veya daha fazla alanın değerlerini ayarlayarak bu varsayılan davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fec55-120">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="fec55-121">Çoğu durumda, <xref:System.Runtime.InteropServices.DllImportAttribute> bir değer ayarlamak için öğesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fec55-121">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="fec55-122">Aşağıdaki tablo, platform Invoke ile ilgili olan öznitelik alanlarının tamamını listeler.</span><span class="sxs-lookup"><span data-stu-id="fec55-122">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="fec55-123">Her alan için tablo, varsayılan değeri ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanların nasıl kullanılacağına ilişkin bilgilere bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="fec55-123">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="fec55-124">Alan</span><span class="sxs-lookup"><span data-stu-id="fec55-124">Field</span></span>|<span data-ttu-id="fec55-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fec55-125">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="fec55-126">En uygun eşlemeyi etkinleştirilir veya devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="fec55-126">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="fec55-127">Yöntem bağımsız değişkenlerini geçirilerek kullanılacak çağırma kuralını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fec55-127">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="fec55-128">Varsayılan değer `WinAPI` , `__stdcall` 32 bit Intel tabanlı platformlar için karşılık gelir.</span><span class="sxs-lookup"><span data-stu-id="fec55-128">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="fec55-129">Denetim adı değiştirmeyi ve dize bağımsız değişkenlerinin işleve sıralanması gereken yolu.</span><span class="sxs-lookup"><span data-stu-id="fec55-129">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="fec55-130">Varsayılan değer: `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="fec55-130">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="fec55-131">Çağrılacak DLL giriş noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fec55-131">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="fec55-132">Bir giriş noktasının karakter kümesine karşılık olarak değiştirilmesi gerekip gerekmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="fec55-132">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="fec55-133">Varsayılan değer programlama diline göre değişir.</span><span class="sxs-lookup"><span data-stu-id="fec55-133">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="fec55-134">Yönetilen yöntem imzasının bir HRESULT döndüren yönetilmeyen imzaya dönüştürülmesi gerekip gerekmediğini ve dönüş değeri için ek bir [Out, retval] bağımsız değişkenine sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="fec55-134">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="fec55-135">Varsayılan değer `true` (imza dönüştürülmemelidir).</span><span class="sxs-lookup"><span data-stu-id="fec55-135">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="fec55-136">Çağıran, `Marshal.GetLastWin32Error` metodu yürütürken bir hata oluşup oluşmadığını anlamak için API işlevini kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fec55-136">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="fec55-137">Visual Basic ' de, varsayılan ' dir `true` ; C# ve C++ ' ta varsayılandır `false` .</span><span class="sxs-lookup"><span data-stu-id="fec55-137">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="fec55-138">Bir ANSI "?" karakterine dönüştürülmüş, eşlenebilir bir Unicode karakter üzerinde özel durum üretilmesini denetler.</span><span class="sxs-lookup"><span data-stu-id="fec55-138">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="fec55-139">Ayrıntılı başvuru bilgileri için bkz <xref:System.Runtime.InteropServices.DllImportAttribute> ..</span><span class="sxs-lookup"><span data-stu-id="fec55-139">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="fec55-140">Platform çağırma güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="fec55-140">Platform invoke security considerations</span></span>  
 <span data-ttu-id="fec55-141">`Assert`, `Deny` Ve `PermitOnly` <xref:System.Security.Permissions.SecurityAction> numaralandırmanın üyeleri *Yığın ilerleme değiştiricileri*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fec55-141">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="fec55-142">Bu Üyeler platform çağırma bildirimleri ve COM arabirim tanım dili (IDL) deyimlerinde bildirime dayalı öznitelikler olarak kullanılıyorsa yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="fec55-142">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="fec55-143">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="fec55-143">Platform Invoke Examples</span></span>  
 <span data-ttu-id="fec55-144">Bu bölümdeki platform çağırma örnekleri, `RegistryPermission` yığın yürüme değiştiricilerine sahip özniteliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fec55-144">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="fec55-145">Aşağıdaki örnekte,, <xref:System.Security.Permissions.SecurityAction> `Assert` `Deny` ve `PermitOnly` değiştiricileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="fec55-145">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
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
  
 <span data-ttu-id="fec55-146">Ancak, `Demand` Aşağıdaki örnekteki değiştirici kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="fec55-146">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="fec55-147"><xref:System.Security.Permissions.SecurityAction> değiştiriciler, platform çağırma çağrısını içeren (sarmalanmış) bir sınıfa yerleştirilirse doğru çalışır.</span><span class="sxs-lookup"><span data-stu-id="fec55-147"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
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
  
 <span data-ttu-id="fec55-148"><xref:System.Security.Permissions.SecurityAction> değiştiriciler, platform çağırma çağrısının çağıranına yerleştirildikleri iç içe geçmiş bir senaryoda da doğru çalışır:</span><span class="sxs-lookup"><span data-stu-id="fec55-148"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
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
  
#### <a name="com-interop-examples"></a><span data-ttu-id="fec55-149">COM birlikte çalışabilirlik örnekleri</span><span class="sxs-lookup"><span data-stu-id="fec55-149">COM Interop Examples</span></span>  
 <span data-ttu-id="fec55-150">Bu bölümdeki COM birlikte çalışabilirlik örnekleri, `RegistryPermission` yığın yürüme değiştiricilerine sahip özniteliğin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fec55-150">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="fec55-151">Aşağıdaki COM birlikte çalışma arabirimi bildirimleri, `Assert` `Deny` `PermitOnly` önceki bölümde bulunan Platform çağırma örneklerine benzer şekilde,, ve değiştiricilerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="fec55-151">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="fec55-152">Ek olarak, `Demand` Aşağıdaki örnekte gösterildiği gibi, DEĞIŞTIRICI com birlikte çalışma arabirimi bildirim senaryolarında kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="fec55-152">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fec55-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fec55-153">See also</span></span>

- [<span data-ttu-id="fec55-154">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="fec55-154">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="fec55-155">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="fec55-155">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="fec55-156">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="fec55-156">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="fec55-157">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="fec55-157">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="fec55-158">[Platform çağırma güvenlik konuları](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fec55-158">[Platform Invoke Security Considerations](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="fec55-159">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="fec55-159">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="fec55-160">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fec55-160">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="fec55-161">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="fec55-161">Calling a DLL Function</span></span>](calling-a-dll-function.md)
