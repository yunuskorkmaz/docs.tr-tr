---
title: "Nasıl yapılır: Sarmalayıcıları Elle Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: wrappers, creating manually
ms.assetid: cc2a70d8-6a58-4071-a8cf-ce28c018c09b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19f605203a79f8435d414fb3c2eb7041c9824640
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-wrappers-manually"></a><span data-ttu-id="5aaa9-102">Nasıl yapılır: Sarmalayıcıları Elle Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5aaa9-102">How to: Create Wrappers Manually</span></span>
<span data-ttu-id="5aaa9-103">Yönetilen kaynak kodunda el ile COM türlerinizi karar verirseniz, başlatmak için en iyi varolan arabirimi tanım dili (IDL) dosyası ya da tür kitaplığı ile yerdir.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-103">If you decide to declare COM types manually in managed source code, the best place to start is with an existing Interface Definition Language (IDL) file or type library.</span></span> <span data-ttu-id="5aaa9-104">IDL dosya yok veya bir tür kitaplığı dosya oluşturulamıyor, yönetilen bildirimleri oluşturarak COM türlerini benzetimini yapabilirsiniz ve sonuçta elde edilen derleme için bir tür kitaplığı dışarı aktarma.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-104">When you do not have the IDL file or cannot generate a type library file, you can simulate the COM types by creating managed declarations and exporting the resulting assembly to a type library.</span></span>  
  
### <a name="to-simulate-com-types-from-managed-source"></a><span data-ttu-id="5aaa9-105">Yönetilen kaynak COM türlerinden benzetimini yapmak için</span><span class="sxs-lookup"><span data-stu-id="5aaa9-105">To simulate COM types from managed source</span></span>  
  
1.  <span data-ttu-id="5aaa9-106">Ortak dil belirtimi (CLS) ile uyumlu olan bir dildeki türleri bildirme ve dosyasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-106">Declare the types in a language that is compliant with the Common Language Specification (CLS) and compile the file.</span></span>  
  
