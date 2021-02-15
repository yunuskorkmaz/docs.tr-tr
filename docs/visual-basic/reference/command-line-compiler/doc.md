---
description: Daha fazla bilgi edinin:-doc
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: da1ff6ad133dd2f46484b61ff73e1c6159eae557
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461430"
---
# <a name="-doc"></a><span data-ttu-id="e6c04-103">-doc</span><span class="sxs-lookup"><span data-stu-id="e6c04-103">-doc</span></span>

<span data-ttu-id="e6c04-104">Belge açıklamalarını bir XML dosyasına işler.</span><span class="sxs-lookup"><span data-stu-id="e6c04-104">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6c04-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6c04-105">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="e6c04-106">veya</span><span class="sxs-lookup"><span data-stu-id="e6c04-106">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6c04-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="e6c04-107">Arguments</span></span>  
  
|<span data-ttu-id="e6c04-108">Terim</span><span class="sxs-lookup"><span data-stu-id="e6c04-108">Term</span></span>|<span data-ttu-id="e6c04-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="e6c04-109">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e6c04-110">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e6c04-110">`+` &#124; `-`</span></span>|<span data-ttu-id="e6c04-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e6c04-111">Optional.</span></span> <span data-ttu-id="e6c04-112">Yalnızca + veya belirtildiğinde `-doc` , derleyicinin belge bilgilerini oluşturmasına ve BIR XML dosyasına yerleştirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="e6c04-112">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="e6c04-113">Belirtildiğinde `-` `-doc` , hiçbir belge bilgisinin oluşturulmamasına neden olmayan bir değer belirtilmiyor.</span><span class="sxs-lookup"><span data-stu-id="e6c04-113">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="e6c04-114">Kullanılıyorsa gereklidir `-doc:` .</span><span class="sxs-lookup"><span data-stu-id="e6c04-114">Required if `-doc:` is used.</span></span> <span data-ttu-id="e6c04-115">Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan çıkış XML dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6c04-115">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="e6c04-116">Dosya adı bir boşluk içeriyorsa, adı tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="e6c04-116">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6c04-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e6c04-117">Remarks</span></span>  

 <span data-ttu-id="e6c04-118">`-doc`Seçeneği, derleyicinin belge açıklamalarını içeren BIR XML dosyası oluşturup üretmediğini denetler.</span><span class="sxs-lookup"><span data-stu-id="e6c04-118">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="e6c04-119">`-doc:file`Söz dizimini kullanırsanız `file` PARAMETRESI, XML dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6c04-119">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="e6c04-120">`-doc`Veya kullanıyorsanız `-doc+` , derleyici XML dosya adını derleyicinin oluşturmakta olduğu yürütülebilir dosya veya kitaplıktan alır.</span><span class="sxs-lookup"><span data-stu-id="e6c04-120">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="e6c04-121">`-doc-`Seçeneğini kullanırsanız veya belirtmezseniz `-doc` , DERLEYICI bir XML dosyası oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="e6c04-121">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="e6c04-122">Kaynak kodu dosyalarında, belge açıklamaları aşağıdaki tanımlardan önce olabilir:</span><span class="sxs-lookup"><span data-stu-id="e6c04-122">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="e6c04-123">Bir [sınıf](../../language-reference/statements/class-statement.md) veya [arabirim](../../language-reference/statements/interface-statement.md) gibi Kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="e6c04-123">User-defined types, such as a [class](../../language-reference/statements/class-statement.md) or [interface](../../language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="e6c04-124">Alan, [olay](../../language-reference/statements/event-statement.md), [özellik](../../language-reference/statements/property-statement.md), [işlev](../../language-reference/statements/function-statement.md)veya alt [yordam](../../language-reference/statements/sub-statement.md)gibi Üyeler.</span><span class="sxs-lookup"><span data-stu-id="e6c04-124">Members, such as a field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md), or [subroutine](../../language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="e6c04-125">Oluşturulan XML dosyasını Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle birlikte kullanmak IÇIN, XML dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin.</span><span class="sxs-lookup"><span data-stu-id="e6c04-125">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="e6c04-126">XML dosyasının derlemeyle aynı dizinde olduğundan emin olun; böylece derlemeye Visual Studio projesinde başvuruluyorsa,. xml dosyası da bulunur.</span><span class="sxs-lookup"><span data-stu-id="e6c04-126">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="e6c04-127">IntelliSense 'in bir proje içinde veya bir proje tarafından başvurulan projelerde kod için çalışması için XML belge dosyaları gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e6c04-127">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="e6c04-128">İle derleme yapmadığınız takdirde `-target:module` , XML dosyası etiketleri içerir `<assembly></assembly>` .</span><span class="sxs-lookup"><span data-stu-id="e6c04-128">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="e6c04-129">Bu Etiketler, derlemenin çıkış dosyası için derleme bildirimini içeren dosyanın adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e6c04-129">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="e6c04-130">Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md) .</span><span class="sxs-lookup"><span data-stu-id="e6c04-130">See [XML Comment Tags](../../language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="e6c04-131">Visual Studio tümleşik geliştirme ortamında belge ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e6c04-131">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e6c04-132">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e6c04-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e6c04-133">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e6c04-133">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e6c04-134">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e6c04-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="e6c04-135">3. **XML belgesi oluştur dosyası** kutusunda değeri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e6c04-135">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e6c04-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6c04-136">Example</span></span>  

 <span data-ttu-id="e6c04-137">Bkz. bir örnek için [kodunuzu XML Ile belgeleme](../../programming-guide/program-structure/documenting-your-code-with-xml.md) .</span><span class="sxs-lookup"><span data-stu-id="e6c04-137">See [Documenting Your Code with XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6c04-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6c04-138">See also</span></span>

- [<span data-ttu-id="e6c04-139">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e6c04-139">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e6c04-140">XML ile Kodunuzu Belgeleme</span><span class="sxs-lookup"><span data-stu-id="e6c04-140">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
