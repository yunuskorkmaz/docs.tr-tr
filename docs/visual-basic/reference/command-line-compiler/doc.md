---
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: 13005eb55b430f6ff9b3a6408582a02e53838742
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824591"
---
# <a name="-doc"></a><span data-ttu-id="86730-102">-doc</span><span class="sxs-lookup"><span data-stu-id="86730-102">-doc</span></span>
<span data-ttu-id="86730-103">Belge yorumlarını bir XML dosyasına işler.</span><span class="sxs-lookup"><span data-stu-id="86730-103">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86730-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86730-104">Syntax</span></span>  
  
```  
-doc[+ | -]  
' -or-  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="86730-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="86730-105">Arguments</span></span>  
  
|<span data-ttu-id="86730-106">Terim</span><span class="sxs-lookup"><span data-stu-id="86730-106">Term</span></span>|<span data-ttu-id="86730-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="86730-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="86730-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="86730-108">`+` &#124; `-`</span></span>|<span data-ttu-id="86730-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="86730-109">Optional.</span></span> <span data-ttu-id="86730-110">Belirtme +, veya yalnızca `-doc`, derleyicinin belgelendirme bilgilerini oluşturmak ve bir XML dosyasında yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="86730-110">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="86730-111">Belirtme `-` eşdeğeri değildir belirtme `-doc`, oluşturulacak belge bilgi neden.</span><span class="sxs-lookup"><span data-stu-id="86730-111">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="86730-112">Gerekli if `-doc:` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86730-112">Required if `-doc:` is used.</span></span> <span data-ttu-id="86730-113">Kaynak kodu dosyaları derleme açıklamalardan doldurulur çıkış XML dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86730-113">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="86730-114">Dosya adı boşluk içeriyorsa adı tırnak işaretleri ile çevreleyen ("").</span><span class="sxs-lookup"><span data-stu-id="86730-114">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86730-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="86730-115">Remarks</span></span>  
 <span data-ttu-id="86730-116">`-doc` Seçeneği denetimleri olmadığını derleyici içeren belge yorumlarını bir XML dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="86730-116">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="86730-117">Kullanırsanız `-doc:file` söz dizimini `file` parametre XML dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="86730-117">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="86730-118">Kullanırsanız `-doc` veya `-doc+`, derleyicinin XML dosya adı yürütülebilir dosya veya derleyici oluşturma kitaplığından alır.</span><span class="sxs-lookup"><span data-stu-id="86730-118">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="86730-119">Kullanırsanız `-doc-` veya belirtmeyin `-doc` seçeneği, derleyicinin bir XML dosyası oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="86730-119">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="86730-120">Kaynak kodu dosyalarında belge açıklamaları aşağıdaki tanımları koyabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86730-120">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
-   <span data-ttu-id="86730-121">Kullanıcı tanımlı türleri, aşağıdaki gibi bir [sınıfı](../../../visual-basic/language-reference/statements/class-statement.md) veya [arabirimi](../../../visual-basic/language-reference/statements/interface-statement.md)</span><span class="sxs-lookup"><span data-stu-id="86730-121">User-defined types, such as a [class](../../../visual-basic/language-reference/statements/class-statement.md) or [interface](../../../visual-basic/language-reference/statements/interface-statement.md)</span></span>  
  
-   <span data-ttu-id="86730-122">Bir alan gibi bir üye [olay](../../../visual-basic/language-reference/statements/event-statement.md), [özelliği](../../../visual-basic/language-reference/statements/property-statement.md), [işlevi](../../../visual-basic/language-reference/statements/function-statement.md), veya [alt yordam](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="86730-122">Members, such as a field, [event](../../../visual-basic/language-reference/statements/event-statement.md), [property](../../../visual-basic/language-reference/statements/property-statement.md), [function](../../../visual-basic/language-reference/statements/function-statement.md), or [subroutine](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="86730-123">Visual Studio ile oluşturulan XML dosyasını kullanmak için [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, desteklemek istediğiniz derleme ile aynı olması, XML dosyasının dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="86730-123">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="86730-124">Visual Studio projesinde derlemeye başvurulduğundan, .xml dosyasını da bulunur, böylece XML dosyasını derleme olarak aynı dizinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="86730-124">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="86730-125">XML belge dosyaları, IntelliSense, kod bir proje veya içinde bir proje tarafından başvurulan projeler için çalışması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="86730-125">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="86730-126">Derleme sürece `/target:module`, etiket XML dosyasını içeren `<assembly></assembly>`.</span><span class="sxs-lookup"><span data-stu-id="86730-126">Unless you compile with `/target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="86730-127">Bu etiketler, derleme çıktı dosyası için derleme bildirimini içeren dosya adını belirtin.</span><span class="sxs-lookup"><span data-stu-id="86730-127">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="86730-128">Bkz: [XML açıklama etiketleri](../../../visual-basic/language-reference/xmldoc/index.md) kodunuza yorumlar gelen belgeleri oluşturmak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="86730-128">See [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="86730-129">Ayarlanacak - doc Visual Studio tümleşik geliştirme ortamı</span><span class="sxs-lookup"><span data-stu-id="86730-129">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="86730-130">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="86730-130">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="86730-131">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="86730-131">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="86730-132">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="86730-132">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="86730-133">3.  Değer kümesindeki **oluşturmak XML belge dosyası** kutusu.</span><span class="sxs-lookup"><span data-stu-id="86730-133">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86730-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="86730-134">Example</span></span>  
 <span data-ttu-id="86730-135">Bkz: [kodunuzu belgeleme XML ile](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="86730-135">See [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86730-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86730-136">See also</span></span>

- [<span data-ttu-id="86730-137">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="86730-137">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="86730-138">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="86730-138">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
