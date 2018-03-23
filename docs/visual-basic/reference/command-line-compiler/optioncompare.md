---
title: -optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 033be2ce3845ed470d56c2097b89b81d10275046
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-optioncompare"></a><span data-ttu-id="0cc82-102">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="0cc82-102">-optioncompare</span></span>
<span data-ttu-id="0cc82-103">Dize karşılaştırmaları nasıl yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0cc82-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc82-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cc82-104">Syntax</span></span>  
  
```  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="0cc82-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cc82-105">Remarks</span></span>  
 <span data-ttu-id="0cc82-106">Belirleyebileceğiniz `-optioncompare` iki forms birinde: `-optioncompare:binary` ikili dize karşılaştırmaları kullanmak için ve `-optioncompare:text` metin dize karşılaştırmaları kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="0cc82-106">You can specify `-optioncompare` in one of two forms: `-optioncompare:binary` to use binary string comparisons, and `-optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="0cc82-107">Varsayılan olarak, derleyici kullanır `-optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="0cc82-107">By default, the compiler uses `-optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="0cc82-108">Microsoft Windows'daki geçerli kod sayfası ikili sıralama düzenini belirler.</span><span class="sxs-lookup"><span data-stu-id="0cc82-108">In Microsoft Windows, the current code page determines the binary sort order.</span></span> <span data-ttu-id="0cc82-109">Tipik bir ikili sıralama aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0cc82-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="0cc82-110">Metin tabanlı dize karşılaştırmaları sisteminizin bölgeye göre belirlenir büyük küçük harf duyarsız metin sıralama düzenini temel alır.</span><span class="sxs-lookup"><span data-stu-id="0cc82-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="0cc82-111">Bir normal metin sıralama aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0cc82-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="0cc82-112">Visual Studio IDE'de - optioncompare ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0cc82-112">To set -optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="0cc82-113">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="0cc82-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0cc82-114">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="0cc82-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="0cc82-115">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="0cc82-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="0cc82-116">Değer değiştirme **seçeneği karşılaştırmak** kutusu.</span><span class="sxs-lookup"><span data-stu-id="0cc82-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set--optioncompare-programmatically"></a><span data-ttu-id="0cc82-117">-Optioncompare programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="0cc82-117">To set -optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="0cc82-118">Bkz: [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0cc82-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc82-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="0cc82-119">Example</span></span>  
 <span data-ttu-id="0cc82-120">Aşağıdaki kod derlerken `ProjFile.vb` ve ikili dize karşılaştırmalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="0cc82-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cc82-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0cc82-121">See Also</span></span>  
 [<span data-ttu-id="0cc82-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="0cc82-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0cc82-123">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="0cc82-123">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="0cc82-124">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="0cc82-124">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="0cc82-125">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="0cc82-125">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="0cc82-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="0cc82-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0cc82-127">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="0cc82-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="0cc82-128">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="0cc82-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
