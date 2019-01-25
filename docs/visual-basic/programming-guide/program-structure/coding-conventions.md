---
title: Visual Basic Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: f2b1676ae959c5426af3021bbd340980115c5da6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724888"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="7c999-102">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="7c999-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="7c999-103">Microsoft, örnekler ve bu konudaki yönergeleri izleyen belgeler geliştirir.</span><span class="sxs-lookup"><span data-stu-id="7c999-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="7c999-104">Aynı kodlama kurallarını takip ederseniz, aşağıdaki faydaları elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7c999-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
-   <span data-ttu-id="7c999-105">Okuyucular düzene değil içeriğe göre daha iyi odaklanabilmeniz için kodunuzu tutarlı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7c999-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="7c999-106">Bunlar önceki deneyime dayanan varsayımlar yapabilecekleri için Okuyucular kodunuzu daha hızlı bir şekilde anlayın.</span><span class="sxs-lookup"><span data-stu-id="7c999-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="7c999-107">Kopyalama, değiştirme ve kodu daha kolay korumak.</span><span class="sxs-lookup"><span data-stu-id="7c999-107">You can copy, change, and maintain the code more easily.</span></span>  
  
-   <span data-ttu-id="7c999-108">Kodunuzu Visual Basic için "en iyi uygulamaları" göstermesini sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7c999-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="7c999-109">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="7c999-109">Naming Conventions</span></span>  
  
-   <span data-ttu-id="7c999-110">Adlandırma yönergeleri hakkında daha fazla bilgi için bkz: [adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konu.</span><span class="sxs-lookup"><span data-stu-id="7c999-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
-   <span data-ttu-id="7c999-111">Bir değişken adının parçası olarak "My" veya "my" kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7c999-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="7c999-112">Bu yöntem karışıklık oluşturur `My` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7c999-112">This practice creates confusion with the `My` objects.</span></span>  
  
-   <span data-ttu-id="7c999-113">Nesnelerin yönergelere sığması olacak şekilde otomatik olarak oluşturulan kod adlarını değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7c999-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="7c999-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="7c999-114">Layout Conventions</span></span>  
  
-   <span data-ttu-id="7c999-115">Sekmeleri boşluk olarak ekleyin ve dört boşluklu akıllı girintileme kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
-   <span data-ttu-id="7c999-116">Kullanım **(yeniden biçimlendirme) kodu düzgün listeleme** Kod düzenleyicisinde kodunuzu yeniden biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="7c999-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="7c999-117">Daha fazla bilgi için [seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7c999-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
-   <span data-ttu-id="7c999-118">Her satırda yalnızca bir deyim kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-118">Use only one statement per line.</span></span> <span data-ttu-id="7c999-119">Visual Basic Satır Ayırıcı karakterini (:) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7c999-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
-   <span data-ttu-id="7c999-120">Dil her izin verdiğinde örtük satır devamlılığı açık satır devamlılığı karakterini "_" kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="7c999-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
-   <span data-ttu-id="7c999-121">Her satırda yalnızca bir bildirim kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-121">Use only one declaration per line.</span></span>  
  
-   <span data-ttu-id="7c999-122">Varsa **(yeniden biçimlendirme) kodu düzgün listeleme** devamlılık satırlarını otomatik olarak, el ile devamlılık satırlarını bir sekme durağı girinti verin.</span><span class="sxs-lookup"><span data-stu-id="7c999-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="7c999-123">Ancak, her zaman sola bir listedeki öğeler Hizala.</span><span class="sxs-lookup"><span data-stu-id="7c999-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
-   <span data-ttu-id="7c999-124">Yöntem ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c999-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="7c999-125">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="7c999-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="7c999-126">Açıklamaları bir kod satırının sonundaki yerine ayrı bir satıra yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7c999-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="7c999-127">Son yorum metnini noktayla yanı sıra büyük harfle yorum metni başlatın.</span><span class="sxs-lookup"><span data-stu-id="7c999-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
-   <span data-ttu-id="7c999-128">Açıklama sınırlayıcısı (') ve açıklama metni arasına tek boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7c999-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_1.vb)]  
  
-   <span data-ttu-id="7c999-129">Biçimlendirilmiş yıldız işareti blokları yorumlarla başına değil.</span><span class="sxs-lookup"><span data-stu-id="7c999-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="7c999-130">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="7c999-130">Program Structure</span></span>  
  
-   <span data-ttu-id="7c999-131">Kullanırken `Main` yöntemi, yeni konsol uygulamaları için varsayılan yapıyı kullanın ve kullanmak `My` için komut satırı bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="7c999-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_2.vb)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="7c999-132">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="7c999-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="7c999-133">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7c999-133">String Data Type</span></span>  
  
-   <span data-ttu-id="7c999-134">Dizeleri birleştirmek için bir ve işareti kullanın (&).</span><span class="sxs-lookup"><span data-stu-id="7c999-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_3.vb)]  
  
-   <span data-ttu-id="7c999-135">Döngülere diziler eklemek için kullanın <xref:System.Text.StringBuilder> nesne.</span><span class="sxs-lookup"><span data-stu-id="7c999-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_4.vb)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="7c999-136">Olay işleyicileri'ndeki gevşek temsilciler</span><span class="sxs-lookup"><span data-stu-id="7c999-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="7c999-137">Bağımsız değişkenleri (Object ve EventArgs) açıkça olay işleyicilerine nitelendirmeyin.</span><span class="sxs-lookup"><span data-stu-id="7c999-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="7c999-138">Bir olaya (örneğin, nesne olarak gönderen, EventArgs olarak e) geçirilen olay bağımsız değişkenlerinin kullanmıyorsanız, gevşek temsilcileri kullanın ve olay bağımsız değişkenlerini kodunuzun içinde bırakın:</span><span class="sxs-lookup"><span data-stu-id="7c999-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_5.vb)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="7c999-139">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="7c999-139">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="7c999-140">Kullanım `Integer` gerekli olduğu dışında imzasız türler yerine.</span><span class="sxs-lookup"><span data-stu-id="7c999-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="7c999-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="7c999-141">Arrays</span></span>  
  
-   <span data-ttu-id="7c999-142">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="7c999-143">Örneğin, aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_6.vb)]  
  
     <span data-ttu-id="7c999-144">Aşağıdaki sözdizimini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="7c999-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_7.vb)]  
  
