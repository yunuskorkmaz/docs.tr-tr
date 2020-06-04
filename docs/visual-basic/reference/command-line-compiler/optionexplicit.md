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
ms.openlocfilehash: b004acb0c1c7d145c59a1e3a88ef7f1d405a91c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400571"
---
# <a name="-optionexplicit"></a><span data-ttu-id="a18d2-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="a18d2-102">-optionexplicit</span></span>
<span data-ttu-id="a18d2-103">Değişkenler kullanılmadan önce bildirilmemiş olursa derleyicinin hata raporlamasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="a18d2-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a18d2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a18d2-104">Syntax</span></span>  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a18d2-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="a18d2-105">Arguments</span></span>  
 <span data-ttu-id="a18d2-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="a18d2-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a18d2-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a18d2-107">Optional.</span></span> <span data-ttu-id="a18d2-108">`-optionexplicit+`Değişkenlerin açık bildirimini gerektirmek için belirtin.</span><span class="sxs-lookup"><span data-stu-id="a18d2-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="a18d2-109">`-optionexplicit+`Varsayılan seçenektir ve ile aynıdır `-optionexplicit` .</span><span class="sxs-lookup"><span data-stu-id="a18d2-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="a18d2-110">`-optionexplicit-`Seçeneği, değişkenlerin örtülü bildirimini sunar.</span><span class="sxs-lookup"><span data-stu-id="a18d2-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a18d2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a18d2-111">Remarks</span></span>  
 <span data-ttu-id="a18d2-112">Kaynak kodu dosyası [açık bir seçenek ifade](../../language-reference/statements/option-explicit-statement.md)içeriyorsa, ifade `-optionexplicit` komut satırı derleyici ayarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="a18d2-112">If the source code file contains an [Option Explicit statement](../../language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="a18d2-113">Visual Studio IDE 'de ayarlamak için-OptionExplicit</span><span class="sxs-lookup"><span data-stu-id="a18d2-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="a18d2-114">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a18d2-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a18d2-115">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a18d2-115">On the **Project** menu, click **Properties**.</span></span>
  
2. <span data-ttu-id="a18d2-116">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a18d2-116">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="a18d2-117">**Açık** kutudaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="a18d2-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a18d2-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="a18d2-118">Example</span></span>  
 <span data-ttu-id="a18d2-119">Aşağıdaki kod, kullanıldığında derlenir `-optionexplicit-` .</span><span class="sxs-lookup"><span data-stu-id="a18d2-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="a18d2-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a18d2-120">See also</span></span>

- [<span data-ttu-id="a18d2-121">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a18d2-121">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a18d2-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="a18d2-122">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="a18d2-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="a18d2-123">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="a18d2-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="a18d2-124">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="a18d2-125">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a18d2-125">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="a18d2-126">Option Explicit Deyimi</span><span class="sxs-lookup"><span data-stu-id="a18d2-126">Option Explicit Statement</span></span>](../../language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="a18d2-127">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="a18d2-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
