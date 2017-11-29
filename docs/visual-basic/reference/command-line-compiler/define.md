---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a><span data-ttu-id="72a84-102">/define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72a84-102">/define (Visual Basic)</span></span>
<span data-ttu-id="72a84-103">Koşullu derleme sabitleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="72a84-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72a84-104">Syntax</span></span>  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="72a84-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="72a84-105">Arguments</span></span>  
  
|<span data-ttu-id="72a84-106">Terim</span><span class="sxs-lookup"><span data-stu-id="72a84-106">Term</span></span>|<span data-ttu-id="72a84-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="72a84-107">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="72a84-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="72a84-108">Required.</span></span> <span data-ttu-id="72a84-109">Tanımlamak için simge.</span><span class="sxs-lookup"><span data-stu-id="72a84-109">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="72a84-110">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="72a84-110">Optional.</span></span> <span data-ttu-id="72a84-111">Atanacak değer `symbol`.</span><span class="sxs-lookup"><span data-stu-id="72a84-111">The value to assign `symbol`.</span></span> <span data-ttu-id="72a84-112">Varsa `value` bir dizedir ters eğik çizgi /-tırnağından sıraları ile alınmalıdır (\\") tırnak işareti yerine.</span><span class="sxs-lookup"><span data-stu-id="72a84-112">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="72a84-113">Değer belirtilmedi sonra olması için geçen True.</span><span class="sxs-lookup"><span data-stu-id="72a84-113">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a84-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72a84-114">Remarks</span></span>  
 <span data-ttu-id="72a84-115">`/define` Seçeneği bir etkisi kullanmaya benzer bir `#Const` ile tanımlanmış bu sabitleri dışında kaynak dosyanızdaki önişlemci yönergesi `/define` ortak ve projedeki tüm dosyalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="72a84-115">The `/define` option has an effect  similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `/define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="72a84-116">Bu seçenek ile tarafından oluşturulan simgeleri kullanabilirsiniz `#If`... `Then`... `#Else` kaynak dosyaları koşullu derleme yönergesi.</span><span class="sxs-lookup"><span data-stu-id="72a84-116">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="72a84-117">`/d`kısa biçimi olan `/define`.</span><span class="sxs-lookup"><span data-stu-id="72a84-117">`/d` is the short form of `/define`.</span></span>  
  
 <span data-ttu-id="72a84-118">Birden çok sembolleriyle tanımlayabilirsiniz `/define` simge tanımlarını ayırmak için virgül kullanarak.</span><span class="sxs-lookup"><span data-stu-id="72a84-118">You can define multiple symbols with `/define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="72a84-119">Ayarlamak için Visual Studio tümleşik geliştirme ortamında tanımlayın</span><span class="sxs-lookup"><span data-stu-id="72a84-119">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="72a84-120">1.  Seçili bir projeyi **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="72a84-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="72a84-121">Üzerinde **proje** menüsünde tıklatın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="72a84-121">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="72a84-122">Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="72a84-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="72a84-123">2.  Tıklatın **derleme** sekmesi.</span><span class="sxs-lookup"><span data-stu-id="72a84-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="72a84-124">3.  **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="72a84-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="72a84-125">4.  Değer değiştirme **özel sabitleri** kutusu.</span><span class="sxs-lookup"><span data-stu-id="72a84-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="72a84-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="72a84-126">Example</span></span>  
 <span data-ttu-id="72a84-127">Aşağıdaki kod tanımlar ve iki koşullu derleyici sabitleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="72a84-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="72a84-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72a84-128">See Also</span></span>  
 [<span data-ttu-id="72a84-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="72a84-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="72a84-130">#If... Then... #Else yönergeleri</span><span class="sxs-lookup"><span data-stu-id="72a84-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="72a84-131">#Const yönergesi</span><span class="sxs-lookup"><span data-stu-id="72a84-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
 [<span data-ttu-id="72a84-132">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="72a84-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
