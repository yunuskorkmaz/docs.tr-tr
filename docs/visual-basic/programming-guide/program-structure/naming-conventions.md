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
ms.openlocfilehash: 20531e379ddf9b93a278795e9b3c0eb91b47e077
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398350"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="aed7c-102">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="aed7c-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="aed7c-103">Visual Basic uygulamanızda bir öğe belirlediğinizde, bu adın ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aed7c-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="aed7c-104">Ancak, bir alt çizgiyle başlayan adların, [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmadığına unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aed7c-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="aed7c-105">Aşağıdaki öneriler adlandırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="aed7c-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="aed7c-106">Bir ad içindeki her bir sözcüğü, ve ' de olduğu gibi büyük harfle `FindLastRecord` başlatın `RedrawMyForm` .</span><span class="sxs-lookup"><span data-stu-id="aed7c-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="aed7c-107">Veya gibi bir fiil ile işlev ve yöntem adlarını başlatın `InitNameArray` `CloseDialog` .</span><span class="sxs-lookup"><span data-stu-id="aed7c-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="aed7c-108">Ya da ' de olduğu gibi, sınıf, yapı, modül ve özellik adlarını bir ad ile başlatın `EmployeeName` `CarAccessory` .</span><span class="sxs-lookup"><span data-stu-id="aed7c-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="aed7c-109">Arabirim adlarını "I" önekiyle, ardından bir ad veya bir ad ifadesi ile, örneğin gibi `IComponent` arabirimin davranışını açıklayan bir sıfat ile başlatın `IPersistable` .</span><span class="sxs-lookup"><span data-stu-id="aed7c-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="aed7c-110">Alt çizgi kullanmayın ve kısaltmaların düzgün şekilde kullanılmasını sağlayabilirsiniz çünkü kısaltmalar karışıklıklara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="aed7c-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="aed7c-111">Olay işleyicisi adlarını olay türünü açıklayan bir ad ile başlatın ve "" `EventHandler` içinde olduğu gibi "" son eki tarafından gelir `MouseEventHandler` .</span><span class="sxs-lookup"><span data-stu-id="aed7c-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="aed7c-112">Olay bağımsız değişkeni sınıflarının adlarında " `EventArgs` " sonekini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aed7c-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="aed7c-113">Bir olayda "önce" veya "After" kavramı varsa, " `ControlAdd` " veya "" içinde olduğu gibi, mevcut veya geçmiş zaman hali için bir sonek kullanın `ControlAdded` .</span><span class="sxs-lookup"><span data-stu-id="aed7c-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="aed7c-114">Uzun veya sık kullanılan şartlar için, "Köprü Metni Biçimlendirme Dili" yerine "HTML" gibi ad uzunluklarının mantıklı tutulması için kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="aed7c-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="aed7c-115">Genel olarak, 32 karakterden büyük değişken adları, düşük çözünürlüğe sahip bir izleyici kümesini okumak zordur.</span><span class="sxs-lookup"><span data-stu-id="aed7c-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="aed7c-116">Ayrıca, kısaltmalarınızın tüm uygulama genelinde tutarlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="aed7c-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="aed7c-117">Bir projede "HTML" ve "Köprü Metni Biçimlendirme Dili" arasında rastgele geçiş, karışıklıklara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="aed7c-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="aed7c-118">Bir dış kapsamdaki adlarla aynı olan bir iç kapsamdaki adları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="aed7c-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="aed7c-119">Yanlış değişkene erişildiğinde hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="aed7c-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="aed7c-120">Bir değişken ve aynı ada sahip anahtar sözcük arasında bir çakışma oluşursa, anahtar sözcüğünü uygun tür kitaplığı ile önce tanımlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="aed7c-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="aed7c-121">Örneğin, adlı bir değişkene sahipseniz `Date` , `Date` yalnızca çağırarak iç işlevi kullanabilirsiniz <xref:System.DateTime.Date%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aed7c-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aed7c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aed7c-122">See also</span></span>

- [<span data-ttu-id="aed7c-123">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="aed7c-123">Keywords as Element Names in Code</span></span>](keywords-as-element-names-in-code.md)
- [<span data-ttu-id="aed7c-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="aed7c-124">Me, My, MyBase, and MyClass</span></span>](me-my-mybase-and-myclass.md)
- [<span data-ttu-id="aed7c-125">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="aed7c-125">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="aed7c-126">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="aed7c-126">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="aed7c-127">Visual Basic dil başvurusu</span><span class="sxs-lookup"><span data-stu-id="aed7c-127">Visual Basic Language Reference</span></span>](../../language-reference/index.md)
