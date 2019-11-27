---
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: fd0875f09bf3ba7211ede500aa0da45f8b7cd2c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344771"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="d285a-102">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d285a-102">-define (Visual Basic)</span></span>
<span data-ttu-id="d285a-103">Koşullu derleyici sabitlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d285a-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d285a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d285a-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="d285a-105">veya</span><span class="sxs-lookup"><span data-stu-id="d285a-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d285a-106">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d285a-106">Arguments</span></span>  
  
|<span data-ttu-id="d285a-107">Terim</span><span class="sxs-lookup"><span data-stu-id="d285a-107">Term</span></span>|<span data-ttu-id="d285a-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="d285a-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="d285a-109">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d285a-109">Required.</span></span> <span data-ttu-id="d285a-110">Tanımlanacak simge.</span><span class="sxs-lookup"><span data-stu-id="d285a-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="d285a-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="d285a-111">Optional.</span></span> <span data-ttu-id="d285a-112">`symbol`atanacak değer.</span><span class="sxs-lookup"><span data-stu-id="d285a-112">The value to assign `symbol`.</span></span> <span data-ttu-id="d285a-113">`value` bir dizeyse, tırnak işaretleri yerine ters eğik çizgi/tırnak işareti dizileri (\\") ile çevrelenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d285a-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="d285a-114">Hiçbir değer belirtilmemişse, true olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="d285a-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d285a-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d285a-115">Remarks</span></span>  
 <span data-ttu-id="d285a-116">`-define` seçeneği, kaynak dosyanızda `#Const` Önişlemci yönergesini kullanmayla benzer bir etkiye sahiptir, ancak `-define` ile tanımlanmış sabitler ortak olur ve projedeki tüm dosyalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d285a-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="d285a-117">Bu seçenek tarafından oluşturulan sembolleri, kaynak dosyaları koşullu olarak derlemek için `#If`...`Then`...`#Else` yönergesi ile kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d285a-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="d285a-118">`-d`, `-define`kısa bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="d285a-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="d285a-119">Sembol tanımlarını ayırmak için virgül kullanarak `-define` birden çok sembol tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d285a-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="d285a-120">Visual Studio tümleşik geliştirme ortamında/define ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d285a-120">To set /define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d285a-121">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d285a-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d285a-122">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d285a-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d285a-123">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d285a-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="d285a-124">3. **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="d285a-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="d285a-125">4. **Özel sabitler** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d285a-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d285a-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="d285a-126">Example</span></span>  
 <span data-ttu-id="d285a-127">Aşağıdaki kod, iki koşullu derleyici sabiti tanımlar ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="d285a-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="d285a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d285a-128">See also</span></span>

- [<span data-ttu-id="d285a-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d285a-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d285a-130">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="d285a-130">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="d285a-131">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="d285a-131">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="d285a-132">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="d285a-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
