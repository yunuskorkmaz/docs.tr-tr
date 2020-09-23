---
title: Kodlama Kuralları
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: eae283c757ddeb1290c15d82a41c8028a8941e63
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059164"
---
# <a name="visual-basic-coding-conventions"></a><span data-ttu-id="a60c2-102">Visual Basic Kodlama Kuralları</span><span class="sxs-lookup"><span data-stu-id="a60c2-102">Visual Basic Coding Conventions</span></span>

<span data-ttu-id="a60c2-103">Microsoft, bu konudaki yönergeleri izleyen örnekler ve belgeler geliştirir.</span><span class="sxs-lookup"><span data-stu-id="a60c2-103">Microsoft develops samples and documentation that follow the guidelines in this topic.</span></span> <span data-ttu-id="a60c2-104">Aynı kodlama kurallarını izlerseniz, aşağıdaki avantajları elde edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a60c2-104">If you follow the same coding conventions, you may gain the following benefits:</span></span>  
  
- <span data-ttu-id="a60c2-105">Kodunuzun tutarlı bir görünümü olur, böylece okuyucular düzene göre değil içeriğe daha iyi odaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="a60c2-105">Your code will have a consistent look, so that readers can better focus on content, not layout.</span></span>  
  
- <span data-ttu-id="a60c2-106">Okuyucular, önceki deneyimle ilgili varsayımlar yapabildiğinden kodunuzu daha hızlı bir şekilde öğrenirler.</span><span class="sxs-lookup"><span data-stu-id="a60c2-106">Readers understand your code more quickly because they can make assumptions based on previous experience.</span></span>  
  
- <span data-ttu-id="a60c2-107">Kodu daha kolay kopyalayabilir, değiştirebilir ve bakımını yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a60c2-107">You can copy, change, and maintain the code more easily.</span></span>  
  
- <span data-ttu-id="a60c2-108">Kodunuzun, Visual Basic için "en iyi uygulamaları" gösterdiği sağlanmasına yardımcı olursunuz.</span><span class="sxs-lookup"><span data-stu-id="a60c2-108">You help ensure that your code demonstrates "best practices" for Visual Basic.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="a60c2-109">Adlandırma Kuralları</span><span class="sxs-lookup"><span data-stu-id="a60c2-109">Naming Conventions</span></span>  
  
