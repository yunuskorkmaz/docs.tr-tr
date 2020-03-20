---
title: 'Nasıl yapılır: Sarmalayıcıları Elle Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
ms.openlocfilehash: a7818a1c08d8538acfacb22dc270d7ef23a7a582
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181424"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="46e35-102">Nasıl yapılır: Sarmalayıcıları Elle Oluşturma</span><span class="sxs-lookup"><span data-stu-id="46e35-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="46e35-103">Yönetilen kaynak kodunda COM türlerini el ile bildirmeye karar verirseniz, başlamak için en iyi yer varolan bir Arabirim Tanımı Dili (IDL) dosyası veya tür kitaplığıdır.</span><span class="sxs-lookup"><span data-stu-id="46e35-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="46e35-104">IDL dosyasıyoksa veya bir tür kitaplığı dosyası oluşturamıyorsa, yönetilen bildirimler oluşturarak ve ortaya çıkan derlemeyi bir tür kitaplığına dışa aktararak COM türlerini simüle edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e35-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="46e35-105">Yönetilen kaynaktan COM türlerini simüle etmek için</span><span class="sxs-lookup"><span data-stu-id="46e35-105">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="46e35-106">Türleri Ortak Dil Belirtimi (CLS) ile uyumlu bir dilde bildirin ve dosyayı derle.</span><span class="sxs-lookup"><span data-stu-id="46e35-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="46e35-107">[Tip Kitaplığı İhracatçısı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md)ile türleri içeren montajı dışa aktarın.</span><span class="sxs-lookup"><span data-stu-id="46e35-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="46e35-108">Dışa aktarılan COM türü kitaplığını, COM yönelimli yönetilen türleri bildirmek için temel olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="46e35-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="46e35-109">Çalışma zamanı çağrılabilir sarıcı (RCW) oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="46e35-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="46e35-110">Bir IDL dosyanız veya tür kitaplığı dosyanız olduğunu varsayarsak, özel RCW'ye hangi sınıfları ve arabirimleri eklemek istediğinize karar verin.</span><span class="sxs-lookup"><span data-stu-id="46e35-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="46e35-111">Doğrudan veya dolaylı olarak uygulamanızda kullanmak niyetinde olmadığınız türleri hariç tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e35-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="46e35-112">CLS uyumlu bir dilde bir kaynak dosyası oluşturun ve türleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="46e35-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="46e35-113">Alma dönüştürme işleminin tam açıklaması için [Derleme Dönüşüm Özeti türüne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) bakın.</span><span class="sxs-lookup"><span data-stu-id="46e35-113">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="46e35-114">Etkili bir şekilde, özel bir RCW oluşturduğunuzda, [Tür Kitaplığı İthalatçısı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından sağlanan tür dönüştürme etkinliğini el ile gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="46e35-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="46e35-115">Sonraki bölümdeki örnekte, IDL veya tür kitaplığı dosyasındaki türleri ve bunların C# kodundaki karşılık gelen türleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="46e35-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="46e35-116">Bildirimler tamamlandığında, diğer yönetilen kaynak kodlarını derlerken dosyayı derle.</span><span class="sxs-lookup"><span data-stu-id="46e35-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="46e35-117">Tlbimp.exe ile alınan türleri olduğu gibi, bazı doğrudan kodunuza ekleyebilirsiniz ek bilgi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="46e35-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="46e35-118">Ayrıntılar için [bkz: Interop Montajlarını Edit.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46e35-118">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="46e35-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="46e35-119">Example</span></span>  
 <span data-ttu-id="46e35-120">Aşağıdaki kod, IDL'deki `ISATest` `SATest` arabirim ve sınıfın bir örneğini ve C# kaynak kodundaki ilgili türleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="46e35-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="46e35-121">**IDL veya tür kitaplığı dosyası**</span><span class="sxs-lookup"><span data-stu-id="46e35-121">**IDL or type library file**</span></span>  
  
```cpp
 [  
object,  
uuid(40A8C65D-2448-447A-B786-64682CBEF133),  
dual,  
helpstring("ISATest Interface"),  
pointer_default(unique)  
 ]  
interface ISATest : IDispatch  
 {  
[id(1), helpstring("method InSArray")]
HRESULT InSArray([in] SAFEARRAY(int) *ppsa, [out,retval] int *pSum);  
 };  
 [  
uuid(116CCA1E-7E39-4515-9849-90790DA6431E),  
helpstring("SATest Class")  
 ]  
coclass SATest  
 {  
  [default] interface ISATest;  
 };  
```  
  
 <span data-ttu-id="46e35-122">**Yönetilen kaynak kodunda sarıcı**</span><span class="sxs-lookup"><span data-stu-id="46e35-122">**Wrapper in managed source code**</span></span>  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
using System.Runtime.CompilerServices;  
  
[assembly:Guid("E4A992B8-6F5C-442C-96E7-C4778924C753")]  
[assembly:ImportedFromTypeLib("SAServerLib")]  
namespace SAServer  
{  
 [ComImport]  
 [Guid("40A8C65D-2448-447A-B786-64682CBEF133")]  
 [TypeLibType(TypeLibTypeFlags.FLicensed)]  
 public interface ISATest  
 {  
  [DispId(1)]  
  //[MethodImpl(MethodImplOptions.InternalCall,  
  // MethodCodeType=MethodCodeType.Runtime)]  
  int InSArray( [MarshalAs(UnmanagedType.SafeArray,  
      SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }
 [ComImport]  
 [Guid("116CCA1E-7E39-4515-9849-90790DA6431E")]  
 [ClassInterface(ClassInterfaceType.None)]  
 [TypeLibType(TypeLibTypeFlags.FCanCreate)]  
 public class SATest : ISATest  
 {  
  [DispId(1)]  
  [MethodImpl(MethodImplOptions.InternalCall,
  MethodCodeType=MethodCodeType.Runtime)]  
  extern int ISATest.InSArray( [MarshalAs(UnmanagedType.SafeArray,
  SafeArraySubType=VarEnum.VT_I4)] ref int[] param );  
 }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="46e35-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46e35-123">See also</span></span>

- <span data-ttu-id="46e35-124">[Runtime Çağrılanabilir Sarmalayıcıları Özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46e35-124">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>
- <span data-ttu-id="46e35-125">[COM Veri Türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46e35-125">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>
- <span data-ttu-id="46e35-126">[Nasıl yapılsın: Interop Montajlarını Edit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46e35-126">[How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span></span>
- <span data-ttu-id="46e35-127">[Tür Kitaplığı ndan Montaja Dönüşüm Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46e35-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="46e35-128">Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="46e35-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="46e35-129">Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="46e35-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
