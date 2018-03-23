---
title: -doc
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0948b9ef0675541ca595bb297e01e62c9d79a181
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-doc"></a><span data-ttu-id="effca-102">-doc</span><span class="sxs-lookup"><span data-stu-id="effca-102">-doc</span></span>
<span data-ttu-id="effca-103">Belge açıklamaları bir XML dosyasına işler.</span><span class="sxs-lookup"><span data-stu-id="effca-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="effca-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="effca-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="effca-105">Arguments</span></span>  
  
|<span data-ttu-id="effca-106">Terim</span><span class="sxs-lookup"><span data-stu-id="effca-106">Term</span></span>|<span data-ttu-id="effca-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="effca-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="effca-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="effca-108">`+` &#124; `-`</span></span>|<span data-ttu-id="effca-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="effca-109">Optional.</span></span> <span data-ttu-id="effca-110">Belirtme +, veya yalnızca `-doc`, belgeleri bilgileri oluşturmak ve bir XML dosyasında yerleştirmek derleyici neden olur.</span><span class="sxs-lookup"><span data-stu-id="effca-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="effca-111">Belirtme `-` değil belirtme eşdeğerdir `-doc`, hiçbir belge bilgiler oluşturulmasına neden.</span><span class="sxs-lookup"><span data-stu-id="effca-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="effca-112">Gerekli olursa `-doc:` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="effca-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="effca-113">Derleme kaynak kodu dosyaları açıklamalardan doldurulur çıkış XML dosyasının belirtir.</span><span class="sxs-lookup"><span data-stu-id="effca-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="effca-114">Dosya adı boşluk içeriyorsa adı tırnak işaretleri çevreleyen ("").</span><span class="sxs-lookup"><span data-stu-id="effca-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="effca-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="effca-115">Remarks</span></span>  
 <span data-ttu-id="effca-116">`-doc` Derleyici belge açıklamaları içeren bir XML dosyası oluşturur olup olmadığını kontrol eder seçeneği.</span><span class="sxs-lookup"><span data-stu-id="effca-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="effca-117">Kullanırsanız `-doc:file` sözdizimi, `file` parametresi, XML dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="effca-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="effca-118">Kullanırsanız `-doc` veya `-doc+`, derleyici XML dosya adı yürütülebilir dosya veya derleyici oluşturma kitaplığından alır.</span><span class="sxs-lookup"><span data-stu-id="effca-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="effca-119">Kullanırsanız `-doc-` veya belirtmeyin `-doc` seçeneği, derleyici bir XML dosyası oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="effca-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="effca-120">Kaynak kodu dosyaları belge açıklamaları aşağıdaki tanımları koyun:</span><span class="sxs-lookup"><span data-stu-id="effca-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="effca-121">Kullanıcı tanımlı türleri, aşağıdaki gibi bir [sınıfı](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirimi](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="effca-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="effca-122">Bir alan gibi üyeleri [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özelliği](../../../visual-basic/language-reference/statements/property-statement.md), [işlevi](../../../visual-basic/language-reference/statements/function-statement.md), veya [alt yordama](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="effca-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="effca-123">Oluşturulan XML dosyası ile kullanmak için [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, desteklemek istediğiniz derleme ile aynı olması, XML dosyasının dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="effca-123">To use the generated XML file with the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="effca-124">XML dosyası derleme ile aynı dizinde böylece zaman derleme başvuru olduğundan emin olun [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] proje, .xml dosyasını da bulunduğunda.</span><span class="sxs-lookup"><span data-stu-id="effca-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] project, the .xml file is found as well.</span></span> <span data-ttu-id="effca-125">XML belge dosyalarını kod projesi tarafından başvurulan projeleri veya bir proje içinde çalışmak IntelliSense için gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="effca-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="effca-126">İle derleme sürece `/target:module`, etiketler XML dosyasını içeren `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="effca-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="effca-127">Bu etiketler derleme çıktı dosyası için derleme bildirimi içeren dosyanın adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="effca-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="effca-128">Bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) yolları belgeleri açıklamaları kodunuzda oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="effca-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="effca-129">Belge Visual Studio tümleşik geliştirme ortamı ayarlamak için-</span><span class="sxs-lookup"><span data-stu-id="effca-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="effca-130">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="effca-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="effca-131">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="effca-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="effca-132">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="effca-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="effca-133">3.  Değer kümesinde **oluşturmak XML belge dosyası** kutusu.</span><span class="sxs-lookup"><span data-stu-id="effca-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="effca-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="effca-134">Example</span></span>  
 <span data-ttu-id="effca-135">Bkz: [kodunuzu belgeleme XML ile](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) bir örnek için.</span><span class="sxs-lookup"><span data-stu-id="effca-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effca-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="effca-136">See Also</span></span>  
 [<span data-ttu-id="effca-137">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="effca-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="effca-138">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="effca-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
