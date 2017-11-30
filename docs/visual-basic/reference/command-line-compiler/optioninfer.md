---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4400ee58214c8f9990d4b123e17ef0f6553a5a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optioninfer"></a><span data-ttu-id="e30ba-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="e30ba-102">/optioninfer</span></span>
<span data-ttu-id="e30ba-103">Yerel türü çıkarımı değişken bildirimlerden kullanımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e30ba-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e30ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e30ba-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e30ba-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e30ba-105">Arguments</span></span>  
  
|<span data-ttu-id="e30ba-106">Terim</span><span class="sxs-lookup"><span data-stu-id="e30ba-106">Term</span></span>|<span data-ttu-id="e30ba-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="e30ba-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="e30ba-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e30ba-108">`+` &#124; `-`</span></span>|<span data-ttu-id="e30ba-109">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e30ba-109">Optional.</span></span> <span data-ttu-id="e30ba-110">Belirtin `/optioninfer+` yerel türü çıkarımı etkinleştirmek için veya `/optioninfer-` bunu engellemek için.</span><span class="sxs-lookup"><span data-stu-id="e30ba-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="e30ba-111">`/optioninfer` Seçeneği, belirtilen herhangi bir değer ile aynı olup `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="e30ba-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="e30ba-112">Varsayılan değer `/optioninfer` anahtar mevcut değil de `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="e30ba-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="e30ba-113">Varsayılan değer Vbc.rsp yanıt dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e30ba-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e30ba-114">Kullanabileceğiniz `/noconfig` seçeneği vbc.rsp içinde belirtilen yerine derleyicinin iç Varsayılanları koruyun.</span><span class="sxs-lookup"><span data-stu-id="e30ba-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="e30ba-115">Bu seçenek için derleyici varsayılan değer `/optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="e30ba-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e30ba-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e30ba-116">Remarks</span></span>  
 <span data-ttu-id="e30ba-117">Kaynak kodu dosyasının içeriyorsa bir [Option Infer deyimi](../../../visual-basic/language-reference/statements/option-infer-statement.md), deyim için geçersiz kılar `/optioninfer` komut satırı derleyicisi ayarı.</span><span class="sxs-lookup"><span data-stu-id="e30ba-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="e30ba-118">/ Optioninfer Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="e30ba-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e30ba-119">Bir projedeki seçin **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="e30ba-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="e30ba-120">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="e30ba-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="e30ba-121">Daha fazla bilgi için bkz: [NIB: Proje özellikleriyle yönetme Proje Tasarımcısı](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="e30ba-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="e30ba-122">Üzerinde **derleme** sekmesinde, değeri Değiştir **Option Infer** kutusu.</span><span class="sxs-lookup"><span data-stu-id="e30ba-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30ba-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="e30ba-123">Example</span></span>  
 <span data-ttu-id="e30ba-124">Aşağıdaki kod derlerken `test.vb` etkin yerel türü çıkarımı ile.</span><span class="sxs-lookup"><span data-stu-id="e30ba-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e30ba-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e30ba-125">See Also</span></span>  
 [<span data-ttu-id="e30ba-126">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e30ba-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e30ba-127">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="e30ba-127">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="e30ba-128">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e30ba-128">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="e30ba-129">/ optionstrict</span><span class="sxs-lookup"><span data-stu-id="e30ba-129">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="e30ba-130">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="e30ba-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e30ba-131">Option Infer deyimi</span><span class="sxs-lookup"><span data-stu-id="e30ba-131">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="e30ba-132">Yerel tür çıkarımı</span><span class="sxs-lookup"><span data-stu-id="e30ba-132">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="e30ba-133">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="e30ba-133">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="e30ba-134">Derle sayfası, Proje Tasarımcısı (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e30ba-134">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="e30ba-135">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="e30ba-135">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="e30ba-136">Komut satırından oluşturma</span><span class="sxs-lookup"><span data-stu-id="e30ba-136">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
