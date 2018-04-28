---
title: Bir Visual Basic Programının Yapısı
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5def0de1e22af39eb16489a2d4d27bdbd1853f2b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="9f6a4-102">Bir Visual Basic Programının Yapısı</span><span class="sxs-lookup"><span data-stu-id="9f6a4-102">Structure of a Visual Basic Program</span></span>
<span data-ttu-id="9f6a4-103">Visual Basic programı standart yapı taşları oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-103">A Visual Basic program is built up from standard building blocks.</span></span> <span data-ttu-id="9f6a4-104">A *çözüm* bir veya daha fazla projeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="9f6a4-105">A *proje* bir veya daha fazla derlemeleri sırayla içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="9f6a4-106">Her *derleme* bir veya daha fazla kaynak dosyalarından derlenir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="9f6a4-107">A *kaynak dosyası* tanımı ve uygulama sınıflar, yapılar, modüller ve sonuç olarak tüm kodunuzu içeren arabirimleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="9f6a4-108">Visual Basic programı bu yapı taşları hakkında daha fazla bilgi için bkz: [çözümler ve projeler](/visualstudio/ide/solutions-and-projects-in-visual-studio) ve [derlemeler ve genel derleme önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-108">For more information about these building blocks of a Visual Basic program, see [Solutions and Projects](/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="9f6a4-109">Dosya düzeyinde programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-109">File-Level Programming Elements</span></span>  
 <span data-ttu-id="9f6a4-110">Bir proje veya dosya başlatın ve Kod Düzenleyicisi'ni açın, biraz kod zaten yerinde ve doğru sırada bakın.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="9f6a4-111">Yazdığınız herhangi bir kod aşağıdaki sırayı izlemelisiniz:</span><span class="sxs-lookup"><span data-stu-id="9f6a4-111">Any code that you write should follow the following sequence:</span></span>  
  
1.  <span data-ttu-id="9f6a4-112">`Option` Deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-112">`Option` statements</span></span>  
  
2.  <span data-ttu-id="9f6a4-113">`Imports` Deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-113">`Imports` statements</span></span>  
  
3.  <span data-ttu-id="9f6a4-114">`Namespace` ifadeler ve ad alanı düzeyinde öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="9f6a4-115">Farklı bir sırada deyimleri girerseniz, derleme hataları neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="9f6a4-116">Bir program koşullu derleme deyimleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="9f6a4-117">Bunlar önceki dizisi deyimleri arasında kaynak dosyasında intersperse.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="9f6a4-118">Seçenek deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-118">Option Statements</span></span>  
 <span data-ttu-id="9f6a4-119">`Option` deyimleri izleyen kod, sözdizimi ve mantık hataları önlemeye yardımcı olmak için başından başlayarak kurallar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="9f6a4-120">[Option Explicit deyimi](../../../visual-basic/language-reference/statements/option-explicit-statement.md) tüm değişkenleri bildirilir ve doğru yazıldığından emin, hata ayıklama süresini azaltır sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-120">The [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="9f6a4-121">[Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md) farklı veri türleri değişkenleri arasında çalışırken oluşabilecek mantık hataları ve veri kaybını en aza indirmek için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-121">The [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="9f6a4-122">[Option Compare deyimi](../../../visual-basic/language-reference/statements/option-compare-statement.md) şekilde dizeleri birbirlerine, üzerinde bağlı karşılaştırılır belirtir kendi `Binary` veya `Text` değerleri.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-122">The [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="9f6a4-123">İçeri aktarmalar deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-123">Imports Statements</span></span>  
 <span data-ttu-id="9f6a4-124">Dahil edebileceğiniz bir [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dışında proje tanımlanan adları almak için.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-124">You can include an [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="9f6a4-125">Bir `Imports` deyimi sınıfları ve bunları uygun gerek kalmadan içeri aktarılan ad alanı içinde tanımlanan diğer türleri başvurmak kodunuzu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="9f6a4-126">Birçok kullanabileceğiniz `Imports` deyimleri uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="9f6a4-127">Daha fazla bilgi için bkz: [References ve Imports deyimi](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-127">For more information, see [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="9f6a4-128">Namespace deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-128">Namespace Statements</span></span>  
 <span data-ttu-id="9f6a4-129">Düzenlemek ve programlama öğelerinizi gruplandırma ve erişim kolaylığı için Sınıflandır ad alanları yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="9f6a4-130">Kullandığınız [Namespace deyimi](../../../visual-basic/language-reference/statements/namespace-statement.md) aşağıdaki deyimleri belirli bir ad alanı içinde sınıflandırmak için.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-130">You use the [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="9f6a4-131">Daha fazla bilgi için bkz: [Visual Basic'de ad alanları](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-131">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="9f6a4-132">Koşullu derleme deyimleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-132">Conditional Compilation Statements</span></span>  
 <span data-ttu-id="9f6a4-133">Koşullu derleme deyimleri neredeyse her yerden kaynak dosyanızda yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="9f6a4-134">Bunlar, dahil edilecek veya belirli koşullara bağlı olarak derleme zamanında hariç için kodunuzu bölümlerini neden.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="9f6a4-135">Koşullu kod modu yalnızca hata ayıklama çalıştığından, ayrıca bunları uygulamanızın, hata ayıklama için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="9f6a4-136">Daha fazla bilgi için bkz: [koşullu derleme](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-136">For more information, see [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="9f6a4-137">Namespace düzeyi programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-137">Namespace-Level Programming Elements</span></span>  
 <span data-ttu-id="9f6a4-138">Sınıflar, yapılar ve modülleri kaynak dosyanızdaki tüm kod içerir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="9f6a4-139">Bunlar *ad alanı düzeyinde* bir ad alanı içinde veya kaynak dosya düzeyinde görünebilir öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="9f6a4-140">Bunlar, diğer programlama öğeleri bildirimlerini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="9f6a4-141">Öğe imzaları tanımlamak, ancak hiçbir uygulama sunmak, arabirimleri, aynı zamanda Modül düzeyinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="9f6a4-142">Modül düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:</span><span class="sxs-lookup"><span data-stu-id="9f6a4-142">For more information on the module-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="9f6a4-143">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-143">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="9f6a4-144">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-144">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [<span data-ttu-id="9f6a4-145">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-145">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [<span data-ttu-id="9f6a4-146">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-146">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="9f6a4-147">Veri ad alanı düzeyinde sabit listeleri ve temsilciler öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="9f6a4-148">Modül düzeyi programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-148">Module-Level Programming Elements</span></span>  
 <span data-ttu-id="9f6a4-149">Yordamlar, işleçleri, özellikleri ve olayları yürütülebilir kod (çalışma zamanında eylemleri gerçekleştirme deyimleri) tutabileceği yalnızca programlama öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="9f6a4-150">Bunlar *modül düzeyi* programınızın öğeleri.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="9f6a4-151">Yordam düzeyi öğeler hakkında daha fazla bilgi için aşağıdakilere bakın:</span><span class="sxs-lookup"><span data-stu-id="9f6a4-151">For more information on the procedure-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="9f6a4-152">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-152">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="9f6a4-153">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-153">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="9f6a4-154">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-154">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="9f6a4-155">Operator Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-155">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [<span data-ttu-id="9f6a4-156">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-156">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="9f6a4-157">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="9f6a4-157">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="9f6a4-158">Veri modülü düzeyinde değişkenlerinin, sabitleri, numaralandırmaları ve temsilciler öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="9f6a4-159">Yordam düzeyi programlama öğeleri</span><span class="sxs-lookup"><span data-stu-id="9f6a4-159">Procedure-Level Programming Elements</span></span>  
 <span data-ttu-id="9f6a4-160">Çoğu içeriğinin *yordam düzeyi* , programın çalışma zamanı kodu oluşturan executable deyimleri öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="9f6a4-161">Tüm yürütülebilir kod bazı yordamda olmalıdır (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="9f6a4-162">Daha fazla bilgi için bkz: [deyimleri](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-162">For more information, see [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
 <span data-ttu-id="9f6a4-163">Veri öğeleri yordamı düzeyinde, yerel değişkenleri ve sabitleri sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="9f6a4-164">Main yordamı</span><span class="sxs-lookup"><span data-stu-id="9f6a4-164">The Main Procedure</span></span>  
 <span data-ttu-id="9f6a4-165">`Main` Uygulamanızı yüklendiğinde çalıştırmak için ilk kod bir yordamdır.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="9f6a4-166">`Main` Uygulamanız için genel denetim ve başlangıç noktası olarak görevi görür.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="9f6a4-167">Dört çeşitleri vardır `Main`:</span><span class="sxs-lookup"><span data-stu-id="9f6a4-167">There are four varieties of `Main`:</span></span>  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="9f6a4-168">Bu yordam, en yaygın çeşitli olduğu `Sub Main()`.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="9f6a4-169">Daha fazla bilgi için bkz: [Visual Basic'de ana yordam](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="9f6a4-169">For more information, see [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6a4-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f6a4-170">See Also</span></span>  
 [<span data-ttu-id="9f6a4-171">Visual Basic'de ana yordam</span><span class="sxs-lookup"><span data-stu-id="9f6a4-171">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 [<span data-ttu-id="9f6a4-172">Visual Basic adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="9f6a4-172">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="9f6a4-173">Visual Basic sınırlamaları</span><span class="sxs-lookup"><span data-stu-id="9f6a4-173">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)
