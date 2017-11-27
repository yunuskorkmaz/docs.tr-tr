---
title: "Nasıl yapılır: Derleme İçeriklerini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddbbf9fda01328986bf586203116fdabbcd9b55e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="c4727-102">Nasıl yapılır: Derleme İçeriklerini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c4727-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="c4727-103">Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) bir dosyada Microsoft Ara dili (MSIL) bilgilerini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="c4727-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="c4727-104">İncelenmesi dosyanın derleme olup, bu bilgileri derlemenin öznitelikleri yanı sıra diğer modüller ve derleme başvurularını ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4727-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="c4727-105">Bu bilgiler bir dosyayı bir derleme veya derleme parçası olmasına ve dosya derlemeleri veya diğer modüller başvurular olup saptamanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4727-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="c4727-106">Ildasm.exe kullanarak bir derlemeye içeriğini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c4727-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="c4727-107">Tür **ildasm** \< *derleme adı*> komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="c4727-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="c4727-108">Örneğin, aşağıdaki komutu ayrıştırır `Hello.exe` derleme.</span><span class="sxs-lookup"><span data-stu-id="c4727-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="c4727-109">Derleme bildirimi bilgilerini görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c4727-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="c4727-110">MSIL ayrıştırıcı penceresinde bildirim simgesini çift tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c4727-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4727-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c4727-111">Example</span></span>  
 <span data-ttu-id="c4727-112">Aşağıdaki örnek, temel bir "Hello, World" programla başlatır.</span><span class="sxs-lookup"><span data-stu-id="c4727-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="c4727-113">Program derledikten sonra Ildasm.exe Hello.exe derleme Ayır ve derleme bildirimi görüntülemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c4727-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="c4727-114">Komut ildasm.exe Hello.exe derleme üzerinde çalışan ve IL DASM penceresinde bildirim simgesini çift şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c4727-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="c4727-115">Aşağıdaki tabloda, her örnekte kullanılan Hello.exe derlemenin derleme bildirimi yönergesinde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c4727-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="c4727-116">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="c4727-116">Directive</span></span>|<span data-ttu-id="c4727-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c4727-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c4727-118">**.Assembly extern \<**  *derleme adı***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="c4727-119">Geçerli bir modül tarafından başvurulan öğeleri içeren başka bir derleme belirtir (Bu örnekte, `mscorlib`).</span><span class="sxs-lookup"><span data-stu-id="c4727-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="c4727-120">**.PublicKeyToken \<**  *belirteci***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="c4727-121">Başvurulan derlemeyi gerçek anahtarı belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="c4727-122">**.ver \<**  *sürüm numarası***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="c4727-123">Başvurulan derlemeyi sürüm numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="c4727-124">**.Assembly \<**  *derleme adı***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="c4727-125">Derleme adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="c4727-126">**.hash algoritması \<**  *Int32 değeri***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="c4727-127">Kullanılan karma algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="c4727-128">**.ver \<**  *sürüm numarası***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="c4727-129">Derlemenin sürüm numarasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="c4727-130">**.Module \<**  *dosya adı***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="c4727-131">Derlemeyi oluşturan modüllerin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="c4727-132">Bu örnekte, yalnızca bir dosyasından derleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="c4727-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="c4727-133">**.Subsystem \<**  *değeri***>**</span><span class="sxs-lookup"><span data-stu-id="c4727-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="c4727-134">Program için gereken uygulama ortamı belirtir.</span><span class="sxs-lookup"><span data-stu-id="c4727-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="c4727-135">Bu örnekte, bu yürütülebilir dosya bir konsoldan çalıştırıldığını 3 değeri gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4727-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="c4727-136">**.corflags**</span><span class="sxs-lookup"><span data-stu-id="c4727-136">**.corflags**</span></span>|<span data-ttu-id="c4727-137">Şu anda ayrılmış alan meta veriler.</span><span class="sxs-lookup"><span data-stu-id="c4727-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="c4727-138">Derleme bildirimi derleme içeriğini bağlı olarak farklı yönergeleri sayısı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c4727-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="c4727-139">Derleme bildirimi yönergeleri kapsamlı bir listesi için "özellikle Bölüm II: meta veri tanım ve semantik" ve "Bölüm III: CIL yönerge kümesi" ECMA belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="c4727-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="c4727-140">Belge çevrimiçi kullanılabilir; bkz: [ECMA C# ve ortak dil altyapısı standartları](http://go.microsoft.com/fwlink/?LinkID=99212) MSDN'de ve [standart ECMA-335 - ortak dil altyapısı (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) Ecma uluslararası Web sitesinde.</span><span class="sxs-lookup"><span data-stu-id="c4727-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4727-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c4727-141">See Also</span></span>  
 [<span data-ttu-id="c4727-142">Uygulama etki alanları ve derlemeler</span><span class="sxs-lookup"><span data-stu-id="c4727-142">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [<span data-ttu-id="c4727-143">Uygulama etki alanları ve derlemeler nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="c4727-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [<span data-ttu-id="c4727-144">Ildasm.exe (IL ayrıştırıcı)</span><span class="sxs-lookup"><span data-stu-id="c4727-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
