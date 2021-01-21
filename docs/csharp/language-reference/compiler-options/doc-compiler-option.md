---
description: -Doc (C# derleyici seçenekleri)
title: -Doc (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: e55b86e5b028fb871f309d80217477cfd164c106
ms.sourcegitcommit: f0eb7eeedf3ceec726499fa678786d03083214ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98629260"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="2fbca-103">-Doc (C# derleyici seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="2fbca-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="2fbca-104">**-Doc** seçeneği, belge AÇıKLAMALARıNı bir XML dosyasına eklemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fbca-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fbca-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2fbca-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="2fbca-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="2fbca-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="2fbca-107">Derlemenin kaynak kodu dosyalarındaki yorumlarla doldurulan XML için çıkış dosyası.</span><span class="sxs-lookup"><span data-stu-id="2fbca-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fbca-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fbca-108">Remarks</span></span>  

 <span data-ttu-id="2fbca-109">Kaynak kodu dosyalarında, aşağıdakilerden önce gelen belge açıklamaları işlenebilir ve XML dosyasına eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="2fbca-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="2fbca-110">Bir [sınıf](../keywords/class.md), [temsilci](../builtin-types/reference-types.md#the-delegate-type)veya [arabirim](../keywords/interface.md) olarak Kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="2fbca-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="2fbca-111">Alan, [olay](../keywords/event.md), [özellik](../../programming-guide/classes-and-structs/using-properties.md)veya yöntem olarak bu Üyeler</span><span class="sxs-lookup"><span data-stu-id="2fbca-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="2fbca-112">Main içeren kaynak kodu dosyası ilk olarak XML 'e çıktı.</span><span class="sxs-lookup"><span data-stu-id="2fbca-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="2fbca-113">[IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle kullanılmak üzere oluşturulan. xml dosyasını kullanmak için,. xml dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasına izin verin ve. xml dosyasının derlemeyle aynı dizinde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fbca-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="2fbca-114">Bu nedenle, Visual Studio projesinde derlemeye başvuruluyorsa. xml dosyası da bulunur.</span><span class="sxs-lookup"><span data-stu-id="2fbca-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="2fbca-115">Bkz. [kod açıklamaları sağlama](/visualstudio/ide/reference/generate-xml-documentation-comments) ve daha fazla bilgi.</span><span class="sxs-lookup"><span data-stu-id="2fbca-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="2fbca-116">[-Target: Module](./target-module-compiler-option.md)ile derlemediğiniz takdirde, derlemenin `file` \<assembly> \</assembly> Çıkış dosyası için derleme bildirimini içeren dosyanın adını belirten etiketler içerecektir.</span><span class="sxs-lookup"><span data-stu-id="2fbca-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fbca-117">-Doc seçeneği tüm giriş dosyaları için geçerlidir; veya proje ayarları 'nda ayarlandıysa, projedeki tüm dosyalar.</span><span class="sxs-lookup"><span data-stu-id="2fbca-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="2fbca-118">Belirli bir dosyanın veya kod bölümünün belge açıklamalarıyla ilgili uyarıları devre dışı bırakmak için [#pragma uyarı](../preprocessor-directives/preprocessor-pragma-warning.md)kullanın.</span><span class="sxs-lookup"><span data-stu-id="2fbca-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="2fbca-119">Kodunuzda açıklamalardan belge oluşturma yolları için bkz. [belge açıklamaları Için önerilen Etiketler](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) .</span><span class="sxs-lookup"><span data-stu-id="2fbca-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-2019-development-environment"></a><span data-ttu-id="2fbca-120">Visual Studio 2019 geliştirme ortamında bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2fbca-120">To set this compiler option in the Visual Studio 2019 development environment</span></span>  

1. <span data-ttu-id="2fbca-121">Projenin **Özellikler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="2fbca-121">Open the project's **Properties** page.</span></span>  
2. <span data-ttu-id="2fbca-122">**Derleme** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2fbca-122">Click the **Build** tab.</span></span>
3. <span data-ttu-id="2fbca-123">**XML belge dosyası** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2fbca-123">Modify the **XML documentation file** property.</span></span>
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-for-mac-development-environment"></a><span data-ttu-id="2fbca-124">Mac için Visual Studio geliştirme ortamında bu derleyici seçeneğini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2fbca-124">To set this compiler option in the Visual Studio for Mac development environment</span></span>  
  
1. <span data-ttu-id="2fbca-125">Projenin **Seçenekler** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="2fbca-125">Open the project's **Options** page.</span></span>
2. <span data-ttu-id="2fbca-126">**Derleyici** sekmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2fbca-126">Select the **Compiler** tab.</span></span>
3. <span data-ttu-id="2fbca-127">**XML belgesi oluştur** ' u seçin ve metin kutusuna dosya adını girin.</span><span class="sxs-lookup"><span data-stu-id="2fbca-127">Select **Generate xml documentation** and enter the file name in the text box.</span></span>

<span data-ttu-id="2fbca-128">Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A> ..</span><span class="sxs-lookup"><span data-stu-id="2fbca-128">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbca-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbca-129">See also</span></span>

- [<span data-ttu-id="2fbca-130">C# derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2fbca-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2fbca-131">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="2fbca-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
