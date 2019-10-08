---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 6d281fe07754f0471f8d6c0e31cf3ea890060504
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005342"
---
# <a name="-optionstrict"></a><span data-ttu-id="22726-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="22726-102">-optionstrict</span></span>
<span data-ttu-id="22726-103">Örtük tür dönüşümlerini kısıtlamak için katı tür semantiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="22726-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22726-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="22726-104">Syntax</span></span>  
  
```console  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="22726-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="22726-105">Arguments</span></span>  
 <span data-ttu-id="22726-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="22726-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="22726-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="22726-107">Optional.</span></span> <span data-ttu-id="22726-108">@No__t-0 seçeneği örtük tür dönüştürmeyi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="22726-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="22726-109">Bu seçenek için varsayılan değer `-optionstrict-` ' dır.</span><span class="sxs-lookup"><span data-stu-id="22726-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="22726-110">@No__t-0 seçeneği, `-optionstrict` ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="22726-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="22726-111">Hem izin veren tür semantiğinin hem de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22726-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="22726-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="22726-112">Required.</span></span> <span data-ttu-id="22726-113">Katı dil semantiklerine uyulmadığında uyar.</span><span class="sxs-lookup"><span data-stu-id="22726-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22726-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="22726-114">Remarks</span></span>  
 <span data-ttu-id="22726-115">@No__t-0 etkin olduğunda, yalnızca genişletme türü dönüşümleri örtülü olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="22726-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="22726-116">Bir tamsayı türü nesnesine `Decimal` tür nesnesi atama gibi örtülü daraltma türü dönüştürmeleri hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="22726-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="22726-117">Örtük daraltma türü dönüştürmeleri için uyarı oluşturmak üzere `-optionstrict:custom` kullanın.</span><span class="sxs-lookup"><span data-stu-id="22726-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="22726-118">Belirli uyarıları yok saymak için `-nowarn:numberlist` ve belirli uyarıları hata olarak değerlendirmek için `-warnaserror:numberlist` kullanın.</span><span class="sxs-lookup"><span data-stu-id="22726-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="22726-119">Visual Studio IDE 'de-OptionStrict öğesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="22726-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="22726-120">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22726-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="22726-121">**Proje** menüsünde Özellikler ' e tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="22726-121">On the **Project** menu, click **Properties.**</span></span>   
  
2. <span data-ttu-id="22726-122">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="22726-122">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="22726-123">**Seçenek katı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="22726-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="22726-124">Program aracılığıyla ayarlama-OptionStrict</span><span class="sxs-lookup"><span data-stu-id="22726-124">To set -optionstrict programmatically</span></span>  
  
- <span data-ttu-id="22726-125">Bkz. [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="22726-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22726-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="22726-126">Example</span></span>  
 <span data-ttu-id="22726-127">Aşağıdaki kod, `Test.vb` ' i katı tür semantiğini kullanarak derler.</span><span class="sxs-lookup"><span data-stu-id="22726-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="22726-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22726-128">See also</span></span>

- [<span data-ttu-id="22726-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="22726-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="22726-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="22726-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="22726-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="22726-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="22726-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="22726-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="22726-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="22726-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="22726-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22726-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="22726-135">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="22726-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="22726-136">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="22726-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="22726-137">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="22726-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
