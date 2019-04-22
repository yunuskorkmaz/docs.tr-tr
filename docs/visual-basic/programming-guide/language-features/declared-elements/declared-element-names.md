---
title: Bildirilen Öğe Adları (Visual Basic)
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
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814074"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="05530-102">Bildirilen Öğe Adları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05530-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="05530-103">Bildirilen her öğe olarak da bilinen bir ada sahip bir *tanımlayıcı*, olan kod başvurduğu için kullanır.</span><span class="sxs-lookup"><span data-stu-id="05530-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="05530-104">Kurallar</span><span class="sxs-lookup"><span data-stu-id="05530-104">Rules</span></span>  
 <span data-ttu-id="05530-105">Visual Basic'te bir öğe adı, aşağıdaki kurallara uymanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="05530-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="05530-106">Alfabetik bir karakter veya alt çizgi ile başlamalıdır (`_`).</span><span class="sxs-lookup"><span data-stu-id="05530-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="05530-107">Yalnızca alfabetik karakterler, ondalık sayılar ve alt çizgi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="05530-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="05530-108">Bir alt çizgiyle başlıyorsa en az bir alfasayısal karakter veya ondalık sayı içermelidir.</span><span class="sxs-lookup"><span data-stu-id="05530-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="05530-109">Daha fazla 1023 karakterden uzun olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="05530-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="05530-110">Uzunluk sınırını 1023 karakteri de tam adı, tüm dize gibi geçerlidir `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="05530-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="05530-111">Aşağıdaki örnek, bazı geçerli öğe adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="05530-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="05530-112">Aşağıdaki örnek, bazı geçersiz öğe adları gösterir.</span><span class="sxs-lookup"><span data-stu-id="05530-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="05530-113">İlk yalnızca bir alt çizgi içeren ikinci bir ondalık basamak ile başlar ve üçüncü geçersiz karakter ($) içeriyor.</span><span class="sxs-lookup"><span data-stu-id="05530-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="05530-114">Bir alt çizgiyle başlayan öğe adları (`_`) parçası değildir [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod tür adları tanımlayan bir bileşen kullanamazlar.</span><span class="sxs-lookup"><span data-stu-id="05530-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="05530-115">Ancak, diğer konumunda bir öğe adı alt çizgi, CLS uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="05530-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="05530-116">Ad uzunluğu yönergeleri</span><span class="sxs-lookup"><span data-stu-id="05530-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="05530-117">Pratik olursa olsun adınızı öğe yapısını açıkça hala tanımlanırken olabildiğince kısa olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05530-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="05530-118">Bu, kodunuzun okunabilirliği geliştirir ve satır uzunluğu ve kaynak dosya boyutunu azaltır.</span><span class="sxs-lookup"><span data-stu-id="05530-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="05530-119">Öte yandan, adınız, yeterince ne öğesi temsil eder ve nasıl kodunuzun kullandığı tanımlamaz, bu nedenle kısa olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="05530-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="05530-120">Bu, kodunuzun okunabilirliği için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="05530-120">This is important for the readability of your code.</span></span> <span data-ttu-id="05530-121">Başka birisi tarafından anlayabilmek çalışıyor ya da sizin, uzun bir süre sonra yazdığınız kullanmak istiyorsanız, uygun öğe adları önemli miktarda zaman kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05530-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="05530-122">Kaçış adları</span><span class="sxs-lookup"><span data-stu-id="05530-122">Escaped Names</span></span>  
 <span data-ttu-id="05530-123">Genellikle, bir öğe adı herhangi bir Visual Basic, gibi ayrılmış anahtar sözcükler eşleşmemelidir `Case` veya `Friend`.</span><span class="sxs-lookup"><span data-stu-id="05530-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="05530-124">Ancak, tanımlayabileceğiniz bir *adı kaçış*, köşeli parantez içine (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="05530-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="05530-125">Belirsizlik köşeli ayraçları Kaldır beri kaçan bir adı bir Visual Basic anahtar sözcüğü eşleşebilir.</span><span class="sxs-lookup"><span data-stu-id="05530-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="05530-126">Daha sonra kodunuzda adına başvurduğunuzda parantez de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05530-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="05530-127">Genel olarak, kaçış adları kullanmanız gereken yalnızca:</span><span class="sxs-lookup"><span data-stu-id="05530-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="05530-128">Kodunuzu anahtar sözcüğü bir ad kullanılan yedek değil Visual Basic'in önceki bir sürümden geçiş yaptı; veya</span><span class="sxs-lookup"><span data-stu-id="05530-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="05530-129">Belirli bir anahtar değil ayrılmış başka bir dilde yazılmış kodu ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="05530-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="05530-130">Aksi takdirde, adını, anahtar sözcüğü ile çakışırsa, öğeyi yeniden adlandırmadan düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="05530-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="05530-131">Tümleşik geliştirme ortamı (IDE), bunu yapmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="05530-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="05530-132">Daha fazla bilgi için [yeniden düzenleme](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="05530-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="05530-133">Adları büyük/küçük harf duyarlılığı</span><span class="sxs-lookup"><span data-stu-id="05530-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="05530-134">Visual Basic'te öğe adları büyük/küçük harfe duyarsızdır.</span><span class="sxs-lookup"><span data-stu-id="05530-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="05530-135">Bu, derleyici alfabetik yalnızca farklı iki ad karşılaştırır, bunların aynı ada yorumlar, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="05530-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="05530-136">Örneğin, göz önünde bulundurur `ABC` ve `abc` aynı bildirilen öğeye başvurmak üzere.</span><span class="sxs-lookup"><span data-stu-id="05530-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="05530-137">Ancak, ortak dil çalışma zamanı (CLR) büyük/küçük harfe bağlama kullanır.</span><span class="sxs-lookup"><span data-stu-id="05530-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="05530-138">Bir derleme veya bir DLL üretmek ve diğer derlemeleri kullandırmak, bu nedenle, adları artık büyük küçük harf duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="05530-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="05530-139">Örneğin, adında bir öğe ile bir sınıf tanımlama `ABC`, ve diğer derlemeler ortak dil çalışma zamanı aracılığıyla sınıfınızın kullanın, öğesine başvurmalıdır `ABC`.</span><span class="sxs-lookup"><span data-stu-id="05530-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="05530-140">Daha sonra sınıfı yeniden derleyin ve öğenin adını değiştirmek `abc`, sınıfınıza kullanarak diğer derlemeleri artık bu öğeye erişebilir.</span><span class="sxs-lookup"><span data-stu-id="05530-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="05530-141">Bu nedenle, bir derleme güncelleştirilmiş bir sürümünü serbest bıraktığınızda, ortak öğeleri alfabetik durumunu değiştirmemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="05530-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="05530-142">Adları ve yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="05530-142">Names and Locales</span></span>  
 <span data-ttu-id="05530-143">Yerel ayarı karşılaştırma adlarının bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="05530-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="05530-144">Bir yerel ayarda iki adlarıyla, tüm yerel ayarlarda eşleşecek şekilde garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="05530-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05530-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05530-145">See also</span></span>

- [<span data-ttu-id="05530-146">Bildirilen Öğeler</span><span class="sxs-lookup"><span data-stu-id="05530-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="05530-147">Bildirilen Öğe Özellikleri</span><span class="sxs-lookup"><span data-stu-id="05530-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="05530-148">Bildirilmiş Öğelere Başvurular</span><span class="sxs-lookup"><span data-stu-id="05530-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="05530-149">Deyimler</span><span class="sxs-lookup"><span data-stu-id="05530-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
