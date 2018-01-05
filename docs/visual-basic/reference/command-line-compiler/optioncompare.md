---
title: /optioncompare
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 62a9a4bf3428f3ee731e7ecc63be51dbf3076ee4
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="optioncompare"></a><span data-ttu-id="b3e49-102">/optioncompare</span><span class="sxs-lookup"><span data-stu-id="b3e49-102">/optioncompare</span></span>
<span data-ttu-id="b3e49-103">Dize karşılaştırmaları nasıl yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3e49-103">Specifies how string comparisons are made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3e49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3e49-104">Syntax</span></span>  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3e49-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3e49-105">Remarks</span></span>  
 <span data-ttu-id="b3e49-106">Belirleyebileceğiniz `/optioncompare` iki forms birinde: `/optioncompare:binary` ikili dize karşılaştırmaları kullanmak için ve `/optioncompare:text` metin dize karşılaştırmaları kullanmak için.</span><span class="sxs-lookup"><span data-stu-id="b3e49-106">You can specify `/optioncompare` in one of two forms: `/optioncompare:binary` to use binary string comparisons, and `/optioncompare:text` to use text string comparisons.</span></span> <span data-ttu-id="b3e49-107">Varsayılan olarak, derleyici kullanır `/optioncompare:binary`.</span><span class="sxs-lookup"><span data-stu-id="b3e49-107">By default, the compiler uses `/optioncompare:binary`.</span></span>  
  
 <span data-ttu-id="b3e49-108">Microsoft Windows'daki kullanılan kod sayfası ikili sıralama düzenini belirler.</span><span class="sxs-lookup"><span data-stu-id="b3e49-108">In Microsoft Windows, the code page being used determines the binary sort order.</span></span> <span data-ttu-id="b3e49-109">Tipik bir ikili sıralama aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b3e49-109">A typical binary sort order is as follows:</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="b3e49-110">Metin tabanlı dize karşılaştırmaları sisteminizin bölgeye göre belirlenir büyük küçük harf duyarsız metin sıralama düzenini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b3e49-110">Text-based string comparisons are based on a case-insensitive text sort order determined by your system's locale.</span></span> <span data-ttu-id="b3e49-111">Bir normal metin sıralama aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b3e49-111">A typical text sort order is as follows:</span></span>  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a><span data-ttu-id="b3e49-112">/ Optioncompare Visual Studio IDE'de ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b3e49-112">To set /optioncompare in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="b3e49-113">Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="b3e49-113">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b3e49-114">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="b3e49-114">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="b3e49-115">Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="b3e49-115">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="b3e49-116">Değer değiştirme **seçeneği karşılaştırmak** kutusu.</span><span class="sxs-lookup"><span data-stu-id="b3e49-116">Modify the value in the **Option Compare** box.</span></span>  
  
### <a name="to-set-optioncompare-programmatically"></a><span data-ttu-id="b3e49-117">/ Optioncompare programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b3e49-117">To set /optioncompare programmatically</span></span>  
  
-   <span data-ttu-id="b3e49-118">Bkz: [Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b3e49-118">See [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3e49-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3e49-119">Example</span></span>  
 <span data-ttu-id="b3e49-120">Aşağıdaki kod derlerken `ProjFile.vb` ve ikili dize karşılaştırmalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b3e49-120">The following code compiles `ProjFile.vb` and uses binary string comparisons.</span></span>  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3e49-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3e49-121">See Also</span></span>  
 [<span data-ttu-id="b3e49-122">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="b3e49-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b3e49-123">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="b3e49-123">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="b3e49-124">/optionstrict</span><span class="sxs-lookup"><span data-stu-id="b3e49-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="b3e49-125">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="b3e49-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="b3e49-126">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="b3e49-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="b3e49-127">Option Compare Deyimi</span><span class="sxs-lookup"><span data-stu-id="b3e49-127">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="b3e49-128">Visual Basic Varsayılanları, projeler, Seçenekler iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="b3e49-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
