---
title: "Yönetilen Kodda Prototipler Oluşturma"
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
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1006f59f9841a10066c83a8f0800d3a7c17500a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="7d73f-102">Yönetilen Kodda Prototipler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d73f-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="7d73f-103">Bu konu, yönetilmeyen işlevlere erişim açıklar ve yönetilen kod yöntemi tanımında açıklama birkaç öznitelik alanları tanıtır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="7d73f-104">Örnekler için nasıl oluşturulacağını gösterir. Platformuyla kullanılacak bildirimleri NET tabanlı çağırmak için bkz: [Platform Çağırma ile veri hazırlama](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="7d73f-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="7d73f-105">Yönetilen koddan yönetilmeyen DLL işlev erişebilmeniz için önce işlevin adını ve bunu aktarır DLL adını bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="7d73f-106">Bu bilgilerle DLL'de uygulanır, yönetilmeyen bir işleve yönetilen tanımı yazmaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d73f-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="7d73f-107">Ayrıca, şeklini ayarlayabilirsiniz bu platform çağırma işlev oluşturur ve veri işlevi gelen ve giden sıralar.</span><span class="sxs-lookup"><span data-stu-id="7d73f-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d73f-108">Bir dize tahsis Win32 API işlevleri dize gibi bir yöntem kullanarak boşaltmak etkinleştirme `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="7d73f-108">Win32 API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="7d73f-109">Platform çağırma gibi parametreleri farklı şekilde ele alır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="7d73f-110">Çağrıları için platform çağırma, parametre olun bir `IntPtr` türü yerine bir `String` türü.</span><span class="sxs-lookup"><span data-stu-id="7d73f-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="7d73f-111">Tarafından sağlanan yöntemleri kullanın <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> türü el ile bir dizeye dönüştürmek ve el ile boş sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7d73f-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="7d73f-112">Bildirim temelleri</span><span class="sxs-lookup"><span data-stu-id="7d73f-112">Declaration Basics</span></span>  
 <span data-ttu-id="7d73f-113">Aşağıdaki örneklerde görüldüğü gibi yönetilen tanımları yönetilmeyen işlevleri için dile bağlı.</span><span class="sxs-lookup"><span data-stu-id="7d73f-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="7d73f-114">Daha eksiksiz kod örnekleri için bkz: [Platform çağırma örnekleri](../../../docs/framework/interop/platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="7d73f-114">For more complete code examples, see [Platform Invoke Examples](../../../docs/framework/interop/platform-invoke-examples.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 <span data-ttu-id="7d73f-115">Uygulanacak <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, veya <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> alanları bir [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] bildirimi kullanmalıdır <xref:System.Runtime.InteropServices.DllImportAttribute> yerine özniteliği `Declare` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7d73f-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="7d73f-116">Tanım ayarlama</span><span class="sxs-lookup"><span data-stu-id="7d73f-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="7d73f-117">Bunları açıkça veya değil ayarlanmış olup olmadığını özniteliği yönetilen kod davranışını tanımlama İşte alanlardır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="7d73f-118">Platform çağırma bir derlemenin meta verilerde mevcut çeşitli alanlarını Ayarla varsayılan değerlere göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="7d73f-119">Bir veya daha fazla alan değerlerini ayarlayarak bu varsayılan davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d73f-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="7d73f-120">Çoğu durumda, kullandığınız <xref:System.Runtime.InteropServices.DllImportAttribute> bir değer ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="7d73f-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="7d73f-121">Aşağıdaki tabloda tamamını çağırmada platformuna ilgilidir alanları özniteliği listeler.</span><span class="sxs-lookup"><span data-stu-id="7d73f-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="7d73f-122">Her bir alan tablo, varsayılan değer ve yönetilmeyen DLL işlevlerini tanımlamak için bu alanları kullanma hakkında bilgi için bir bağlantı içerir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="7d73f-123">Alan</span><span class="sxs-lookup"><span data-stu-id="7d73f-123">Field</span></span>|<span data-ttu-id="7d73f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d73f-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="7d73f-125">Etkinleştirir veya en uygun eşlemeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="7d73f-126">Yöntem bağımsız değişkenleri geçirme kullanılacak çağırma kuralı belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="7d73f-127">Varsayılan değer `WinAPI`, hangi karşılık gelen `__stdcall` Intel tabanlı 32-bit platformu için.</span><span class="sxs-lookup"><span data-stu-id="7d73f-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="7d73f-128">Denetimleri ad bozma ve bağımsız değişkenleri dize şekilde işleve sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="7d73f-129">Varsayılan, `CharSet.Ansi` değeridir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="7d73f-130">Çağrılacak DLL giriş noktası belirtir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="7d73f-131">Bir giriş noktası için karakter kümesi karşılık gelecek şekilde değiştirilmiş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7d73f-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="7d73f-132">Varsayılan değer programlama dili olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="7d73f-133">Yönetilen yöntem imzası HRESULT döndürür ve dönüş değeri için [out, retval] ek bağımsız değişken olan yönetilmeyen bir imza içine dönüştürülmüş olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7d73f-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="7d73f-134">Varsayılan değer `true` (imza değil dönüştürülmesi).</span><span class="sxs-lookup"><span data-stu-id="7d73f-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="7d73f-135">Kullanılacak çağıran etkinleştirir `Marshal.GetLastWin32Error` yöntemi yürütülürken bir hata oluştu olup olmadığını belirlemek için API işlevi.</span><span class="sxs-lookup"><span data-stu-id="7d73f-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="7d73f-136">Visual Basic'te varsayılandır `true`; C# ve C++, varsayılan `false`.</span><span class="sxs-lookup"><span data-stu-id="7d73f-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="7d73f-137">Denetimleri için ANSI dönüştürülür eşlenemez bir Unicode karakter üzerinde bir özel durum atma "?" karakter.</span><span class="sxs-lookup"><span data-stu-id="7d73f-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="7d73f-138">Ayrıntılı başvuru bilgileri için bkz: <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7d73f-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="7d73f-139">Platform çağırma güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="7d73f-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="7d73f-140">`Assert`, `Deny`, Ve `PermitOnly` üyeleri <xref:System.Security.Permissions.SecurityAction> numaralandırma denir *ilerlemesi değiştiricileri yığın*.</span><span class="sxs-lookup"><span data-stu-id="7d73f-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="7d73f-141">Bildirimler ve COM arabirimi tanım dili (IDL) deyimleri platform bildirim temelli özniteliklerinde çağırma olarak kullanılıyorsa, bu üyeler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="7d73f-142">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="7d73f-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="7d73f-143">Platform çağırma örnekleri bu bölümde göstermeye kullanımını `RegistryPermission` yığın ilerlemesi değiştiricileri özniteliğiyle.</span><span class="sxs-lookup"><span data-stu-id="7d73f-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="7d73f-144">Aşağıdaki kod örneğinde, <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, ve `PermitOnly` değiştiricileri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7d73f-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
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
  
 <span data-ttu-id="7d73f-145">Ancak, `Demand` aşağıdaki örnekte değiştiricisi tarafından kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7d73f-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="7d73f-146"><xref:System.Security.Permissions.SecurityAction>değiştiriciler iş doğru platform (sarmalayan) içeren bir sınıf girdiyseniz çağrısı başlatılacak.</span><span class="sxs-lookup"><span data-stu-id="7d73f-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
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
  
 <span data-ttu-id="7d73f-147"><xref:System.Security.Permissions.SecurityAction>değiştiriciler platform çağıran üzerinde nereye yerleştirileceğini doğru bir senaryoda iç içe geçmiş iş ayrıca çağrısı başlatılacak:</span><span class="sxs-lookup"><span data-stu-id="7d73f-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
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
  
#### <a name="com-interop-examples"></a><span data-ttu-id="7d73f-148">COM birlikte çalışma örnekleri</span><span class="sxs-lookup"><span data-stu-id="7d73f-148">COM Interop Examples</span></span>  
 <span data-ttu-id="7d73f-149">Bu bölümdeki COM birlikte çalışma örnekler kullanımını göstermek `RegistryPermission` yığın ilerlemesi değiştiricileri özniteliğiyle.</span><span class="sxs-lookup"><span data-stu-id="7d73f-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="7d73f-150">Aşağıdaki COM birlikte çalışma arabirimi bildirimlerini Yoksay `Assert`, `Deny`, ve `PermitOnly` benzer şekilde platform değiştiriciler çağırma önceki bölümdeki örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7d73f-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
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
  
 <span data-ttu-id="7d73f-151">Ayrıca, `Demand` aşağıdaki örnekte gösterildiği gibi değiştiricisi COM birlikte çalışma arabirimi bildirimi senaryolarda değil kabul.</span><span class="sxs-lookup"><span data-stu-id="7d73f-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d73f-152">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7d73f-152">See Also</span></span>  
 [<span data-ttu-id="7d73f-153">Yönetilmeyen DLL İşlevlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="7d73f-153">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="7d73f-154">Giriş Noktası Belirtme</span><span class="sxs-lookup"><span data-stu-id="7d73f-154">Specifying an Entry Point</span></span>](../../../docs/framework/interop/specifying-an-entry-point.md)  
 [<span data-ttu-id="7d73f-155">Karakter Kümesi Belirtme</span><span class="sxs-lookup"><span data-stu-id="7d73f-155">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)  
 [<span data-ttu-id="7d73f-156">Platform Çağırma Örnekleri</span><span class="sxs-lookup"><span data-stu-id="7d73f-156">Platform Invoke Examples</span></span>](../../../docs/framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="7d73f-157">Platform çağırma güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="7d73f-157">Platform Invoke Security Considerations</span></span>](http://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb)  
 [<span data-ttu-id="7d73f-158">DLL'lerde İşlevleri Tanımlama</span><span class="sxs-lookup"><span data-stu-id="7d73f-158">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="7d73f-159">DLL İşlevleri için bir Sınıf Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7d73f-159">Creating a Class to Hold DLL Functions</span></span>](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="7d73f-160">DLL İşlevini Çağırma</span><span class="sxs-lookup"><span data-stu-id="7d73f-160">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
