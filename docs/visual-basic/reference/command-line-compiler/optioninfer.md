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
ms.openlocfilehash: 524660fca7c56fa490cc85169898bf2bf6d1a16e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400584"
---
# <a name="-optioninfer"></a><span data-ttu-id="c421b-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="c421b-102">-optioninfer</span></span>
<span data-ttu-id="c421b-103">Değişken bildirimlerinde yerel tür çıkarımı kullanımını mümkün.</span><span class="sxs-lookup"><span data-stu-id="c421b-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c421b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c421b-104">Syntax</span></span>  
  
```console  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c421b-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c421b-105">Arguments</span></span>  
  
|<span data-ttu-id="c421b-106">Terim</span><span class="sxs-lookup"><span data-stu-id="c421b-106">Term</span></span>|<span data-ttu-id="c421b-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c421b-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="c421b-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="c421b-108">`+` &#124; `-`</span></span>|<span data-ttu-id="c421b-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c421b-109">Optional.</span></span> <span data-ttu-id="c421b-110">`-optioninfer+`Yerel tür çıkarımını etkinleştirmek veya engellemek için belirtin `-optioninfer-` .</span><span class="sxs-lookup"><span data-stu-id="c421b-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="c421b-111">`-optioninfer`Belirtilen değer olmadan seçeneği, ile aynıdır `-optioninfer+` .</span><span class="sxs-lookup"><span data-stu-id="c421b-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="c421b-112">Anahtar mevcut olmadığında varsayılan değer `-optioninfer` de vardır `-optioninfer+` .</span><span class="sxs-lookup"><span data-stu-id="c421b-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="c421b-113">Varsayılan değer Vbc. rsp yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c421b-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c421b-114">`-noconfig`Söz konusu seçeneği, vbc. rsp ' de belirtilenler yerine derleyicinin iç varsayılan değerlerini koruma için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c421b-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="c421b-115">Bu seçenek için varsayılan derleyicidir `-optioninfer-` .</span><span class="sxs-lookup"><span data-stu-id="c421b-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c421b-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c421b-116">Remarks</span></span>  
 <span data-ttu-id="c421b-117">Kaynak kodu dosyası bir [seçenek çıkarımı bildirisi](../../language-reference/statements/option-infer-statement.md)içeriyorsa, ifade `-optioninfer` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c421b-117">If the source code file contains an [Option Infer Statement](../../language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="c421b-118">Visual Studio IDE 'de set-OptionInfer</span><span class="sxs-lookup"><span data-stu-id="c421b-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="c421b-119">**Çözüm Gezgini**bir proje seçin.</span><span class="sxs-lookup"><span data-stu-id="c421b-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="c421b-120">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c421b-120">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="c421b-121">**Derle** sekmesinde, **seçenek çıkarımı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c421b-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c421b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="c421b-122">Example</span></span>  
 <span data-ttu-id="c421b-123">Aşağıdaki kod, `test.vb` Yerel tür çıkarımı etkin ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="c421b-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c421b-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c421b-124">See also</span></span>

- [<span data-ttu-id="c421b-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c421b-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c421b-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c421b-126">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="c421b-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c421b-127">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="c421b-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="c421b-128">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="c421b-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c421b-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="c421b-130">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="c421b-130">Option Infer Statement</span></span>](../../language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="c421b-131">Yerel Tür Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c421b-131">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="c421b-132">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="c421b-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="c421b-133">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c421b-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="c421b-134">-noconfig</span><span class="sxs-lookup"><span data-stu-id="c421b-134">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="c421b-135">Komut Satırından Derleme</span><span class="sxs-lookup"><span data-stu-id="c421b-135">Building from the Command Line</span></span>](building-from-the-command-line.md)
