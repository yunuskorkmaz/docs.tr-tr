---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 37ccd14dae0ebba2535185f2646e312d9bb70390
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266735"
---
# <a name="-optionexplicit"></a><span data-ttu-id="9ab0b-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="9ab0b-102">-optionexplicit</span></span>
<span data-ttu-id="9ab0b-103">Değişkenler kullanılmadan önce bildirilmemişse derleyicinin hataları bildirmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab0b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ab0b-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9ab0b-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9ab0b-105">Arguments</span></span>  
 <span data-ttu-id="9ab0b-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="9ab0b-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="9ab0b-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-107">Optional.</span></span> <span data-ttu-id="9ab0b-108">Değişkenlerin açık bildirimini gerektirecek şekilde belirtin. `-optionexplicit+`</span><span class="sxs-lookup"><span data-stu-id="9ab0b-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="9ab0b-109">Seçenek `-optionexplicit+` varsayılandır ve `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="9ab0b-110">Bu `-optionexplicit-` seçenek, değişkenlerin örtülü olarak beyan edilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ab0b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ab0b-111">Remarks</span></span>  
 <span data-ttu-id="9ab0b-112">Kaynak kod dosyası bir [Seçenek Açık deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md)içeriyorsa, deyim komut satırı derleyici ayarını `-optionexplicit` geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="9ab0b-113">Visual Studio IDE'de -optionexplicit'ı ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="9ab0b-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="9ab0b-114">**Çözüm Gezgini'nde**bir proje seçili var.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9ab0b-115">**Proje** menüsünde **Özellikler'i**tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="9ab0b-116">**Derle** sekmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="9ab0b-117">**Seçenek Açık** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab0b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ab0b-118">Example</span></span>  
 <span data-ttu-id="9ab0b-119">Aşağıdaki kod kullanıldığında `-optionexplicit-` derlenir.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="9ab0b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ab0b-120">See also</span></span>

- [<span data-ttu-id="9ab0b-121">Visual Basic Command-Line Derleyicisi</span><span class="sxs-lookup"><span data-stu-id="9ab0b-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9ab0b-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="9ab0b-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="9ab0b-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="9ab0b-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="9ab0b-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="9ab0b-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="9ab0b-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="9ab0b-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="9ab0b-126">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="9ab0b-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="9ab0b-127">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="9ab0b-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
