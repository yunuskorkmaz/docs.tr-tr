---
title: 'Nasıl yapılır: Sarmalayıcıları Elle Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d61095e4e8c7f9b3795b751a5894de99d6ce8f99
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390269"
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="e3373-102">Nasıl yapılır: Sarmalayıcıları Elle Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3373-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="e3373-103">Yönetilen kaynak kodunda el ile COM türlerinizi karar verirseniz, başlatmak için en iyi varolan arabirimi tanım dili (IDL) dosyası ya da tür kitaplığı ile yerdir.</span><span class="sxs-lookup"><span data-stu-id="e3373-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="e3373-104">IDL dosya yok veya bir tür kitaplığı dosya oluşturulamıyor, yönetilen bildirimleri oluşturarak COM türlerini benzetimini yapabilirsiniz ve sonuçta elde edilen derleme için bir tür kitaplığı dışarı aktarma.</span><span class="sxs-lookup"><span data-stu-id="e3373-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="e3373-105">Yönetilen kaynak COM türlerinden benzetimini yapmak için</span><span class="sxs-lookup"><span data-stu-id="e3373-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="e3373-106">Ortak dil belirtimi (CLS) ile uyumlu olan bir dildeki türleri bildirme ve dosyasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="e3373-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="e3373-107">Türleriyle içeren derlemenin verme [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="e3373-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="e3373-108">Dışarı aktarılan COM tür kitaplığı yönetilen türleri COM odaklı bildirmek için temel olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="e3373-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="e3373-109">Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e3373-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="e3373-110">Bir IDL dosya veya türü kitaplık dosyası olmadığı varsayılarak, hangi sınıflar ve arabirimler özel RCW dahil etmek istediğiniz karar verin.</span><span class="sxs-lookup"><span data-stu-id="e3373-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="e3373-111">Doğrudan veya dolaylı olarak kullanmak için uygulamanızda düşünmüyorsanız türlerini hariç tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3373-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="e3373-112">CLS uyumlu bir dilde kaynak dosyası oluşturma ve türleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="e3373-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="e3373-113">Bkz: [derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) alma dönüştürme işlemini eksiksiz bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="e3373-113">See [Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)) for a complete description of the import conversion process.</span></span> <span data-ttu-id="e3373-114">Özel RCW oluşturduğunuzda, etkili bir şekilde el ile tarafından sağlanan tür dönüştürme etkinliği gerçekleştirdiğiniz [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="e3373-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="e3373-115">Sonraki bölümdeki örnek, bir IDL veya tür kitaplığı dosyasını ve bunların karşılık gelen türlerine C# kodunda türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3373-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="e3373-116">Bildirimleri tamamlandığı zaman, herhangi bir yönetilen kaynak kodu derleme gibi dosyasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="e3373-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="e3373-117">Türleriyle Tlbimp.exe ile içeri gibi bazı kodunuzu doğrudan ekleyebileceğiniz ek bilgi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e3373-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="e3373-118">Ayrıntılar için bkz [nasıl yapılır: Düzenle birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e3373-118">For details, see [How to: Edit Interop Assemblies](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3373-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="e3373-119">Example</span></span>  
 <span data-ttu-id="e3373-120">Aşağıdaki kod örneği gösterilmektedir `ISATest` arabirimi ve `SATest` IDL sınıfında ve karşılık gelen türlerine C# kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="e3373-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="e3373-121">**IDL veya türü kitaplık dosyası**</span><span class="sxs-lookup"><span data-stu-id="e3373-121">**IDL or type library file**</span></span>  
  
```  
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
  
 <span data-ttu-id="e3373-122">**Yönetilen kaynak kodunda sarmalayıcı**</span><span class="sxs-lookup"><span data-stu-id="e3373-122">**Wrapper in managed source code**</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3373-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e3373-123">See Also</span></span>  
 <span data-ttu-id="e3373-124">[Çalışma zamanı aranabilir sarmalayıcıları özelleştirme](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3373-124">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be(v=vs.100))</span></span>  
 <span data-ttu-id="e3373-125">[COM veri türleri](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3373-125">[COM Data Types](https://msdn.microsoft.com/library/f93ae35d-a416-4218-8700-c8218cc90061(v=vs.100))</span></span>  
 <span data-ttu-id="e3373-126">[Nasıl yapılır: Düzenle birlikte çalışma derlemeleri](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3373-126">[How to: Edit Interop Assemblies](https://msdn.microsoft.com/library/16aacb20-2269-42bf-a812-b6a7df17e277(v=vs.100))</span></span>  
 <span data-ttu-id="e3373-127">[Derleme dönüştürme özeti için tür kitaplığı](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3373-127">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))</span></span>  
 [<span data-ttu-id="e3373-128">Tlbimp.exe (Tür Kitaplığı İçeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="e3373-128">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="e3373-129">Tlbexp.exe (Tür Kitaplığı Dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="e3373-129">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