2.  <span data-ttu-id="5aaa9-107">Türleriyle içeren derlemenin verme [tür kitaplığı dışarı Aktarıcı (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="5aaa9-107">Export the assembly containing the types with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
3.  <span data-ttu-id="5aaa9-108">Dışarı aktarılan COM tür kitaplığı yönetilen türleri COM odaklı bildirmek için temel olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-108">Use the exported COM type library as a basis for declaring COM-oriented managed types.</span></span>  
  
### <a name="to-create-a-runtime-callable-wrapper-rcw"></a><span data-ttu-id="5aaa9-109">Bir çalışma zamanı aranabilir sarmalayıcısı (RCW) oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5aaa9-109">To create a runtime callable wrapper (RCW)</span></span>  
  
1.  <span data-ttu-id="5aaa9-110">Bir IDL dosya veya türü kitaplık dosyası olmadığı varsayılarak, hangi sınıflar ve arabirimler özel RCW dahil etmek istediğiniz karar verin.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-110">Assuming that you have an IDL file or type library file, decide which classes and interfaces you want to include in the custom RCW.</span></span> <span data-ttu-id="5aaa9-111">Doğrudan veya dolaylı olarak kullanmak için uygulamanızda düşünmüyorsanız türlerini hariç tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-111">You can exclude any types that you do not intend to use directly or indirectly in your application.</span></span>  
  
2.  <span data-ttu-id="5aaa9-112">CLS uyumlu bir dilde kaynak dosyası oluşturma ve türleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-112">Create a source file in a CLS-compliant language and declare the types.</span></span> <span data-ttu-id="5aaa9-113">Bkz: [derleme dönüştürme özeti için tür kitaplığı](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) alma dönüştürme işlemini eksiksiz bir açıklaması.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-113">See [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958) for a complete description of the import conversion process.</span></span> <span data-ttu-id="5aaa9-114">Özel RCW oluşturduğunuzda, etkili bir şekilde el ile tarafından sağlanan tür dönüştürme etkinliği gerçekleştirdiğiniz [tür kitaplığı içeri Aktarıcı (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="5aaa9-114">Effectively, when you create a custom RCW, you are manually performing the type conversion activity provided by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="5aaa9-115">Sonraki bölümdeki örnek, bir IDL veya tür kitaplığı dosyasını ve bunların karşılık gelen türlerine C# kodunda türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-115">The example in the next section shows types in an IDL or type library file and their corresponding types in C# code.</span></span>  
  
3.  <span data-ttu-id="5aaa9-116">Bildirimleri tamamlandığı zaman, herhangi bir yönetilen kaynak kodu derleme gibi dosyasını derleyin.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-116">When the declarations are complete, compile the file as you compile any other managed source code.</span></span>  
  
4.  <span data-ttu-id="5aaa9-117">Türleriyle Tlbimp.exe ile içeri gibi bazı kodunuzu doğrudan ekleyebileceğiniz ek bilgi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-117">As with the types imported with Tlbimp.exe, some require additional information, which you can add directly to your code.</span></span> <span data-ttu-id="5aaa9-118">Ayrıntılar için bkz [nasıl yapılır: Düzenle birlikte çalışma derlemeleri](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277).</span><span class="sxs-lookup"><span data-stu-id="5aaa9-118">For details, see [How to: Edit Interop Assemblies](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5aaa9-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5aaa9-119">Example</span></span>  
 <span data-ttu-id="5aaa9-120">Aşağıdaki kod örneği gösterilmektedir `ISATest` arabirimi ve `SATest` IDL sınıfında ve karşılık gelen türlerine C# kaynak kodu.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-120">The following code shows an example of the `ISATest` interface and `SATest` class in IDL and the corresponding types in C# source code.</span></span>  
  
 <span data-ttu-id="5aaa9-121">**IDL veya türü kitaplık dosyası**</span><span class="sxs-lookup"><span data-stu-id="5aaa9-121">**IDL or type library file**</span></span>  
  
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
  
 <span data-ttu-id="5aaa9-122">**Yönetilen kaynak kodunda sarmalayıcı**</span><span class="sxs-lookup"><span data-stu-id="5aaa9-122">**Wrapper in managed source code**</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5aaa9-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5aaa9-123">See Also</span></span>  
 [<span data-ttu-id="5aaa9-124">Çalışma zamanı aranabilir sarmalayıcıları özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5aaa9-124">Customizing Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be)  
 [<span data-ttu-id="5aaa9-125">COM veri türleri</span><span class="sxs-lookup"><span data-stu-id="5aaa9-125">COM Data Types</span></span>](http://msdn.microsoft.com/en-us/f93ae35d-a416-4218-8700-c8218cc90061)  
 [<span data-ttu-id="5aaa9-126">Nasıl yapılır: Düzenle birlikte çalışma derlemeleri</span><span class="sxs-lookup"><span data-stu-id="5aaa9-126">How to: Edit Interop Assemblies</span></span>](http://msdn.microsoft.com/en-us/16aacb20-2269-42bf-a812-b6a7df17e277)  
 [<span data-ttu-id="5aaa9-127">Derleme dönüştürme özeti için tür kitaplığı</span><span class="sxs-lookup"><span data-stu-id="5aaa9-127">Type Library to Assembly Conversion Summary</span></span>](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [<span data-ttu-id="5aaa9-128">Tlbimp.exe (tür kitaplığı içeri Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="5aaa9-128">Tlbimp.exe (Type Library Importer)</span></span>](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [<span data-ttu-id="5aaa9-129">Tlbexp.exe (tür kitaplığı dışarı Aktarıcı)</span><span class="sxs-lookup"><span data-stu-id="5aaa9-129">Tlbexp.exe (Type Library Exporter)</span></span>](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
