---
title: 'Öğretici: İlk Çözümleyicisi ve kod düzeltmenizi yazın'
description: Bu öğretici bir çözümleyici oluşturmak için adım adım yönergeler sağlar ve kod düzeltmesi .NET derleyici SDK'sı (Roslyn API'leri) kullanarak.
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: 665dac9d36933c35be19cc826b8b4dc614c38ed2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677193"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="caaec-103">Öğretici: İlk Çözümleyicisi ve kod düzeltmenizi yazın</span><span class="sxs-lookup"><span data-stu-id="caaec-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="caaec-104">.NET derleyici Platformu SDK'sı, özel uyarıları, hedef C# veya Visual Basic kodunu oluşturmak için ihtiyacınız olan araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="caaec-105">**Çözümleyicisi** , kural ihlalleri algılar kodunu içerir.</span><span class="sxs-lookup"><span data-stu-id="caaec-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="caaec-106">**Kod düzeltme** ihlali düzelten kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="caaec-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="caaec-107">Uygulamanız kuralları kodlama stili için adlandırma kuralları ve daha fazla bilgi için kod yapısını her şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="caaec-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="caaec-108">.NET derleyici platformu, geliştiricilerin kod yazma ve tüm Visual Studio kullanıcı Arabirimi özellikleri kodu düzeltmek için analiz çalıştırmak için framework sunar: dalgalı çizgiler Visual Studio hata oluşturma "ampule" listesinde doldurma Düzenleyicisi'nde gösteriliyor öneriler ve önerilen düzeltmeleri zengin önizlemesi gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="caaec-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="caaec-109">Bu öğreticide, oluşturma hakkında bilgi edineceksiniz bir **Çözümleyicisi** ve yayarsa **kod düzeltme** Roslyn API'leri kullanma.</span><span class="sxs-lookup"><span data-stu-id="caaec-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="caaec-110">Bir çözümleyici, kaynak kod analizini gerçekleştirin ve kullanıcıya bir sorun bildirmek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="caaec-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="caaec-111">İsteğe bağlı olarak, bir çözümleyici, kullanıcının kaynak kodu için bir değişiklik gösteren bir kod düzeltme de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="caaec-112">Bu öğreticide kullanılarak bildirilebilir yerel değişken bildirimlerini bulan bir çözümleyici oluşturur `const` değiştiricisi ancak değildir.</span><span class="sxs-lookup"><span data-stu-id="caaec-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="caaec-113">Eşlik eden kod düzeltmesi eklemek için bu bildirimler değiştirir `const` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="caaec-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="caaec-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="caaec-114">Prerequisites</span></span>

