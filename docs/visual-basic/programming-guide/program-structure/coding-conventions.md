---
title: Visual Basic Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: fe07b01cfa62d8d1cbc2e4a61cac814425af7da0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639845"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="d38c8-102">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="d38c8-102">Visual Basic Coding Conventions</span></span>
<span data-ttu-id="d38c8-103">Microsoft, örnekler ve bu konudaki yönergeleri izleyen belgeler geliştirir.</span><span class="sxs-lookup"><span data-stu-id="d38c8-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="d38c8-104">Aynı kodlama kurallarını takip ederseniz, aşağıdaki faydaları elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d38c8-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="d38c8-105">Okuyucular düzene değil içeriğe göre daha iyi odaklanabilmeniz için kodunuzu tutarlı bir görünüm olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d38c8-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="d38c8-106">Bunlar önceki deneyime dayanan varsayımlar yapabilecekleri için Okuyucular kodunuzu daha hızlı bir şekilde anlayın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="d38c8-107">Kopyalama, değiştirme ve kodu daha kolay korumak.</span><span class="sxs-lookup"><span data-stu-id="d38c8-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="d38c8-108">Kodunuzu Visual Basic için "en iyi uygulamaları" göstermesini sağlamaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d38c8-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="d38c8-109">Adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="d38c8-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="d38c8-110">Adlandırma yönergeleri hakkında daha fazla bilgi için bkz: [adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konu.</span><span class="sxs-lookup"><span data-stu-id="d38c8-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="d38c8-111">Bir değişken adının parçası olarak "My" veya "my" kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="d38c8-112">Bu yöntem karışıklık oluşturur `My` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d38c8-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="d38c8-113">Nesnelerin yönergelere sığması olacak şekilde otomatik olarak oluşturulan kod adlarını değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d38c8-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="d38c8-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="d38c8-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="d38c8-115">Sekmeleri boşluk olarak ekleyin ve dört boşluklu akıllı girintileme kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="d38c8-116">Kullanım **(yeniden biçimlendirme) kodu düzgün listeleme** Kod düzenleyicisinde kodunuzu yeniden biçimlendirmek için.</span><span class="sxs-lookup"><span data-stu-id="d38c8-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="d38c8-117">Daha fazla bilgi için [seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d38c8-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="d38c8-118">Her satırda yalnızca bir deyim kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-118">Use only one statement per line.</span></span> <span data-ttu-id="d38c8-119">Visual Basic Satır Ayırıcı karakterini (:) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="d38c8-120">Dil her izin verdiğinde örtük satır devamlılığı açık satır devamlılığı karakterini "_" kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="d38c8-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="d38c8-121">Her satırda yalnızca bir bildirim kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="d38c8-122">Varsa **(yeniden biçimlendirme) kodu düzgün listeleme** devamlılık satırlarını otomatik olarak, el ile devamlılık satırlarını bir sekme durağı girinti verin.</span><span class="sxs-lookup"><span data-stu-id="d38c8-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="d38c8-123">Ancak, her zaman sola bir listedeki öğeler Hizala.</span><span class="sxs-lookup"><span data-stu-id="d38c8-123">However, always left-align items in a list.</span></span>  
  
    ```  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="d38c8-124">Yöntem ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d38c8-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="d38c8-125">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="d38c8-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="d38c8-126">Açıklamaları bir kod satırının sonundaki yerine ayrı bir satıra yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d38c8-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="d38c8-127">Son yorum metnini noktayla yanı sıra büyük harfle yorum metni başlatın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="d38c8-128">Açıklama sınırlayıcısı (') ve açıklama metni arasına tek boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d38c8-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="d38c8-129">Biçimlendirilmiş yıldız işareti blokları yorumlarla başına değil.</span><span class="sxs-lookup"><span data-stu-id="d38c8-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="d38c8-130">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="d38c8-130">Program Structure</span></span>  
  
- <span data-ttu-id="d38c8-131">Kullanırken `Main` yöntemi, yeni konsol uygulamaları için varsayılan yapıyı kullanın ve kullanmak `My` için komut satırı bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="d38c8-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="d38c8-132">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="d38c8-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="d38c8-133">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d38c8-133">String Data Type</span></span>  
  
- <span data-ttu-id="d38c8-134">Dizeleri birleştirmek için bir ve işareti kullanın (&).</span><span class="sxs-lookup"><span data-stu-id="d38c8-134">To concatenate strings, use an ampersand (&).</span></span>  
  
     [!code-vb[VbVbalrGuidelines#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#4)]  
  
- <span data-ttu-id="d38c8-135">Döngülere diziler eklemek için kullanın <xref:System.Text.StringBuilder> nesne.</span><span class="sxs-lookup"><span data-stu-id="d38c8-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="d38c8-136">Olay işleyicileri'ndeki gevşek temsilciler</span><span class="sxs-lookup"><span data-stu-id="d38c8-136">Relaxed Delegates in Event Handlers</span></span>  
 <span data-ttu-id="d38c8-137">Bağımsız değişkenleri (Object ve EventArgs) açıkça olay işleyicilerine nitelendirmeyin.</span><span class="sxs-lookup"><span data-stu-id="d38c8-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="d38c8-138">Bir olaya (örneğin, nesne olarak gönderen, EventArgs olarak e) geçirilen olay bağımsız değişkenlerinin kullanmıyorsanız, gevşek temsilcileri kullanın ve olay bağımsız değişkenlerini kodunuzun içinde bırakın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="d38c8-139">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="d38c8-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="d38c8-140">Kullanım `Integer` gerekli olduğu dışında imzasız türler yerine.</span><span class="sxs-lookup"><span data-stu-id="d38c8-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="d38c8-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="d38c8-141">Arrays</span></span>  
  
- <span data-ttu-id="d38c8-142">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="d38c8-143">Örneğin, aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="d38c8-144">Aşağıdaki sözdizimini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="d38c8-145">Dizi göstergesini, tür, değişken üzerinde yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d38c8-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="d38c8-146">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="d38c8-147">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="d38c8-148">Bildirme ve temel veri türleri dizilerini başlatmak {} sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="d38c8-149">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="d38c8-150">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="d38c8-151">Kullanım anahtar sözcüğü ile</span><span class="sxs-lookup"><span data-stu-id="d38c8-151">Use the With Keyword</span></span>  
 <span data-ttu-id="d38c8-152">Bir dizi bir nesneye çağrısı yaptığınızda kullanmayı `With` anahtar sözcüğü:</span><span class="sxs-lookup"><span data-stu-id="d38c8-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="d38c8-153">Try kullan... Catch ve Using deyimlerini özel durum işlemeyi kullandığınızda</span><span class="sxs-lookup"><span data-stu-id="d38c8-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  
 <span data-ttu-id="d38c8-154">Kullanmayın `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="d38c8-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="d38c8-155">IsNot anahtar sözcüğünü kullanın</span><span class="sxs-lookup"><span data-stu-id="d38c8-155">Use the IsNot Keyword</span></span>  
 <span data-ttu-id="d38c8-156">Kullanım `IsNot` anahtar sözcüğü yerine `Not...Is Nothing`.</span><span class="sxs-lookup"><span data-stu-id="d38c8-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="d38c8-157">Yeni anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d38c8-157">New Keyword</span></span>  
  
