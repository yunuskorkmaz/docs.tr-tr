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
# <a name="-optionexplicit"></a><span data-ttu-id="ad065-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="ad065-102">-optionexplicit</span></span>
<span data-ttu-id="ad065-103">Değişkenler kullanılmadan önce bildirilmemiş olursa derleyicinin hata raporlamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ad065-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad065-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad065-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad065-105">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ad065-105">Arguments</span></span>  
 <span data-ttu-id="ad065-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="ad065-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="ad065-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ad065-107">Optional.</span></span> <span data-ttu-id="ad065-108">Değişkenlerin `-optionexplicit+` açık bildirimini gerektirmek için belirtin.</span><span class="sxs-lookup"><span data-stu-id="ad065-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="ad065-109">Varsayılan `-optionexplicit+` seçenektir ve ile aynıdır `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="ad065-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="ad065-110">Seçeneği `-optionexplicit-` , değişkenlerin örtülü bildirimini sunar.</span><span class="sxs-lookup"><span data-stu-id="ad065-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad065-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad065-111">Remarks</span></span>  
 <span data-ttu-id="ad065-112">Kaynak kodu dosyası [açık bir seçenek ifade](../../../visual-basic/language-reference/statements/option-explicit-statement.md)içeriyorsa, ifade `-optionexplicit` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="ad065-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="ad065-113">Visual Studio IDE 'de ayarlamak için-OptionExplicit</span><span class="sxs-lookup"><span data-stu-id="ad065-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="ad065-114">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad065-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ad065-115">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ad065-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="ad065-116">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="ad065-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="ad065-117">**Açık** kutudaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ad065-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad065-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad065-118">Example</span></span>  
 <span data-ttu-id="ad065-119">Aşağıdaki kod, kullanıldığında derlenir `-optionexplicit-` .</span><span class="sxs-lookup"><span data-stu-id="ad065-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ad065-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad065-120">See also</span></span>

- [<span data-ttu-id="ad065-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ad065-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ad065-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="ad065-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="ad065-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="ad065-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="ad065-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="ad065-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="ad065-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ad065-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ad065-126">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="ad065-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="ad065-127">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="ad065-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
