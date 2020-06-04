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
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400545"
---
# <a name="-optionstrict"></a><span data-ttu-id="04948-102">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="04948-102">-optionstrict</span></span>

<span data-ttu-id="04948-103">Örtük tür dönüşümlerini kısıtlamak için katı tür semantiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="04948-103">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="04948-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="04948-104">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="04948-105">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="04948-105">Arguments</span></span>

<span data-ttu-id="04948-106">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="04948-106">`+` &#124; `-`</span></span>  
<span data-ttu-id="04948-107">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="04948-107">Optional.</span></span> <span data-ttu-id="04948-108">`-optionstrict+`Seçeneği örtük tür dönüştürmeyi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="04948-108">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="04948-109">Bu seçenek için varsayılan değer `-optionstrict-` .</span><span class="sxs-lookup"><span data-stu-id="04948-109">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="04948-110">`-optionstrict+`Seçeneği ile aynıdır `-optionstrict` .</span><span class="sxs-lookup"><span data-stu-id="04948-110">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="04948-111">Hem izin veren tür semantiğinin hem de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04948-111">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="04948-112">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="04948-112">Required.</span></span> <span data-ttu-id="04948-113">Katı dil semantiklerine uyulmadığında uyar.</span><span class="sxs-lookup"><span data-stu-id="04948-113">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="04948-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04948-114">Remarks</span></span>

<span data-ttu-id="04948-115">`-optionstrict+`Etkin olduğunda, yalnızca genişleyen tür dönüştürmeleri örtülü olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="04948-115">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="04948-116">Bir tamsayı türü nesnesine bir tür nesnesi atama gibi örtülü daraltma tür dönüştürmeleri `Decimal` hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="04948-116">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="04948-117">Örtülü daraltma tür dönüştürmeleri için uyarı oluşturmak için kullanın `-optionstrict:custom` .</span><span class="sxs-lookup"><span data-stu-id="04948-117">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="04948-118">`-nowarn:numberlist`Belirli uyarıları yoksaymak ve `-warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="04948-118">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="04948-119">Visual Studio IDE 'de-OptionStrict öğesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="04948-119">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="04948-120">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04948-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="04948-121">**Proje** menüsünde Özellikler ' e tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="04948-121">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="04948-122">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="04948-122">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="04948-123">**Seçenek katı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="04948-123">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="04948-124">Program aracılığıyla ayarlama-OptionStrict</span><span class="sxs-lookup"><span data-stu-id="04948-124">To set -optionstrict programmatically</span></span>

<span data-ttu-id="04948-125">Bkz. [Option Strict deyimdir](../../language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="04948-125">See [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="04948-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="04948-126">Example</span></span>

<span data-ttu-id="04948-127">Aşağıdaki kod, `Test.vb` katı tür semantiğini kullanarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="04948-127">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="04948-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04948-128">See also</span></span>

- [<span data-ttu-id="04948-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="04948-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="04948-130">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="04948-130">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="04948-131">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="04948-131">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="04948-132">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="04948-132">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="04948-133">-nowarn</span><span class="sxs-lookup"><span data-stu-id="04948-133">-nowarn</span></span>](nowarn.md)
- [<span data-ttu-id="04948-134">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04948-134">-warnaserror (Visual Basic)</span></span>](warnaserror.md)
- [<span data-ttu-id="04948-135">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="04948-135">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="04948-136">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="04948-136">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="04948-137">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="04948-137">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
