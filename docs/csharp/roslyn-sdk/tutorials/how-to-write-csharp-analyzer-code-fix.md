---
title: 'Öğretici: İlk çözümleyicinizi ve kod düzeltmenizi yazın'
description: Bu öğretici, .NET Derleyici SDK 'yu (Roslyn API'leri) kullanarak bir çözümleyici ve kod düzeltmesi oluşturmak için adım adım yönergeler sağlar.
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: f6fc21c010f9b5fcd5e709ef822639c020a7c93b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240556"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="bdffd-103">Öğretici: İlk çözümleyicinizi ve kod düzeltmenizi yazın</span><span class="sxs-lookup"><span data-stu-id="bdffd-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="bdffd-104">.NET Derleyici Platformu SDK, C# veya Visual Basic kodunu hedefleyen özel uyarılar oluşturmak için ihtiyacınız olan araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="bdffd-105">**Çözümleyiciniz,** kural ihlallerinizi tanıyan kod lar içerir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="bdffd-106">**Kod düzeltmeniz** ihlali düzelten kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="bdffd-107">Uyguladığınız kurallar, kod yapısından kodlama stiline, adlandırma kurallarına ve daha fazlasına kadar her şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="bdffd-108">.NET Derleyici Platformu, geliştiriciler kod yazarken analiz leri çalıştırmak için bir çerçeve sağlar ve kodu sabitlemek için tüm Visual Studio UI özellikleri: editörde squiggles gösteren, Visual Studio Hata Listesi doldurma, "ampul" oluşturma öneriler ve önerilen düzeltmelerin zengin önizlemegösteren.</span><span class="sxs-lookup"><span data-stu-id="bdffd-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="bdffd-109">Bu eğitimde, Roslyn API'lerini kullanarak bir **çözümleyici** ve beraberindeki **kod düzeltmesinin** oluşturulmasını keşfedeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="bdffd-110">Çözümleyici, kaynak kodu çözümlemesi gerçekleştirmenin ve bir sorunu kullanıcıya bildirmenin bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="bdffd-111">İsteğe bağlı olarak, bir çözümleyici kullanıcının kaynak kodunda yapılan bir değişikliği temsil eden bir kod düzeltmesi de sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="bdffd-112">Bu öğretici, `const` değiştirici kullanılarak bildirilebilen ancak olmayan yerel değişken bildirimleri bulan bir çözümleyici oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="bdffd-113">Eşlik eden kod düzeltmesi, `const` değiştiricieklemek için bu bildirimleri değiştirir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bdffd-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="bdffd-114">Prerequisites</span></span>

