---
description: 'Hakkında daha fazla bilgi edinin: tanımlama (Visual Basic)'
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
ms.openlocfilehash: 9d6394ecad8e59d64ef3c51312ac85562ba3ec2c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466984"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="8e412-103">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e412-103">-define (Visual Basic)</span></span>

<span data-ttu-id="8e412-104">Koşullu derleyici sabitlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8e412-104">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e412-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e412-105">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="8e412-106">veya</span><span class="sxs-lookup"><span data-stu-id="8e412-106">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e412-107">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8e412-107">Arguments</span></span>  
  
|<span data-ttu-id="8e412-108">Terim</span><span class="sxs-lookup"><span data-stu-id="8e412-108">Term</span></span>|<span data-ttu-id="8e412-109">Tanım</span><span class="sxs-lookup"><span data-stu-id="8e412-109">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="8e412-110">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8e412-110">Required.</span></span> <span data-ttu-id="8e412-111">Tanımlanacak simge.</span><span class="sxs-lookup"><span data-stu-id="8e412-111">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="8e412-112">İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="8e412-112">Optional.</span></span> <span data-ttu-id="8e412-113">Atanacak değer `symbol` .</span><span class="sxs-lookup"><span data-stu-id="8e412-113">The value to assign `symbol`.</span></span> <span data-ttu-id="8e412-114">`value`Bir dizeyse, tırnak işaretleri yerine ters eğik çizgi/tırnak işareti dizileri ( \\ ") arasına alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e412-114">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="8e412-115">Hiçbir değer belirtilmemişse, true olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="8e412-115">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e412-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8e412-116">Remarks</span></span>  

 <span data-ttu-id="8e412-117">`-define`Bu seçenek, kaynak dosyanızda ön işlemci yönergesini kullanmayla benzer bir etkiye sahiptir `#Const` , ancak ile tanımlanmış sabitler `-define` ortak olur ve projedeki tüm dosyalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8e412-117">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="8e412-118">Bu seçenek tarafından oluşturulan sembolleri `#If` .. `Then` . ile kullanabilirsiniz. ...`#Else` kaynak dosyaları koşullu olarak derlemek için yönerge.</span><span class="sxs-lookup"><span data-stu-id="8e412-118">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="8e412-119">`-d` , öğesinin kısa biçimidir `-define` .</span><span class="sxs-lookup"><span data-stu-id="8e412-119">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="8e412-120">`-define`Sembol tanımlarını ayırmak için virgül kullanarak birden çok sembol tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e412-120">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="8e412-121">Visual Studio tümleşik geliştirme ortamında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8e412-121">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8e412-122">1. **Çözüm Gezgini** bir proje seçili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8e412-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8e412-123">**Proje** menüsünde **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e412-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8e412-124">2. **Derle** sekmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e412-124">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8e412-125">3. **Gelişmiş**'e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="8e412-125">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="8e412-126">4. **Özel sabitler** kutusundaki değeri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8e412-126">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e412-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e412-127">Example</span></span>  

 <span data-ttu-id="8e412-128">Aşağıdaki kod, iki koşullu derleyici sabiti tanımlar ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e412-128">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="8e412-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e412-129">See also</span></span>

- [<span data-ttu-id="8e412-130">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="8e412-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="8e412-131">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="8e412-131">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="8e412-132">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="8e412-132">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)
- [<span data-ttu-id="8e412-133">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="8e412-133">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
