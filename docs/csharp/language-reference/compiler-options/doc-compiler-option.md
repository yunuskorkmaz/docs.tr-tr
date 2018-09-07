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
ms.openlocfilehash: 24eb3b1a70c420fd0008ea9c202c774592e1d346
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44071641"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="d5da4-102">-doc (C# Derleyici Seçenekleri)</span><span class="sxs-lookup"><span data-stu-id="d5da4-102">-doc (C# Compiler Options)</span></span>
<span data-ttu-id="d5da4-103">**-Doc** seçenek belge yorumlarını bir XML dosyasında yerleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5da4-103">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5da4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5da4-104">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5da4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d5da4-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="d5da4-106">Çıkış dosyası için derleme kaynak kod dosyalarını yorumlarda doldurulur XML.</span><span class="sxs-lookup"><span data-stu-id="d5da4-106">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5da4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5da4-107">Remarks</span></span>  
 <span data-ttu-id="d5da4-108">Kaynak kodu dosyalarında aşağıdaki önünde belge açıklamaları işlenir ve XML dosyasına eklendi:</span><span class="sxs-lookup"><span data-stu-id="d5da4-108">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
-   <span data-ttu-id="d5da4-109">Gibi kullanıcı tanımlı türler bir [sınıfı](../../../csharp/language-reference/keywords/class.md), [temsilci](../../../csharp/language-reference/keywords/delegate.md), veya [arabirimi](../../../csharp/language-reference/keywords/interface.md)</span><span class="sxs-lookup"><span data-stu-id="d5da4-109">Such user-defined types as a [class](../../../csharp/language-reference/keywords/class.md), [delegate](../../../csharp/language-reference/keywords/delegate.md), or [interface](../../../csharp/language-reference/keywords/interface.md)</span></span>  
  
-   <span data-ttu-id="d5da4-110">Bir alan olarak tür üyeleri [olay](../../../csharp/language-reference/keywords/event.md), [özelliği](../../../csharp/programming-guide/classes-and-structs/using-properties.md), veya yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5da4-110">Such members as a field, [event](../../../csharp/language-reference/keywords/event.md), [property](../../../csharp/programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="d5da4-111">Ana içeren kaynak kodu dosyasının çıkış önce XML öğesine var.</span><span class="sxs-lookup"><span data-stu-id="d5da4-111">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="d5da4-112">Oluşturulan .xml dosyası ile kullanılmak üzere [IntelliSense](/visualstudio/ide/using-intellisense) özelliği, aynı olması, istediğiniz .xml dosyasını emin olun ve desteklemek için derleme derleme olarak aynı dizinde olduğundan .xml dosyasının dosya adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5da4-112">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="d5da4-113">Bu nedenle, Visual Studio projesinde derlemeye başvurulduğundan, .xml dosyasını da bulunur.</span><span class="sxs-lookup"><span data-stu-id="d5da4-113">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="d5da4-114">Bkz: [kodu açıklamalarını sağlama](/visualstudio/ide/supplying-xml-code-comments) ve daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d5da4-114">See [Supplying Code Comments](/visualstudio/ide/supplying-xml-code-comments) and for more information.</span></span>  
  
 <span data-ttu-id="d5da4-115">Derleme sürece [-target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` içerecek \<derleme > \< /Assembly > etiketleri çıktı dosyası için derleme bildirimini içeren dosya adını belirtme derleme.</span><span class="sxs-lookup"><span data-stu-id="d5da4-115">Unless you compile with [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5da4-116">Doc seçenek, tüm giriş dosyaları için geçerlidir veya proje ayarlarında, projedeki tüm dosyalar.</span><span class="sxs-lookup"><span data-stu-id="d5da4-116">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="d5da4-117">Belge açıklamaları için belirli dosya veya kod bölümüne ilgili uyarıları devre dışı bırakmak için [#pragma Uyarısı](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span><span class="sxs-lookup"><span data-stu-id="d5da4-117">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="d5da4-118">Bkz: [belge açıklamaları için önerilen etiketler](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) kodunuza yorumlar gelen belgeleri oluşturmak yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="d5da4-118">See [Recommended Tags for Documentation Comments](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d5da4-119">Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d5da4-119">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d5da4-120">Projenin açın **özellikleri** sayfası.</span><span class="sxs-lookup"><span data-stu-id="d5da4-120">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="d5da4-121">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="d5da4-121">Click the **Build** tab.</span></span>  
  
3.  <span data-ttu-id="d5da4-122">Değiştirme **XML belge dosyası** özelliği.</span><span class="sxs-lookup"><span data-stu-id="d5da4-122">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="d5da4-123">Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5da4-123">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5da4-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5da4-124">See Also</span></span>  

- [<span data-ttu-id="d5da4-125">C# Derleyici Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d5da4-125">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="d5da4-126">Proje ve Çözüm Özelliklerini Yönetme</span><span class="sxs-lookup"><span data-stu-id="d5da4-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