-   <span data-ttu-id="7c999-145">Dizi göstergesini, tür, değişken üzerinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7c999-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="7c999-146">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c999-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_8.vb)]  
  
     <span data-ttu-id="7c999-147">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="7c999-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_9.vb)]  
  
-   <span data-ttu-id="7c999-148">Bildirme ve temel veri türleri dizilerini başlatmak {} sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="7c999-149">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c999-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_10.vb)]  
  
     <span data-ttu-id="7c999-150">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="7c999-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_11.vb)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="7c999-151">Kullanım anahtar sözcüğü ile</span><span class="sxs-lookup"><span data-stu-id="7c999-151">Use the With Keyword</span></span>  
 <span data-ttu-id="7c999-152">Bir dizi bir nesneye çağrısı yaptığınızda kullanmayı `With` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="7c999-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_12.vb)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="7c999-153">Try kullan... Catch ve Using deyimlerini özel durum işlemeyi kullandığınızda</span><span class="sxs-lookup"><span data-stu-id="7c999-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="7c999-154">Kullanmayın `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="7c999-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="7c999-155">IsNot anahtar sözcüğünü kullanın</span><span class="sxs-lookup"><span data-stu-id="7c999-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="7c999-156">Kullanım `IsNot` anahtar sözcüğü yerine `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7c999-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="7c999-157">Yeni anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="7c999-157">New Keyword</span></span>  
  
-   <span data-ttu-id="7c999-158">Kısa örnekleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-158">Use short instantiation.</span></span> <span data-ttu-id="7c999-159">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c999-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_13.vb)]  
  
     <span data-ttu-id="7c999-160">Önceki satır aşağıdakine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="7c999-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_14.vb)]  
  
-   <span data-ttu-id="7c999-161">Parametresiz oluşturucusu yerine yeni nesneler için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c999-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_15.vb)]  
  
### <a name="event-handling"></a><span data-ttu-id="7c999-162">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="7c999-162">Event Handling</span></span>  
  
