---
title: Visual Basic'de Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 4698435cb2ab15d16d8a8a898a01a9ffbc4f69c2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64639795"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="2351b-102">Visual Basic'de Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="2351b-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="2351b-103">İçinde *koşullu derleme*, belirli bir programda kod bloklarının diğerleri göz ardı edilir ancak seçmeli olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="2351b-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="2351b-104">Örneğin, yazmak isteyebilirsiniz veya aynı programlama görevi farklı yaklaşımlara hızını karşılaştırma ifadeleri hata ayıklama birden çok dil için bir uygulamayı yerelleştirme getirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="2351b-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="2351b-105">Koşullu derleme deyimleri, çalışma zamanında değil derleme zamanında çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2351b-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="2351b-106">İle koşullu olarak derlenmiş kod bloklarını belirtmek `#If...Then...#Else` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="2351b-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="2351b-107">Örneğin, Fransızca ve Almanca dil oluşturmak için aynı uygulama aynı sürümleri kaynak kodu, platforma özgü kod kesimlerinde ekleme `#If...Then` önceden tanımlı sabitler kullanılarak deyimleri `FrenchVersion` ve `GermanVersion`.</span><span class="sxs-lookup"><span data-stu-id="2351b-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="2351b-108">Aşağıdaki örnek, gösterir nasıl:</span><span class="sxs-lookup"><span data-stu-id="2351b-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="2351b-109">Değerini ayarlarsanız `FrenchVersion` koşullu derleme sabiti `True` derleme zamanında Fransızca sürümü için koşullu kod derlenir.</span><span class="sxs-lookup"><span data-stu-id="2351b-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="2351b-110">Değerini ayarlarsanız `GermanVersion` için sabit `True`, derleyici Almanca sürümü kullanır.</span><span class="sxs-lookup"><span data-stu-id="2351b-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="2351b-111">Hiçbiri ayarlanırsa `True`, son kodda `Else` bloğu çalışır.</span><span class="sxs-lookup"><span data-stu-id="2351b-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2351b-112">Otomatik Tamamlama düzenleme kodlarken not işlevi ve kodun geçerli dal parçası değilse, koşullu derleme yönergeleri kullanarak olur.</span><span class="sxs-lookup"><span data-stu-id="2351b-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="2351b-113">Koşullu derleme Sabitleri Bildirme</span><span class="sxs-lookup"><span data-stu-id="2351b-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="2351b-114">Koşullu derleme sabitleri üç yoldan biriyle ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2351b-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="2351b-115">İçinde **Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="2351b-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="2351b-116">Komut satırı derleyicisini kullanarak komut satırında</span><span class="sxs-lookup"><span data-stu-id="2351b-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="2351b-117">Kodunuzda</span><span class="sxs-lookup"><span data-stu-id="2351b-117">In your code</span></span>  
  
 <span data-ttu-id="2351b-118">Koşullu derleme sabitleri, özel bir kapsama sahip ve standart koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="2351b-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="2351b-119">Koşullu derleme sabiti kapsamı ayarlanmış şekilde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2351b-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="2351b-120">Aşağıdaki tabloda her yukarıda açıklanan üç yoldan birini kullanarak bildirilen sabitlerin kapsamı listeler.</span><span class="sxs-lookup"><span data-stu-id="2351b-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="2351b-121">Sabiti nasıl ayarlanır</span><span class="sxs-lookup"><span data-stu-id="2351b-121">How constant is set</span></span>|<span data-ttu-id="2351b-122">Sabit kapsam</span><span class="sxs-lookup"><span data-stu-id="2351b-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="2351b-123">**Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="2351b-123">**Project Designer**</span></span>|<span data-ttu-id="2351b-124">Projedeki tüm dosyalara genel</span><span class="sxs-lookup"><span data-stu-id="2351b-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="2351b-125">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="2351b-125">Command line</span></span>|<span data-ttu-id="2351b-126">Komut satırı derleyiciye tüm dosyalara genel</span><span class="sxs-lookup"><span data-stu-id="2351b-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="2351b-127">`#Const` koddaki bildirimi</span><span class="sxs-lookup"><span data-stu-id="2351b-127">`#Const` statement in code</span></span>|<span data-ttu-id="2351b-128">İçinde bildirildiği dosyanın özel</span><span class="sxs-lookup"><span data-stu-id="2351b-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="2351b-129">Proje Tasarımcısı'nda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2351b-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="2351b-130">-Sabitler, yürütülebilir dosya oluşturma önce kümesinde **Proje Tasarımcısı** içinde sağlanan adımları izleyerek [yönetme proje ve çözüm özelliklerini](/visualstudio/ide/managing-project-and-solution-properties).</span><span class="sxs-lookup"><span data-stu-id="2351b-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="2351b-131">Komut satırında sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2351b-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="2351b-132">-Kullanma **/d** geçme aşağıdaki örnekte olduğu gibi koşullu derleme sabitleri girin:</span><span class="sxs-lookup"><span data-stu-id="2351b-132">-   Use the **/d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="2351b-133">Arasında boşluk gereklidir **/d** anahtar ve ilk sabiti.</span><span class="sxs-lookup"><span data-stu-id="2351b-133">No space is required between the **/d** switch and the first constant.</span></span> <span data-ttu-id="2351b-134">Daha fazla bilgi için [/ define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="2351b-134">For more information, see [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="2351b-135">Komut satırı bildirimleri geçersiz kılma bildirimi girilen **Proje Tasarımcısı**, ancak bunları silme.</span><span class="sxs-lookup"><span data-stu-id="2351b-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="2351b-136">Bağımsız değişkenler kümesinde **Proje Tasarımcısı** sonraki derleme için yürürlükte kalır.</span><span class="sxs-lookup"><span data-stu-id="2351b-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="2351b-137">Sabitler kodda yazarken, hiçbir katı kurallar vardır, yerleştirme için kendi kapsamı içinde bildirildikleri tüm modül olduğundan.</span><span class="sxs-lookup"><span data-stu-id="2351b-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="2351b-138">Kodunuzda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="2351b-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="2351b-139">-Sabitleri bunlar kullanılır modül bildirimi bloğunda yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="2351b-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="2351b-140">Bu, kodunuzu düzenli ve okunması kolay tutmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="2351b-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="2351b-141">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="2351b-141">Related Topics</span></span>  
  
|<span data-ttu-id="2351b-142">Başlık</span><span class="sxs-lookup"><span data-stu-id="2351b-142">Title</span></span>|<span data-ttu-id="2351b-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2351b-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="2351b-144">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="2351b-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="2351b-145">Kodunuzu okunması ve düzenlenmesi daha kolay yapmak için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2351b-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="2351b-146">Başvuru</span><span class="sxs-lookup"><span data-stu-id="2351b-146">Reference</span></span>  
 [<span data-ttu-id="2351b-147">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="2351b-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="2351b-148">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="2351b-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="2351b-149">/ define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2351b-149">/define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
