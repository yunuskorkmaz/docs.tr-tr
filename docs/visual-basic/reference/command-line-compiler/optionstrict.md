---
description: Daha fazla bilgi edinin:-OptionStrict
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: ad58c7775eaa77c1bf693629cf12cc70e4222920
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475909"
---
# <a name="-optionstrict"></a><span data-ttu-id="b4ec9-103">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="b4ec9-103">-optionstrict</span></span>

<span data-ttu-id="b4ec9-104">Örtük tür dönüşümlerini kısıtlamak için katı tür semantiğini zorlar.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-104">Enforces strict type semantics to restrict implicit type conversions.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4ec9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b4ec9-105">Syntax</span></span>

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a><span data-ttu-id="b4ec9-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b4ec9-106">Arguments</span></span>

<span data-ttu-id="b4ec9-107">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="b4ec9-107">`+` &#124; `-`</span></span>  
<span data-ttu-id="b4ec9-108">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-108">Optional.</span></span> <span data-ttu-id="b4ec9-109">`-optionstrict+`Seçeneği örtük tür dönüştürmeyi kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-109">The `-optionstrict+` option restricts implicit type conversion.</span></span> <span data-ttu-id="b4ec9-110">Bu seçenek için varsayılan değer `-optionstrict-` .</span><span class="sxs-lookup"><span data-stu-id="b4ec9-110">The default for this option is `-optionstrict-`.</span></span> <span data-ttu-id="b4ec9-111">`-optionstrict+`Seçeneği ile aynıdır `-optionstrict` .</span><span class="sxs-lookup"><span data-stu-id="b4ec9-111">The `-optionstrict+` option is the same as `-optionstrict`.</span></span> <span data-ttu-id="b4ec9-112">Hem izin veren tür semantiğinin hem de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-112">You can use both for permissive type semantics.</span></span>

`custom`  
<span data-ttu-id="b4ec9-113">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-113">Required.</span></span> <span data-ttu-id="b4ec9-114">Katı dil semantiklerine uyulmadığında uyar.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-114">Warn when strict language semantics are not respected.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4ec9-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4ec9-115">Remarks</span></span>

<span data-ttu-id="b4ec9-116">`-optionstrict+`Etkin olduğunda, yalnızca genişleyen tür dönüştürmeleri örtülü olarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-116">When `-optionstrict+` is in effect, only widening type conversions can be made implicitly.</span></span> <span data-ttu-id="b4ec9-117">Bir tamsayı türü nesnesine bir tür nesnesi atama gibi örtülü daraltma tür dönüştürmeleri `Decimal` hata olarak bildirilir.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-117">Implicit narrowing type conversions, such as assigning a `Decimal` type object to an integer type object, are reported as errors.</span></span>

<span data-ttu-id="b4ec9-118">Örtülü daraltma tür dönüştürmeleri için uyarı oluşturmak için kullanın `-optionstrict:custom` .</span><span class="sxs-lookup"><span data-stu-id="b4ec9-118">To generate warnings for implicit narrowing type conversions, use `-optionstrict:custom`.</span></span> <span data-ttu-id="b4ec9-119">`-nowarn:numberlist`Belirli uyarıları yoksaymak ve `-warnaserror:numberlist` belirli uyarıları hata olarak değerlendirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-119">Use `-nowarn:numberlist` to ignore particular warnings and `-warnaserror:numberlist` to treat particular warnings as errors.</span></span>

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a><span data-ttu-id="b4ec9-120">Visual Studio IDE 'de-OptionStrict öğesini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b4ec9-120">To set -optionstrict in the Visual Studio IDE</span></span>

1. <span data-ttu-id="b4ec9-121">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-121">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b4ec9-122">**Proje** menüsünde Özellikler ' e tıklayın **.**</span><span class="sxs-lookup"><span data-stu-id="b4ec9-122">On the **Project** menu, click **Properties.**</span></span>

2. <span data-ttu-id="b4ec9-123">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-123">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="b4ec9-124">**Seçenek katı** kutusunda değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-124">Modify the value in the **Option Strict** box.</span></span>

### <a name="to-set--optionstrict-programmatically"></a><span data-ttu-id="b4ec9-125">Program aracılığıyla ayarlama-OptionStrict</span><span class="sxs-lookup"><span data-stu-id="b4ec9-125">To set -optionstrict programmatically</span></span>

<span data-ttu-id="b4ec9-126">Bkz. [Option Strict deyimdir](../../language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b4ec9-126">See [Option Strict Statement](../../language-reference/statements/option-strict-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4ec9-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4ec9-127">Example</span></span>

<span data-ttu-id="b4ec9-128">Aşağıdaki kod, `Test.vb` katı tür semantiğini kullanarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-128">The following code compiles `Test.vb` using strict type semantics.</span></span>

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a><span data-ttu-id="b4ec9-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4ec9-129">See also</span></span>

- [<span data-ttu-id="b4ec9-130">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b4ec9-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="b4ec9-131">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="b4ec9-131">-optioncompare</span></span>](optioncompare.md)
- [<span data-ttu-id="b4ec9-132">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="b4ec9-132">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="b4ec9-133">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="b4ec9-133">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="b4ec9-134">-nowarn</span><span class="sxs-lookup"><span data-stu-id="b4ec9-134">-nowarn</span></span>](nowarn.md)
- [<span data-ttu-id="b4ec9-135">-warnaserror (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4ec9-135">-warnaserror (Visual Basic)</span></span>](warnaserror.md)
- [<span data-ttu-id="b4ec9-136">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b4ec9-136">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="b4ec9-137">Option Strict Deyimi</span><span class="sxs-lookup"><span data-stu-id="b4ec9-137">Option Strict Statement</span></span>](../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="b4ec9-138">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="b4ec9-138">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
