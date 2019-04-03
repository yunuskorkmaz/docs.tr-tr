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
ms.openlocfilehash: 0c23a74f91cd6666a0c4bef5ea67c58430c511b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819423"
---
# <a name="-optioncompare"></a><span data-ttu-id="ce6bc-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="ce6bc-102">-optioncompare</span></span>
<span data-ttu-id="ce6bc-103">Dize karşılaştırmaları nasıl yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce6bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce6bc-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce6bc-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce6bc-105">Remarks</span></span>  
 <span data-ttu-id="ce6bc-106">Belirtebileceğiniz `-optioncompare` içindeki iki farklı: `-optioncompare:binary` ikili dize karşılaştırmaları, kullanılacak ve `-optioncompare:text` metin dize karşılaştırmaları kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="ce6bc-107">Varsayılan olarak, derleyicinin kullandığı `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="ce6bc-108">Microsoft Windows içinde mevcut kod sayfasında ikili sıralama düzenini belirler.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="ce6bc-109">Tipik ikili sıralama düzeninde aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ce6bc-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="ce6bc-110">Metin tabanlı dize karşılaştırmaları büyük/küçük harfe metin sıralama düzeni, sisteminizin yerel ayarı tarafından belirlenen temel alır.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="ce6bc-111">Normal metin sıralama düzeni aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ce6bc-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="ce6bc-112">-Optioncompare Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ce6bc-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="ce6bc-113">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ce6bc-114">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="ce6bc-115">Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="ce6bc-116">Değer değiştirme **Option Compare** kutusu.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="ce6bc-117">-Optioncompare program üzerinden ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ce6bc-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="ce6bc-118">Bkz: [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce6bc-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce6bc-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce6bc-119">Example</span></span>  
 <span data-ttu-id="ce6bc-120">Aşağıdaki kod derlenir `ProjFile.vb` ve ikili dize karşılaştırmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce6bc-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce6bc-121">See also</span></span>

- [<span data-ttu-id="ce6bc-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ce6bc-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ce6bc-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="ce6bc-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [<span data-ttu-id="ce6bc-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="ce6bc-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [<span data-ttu-id="ce6bc-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="ce6bc-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="ce6bc-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ce6bc-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="ce6bc-127">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce6bc-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="ce6bc-128">Visual Basic Varsayılanları, Projeler, Seçenekler İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="ce6bc-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
