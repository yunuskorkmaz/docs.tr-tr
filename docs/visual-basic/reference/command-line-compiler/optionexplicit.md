---
description: Daha fazla bilgi edinin:-OptionExplicit
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
ms.openlocfilehash: 4d1ab14bbf9de176de17fb5077f4bb919f5472b4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433568"
---
# <a name="-optionexplicit"></a><span data-ttu-id="c415e-103">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="c415e-103">-optionexplicit</span></span>

<span data-ttu-id="c415e-104">Değişkenler kullanılmadan önce bildirilmemiş olursa derleyicinin hata raporlamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c415e-104">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c415e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c415e-105">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c415e-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="c415e-106">Arguments</span></span>  

 <span data-ttu-id="c415e-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c415e-107">`+` &#124; `-`</span></span>  
 <span data-ttu-id="c415e-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="c415e-108">Optional.</span></span> <span data-ttu-id="c415e-109">`-optionexplicit+`Değişkenlerin açık bildirimini gerektirmek için belirtin.</span><span class="sxs-lookup"><span data-stu-id="c415e-109">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="c415e-110">`-optionexplicit+`Varsayılan seçenektir ve ile aynıdır `-optionexplicit` .</span><span class="sxs-lookup"><span data-stu-id="c415e-110">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="c415e-111">`-optionexplicit-`Seçeneği, değişkenlerin örtülü bildirimini sunar.</span><span class="sxs-lookup"><span data-stu-id="c415e-111">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c415e-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c415e-112">Remarks</span></span>  

 <span data-ttu-id="c415e-113">Kaynak kodu dosyası [açık bir seçenek ifade](../../language-reference/statements/option-explicit-statement.md)içeriyorsa, ifade `-optionexplicit` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="c415e-113">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="c415e-114">Visual Studio IDE 'de ayarlamak için-OptionExplicit</span><span class="sxs-lookup"><span data-stu-id="c415e-114">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="c415e-115">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c415e-115">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c415e-116">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c415e-116">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="c415e-117">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c415e-117">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="c415e-118">**Açık** kutudaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c415e-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c415e-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="c415e-119">Example</span></span>  

 <span data-ttu-id="c415e-120">Aşağıdaki kod, kullanıldığında derlenir `-optionexplicit-` .</span><span class="sxs-lookup"><span data-stu-id="c415e-120">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c415e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c415e-121">See also</span></span>

- [<span data-ttu-id="c415e-122">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="c415e-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="c415e-123">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c415e-123">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="c415e-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="c415e-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="c415e-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="c415e-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="c415e-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="c415e-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="c415e-127">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="c415e-127">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="c415e-128">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="c415e-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
