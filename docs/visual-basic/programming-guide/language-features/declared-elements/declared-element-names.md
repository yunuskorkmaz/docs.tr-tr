---
title: Bildirilen Öğe Adları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad883dd8e1de419c74b5bcdb8762994e762b4cf7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="abc4d-102">Bildirilen Öğe Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abc4d-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="abc4d-103">Bildirilen her öğe olarak da adlandırılan bir ada sahip bir *tanımlayıcısı*, olduğu kod başvurduğu için kullanır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="abc4d-104">Kurallar</span><span class="sxs-lookup"><span data-stu-id="abc4d-104">Rules</span></span>  
 <span data-ttu-id="abc4d-105">Visual Basic'te bir öğe adı aşağıdaki kurallara uymanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="abc4d-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="abc4d-106">Alfabetik bir karakter veya alt çizgi ile başlaması gerekir (`_`).</span><span class="sxs-lookup"><span data-stu-id="abc4d-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="abc4d-107">Yalnızca alfasayısal karakterler, ondalık sayılar ve alt çizgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="abc4d-108">Bir alt çizgiyle başlıyorsa, en az bir alfasayısal karakter veya ondalık sayı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="abc4d-109">Birden fazla 1023 karakterden uzun olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="abc4d-110">1023 karakter uzunluğunu de bir tam ad tüm dizeye gibi geçerlidir `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="abc4d-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="abc4d-111">Aşağıdaki örnek, bazı geçerli öğe adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="abc4d-112">Aşağıdaki örnek, bazı geçersiz öğe adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="abc4d-113">İlk yalnızca bir alt çizgi, ikinci bir ondalık sayı ile başlar, ve üçüncü geçersiz bir karakter ($) içerir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="abc4d-114">Öğe adları alt çizgi ile başlayan (`_`) parçası olan [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod tür adları tanımlayan bir bileşen kullanamazlar.</span><span class="sxs-lookup"><span data-stu-id="abc4d-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="abc4d-115">Ancak, alt çizgi herhangi bir öğe adı konumunda CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="abc4d-116">Ad uzunluğu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="abc4d-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="abc4d-117">Pratik geçtiğinden bağımsız adınızı hala açık bir şekilde öğe yapısını tanımlanırken olabildiğinde kısa olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="abc4d-118">Bu, kodunuzun okunabilirliğini artırır ve satır uzunluğu ve kaynak dosya boyutu azaltır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="abc4d-119">Diğer taraftan, adınızı, yeterli ne öğeyi temsil eder ve nasıl kodunuzu kullanır tanımlamaz, bu nedenle kısa olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="abc4d-120">Bu, kodunuzu okunabilirlik için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-120">This is important for the readability of your code.</span></span> <span data-ttu-id="abc4d-121">Başkası anladığınızı çalışıyor ya da sizin, uzun süre yazdığınız sonra arıyorsanız, uygun öğe adları önemli miktarda zaman kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abc4d-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="abc4d-122">Kaçış adları</span><span class="sxs-lookup"><span data-stu-id="abc4d-122">Escaped Names</span></span>  
 <span data-ttu-id="abc4d-123">Genellikle, bir öğe adı herhangi bir Visual Basic tarafından gibi ayrılmış anahtar sözcükler eşleşmemelidir `Case` veya `Friend`.</span><span class="sxs-lookup"><span data-stu-id="abc4d-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="abc4d-124">Ancak, tanımlayabilirsiniz bir *adı kaçışlı*, köşeli parantez içine (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="abc4d-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="abc4d-125">Köşeli ayraçlar herhangi belirsizliğini kaldırmak bu yana bir kaçış karakterli adı tüm Visual Basic anahtar sözcüğü eşleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abc4d-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="abc4d-126">Daha sonra kodunuzda adına başvurduğunuzda köşeli ayraçlar de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abc4d-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="abc4d-127">Kaçış adları kullanması gereken genel olarak, yalnızca:</span><span class="sxs-lookup"><span data-stu-id="abc4d-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="abc4d-128">Kodunuzu ad olarak kullanılan anahtar sözcüğü yedek değil Visual Basic önceki bir sürümünden geçiş yaptı; veya</span><span class="sxs-lookup"><span data-stu-id="abc4d-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="abc4d-129">Belirtilen anahtar sözcüğü olmayan ayrılmış başka bir dilde yazılan kod ile çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="abc4d-130">Aksi takdirde, adı olan bir anahtar sözcük çakışırsa öğesini yeniden adlandırma göz önünde bulundurmalısınız.</span><span class="sxs-lookup"><span data-stu-id="abc4d-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="abc4d-131">Tümleşik geliştirme ortamı (IDE), bunu yapmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc4d-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="abc4d-132">Daha fazla bilgi için bkz: [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="abc4d-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="abc4d-133">Adları büyük/küçük harfe duyarlılık</span><span class="sxs-lookup"><span data-stu-id="abc4d-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="abc4d-134">Visual Basic'te öğe adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="abc4d-135">Bu, yalnızca alfabetik durumlarda farklı iki ad derleyici karşılaştırır, bunları aynı adı taşıyan yorumlar olduğunu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="abc4d-136">Örneğin, göz önünde bulundurur `ABC` ve `abc` aynı bildirilen öğe başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="abc4d-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="abc4d-137">Ancak, ortak dil çalışma zamanı (CLR) büyük küçük harfe duyarlı bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="abc4d-138">Bir derlemeyi ya da bir DLL oluşturabilir ve diğer derlemeler için kullanılabilir hale getirmek, bu nedenle, adlarınızı artık büyük küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="abc4d-139">Örneğin, bir sınıf olarak adlandırılan bir öğesiyle tanımlarsanız `ABC`, ve diğer derlemelerden ortak dil çalışma zamanı sınıfınızın kullanın, öğesine başvurmalıdır `ABC`.</span><span class="sxs-lookup"><span data-stu-id="abc4d-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="abc4d-140">Daha sonra sınıfınız derlenir ve öğenin adını değiştirmek, `abc`, sınıfınız kullanarak diğer derlemeler artık o öğeye erişebilir.</span><span class="sxs-lookup"><span data-stu-id="abc4d-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="abc4d-141">Bu nedenle, bir derlemeyi güncelleştirilmiş bir sürümünü serbest bıraktığınızda, herhangi bir genel öğesi alfabetik durumunda değiştirmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="abc4d-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="abc4d-142">Adları ve yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="abc4d-142">Names and Locales</span></span>  
 <span data-ttu-id="abc4d-143">Yerel ayarı karşılaştırma adlarının bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="abc4d-144">İki adı bir yerel ayarda eşleşirse, bunlar tüm yerel eşleşen sağlanır.</span><span class="sxs-lookup"><span data-stu-id="abc4d-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc4d-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="abc4d-145">See Also</span></span>  
 [<span data-ttu-id="abc4d-146">Bildirilen Öğeler</span><span class="sxs-lookup"><span data-stu-id="abc4d-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [<span data-ttu-id="abc4d-147">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="abc4d-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="abc4d-148">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="abc4d-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="abc4d-149">Deyimler</span><span class="sxs-lookup"><span data-stu-id="abc4d-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
