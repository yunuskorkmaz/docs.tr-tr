---
title: Visual Basic'de Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 0767b2054697735c3f5190b6e30a2c80ea5288bc
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775710"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="ff24a-102">Visual Basic'de Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="ff24a-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="ff24a-103">*Koşullu derlemede*, bir programdaki belirli kod blokları, diğerleri gözardı edilirken seçime bağlı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="ff24a-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="ff24a-104">Örneğin, farklı yaklaşımların hızını aynı programlama göreviyle karşılaştıran hata ayıklama deyimleri yazmak veya bir uygulamayı birden çok dil için yerelleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff24a-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="ff24a-105">Koşullu derleme deyimleri, çalışma zamanında değil, derleme zamanı sırasında çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ff24a-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="ff24a-106">Kod bloklarını `#If...Then...#Else` yönergeyle koşullu olarak derlenebilecek şekilde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff24a-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="ff24a-107">Örneğin, aynı kaynak koddan aynı uygulamanın Fransızca ve Almanca dil sürümlerini oluşturmak için, önceden tanımlanmış sabitleri `FrenchVersion` ve `GermanVersion` kullanarak platforma özgü kod kesimlerini `#If...Then` deyimlerine eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="ff24a-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="ff24a-108">Aşağıdaki örnek, aşağıdakilerin nasıl yapıldığını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="ff24a-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="ff24a-109">@No__t_0 koşullu derleme sabitinin değerini derleme zamanında `True` olarak ayarlarsanız, Fransızca sürümü için koşullu kod derlenir.</span><span class="sxs-lookup"><span data-stu-id="ff24a-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="ff24a-110">@No__t_0 sabitinin değerini `True` olarak ayarlarsanız, derleyici Almanca sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="ff24a-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="ff24a-111">Hiçbiri `True` olarak ayarlanmazsa, son `Else` bloğundaki kod çalışır.</span><span class="sxs-lookup"><span data-stu-id="ff24a-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff24a-112">Kod düzenlenirken otomatik tamamlama çalışmaz ve kod geçerli dalın bir parçası değilse koşullu derleme yönergeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff24a-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="ff24a-113">Koşullu derleme sabitleri bildirme</span><span class="sxs-lookup"><span data-stu-id="ff24a-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="ff24a-114">Koşullu derleme sabitlerini üç şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ff24a-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="ff24a-115">**Proje tasarımcısında**</span><span class="sxs-lookup"><span data-stu-id="ff24a-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="ff24a-116">Komut satırı derleyicisini kullanırken komut satırında</span><span class="sxs-lookup"><span data-stu-id="ff24a-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="ff24a-117">Kodunuzda</span><span class="sxs-lookup"><span data-stu-id="ff24a-117">In your code</span></span>  
  
 <span data-ttu-id="ff24a-118">Koşullu derleme sabitleri özel bir kapsama sahiptir ve standart koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="ff24a-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="ff24a-119">Koşullu derleme sabitinin kapsamı, ayarlandığı yönteme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ff24a-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="ff24a-120">Aşağıdaki tabloda, yukarıda bahsedilen üç yol kullanılarak bildirilen sabitlerin kapsamı listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff24a-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="ff24a-121">Sabit nasıl ayarlanır</span><span class="sxs-lookup"><span data-stu-id="ff24a-121">How constant is set</span></span>|<span data-ttu-id="ff24a-122">Sabit kapsamı</span><span class="sxs-lookup"><span data-stu-id="ff24a-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="ff24a-123">**Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="ff24a-123">**Project Designer**</span></span>|<span data-ttu-id="ff24a-124">Projedeki tüm dosyalar için ortak</span><span class="sxs-lookup"><span data-stu-id="ff24a-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="ff24a-125">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="ff24a-125">Command line</span></span>|<span data-ttu-id="ff24a-126">Komut satırı derleyicisine geçirilen tüm dosyalar için ortak</span><span class="sxs-lookup"><span data-stu-id="ff24a-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="ff24a-127">koddaki `#Const` ifade</span><span class="sxs-lookup"><span data-stu-id="ff24a-127">`#Const` statement in code</span></span>|<span data-ttu-id="ff24a-128">Özel olarak bildirildiği dosya</span><span class="sxs-lookup"><span data-stu-id="ff24a-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="ff24a-129">Proje tasarımcısında sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ff24a-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="ff24a-130">-Yürütülebilir dosyanızı oluşturmadan önce, [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)bölümünde belirtilen adımları Izleyerek **Proje tasarımcısında** sabitler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ff24a-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="ff24a-131">Sabitleri komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ff24a-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="ff24a-132">-Aşağıdaki örnekte gösterildiği gibi, koşullu derleme sabitleri girmek için **-d** anahtarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="ff24a-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="ff24a-133">**-D** anahtarı ve ilk sabit arasında boşluk gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ff24a-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="ff24a-134">Daha fazla bilgi için bkz. [-tanımlama (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="ff24a-134">For more information, see [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="ff24a-135">Komut satırı bildirimleri **Proje tasarımcısında**girilen bildirimleri geçersiz kılar, ancak onları silmez.</span><span class="sxs-lookup"><span data-stu-id="ff24a-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="ff24a-136">**Proje tasarımcısında** ayarlanan bağımsız değişkenler sonraki derlemeler için geçerli olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="ff24a-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="ff24a-137">Koda sabitler yazarken, kendi kapsamları bildirildiği modülün tamamı olduğundan, kendi yerleşimine göre kesin bir kural yoktur.</span><span class="sxs-lookup"><span data-stu-id="ff24a-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="ff24a-138">Kodunuzda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="ff24a-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="ff24a-139">-Sabitleri, kullanıldıkları modülün bildirim bloğuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ff24a-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="ff24a-140">Bu, kodunuzun düzenlenmesine ve okunmasını daha kolay tutmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ff24a-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="ff24a-141">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="ff24a-141">Related Topics</span></span>  
  
|<span data-ttu-id="ff24a-142">Başlık</span><span class="sxs-lookup"><span data-stu-id="ff24a-142">Title</span></span>|<span data-ttu-id="ff24a-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff24a-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="ff24a-144">Program Yapısı ve Kod Kuralları</span><span class="sxs-lookup"><span data-stu-id="ff24a-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="ff24a-145">Kodunuzun okunmasını ve korunmasını kolaylaştırmak için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff24a-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="ff24a-146">Başvuru</span><span class="sxs-lookup"><span data-stu-id="ff24a-146">Reference</span></span>  
 [<span data-ttu-id="ff24a-147">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="ff24a-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="ff24a-148">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="ff24a-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="ff24a-149">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ff24a-149">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
