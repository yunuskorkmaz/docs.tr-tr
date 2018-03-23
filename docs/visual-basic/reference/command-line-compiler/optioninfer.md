---
title: -optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df01fccd7276f0ec759065306ad3614d735f89ef
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-optioninfer"></a><span data-ttu-id="3feb7-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="3feb7-102">-optioninfer</span></span>
<span data-ttu-id="3feb7-103">Yerel türü çıkarımı değişken bildirimlerden kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="3feb7-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3feb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3feb7-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3feb7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="3feb7-105">Arguments</span></span>  
  
|<span data-ttu-id="3feb7-106">Terim</span><span class="sxs-lookup"><span data-stu-id="3feb7-106">Term</span></span>|<span data-ttu-id="3feb7-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="3feb7-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="3feb7-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="3feb7-108">`+` &#124; `-`</span></span>|<span data-ttu-id="3feb7-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3feb7-109">Optional.</span></span> <span data-ttu-id="3feb7-110">Belirtin `-optioninfer+` yerel türü çıkarımı etkinleştirmek için veya `-optioninfer-` bunu engellemek için.</span><span class="sxs-lookup"><span data-stu-id="3feb7-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="3feb7-111">`-optioninfer` Seçeneği, belirtilen herhangi bir değer ile aynı olup `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="3feb7-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="3feb7-112">Varsayılan değer `-optioninfer` anahtar mevcut değil de `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="3feb7-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="3feb7-113">Varsayılan değer Vbc.rsp yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3feb7-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="3feb7-114">Kullanabileceğiniz `-noconfig` seçeneği vbc.rsp içinde belirtilen yerine derleyicinin iç Varsayılanları koruyun.</span><span class="sxs-lookup"><span data-stu-id="3feb7-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="3feb7-115">Bu seçenek için derleyici varsayılan değer `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="3feb7-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3feb7-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3feb7-116">Remarks</span></span>  
 <span data-ttu-id="3feb7-117">Kaynak kodu dosyasının içeriyorsa bir [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md), deyim için geçersiz kılar `-optioninfer` komut satırı derleyicisi ayarı.</span><span class="sxs-lookup"><span data-stu-id="3feb7-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="3feb7-118">Visual Studio IDE'de - optioninfer ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3feb7-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="3feb7-119">Bir projedeki seçin **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="3feb7-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="3feb7-120">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3feb7-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="3feb7-121">Üzerinde **derleme** sekmesinde, değeri Değiştir **Option Infer** kutusu.</span><span class="sxs-lookup"><span data-stu-id="3feb7-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3feb7-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="3feb7-122">Example</span></span>  
 <span data-ttu-id="3feb7-123">Aşağıdaki kod derlerken `test.vb` etkin yerel türü çıkarımı ile.</span><span class="sxs-lookup"><span data-stu-id="3feb7-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3feb7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3feb7-124">See Also</span></span>  
 [<span data-ttu-id="3feb7-125">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3feb7-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3feb7-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="3feb7-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="3feb7-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="3feb7-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="3feb7-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="3feb7-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="3feb7-129">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3feb7-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="3feb7-130">Option Infer Deyimi</span><span class="sxs-lookup"><span data-stu-id="3feb7-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="3feb7-131">Yerel Çıkarım</span><span class="sxs-lookup"><span data-stu-id="3feb7-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="3feb7-132">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="3feb7-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="3feb7-133">Derleme Sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3feb7-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="3feb7-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="3feb7-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="3feb7-135">Komut Satırından Derleme</span><span class="sxs-lookup"><span data-stu-id="3feb7-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
