---
title: -optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ad78c82303d3655d5dda9e2286df0a55b8bf3e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-optionexplicit"></a><span data-ttu-id="affc9-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="affc9-102">-optionexplicit</span></span>
<span data-ttu-id="affc9-103">Kullanıldıkları önce değişkenleri bildirilmeyen, derleyici hatalarını raporlamak neden olur.</span><span class="sxs-lookup"><span data-stu-id="affc9-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="affc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="affc9-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="affc9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="affc9-105">Arguments</span></span>  
 <span data-ttu-id="affc9-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="affc9-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="affc9-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="affc9-107">Optional.</span></span> <span data-ttu-id="affc9-108">Belirtin `-optionexplicit+` değişkenlerin açıkça bildirilmesini istemek için.</span><span class="sxs-lookup"><span data-stu-id="affc9-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="affc9-109">`-optionexplicit+` Seçenek varsayılandır ve aynı `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="affc9-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="affc9-110">`-optionexplicit-` Seçeneği değişkenlerin örtük bildirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="affc9-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="affc9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="affc9-111">Remarks</span></span>  
 <span data-ttu-id="affc9-112">Kaynak kodu dosyasının içeriyorsa bir [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md), deyim için geçersiz kılar `-optionexplicit` komut satırı derleyicisi ayarı.</span><span class="sxs-lookup"><span data-stu-id="affc9-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="affc9-113">Visual Studio IDE'de - optionexplicit ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="affc9-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="affc9-114">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="affc9-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="affc9-115">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="affc9-115">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="affc9-116">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="affc9-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="affc9-117">Değer değiştirme **Option Explicit** kutusu.</span><span class="sxs-lookup"><span data-stu-id="affc9-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="affc9-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="affc9-118">Example</span></span>  
 <span data-ttu-id="affc9-119">Aşağıdaki kod ne zaman derler `-optionexplicit-` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="affc9-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="affc9-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="affc9-120">See Also</span></span>  
 [<span data-ttu-id="affc9-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="affc9-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="affc9-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="affc9-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="affc9-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="affc9-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="affc9-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="affc9-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="affc9-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="affc9-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="affc9-126">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="affc9-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="affc9-127">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="affc9-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
