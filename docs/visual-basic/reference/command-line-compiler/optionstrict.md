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
ms.openlocfilehash: e18fe451ea4a80ac959ed61b66394920f8bf177f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788940"
---
# <a name="-optionstrict"></a><span data-ttu-id="a5913-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="a5913-102">-optionstrict</span></span>
<span data-ttu-id="a5913-103">Örtük tür dönüştürmelerini kısıtlamak için katı türü anlamları zorlar.</span><span class="sxs-lookup"><span data-stu-id="a5913-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5913-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5913-104">Syntax</span></span>  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5913-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5913-105">Arguments</span></span>  
 <span data-ttu-id="a5913-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a5913-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="a5913-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="a5913-107">Optional.</span></span> <span data-ttu-id="a5913-108">`-optionstrict+` Seçeneği örtük tür dönüştürme kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="a5913-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="a5913-109">Bu seçenek için varsayılan değer `-optionstrict-`.</span><span class="sxs-lookup"><span data-stu-id="a5913-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="a5913-110">`-optionstrict+` Seçeneği aynıdır `-optionstrict`.</span><span class="sxs-lookup"><span data-stu-id="a5913-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="a5913-111">Esnek türü anlamları için her ikisini de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5913-111">You can use both for permissive type semantics.</span></span>  
  
 `custom`  
 <span data-ttu-id="a5913-112">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="a5913-112">Required.</span></span> <span data-ttu-id="a5913-113">Katı dil semantiği değil uymaya uyar.</span><span class="sxs-lookup"><span data-stu-id="a5913-113">Warn when strict language semantics are not respected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5913-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a5913-114">Remarks</span></span>  
 <span data-ttu-id="a5913-115">Zaman `-optionstrict+` kıyaslandığında geçerli tür dönüştürmelerine yalnızca bir örtülü olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5913-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="a5913-116">Örtük tür dönüştürmelerini atama gibi daraltma bir `Decimal` türü nesnesi bir tamsayı türü nesne, hata olarak raporlanır.</span><span class="sxs-lookup"><span data-stu-id="a5913-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>  
  
 <span data-ttu-id="a5913-117">Daraltma örtük tür dönüştürmelerini için Uyarılar oluşturmak için `-optionstrict:custom`.</span><span class="sxs-lookup"><span data-stu-id="a5913-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="a5913-118">Kullanım `-nowarn:numberlist` belirli uyarılarını gözardı etme ve `-warnaserror:numberlist` belirli uyarıları hata olarak değerlendirilecek.</span><span class="sxs-lookup"><span data-stu-id="a5913-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="a5913-119">-Optionstrict Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a5913-119">To set -optionstrict in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="a5913-120">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="a5913-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="a5913-121">Üzerinde **proje** menüsünü tıklatın **özellikleri.**</span><span class="sxs-lookup"><span data-stu-id="a5913-121">On the **Project** menu, click **Properties.**</span></span>   
  
2. <span data-ttu-id="a5913-122">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="a5913-122">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="a5913-123">Değer değiştirme **Option Strict** kutusu.</span><span class="sxs-lookup"><span data-stu-id="a5913-123">Modify the value in the **Option Strict** box.</span></span>  
  
### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="a5913-124">-Optionstrict program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a5913-124">To set -optionstrict programmatically</span></span>  
  
- <span data-ttu-id="a5913-125">Bkz: [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a5913-125">See [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5913-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5913-126">Example</span></span>  
 <span data-ttu-id="a5913-127">Aşağıdaki kod derlenir `Test.vb` katı tür semantiği kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a5913-127">The following code compiles `Test.vb` using strict type semantics.</span></span>  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5913-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5913-128">See also</span></span>

- [<span data-ttu-id="a5913-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a5913-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="a5913-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="a5913-130">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="a5913-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="a5913-131">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="a5913-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="a5913-132">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="a5913-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="a5913-133">-nowarn</span></span>](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [<span data-ttu-id="a5913-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5913-134">-warnaserror (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [<span data-ttu-id="a5913-135">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a5913-135">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="a5913-136">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="a5913-136">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="a5913-137">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="a5913-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
