---
title: Visual Basic Adlandırma Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: cb7e9f2a577e95e09fde885df1a78aea4e7fa466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651924"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="13818-102">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="13818-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="13818-103">Visual Basic uygulamanızda öğenin adlandırdığınızda, bu adının ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13818-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="13818-104">Ancak, alt çizgi ile başlayan adları ile uyumlu olmadığını unutmayın [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="13818-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="13818-105">Adlandırma için aşağıdaki önerileri uygulayın.</span><span class="sxs-lookup"><span data-stu-id="13818-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="13818-106">Her ayrı bir sözcük bir büyük harf olan bir ad olarak başlamak `FindLastRecord` ve `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="13818-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="13818-107">Bir fiil işlevi ve yöntem adları olarak başlamak `InitNameArray` veya `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="13818-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="13818-108">Sınıfı, yapısı, modül ve özellik adlarıyla bir isim olarak başlamak `EmployeeName` veya `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="13818-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="13818-109">Arabirim adları önek ile başlayan "T", bir isim veya bir isim deyimi gibi izlemelidir `IComponent`, veya arabiriminin davranışı gibi açıklayan gelen ile `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="13818-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="13818-110">Alt çizgi kullanma ve kısaltmalar karışıklığa neden olabileceğinden kısaltmalar tutumlu, kullanın.</span><span class="sxs-lookup"><span data-stu-id="13818-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="13818-111">Olay işleyici adları ve ardından olay türünü tanımlayan bir isim başlayın "`EventHandler`", ın soneki"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="13818-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="13818-112">Olay bağımsız değişkeni sınıfların, adlarında "`EventArgs`" soneki.</span><span class="sxs-lookup"><span data-stu-id="13818-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="13818-113">Bir olay "önce" veya "sonra" kavramı, varsa, bir sonek yoksa veya geçmiş zamanın olarak kullanın "`ControlAdd`"veya"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="13818-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="13818-114">Uzun veya sık kullanılan terimler için ad uzunlukları makul, tutmak için örneğin, "HTML", "Köprü Metni Biçimlendirme Dili" yerine kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="13818-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="13818-115">Genel olarak, değişken adları 32 karakterden daha düşük bir çözüm ayarlamak monitörde okumak zordur.</span><span class="sxs-lookup"><span data-stu-id="13818-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="13818-116">Ayrıca, kısaltmalar tüm uygulama genelinde tutarlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="13818-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="13818-117">Rastgele bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında geçiş yapma karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="13818-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="13818-118">Bir dış kapsamdaki adları ile aynı olan bir iç kapsamda adlarında kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="13818-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="13818-119">Yanlış değişken erişiliyorsa hatalar neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="13818-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="13818-120">Anahtar sözcüğü aynı ada sahip bir değişken arasında bir çakışma meydana gelirse, uygun bir tür kitaplığı ile koyarak anahtar sözcüğü tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="13818-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="13818-121">Adlı bir değişken varsa, örneğin, `Date`, iç kullanabilirsiniz `Date` çağırarak yalnızca işlevi <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13818-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13818-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13818-122">See Also</span></span>  
 [<span data-ttu-id="13818-123">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="13818-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="13818-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="13818-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="13818-125">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="13818-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="13818-126">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="13818-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="13818-127">Visual Basic Dil Başvurusu</span><span class="sxs-lookup"><span data-stu-id="13818-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