- [<span data-ttu-id="bdffd-115">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="bdffd-115">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="bdffd-116">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="bdffd-116">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="bdffd-117">**.NET Derleyici Platformu SDK'yı** Visual Studio Installer üzerinden yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-117">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="bdffd-118">Çözümleyicinizi oluşturmak ve doğrulamak için birkaç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="bdffd-118">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="bdffd-119">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-119">Create the solution.</span></span>
1. <span data-ttu-id="bdffd-120">Çözümleyici adını ve açıklamasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-120">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="bdffd-121">Çözümleyici uyarılarını ve önerilerini bildirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-121">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="bdffd-122">Önerileri kabul etmek için kod düzeltmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-122">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="bdffd-123">Birim testleri ile analizi geliştirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-123">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="bdffd-124">Çözümleyici şablonu keşfedin</span><span class="sxs-lookup"><span data-stu-id="bdffd-124">Explore the analyzer template</span></span>

<span data-ttu-id="bdffd-125">Çözümleyiciniz, yerel sabitlere dönüştürülebilecek yerel değişken bildirimlerini kullanıcıya bildirir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-125">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="bdffd-126">Örneğin, aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="bdffd-126">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bdffd-127">Yukarıdaki kodda, `x` sabit bir değer atanır ve hiçbir zaman değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="bdffd-127">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="bdffd-128">`const` Değiştirici kullanılarak bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-128">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bdffd-129">Bir değişkenin sabit yapılıp yapılamayacağını belirlemek için yapılan analiz, sözdizimsal analiz, değişkenin asla yazılmamasını sağlamak için başharf ifadesinin sürekli analizi ve veri akışı analizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-129">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="bdffd-130">.NET Derleyici Platformu, bu çözümlemesi kolaylaştıran API'ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-130">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="bdffd-131">İlk adım kod düzeltme projesi ile yeni bir C # **Analyzer** oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-131">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="bdffd-132">Visual Studio'da, Yeni Proje iletişim kutusunu görüntülemek için **Dosya > Yeni > Projesi...** seçeneğini belirleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-132">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="bdffd-133">**Visual C# > Genişletilebilirlik** **altında, kod düzeltmeli Çözümleyici'yi (.NET Standart)** seçin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-133">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="bdffd-134">Projenize "**MakeConst**" adını ve Tamam'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-134">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="bdffd-135">Kod düzeltme şablonuna sahip çözümleyici üç proje oluşturur: biri çözümleyici ve kod düzeltmesi içerir, ikincisi birim test projesidir ve üçüncüsü VSIX projesidir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-135">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="bdffd-136">Varsayılan başlangıç projesi VSIX projesidir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-136">The default startup project is the VSIX project.</span></span> <span data-ttu-id="bdffd-137">VSIX projesini başlatmak için **F5** tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-137">Press **F5** to start the VSIX project.</span></span> <span data-ttu-id="bdffd-138">Bu, yeni çözümleyicinizi yüklemiş olan Visual Studio'nun ikinci bir örneğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-138">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="bdffd-139">Çözümleyicinizi çalıştırdığınızda Visual Studio'nun ikinci bir kopyasını başlayırsınız.</span><span class="sxs-lookup"><span data-stu-id="bdffd-139">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="bdffd-140">Bu ikinci kopya, ayarları depolamak için farklı bir kayıt defteri kovanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-140">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="bdffd-141">Bu, Visual Studio'nun iki kopyasındaki görsel ayarları ayırt etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-141">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="bdffd-142">Visual Studio'nun deneysel çalışması için farklı bir tema seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-142">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="bdffd-143">Buna ek olarak, Visual Studio'nun deneysel çalışmasını kullanarak ayarlarınızda gezinmeyin veya Visual Studio hesabınıza giriş yapmayın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-143">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="bdffd-144">Bu ayarları farklı tutar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-144">That keeps the settings different.</span></span>

<span data-ttu-id="bdffd-145">Yeni başladığınız ikinci Visual Studio örneğinde, yeni bir C# Console Application projesi oluşturun (.NET Core veya .NET Framework projesi çalışacaktır - çözümleyiciler kaynak düzeyinde çalışır.) Dalgalı bir alt çizgi ile belirteci üzerinde gezinmek ve bir çözümleyici tarafından sağlanan uyarı metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-145">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="bdffd-146">Şablon, tür adının aşağıdaki şekilde gösterildiği gibi küçük harfler içerdiği her tür bildiriminde bir uyarı bildiren bir çözümleyici oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bdffd-146">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Çözümleyici raporlama uyarısı](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="bdffd-148">Şablon ayrıca, küçük harf karakterleri içeren herhangi bir tür adını tüm büyük harflerle değiştiren bir kod düzeltmesi de sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-148">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="bdffd-149">Önerilen değişiklikleri görmek için uyarıyla birlikte görüntülenen ampule tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-149">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="bdffd-150">Önerilen değişiklikleri kabul etmek, tür adını ve çözümdeki bu türe yapılan tüm başvuruları güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-150">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="bdffd-151">Şimdi ilk çözümleyiciyi iş başında gördüğünüze göre, ikinci Visual Studio örneğini kapatın ve çözümleyici projenize geri dönün.</span><span class="sxs-lookup"><span data-stu-id="bdffd-151">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="bdffd-152">Visual Studio'nun ikinci bir kopyasını başlatmak ve çözümleyicinizdeki her değişikliği test etmek için yeni kodlar oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bdffd-152">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="bdffd-153">Şablon ayrıca sizin için bir birim test projesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-153">The template also creates a unit test project for you.</span></span> <span data-ttu-id="bdffd-154">Bu proje iki test içeriyor.</span><span class="sxs-lookup"><span data-stu-id="bdffd-154">That project contains two tests.</span></span> <span data-ttu-id="bdffd-155">`TestMethod1`tanılamayı tetiklemeden kodu çözümleyen bir testin tipik biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-155">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="bdffd-156">`TestMethod2`tanılamayı tetikleyen bir testin biçimini gösterir ve ardından önerilen kod düzeltmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="bdffd-156">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="bdffd-157">Çözümleyicinizi ve kod düzeltmenizi oluştururken, çalışmanızı doğrulamak için farklı kod yapıları için testler yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="bdffd-157">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="bdffd-158">Analizörler için birim testleri Visual Studio ile etkileşimli olarak test etmekten çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-158">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="bdffd-159">Çözümleyici birim testleri, çözümleyicinizi hangi kod oluşturmanın tetiklemesi gerektiğini ve tetiklememesi gerektiğini bildiğinizde harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-159">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="bdffd-160">Visual Studio başka bir kopyasını analizör yükleme keşfetmek ve henüz düşünmemiş olabilirsiniz yapıları bulmak için harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-160">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="bdffd-161">Çözümleyici kayıtları oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdffd-161">Create analyzer registrations</span></span>

<span data-ttu-id="bdffd-162">Şablon, `DiagnosticAnalyzer` **MakeConstAnalyzer.cs** dosyasında ilk sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-162">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="bdffd-163">Bu ilk çözümleyici her çözümleyicinin iki önemli özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-163">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="bdffd-164">Her tanı çözümleyicisi, çalıştığı dili açıklayan bir `[DiagnosticAnalyzer]` öznitelik sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-164">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="bdffd-165">Her tanı analizörü sınıftan <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> türemelidir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-165">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="bdffd-166">Şablon ayrıca herhangi bir çözümleyicinin parçası olan temel özellikleri de gösterir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-166">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="bdffd-167">Eylemleri kaydedin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-167">Register actions.</span></span> <span data-ttu-id="bdffd-168">Eylemler, ihlaller için kodu incelemek için çözümleyicinizi tetikleyecek kod değişikliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bdffd-168">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="bdffd-169">Visual Studio kayıtlı bir eylemle eşleşen kod edinimi algıladığında, çözümleyicinizin kayıtlı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-169">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="bdffd-170">Tanılama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-170">Create diagnostics.</span></span> <span data-ttu-id="bdffd-171">Çözümleyiciniz bir ihlali algıladığında, Visual Studio'nun kullanıcıyı ihlali bildirmek için kullandığı bir tanılama nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-171">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="bdffd-172">Eylemleri metodu geçersiz <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> kılmanızda kaydedersiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-172">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bdffd-173">Bu öğreticide, yerel bildirimleri arayan **sözdizimi düğümlerini** ziyaret eder ve bunlardan hangisinin sabit değerlere sahip olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-173">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="bdffd-174">Bir bildirim sabit olabilirse, çözümleyiciniz bir tanı oluşturur ve raporlar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-174">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="bdffd-175">İlk adım, bu sabitlerin "Const Yap" çözümleyicinizi göstermesi için kayıt sabitlerini ve `Initialize` yöntemini güncelleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-175">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="bdffd-176">Dize sabitlerinin çoğu dize kaynak dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-176">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="bdffd-177">Daha kolay yerelleştirme için bu uygulamayı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-177">You should follow that practice for easier localization.</span></span> <span data-ttu-id="bdffd-178">**MakeConst** çözümleyici projesi için **Resources.resx** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-178">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="bdffd-179">Bu, kaynak düzenleyicisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bdffd-179">This displays the resource editor.</span></span> <span data-ttu-id="bdffd-180">Dize kaynaklarını aşağıdaki gibi güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-180">Update the string resources as follows:</span></span>

- <span data-ttu-id="bdffd-181">"Değişken sabit yapılabilir" olarak değiştirin. `AnalyzerTitle`</span><span class="sxs-lookup"><span data-stu-id="bdffd-181">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="bdffd-182">"Sabit yapılabilir" olarak değiştirin. `AnalyzerMessageFormat`</span><span class="sxs-lookup"><span data-stu-id="bdffd-182">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="bdffd-183">"Constant yap" olarak değiştirin. `AnalyzerDescription`</span><span class="sxs-lookup"><span data-stu-id="bdffd-183">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="bdffd-184">Ayrıca, **Access Değiştirici** açılır'ı `public`' olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-184">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="bdffd-185">Bu, birim testlerinde bu sabitlerin kullanılmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-185">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="bdffd-186">Bitirdikten sonra, kaynak düzenleyicisi aşağıdaki şekilde görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Dize kaynaklarını güncelleştirme](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="bdffd-188">Kalan değişiklikler çözümleyici dosyasında dır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="bdffd-189">Visual Studio'da **MakeConstAnalyzer.cs** aç.</span><span class="sxs-lookup"><span data-stu-id="bdffd-189">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="bdffd-190">Kayıtlı eylemi, semboller üzerinde hareket eden bir eylemden sözdiziminde hareket eden eyleme değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="bdffd-191">`MakeConstAnalyzerAnalyzer.Initialize` Yöntemde, eylemi semboller üzerinde kaydeden satırı bulun:</span><span class="sxs-lookup"><span data-stu-id="bdffd-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="bdffd-192">Aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="bdffd-193">Bu değişiklikten `AnalyzeSymbol` sonra yöntemi silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="bdffd-194">Bu çözümleyici <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>ifadeleri <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> değil, inceler.</span><span class="sxs-lookup"><span data-stu-id="bdffd-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="bdffd-195">Altında `AnalyzeNode` kırmızı dalgalar olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="bdffd-196">Az önce eklediğiniz `AnalyzeNode` kod, bildirilmemiş bir yönteme başvurur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="bdffd-197">Bu yöntemi aşağıdaki kodu kullanarak bildirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="bdffd-198">Aşağıdaki `Category` kodda gösterildiği **gibi MakeConstAnalyzer.cs** "Kullanım" olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-198">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="bdffd-199">Const olabilecek yerel bildirimleri bulma</span><span class="sxs-lookup"><span data-stu-id="bdffd-199">Find local declarations that could be const</span></span>

<span data-ttu-id="bdffd-200">`AnalyzeNode` Yöntemin ilk sürümünü yazma nın zamanı.</span><span class="sxs-lookup"><span data-stu-id="bdffd-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="bdffd-201">Aşağıdaki kod gibi olabilir `const` ama olmayabilir tek bir yerel bildirim için bakmak gerekir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bdffd-202">İlk adım yerel bildirimleri bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-202">The first step is to find local declarations.</span></span> <span data-ttu-id="bdffd-203">MakeConstAnalyzer.cs aşağıdaki kodu `AnalyzeNode` **MakeConstAnalyzer.cs**ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-203">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="bdffd-204">Çözümleyiciniz yerel bildirimlerdeki değişiklikler ve yalnızca yerel bildirimler için kaydolduğundan, bu döküm her zaman başarılı dır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="bdffd-205">Başka hiçbir düğüm türü yönteminize `AnalyzeNode` çağrı yı tetiklemez.</span><span class="sxs-lookup"><span data-stu-id="bdffd-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="bdffd-206">Ardından, değiştiriciler `const` için bildirimi denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="bdffd-207">Onları bulursanız, hemen geri dönün.</span><span class="sxs-lookup"><span data-stu-id="bdffd-207">If you find them, return immediately.</span></span> <span data-ttu-id="bdffd-208">Aşağıdaki kod, yerel `const` bildirimdeki herhangi bir değiştiriciyi arar:</span><span class="sxs-lookup"><span data-stu-id="bdffd-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="bdffd-209">Son olarak, değişkenin `const`.</span><span class="sxs-lookup"><span data-stu-id="bdffd-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="bdffd-210">Bu, baş harfe atandıktan sonra asla atanmamalarını sağlamak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="bdffd-211">Bazı anlamsal analizler <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="bdffd-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="bdffd-212">Bağımsız değişkeni, `context` yerel değişken bildiriminin yapılıp yapılamayacağını `const`belirlemek için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bdffd-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="bdffd-213">A, <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> tek bir kaynak dosyadaki tüm anlamsal bilgilerin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bdffd-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents of all semantic information in a single source file.</span></span> <span data-ttu-id="bdffd-214">[Semantik modelleri](../work-with-semantics.md)kapsayan makalede daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="bdffd-215">Yerel bildirim deyiminde veri akışı çözümlemesi gerçekleştirmek <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bdffd-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="bdffd-216">Ardından, yerel değişkenin başka bir yerde yeni bir değerle yazılmadığından emin olmak için bu veri akışı çözümlemesi sonuçlarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bdffd-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="bdffd-217">Değişkeniçin <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> almak <xref:Microsoft.CodeAnalysis.ILocalSymbol> için uzantı yöntemini arayın ve veri akışı <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> çözümlemesi koleksiyonunda bulunup bulunmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="bdffd-218">`AnalyzeNode` Yöntemin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="bdffd-219">Eklenen kod, değişkenin değiştirilmemesini sağlar ve bu `const`nedenle yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="bdffd-220">Teşhisi yükseltme nin zamanı.</span><span class="sxs-lookup"><span data-stu-id="bdffd-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="bdffd-221">Son satır olarak aşağıdaki kodu `AnalyzeNode`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="bdffd-222">Çözümleyicinizi çalıştırmak için **F5** tuşuna basarak ilerlemenizi kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-222">You can check your progress by pressing **F5** to run your analyzer.</span></span> <span data-ttu-id="bdffd-223">Daha önce oluşturduğunuz konsol uygulamasını yükleyebilir ve ardından aşağıdaki test kodunu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdffd-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bdffd-224">Ampul görünmelidir ve çözümleyiciniz bir tanı bildirmelidir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="bdffd-225">Ancak, ampul hala şablon oluşturulan kod düzeltme kullanır ve büyük harf yapılabilir söyler.</span><span class="sxs-lookup"><span data-stu-id="bdffd-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="bdffd-226">Sonraki bölümde kod düzeltmesi nasıl yazılalıyorum.</span><span class="sxs-lookup"><span data-stu-id="bdffd-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="bdffd-227">Kod düzeltmesini yazma</span><span class="sxs-lookup"><span data-stu-id="bdffd-227">Write the code fix</span></span>

<span data-ttu-id="bdffd-228">Bir çözümleyici bir veya daha fazla kod düzeltmeleri sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="bdffd-229">Kod düzeltmesi, bildirilen sorunu gideren bir düzenleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bdffd-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="bdffd-230">Oluşturduğunuz çözümleyici için, const anahtar sözcüğü ekleyen bir kod düzeltmesi sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdffd-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="bdffd-231">Kullanıcı editör ve Visual Studio ampul UI kodu değiştirir onu seçer.</span><span class="sxs-lookup"><span data-stu-id="bdffd-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="bdffd-232">Şablon tarafından eklenen **MakeConstCodeFixProvider.cs** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-232">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="bdffd-233">Bu kod düzeltmesi zaten tanılama çözümleyiciniz tarafından üretilen Tanılama Kimliği'ne bağlanmış durumda, ancak henüz doğru kod dönüştürmesini uygulamamaktadır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-233">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="bdffd-234">Önce şablon kodunun bir kısmını kaldırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-234">First you should remove some of the template code.</span></span> <span data-ttu-id="bdffd-235">Başlık dizesini "Sabit yap" olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-235">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="bdffd-236">Ardından, `MakeUppercaseAsync` yöntemi silin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-236">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="bdffd-237">Artık geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="bdffd-237">It no longer applies.</span></span>

<span data-ttu-id="bdffd-238">Tüm kod düzeltme <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>sağlayıcıları.</span><span class="sxs-lookup"><span data-stu-id="bdffd-238">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="bdffd-239">Bunların tümü <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmelerini bildirmek için geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-239">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="bdffd-240">In `RegisterCodeFixesAsync`, tanılama eşleşecek şekilde <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> aradığınız ata düğümü türünü değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-240">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="bdffd-241">Ardından, kod düzeltmesini kaydetmek için son satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-241">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="bdffd-242">Düzeltmeniz, `const` değiştiriciyi varolan bir bildirime eklemeden kaynaklanan yeni bir belge oluşturur:</span><span class="sxs-lookup"><span data-stu-id="bdffd-242">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="bdffd-243">Az önce sembole `MakeConstAsync`eklediğiniz kodda kırmızı dalgalı lıklar fark edeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-243">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="bdffd-244">Aşağıdaki kod `MakeConstAsync` gibi bir bildirim ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-244">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="bdffd-245">Yeni `MakeConstAsync` yöntemin, <xref:Microsoft.CodeAnalysis.Document> kullanıcının kaynak dosyasını temsil eden <xref:Microsoft.CodeAnalysis.Document> dosyayı `const` şimdi bir bildirim içeren yeni bir dosyaya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bdffd-245">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="bdffd-246">Bildirim deyiminin `const` önüne eklemek için yeni bir anahtar kelime belirteci oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-246">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="bdffd-247">Önce bildirim deyiminin ilk belirteci herhangi bir satır ı kaldırmak `const` ve belirteç eklemek için dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-247">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="bdffd-248">`MakeConstAsync` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-248">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="bdffd-249">Ardından, aşağıdaki `const` kodu kullanarak bildirime belirteci ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-249">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="bdffd-250">Ardından, c# biçimlendirme kurallarıyla eşleşecek şekilde yeni bildiriyi biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-250">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="bdffd-251">Değişikliklerinizi varolan kodla eşleşecek şekilde biçimlendirmek daha iyi bir deneyim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-251">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="bdffd-252">Varolan koddan hemen sonra aşağıdaki ifadeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-252">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="bdffd-253">Bu kod için yeni bir ad alanı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-253">A new namespace is required for this code.</span></span> <span data-ttu-id="bdffd-254">Dosyanın `using` üst bölümüne aşağıdaki ifadeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-254">Add the following `using` statement to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="bdffd-255">Son adım, sizin de bir şey yapmaktır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-255">The final step is to make your edit.</span></span> <span data-ttu-id="bdffd-256">Bu işlemin üç adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="bdffd-256">There are three steps to this process:</span></span>

1. <span data-ttu-id="bdffd-257">Varolan belgeye bir tanıtıcı alın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-257">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="bdffd-258">Varolan bildirgeyi yeni bildirimle değiştirerek yeni bir belge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-258">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="bdffd-259">Yeni belgeyi döndürün.</span><span class="sxs-lookup"><span data-stu-id="bdffd-259">Return the new document.</span></span>

<span data-ttu-id="bdffd-260">`MakeConstAsync` Yöntemin sonuna aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-260">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="bdffd-261">Kod düzeltmeniz denemeye hazır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-261">Your code fix is ready to try.</span></span>  <span data-ttu-id="bdffd-262">Çözümleyici projesini Visual Studio'nun ikinci bir örneğinde çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-262">Press F5 to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="bdffd-263">İkinci Visual Studio örneğinde, yeni bir C# Console Application projesi oluşturun ve Main yöntemine sabit değerlerle birlikte birkaç yerel değişken bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-263">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="bdffd-264">Bunların aşağıdaki gibi uyarılar olarak bildirildiğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-264">You'll see that they are reported as warnings as below.</span></span>

![Const uyarılar yapabilir](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="bdffd-266">Çok ilerleme kaydettin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-266">You've made a lot of progress.</span></span> <span data-ttu-id="bdffd-267">Yapılabilecek `const`beyanların altında squiggles var.</span><span class="sxs-lookup"><span data-stu-id="bdffd-267">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="bdffd-268">Ama hala yapılacak işler var.</span><span class="sxs-lookup"><span data-stu-id="bdffd-268">But there is still work to do.</span></span> <span data-ttu-id="bdffd-269">Bu, sonra `const` `j` ve son olarak `k`ile `i`başlayan bildirimleri eklerseniz iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-269">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="bdffd-270">`const` Ancak, değiştiriciyi farklı bir sırada eklerseniz, `k`ile başlayarak , `k` çözümleyiciniz hatalar `const`oluşturur: bildirileme edilemez , sürece `i` ve `j` her ikisi de zaten `const`.</span><span class="sxs-lookup"><span data-stu-id="bdffd-270">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="bdffd-271">Değişkenlerin bildirilip başharfe böldüğü farklı şekillerde ele aldığınızdan emin olmak için daha fazla analiz yapmalısın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-271">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="bdffd-272">Veri odaklı testler oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdffd-272">Build data driven tests</span></span>

<span data-ttu-id="bdffd-273">Çözümleyiciniz ve kod düzeltme çalışmanız, const yapilebilen tek bir bildirimin basit bir durumu üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-273">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="bdffd-274">Bu uygulamanın hata yaptığı çok sayıda olası bildirim bildirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-274">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="bdffd-275">Şablon tarafından yazılmış birim test kitaplığıyla çalışarak bu durumları giderin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-275">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="bdffd-276">Visual Studio'nun ikinci bir kopyasını tekrar tekrar açmaktan çok daha hızlı.</span><span class="sxs-lookup"><span data-stu-id="bdffd-276">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="bdffd-277">Birim test projesinde **MakeConstUnitTests.cs** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-277">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="bdffd-278">Şablon, çözümleyici ve kod düzeltme birimi testi için iki ortak desen izleyen iki test oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="bdffd-278">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="bdffd-279">`TestMethod1`çözümleyicinin tanılamayı bildirmemesini sağlayan bir testin deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-279">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="bdffd-280">`TestMethod2`tanılama yı raporlama ve kod düzeltmesini çalıştırma deseni gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-280">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="bdffd-281">Çözümleyiciniz için hemen hemen her testin kodu bu iki modelden birini izler.</span><span class="sxs-lookup"><span data-stu-id="bdffd-281">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="bdffd-282">İlk adım için, bu testleri veri odaklı testler olarak yeniden çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-282">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="bdffd-283">Daha sonra, farklı test girişlerini temsil edecek yeni dize sabitleri ekleyerek yeni testler oluşturmak kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-283">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="bdffd-284">Verimlilik için ilk adım, iki testi veri odaklı testlere yeniden dahil etmektir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-284">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="bdffd-285">Daha sonra, her yeni test için yalnızca bir çift dize sabiti tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-285">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="bdffd-286">Yeniden düzenleme yaparken, her iki yöntemi de daha iyi adlara yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-286">While your refactoring, rename both methods to better names.</span></span> <span data-ttu-id="bdffd-287">Tanılamanın yapılmadığını garanti eden bu testle değiştirin: `TestMethod1`</span><span class="sxs-lookup"><span data-stu-id="bdffd-287">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="bdffd-288">Tanılamanızın bir uyarıyı tetiklemesi için neden olmaması gereken herhangi bir kod parçası tanımlayarak bu test için yeni bir veri satırı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-288">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="bdffd-289">Kaynak kodu `VerifyCSharpDiagnostic` parçası için tetiklenen tanılama olmadığında bu aşırı geçiş yükü.</span><span class="sxs-lookup"><span data-stu-id="bdffd-289">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="bdffd-290">Ardından, `TestMethod2` tanılamanın yükseltilmesini ve kaynak kod parçası için bir kod düzeltmesinin uygulanmasını sağlayan bu testle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-290">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="bdffd-291">Önceki kod da beklenen tanılama sonucu oluşturur kod için birkaç değişiklik yaptı.</span><span class="sxs-lookup"><span data-stu-id="bdffd-291">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="bdffd-292">`MakeConst` Çözümleyicide kayıtlı genel sabitleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-292">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="bdffd-293">Buna ek olarak, giriş ve sabit kaynak için iki dize sabitleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-293">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="bdffd-294">`UnitTest` Sınıfa aşağıdaki dize sabitlerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-294">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="bdffd-295">Geçtiklerinden emin olmak için bu iki testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-295">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="bdffd-296">**Test** > Visual Studio'da,**Test Windows** > **Test Gezgini'ni**seçerek Test **Gezgini'ni** açın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-296">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span>  <span data-ttu-id="bdffd-297">**Tümlerini Çalıştır** bağlantısına basın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-297">The press the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="bdffd-298">Geçerli bildirimler için testler oluşturma</span><span class="sxs-lookup"><span data-stu-id="bdffd-298">Create tests for valid declarations</span></span>

<span data-ttu-id="bdffd-299">Genel bir kural olarak, çözümleyiciler en az iş yaparak, mümkün olduğunca çabuk çıkmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-299">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="bdffd-300">Visual Studio, kullanıcı kodu edinirken kayıtlı çözümleyicileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-300">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="bdffd-301">Yanıt verme önemli bir gereksinimdir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-301">Responsiveness is a key requirement.</span></span> <span data-ttu-id="bdffd-302">Tanılamanızı yükseltmemesi gereken kod için birkaç test çalışması vardır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-302">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="bdffd-303">Çözümleyiciniz zaten bu testlerden birini işler, bir değişkenin baş harfe döndürüldüğü durumlarda.</span><span class="sxs-lookup"><span data-stu-id="bdffd-303">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="bdffd-304">Bu durumda temsil etmek için testlerinize aşağıdaki dize sabitini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-304">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="bdffd-305">Ardından, aşağıdaki snippet'te gösterildiği gibi bu test için bir veri satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-305">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="bdffd-306">Bu test de geçer.</span><span class="sxs-lookup"><span data-stu-id="bdffd-306">This test passes as well.</span></span> <span data-ttu-id="bdffd-307">Ardından, henüz işlemediğiniz koşullar için sabitler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-307">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="bdffd-308">Zaten const `const`oldukları için zaten olan bildirimler:</span><span class="sxs-lookup"><span data-stu-id="bdffd-308">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="bdffd-309">Kullanılacak bir değer olmadığından, baş harfe aday olmayan bildirimler:</span><span class="sxs-lookup"><span data-stu-id="bdffd-309">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="bdffd-310">Başharfin sabit olmadığı bildirimler, çünkü zaman sabitlerini derleyemezler:</span><span class="sxs-lookup"><span data-stu-id="bdffd-310">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="bdffd-311">C# tek bir bildirim olarak birden çok bildirime izin verdiğinden daha da karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-311">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="bdffd-312">Aşağıdaki test çalışması dize sabitini düşünün:</span><span class="sxs-lookup"><span data-stu-id="bdffd-312">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="bdffd-313">Değişken `i` sabit yapılabilir, ancak değişken `j` yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-313">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="bdffd-314">Bu nedenle, bu bildirim const bir bildirim deılamaz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-314">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="bdffd-315">Tüm `DataRow` bu testler için bildirimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-315">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="bdffd-316">Testlerinizi yeniden çalıştırın ve bu yeni test çalışmalarının başarısız olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-316">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="bdffd-317">Doğru bildirimleri yoksaymak için çözümleyicinizi güncelleştirin</span><span class="sxs-lookup"><span data-stu-id="bdffd-317">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="bdffd-318">Bu koşullarla eşleşen kodu filtrelemek `AnalyzeNode` için çözümleyicinizin yönteminde bazı geliştirmeler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-318">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="bdffd-319">Bunların hepsi ilgili koşullardır, bu nedenle benzer değişiklikler tüm bu koşulları düzeltecektir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-319">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="bdffd-320">Aşağıdaki değişiklikleri `AnalyzeNode`yapın:</span><span class="sxs-lookup"><span data-stu-id="bdffd-320">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="bdffd-321">Anlamsal analiziniz tek bir değişken bildirimini inceledi.</span><span class="sxs-lookup"><span data-stu-id="bdffd-321">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="bdffd-322">Bu kodun, aynı `foreach` ifadede bildirilen tüm değişkenleri inceleyen bir döngüde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-322">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="bdffd-323">Bildirilen her değişkenin bir baş harfe sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-323">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="bdffd-324">Bildirilen her değişkenin başharfi derleme zamanı sabiti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-324">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="bdffd-325">Yönteminizde, orijinal anlamsal analizi değiştirin: `AnalyzeNode`</span><span class="sxs-lookup"><span data-stu-id="bdffd-325">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="bdffd-326">aşağıdaki kod parçacığı ile:</span><span class="sxs-lookup"><span data-stu-id="bdffd-326">with the following code snippet:</span></span>

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

<span data-ttu-id="bdffd-327">İlk `foreach` döngü, her değişken bildirimini sözdizimanalizi ni kullanarak inceler.</span><span class="sxs-lookup"><span data-stu-id="bdffd-327">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="bdffd-328">İlk çek, değişkenin bir baş harfe sahip olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="bdffd-328">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="bdffd-329">İkinci çek, baş harfin sabit olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="bdffd-329">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="bdffd-330">İkinci döngü orijinal semantik analize sahiptir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-330">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="bdffd-331">Anlamsal denetimler, performans üzerinde daha büyük bir etkiye sahip olduğundan ayrı bir döngüdedir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-331">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="bdffd-332">Testlerinizi tekrar çalıştırın ve hepsinin geçtiğini göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-332">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="bdffd-333">Son cila ekle</span><span class="sxs-lookup"><span data-stu-id="bdffd-333">Add the final polish</span></span>

<span data-ttu-id="bdffd-334">Neredeyse bitti.</span><span class="sxs-lookup"><span data-stu-id="bdffd-334">You're almost done.</span></span> <span data-ttu-id="bdffd-335">Çözümleyicinizin işlemesi için birkaç koşul daha vardır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-335">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="bdffd-336">Kullanıcı kod yazarken Visual Studio çözümleyicileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-336">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="bdffd-337">Çözümleyiciniz genellikle derlemeyen kod için çağrılacak tır.</span><span class="sxs-lookup"><span data-stu-id="bdffd-337">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="bdffd-338">Tanı çözümleyicinin `AnalyzeNode` yöntemi, sabit değerin değişken türüne dönüştürülüp dönüştürülemeyeceğini kontrol etmez.</span><span class="sxs-lookup"><span data-stu-id="bdffd-338">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="bdffd-339">Yani, geçerli uygulama mutlu int i = "abc" gibi yanlış bir bildirimi yerel bir sabit dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bdffd-339">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="bdffd-340">Bu durum için bir kaynak dize sabiti ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-340">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="bdffd-341">Ayrıca, başvuru türleri düzgün şekilde işlenmez.</span><span class="sxs-lookup"><span data-stu-id="bdffd-341">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="bdffd-342">Bir başvuru türü için izin `null`verilen tek sabit <xref:System.String?displayProperty=nameWithType>değer, dize literals sağlayan bu durumda dışında.</span><span class="sxs-lookup"><span data-stu-id="bdffd-342">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="bdffd-343">Başka bir `const string s = "abc"` deyişle, yasal, ama `const object s = "abc"` değildir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-343">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="bdffd-344">Bu kod snippet bu koşulu doğrular:</span><span class="sxs-lookup"><span data-stu-id="bdffd-344">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="bdffd-345">Ayrıntılı olması için, bir dize için sabit bir bildirim oluşturabileceğinizden emin olmak için başka bir sınayı eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-345">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="bdffd-346">Aşağıdaki parçacık hem tanılamayı yükselten kodu hem de düzeltme uygulandıktan sonra kodu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="bdffd-346">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="bdffd-347">Son olarak, bir değişken `var` anahtar kelimeyle birlikte bildirilirse, kod `const var` düzeltmesi yanlış bir şey yapar ve C# dili tarafından desteklenmeyen bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdffd-347">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="bdffd-348">Bu hatayı düzeltmek için kod düzeltmesinin anahtar kelimeyi `var` çıkarılan türün adı ile değiştirmesi gerekir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-348">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="bdffd-349">Bu değişiklikler, her iki test için veri satırı bildirimlerini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-349">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="bdffd-350">Aşağıdaki kod tüm veri satırı öznitelikleri ile bu testleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-350">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="bdffd-351">Neyse ki, yukarıdaki hataların hepsi sadece öğrendim aynı teknikleri kullanarak ele alınabilir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-351">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="bdffd-352">İlk hatayı düzeltmek için, ilk **DiagnosticAnalyzer.cs** açın ve her bir yerel bildirimin başharflerinin işaretlendiği foreach döngüyü bulun ve sabit değerlerle atandıklarından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-352">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="bdffd-353">Her biri için ilk döngüden hemen _önce,_ yerel bildirimin bildirilen türü hakkında ayrıntılı bilgi almak için arayın: `context.SemanticModel.GetTypeInfo()`</span><span class="sxs-lookup"><span data-stu-id="bdffd-353">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="bdffd-354">Daha sonra, `foreach` döngünüzün içinde, değişken türüne dönüştürülebilen olduğundan emin olmak için her bir baş harfe işaret edin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-354">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="bdffd-355">Baş harfin sabit olduğundan emin olduktan sonra aşağıdaki çeki ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-355">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="bdffd-356">Bir sonraki değişiklik sonuncusu üzerine inşa edin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-356">The next change builds upon the last one.</span></span> <span data-ttu-id="bdffd-357">İlk foreach döngükapanış kıvırcık ayraç önce, sabit bir dize veya null olduğunda yerel bildirimin türünü kontrol etmek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-357">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="bdffd-358">Var' anahtar sözcüğünün doğru tür adı ile değiştirilmesi için kod düzeltme sağlayıcınıza biraz daha kod yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-358">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="bdffd-359">**CodeFixProvider.cs**dön.</span><span class="sxs-lookup"><span data-stu-id="bdffd-359">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="bdffd-360">Ekleyeceğiniz kod aşağıdaki adımları yapar:</span><span class="sxs-lookup"><span data-stu-id="bdffd-360">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="bdffd-361">Bildirimin bir `var` bildirim olup olmadığını ve aşağıdakileri yapıp olmadığını denetleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-361">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="bdffd-362">Çıkarılan tür için yeni bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-362">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="bdffd-363">Tür bildiriminin takma ad olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-363">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="bdffd-364">Eğer öyleyse, beyan `const var`etmek yasal.</span><span class="sxs-lookup"><span data-stu-id="bdffd-364">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="bdffd-365">Bu `var` programda bir tür adı olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-365">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="bdffd-366">(Eğer öyleyse, `const var` yasal).</span><span class="sxs-lookup"><span data-stu-id="bdffd-366">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="bdffd-367">Tam tür adını basitleştirin</span><span class="sxs-lookup"><span data-stu-id="bdffd-367">Simplify the full type name</span></span>

<span data-ttu-id="bdffd-368">Kulağa çok fazla kod gibi geliyor.</span><span class="sxs-lookup"><span data-stu-id="bdffd-368">That sounds like a lot of code.</span></span> <span data-ttu-id="bdffd-369">Değil.</span><span class="sxs-lookup"><span data-stu-id="bdffd-369">It's not.</span></span> <span data-ttu-id="bdffd-370">Bildiren ve başharfe gelen `newLocal` satırı aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-370">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="bdffd-371">Bu hemen başlatılmasından `newModifiers`sonra gider:</span><span class="sxs-lookup"><span data-stu-id="bdffd-371">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="bdffd-372">Türü kullanmak için bir `using` deyim eklemeniz <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> gerekir:</span><span class="sxs-lookup"><span data-stu-id="bdffd-372">You'll need to add one `using` statement to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="bdffd-373">Testlerinizi çalıştırın ve hepsi geçsin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-373">Run your tests, and they should all pass.</span></span> <span data-ttu-id="bdffd-374">Bitmiş analizörünüzü çalıştırarak kendinizi tebrik edin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-374">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="bdffd-375">Analizör projesini, Roslyn Preview uzantısı yüklü Visual Studio'nun ikinci bir örneğinde çalıştırmak için Ctrl+F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-375">Press Ctrl+F5 to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="bdffd-376">İkinci Visual Studio örneğinde, yeni bir C# `int x = "abc";` Console Application projesi oluşturun ve Ana yönteme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-376">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="bdffd-377">İlk hata düzeltmesi sayesinde, bu yerel değişken bildirimi için hiçbir uyarı bildirilmelidir (beklendiği gibi bir derleyici hatası olsa da).</span><span class="sxs-lookup"><span data-stu-id="bdffd-377">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="bdffd-378">Ardından, `object s = "abc";` Ana yönteme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-378">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="bdffd-379">İkinci hata düzeltmesi nedeniyle hiçbir uyarı bildirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="bdffd-379">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="bdffd-380">Son olarak, anahtar kelimeyi `var` kullanan başka bir yerel değişken ekleyin.</span><span class="sxs-lookup"><span data-stu-id="bdffd-380">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="bdffd-381">Bir uyarının rapor olduğunu ve sola doğru bir öneri nin görüntülediğini görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-381">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="bdffd-382">Düzenleyiciyi kıvrımlı altı çizili üzerine taşıyın ve Ctrl+ tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-382">Move the editor caret over the squiggly underline and press Ctrl+.</span></span> <span data-ttu-id="bdffd-383">önerilen kod düzeltmesini görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="bdffd-383">to display the suggested code fix.</span></span> <span data-ttu-id="bdffd-384">Kod düzeltmenizi seçtikten sonra, var' anahtar kelimesinin artık doğru şekilde işleneceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="bdffd-384">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="bdffd-385">Son olarak, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdffd-385">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="bdffd-386">Bu değişikliklerden sonra, yalnızca ilk iki değişkende kırmızı dalgalı squiggles olsun.</span><span class="sxs-lookup"><span data-stu-id="bdffd-386">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="bdffd-387">Her `const` ikisine `i` de ekleyin ve `j`, `k` şimdi olabilir, `const`çünkü yeni bir uyarı almak .</span><span class="sxs-lookup"><span data-stu-id="bdffd-387">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="bdffd-388">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="bdffd-388">Congratulations!</span></span> <span data-ttu-id="bdffd-389">Bir sorunu algılamak için anında kod çözümlemesi gerçekleştiren ve düzeltmek için hızlı bir düzeltme sağlayan ilk .NET Derleyici Platformu uzantınızı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-389">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="bdffd-390">Yol boyunca, .NET Derleyici Platformu SDK'nın (Roslyn API'leri) bir parçası olan kod API'lerinin çoğunu öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-390">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="bdffd-391">GitHub depomuzda [tamamlanan örnekle](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) karşı çalışmanızı kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdffd-391">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="bdffd-392">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="bdffd-392">Other resources</span></span>

- [<span data-ttu-id="bdffd-393">Sözdizimi analizine başlayın</span><span class="sxs-lookup"><span data-stu-id="bdffd-393">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="bdffd-394">Anlamsal analize başlayın</span><span class="sxs-lookup"><span data-stu-id="bdffd-394">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
