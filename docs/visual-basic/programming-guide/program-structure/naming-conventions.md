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
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050382"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="e4ef0-102">Visual Basic Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="e4ef0-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="e4ef0-103">Visual Basic uygulamanızda bir öğe adı, adının ilk karakteri alfabetik bir karakter veya alt çizgi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="e4ef0-104">Ancak, alt çizgi ile başlayan adları ile uyumlu olmayan unutmayın [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="e4ef0-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="e4ef0-105">Aşağıdaki öneriler, adlandırma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="e4ef0-106">Her ayrı bir sözcüğün bir ada sahip bir büyük harf olarak başlayan `FindLastRecord` ve `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="e4ef0-107">Bir fiil, işlevi ve yöntem adları olarak başlayan `InitNameArray` veya `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="e4ef0-108">Sınıfı, yapı, modül ve özellik adlarını içeren bir isim olarak başlayan `EmployeeName` veya `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="e4ef0-109">Arabirimi adları önek ile başlayan "I", ardından bir isim veya bir isim tümceciği gibi `IComponent`, veya arabiriminin davranışı gibi açıklayan bir sıfat `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="e4ef0-110">Değil çizgi kullanın ve kısaltmalar kullanıcılarda kafa karışıklığına neden olabileceği için kısaltmalar gerektiğinde, kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="e4ef0-111">Olay işleyici adlarının ardından olayın türünü tanımlayan bir isim başlayın "`EventHandler`", olarak soneki"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="e4ef0-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="e4ef0-112">Olay bağımsız değişkeni sınıflarının adları dahil "`EventArgs`" soneki.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="e4ef0-113">Bir olayı "önce" veya "sonra" kavramı, varsa, bir son eki var veya geçmiş şimdiki olarak kullanın "`ControlAdd`"veya"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="e4ef0-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="e4ef0-114">Uzun veya sık kullanılan terimler için ad uzunlukları makul, tutmak için örneğin, "HTML", "Köprü Metni İşaretleme Dili" yerine kısaltmalar kullanın.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="e4ef0-115">Genel olarak, 32 karakterden değişken adları ayarlamak için düşük çözünürlüklü bir monitörde okunması zordur.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="e4ef0-116">Ayrıca, tüm uygulamanın tamamında tutarlı bir kısaltmalar emin olun.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="e4ef0-117">Rastgele bir projede "HTML" ve "Köprü Metni İşaretleme Dili" arasında geçiş yapma karışıklığa neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="e4ef0-118">Bir iç kapsamındaki bir dış kapsamdaki adları aynı adları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="e4ef0-119">Yanlış değişken erişildiği durumda hatalar oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="e4ef0-120">Bir değişken ile aynı ada sahip bir anahtar sözcüğü arasında bir çakışma ortaya çıkarsa, uygun bir tür kitaplığı ile koyarak anahtar sözcüğü belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="e4ef0-121">Örneğin, adında bir değişkene varsa `Date`, iç kullanabilirsiniz `Date` işlevini çağırarak yalnızca <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ef0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4ef0-122">See also</span></span>

- [<span data-ttu-id="e4ef0-123">Code’da Öğe Adları Olarak Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e4ef0-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="e4ef0-124">Me, My, MyBase ve MyClass</span><span class="sxs-lookup"><span data-stu-id="e4ef0-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="e4ef0-125">Bildirilen Öğe Adları</span><span class="sxs-lookup"><span data-stu-id="e4ef0-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="e4ef0-126">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="e4ef0-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="e4ef0-127">Visual Basic Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e4ef0-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
