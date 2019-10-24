---
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d7209e431b84e52e487bccbf73bd633a346efde0
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775613"
---
# <a name="-optioninfer"></a><span data-ttu-id="2f416-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="2f416-102">-optioninfer</span></span>
<span data-ttu-id="2f416-103">Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.</span><span class="sxs-lookup"><span data-stu-id="2f416-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f416-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f416-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2f416-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2f416-105">Arguments</span></span>  
  
|<span data-ttu-id="2f416-106">Terim</span><span class="sxs-lookup"><span data-stu-id="2f416-106">Term</span></span>|<span data-ttu-id="2f416-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="2f416-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="2f416-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2f416-108">`+` &#124; `-`</span></span>|<span data-ttu-id="2f416-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2f416-109">Optional.</span></span> <span data-ttu-id="2f416-110">Yerel tür çıkarımını etkinleştirmek için `-optioninfer+` belirtin veya bunu engellemek için `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="2f416-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="2f416-111">Değer belirtilmemiş `-optioninfer` seçeneği, `-optioninfer+` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2f416-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="2f416-112">@No__t_0 anahtarı mevcut olmadığında varsayılan değer de `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="2f416-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="2f416-113">Varsayılan değer Vbc. rsp yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2f416-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2f416-114">@No__t_0 seçeneğini kullanarak, vbc. rsp ' de belirtiler yerine derleyicinin iç varsayılan ayarlarını koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f416-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="2f416-115">Bu seçenek için varsayılan derleyici `-optioninfer-` ' dır.</span><span class="sxs-lookup"><span data-stu-id="2f416-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f416-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f416-116">Remarks</span></span>  
 <span data-ttu-id="2f416-117">Kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](../../../visual-basic/language-reference/statements/option-infer-statement.md)içeriyorsa, ifade `-optioninfer` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2f416-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="2f416-118">Visual Studio IDE 'de set-OptionInfer</span><span class="sxs-lookup"><span data-stu-id="2f416-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="2f416-119">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="2f416-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="2f416-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="2f416-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="2f416-121">**Derle** sekmesinde, **seçenek çıkarımı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="2f416-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f416-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f416-122">Example</span></span>  
 <span data-ttu-id="2f416-123">Aşağıdaki kod, `test.vb` ' i yerel tür çıkarımı etkin ile derler.</span><span class="sxs-lookup"><span data-stu-id="2f416-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f416-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f416-124">See also</span></span>

- [<span data-ttu-id="2f416-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="2f416-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="2f416-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="2f416-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="2f416-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="2f416-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="2f416-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="2f416-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="2f416-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="2f416-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="2f416-130">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="2f416-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="2f416-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="2f416-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="2f416-132">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="2f416-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="2f416-133">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f416-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="2f416-134">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2f416-134">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="2f416-135">Komut Satırından Derleme</span><span class="sxs-lookup"><span data-stu-id="2f416-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
