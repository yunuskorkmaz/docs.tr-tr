---
title: -doc (C# Derleyici Seçenekleri)
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
ms.openlocfilehash: 01ea71f3de9e30abe25184e38a59f3707b54bd5a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73422967"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="5465e-102">-doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="5465e-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="5465e-103">**-doc** seçeneği, belge açıklamalarını bir XML dosyasına yerleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5465e-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5465e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5465e-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="5465e-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="5465e-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="5465e-106">Derlemenin kaynak kodu dosyalarındaki açıklamalarla doldurulan XML'nin çıktı dosyası.</span><span class="sxs-lookup"><span data-stu-id="5465e-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5465e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5465e-107">Remarks</span></span>  
 <span data-ttu-id="5465e-108">Kaynak kod dosyalarında, aşağıdakilerden önce gelen dokümantasyon açıklamaları işlenebilir ve XML dosyasına eklenebilir:</span><span class="sxs-lookup"><span data-stu-id="5465e-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="5465e-109">[Sınıf,](../keywords/class.md) [temsilci](../builtin-types/reference-types.md#the-delegate-type)veya [arabirim](../keywords/interface.md) gibi kullanıcı tanımlı türler</span><span class="sxs-lookup"><span data-stu-id="5465e-109">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="5465e-110">Alan, [olay,](../keywords/event.md) [özellik](../../programming-guide/classes-and-structs/using-properties.md)veya yöntem gibi üyeler</span><span class="sxs-lookup"><span data-stu-id="5465e-110">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="5465e-111">Main'i içeren kaynak kod dosyası ilk olarak XML'e çıkar.</span><span class="sxs-lookup"><span data-stu-id="5465e-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="5465e-112">Oluşturulan .xml dosyasını [IntelliSense](/visualstudio/ide/using-intellisense) özelliğiyle kullanmak için kullanmak için ,.xml dosyasının dosya adının desteklemek istediğiniz derlemeyle aynı olmasını ve ardından .xml dosyasının derlemeyle aynı dizinde olduğundan emin olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5465e-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="5465e-113">Böylece, derleme Visual Studio projesinde başvurulduğunda, .xml dosyası da bulunur.</span><span class="sxs-lookup"><span data-stu-id="5465e-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="5465e-114">Bkz. [Kod Açıklamaları Sağlama](/visualstudio/ide/reference/generate-xml-documentation-comments) ve daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="5465e-114">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="5465e-115">[-target:module](./target-module-compiler-option.md)ile derlemediğiniz `file` sürece, \<derlemenin çıktı dosyası için derleme bildirimini içeren dosyanın adını belirten derleme>\</derleme> etiketleri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="5465e-115">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5465e-116">-doc seçeneği tüm giriş dosyaları için geçerlidir; veya Proje Ayarları'nda ayarlanmışsa, projedeki tüm dosyalar.</span><span class="sxs-lookup"><span data-stu-id="5465e-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="5465e-117">Belirli bir dosya veya kod bölümü için belge açıklamalarıyla ilgili uyarıları devre dışı kullanabilirsiniz, [#pragma uyarıkullanın.](../preprocessor-directives/preprocessor-pragma-warning.md)</span><span class="sxs-lookup"><span data-stu-id="5465e-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="5465e-118">Kodunuzdaki yorumlardan belge oluşturma yolları için [Belgeler Için Önerilen Etiketlere](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) bakın Açıklamalar.</span><span class="sxs-lookup"><span data-stu-id="5465e-118">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5465e-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5465e-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5465e-120">Projenin **Özellikleri** sayfasını açın.</span><span class="sxs-lookup"><span data-stu-id="5465e-120">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="5465e-121">**Yapı** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5465e-121">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="5465e-122">**XML dokümantasyon dosyası** özelliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5465e-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="5465e-123">Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A></span><span class="sxs-lookup"><span data-stu-id="5465e-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5465e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5465e-124">See also</span></span>

- [<span data-ttu-id="5465e-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="5465e-125">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5465e-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="5465e-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
