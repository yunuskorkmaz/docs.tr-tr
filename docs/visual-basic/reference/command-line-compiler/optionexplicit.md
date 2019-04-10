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
ms.openlocfilehash: 54d438541e8840e4394b24b20b4f394ff8cdb820
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332397"
---
# <a name="-optionexplicit"></a><span data-ttu-id="81bb5-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="81bb5-102">-optionexplicit</span></span>
<span data-ttu-id="81bb5-103">Bunlar kullanılmadan önce değişkenleri bildirilmedikçe derleyici hatalarını raporlamak için neden olur.</span><span class="sxs-lookup"><span data-stu-id="81bb5-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81bb5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="81bb5-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="81bb5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="81bb5-105">Arguments</span></span>  
 `+` <span data-ttu-id="81bb5-106">&#124;</span><span class="sxs-lookup"><span data-stu-id="81bb5-106">&#124;</span></span> `-`  
 <span data-ttu-id="81bb5-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="81bb5-107">Optional.</span></span> <span data-ttu-id="81bb5-108">Belirtin `-optionexplicit+` değişkenleri açık bildirimini gerektiren.</span><span class="sxs-lookup"><span data-stu-id="81bb5-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="81bb5-109">`-optionexplicit+` Seçenek varsayılandır ve aynı `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="81bb5-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="81bb5-110">`-optionexplicit-` Örtük bir değişken bildirimi seçeneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="81bb5-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81bb5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="81bb5-111">Remarks</span></span>  
 <span data-ttu-id="81bb5-112">Kaynak kodu dosyası içeriyorsa bir [Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md), deyim geçersiz kılmalar `-optionexplicit` komut satırı derleyicisini ayarı.</span><span class="sxs-lookup"><span data-stu-id="81bb5-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="81bb5-113">-Optionexplicit Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="81bb5-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="81bb5-114">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="81bb5-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="81bb5-115">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="81bb5-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="81bb5-116">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="81bb5-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="81bb5-117">Değer değiştirme **Option Explicit** kutusu.</span><span class="sxs-lookup"><span data-stu-id="81bb5-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81bb5-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bb5-118">Example</span></span>  
 <span data-ttu-id="81bb5-119">Aşağıdaki kod zaman derler `-optionexplicit-` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="81bb5-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="81bb5-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="81bb5-120">See also</span></span>

- [<span data-ttu-id="81bb5-121">Visual Basic Komut Satırı Derleyicisi</span><span class="sxs-lookup"><span data-stu-id="81bb5-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="81bb5-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="81bb5-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="81bb5-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="81bb5-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="81bb5-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="81bb5-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="81bb5-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="81bb5-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="81bb5-126">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="81bb5-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="81bb5-127">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="81bb5-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
