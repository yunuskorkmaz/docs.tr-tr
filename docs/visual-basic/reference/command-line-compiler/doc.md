---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: a818fd46bd93682f0bede1d22b8cbc2ca6467a40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716735"
---
# <a name="-doc"></a><span data-ttu-id="06586-102">-doc</span><span class="sxs-lookup"><span data-stu-id="06586-102">-doc</span></span>
<span data-ttu-id="06586-103">Belge açıklamalarını bir XML dosyasına işler.</span><span class="sxs-lookup"><span data-stu-id="06586-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06586-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06586-104">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="06586-105">veya</span><span class="sxs-lookup"><span data-stu-id="06586-105">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="06586-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="06586-106">Arguments</span></span>  
  
|<span data-ttu-id="06586-107">Terim</span><span class="sxs-lookup"><span data-stu-id="06586-107">Term</span></span>|<span data-ttu-id="06586-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="06586-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="06586-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="06586-109">`+` &#124; `-`</span></span>|<span data-ttu-id="06586-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="06586-110">Optional.</span></span> <span data-ttu-id="06586-111">\+ Veya yalnızca `-doc`belirtme, derleyicinin belge bilgilerini oluşturmasını ve bir XML dosyasına yerleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="06586-111">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="06586-112">`-` belirtmek, `-doc`Belirtmemeye, hiçbir belge bilgisinin oluşturumamasına neden olan eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="06586-112">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="06586-113">`-doc:` kullanılıyorsa gereklidir.</span><span class="sxs-lookup"><span data-stu-id="06586-113">Required if `-doc:` is used.</span></span> <span data-ttu-id="06586-114">Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan çıkış XML dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06586-114">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="06586-115">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="06586-115">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06586-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06586-116">Remarks</span></span>  
 <span data-ttu-id="06586-117">`-doc` seçeneği, derleyicinin belge açıklamalarını içeren bir XML dosyası oluşturup oluşturmayacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="06586-117">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="06586-118">`-doc:file` sözdizimini kullanırsanız `file` parametresi, XML dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06586-118">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="06586-119">`-doc` veya `-doc+`kullanırsanız, derleyici XML dosya adını derleyicinin oluşturmakta olduğu yürütülebilir dosya veya kitaplıktan alır.</span><span class="sxs-lookup"><span data-stu-id="06586-119">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="06586-120">`-doc-` kullanırsanız veya `-doc` seçeneğini belirtmezseniz, derleyici bir XML dosyası oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="06586-120">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="06586-121">Kaynak kodu dosyalarında, belge açıklamaları aşağıdaki tanımlardan önce olabilir:</span><span class="sxs-lookup"><span data-stu-id="06586-121">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="06586-122">Bir [sınıf](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirim](../../../visual-basic/language-reference/statements/interface-statement.md) gibi Kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="06586-122">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="06586-123">Alan, [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özellik](../../../visual-basic/language-reference/statements/property-statement.md), [işlev](../../../visual-basic/language-reference/statements/function-statement.md)veya alt [yordam](../../../visual-basic/language-reference/statements/sub-statement.md)gibi Üyeler.</span><span class="sxs-lookup"><span data-stu-id="06586-123">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="06586-124">Oluşturulan XML dosyasını Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle birlikte kullanmak IÇIN, XML dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="06586-124">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="06586-125">XML dosyasının derlemeyle aynı dizinde olduğundan emin olun; böylece derlemeye Visual Studio projesinde başvuruluyorsa,. xml dosyası da bulunur.</span><span class="sxs-lookup"><span data-stu-id="06586-125">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="06586-126">IntelliSense 'in bir proje içinde veya bir proje tarafından başvurulan projelerde kod için çalışması için XML belge dosyaları gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="06586-126">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="06586-127">`-target:module`ile derlemediğiniz takdirde, XML dosyası `<assembly></assembly>`Etiketler içerir.</span><span class="sxs-lookup"><span data-stu-id="06586-127">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="06586-128">Bu Etiketler, derlemenin çıkış dosyası için derleme bildirimini içeren dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="06586-128">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="06586-129">Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/index.md) .</span><span class="sxs-lookup"><span data-stu-id="06586-129">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="06586-130">Visual Studio tümleşik geliştirme ortamında belge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="06586-130">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="06586-131">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="06586-131">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="06586-132">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="06586-132">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="06586-133">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="06586-133">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="06586-134">3. **XML belgesi oluştur dosyası** kutusunda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="06586-134">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="06586-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="06586-135">Example</span></span>  
 <span data-ttu-id="06586-136">Bkz. bir örnek için [kodunuzu XML Ile belgeleme](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) .</span><span class="sxs-lookup"><span data-stu-id="06586-136">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06586-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06586-137">See also</span></span>

- [<span data-ttu-id="06586-138">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="06586-138">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="06586-139">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="06586-139">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