- <span data-ttu-id="a60c2-110">Adlandırma yönergeleri hakkında daha fazla bilgi için bkz. [Adlandırma yönergeleri](../../../standard/design-guidelines/naming-guidelines.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="a60c2-110">For information about naming guidelines, see [Naming Guidelines](../../../standard/design-guidelines/naming-guidelines.md) topic.</span></span>  
  
- <span data-ttu-id="a60c2-111">Değişken adının bir parçası olarak "My" veya "My" kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-111">Do not use "My" or "my" as part of a variable name.</span></span> <span data-ttu-id="a60c2-112">Bu uygulama, nesneleriyle karışıklık oluşturur `My` .</span><span class="sxs-lookup"><span data-stu-id="a60c2-112">This practice creates confusion with the `My` objects.</span></span>  
  
- <span data-ttu-id="a60c2-113">Otomatik olarak oluşturulan koddaki nesnelerin adlarını, kurallara uyacak şekilde değiştirmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a60c2-113">You do not have to change the names of objects in auto-generated code to make them fit the guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="a60c2-114">Düzeni Kuralları</span><span class="sxs-lookup"><span data-stu-id="a60c2-114">Layout Conventions</span></span>  
  
- <span data-ttu-id="a60c2-115">Sekmeleri boşluk olarak ekleyin ve dört boşluklu girintilerle akıllı girintileme kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-115">Insert tabs as spaces, and use smart indenting with four-space indents.</span></span>  
  
- <span data-ttu-id="a60c2-116">Kod düzenleyicisinde kodunuzu yeniden biçimlendirmek için **kodun düzgün listesini (yeniden biçimlendirme)** kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-116">Use **Pretty listing (reformatting) of code** to reformat your code in the code editor.</span></span> <span data-ttu-id="a60c2-117">Daha fazla bilgi için bkz. [Seçenekler, metin düzenleyici, temel (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="a60c2-117">For more information, see [Options, Text Editor, Basic (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).</span></span>  
  
- <span data-ttu-id="a60c2-118">Her satırda yalnızca bir ifade kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-118">Use only one statement per line.</span></span> <span data-ttu-id="a60c2-119">Visual Basic çizgi ayırıcı karakterini kullanmayın (:).</span><span class="sxs-lookup"><span data-stu-id="a60c2-119">Don't use the Visual Basic line separator character (:).</span></span>  
  
- <span data-ttu-id="a60c2-120">"_" Açık satır devamlılığı, dilin izin verdiği her yerde örtük satır devamlılığı kullanımına karşı kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="a60c2-120">Avoid using the explicit line continuation character "_" in favor of implicit line continuation wherever the language allows it.</span></span>  
  
- <span data-ttu-id="a60c2-121">Her satırda yalnızca bir bildirim kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-121">Use only one declaration per line.</span></span>  
  
- <span data-ttu-id="a60c2-122">**Kodun düzgün listelenmesi (yeniden biçimlendirilmesi)** devam satırlarını otomatik olarak biçimlendirmezse, devamlılık satırlarını bir sekme durağı olarak el ile girintileyin.</span><span class="sxs-lookup"><span data-stu-id="a60c2-122">If **Pretty listing (reformatting) of code** doesn't format continuation lines automatically, manually indent continuation lines one tab stop.</span></span> <span data-ttu-id="a60c2-123">Ancak, her zaman bir listedeki öğeleri sola hizalayın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-123">However, always left-align items in a list.</span></span>  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- <span data-ttu-id="a60c2-124">Yöntem ve özellik tanımları arasına en az bir boş satır ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a60c2-124">Add at least one blank line between method and property definitions.</span></span>  
  
## <a name="commenting-conventions"></a><span data-ttu-id="a60c2-125">Yorum Oluşturma Kuralları</span><span class="sxs-lookup"><span data-stu-id="a60c2-125">Commenting Conventions</span></span>  
  
- <span data-ttu-id="a60c2-126">Açıklamaları bir kod satırının sonu yerine ayrı bir satıra koyun.</span><span class="sxs-lookup"><span data-stu-id="a60c2-126">Put comments on a separate line instead of at the end of a line of code.</span></span>  
  
- <span data-ttu-id="a60c2-127">Açıklama metnini büyük harfle başlatın ve açıklama metnini noktayla bitirin.</span><span class="sxs-lookup"><span data-stu-id="a60c2-127">Start comment text with an uppercase letter, and end comment text with a period.</span></span>  
  
- <span data-ttu-id="a60c2-128">Açıklama sınırlayıcısı (') ve açıklama metni arasına bir boşluk ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a60c2-128">Insert one space between the comment delimiter (') and the comment text.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- <span data-ttu-id="a60c2-129">Açıklamaları, biçimli yıldız blokları ile çevrelemeyin.</span><span class="sxs-lookup"><span data-stu-id="a60c2-129">Do not surround comments with formatted blocks of asterisks.</span></span>  
  
## <a name="program-structure"></a><span data-ttu-id="a60c2-130">Program Yapısı</span><span class="sxs-lookup"><span data-stu-id="a60c2-130">Program Structure</span></span>  
  
- <span data-ttu-id="a60c2-131">`Main`Yöntemini kullandığınızda, yeni konsol uygulamaları için varsayılan yapıyı kullanın ve `My` komut satırı bağımsız değişkenleri için kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-131">When you use the `Main` method, use the default construct for new console applications, and use `My` for command-line arguments.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a><span data-ttu-id="a60c2-132">Dil Kuralları</span><span class="sxs-lookup"><span data-stu-id="a60c2-132">Language Guidelines</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="a60c2-133">Dize Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a60c2-133">String Data Type</span></span>  
  
- <span data-ttu-id="a60c2-134">Aşağıdaki kodda gösterildiği gibi, kısa dizeleri birleştirmek için [dize ilişkilendirmeyi](../language-features/strings/interpolated-strings.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-134">Use [string interpolation](../language-features/strings/interpolated-strings.md) to concatenate short strings, as shown in the following code.</span></span>
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- <span data-ttu-id="a60c2-135">Döngülerde dizeler eklemek için <xref:System.Text.StringBuilder> nesnesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-135">To append strings in loops, use the <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a><span data-ttu-id="a60c2-136">Olay Işleyicilerinde gevşek temsilciler</span><span class="sxs-lookup"><span data-stu-id="a60c2-136">Relaxed Delegates in Event Handlers</span></span>  

 <span data-ttu-id="a60c2-137">Bağımsız değişkenleri (Object ve EventArgs) olay işleyicileriyle açıkça nitelemeyin.</span><span class="sxs-lookup"><span data-stu-id="a60c2-137">Do not explicitly qualify the arguments (Object and EventArgs) to event handlers.</span></span> <span data-ttu-id="a60c2-138">Bir olaya iletilen olay bağımsız değişkenlerini kullanmıyorsanız (örneğin, gönderen nesne, EventArgs olarak e), gevşek temsilciler kullanın ve kodunuzda olay bağımsız değişkenlerini bırakın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-138">If you are not using the event arguments that are passed to an event (for example, sender as Object, e as EventArgs), use relaxed delegates, and leave out the event arguments in your code:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="a60c2-139">İmzasız Veri Türü</span><span class="sxs-lookup"><span data-stu-id="a60c2-139">Unsigned Data Type</span></span>  
  
- <span data-ttu-id="a60c2-140">`Integer`Gerekli olduğu durumlar dışında, imzasız türler yerine kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-140">Use `Integer` rather than unsigned types, except where they are necessary.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="a60c2-141">Diziler</span><span class="sxs-lookup"><span data-stu-id="a60c2-141">Arrays</span></span>  
  
- <span data-ttu-id="a60c2-142">Bildirim satırında dizileri başlattığınızda kısa sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-142">Use the short syntax when you initialize arrays on the declaration line.</span></span> <span data-ttu-id="a60c2-143">Örneğin, aşağıdaki sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-143">For example, use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     <span data-ttu-id="a60c2-144">Aşağıdaki sözdizimini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-144">Do not use the following syntax.</span></span>  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- <span data-ttu-id="a60c2-145">Dizi göstergesini değişkene değil, türüne koyun.</span><span class="sxs-lookup"><span data-stu-id="a60c2-145">Put the array designator on the type, not on the variable.</span></span> <span data-ttu-id="a60c2-146">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-146">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     <span data-ttu-id="a60c2-147">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-147">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- <span data-ttu-id="a60c2-148">Temel veri türleri dizilerini bildirdiğinizde ve başlattığınızda {} sözdizimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-148">Use the { } syntax when you declare and initialize arrays of basic data types.</span></span> <span data-ttu-id="a60c2-149">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-149">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     <span data-ttu-id="a60c2-150">Aşağıdaki sözdizimini kullanmayın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-150">Do not use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a><span data-ttu-id="a60c2-151">WITH anahtar sözcüğünü kullanma</span><span class="sxs-lookup"><span data-stu-id="a60c2-151">Use the With Keyword</span></span>  

 <span data-ttu-id="a60c2-152">Bir nesneye bir dizi çağrı yaptığınızda, `With` anahtar sözcüğünü kullanmayı düşünün:</span><span class="sxs-lookup"><span data-stu-id="a60c2-152">When you make a series of calls to one object, consider using the `With` keyword:</span></span>  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a><span data-ttu-id="a60c2-153">TRY... öğesini kullanın Özel durum Işleme kullandığınızda deyimleri yakalama ve kullanma</span><span class="sxs-lookup"><span data-stu-id="a60c2-153">Use the Try...Catch and Using Statements when you use Exception Handling</span></span>  

 <span data-ttu-id="a60c2-154">Kullanmayın `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="a60c2-154">Do not use `On Error Goto`.</span></span>  
  
### <a name="use-the-isnot-keyword"></a><span data-ttu-id="a60c2-155">Inot anahtar sözcüğünü kullanma</span><span class="sxs-lookup"><span data-stu-id="a60c2-155">Use the IsNot Keyword</span></span>  

 <span data-ttu-id="a60c2-156">`IsNot`Yerine anahtar sözcüğünü kullanın `Not...Is Nothing` .</span><span class="sxs-lookup"><span data-stu-id="a60c2-156">Use the `IsNot` keyword instead of `Not...Is Nothing`.</span></span>  
  
### <a name="new-keyword"></a><span data-ttu-id="a60c2-157">Yeni anahtar sözcük</span><span class="sxs-lookup"><span data-stu-id="a60c2-157">New Keyword</span></span>  
  
- <span data-ttu-id="a60c2-158">Kısa örnek oluşturma kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-158">Use short instantiation.</span></span> <span data-ttu-id="a60c2-159">Örneğin, aşağıdaki sözdizimini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-159">For example, use the following syntax:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     <span data-ttu-id="a60c2-160">Yukarıdaki satır buna eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="a60c2-160">The preceding line is equivalent to this:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- <span data-ttu-id="a60c2-161">Parametresiz Oluşturucu yerine yeni nesneler için nesne başlatıcıları kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-161">Use object initializers for new objects instead of the parameterless constructor:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a><span data-ttu-id="a60c2-162">Olay İşleme</span><span class="sxs-lookup"><span data-stu-id="a60c2-162">Event Handling</span></span>  
  
- <span data-ttu-id="a60c2-163">`Handles`Yerine kullanın `AddHandler` :</span><span class="sxs-lookup"><span data-stu-id="a60c2-163">Use `Handles` rather than `AddHandler`:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- <span data-ttu-id="a60c2-164">`AddressOf`Öğesini kullanın ve temsilciyi açıkça örneğini oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a60c2-164">Use `AddressOf`, and do not instantiate the delegate explicitly:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- <span data-ttu-id="a60c2-165">Bir olay tanımladığınızda, kısa sözdizimini kullanın ve derleyicinin temsilciyi tanımlamasına izin verin:</span><span class="sxs-lookup"><span data-stu-id="a60c2-165">When you define an event, use the short syntax, and let the compiler define the delegate:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- <span data-ttu-id="a60c2-166">`Nothing`Yöntemi çağırmadan önce bir olayın (null) olup olmadığını doğrulama `RaiseEvent` .</span><span class="sxs-lookup"><span data-stu-id="a60c2-166">Do not verify whether an event is `Nothing` (null) before you call the `RaiseEvent` method.</span></span> <span data-ttu-id="a60c2-167">`RaiseEvent``Nothing`olayı oluşturmadan önce olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="a60c2-167">`RaiseEvent` checks for `Nothing` before it raises the event.</span></span>  
  
### <a name="using-shared-members"></a><span data-ttu-id="a60c2-168">Paylaşılan üyeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="a60c2-168">Using Shared Members</span></span>  

 <span data-ttu-id="a60c2-169">`Shared`Bir örnek değişkeninden değil sınıf adını kullanarak üyeleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-169">Call `Shared` members by using the class name, not from an instance variable.</span></span>  
  
### <a name="use-xml-literals"></a><span data-ttu-id="a60c2-170">XML değişmez değerlerini kullan</span><span class="sxs-lookup"><span data-stu-id="a60c2-170">Use XML Literals</span></span>  

 <span data-ttu-id="a60c2-171">XML sabit değerleri, XML ile çalışırken karşılaşabileceğiniz en yaygın görevleri basitleştirir (örneğin, Load, Query ve Transform).</span><span class="sxs-lookup"><span data-stu-id="a60c2-171">XML literals simplify the most common tasks that you encounter when you work with XML (for example, load, query, and transform).</span></span> <span data-ttu-id="a60c2-172">XML ile geliştirme yaparken şu yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="a60c2-172">When you develop with XML, follow these guidelines:</span></span>  
  
- <span data-ttu-id="a60c2-173">XML API 'Lerini doğrudan çağırmak yerine XML belgelerini ve parçalarını oluşturmak için XML değişmez değerlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-173">Use XML literals to create XML documents and fragments instead of calling XML APIs directly.</span></span>  
  
- <span data-ttu-id="a60c2-174">XML değişmez değerleri için performans iyileştirmelerinden faydalanmak için dosya veya proje düzeyinde XML ad alanlarını içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-174">Import XML namespaces at the file or project level to take advantage of the performance optimizations for XML literals.</span></span>  
  
- <span data-ttu-id="a60c2-175">XML belgesindeki öğelere ve özniteliklere erişmek için XML eksen özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-175">Use the XML axis properties to access elements and attributes in an XML document.</span></span>  
  
- <span data-ttu-id="a60c2-176">Yöntem gibi API çağrılarını kullanmak yerine mevcut değerlerden XML oluşturmak ve değerleri dahil etmek için gömülü ifadeleri kullanın `Add` :</span><span class="sxs-lookup"><span data-stu-id="a60c2-176">Use embedded expressions to include values and to create XML from existing values instead of using API calls such as the `Add` method:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a><span data-ttu-id="a60c2-177">LINQ Sorguları</span><span class="sxs-lookup"><span data-stu-id="a60c2-177">LINQ Queries</span></span>  
  
- <span data-ttu-id="a60c2-178">Sorgu değişkenleri için anlamlı adlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-178">Use meaningful names for query variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- <span data-ttu-id="a60c2-179">Anonim türlerin özellik adlarının, Pascal büyük harfleri kullanarak doğru şekilde büyük harfli olduğundan emin olmak için bir sorgudaki öğelerin adlarını sağlayın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-179">Provide names for elements in a query to make sure that property names of anonymous types are correctly capitalized using Pascal casing:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- <span data-ttu-id="a60c2-180">Sonuç içindeki Özellik adları belirsiz olduğunda özellikleri yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a60c2-180">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="a60c2-181">Örneğin, sorgunuz bir müşteri adı ve bir sipariş KIMLIĞI döndürürse, bunları ve sonuç olarak bırakmak yerine yeniden adlandırın `Name` `ID` :</span><span class="sxs-lookup"><span data-stu-id="a60c2-181">For example, if your query returns a customer name and an order ID, rename them instead of leaving them as `Name` and `ID` in the result:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- <span data-ttu-id="a60c2-182">Sorgu değişkenleri ve Aralık değişkenleri bildiriminde tür çıkarımı kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-182">Use type inference in the declaration of query variables and range variables:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- <span data-ttu-id="a60c2-183">Sorgu yan tümcelerini deyimin altına Hizala `From` :</span><span class="sxs-lookup"><span data-stu-id="a60c2-183">Align query clauses under the `From` statement:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- <span data-ttu-id="a60c2-184">`Where`Daha sonra sorgu yan tümcelerinin filtrelenmiş veri kümesinde çalışması için diğer sorgu yan tümcelerinden önce yan tümceleri kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-184">Use `Where` clauses before other query clauses so that later query clauses operate on the filtered set of data:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- <span data-ttu-id="a60c2-185">`Join` `Where` Bir JOIN işlemini örtük olarak tanımlamak için yan tümcesini kullanmak yerine bir JOIN işlemini açıkça tanımlamak için yan tümcesini kullanın:</span><span class="sxs-lookup"><span data-stu-id="a60c2-185">Use the `Join` clause to explicitly define a join operation instead of using the `Where` clause to implicitly define a join operation:</span></span>  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="a60c2-186">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a60c2-186">See also</span></span>

- [<span data-ttu-id="a60c2-187">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a60c2-187">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