* [<span data-ttu-id="caaec-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="caaec-115">Visual Studio 2017</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="caaec-116">Yüklemeniz gerekir **.NET derleyici Platformu SDK'sı**:</span><span class="sxs-lookup"><span data-stu-id="caaec-116">You'll need to install the **.NET Compiler Platform SDK**:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="caaec-117">Birkaç adım vardır, çözümleyici doğrulamak ve oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="caaec-117">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="caaec-118">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caaec-118">Create the solution.</span></span>
1. <span data-ttu-id="caaec-119">Çözümleyici bir ad ve açıklama kaydedin.</span><span class="sxs-lookup"><span data-stu-id="caaec-119">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="caaec-120">Rapor Çözümleyicisi uyarıları ve öneriler.</span><span class="sxs-lookup"><span data-stu-id="caaec-120">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="caaec-121">Önerileri kabul etmek için kod düzeltmeyi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="caaec-121">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="caaec-122">Analiz birim testleri ile geliştirin.</span><span class="sxs-lookup"><span data-stu-id="caaec-122">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="caaec-123">Çözümleyici şablonu keşfedin</span><span class="sxs-lookup"><span data-stu-id="caaec-123">Explore the analyzer template</span></span>

<span data-ttu-id="caaec-124">Çözümleyici yerel sabitleri dönüştürülebilir yerel değişken bildirimlerini kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="caaec-124">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="caaec-125">Örneğin, aşağıdaki kodu düşünün:</span><span class="sxs-lookup"><span data-stu-id="caaec-125">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="caaec-126">Yukarıdaki kodda `x` sabit bir değer atanır ve hiçbir zaman değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="caaec-126">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="caaec-127">Kullanılarak bildirilebilir `const` değiştiricisi:</span><span class="sxs-lookup"><span data-stu-id="caaec-127">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="caaec-128">Bir değişken sabit yapılan olup olmadığını belirlemek için analiz gerektiren söz dizimi analizi, sabit Başlatıcı ifadesinin analizini ve değişkeni için hiçbir zaman yazıldığından emin olmak için veri akışı analizini yapar.</span><span class="sxs-lookup"><span data-stu-id="caaec-128">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="caaec-129">.NET derleyici platformu bu analiz gerçekleştirmeyi kolaylaştıran API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-129">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="caaec-130">Yeni C# oluşturmak için ilk adımıdır **Çözümleyicisi kod düzeltme** proje.</span><span class="sxs-lookup"><span data-stu-id="caaec-130">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

* <span data-ttu-id="caaec-131">Visual Studio'da **Dosya > Yeni > Proje...**  yeni proje iletişim kutusu görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="caaec-131">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
* <span data-ttu-id="caaec-132">Altında **Visual C# > genişletilebilirlik**, seçin **kod düzeltme (.NET Standard) Çözümleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="caaec-132">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
* <span data-ttu-id="caaec-133">Projenizi adlandırın "**MakeConst**" ve Tamam'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="caaec-133">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="caaec-134">Üç projenin kod düzeltme şablonuyla Çözümleyicisi oluşturur: Çözümleyicisi ve kod düzeltmesi içerir, ikinci bir birim test projesi ve üçüncü VSIX projesi.</span><span class="sxs-lookup"><span data-stu-id="caaec-134">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="caaec-135">Varsayılan başlangıç projesi VSIX projesinde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="caaec-135">The default startup project is the VSIX project.</span></span> <span data-ttu-id="caaec-136">Tuşuna **F5** VSIX projesi başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="caaec-136">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="caaec-137">Bu, yeni Çözümleyicisi yükledi Visual Studio'nun ikinci bir örneğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="caaec-137">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="caaec-138">Çözümleyicisi'ni çalıştırdığınızda, Visual Studio'nun ikinci bir kopya başlatın.</span><span class="sxs-lookup"><span data-stu-id="caaec-138">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="caaec-139">Bu ikinci kopyanın farklı bir kayıt defteri kovanı ayarlarını depolamak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="caaec-139">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="caaec-140">Visual Studio iki kopyasını visual ayarlarında ayırt etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-140">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="caaec-141">Visual Studio'nun Deneysel çalıştırma için farklı bir tema seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-141">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="caaec-142">Ayrıca, ayarları veya oturum açma Visual Studio Deneysel kullanarak hesabı çalıştırma Visual Studio için Dolaşımda yok.</span><span class="sxs-lookup"><span data-stu-id="caaec-142">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="caaec-143">Ayarları farklı saklar.</span><span class="sxs-lookup"><span data-stu-id="caaec-143">That keeps the settings different.</span></span>

<span data-ttu-id="caaec-144">Başlattığınız ikinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi (.NET Core veya .NET Framework projesi olacaktır işler--kaynak düzeyinde Çözümleyicileri işler.) oluşturma Dalgalı çizgi belirteciyle üzerine gelin ve bir çözümleyici tarafından sağlanan uyarı metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="caaec-144">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="caaec-145">Şablon, aşağıdaki resimde gösterildiği gibi her tür bildiriminde tür adı küçük harf, burada içeren bir uyarı bildirir bir çözümleyici oluşturur:</span><span class="sxs-lookup"><span data-stu-id="caaec-145">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Uyarı raporlama Çözümleyicisi](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="caaec-147">Şablon, tüm büyük küçük harf karakter içeren herhangi bir tür adı değiştiren bir kod düzeltme de sağlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-147">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="caaec-148">Önerilen değişiklikleri görmek için uyarı ile görüntülenen ampul tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-148">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="caaec-149">Önerilen değişikliklerin güncelleştirmeler tür adı ve bu tür iş Çözümdeki tüm başvurular kabul etme.</span><span class="sxs-lookup"><span data-stu-id="caaec-149">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="caaec-150">Uygulamada ilk Çözümleyicisi gördüğünüze göre ikinci Visual Studio örneğini kapatın ve Çözümleyicisi projenize döndürür.</span><span class="sxs-lookup"><span data-stu-id="caaec-150">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="caaec-151">Visual Studio ikinci bir kopyası başlayıp her değişiklik Çözümleyicisi'nde test etmek için yeni kod gerekmez.</span><span class="sxs-lookup"><span data-stu-id="caaec-151">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="caaec-152">Şablon birim testi projesi ayrıca sizin için oluşturur.</span><span class="sxs-lookup"><span data-stu-id="caaec-152">The template also creates a unit test project for you.</span></span> <span data-ttu-id="caaec-153">Bu proje, iki testleri içerir.</span><span class="sxs-lookup"><span data-stu-id="caaec-153">That project contains two tests.</span></span> <span data-ttu-id="caaec-154">`TestMethod1` Tipik bir tanılama tetiklemeden kod analiz eden bir testi biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="caaec-154">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="caaec-155">`TestMethod2` bir tanılama tetikler ve ardından bir önerilen kod düzeltme uygular bir test biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="caaec-155">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="caaec-156">Çözümleyicisi ve kod düzeltmesi oluştururken farklı kod yapıları iş doğrulamak için testler yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="caaec-156">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="caaec-157">Çözümleyici için birim testleri, Visual Studio ile etkileşimli olarak sınama daha çok daha hızlı.</span><span class="sxs-lookup"><span data-stu-id="caaec-157">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="caaec-158">Hangi kod yapıları gerekir ve sizin Çözümleyicisi tetikleyin olmamalıdır bildiğinizde Çözümleyicisi birim testleri harika bir araçlardır.</span><span class="sxs-lookup"><span data-stu-id="caaec-158">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="caaec-159">Visual Studio'nun başka bir kopya, Çözümleyicisinde yüklenirken Keşfetmenin yanı sıra, hakkında henüz düşündüğünüz değil yapıları için harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="caaec-159">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="caaec-160">Çözümleyici kayıtları oluşturma</span><span class="sxs-lookup"><span data-stu-id="caaec-160">Create analyzer registrations</span></span>

<span data-ttu-id="caaec-161">İlk şablon oluşturur `DiagnosticAnalyzer` içinde sınıf **MakeConstAnalyzer.cs** dosya.</span><span class="sxs-lookup"><span data-stu-id="caaec-161">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="caaec-162">Bu ilk Çözümleyicisi her analyzer'ın iki önemli özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="caaec-162">This initial analyzer shows two important properties of every analyzer.</span></span>

* <span data-ttu-id="caaec-163">Her bir Tanılama Çözümleyicisi sağlamalısınız bir `[DiagnosticAnalyzer]` yerler üzerinde çalışır dil açıklayan öznitelik.</span><span class="sxs-lookup"><span data-stu-id="caaec-163">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
* <span data-ttu-id="caaec-164">Her bir Tanılama Çözümleyicisi öğesinden türetilmelidir <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="caaec-164">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="caaec-165">Şablon ayrıca tüm Çözümleyicisi parçası olan temel özelliklerini gösterir:</span><span class="sxs-lookup"><span data-stu-id="caaec-165">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="caaec-166">Eylemler kaydedin.</span><span class="sxs-lookup"><span data-stu-id="caaec-166">Register actions.</span></span> <span data-ttu-id="caaec-167">Eylemleri ihlalleri kod inceleme, çözümleyici tetiklemesi gereken kod değişikliği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="caaec-167">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="caaec-168">Visual Studio kayıtlı eylem eşleşen kod düzenleme algıladığında, kayıtlı Çözümleyicisi'nin yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="caaec-168">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="caaec-169">Tanılama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caaec-169">Create diagnostics.</span></span> <span data-ttu-id="caaec-170">Çözümleyici ihlalinin algıladığında, kullanıcıya ihlalin bildirmek için Visual Studio kullanan bir tanılama nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="caaec-170">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="caaec-171">İçinde geçersiz kılma eylemleri Kaydet <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-171">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="caaec-172">Bu öğreticide, ziyaret ettiğiniz **söz dizimi düğümleri** yerel bildirimler için arama ve sabit değerleri bu olan bakın.</span><span class="sxs-lookup"><span data-stu-id="caaec-172">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="caaec-173">Bir bildirimi sabit ise, çözümleyici oluşturun ve bir tanılama raporu.</span><span class="sxs-lookup"><span data-stu-id="caaec-173">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="caaec-174">Kayıt sabitleri güncelleştirmek için ilk adımıdır ve `Initialize` "Const olun" Çözümleyicisi'ni bu sabiti belirtmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-174">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="caaec-175">Çoğu dize sabitleri dize kaynak dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="caaec-175">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="caaec-176">Bu yöntem daha kolay bir şekilde yerelleştirilmesi izlemelidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-176">You should follow that practice for easier localization.</span></span> <span data-ttu-id="caaec-177">Açık **Resources.resx** dosya **MakeConst** Çözümleyicisi proje.</span><span class="sxs-lookup"><span data-stu-id="caaec-177">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="caaec-178">Bu kaynak düzenleyicisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="caaec-178">This displays the resource editor.</span></span> <span data-ttu-id="caaec-179">Dize kaynakları şu şekilde güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="caaec-179">Update the string resources as follows:</span></span>

* <span data-ttu-id="caaec-180">Değişiklik `AnalyzerTitle` "Değişkeni sabit yapılabilmesi için" için.</span><span class="sxs-lookup"><span data-stu-id="caaec-180">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
* <span data-ttu-id="caaec-181">Değişiklik `AnalyzerMessageFormat` "sabit yapılabilmesi için" için.</span><span class="sxs-lookup"><span data-stu-id="caaec-181">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
* <span data-ttu-id="caaec-182">Değişiklik `AnalyzerDescription` "Sabit yapmak için".</span><span class="sxs-lookup"><span data-stu-id="caaec-182">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="caaec-183">Ayrıca, değişiklik **erişim değiştiricisi** açılan `public`.</span><span class="sxs-lookup"><span data-stu-id="caaec-183">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="caaec-184">Bu, birim testleri bu sabiti kullanmak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="caaec-184">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="caaec-185">İşiniz bittiğinde, kaynak düzenleyicisini şekil gösterir izleyin gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="caaec-185">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Dize kaynaklarını güncelleştir](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="caaec-187">Kalan Çözümleyicisi dosyasında değişikliklerdir.</span><span class="sxs-lookup"><span data-stu-id="caaec-187">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="caaec-188">Açık **MakeConstAnalyzer.cs** Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="caaec-188">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="caaec-189">Kayıtlı eylem söz dizimini temel görevi gören bir simge gerçekleştirildiği birinden değiştirin.</span><span class="sxs-lookup"><span data-stu-id="caaec-189">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="caaec-190">İçinde `MakeConstAnalyzerAnalyzer.Initialize` yöntemi, eylem simgeleri kaydeder satırı bulun:</span><span class="sxs-lookup"><span data-stu-id="caaec-190">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="caaec-191">Bunu, aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="caaec-191">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="caaec-192">Bu değişiklikten sonra silmeniz `AnalyzeSymbol` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-192">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="caaec-193">Bu çözümleyici inceler <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>değil <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> deyimleri.</span><span class="sxs-lookup"><span data-stu-id="caaec-193">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="caaec-194">Dikkat `AnalyzeNode` kırmızı dalgalı çizgiler altındaki sahiptir.</span><span class="sxs-lookup"><span data-stu-id="caaec-194">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="caaec-195">Yeni kod başvurularını eklenen bir `AnalyzeNode` bildirilmeyen yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-195">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="caaec-196">Bu yöntem aşağıdaki kodu kullanarak bildirin:</span><span class="sxs-lookup"><span data-stu-id="caaec-196">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="caaec-197">Değişiklik `Category` "Kullanımı" **MakeConstAnalyzer.cs** aşağıdaki kodda gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="caaec-197">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="caaec-198">Const yerel bildirimleri Bul</span><span class="sxs-lookup"><span data-stu-id="caaec-198">Find local declarations that could be const</span></span>

<span data-ttu-id="caaec-199">Ürününün ilk sürümünü yazmak için zamanı `AnalyzeNode` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-199">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="caaec-200">Olabilecek tek bir yerel bildirim için görünmelidir `const` ancak şu kod gibi:</span><span class="sxs-lookup"><span data-stu-id="caaec-200">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="caaec-201">İlk adım, yerel bildirimleri bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="caaec-201">The first step is to find local declarations.</span></span> <span data-ttu-id="caaec-202">Aşağıdaki kodu ekleyin `AnalyzeNode` içinde **MakeConstAnalyzer.cs**:</span><span class="sxs-lookup"><span data-stu-id="caaec-202">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="caaec-203">Bu tür dönüştürme, çözümleyici değişiklikler yerel bildirimleri ve yalnızca yerel bildirimler için kayıtlı olduğundan her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="caaec-203">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="caaec-204">Başka bir düğüm türü için bir çağrı tetikler, `AnalyzeNode` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-204">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="caaec-205">Ardından, herhangi bir bildirim denetleyin `const` değiştiriciler.</span><span class="sxs-lookup"><span data-stu-id="caaec-205">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="caaec-206">Bulursanız, hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="caaec-206">If you find them, return immediately.</span></span> <span data-ttu-id="caaec-207">Aşağıdaki kod için görünür `const` yerel bildiriminde değiştiriciler:</span><span class="sxs-lookup"><span data-stu-id="caaec-207">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="caaec-208">Son olarak, değişkeni olabilir denetlemek ihtiyacınız `const`.</span><span class="sxs-lookup"><span data-stu-id="caaec-208">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="caaec-209">Başlatıldıktan sonra emin olunmasını hiçbir zaman atandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="caaec-209">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="caaec-210">Anlam analizi kullanarak, yerine getireceğiniz <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span><span class="sxs-lookup"><span data-stu-id="caaec-210">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="caaec-211">Kullandığınız `context` yerel değişken bildiriminde yapılan olup olmadığını belirlemek için bağımsız değişken `const`.</span><span class="sxs-lookup"><span data-stu-id="caaec-211">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="caaec-212">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> tek bir kaynak dosyası tüm anlamsal bilgilerin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="caaec-212">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="caaec-213">Kapsayan makalesinde daha fazla bilgi [anlam modelleri'ne](../work-with-semantics.md).</span><span class="sxs-lookup"><span data-stu-id="caaec-213">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="caaec-214">Kullanacağınız <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> yerel bir bildirim deyiminin veri akış analizi gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-214">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="caaec-215">Ardından, bu veri akışını analiz sonuçlarını yerel değişkeni başka bir yerde yeni değerle yazılan olmadığından emin olmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="caaec-215">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="caaec-216">Çağrı <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> almak için genişletme yöntemi <xref:Microsoft.CodeAnalysis.ILocalSymbol> değişkeni ve bulunan olmayan onay <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> akış analizi veri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="caaec-216">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="caaec-217">Sonuna aşağıdaki kodu ekleyin `AnalyzeNode` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="caaec-217">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="caaec-218">Yeni eklenen kod değişkeni değiştirilmez ve bu nedenle yapılabilir sağlar `const`.</span><span class="sxs-lookup"><span data-stu-id="caaec-218">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="caaec-219">Bu tanılama yükseltme zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="caaec-219">It's time to raise the diagnostic.</span></span> <span data-ttu-id="caaec-220">Son satırı olarak aşağıdaki kodu ekleyin `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="caaec-220">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="caaec-221">İlerleme durumunuzu tuşlarına basarak denetleyebilirsiniz **F5** , Çözümleyicisi'ni çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="caaec-221">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="caaec-222">Daha önce oluşturduğunuz konsol uygulaması yükleyin ve ardından aşağıdaki test kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-222">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="caaec-223">Ampul görünür olmalıdır ve bir tanılama, çözümleyici bildirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-223">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="caaec-224">Ancak, ampul hala Şablonu oluşturulan kod düzeltme kullanır ve büyük harf yapılmış söyler.</span><span class="sxs-lookup"><span data-stu-id="caaec-224">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="caaec-225">Sonraki bölümde, kod yazmaya açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="caaec-225">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="caaec-226">Kod yazmaya</span><span class="sxs-lookup"><span data-stu-id="caaec-226">Write the code fix</span></span>

<span data-ttu-id="caaec-227">Bir çözümleyici, bir veya daha fazla kod düzeltmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="caaec-227">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="caaec-228">Bir kod düzeltme bildirilen sorunu ele alan bir düzenleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-228">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="caaec-229">Oluşturduğunuz için Çözümleyicisi, const anahtar sözcüğü ekleyen bir kod düzeltme sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="caaec-229">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="caaec-230">Kullanıcı buradan ampul UI düzenleyicide ve Visual Studio kod değişikliklerini seçer.</span><span class="sxs-lookup"><span data-stu-id="caaec-230">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="caaec-231">Açık **MakeConstCodeFixProvider.cs** şablon tarafından eklenen dosya.</span><span class="sxs-lookup"><span data-stu-id="caaec-231">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="caaec-232">Bu kod düzeltmesi zaten tanı, tanılama, çözümleyici tarafından üretilen kimliği en fazla kablolu, ancak henüz doğru kod dönüşüm uygulamaz.</span><span class="sxs-lookup"><span data-stu-id="caaec-232">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="caaec-233">İlk şablon kodunu bazıları kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="caaec-233">First you should remove some of the template code.</span></span> <span data-ttu-id="caaec-234">Başlık dizesini "Yapma sabitine" değiştirin:</span><span class="sxs-lookup"><span data-stu-id="caaec-234">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="caaec-235">Ardından, silmek `MakeUppercaseAsync` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-235">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="caaec-236">Artık geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-236">It no longer applies.</span></span>

<span data-ttu-id="caaec-237">Tüm kod düzeltmeleri türetilmesi <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span><span class="sxs-lookup"><span data-stu-id="caaec-237">All code fixes derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="caaec-238">Bunların tümü geçersiz kılma <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmeleri bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="caaec-238">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="caaec-239">İçinde `RegisterCodeFixesAsync`, değiştirmek için aradığınız üst düğüm türü bir <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tanılama eşleştirmek için:</span><span class="sxs-lookup"><span data-stu-id="caaec-239">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="caaec-240">Ardından, bir kod düzeltme kaydetmek için son satırını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="caaec-240">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="caaec-241">Düzeltmenizi eklemesini sonuçları yeni bir belge oluşturacak `const` değiştiricisi var olan bir bildirim için:</span><span class="sxs-lookup"><span data-stu-id="caaec-241">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="caaec-242">Sembol sunucusunda yeni eklenen kod kırmızı dalgalı çizgiler görürsünüz `MakeConstAsync`.</span><span class="sxs-lookup"><span data-stu-id="caaec-242">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="caaec-243">Eklemek için bir bildirim `MakeConstAsync` aşağıdaki kod gibi:</span><span class="sxs-lookup"><span data-stu-id="caaec-243">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="caaec-244">Yeni `MakeConstAsync` transform metodu <xref:Microsoft.CodeAnalysis.Document> yeni bir kullanıcının kaynak dosyasını temsil eden <xref:Microsoft.CodeAnalysis.Document> artık içeren bir `const` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="caaec-244">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="caaec-245">Yeni oluşturduğunuz `const` bildirim deyiminin önündeki eklemek için anahtar belirteci.</span><span class="sxs-lookup"><span data-stu-id="caaec-245">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="caaec-246">İlk önde gelen tüm Meraklısına Notlar bildirim deyiminin ilk belirtecinden kaldırıp ekleyebilir dikkatli olun `const` belirteci.</span><span class="sxs-lookup"><span data-stu-id="caaec-246">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="caaec-247">Aşağıdaki kodu ekleyin `MakeConstAsync` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="caaec-247">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="caaec-248">Ardından, ekleme `const` aşağıdaki kodu kullanarak bildirimine belirteci:</span><span class="sxs-lookup"><span data-stu-id="caaec-248">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="caaec-249">Ardından, yeni bir bildirim C# biçimlendirme kurallarını eşleşecek şekilde biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="caaec-249">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="caaec-250">Varolan kodu eşleştirmek için değişikliklerinizi biçimlendirme daha iyi bir deneyim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="caaec-250">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="caaec-251">Mevcut koddan hemen sonra aşağıdaki deyimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-251">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="caaec-252">Bu kod için yeni bir ad alanı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-252">A new namespace is required for this code.</span></span> <span data-ttu-id="caaec-253">Aşağıdaki `using` deyimini dosyanın en üstüne:</span><span class="sxs-lookup"><span data-stu-id="caaec-253">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="caaec-254">Son adım, düzenlemeniz olmasını sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="caaec-254">The final step is to make your edit.</span></span> <span data-ttu-id="caaec-255">Bu işlem için üç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="caaec-255">There are three steps to this process:</span></span>

1. <span data-ttu-id="caaec-256">Var olan bir belgeyi tanıtıcısını alın.</span><span class="sxs-lookup"><span data-stu-id="caaec-256">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="caaec-257">Var olan bildirim yeni bildirimiyle değiştirerek yeni bir belge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caaec-257">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="caaec-258">Yeni belge döndürür.</span><span class="sxs-lookup"><span data-stu-id="caaec-258">Return the new document.</span></span>

<span data-ttu-id="caaec-259">Sonuna aşağıdaki kodu ekleyin `MakeConstAsync` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="caaec-259">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="caaec-260">Kod düzeltmenizi denemek hazırdır.</span><span class="sxs-lookup"><span data-stu-id="caaec-260">Your code fix is ready to try.</span></span>  <span data-ttu-id="caaec-261">Visual Studio ikinci bir örneğini Çözümleyicisi projeyi çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="caaec-261">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="caaec-262">İkinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi oluşturun ve Main yöntemi için sabit değerlerle başlatılan birkaç yerel değişken bildirimlerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="caaec-262">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="caaec-263">Bunlar aşağıda gösterildiği gibi uyarı olarak raporlanır görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="caaec-263">You'll see that they are reported as warnings as below.</span></span>

![Const uyarıları yapabilirsiniz](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="caaec-265">Devam eden birçok yaptık.</span><span class="sxs-lookup"><span data-stu-id="caaec-265">You've made a lot of progress.</span></span> <span data-ttu-id="caaec-266">Yapılabilecek bildirimleri altında dalgalı çizgiler vardır `const`.</span><span class="sxs-lookup"><span data-stu-id="caaec-266">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="caaec-267">Ancak yine de yapmak için iş yok.</span><span class="sxs-lookup"><span data-stu-id="caaec-267">But there is still work to do.</span></span> <span data-ttu-id="caaec-268">Eklerseniz bu düzgün çalışır. `const` başlayarak bildirimlere `i`, ardından `j` ve son olarak `k`.</span><span class="sxs-lookup"><span data-stu-id="caaec-268">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="caaec-269">Ancak eklerseniz `const` değiştiricisi ile başlayarak, farklı bir sıra i `k`, hataları, çözümleyici oluşturur: `k` bildirilemez `const`sürece `i` ve `j` her ikisi de zaten olan `const`.</span><span class="sxs-lookup"><span data-stu-id="caaec-269">But, if you add the `const` modifier i a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="caaec-270">Değişkenleri bildirilir ve başlatılır farklı şekilde ele emin olmak için daha fazla analiz yapmak var.</span><span class="sxs-lookup"><span data-stu-id="caaec-270">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="caaec-271">Veri odaklı testler oluşturun</span><span class="sxs-lookup"><span data-stu-id="caaec-271">Build data driven tests</span></span>

<span data-ttu-id="caaec-272">Çözümleyicisi ve kod basit bir const yapılabilmesi için tek bir bildirimde kasasındaki iş düzeltin.</span><span class="sxs-lookup"><span data-stu-id="caaec-272">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="caaec-273">Bu uygulama hatalarını burada yapar, çok sayıda olası bildirim deyimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="caaec-273">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="caaec-274">Bu gibi durumlarda, şablon tarafından yazılmış birim testi kitaplığı birlikte çalışarak karşılayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-274">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="caaec-275">Visual Studio ikinci bir kopyası tekrar tekrar açarak değerinden daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="caaec-275">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="caaec-276">Açık **MakeConstUnitTests.cs** birim test projesi dosyasında.</span><span class="sxs-lookup"><span data-stu-id="caaec-276">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="caaec-277">Şablon bir Çözümleyicisi ve kod düzeltmesi birim testi için iki ortak desenler izleyen iki testten oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="caaec-277">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="caaec-278">`TestMethod1` Bu karakteri, bir Tanılama Çözümleyicisi sağlayan bir test desenini bildirmez gösterir.</span><span class="sxs-lookup"><span data-stu-id="caaec-278">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="caaec-279">`TestMethod2` bir tanılama raporlama ve kod düzeltmesi çalıştıran desenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="caaec-279">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="caaec-280">Aşağıdaki kod, Çözümleyicisi için neredeyse her test için bu iki Düzen biri.</span><span class="sxs-lookup"><span data-stu-id="caaec-280">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="caaec-281">Birinci adım için veri odaklı testler bu testleri yeniden.</span><span class="sxs-lookup"><span data-stu-id="caaec-281">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="caaec-282">Ardından, farklı test girişleri göstermek için yeni dize sabitleri ekleyerek yeni testler oluşturun kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="caaec-282">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="caaec-283">Verimlilik için veri odaklı testler iki testleri yeniden düzenleme ilk adımdır.</span><span class="sxs-lookup"><span data-stu-id="caaec-283">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="caaec-284">Ardından, her yeni test için birkaç dize sabitleri tanımlamak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-284">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="caaec-285">Yeniden düzenleme sırasında her iki yöntem de daha iyi yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="caaec-285">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="caaec-286">Değiştirin `TestMethod1` hiçbir tanılama sağlar. Bu test ile oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="caaec-286">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="caaec-287">Bu test için yeni bir veri satırı bir uyarı tetiklemek, tanılama oluşmamalıdır herhangi bir kod parçası tanımlayarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-287">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="caaec-288">Bu aşırı yüklemesini `VerifyCSharpDiagnostic` için kaynak kod parçasını harekete hiçbir tanılama olduğunda geçirir.</span><span class="sxs-lookup"><span data-stu-id="caaec-288">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="caaec-289">Ardından, değiştirin `TestMethod2` bir tanılama oluşturulur sağlar. Bu test ve kaynak kod parçasını için uygulanan bir kod düzeltmesi:</span><span class="sxs-lookup"><span data-stu-id="caaec-289">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="caaec-290">Yukarıdaki kod, beklenen Tanılama sonucu oluşturan koda da birkaç değişiklikler yaptınız.</span><span class="sxs-lookup"><span data-stu-id="caaec-290">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="caaec-291">Kayıtlı genel sabitleri kullanan `MakeConst` Çözümleyicisi.</span><span class="sxs-lookup"><span data-stu-id="caaec-291">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="caaec-292">Ayrıca, iki dize sabitleri için girdi ve sabit kaynak kullanır.</span><span class="sxs-lookup"><span data-stu-id="caaec-292">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="caaec-293">Aşağıdaki dize sabitleri ekleyin `UnitTest` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="caaec-293">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="caaec-294">Bunlar geçirmek emin olmak için bu iki testleri çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="caaec-294">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="caaec-295">Visual Studio'da açın **Test Gezgini** seçerek **Test** > **Windows** > **Test Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="caaec-295">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="caaec-296">Baskı **tümünü Çalıştır** bağlantı.</span><span class="sxs-lookup"><span data-stu-id="caaec-296">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="caaec-297">Geçerli bildirimleri için testler oluşturma</span><span class="sxs-lookup"><span data-stu-id="caaec-297">Create tests for valid declarations</span></span>

<span data-ttu-id="caaec-298">Genel kural olarak, en az iş yapmak mümkün olan en kısa sürede Çözümleyicileri çıkılması gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="caaec-298">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="caaec-299">Visual Studio çağrıları kullanıcı düzenlemeleri kod Çözümleyicileri kayıtlı.</span><span class="sxs-lookup"><span data-stu-id="caaec-299">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="caaec-300">Yanıt verme hızını önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="caaec-300">Responsiveness is a key requirement.</span></span> <span data-ttu-id="caaec-301">Çeşitli test çalışmaları, tanılama tetiklemelidir olmayan kod için vardır.</span><span class="sxs-lookup"><span data-stu-id="caaec-301">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="caaec-302">Çözümleyici zaten bu testler, burada bir değişken başlatıldıktan sonra atanır çalışması birini işler.</span><span class="sxs-lookup"><span data-stu-id="caaec-302">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="caaec-303">Bu durumda temsil etmek için testlerinizi aşağıdaki dize sabiti ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-303">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="caaec-304">Ardından, aşağıdaki kod parçacığında gösterildiği gibi bu test için veri satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-304">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="caaec-305">Bu test de geçer.</span><span class="sxs-lookup"><span data-stu-id="caaec-305">This test passes as well.</span></span> <span data-ttu-id="caaec-306">Ardından, henüz işlenen henüz koşulları için sabitleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-306">Next, add constants for conditions you haven't handled yet:</span></span>

* <span data-ttu-id="caaec-307">Zaten olan bildirimleri `const`zaten const çünkü:</span><span class="sxs-lookup"><span data-stu-id="caaec-307">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

* <span data-ttu-id="caaec-308">Kullanılacak herhangi bir değer olduğundan herhangi bir başlatıcıya sahip bildirimleri:</span><span class="sxs-lookup"><span data-stu-id="caaec-308">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

* <span data-ttu-id="caaec-309">Derleme zamanı sabit olamayacağı Başlatıcı bir sabit olduğu bildirimleri:</span><span class="sxs-lookup"><span data-stu-id="caaec-309">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="caaec-310">C# birden çok bildirimleri bir deyim olarak izin verdiğinden daha da karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="caaec-310">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="caaec-311">Aşağıdaki test çalışması dize sabiti göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="caaec-311">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="caaec-312">Değişken `i` sabiti, ancak değişkeni yapılabilir `j` olamaz.</span><span class="sxs-lookup"><span data-stu-id="caaec-312">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="caaec-313">Bu nedenle, bu deyimi const bildirimi yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="caaec-313">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="caaec-314">Ekleme `DataRow` bildirimleri bu testler için:</span><span class="sxs-lookup"><span data-stu-id="caaec-314">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="caaec-315">Testlerinizi yeniden çalıştırın ve bu yeni test çalışmaları başarısız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="caaec-315">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="caaec-316">Doğru bildirimleri yoksaymayı, çözümleyici güncelleştir</span><span class="sxs-lookup"><span data-stu-id="caaec-316">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="caaec-317">Bazı geliştirmeler, çözümleyicisinin ihtiyacınız `AnalyzeNode` bu koşullara uyan kodu filtrelemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="caaec-317">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="caaec-318">Bu koşullar benzer değişiklikleri çözecektir için tüm ilgili koşulları değildirler.</span><span class="sxs-lookup"><span data-stu-id="caaec-318">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="caaec-319">Aşağıdaki değişiklikleri yapın `AnalyzeNode`:</span><span class="sxs-lookup"><span data-stu-id="caaec-319">Make the following changes to `AnalyzeNode`:</span></span>

* <span data-ttu-id="caaec-320">Anlam analizi, tek bir değişken bildirimine incelenir.</span><span class="sxs-lookup"><span data-stu-id="caaec-320">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="caaec-321">Bu kod içinde olması gereken bir `foreach` tüm değişkenleri araştıran döngü, aynı deyiminde bildirilen.</span><span class="sxs-lookup"><span data-stu-id="caaec-321">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
* <span data-ttu-id="caaec-322">Her bir başlatıcıya sahip gerekiyor değişken bildirildi.</span><span class="sxs-lookup"><span data-stu-id="caaec-322">Each declared variable needs to have an initializer.</span></span>
* <span data-ttu-id="caaec-323">Her bildirilen değişkenin başlatıcısı, bir derleme zamanı sabiti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="caaec-323">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="caaec-324">İçinde `AnalyzeNode` yöntemi, özgün anlam analizi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="caaec-324">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="caaec-325">Aşağıdaki kod parçacığıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="caaec-325">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="caaec-326">İlk `foreach` döngü söz dizimsel analizini kullanarak her bir değişken bildirimini inceler.</span><span class="sxs-lookup"><span data-stu-id="caaec-326">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="caaec-327">İlk denetimi değişkeni bir başlatıcıya sahip olacağını garanti eder.</span><span class="sxs-lookup"><span data-stu-id="caaec-327">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="caaec-328">İkinci onay Başlatıcı bir sabit olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-328">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="caaec-329">İkinci döngü özgün anlam analizi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="caaec-329">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="caaec-330">Anlam denetimleri ayrı bir döngüde olduklarından performans üzerinde büyük bir etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="caaec-330">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="caaec-331">Testlerinizi yeniden çalıştırın ve geçirmek tüm bunların görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="caaec-331">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="caaec-332">Son Lehçe Ekle</span><span class="sxs-lookup"><span data-stu-id="caaec-332">Add the final polish</span></span>

<span data-ttu-id="caaec-333">Neredeyse bitti.</span><span class="sxs-lookup"><span data-stu-id="caaec-333">You're almost done.</span></span> <span data-ttu-id="caaec-334">İşlemek, Çözümleyicisi için birkaç başka koşullar vardır.</span><span class="sxs-lookup"><span data-stu-id="caaec-334">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="caaec-335">Kullanıcı kod yazarken, visual Studio Çözümleyicileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="caaec-335">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="caaec-336">Bu, çözümleyici olacak durum genellikle derleme olmayan kod için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="caaec-336">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="caaec-337">Tanılama Çözümleyicisi'nin `AnalyzeNode` yöntemi için değişken türüne dönüştürülebilir sabit değer olup olmadığını denetlemez.</span><span class="sxs-lookup"><span data-stu-id="caaec-337">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="caaec-338">Bu nedenle, geçerli uygulama Int gibi yanlış bir bildirimi sonsuza dek dönüştürecek miyim "abc" =' için bir yerel sabit.</span><span class="sxs-lookup"><span data-stu-id="caaec-338">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="caaec-339">Bu koşul için bir kaynak dize sabitine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-339">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="caaec-340">Ayrıca, başvuru türleri düzgün işlenmez.</span><span class="sxs-lookup"><span data-stu-id="caaec-340">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="caaec-341">Bir başvuru türü için izin verilen maksimum yalnızca sabit değer `null`, bu durumda dışındaki <xref:System.String?displayProperty=nameWIthType>, dize değişmez değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="caaec-341">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWIthType>, which allows string literals.</span></span> <span data-ttu-id="caaec-342">Diğer bir deyişle, `const string s = "abc"` geçerli, ancak `const object s = "abc"` değil.</span><span class="sxs-lookup"><span data-stu-id="caaec-342">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="caaec-343">Bu kod parçacığı bu koşulu doğrular:</span><span class="sxs-lookup"><span data-stu-id="caaec-343">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="caaec-344">Eksiksiz olması için bir dize için sabit bir bildirimde oluşturabilirsiniz emin olmak için başka bir test eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="caaec-344">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="caaec-345">Aşağıdaki kod parçacığı, hem tanılama başlatır kodu ve kod düzeltme uygulandıktan sonra tanımlar:</span><span class="sxs-lookup"><span data-stu-id="caaec-345">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="caaec-346">Son olarak, bir değişken ile bildirilirse `var` anahtar sözcüğü, kod düzeltmesi yanlış şeyi yapar ve oluşturur bir `const var` bildirimi, C# dil tarafından desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="caaec-346">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="caaec-347">Bu hatayı düzeltmek için kod düzeltme değiştirmelisiniz `var` anahtar sözcüğü ile çıkarsanan tür adı:</span><span class="sxs-lookup"><span data-stu-id="caaec-347">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="caaec-348">Bu değişiklikler iki test için veri satırı bildirimler güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="caaec-348">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="caaec-349">Aşağıdaki kod bu testleri ile tüm veri satır öznitelikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="caaec-349">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="caaec-350">Neyse ki, yukarıdaki hataları tüm yeni öğrendiğiniz teknikleri kullanarak çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="caaec-350">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="caaec-351">İlk hatayı düzeltmek için önce açın **DiagnosticAnalyzer.cs** ve burada her biri yerel bildirimin başlatıcıları sabit değerler atadığınız denetlenir foreach döngüsü bulun.</span><span class="sxs-lookup"><span data-stu-id="caaec-351">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="caaec-352">Hemen _önce_ çağrı, ilk foreach döngüsü `context.SemanticModel.GetTypeInfo()` yerel bildirim türü hakkında ayrıntılı bilgi almak için:</span><span class="sxs-lookup"><span data-stu-id="caaec-352">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="caaec-353">Ardından, içinde `foreach` döngü, her Başlatıcı, değişken türüne dönüştürülebilir olduğundan emin olmak için kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="caaec-353">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="caaec-354">Başlatıcı bir sabit olduğundan emin olduktan sonra aşağıdaki onay ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-354">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="caaec-355">Sonraki değişiklik bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="caaec-355">The next change builds upon the last one.</span></span> <span data-ttu-id="caaec-356">Kapanış küme ayracı, ilk foreach döngüsü önce sabiti, dize veya null olduğunda yerel bildirim türünü denetlemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="caaec-356">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="caaec-357">Var değiştirmek için kod düzeltme sağlayıcısı biraz daha fazla kod yazmanız gereken ' anahtar sözcüğü doğru tür adı.</span><span class="sxs-lookup"><span data-stu-id="caaec-357">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="caaec-358">Geri dönüp **CodeFixProvider.cs**.</span><span class="sxs-lookup"><span data-stu-id="caaec-358">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="caaec-359">Ekleyeceğiniz kod, aşağıdaki adımları gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="caaec-359">The code you'll add does the following steps:</span></span>

* <span data-ttu-id="caaec-360">Bildirimi olup olmadığını bir `var` bildirimi ve bu ise:</span><span class="sxs-lookup"><span data-stu-id="caaec-360">Check if the declaration is a `var` declaration, and if it is:</span></span>
* <span data-ttu-id="caaec-361">Yeni bir tür için çıkarsanan tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="caaec-361">Create a new type for the inferred type.</span></span>
* <span data-ttu-id="caaec-362">Tür bildirimi bir diğer ad olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="caaec-362">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="caaec-363">Bu nedenle, bildirmek için yasal ise `const var`.</span><span class="sxs-lookup"><span data-stu-id="caaec-363">If so, it is legal to declare `const var`.</span></span>
* <span data-ttu-id="caaec-364">Emin olun `var` bu programda bir tür adı değil.</span><span class="sxs-lookup"><span data-stu-id="caaec-364">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="caaec-365">(Bu durumda, `const var` geçerlidir).</span><span class="sxs-lookup"><span data-stu-id="caaec-365">(If so, `const var` is legal).</span></span>
* <span data-ttu-id="caaec-366">Tam tür adı basitleştirin</span><span class="sxs-lookup"><span data-stu-id="caaec-366">Simplify the full type name</span></span>

<span data-ttu-id="caaec-367">Bir sürü kod gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="caaec-367">That sounds like a lot of code.</span></span> <span data-ttu-id="caaec-368">Bu değil.</span><span class="sxs-lookup"><span data-stu-id="caaec-368">It's not.</span></span> <span data-ttu-id="caaec-369">Başlatır ve bildirir satırı değiştirin `newLocal` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="caaec-369">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="caaec-370">Başlatmadan sonra hemen gider `newModifiers`:</span><span class="sxs-lookup"><span data-stu-id="caaec-370">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="caaec-371">Bir eklemeniz gerekecektir `using` kullanılacak ifadesinin <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> türü:</span><span class="sxs-lookup"><span data-stu-id="caaec-371">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="caaec-372">Testlerinizi çalıştırmak ve tüm geçmelidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-372">Run your tests, and they should all pass.</span></span> <span data-ttu-id="caaec-373">Kendinize, tamamlanmış Çözümleyicisi'ni çalıştırarak kutlayın.</span><span class="sxs-lookup"><span data-stu-id="caaec-373">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="caaec-374">Çözümleyici proje yüklenen Roslyn önizlemesi uzantısıyla Visual Studio ikinci bir örneğini çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="caaec-374">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

* <span data-ttu-id="caaec-375">İkinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi oluşturma ve ekleme `int x = "abc";` Main yöntemi için.</span><span class="sxs-lookup"><span data-stu-id="caaec-375">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="caaec-376">(Rağmen bir derleyici hatası beklendiği gibi), hiçbir uyarı ilk hata düzeltmesi sayesinde bu yerel değişken bildirimi olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-376">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
* <span data-ttu-id="caaec-377">Ardından, ekleme `object s = "abc";` Main yöntemi için.</span><span class="sxs-lookup"><span data-stu-id="caaec-377">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="caaec-378">İkinci hata düzeltmesi nedeniyle hiçbir uyarı bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="caaec-378">Because of the second bug fix, no warning should be reported.</span></span>
* <span data-ttu-id="caaec-379">Son olarak, kullanan başka bir yerel değişken Ekle `var` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="caaec-379">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="caaec-380">Bir uyarı bildirilir ve sol altında bir öneri görünür görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="caaec-380">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
* <span data-ttu-id="caaec-381">Düzenleyici giriş işaretinin dalgalı alt çizginin taşıyın ve CTRL tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="caaec-381">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="caaec-382">Önerilen kod düzeltme görüntülenecek.</span><span class="sxs-lookup"><span data-stu-id="caaec-382">to display the suggested code fix.</span></span> <span data-ttu-id="caaec-383">Kod düzeltmenizi seçtikten sonra dikkat var' anahtar sözcüğü artık işlenir doğru.</span><span class="sxs-lookup"><span data-stu-id="caaec-383">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="caaec-384">Son olarak, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="caaec-384">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="caaec-385">Bu değişikliklerden sonra kırmızı dalgalı çizgiler yalnızca ilk iki değişkenlerde alın.</span><span class="sxs-lookup"><span data-stu-id="caaec-385">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="caaec-386">Ekleme `const` hem `i` ve `j`, yeni bir uyarı alın `k` artık olabileceğinden `const`.</span><span class="sxs-lookup"><span data-stu-id="caaec-386">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="caaec-387">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="caaec-387">Congratulations!</span></span> <span data-ttu-id="caaec-388">Sorunu algılamak için üzerinde anında kod analizini yapar ve bunu düzeltmek için bir hızlı düzeltme sağlayan ilk .NET derleyici platformu uzantısı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="caaec-388">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="caaec-389">Süreç boyunca birçok .NET derleyici Platformu SDK'sı (Roslyn API'leri) parçası olan API'leri kod öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="caaec-389">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="caaec-390">Çalışmanızı karşı denetleyebilirsiniz [tamamlanan örnek](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) örnekleri GitHub depomuzda bulunan.</span><span class="sxs-lookup"><span data-stu-id="caaec-390">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span> <span data-ttu-id="caaec-391">Veya karşıdan yükleyebileceğiniz [projeyi ZIP dosyası](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span><span class="sxs-lookup"><span data-stu-id="caaec-391">Or you can download [zip file of the completed project](https://github.com/dotnet/samples/blob/master/csharp/roslyn-sdk/Tutorials/MakeConst.zip)</span></span>

## <a name="other-resources"></a><span data-ttu-id="caaec-392">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="caaec-392">Other resources</span></span>

- [<span data-ttu-id="caaec-393">Söz dizimi Analizi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="caaec-393">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="caaec-394">Anlam Analizi ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="caaec-394">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
