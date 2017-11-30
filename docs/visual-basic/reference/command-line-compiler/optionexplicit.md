---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="1f877-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="1f877-102">/optionexplicit</span></span>
<span data-ttu-id="1f877-103">Kullanıldıkları önce değişkenleri bildirilmeyen, derleyici hatalarını raporlamak neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f877-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f877-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f877-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f877-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f877-105">Arguments</span></span>  
 <span data-ttu-id="1f877-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1f877-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="1f877-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="1f877-107">Optional.</span></span> <span data-ttu-id="1f877-108">Belirtin `/optionexplicit+` değişkenlerin açıkça bildirilmesini istemek için.</span><span class="sxs-lookup"><span data-stu-id="1f877-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="1f877-109">`/optionexplicit+` Seçenek varsayılandır ve aynı `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="1f877-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="1f877-110">`/optionexplicit-` Seçeneği değişkenlerin örtük bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f877-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f877-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f877-111">Remarks</span></span>  
 <span data-ttu-id="1f877-112">Kaynak kodu dosyasının içeriyorsa bir [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md), deyim için geçersiz kılar `/optionexplicit` komut satırı derleyicisi ayarı.</span><span class="sxs-lookup"><span data-stu-id="1f877-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="1f877-113">/ Optionexplicit Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="1f877-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="1f877-114">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="1f877-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1f877-115">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="1f877-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="1f877-116">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1f877-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="1f877-117">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="1f877-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="1f877-118">Değer değiştirme **Option Explicit** kutusu.</span><span class="sxs-lookup"><span data-stu-id="1f877-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f877-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f877-119">Example</span></span>  
 <span data-ttu-id="1f877-120">Aşağıdaki kod ne zaman derler `/optionexplicit-` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f877-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1f877-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f877-121">See Also</span></span>  
 [<span data-ttu-id="1f877-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="1f877-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="1f877-123">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="1f877-123">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="1f877-124">/ optionstrict</span><span class="sxs-lookup"><span data-stu-id="1f877-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="1f877-125">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="1f877-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="1f877-126">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="1f877-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="1f877-127">Option Explicit deyimi</span><span class="sxs-lookup"><span data-stu-id="1f877-127">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="1f877-128">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="1f877-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
