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
# <a name="-optioninfer"></a><span data-ttu-id="42740-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="42740-102">-optioninfer</span></span>
<span data-ttu-id="42740-103">Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.</span><span class="sxs-lookup"><span data-stu-id="42740-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42740-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42740-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="42740-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="42740-105">Arguments</span></span>  
  
|<span data-ttu-id="42740-106">Sözleşme Dönemi</span><span class="sxs-lookup"><span data-stu-id="42740-106">Term</span></span>|<span data-ttu-id="42740-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="42740-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="42740-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="42740-108">`+` &#124; `-`</span></span>|<span data-ttu-id="42740-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="42740-109">Optional.</span></span> <span data-ttu-id="42740-110">Yerel `-optioninfer+` tür çıkarımını etkinleştirmek veya `-optioninfer-` engellemek için belirtin.</span><span class="sxs-lookup"><span data-stu-id="42740-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="42740-111">Belirtilen `-optioninfer` değer olmadan seçeneği, ile aynıdır `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="42740-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="42740-112">`-optioninfer` Anahtar mevcut olmadığında varsayılan değer de `-optioninfer+`vardır.</span><span class="sxs-lookup"><span data-stu-id="42740-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="42740-113">Varsayılan değer Vbc. rsp yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="42740-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="42740-114">Söz konusu seçeneği, `-noconfig` Vbc. rsp ' de belirtilenler yerine derleyicinin iç varsayılan değerlerini koruma için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42740-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="42740-115">Bu seçenek için varsayılan derleyicidir `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="42740-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42740-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42740-116">Remarks</span></span>  
 <span data-ttu-id="42740-117">Kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](../../../visual-basic/language-reference/statements/option-infer-statement.md)içeriyorsa, ifade `-optioninfer` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="42740-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="42740-118">Visual Studio IDE 'de set-OptionInfer</span><span class="sxs-lookup"><span data-stu-id="42740-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="42740-119">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="42740-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="42740-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="42740-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="42740-121">**Derle** sekmesinde, **seçenek çıkarımı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="42740-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42740-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="42740-122">Example</span></span>  
 <span data-ttu-id="42740-123">Aşağıdaki kod, yerel `test.vb` tür çıkarımı etkin ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="42740-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="42740-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42740-124">See also</span></span>

- [<span data-ttu-id="42740-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="42740-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="42740-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="42740-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="42740-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="42740-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="42740-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="42740-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="42740-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="42740-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="42740-130">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="42740-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="42740-131">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42740-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="42740-132">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="42740-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="42740-133">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42740-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="42740-134">-noconfig</span><span class="sxs-lookup"><span data-stu-id="42740-134">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="42740-135">Komut Satırından Derleme</span><span class="sxs-lookup"><span data-stu-id="42740-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