- <span data-ttu-id="d38c8-158">Kısa örnekleme kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-158">Use short instantiation.</span></span> <span data-ttu-id="d38c8-159">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="d38c8-160">Önceki satır aşağıdakine eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="d38c8-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="d38c8-161">Parametresiz oluşturucusu yerine yeni nesneler için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="d38c8-162">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="d38c8-162">Event Handling</span></span>  
  
- <span data-ttu-id="d38c8-163">Kullanım `Handles` yerine `AddHandler`:</span><span class="sxs-lookup"><span data-stu-id="d38c8-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="d38c8-164">Kullanım `AddressOf`ve temsilciyi açıkça örneklemeyin:</span><span class="sxs-lookup"><span data-stu-id="d38c8-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="d38c8-165">Bir olay tanımladığınızda kısa sözdizimi kullanın ve derleyicinin temsilciyi tanımlamasına olanak tanır:</span><span class="sxs-lookup"><span data-stu-id="d38c8-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="d38c8-166">Bir olay olup olmadığını doğrulamayın `Nothing` (null) çağırmadan önce `RaiseEvent` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d38c8-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="d38c8-167">`RaiseEvent` denetler `Nothing` olayı yükseltmeden önce.</span><span class="sxs-lookup"><span data-stu-id="d38c8-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="d38c8-168">Paylaşılan üyeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="d38c8-168">Using Shared Members</span></span>  
 <span data-ttu-id="d38c8-169">Çağrı `Shared` bir örnek değişkeninden değil sınıf adını kullanarak üyeleri.</span><span class="sxs-lookup"><span data-stu-id="d38c8-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="d38c8-170">XML değişmez değerleri kullanma</span><span class="sxs-lookup"><span data-stu-id="d38c8-170">Use XML Literals</span></span>  
 <span data-ttu-id="d38c8-171">XML değişmez değerleri (örneğin, yük, sorgu ve dönüşüm) XML ile çalışırken karşılaştığınız en yaygın görevleri basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="d38c8-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="d38c8-172">XML ile geliştirdiğinizde, aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="d38c8-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="d38c8-173">XML belgeleri ve XML API'lerini doğrudan çağırmak yerine parçaları oluşturmak için XML sabit değerleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="d38c8-174">XML ad alanları XML sabit değerleri için performans iyileştirmeleri yararlanmak için dosyası veya proje düzeyinde içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="d38c8-175">Öğeleri ve özniteliklerinin bir XML belgesi erişmek için XML eksen özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="d38c8-176">Değerler ve gibi API çağrılarını kullanmak yerine var olan değerlerden XML oluşturmak için katıştırılmış ifadeleri kullanın `Add` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d38c8-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="d38c8-177">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="d38c8-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="d38c8-178">Sorgu değişkenleri için anlamlı adlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="d38c8-179">Pascal kullanarak anonim türlerinin özellik adlarının doğru olduğundan emin olmak için bir sorgu içindeki öğeler için adlar sağlamak büyük/küçük harf:</span><span class="sxs-lookup"><span data-stu-id="d38c8-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="d38c8-180">Sonuçtaki özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d38c8-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="d38c8-181">Sorgunuz bir müşteri adı ve sipariş kimliği verir, örneğin, bunları olarak bırakmak yerine Yeniden Adlandır `Name` ve `ID` sonuç:</span><span class="sxs-lookup"><span data-stu-id="d38c8-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="d38c8-182">Sorgu değişkenleri ve aralık değişkenleri bildiriminde tür çıkarımını kullanın:</span><span class="sxs-lookup"><span data-stu-id="d38c8-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="d38c8-183">Altında sorgu yan tümcelerini hizalayın `From` deyimi:</span><span class="sxs-lookup"><span data-stu-id="d38c8-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="d38c8-184">Kullanım `Where` yan tümceleri önce diğer sorgu yan tümceleri böylece sonraki sorgu yan tümcelerinin filtrelenmiş veri kümesinde çalışır:</span><span class="sxs-lookup"><span data-stu-id="d38c8-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="d38c8-185">Kullanım `Join` kullanmak yerine bir birleştirme işlemini açıkça tanımlamak için `Where` örtük olarak bir birleştirme işlemi tanımlamak için:</span><span class="sxs-lookup"><span data-stu-id="d38c8-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="d38c8-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d38c8-186">See also</span></span>

- [<span data-ttu-id="d38c8-187">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="d38c8-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
