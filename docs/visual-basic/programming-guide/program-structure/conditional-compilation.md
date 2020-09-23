---
title: Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e59296882edc018259816c73b6ae861b3b296783
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098975"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="a72f3-102">Visual Basic'de Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="a72f3-102">Conditional Compilation in Visual Basic</span></span>

<span data-ttu-id="a72f3-103">*Koşullu derlemede*, bir programdaki belirli kod blokları, diğerleri gözardı edilirken seçime bağlı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="a72f3-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="a72f3-104">Örneğin, farklı yaklaşımların hızını aynı programlama göreviyle karşılaştıran hata ayıklama deyimleri yazmak veya bir uygulamayı birden çok dil için yerelleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a72f3-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="a72f3-105">Koşullu derleme deyimleri, çalışma zamanında değil, derleme zamanı sırasında çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a72f3-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="a72f3-106">Kod bloklarını yönergeyle koşullu olarak derlenebilecek şekilde belirtebilirsiniz `#If...Then...#Else` .</span><span class="sxs-lookup"><span data-stu-id="a72f3-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="a72f3-107">Örneğin, aynı kaynak koddan aynı uygulamanın Fransızca ve Almanca dil sürümlerini oluşturmak için, `#If...Then` önceden tanımlanmış sabitleri ve kullanarak deyimlerde platforma özel kod kesimleri eklersiniz `FrenchVersion` `GermanVersion` .</span><span class="sxs-lookup"><span data-stu-id="a72f3-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="a72f3-108">Aşağıdaki örnek, aşağıdakilerin nasıl yapıldığını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="a72f3-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="a72f3-109">`FrenchVersion`Koşullu derleme sabitinin değerini `True` derleme zamanında olarak ayarlarsanız, Fransızca sürümü için koşullu kod derlenir.</span><span class="sxs-lookup"><span data-stu-id="a72f3-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="a72f3-110">`GermanVersion`Sabitin değerini olarak ayarlarsanız `True` , derleyici Almanca sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="a72f3-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="a72f3-111">Hiçbiri olarak ayarlanmazsa `True` , son `Else` bloktaki kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="a72f3-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a72f3-112">Kod düzenlenirken otomatik tamamlama çalışmaz ve kod geçerli dalın bir parçası değilse koşullu derleme yönergeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a72f3-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="a72f3-113">Koşullu derleme sabitleri bildirme</span><span class="sxs-lookup"><span data-stu-id="a72f3-113">Declaring Conditional Compilation Constants</span></span>  

 <span data-ttu-id="a72f3-114">Koşullu derleme sabitlerini üç şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a72f3-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="a72f3-115">**Proje tasarımcısında**</span><span class="sxs-lookup"><span data-stu-id="a72f3-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="a72f3-116">Komut satırı derleyicisini kullanırken komut satırında</span><span class="sxs-lookup"><span data-stu-id="a72f3-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="a72f3-117">Kodunuzda</span><span class="sxs-lookup"><span data-stu-id="a72f3-117">In your code</span></span>  
  
 <span data-ttu-id="a72f3-118">Koşullu derleme sabitleri özel bir kapsama sahiptir ve standart koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="a72f3-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="a72f3-119">Koşullu derleme sabitinin kapsamı, ayarlandığı yönteme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a72f3-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="a72f3-120">Aşağıdaki tabloda, yukarıda bahsedilen üç yol kullanılarak bildirilen sabitlerin kapsamı listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="a72f3-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="a72f3-121">Sabit nasıl ayarlanır</span><span class="sxs-lookup"><span data-stu-id="a72f3-121">How constant is set</span></span>|<span data-ttu-id="a72f3-122">Sabit kapsamı</span><span class="sxs-lookup"><span data-stu-id="a72f3-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="a72f3-123">**Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="a72f3-123">**Project Designer**</span></span>|<span data-ttu-id="a72f3-124">Projedeki tüm dosyalar için ortak</span><span class="sxs-lookup"><span data-stu-id="a72f3-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="a72f3-125">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="a72f3-125">Command line</span></span>|<span data-ttu-id="a72f3-126">Komut satırı derleyicisine geçirilen tüm dosyalar için ortak</span><span class="sxs-lookup"><span data-stu-id="a72f3-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="a72f3-127">`#Const` koddaki ifade</span><span class="sxs-lookup"><span data-stu-id="a72f3-127">`#Const` statement in code</span></span>|<span data-ttu-id="a72f3-128">Özel olarak bildirildiği dosya</span><span class="sxs-lookup"><span data-stu-id="a72f3-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="a72f3-129">Proje tasarımcısında sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a72f3-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="a72f3-130">-Yürütülebilir dosyanızı oluşturmadan önce, [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)bölümünde belirtilen adımları Izleyerek **Proje tasarımcısında** sabitler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a72f3-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="a72f3-131">Sabitleri komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a72f3-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="a72f3-132">-Aşağıdaki örnekte gösterildiği gibi, koşullu derleme sabitleri girmek için **-d** anahtarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="a72f3-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="a72f3-133">**-D** anahtarı ve ilk sabit arasında boşluk gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a72f3-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="a72f3-134">Daha fazla bilgi için bkz. [-tanımlama (Visual Basic)](../../reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="a72f3-134">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="a72f3-135">Komut satırı bildirimleri **Proje tasarımcısında**girilen bildirimleri geçersiz kılar, ancak onları silmez.</span><span class="sxs-lookup"><span data-stu-id="a72f3-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="a72f3-136">**Proje tasarımcısında** ayarlanan bağımsız değişkenler sonraki derlemeler için geçerli olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="a72f3-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="a72f3-137">Koda sabitler yazarken, kendi kapsamları bildirildiği modülün tamamı olduğundan, kendi yerleşimine göre kesin bir kural yoktur.</span><span class="sxs-lookup"><span data-stu-id="a72f3-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="a72f3-138">Kodunuzda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="a72f3-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="a72f3-139">-Sabitleri, kullanıldıkları modülün bildirim bloğuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="a72f3-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="a72f3-140">Bu, kodunuzun düzenlenmesine ve okunmasını daha kolay tutmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a72f3-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="a72f3-141">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="a72f3-141">Related Topics</span></span>  
  
|<span data-ttu-id="a72f3-142">Başlık</span><span class="sxs-lookup"><span data-stu-id="a72f3-142">Title</span></span>|<span data-ttu-id="a72f3-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a72f3-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="a72f3-144">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="a72f3-144">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="a72f3-145">Kodunuzun okunmasını ve korunmasını kolaylaştırmak için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a72f3-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="a72f3-146">Başvuru</span><span class="sxs-lookup"><span data-stu-id="a72f3-146">Reference</span></span>  

 [<span data-ttu-id="a72f3-147">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="a72f3-147">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="a72f3-148">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="a72f3-148">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="a72f3-149">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a72f3-149">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
