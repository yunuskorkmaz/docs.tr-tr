---
title: Visual Basic Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: b686747b46529b53b0802a7deb38b5b4949f4d5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655367"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="45dce-102">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="45dce-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="45dce-103">Microsoft, örnekler ve bu konudaki yönergeleri izleyin belgeler geliştirir.</span><span class="sxs-lookup"><span data-stu-id="45dce-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="45dce-104">Aynı kodlama kurallarını izlerseniz, aşağıdaki faydaları elde:</span><span class="sxs-lookup"><span data-stu-id="45dce-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="45dce-105">Okuyucular değil düzeni içeriğe göre daha iyi odaklanabilmeniz için kodunuzu tutarlı bir görünüm sahip olur.</span><span class="sxs-lookup"><span data-stu-id="45dce-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="45dce-106">Önceki deneyimleri temel varsayımları yapabilirsiniz çünkü okuyucular kodunuzu daha hızlı bir şekilde anlayın.</span><span class="sxs-lookup"><span data-stu-id="45dce-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="45dce-107">Kopyalama, değiştirmek ve kodu daha kolay korumak.</span><span class="sxs-lookup"><span data-stu-id="45dce-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="45dce-108">Kodunuz için Visual Basic "en iyi yöntemleri" gösteren sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="45dce-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="45dce-109">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="45dce-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="45dce-110">Adlandırma kuralları hakkında daha fazla bilgi için bkz: [adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konu.</span><span class="sxs-lookup"><span data-stu-id="45dce-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="45dce-111">"Belgelerim" veya "benim" bir değişken adı bir parçası olarak kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="45dce-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="45dce-112">Bu yöntem security'deki oluşturur `My` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="45dce-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="45dce-113">Kodda bunları yönergelerine uygun hale getirmek için otomatik olarak oluşturulan nesnelerin adlarını değiştirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="45dce-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="45dce-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="45dce-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="45dce-115">Sekme alanları olarak ekleyin ve akıllı ile dört alanı girintileri girintileme kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="45dce-116">Kullanım **oldukça (, yeniden biçimlendirme) kod listesi** kodunuzu Kod düzenleyicisinde yeniden biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="45dce-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="45dce-117">Daha fazla bilgi için bkz: [seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="45dce-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="45dce-118">Satır başına yalnızca bir deyim kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-118">Use only one statement per line.</span></span> <span data-ttu-id="45dce-119">Visual Basic satır ayırıcı karakteri (:) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="45dce-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="45dce-120">Dil veren her yerde örtük satır devamlılığı lehinde açık satır devamlılığı karakteri "_" kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="45dce-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="45dce-121">Satır başına yalnızca bir bildirimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="45dce-122">Varsa **oldukça (, yeniden biçimlendirme) kod listesi** biçimi devamlılık satırları otomatik olarak, el ile devamlılık satırları bir sekme durağı girinti değil.</span><span class="sxs-lookup"><span data-stu-id="45dce-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="45dce-123">Bununla birlikte, her zaman sol listedeki öğeleri Hizala.</span><span class="sxs-lookup"><span data-stu-id="45dce-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="45dce-124">Yöntem ve özellik tanımları arasında en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="45dce-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="45dce-125">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="45dce-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="45dce-126">Yerine ayrı bir satırda kod satırının sonunda açıklamaları yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="45dce-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="45dce-127">Açıklama metni büyük harfe ile ve bir süre sonu yorum metni başlatın.</span><span class="sxs-lookup"><span data-stu-id="45dce-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="45dce-128">Açıklama sınırlayıcısı (') ve bir açıklama metni arasında bir boşluk ekler.</span><span class="sxs-lookup"><span data-stu-id="45dce-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   <span data-ttu-id="45dce-129">Yıldız işareti biçimlendirilmiş bloklarını yorumlarla çevreleyen değil.</span><span class="sxs-lookup"><span data-stu-id="45dce-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="45dce-130">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="45dce-130">Program Structure</span></span>  
  
-   <span data-ttu-id="45dce-131">Kullandığınızda `Main` yöntemi, varsayılan yapı için yeni konsol uygulamaları kullanıyorsanız ve `My` komut satırı bağımsız değişkenleri için.</span><span class="sxs-lookup"><span data-stu-id="45dce-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="45dce-132">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="45dce-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="45dce-133">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="45dce-133">String Data Type</span></span>  
  
-   <span data-ttu-id="45dce-134">Dizeyi birleştirmek için ve işareti kullanın (&).</span><span class="sxs-lookup"><span data-stu-id="45dce-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   <span data-ttu-id="45dce-135">Döngüler dizelerde eklemek için kullanın <xref:System.Text.StringBuilder> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="45dce-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="45dce-136">Gevşek temsilci olay işleyicileri</span><span class="sxs-lookup"><span data-stu-id="45dce-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="45dce-137">Açıkça bağımsız değişkenleri (nesne ve EventArgs) olay işleyicileri için uygun değil.</span><span class="sxs-lookup"><span data-stu-id="45dce-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="45dce-138">Bir olay (örneğin, gönderen e EventArgs olarak nesnesi olarak) için geçirilen olay bağımsız değişkenlerinin kullanmıyorsanız, gevşek temsilci kullanın ve olay bağımsız değişkenlerinin kodunuzda çıkışı bırakın:</span><span class="sxs-lookup"><span data-stu-id="45dce-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="45dce-139">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="45dce-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="45dce-140">Kullanım `Integer` gerekli olduğu dışında imzasız türler yerine.</span><span class="sxs-lookup"><span data-stu-id="45dce-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="45dce-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="45dce-141">Arrays</span></span>  
  
-   <span data-ttu-id="45dce-142">Diziler bildirimi satırındaki başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="45dce-143">Örneğin, aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     <span data-ttu-id="45dce-144">Aşağıdaki sözdizimini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="45dce-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   <span data-ttu-id="45dce-145">Dizi Belirleyicisi türünde, değişkeni üzerinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="45dce-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="45dce-146">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="45dce-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     <span data-ttu-id="45dce-147">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="45dce-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   <span data-ttu-id="45dce-148">Bildirme ve temel veri türlerinin dizileri başlatma {} sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="45dce-149">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="45dce-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     <span data-ttu-id="45dce-150">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="45dce-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="45dce-151">Kullanım anahtar sözcüğü ile</span><span class="sxs-lookup"><span data-stu-id="45dce-151">Use the With Keyword</span></span>  
 <span data-ttu-id="45dce-152">Bir dizi bir nesneye çağrısı yaptığınızda, kullanmayı `With` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="45dce-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="45dce-153">İçin try... Catch ve kullanarak özel durum işleme kullandığınızda deyimleri</span><span class="sxs-lookup"><span data-stu-id="45dce-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="45dce-154">Kullanmayın `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="45dce-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="45dce-155">IsNot anahtar sözcüğünü kullanın</span><span class="sxs-lookup"><span data-stu-id="45dce-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="45dce-156">Kullanım `IsNot` anahtar sözcüğü yerine `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="45dce-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="45dce-157">New anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="45dce-157">New Keyword</span></span>  
  
-   <span data-ttu-id="45dce-158">Kısa örneklemesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-158">Use short instantiation.</span></span> <span data-ttu-id="45dce-159">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="45dce-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     <span data-ttu-id="45dce-160">Önceki satır için eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="45dce-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   <span data-ttu-id="45dce-161">Nesne başlatıcıları parametresiz bir kurucusu yerine yeni nesneler için kullanın:</span><span class="sxs-lookup"><span data-stu-id="45dce-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a><span data-ttu-id="45dce-162">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="45dce-162">Event Handling</span></span>  
  
-   <span data-ttu-id="45dce-163">Kullanım `Handles` yerine `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="45dce-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   <span data-ttu-id="45dce-164">Kullanım `AddressOf`ve temsilci açıkça örneği değil:</span><span class="sxs-lookup"><span data-stu-id="45dce-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   <span data-ttu-id="45dce-165">Bir olay tanımladığınızda, kısa söz dizimini kullanın ve temsilci tanımlamak derleyici sağlar:</span><span class="sxs-lookup"><span data-stu-id="45dce-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   <span data-ttu-id="45dce-166">Bir olay olup olmadığını doğrulamaz `Nothing` (çağırmadan önce null) `RaiseEvent` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="45dce-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="45dce-167">`RaiseEvent` denetler `Nothing` olayı oluşturmadan önce.</span><span class="sxs-lookup"><span data-stu-id="45dce-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="45dce-168">Paylaşılan üyeler kullanma</span><span class="sxs-lookup"><span data-stu-id="45dce-168">Using Shared Members</span></span>  
 <span data-ttu-id="45dce-169">Çağrı `Shared` bir örnek değişkeni değil, sınıf adı kullanarak üyeleri.</span><span class="sxs-lookup"><span data-stu-id="45dce-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="45dce-170">XML değişmez değerleri</span><span class="sxs-lookup"><span data-stu-id="45dce-170">Use XML Literals</span></span>  
 <span data-ttu-id="45dce-171">XML değişmez değerleri (örneğin, yükleme, sorgu ve dönüştürme) XML ile çalışırken karşılaştığınız en yaygın görevleri basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="45dce-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="45dce-172">XML ile geliştirirken, aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="45dce-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="45dce-173">XML değişmez değerleri XML belgelerini ve XML API'lerini doğrudan çağırmak yerine parçalarını oluşturmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="45dce-174">XML değişmez değerleri için performans iyileştirmelerinden yararlanmasını için dosya veya proje düzeyinde XML ad alanlarını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="45dce-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="45dce-175">XML eksen özellikleri öğeleri ve özniteliklerinin bir XML belgesi erişmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="45dce-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="45dce-176">Katıştırılmış ifadeler değerleri dahil etmek ve XML API çağrıları gibi kullanmak yerine var olan değerleri oluşturmak için kullanın `Add` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="45dce-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a><span data-ttu-id="45dce-177">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="45dce-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="45dce-178">Sorgu değişkenleri için anlamlı adlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="45dce-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   <span data-ttu-id="45dce-179">Pascal kullanarak anonim türdeki özellik adlarının doğru olduğundan emin olmak için bir sorgu öğe adı sağlayan büyük/küçük harf:</span><span class="sxs-lookup"><span data-stu-id="45dce-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   <span data-ttu-id="45dce-180">Özellik adlarının sonuç belirsiz kullanırken özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="45dce-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="45dce-181">Sorgunuzu adı ve bir sipariş kimliği müşteri döndürürse, örneğin, bunları olarak bırakarak yerine adlandırabilir `Name` ve `ID` sonuç:</span><span class="sxs-lookup"><span data-stu-id="45dce-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   <span data-ttu-id="45dce-182">Tür çıkarımı sorgu değişkenleri ve aralık değişkeni bildiriminde kullanın:</span><span class="sxs-lookup"><span data-stu-id="45dce-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   <span data-ttu-id="45dce-183">Sorgu yan tümceleri altında Hizala `From` deyimi:</span><span class="sxs-lookup"><span data-stu-id="45dce-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   <span data-ttu-id="45dce-184">Kullanım `Where` yan tümceleri diğer önce sorgu yan tümceleri böylece sonraki sorgu yan tümceleri filtrelenmiş veri kümesi üzerinde çalışır:</span><span class="sxs-lookup"><span data-stu-id="45dce-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   <span data-ttu-id="45dce-185">Kullanım `Join` açıkça kullanmak yerine bir birleştirme işlemi tanımlamak için yan tümcesi `Where` örtük olarak bir birleştirme işlemi tanımlamak için yan tümcesi:</span><span class="sxs-lookup"><span data-stu-id="45dce-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45dce-186">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45dce-186">See Also</span></span>  
 [<span data-ttu-id="45dce-187">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="45dce-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
