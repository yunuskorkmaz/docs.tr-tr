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
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581412"
---
# <a name="-optioncompare"></a><span data-ttu-id="401c7-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="401c7-102">-optioncompare</span></span>

<span data-ttu-id="401c7-103">Dize karşılaştırmalarının nasıl yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="401c7-103">Specifies how string comparisons are made.</span></span>

## <a name="syntax"></a><span data-ttu-id="401c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="401c7-104">Syntax</span></span>

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a><span data-ttu-id="401c7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="401c7-105">Remarks</span></span>

<span data-ttu-id="401c7-106">İki formdan birini `-optioncompare` belirtebilirsiniz: `-optioncompare:binary` ikili dize karşılaştırmaları kullanmak ve `-optioncompare:text` metin dizesi karşılaştırmaları kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="401c7-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="401c7-107">Varsayılan olarak, derleyici kullanır `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="401c7-107">By default, the compiler uses `-optioncompare:binary`.</span></span>

<span data-ttu-id="401c7-108">Microsoft Windows 'da, geçerli kod sayfası ikili sıralama düzenini belirler.</span><span class="sxs-lookup"><span data-stu-id="401c7-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="401c7-109">Tipik bir ikili sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="401c7-109">A typical binary sort order is as follows:</span></span>

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

<span data-ttu-id="401c7-110">Metin tabanlı dize karşılaştırmaları, sisteminizin yerel ayarı tarafından belirlenen, büyük/küçük harfe duyarsız metin sıralama düzenini temel alır.</span><span class="sxs-lookup"><span data-stu-id="401c7-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="401c7-111">Tipik bir metin sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="401c7-111">A typical text sort order is as follows:</span></span>

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="401c7-112">Visual Studio IDE 'de set-OptionCompare</span><span class="sxs-lookup"><span data-stu-id="401c7-112">To set -optioncompare in the Visual Studio IDE</span></span>

1. <span data-ttu-id="401c7-113">**Çözüm Gezgini**' de bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="401c7-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="401c7-114">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="401c7-114">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="401c7-115">**Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="401c7-115">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="401c7-116">**Seçenek karşılaştırma** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="401c7-116">Modify the value in the **Option Compare** box.</span></span>

### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="401c7-117">Programlı olarak ayarlama-OptionCompare</span><span class="sxs-lookup"><span data-stu-id="401c7-117">To set -optioncompare programmatically</span></span>

<span data-ttu-id="401c7-118">Bkz. [Option Compare deyimin](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="401c7-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="401c7-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="401c7-119">Example</span></span>

<span data-ttu-id="401c7-120">Aşağıdaki kod derlenir `ProjFile.vb` ve ikili dize karşılaştırmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="401c7-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a><span data-ttu-id="401c7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="401c7-121">See also</span></span>

- [<span data-ttu-id="401c7-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="401c7-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="401c7-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="401c7-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="401c7-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="401c7-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="401c7-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="401c7-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="401c7-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="401c7-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="401c7-127">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="401c7-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="401c7-128">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="401c7-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
