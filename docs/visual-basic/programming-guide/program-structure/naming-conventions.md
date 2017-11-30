---
title: "Visual Basic Adlandırma Kuralları"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a59139b57568810de80de764388eeffa5f8d7ac9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="19fa1-102">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="19fa1-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="19fa1-103">Visual Basic uygulamanızda öğenin adlandırdığınızda, bu adının ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19fa1-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="19fa1-104">Ancak, alt çizgi ile başlayan adları ile uyumlu olmadığını unutmayın [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="19fa1-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="19fa1-105">Adlandırma için aşağıdaki önerileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="19fa1-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="19fa1-106">Her ayrı bir sözcük bir büyük harf olan bir ad olarak başlamak `FindLastRecord` ve `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="19fa1-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="19fa1-107">Bir fiil işlevi ve yöntem adları olarak başlamak `InitNameArray` veya `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="19fa1-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="19fa1-108">Sınıfı, yapısı, modül ve özellik adlarıyla bir isim olarak başlamak `EmployeeName` veya `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="19fa1-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="19fa1-109">Arabirim adları önek ile başlayan "T", bir isim veya bir isim deyimi gibi izlemelidir `IComponent`, veya arabiriminin davranışı gibi açıklayan gelen ile `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="19fa1-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="19fa1-110">Alt çizgi kullanma ve kısaltmalar karışıklığa neden olabileceğinden kısaltmalar tutumlu, kullanın.</span><span class="sxs-lookup"><span data-stu-id="19fa1-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="19fa1-111">Olay işleyici adları ve ardından olay türünü tanımlayan bir isim başlayın "`EventHandler`", ın soneki"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="19fa1-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="19fa1-112">Olay bağımsız değişkeni sınıfların, adlarında "`EventArgs`" soneki.</span><span class="sxs-lookup"><span data-stu-id="19fa1-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="19fa1-113">Bir olay "önce" veya "sonra" kavramı, varsa, bir sonek yoksa veya geçmiş zamanın olarak kullanın "`ControlAdd`"veya"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="19fa1-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="19fa1-114">Uzun veya sık kullanılan terimler için ad uzunlukları makul, tutmak için örneğin, "HTML", "Köprü Metni Biçimlendirme Dili" yerine kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="19fa1-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="19fa1-115">Genel olarak, değişken adları 32 karakterden daha düşük bir çözüm ayarlamak monitörde okumak zordur.</span><span class="sxs-lookup"><span data-stu-id="19fa1-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="19fa1-116">Ayrıca, kısaltmalar tüm uygulama genelinde tutarlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="19fa1-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="19fa1-117">Rastgele bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında geçiş yapma karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="19fa1-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="19fa1-118">Bir dış kapsamdaki adları ile aynı olan bir iç kapsamda adlarında kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="19fa1-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="19fa1-119">Yanlış değişken erişiliyorsa hatalar neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="19fa1-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="19fa1-120">Anahtar sözcüğü aynı ada sahip bir değişken arasında bir çakışma meydana gelirse, uygun bir tür kitaplığı ile koyarak anahtar sözcüğü tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="19fa1-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="19fa1-121">Adlı bir değişken varsa, örneğin, `Date`, iç kullanabilirsiniz `Date` çağırarak yalnızca işlevi <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19fa1-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19fa1-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19fa1-122">See Also</span></span>  
 [<span data-ttu-id="19fa1-123">Kodda öğe adları olarak anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="19fa1-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="19fa1-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="19fa1-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="19fa1-125">Bildirilen öğe adları</span><span class="sxs-lookup"><span data-stu-id="19fa1-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="19fa1-126">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="19fa1-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="19fa1-127">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="19fa1-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
