---
description: :-OptionCompare hakkında daha fazla bilgi edinin
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: 9be4867c75cc16a8f699cf492dc41e9d08b96495
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475935"
---
# <a name="-optioncompare"></a><span data-ttu-id="add43-103">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="add43-103">-optioncompare</span></span>

<span data-ttu-id="add43-104">Dize karşılaştırmalarının nasıl yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="add43-104">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="add43-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="add43-105">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="add43-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="add43-106">Remarks</span></span>

<span data-ttu-id="add43-107">`-optioncompare`İki formdan birini belirtebilirsiniz: `-optioncompare:binary` ikili dize karşılaştırmaları kullanmak ve `-optioncompare:text` metin dizesi karşılaştırmaları kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="add43-107">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="add43-108">Varsayılan olarak, derleyici kullanır `-optioncompare:binary` .</span><span class="sxs-lookup"><span data-stu-id="add43-108">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="add43-109">Microsoft Windows 'da, geçerli kod sayfası ikili sıralama düzenini belirler.</span><span class="sxs-lookup"><span data-stu-id="add43-109">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="add43-110">Tipik bir ikili sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="add43-110">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="add43-111">Metin tabanlı dize karşılaştırmaları, sisteminizin yerel ayarı tarafından belirlenen, büyük/küçük harfe duyarsız metin sıralama düzenini temel alır.</span><span class="sxs-lookup"><span data-stu-id="add43-111">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="add43-112">Tipik bir metin sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="add43-112">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="add43-113">Visual Studio IDE 'de set-OptionCompare</span><span class="sxs-lookup"><span data-stu-id="add43-113">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="add43-114">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="add43-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="add43-115">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="add43-115">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="add43-116">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="add43-116">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="add43-117">**Seçenek karşılaştırma** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="add43-117">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="add43-118">Programlı olarak ayarlama-OptionCompare</span><span class="sxs-lookup"><span data-stu-id="add43-118">To set -optioncompare programmatically</span></span>

<span data-ttu-id="add43-119">Bkz. [Option Compare deyimin](../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="add43-119">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="add43-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="add43-120">Example</span></span>

<span data-ttu-id="add43-121">Aşağıdaki kod derlenir `ProjFile.vb` ve ikili dize karşılaştırmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="add43-121">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="add43-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="add43-122">See also</span></span>

- [<span data-ttu-id="add43-123">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="add43-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="add43-124">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="add43-124">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="add43-125">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="add43-125">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="add43-126">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="add43-126">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="add43-127">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="add43-127">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="add43-128">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="add43-128">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="add43-129">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="add43-129">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
