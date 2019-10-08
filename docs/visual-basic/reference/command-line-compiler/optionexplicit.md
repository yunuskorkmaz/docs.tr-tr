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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005308"
---
# <a name="-optionexplicit"></a><span data-ttu-id="e8ddb-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e8ddb-102">-optionexplicit</span></span>
<span data-ttu-id="e8ddb-103">Değişkenler kullanılmadan önce bildirilmemiş olursa derleyicinin hata raporlamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ddb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8ddb-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e8ddb-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8ddb-105">Arguments</span></span>  
 <span data-ttu-id="e8ddb-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e8ddb-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e8ddb-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-107">Optional.</span></span> <span data-ttu-id="e8ddb-108">Değişkenlerin açık bildirimini gerektirmek için `-optionexplicit+` belirtin.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="e8ddb-109">@No__t-0 seçeneği varsayılandır ve `-optionexplicit` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="e8ddb-110">@No__t-0 seçeneği, değişkenlerin örtülü bildirimini sunar.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8ddb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8ddb-111">Remarks</span></span>  
 <span data-ttu-id="e8ddb-112">Kaynak kodu dosyası [açık bir seçenek ifade](../../../visual-basic/language-reference/statements/option-explicit-statement.md)içeriyorsa, ifade `-optionexplicit` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="e8ddb-113">Visual Studio IDE 'de ayarlamak için-OptionExplicit</span><span class="sxs-lookup"><span data-stu-id="e8ddb-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="e8ddb-114">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e8ddb-115">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-115">On the **Project** menu, click **Properties**.</span></span>   
  
2. <span data-ttu-id="e8ddb-116">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="e8ddb-117">**Açık** kutudaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8ddb-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8ddb-118">Example</span></span>  
 <span data-ttu-id="e8ddb-119">Aşağıdaki kod `-optionexplicit-` kullanıldığında derlenir.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e8ddb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8ddb-120">See also</span></span>

- [<span data-ttu-id="e8ddb-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="e8ddb-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e8ddb-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="e8ddb-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="e8ddb-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="e8ddb-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="e8ddb-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e8ddb-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="e8ddb-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="e8ddb-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="e8ddb-126">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="e8ddb-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="e8ddb-127">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="e8ddb-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
