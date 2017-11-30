---
title: "Visual Basic'de Koşullu Derleme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 559380dc9baceb2fba4dca782e83f335f1bcd92d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="c8358-102">Visual Basic'de Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="c8358-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="c8358-103">İçinde *koşullu derleme*, belirli bir programı kod bloklarını diğerleri yoksayılır sırada seçmeli olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="c8358-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="c8358-104">Örneğin, yazmak isteyebilirsiniz aynı programlama görev veya farklı yaklaşımlara hızını karşılaştırma ifadeleri hata ayıklama bir uygulama için birden çok dilde yerelleştirme isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="c8358-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="c8358-105">Koşullu derleme deyimleri, çalışma zamanında derleme süresi sırasında çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8358-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="c8358-106">İle koşullu derlenmiş kod bloklarını belirtmek `#If...Then...#Else` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="c8358-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="c8358-107">Örneğin, Fransızca ve Almanca dil oluşturmak için aynı uygulama aynı sürümlerini kaynak kodu, platforma özgü kod kesimlerinde katıştırmak `#If...Then` önceden tanımlanmış sabitleri using deyimleri `FrenchVersion` ve `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="c8358-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="c8358-108">Aşağıdaki örnekte gösterilmiştir nasıl:</span><span class="sxs-lookup"><span data-stu-id="c8358-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/conditional-compilation_1.vb)]  
  
 <span data-ttu-id="c8358-109">Değerini ayarlarsanız `FrenchVersion` koşullu derleme sabiti `True` derleme zamanında Fransızca sürümü koşullu kodunu derlenir.</span><span class="sxs-lookup"><span data-stu-id="c8358-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="c8358-110">Değerini ayarlarsanız `GermanVersion` için sabit `True`, Almanca sürümü derleyici kullanır.</span><span class="sxs-lookup"><span data-stu-id="c8358-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="c8358-111">Hiçbiri ayarlanmışsa `True`, son kodda `Else` engelleme çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c8358-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8358-112">Otomatik Tamamlama düzenleme kodlarken çalışmamasına ve kod geçerli dalı parçası değilse, koşullu derleme yönergeleri kullanarak olur.</span><span class="sxs-lookup"><span data-stu-id="c8358-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="c8358-113">Koşullu derleme Sabitleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="c8358-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="c8358-114">Koşullu derleme sabitleri üç şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c8358-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
-   <span data-ttu-id="c8358-115">İçinde **Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="c8358-115">In the **Project Designer**</span></span>  
  
-   <span data-ttu-id="c8358-116">Komut satırı derleyicisi kullanırken komut satırında</span><span class="sxs-lookup"><span data-stu-id="c8358-116">At the command line when using the command-line compiler</span></span>  
  
-   <span data-ttu-id="c8358-117">Kodunuzda</span><span class="sxs-lookup"><span data-stu-id="c8358-117">In your code</span></span>  
  
 <span data-ttu-id="c8358-118">Koşullu derleme sabitleri özel bir kapsama sahip ve standart koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="c8358-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="c8358-119">Koşullu derleme sabiti kapsamını ayarlandı yolda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c8358-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="c8358-120">Aşağıdaki tabloda her yukarıdaki üç yolla kullanılarak bildirilen sabitleri kapsamını listeler.</span><span class="sxs-lookup"><span data-stu-id="c8358-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="c8358-121">Sabiti nasıl ayarlanır</span><span class="sxs-lookup"><span data-stu-id="c8358-121">How constant is set</span></span>|<span data-ttu-id="c8358-122">Kapsamı sabiti</span><span class="sxs-lookup"><span data-stu-id="c8358-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="c8358-123">**Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="c8358-123">**Project Designer**</span></span>|<span data-ttu-id="c8358-124">Projedeki tüm dosyalar için genel</span><span class="sxs-lookup"><span data-stu-id="c8358-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="c8358-125">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="c8358-125">Command line</span></span>|<span data-ttu-id="c8358-126">Komut satırı derleyicisi geçirilen tüm dosyalara genel</span><span class="sxs-lookup"><span data-stu-id="c8358-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="c8358-127">`#Const`kodda deyimi</span><span class="sxs-lookup"><span data-stu-id="c8358-127">`#Const` statement in code</span></span>|<span data-ttu-id="c8358-128">İçinde bildirilmiş dosyasına özel</span><span class="sxs-lookup"><span data-stu-id="c8358-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="c8358-129">Proje Tasarımcısı'nda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c8358-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="c8358-130">-Sabitler yürütülebilir dosyanızı oluşturma önce kümesinde **Proje Tasarımcısı** içinde sağlanan adımları izleyerek [yönetme proje ve çözüm özelliklerini](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="c8358-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="c8358-131">Komut satırında sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c8358-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="c8358-132">-Kullanın **/d** anahtar aşağıdaki örnekteki gibi koşullu derleme sabitleri girin:</span><span class="sxs-lookup"><span data-stu-id="c8358-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="c8358-133">Arasında boşluk gereklidir **/d** anahtarı ve ilk sabiti.</span><span class="sxs-lookup"><span data-stu-id="c8358-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="c8358-134">Daha fazla bilgi için bkz: [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="c8358-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="c8358-135">Komut satırı bildirimleri geçersiz kılma girilen bildirimleri **Proje Tasarımcısı**, ancak bunları silme değil.</span><span class="sxs-lookup"><span data-stu-id="c8358-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="c8358-136">Bağımsız değişkenler kümesinde **Proje Tasarımcısı** sonraki derlemeler için yürürlükte kalır.</span><span class="sxs-lookup"><span data-stu-id="c8358-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="c8358-137">Sabitler kodda yazarken, katı kural yok onların yerini aldığını kapsamlarına bildirilen tüm modülü olduğundan.</span><span class="sxs-lookup"><span data-stu-id="c8358-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="c8358-138">Kodunuzda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="c8358-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="c8358-139">-Sabitleri kullanılacak modülünü bildirimi bloğunda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="c8358-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="c8358-140">Bu, kodunuzu düzenli ve kolay okunur tutmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c8358-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="c8358-141">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="c8358-141">Related Topics</span></span>  
  
|<span data-ttu-id="c8358-142">Başlık</span><span class="sxs-lookup"><span data-stu-id="c8358-142">Title</span></span>|<span data-ttu-id="c8358-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8358-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="c8358-144">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="c8358-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="c8358-145">Kodunuzu okuyun ve sürdürmek daha kolay yapmak için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8358-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="c8358-146">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c8358-146">Reference</span></span>  
 [<span data-ttu-id="c8358-147">#Const yönergesi</span><span class="sxs-lookup"><span data-stu-id="c8358-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="c8358-148">#If... Then... #Else yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c8358-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="c8358-149">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8358-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
