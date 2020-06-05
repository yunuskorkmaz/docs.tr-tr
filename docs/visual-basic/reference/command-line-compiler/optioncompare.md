---
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
ms.openlocfilehash: ed9adc7cddd9eb204937b9819e4eeff176821e95
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400570"
---
# <a name="-optioncompare"></a><span data-ttu-id="cf414-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="cf414-102">-optioncompare</span></span>

<span data-ttu-id="cf414-103">Dize karşılaştırmalarının nasıl yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf414-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf414-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf414-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="cf414-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf414-105">Remarks</span></span>

<span data-ttu-id="cf414-106">`-optioncompare`İki formdan birini belirtebilirsiniz: `-optioncompare:binary` ikili dize karşılaştırmaları kullanmak ve `-optioncompare:text` metin dizesi karşılaştırmaları kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="cf414-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="cf414-107">Varsayılan olarak, derleyici kullanır `-optioncompare:binary` .</span><span class="sxs-lookup"><span data-stu-id="cf414-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="cf414-108">Microsoft Windows 'da, geçerli kod sayfası ikili sıralama düzenini belirler.</span><span class="sxs-lookup"><span data-stu-id="cf414-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="cf414-109">Tipik bir ikili sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cf414-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="cf414-110">Metin tabanlı dize karşılaştırmaları, sisteminizin yerel ayarı tarafından belirlenen, büyük/küçük harfe duyarsız metin sıralama düzenini temel alır.</span><span class="sxs-lookup"><span data-stu-id="cf414-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="cf414-111">Tipik bir metin sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="cf414-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="cf414-112">Visual Studio IDE 'de set-OptionCompare</span><span class="sxs-lookup"><span data-stu-id="cf414-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="cf414-113">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf414-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cf414-114">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cf414-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="cf414-115">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="cf414-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="cf414-116">**Seçenek karşılaştırma** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cf414-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="cf414-117">Programlı olarak ayarlama-OptionCompare</span><span class="sxs-lookup"><span data-stu-id="cf414-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="cf414-118">Bkz. [Option Compare deyimin](../../language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cf414-118">See [Option Compare Statement](../../language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf414-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="cf414-119">Example</span></span>

<span data-ttu-id="cf414-120">Aşağıdaki kod derlenir `ProjFile.vb` ve ikili dize karşılaştırmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="cf414-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="cf414-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf414-121">See also</span></span>

- [<span data-ttu-id="cf414-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="cf414-122">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="cf414-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="cf414-123">-optionexplicit</span></span>](optionexplicit.md)
- [<span data-ttu-id="cf414-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="cf414-124">-optionstrict</span></span>](optionstrict.md)
- [<span data-ttu-id="cf414-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="cf414-125">-optioninfer</span></span>](optioninfer.md)
- [<span data-ttu-id="cf414-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="cf414-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="cf414-127">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="cf414-127">Option Compare Statement</span></span>](../../language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="cf414-128">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="cf414-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
