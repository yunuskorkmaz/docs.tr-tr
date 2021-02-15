---
description: 'Daha fazla bilgi edinin: Visual Basic koşullu derleme'
title: Koşullu Derleme
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: e9cb8a5af4dfbf2ffadef8edd8f6583614188391
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476143"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="7436b-103">Visual Basic'de Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="7436b-103">Conditional Compilation in Visual Basic</span></span>

<span data-ttu-id="7436b-104">*Koşullu derlemede*, bir programdaki belirli kod blokları, diğerleri gözardı edilirken seçime bağlı olarak derlenir.</span><span class="sxs-lookup"><span data-stu-id="7436b-104">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="7436b-105">Örneğin, farklı yaklaşımların hızını aynı programlama göreviyle karşılaştıran hata ayıklama deyimleri yazmak veya bir uygulamayı birden çok dil için yerelleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7436b-105">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="7436b-106">Koşullu derleme deyimleri, çalışma zamanında değil, derleme zamanı sırasında çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7436b-106">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="7436b-107">Kod bloklarını yönergeyle koşullu olarak derlenebilecek şekilde belirtebilirsiniz `#If...Then...#Else` .</span><span class="sxs-lookup"><span data-stu-id="7436b-107">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="7436b-108">Örneğin, aynı kaynak koddan aynı uygulamanın Fransızca ve Almanca dil sürümlerini oluşturmak için, `#If...Then` önceden tanımlanmış sabitleri ve kullanarak deyimlerde platforma özel kod kesimleri eklersiniz `FrenchVersion` `GermanVersion` .</span><span class="sxs-lookup"><span data-stu-id="7436b-108">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="7436b-109">Aşağıdaki örnek, aşağıdakilerin nasıl yapıldığını göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="7436b-109">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="7436b-110">`FrenchVersion`Koşullu derleme sabitinin değerini `True` derleme zamanında olarak ayarlarsanız, Fransızca sürümü için koşullu kod derlenir.</span><span class="sxs-lookup"><span data-stu-id="7436b-110">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="7436b-111">`GermanVersion`Sabitin değerini olarak ayarlarsanız `True` , derleyici Almanca sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7436b-111">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="7436b-112">Hiçbiri olarak ayarlanmazsa `True` , son `Else` bloktaki kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="7436b-112">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7436b-113">Kod düzenlenirken otomatik tamamlama çalışmaz ve kod geçerli dalın bir parçası değilse koşullu derleme yönergeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7436b-113">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="7436b-114">Koşullu derleme sabitleri bildirme</span><span class="sxs-lookup"><span data-stu-id="7436b-114">Declaring Conditional Compilation Constants</span></span>  

 <span data-ttu-id="7436b-115">Koşullu derleme sabitlerini üç şekilde ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7436b-115">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="7436b-116">**Proje tasarımcısında**</span><span class="sxs-lookup"><span data-stu-id="7436b-116">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="7436b-117">Komut satırı derleyicisini kullanırken komut satırında</span><span class="sxs-lookup"><span data-stu-id="7436b-117">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="7436b-118">Kodunuzda</span><span class="sxs-lookup"><span data-stu-id="7436b-118">In your code</span></span>  
  
 <span data-ttu-id="7436b-119">Koşullu derleme sabitleri özel bir kapsama sahiptir ve standart koddan erişilemez.</span><span class="sxs-lookup"><span data-stu-id="7436b-119">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="7436b-120">Koşullu derleme sabitinin kapsamı, ayarlandığı yönteme bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7436b-120">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="7436b-121">Aşağıdaki tabloda, yukarıda bahsedilen üç yol kullanılarak bildirilen sabitlerin kapsamı listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="7436b-121">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="7436b-122">Sabit nasıl ayarlanır</span><span class="sxs-lookup"><span data-stu-id="7436b-122">How constant is set</span></span>|<span data-ttu-id="7436b-123">Sabit kapsamı</span><span class="sxs-lookup"><span data-stu-id="7436b-123">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="7436b-124">**Proje Tasarımcısı**</span><span class="sxs-lookup"><span data-stu-id="7436b-124">**Project Designer**</span></span>|<span data-ttu-id="7436b-125">Projedeki tüm dosyalar için ortak</span><span class="sxs-lookup"><span data-stu-id="7436b-125">Public to all files in the project</span></span>|  
|<span data-ttu-id="7436b-126">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="7436b-126">Command line</span></span>|<span data-ttu-id="7436b-127">Komut satırı derleyicisine geçirilen tüm dosyalar için ortak</span><span class="sxs-lookup"><span data-stu-id="7436b-127">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="7436b-128">`#Const` koddaki ifade</span><span class="sxs-lookup"><span data-stu-id="7436b-128">`#Const` statement in code</span></span>|<span data-ttu-id="7436b-129">Özel olarak bildirildiği dosya</span><span class="sxs-lookup"><span data-stu-id="7436b-129">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="7436b-130">Proje tasarımcısında sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7436b-130">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="7436b-131">-Yürütülebilir dosyanızı oluşturmadan önce, [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)bölümünde belirtilen adımları Izleyerek **Proje tasarımcısında** sabitler ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7436b-131">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="7436b-132">Sabitleri komut satırında ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7436b-132">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="7436b-133">-Aşağıdaki örnekte gösterildiği gibi, koşullu derleme sabitleri girmek için **-d** anahtarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="7436b-133">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="7436b-134">**-D** anahtarı ve ilk sabit arasında boşluk gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7436b-134">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="7436b-135">Daha fazla bilgi için bkz. [-tanımlama (Visual Basic)](../../reference/command-line-compiler/define.md).</span><span class="sxs-lookup"><span data-stu-id="7436b-135">For more information, see [-define (Visual Basic)](../../reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="7436b-136">Komut satırı bildirimleri **Proje tasarımcısında** girilen bildirimleri geçersiz kılar, ancak onları silmez.</span><span class="sxs-lookup"><span data-stu-id="7436b-136">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="7436b-137">**Proje tasarımcısında** ayarlanan bağımsız değişkenler sonraki derlemeler için geçerli olmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="7436b-137">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="7436b-138">Koda sabitler yazarken, kendi kapsamları bildirildiği modülün tamamı olduğundan, kendi yerleşimine göre kesin bir kural yoktur.</span><span class="sxs-lookup"><span data-stu-id="7436b-138">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="7436b-139">Kodunuzda sabitleri ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7436b-139">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="7436b-140">-Sabitleri, kullanıldıkları modülün bildirim bloğuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7436b-140">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="7436b-141">Bu, kodunuzun düzenlenmesine ve okunmasını daha kolay tutmaya yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7436b-141">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="7436b-142">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="7436b-142">Related Topics</span></span>  
  
|<span data-ttu-id="7436b-143">Başlık</span><span class="sxs-lookup"><span data-stu-id="7436b-143">Title</span></span>|<span data-ttu-id="7436b-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7436b-144">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="7436b-145">Program yapısı ve kod kuralları</span><span class="sxs-lookup"><span data-stu-id="7436b-145">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)|<span data-ttu-id="7436b-146">Kodunuzun okunmasını ve korunmasını kolaylaştırmak için öneriler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7436b-146">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="7436b-147">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7436b-147">Reference</span></span>  

 [<span data-ttu-id="7436b-148">#Const Yönergesi</span><span class="sxs-lookup"><span data-stu-id="7436b-148">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="7436b-149">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="7436b-149">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="7436b-150">-tanımla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7436b-150">-define (Visual Basic)</span></span>](../../reference/command-line-compiler/define.md)
