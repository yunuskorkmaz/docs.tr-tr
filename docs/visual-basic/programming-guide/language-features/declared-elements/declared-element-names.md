---
title: Bildirilen Öğe Adları
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: cdba2b5f3e17fc6666ca653abd7f4bd7dfb31c4a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392928"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="07d4c-102">Bildirilen Öğe Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07d4c-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="07d4c-103">Her beyan edilen öğe *tanımlayıcı*olarak da bilinen ve kodun buna başvurmak için kullandığı bir ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="07d4c-104">Kurallar</span><span class="sxs-lookup"><span data-stu-id="07d4c-104">Rules</span></span>  
 <span data-ttu-id="07d4c-105">Visual Basic bir öğe adı aşağıdaki kuralları gözlemlemelidir:</span><span class="sxs-lookup"><span data-stu-id="07d4c-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="07d4c-106">Alfabetik bir karakter veya alt çizgi () ile başlamalıdır `_` .</span><span class="sxs-lookup"><span data-stu-id="07d4c-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="07d4c-107">Yalnızca alfabetik karakter, ondalık rakam ve alt çizgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="07d4c-108">Alt çizgiyle başlıyorsa, en az bir alfabetik karakter veya ondalık basamak içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="07d4c-109">En fazla 1023 karakter uzunluğunda olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="07d4c-110">1023 karakterlik uzunluk sınırı, tam nitelikli bir ada sahip tüm dize için de geçerlidir (örneğin,) `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement` .</span><span class="sxs-lookup"><span data-stu-id="07d4c-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="07d4c-111">Aşağıdaki örnekte bazı geçerli öğe adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="07d4c-112">Aşağıdaki örnekte bazı geçersiz öğe adları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="07d4c-113">Birincisi yalnızca bir alt çizgi içerir, ikincisi ondalık sayıyla başlar ve üçüncüsü geçersiz bir karakter ($) içerir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="07d4c-114">Alt çizgi () ile başlayan öğe adları, `_` [Dil bağımsızlığı ve dilden bağımsız bileşenlerin](../../../../standard/language-independence-and-language-independent-components.md) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod bu adı tanımlayan bir bileşeni kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="07d4c-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="07d4c-115">Ancak, bir öğe adında başka bir konumdaki alt çizgi CLS uyumludur.</span><span class="sxs-lookup"><span data-stu-id="07d4c-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="07d4c-116">Ad uzunluğu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="07d4c-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="07d4c-117">Pratik bir şekilde, sizin de öğenin doğasını açıkça tanımlarken adınızın olabildiğince kısa olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="07d4c-118">Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğunu ve kaynak dosya boyutunu azaltır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="07d4c-119">Öte yandan, adınız öğenin neyi temsil ettiğini ve kodunuzun onu nasıl kullandığını yeterince tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="07d4c-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="07d4c-120">Bu, kodunuzun okunabilirliğini açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-120">This is important for the readability of your code.</span></span> <span data-ttu-id="07d4c-121">Başka birisi bunu anlamayı denmişse veya siz onu yazdıktan sonra uzun bir süre arıyorsanız, uygun öğe adları önemli miktarda zaman kazandırabilir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="07d4c-122">Kaçan adlar</span><span class="sxs-lookup"><span data-stu-id="07d4c-122">Escaped Names</span></span>  
 <span data-ttu-id="07d4c-123">Genellikle, öğe adı, veya gibi Visual Basic tarafından ayrılmış bir anahtar kelimelerle eşleşmemelidir `Case` `Friend` .</span><span class="sxs-lookup"><span data-stu-id="07d4c-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="07d4c-124">Ancak, köşeli ayraç () içine alınmış bir *kaçan adı*tanımlayabilirsiniz `[ ]` .</span><span class="sxs-lookup"><span data-stu-id="07d4c-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="07d4c-125">Kaçış adı herhangi bir Visual Basic anahtar sözcüğüyle eşleşemez, köşeli ayraçlar herhangi bir belirsizliği ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="07d4c-126">Ayrıca, kodunuzun sonraki kısımlarında bulunan ada başvurduğunuzda de ayraçları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="07d4c-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="07d4c-127">Genel olarak, yalnızca şu durumlarda atlanan kaçış adlarını kullanmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="07d4c-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="07d4c-128">Kodunuz, bir ad olarak kullanılmakta olan anahtar sözcüğü ayırmayan Visual Basic önceki bir sürümünden geçirildi; veya</span><span class="sxs-lookup"><span data-stu-id="07d4c-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="07d4c-129">Verilen anahtar sözcüğünün ayrılmadığından, başka bir dilde yazılmış kodla çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="07d4c-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="07d4c-130">Aksi takdirde, adı bir anahtar sözcükle çakışırsa öğesini yeniden adlandırmayı düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="07d4c-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="07d4c-131">Tümleşik geliştirme ortamı (IDE) bunu yapmanın kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="07d4c-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="07d4c-132">Daha fazla bilgi için bkz. yeniden [düzenleme](/visualstudio/ide/refactoring-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="07d4c-132">For more information, see [Refactoring](/visualstudio/ide/refactoring-in-visual-studio).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="07d4c-133">Adlarda büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="07d4c-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="07d4c-134">Visual Basic öğe adları büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="07d4c-135">Bu, derleyici yalnızca alfabetik durumda farklılık gösteren iki adı karşılaştırırken, bunları aynı ad olarak yorumladığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="07d4c-136">Örneğin, `ABC` `abc` aynı tanımlanmış öğeye başvurmak için ve öğesini dikkate alır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="07d4c-137">Ancak, ortak dil çalışma zamanı (CLR) büyük/küçük harfe duyarlı bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="07d4c-138">Bu nedenle, bir derleme veya DLL oluşturduğunuzda ve diğer derlemeler için kullanılabilir hale getirmek istediğinizde, adlarınız artık büyük/küçük harf duyarsız değildir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="07d4c-139">Örneğin, adlı bir öğesi olan bir sınıfı tanımlarsanız `ABC` ve diğer derlemeler, ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanımını kullanıyorsa, öğesini olarak öğesine başvurmalıdır `ABC` .</span><span class="sxs-lookup"><span data-stu-id="07d4c-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="07d4c-140">Daha sonra sınıfınızı yeniden derlemenize ve öğenin adını olarak değiştirirseniz `abc` , sınıfınızı kullanan diğer derlemeler artık bu öğeye erişemez.</span><span class="sxs-lookup"><span data-stu-id="07d4c-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="07d4c-141">Bu nedenle, bir derlemenin güncelleştirilmiş bir sürümünü serbest bırakırsanız, tüm ortak öğelerin alfabetik durumunu değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="07d4c-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="07d4c-142">Adlar ve yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="07d4c-142">Names and Locales</span></span>  
 <span data-ttu-id="07d4c-143">Adların karşılaştırılması yerel ayardan bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="07d4c-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="07d4c-144">İki ad bir yerel ayarda eşleşiyorsa, bunların tüm yerel ayarlarda eşleşmesi garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="07d4c-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d4c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07d4c-145">See also</span></span>

- [<span data-ttu-id="07d4c-146">Bildirilmeyen öğeler</span><span class="sxs-lookup"><span data-stu-id="07d4c-146">Declared Elements</span></span>](index.md)
- [<span data-ttu-id="07d4c-147">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="07d4c-147">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="07d4c-148">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="07d4c-148">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="07d4c-149">Deyimler</span><span class="sxs-lookup"><span data-stu-id="07d4c-149">Statements</span></span>](../../../language-reference/statements/index.md)
