---
description: Daha fazla bilgi edinin:-optionfer
title: -optioninfer
ms.date: 07/20/2015
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
ms.openlocfilehash: d45761914612a28788cc5c1a848d92238f05c162
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475922"
---
# <a name="-optioninfer"></a><span data-ttu-id="b8c9b-103">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="b8c9b-103">-optioninfer</span></span>

<span data-ttu-id="b8c9b-104">Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-104">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8c9b-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b8c9b-105">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="b8c9b-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b8c9b-106">Arguments</span></span>  
  
|<span data-ttu-id="b8c9b-107">Terim</span><span class="sxs-lookup"><span data-stu-id="b8c9b-107">Term</span></span>|<span data-ttu-id="b8c9b-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="b8c9b-108">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="b8c9b-109">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b8c9b-109">`+` &#124; `-`</span></span>|<span data-ttu-id="b8c9b-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-110">Optional.</span></span> <span data-ttu-id="b8c9b-111">`-optioninfer+`Yerel tür çıkarımını etkinleştirmek veya engellemek için belirtin `-optioninfer-` .</span><span class="sxs-lookup"><span data-stu-id="b8c9b-111">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="b8c9b-112">`-optioninfer`Belirtilen değer olmadan seçeneği, ile aynıdır `-optioninfer+` .</span><span class="sxs-lookup"><span data-stu-id="b8c9b-112">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="b8c9b-113">Anahtar mevcut olmadığında varsayılan değer `-optioninfer` de vardır `-optioninfer+` .</span><span class="sxs-lookup"><span data-stu-id="b8c9b-113">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="b8c9b-114">Varsayılan değer Vbc. rsp yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-114">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b8c9b-115">`-noconfig`Söz konusu seçeneği, vbc. rsp ' de belirtilenler yerine derleyicinin iç varsayılan değerlerini koruma için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-115">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="b8c9b-116">Bu seçenek için varsayılan derleyicidir `-optioninfer-` .</span><span class="sxs-lookup"><span data-stu-id="b8c9b-116">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8c9b-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8c9b-117">Remarks</span></span>  

 <span data-ttu-id="b8c9b-118">Kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](../../language-reference/statements/option-infer-statement.md)içeriyorsa, ifade `-optioninfer` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-118">If the source code file contains an [Option Infer Statement](../../language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="b8c9b-119">Visual Studio IDE 'de set-OptionInfer</span><span class="sxs-lookup"><span data-stu-id="b8c9b-119">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="b8c9b-120">**Çözüm Gezgini** bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-120">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="b8c9b-121">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-121">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="b8c9b-122">**Derle** sekmesinde, **seçenek çıkarımı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8c9b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8c9b-123">Example</span></span>  

 <span data-ttu-id="b8c9b-124">Aşağıdaki kod, `test.vb` Yerel tür çıkarımı etkin ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8c9b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8c9b-125">See also</span></span>

- [<span data-ttu-id="b8c9b-126">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b8c9b-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b8c9b-127">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="b8c9b-127">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="b8c9b-128">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="b8c9b-128">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="b8c9b-129">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="b8c9b-129">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="b8c9b-130">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b8c9b-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="b8c9b-131">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="b8c9b-131">Option Infer Statement</span></span>](../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="b8c9b-132">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8c9b-132">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="b8c9b-133">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="b8c9b-133">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="b8c9b-134">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8c9b-134">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="b8c9b-135">-noconfig</span><span class="sxs-lookup"><span data-stu-id="b8c9b-135">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="b8c9b-136">Komut Satırından Derleme</span><span class="sxs-lookup"><span data-stu-id="b8c9b-136">Building from the Command Line</span></span>](building-from-the-command-line.md)
