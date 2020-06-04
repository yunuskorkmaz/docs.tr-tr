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
ms.openlocfilehash: d0d1b03d9ab98f28a0112198f1ecc1e928d6d4a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408718"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="3eac5-102">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3eac5-102">-define (Visual Basic)</span></span>
<span data-ttu-id="3eac5-103">Koşullu derleyici sabitlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3eac5-103">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eac5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3eac5-104">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="3eac5-105">veya</span><span class="sxs-lookup"><span data-stu-id="3eac5-105">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3eac5-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="3eac5-106">Arguments</span></span>  
  
|<span data-ttu-id="3eac5-107">Terim</span><span class="sxs-lookup"><span data-stu-id="3eac5-107">Term</span></span>|<span data-ttu-id="3eac5-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="3eac5-108">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="3eac5-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="3eac5-109">Required.</span></span> <span data-ttu-id="3eac5-110">Tanımlanacak simge.</span><span class="sxs-lookup"><span data-stu-id="3eac5-110">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="3eac5-111">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="3eac5-111">Optional.</span></span> <span data-ttu-id="3eac5-112">Atanacak değer `symbol` .</span><span class="sxs-lookup"><span data-stu-id="3eac5-112">The value to assign `symbol`.</span></span> <span data-ttu-id="3eac5-113">`value`Bir dizeyse, tırnak işaretleri yerine ters eğik çizgi/tırnak işareti dizileri ( \\ ") arasına alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3eac5-113">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="3eac5-114">Hiçbir değer belirtilmemişse, true olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="3eac5-114">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eac5-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3eac5-115">Remarks</span></span>  
 <span data-ttu-id="3eac5-116">`-define`Bu seçenek, kaynak dosyanızda ön işlemci yönergesini kullanmayla benzer bir etkiye sahiptir `#Const` , ancak ile tanımlanmış sabitler `-define` ortak olur ve projedeki tüm dosyalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3eac5-116">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="3eac5-117">Bu seçenek tarafından oluşturulan sembolleri `#If` .. `Then` . ile kullanabilirsiniz. ...`#Else` kaynak dosyaları koşullu olarak derlemek için yönerge.</span><span class="sxs-lookup"><span data-stu-id="3eac5-117">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="3eac5-118">`-d`, öğesinin kısa biçimidir `-define` .</span><span class="sxs-lookup"><span data-stu-id="3eac5-118">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="3eac5-119">`-define`Sembol tanımlarını ayırmak için virgül kullanarak birden çok sembol tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3eac5-119">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="3eac5-120">Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="3eac5-120">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="3eac5-121">1. **Çözüm Gezgini**bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3eac5-121">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3eac5-122">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3eac5-122">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="3eac5-123">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3eac5-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="3eac5-124">3. **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3eac5-124">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="3eac5-125">4. **Özel sabitler** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3eac5-125">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3eac5-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="3eac5-126">Example</span></span>  
 <span data-ttu-id="3eac5-127">Aşağıdaki kod, iki koşullu derleyici sabiti tanımlar ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="3eac5-127">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="3eac5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3eac5-128">See also</span></span>

- [<span data-ttu-id="3eac5-129">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="3eac5-129">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="3eac5-130">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="3eac5-130">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="3eac5-131">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="3eac5-131">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)
- [<span data-ttu-id="3eac5-132">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="3eac5-132">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
