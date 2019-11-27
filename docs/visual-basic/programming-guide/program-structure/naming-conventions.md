---
title: Adlandırma Kuralları
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
ms.openlocfilehash: 98fdda2934c9df1b33f41b6e0442a39246efe168
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347319"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="2ab79-102">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="2ab79-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="2ab79-103">Visual Basic uygulamanızda bir öğe belirlediğinizde, bu adın ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ab79-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="2ab79-104">Ancak, bir alt çizgiyle başlayan adların, [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="2ab79-105">Aşağıdaki öneriler adlandırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2ab79-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="2ab79-106">`FindLastRecord` ve `RedrawMyForm`gibi büyük harfle her bir ada sahip her bir sözcüğe başlayın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="2ab79-107">İşlev ve yöntem adlarını `InitNameArray` veya `CloseDialog`gibi bir fiil ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="2ab79-108">`EmployeeName` veya `CarAccessory`içinde olduğu gibi, sınıf, yapı, modül ve özellik adlarını bir ada sahip olarak başlatın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="2ab79-109">Arabirim adlarını "I" önekiyle, ardından `IComponent`gibi bir ad veya bir ad ifadesi ve `IPersistable`gibi arabirimin davranışını açıklayan bir sıfat ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="2ab79-110">Alt çizgi kullanmayın ve kısaltmaların düzgün şekilde kullanılmasını sağlayabilirsiniz çünkü kısaltmalar karışıklıklara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab79-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="2ab79-111">Olay işleyicisi adlarını, "`MouseEventHandler`" içinde olduğu gibi "`EventHandler`" son eki tarafından izlenen olay türünü açıklayan bir ad ile başlatın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="2ab79-112">Olay bağımsız değişkeni sınıflarının adlarında, "`EventArgs`" sonekini içerir.</span><span class="sxs-lookup"><span data-stu-id="2ab79-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="2ab79-113">Bir olayda "önce" veya "After" kavramı varsa, "`ControlAdd`" veya "`ControlAdded`" içinde olduğu gibi, mevcut veya geçmiş zaman hali için bir sonek kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="2ab79-114">Uzun veya sık kullanılan şartlar için, "Köprü Metni Biçimlendirme Dili" yerine "HTML" gibi ad uzunluklarının mantıklı tutulması için kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ab79-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="2ab79-115">Genel olarak, 32 karakterden büyük değişken adları, düşük çözünürlüğe sahip bir izleyici kümesini okumak zordur.</span><span class="sxs-lookup"><span data-stu-id="2ab79-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="2ab79-116">Ayrıca, kısaltmalarınızın tüm uygulama genelinde tutarlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2ab79-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="2ab79-117">Bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında rastgele geçiş, karışıklıklara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab79-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="2ab79-118">Bir dış kapsamdaki adlarla aynı olan bir iç kapsamdaki adları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="2ab79-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="2ab79-119">Yanlış değişkene erişildiğinde hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="2ab79-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="2ab79-120">Bir değişken ve aynı ada sahip anahtar sözcük arasında bir çakışma oluşursa, anahtar sözcüğünü uygun tür kitaplığı ile önce tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2ab79-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="2ab79-121">Örneğin, `Date`adlı bir değişkeniniz varsa, iç `Date` işlevini yalnızca <xref:System.DateTime.Date%2A?displayProperty=nameWithType>çağırarak kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ab79-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ab79-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ab79-122">See also</span></span>

- [<span data-ttu-id="2ab79-123">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2ab79-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="2ab79-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="2ab79-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="2ab79-125">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="2ab79-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="2ab79-126">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="2ab79-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="2ab79-127">Visual Basic Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2ab79-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