-   <span data-ttu-id="7c999-163">Kullanım `Handles` yerine `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="7c999-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_16.vb)]  
  
-   <span data-ttu-id="7c999-164">Kullanım `AddressOf`ve temsilciyi açıkça örneklemeyin:</span><span class="sxs-lookup"><span data-stu-id="7c999-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_17.vb)]  
  
-   <span data-ttu-id="7c999-165">Bir olay tanımladığınızda kısa sözdizimi kullanın ve derleyicinin temsilciyi tanımlamasına olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="7c999-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_18.vb)]  
  
-   <span data-ttu-id="7c999-166">Bir olay olup olmadığını doğrulamayın `Nothing` (null) çağırmadan önce `RaiseEvent` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7c999-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="7c999-167">`RaiseEvent` denetler `Nothing` olayı yükseltmeden önce.</span><span class="sxs-lookup"><span data-stu-id="7c999-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="7c999-168">Paylaşılan üyeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7c999-168">Using Shared Members</span></span>  
 <span data-ttu-id="7c999-169">Çağrı `Shared` bir örnek değişkeninden değil sınıf adını kullanarak üyeleri.</span><span class="sxs-lookup"><span data-stu-id="7c999-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="7c999-170">XML değişmez değerleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7c999-170">Use XML Literals</span></span>  
 <span data-ttu-id="7c999-171">XML değişmez değerleri (örneğin, yük, sorgu ve dönüşüm) XML ile çalışırken karşılaştığınız en yaygın görevleri basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="7c999-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="7c999-172">XML ile geliştirdiğinizde, aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="7c999-172">When you develop with XML, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="7c999-173">XML belgeleri ve XML API'lerini doğrudan çağırmak yerine parçaları oluşturmak için XML sabit değerleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
-   <span data-ttu-id="7c999-174">XML ad alanları XML sabit değerleri için performans iyileştirmeleri yararlanmak için dosyası veya proje düzeyinde içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="7c999-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
-   <span data-ttu-id="7c999-175">Öğeleri ve özniteliklerinin bir XML belgesi erişmek için XML eksen özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c999-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
-   <span data-ttu-id="7c999-176">Değerler ve gibi API çağrılarını kullanmak yerine var olan değerlerden XML oluşturmak için katıştırılmış ifadeleri kullanın `Add` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7c999-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_19.vb)]  
  
### <a name="linq-queries"></a><span data-ttu-id="7c999-177">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="7c999-177">LINQ Queries</span></span>  
  
-   <span data-ttu-id="7c999-178">Sorgu değişkenleri için anlamlı adlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c999-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_20.vb)]  
  
-   <span data-ttu-id="7c999-179">Pascal kullanarak anonim türlerinin özellik adlarının doğru olduğundan emin olmak için bir sorgu içindeki öğeler için adlar sağlamak büyük/küçük harf:</span><span class="sxs-lookup"><span data-stu-id="7c999-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_21.vb)]  
  
-   <span data-ttu-id="7c999-180">Sonuçtaki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="7c999-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="7c999-181">Sorgunuz bir müşteri adı ve sipariş kimliği verir, örneğin, bunları olarak bırakmak yerine Yeniden Adlandır `Name` ve `ID` sonuç:</span><span class="sxs-lookup"><span data-stu-id="7c999-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_22.vb)]  
  
-   <span data-ttu-id="7c999-182">Sorgu değişkenleri ve aralık değişkenleri bildiriminde tür çıkarımını kullanın:</span><span class="sxs-lookup"><span data-stu-id="7c999-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_23.vb)]  
  
-   <span data-ttu-id="7c999-183">Altında sorgu yan tümcelerini hizalayın `From` deyimi:</span><span class="sxs-lookup"><span data-stu-id="7c999-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_24.vb)]  
  
-   <span data-ttu-id="7c999-184">Kullanım `Where` yan tümceleri önce diğer sorgu yan tümceleri böylece sonraki sorgu yan tümcelerinin filtrelenmiş veri kümesinde çalışır:</span><span class="sxs-lookup"><span data-stu-id="7c999-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_25.vb)]  
  
-   <span data-ttu-id="7c999-185">Kullanım `Join` kullanmak yerine bir birleştirme işlemini açıkça tanımlamak için `Where` örtük olarak bir birleştirme işlemi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="7c999-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/coding-conventions_26.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7c999-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c999-186">See also</span></span>
- [<span data-ttu-id="7c999-187">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="7c999-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
