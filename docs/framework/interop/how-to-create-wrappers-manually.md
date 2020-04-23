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
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="d2674-102">Nasıl yapılır: Sarmalayıcıları Elle Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2674-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="d2674-103">COM türlerini yönetilen kaynak kodunda el ile bildirmeye karar verirseniz, başlamak için en iyi yer, var olan bir arabirim tanım dili (IDL) dosyası veya tür kitaplığı vardır.</span><span class="sxs-lookup"><span data-stu-id="d2674-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="d2674-104">IDL dosyanız yoksa veya bir tür kitaplığı dosyası üretüriyorsa, yönetilen bildirimler oluşturarak ve ortaya çıkan derlemeyi bir tür kitaplığına vererek COM türlerinin benzetimini yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2674-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="d2674-105">Yönetilen kaynaktan COM türlerinin benzetimini yapmak için</span><span class="sxs-lookup"><span data-stu-id="d2674-105">To simulate COM types from managed source</span></span>  
  
1. <span data-ttu-id="d2674-106">Türleri ortak dil belirtimi (CLS) ile uyumlu bir dilde bildirin ve dosyayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="d2674-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2. <span data-ttu-id="d2674-107">Türleri içeren derlemeyi [tür kitaplığı verme programı (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md)ile dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="d2674-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3. <span data-ttu-id="d2674-108">COM tabanlı yönetilen türler bildirmek için bir temel olarak, dışarıya aktarılmış COM tür kitaplığını kullanın.</span><span class="sxs-lookup"><span data-stu-id="d2674-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="d2674-109">Çalışma zamanında çağrılabilir sarmalayıcı (RCW) oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="d2674-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1. <span data-ttu-id="d2674-110">Bir IDL dosyası ya da tür kitaplığı dosyanız olduğunu varsayarsak, özel RCW 'ya dahil etmek istediğiniz sınıfları ve arabirimleri belirleyin.</span><span class="sxs-lookup"><span data-stu-id="d2674-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="d2674-111">Uygulamanızda doğrudan veya dolaylı olarak kullanmayı planlamadığınız tüm türleri dışarıda bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d2674-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2. <span data-ttu-id="d2674-112">CLS uyumlu bir dilde kaynak dosyası oluşturun ve türleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="d2674-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="d2674-113">İçeri aktarma dönüştürme işleminin tüm açıklaması için bkz. [tür kitaplığı, derleme dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="d2674-113">See [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="d2674-114">Etkin olarak, özel bir RCW oluşturduğunuzda, [tür kitaplığı alma programı (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md)tarafından sağlanmış tür dönüştürme etkinliğini el ile gerçekleştirmekten olursunuz.</span><span class="sxs-lookup"><span data-stu-id="d2674-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="d2674-115">Sonraki bölümdeki örnekte, bir IDL veya tür kitaplığı dosyasındaki türler ve C# kodunda bunlara karşılık gelen türler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d2674-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3. <span data-ttu-id="d2674-116">Bildirimler tamamlandığında, başka bir yönetilen kaynak kodu derlerken dosyayı derleyin.</span><span class="sxs-lookup"><span data-stu-id="d2674-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4. <span data-ttu-id="d2674-117">Tlbimp. exe ile içeri aktarılan türlerde, bazıları doğrudan kodunuza ekleyebileceğiniz ek bilgiler gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d2674-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="d2674-118">Ayrıntılar için bkz. [nasıl yapılır: birlikte çalışma derlemelerini düzenleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d2674-118">For details, see [How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2674-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2674-119">Example</span></span>  
 <span data-ttu-id="d2674-120">Aşağıdaki kod, IDL 'deki `ISATest` arabirime ve `SATest` sınıfa ve C# kaynak kodundaki karşılık gelen türlere bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2674-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="d2674-121">**IDL veya tür kitaplığı dosyası**</span><span class="sxs-lookup"><span data-stu-id="d2674-121">**IDL or type library file**</span></span>  
  
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
  
 <span data-ttu-id="d2674-122">**Yönetilen kaynak kodunda sarmalayıcı**</span><span class="sxs-lookup"><span data-stu-id="d2674-122">**Wrapper in managed source code**</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d2674-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2674-123">See also</span></span>

- <span data-ttu-id="d2674-124">[Çalışma zamanı çağrılabilir sarmalayıcıları özelleştirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2674-124">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>
- <span data-ttu-id="d2674-125">[COM veri türleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2674-125">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>
- <span data-ttu-id="d2674-126">[Nasıl yapılır: birlikte çalışma derlemelerini düzenleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2674-126">[How to: Edit Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8zbc969t(v=vs.100))</span></span>
- <span data-ttu-id="d2674-127">[Tür kitaplığını derlemeye dönüştürme Özeti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2674-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="d2674-128">Tlbimp. exe (tür kitaplığı Içeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="d2674-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="d2674-129">Tlbexp. exe (tür kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="d2674-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
