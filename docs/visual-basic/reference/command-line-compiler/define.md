---
title: -tanımlama (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: c21223cc353b7a4614511aa97340c6bc5d61e70e
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200664"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="5ce83-102">-tanımlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ce83-102">-define (Visual Basic)</span></span>
<span data-ttu-id="5ce83-103">Koşullu derleyici sabitlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ce83-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce83-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ce83-104">Syntax</span></span>  
  
```  
-define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ce83-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5ce83-105">Arguments</span></span>  
  
|<span data-ttu-id="5ce83-106">Terim</span><span class="sxs-lookup"><span data-stu-id="5ce83-106">Term</span></span>|<span data-ttu-id="5ce83-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="5ce83-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="5ce83-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="5ce83-108">Required.</span></span> <span data-ttu-id="5ce83-109">Tanımlamak için simge.</span><span class="sxs-lookup"><span data-stu-id="5ce83-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="5ce83-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="5ce83-110">Optional.</span></span> <span data-ttu-id="5ce83-111">Atanacak değer `symbol`.</span><span class="sxs-lookup"><span data-stu-id="5ce83-111">The value to assign `symbol`.</span></span> <span data-ttu-id="5ce83-112">Varsa `value` bir dizedir, geçen dilerle ters eğik çizgi /-tırnak içine alınmalıdır (\\") tırnak işaretleri yerine.</span><span class="sxs-lookup"><span data-stu-id="5ce83-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="5ce83-113">Değer belirtilmezse sonra olacak şekilde gerçekleştirilen True.</span><span class="sxs-lookup"><span data-stu-id="5ce83-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ce83-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ce83-114">Remarks</span></span>  
 <span data-ttu-id="5ce83-115">`-define` Seçeneğinin etkisi bir kullanmaya benzer bir `#Const` önişlemci yönergesi ile tanımlanan, sabitleri dışında kaynak dosyanızdaki `-define` herkese açık ve projedeki tüm dosyalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5ce83-115">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="5ce83-116">Bu seçenekle tarafından oluşturulan simgeleri kullanabilirsiniz `#If`... `Then`... `#Else` yönergesi, kaynak dosyaları koşullu olarak derleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ce83-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="5ce83-117">`-d` öğesinin kısa biçimidir `-define`.</span><span class="sxs-lookup"><span data-stu-id="5ce83-117">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="5ce83-118">Birden çok sembolleriyle tanımlayabilirsiniz `-define` sembol tanımlarını ayırmak için virgül kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5ce83-118">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="5ce83-119">Ayarlama / Visual Studio tümleşik geliştirme ortamında tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="5ce83-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="5ce83-120">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="5ce83-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5ce83-121">Üzerinde **proje** menüsünü tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5ce83-121">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="5ce83-122">2.  Tıklayın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="5ce83-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="5ce83-123">3.  **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5ce83-123">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="5ce83-124">4.  Değer değiştirme **özel sabitleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="5ce83-124">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5ce83-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ce83-125">Example</span></span>  
 <span data-ttu-id="5ce83-126">Aşağıdaki kod, tanımlar ve sonra iki koşullu derleyici sabitlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5ce83-126">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="5ce83-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ce83-127">See also</span></span>
- [<span data-ttu-id="5ce83-128">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="5ce83-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5ce83-129">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5ce83-129">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="5ce83-130">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="5ce83-130">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="5ce83-131">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="5ce83-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
