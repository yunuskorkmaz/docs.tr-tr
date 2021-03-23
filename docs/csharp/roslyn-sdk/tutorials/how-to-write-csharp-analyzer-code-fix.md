---
title: 'Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma'
description: Bu öğretici, .NET derleyici SDK 'sını (Roslyn API 'Ler) kullanarak bir çözümleyici ve kod düzeltmesini oluşturmak için adım adım yönergeler sağlar.
ms.date: 03/02/2021
ms.custom: mvc
ms.openlocfilehash: ca586874d79e9de5f293e548b1cfd08c694d3479
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104876168"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="b1d33-103">Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma</span><span class="sxs-lookup"><span data-stu-id="b1d33-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="b1d33-104">.NET Compiler Platform SDK 'Sı, C# veya Visual Basic kodunu hedefleyen özel Tanılamalar (çözümleyiciler), kod düzeltmeleri, kod yeniden düzenleme ve tanılama Gizleyiciler oluşturmak için ihtiyacınız olan araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-104">The .NET Compiler Platform SDK provides the tools you need to create custom diagnostics (analyzers), code fixes, code refactoring, and diagnostic suppressors that target C# or Visual Basic code.</span></span> <span data-ttu-id="b1d33-105">**Çözümleyici** , kuralınızın ihlallerini algılayan kod içerir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-105">An **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="b1d33-106">**Kod düzeltmenizi** ihlalin giderdiği kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="b1d33-107">Uyguladığınız kurallar, kod yapısından, adlandırma kurallarına ve daha fazlasına yönelik kodlama stiline kadar herhangi bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="b1d33-108">.NET Compiler Platform, geliştiricilerin kod yazmakta olduğu ve kodu düzeltmek için tüm Visual Studio Kullanıcı arabirimi özelliklerinin yanı sıra kodu çözmede, Visual Studio Hata Listesi, "ampul" önerilerini oluşturarak ve önerilen düzeltmelerin zengin önizlemesini göstererek, analiz çalıştırma çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="b1d33-109">Bu öğreticide, bir **çözümleyici** oluşturmayı ve Roslyn API 'lerini kullanarak bir **kod düzeltmesini** inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="b1d33-110">Çözümleyici, kaynak kodu analizini gerçekleştirmek ve kullanıcıya bir sorun bildirmek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="b1d33-111">İsteğe bağlı olarak, kullanıcının kaynak kodunda yapılan bir değişikliği göstermek için bir kod onarımı çözümleyici ile ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-111">Optionally, a code fix can be associated with the analyzer to represent a modification to the user's source code.</span></span> <span data-ttu-id="b1d33-112">Bu öğreticide, değiştirici kullanılarak bildirilebilecek ancak olmayan yerel değişken bildirimlerini bulan bir çözümleyici oluşturulur `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="b1d33-113">Eşlik eden kod düzeltilmesi, değiştiriciyi eklemek için bu bildirimleri değiştirir `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1d33-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b1d33-114">Prerequisites</span></span>

- <span data-ttu-id="b1d33-115">[Visual Studio 2019](https://www.visualstudio.com/downloads) sürüm 16,8 veya üzeri</span><span class="sxs-lookup"><span data-stu-id="b1d33-115">[Visual Studio 2019](https://www.visualstudio.com/downloads) version 16.8 or later</span></span>

<span data-ttu-id="b1d33-116">**.Net Compiler Platform SDK 'sını** Visual Studio yükleyicisi aracılığıyla yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b1d33-116">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="b1d33-117">Çözümleyicinizi oluşturmak ve doğrulamak için birkaç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="b1d33-117">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="b1d33-118">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-118">Create the solution.</span></span>
1. <span data-ttu-id="b1d33-119">Çözümleyici adını ve açıklamasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-119">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="b1d33-120">Rapor çözümleyici uyarıları ve önerileri.</span><span class="sxs-lookup"><span data-stu-id="b1d33-120">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="b1d33-121">Önerileri kabul etmek için kod düzeltmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-121">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="b1d33-122">Birim testler aracılığıyla Analizi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="b1d33-122">Improve the analysis through unit tests.</span></span>

## <a name="create-the-solution"></a><span data-ttu-id="b1d33-123">Çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1d33-123">Create the solution</span></span>

- <span data-ttu-id="b1d33-124">Visual Studio 'da yeni proje iletişim kutusunu göstermek için **dosya > yeni > proje..** . öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-124">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="b1d33-125">**Visual C# > genişletilebilirlik** altında, **kod düzeltmesine sahip çözümleyici 'yi (.NET Standard)** seçin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-125">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="b1d33-126">Projenizi "**Makeconst**" olarak adlandırın ve Tamam ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-126">Name your project "**MakeConst**" and click OK.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="b1d33-127">Çözümleyici şablonunu keşfet</span><span class="sxs-lookup"><span data-stu-id="b1d33-127">Explore the analyzer template</span></span>

<span data-ttu-id="b1d33-128">Kod düzelme şablonuyla çözümleyici, beş proje oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b1d33-128">The analyzer with code fix template creates five projects:</span></span>

- <span data-ttu-id="b1d33-129">Çözümleyicisi içeren **Makeconst**.</span><span class="sxs-lookup"><span data-stu-id="b1d33-129">**MakeConst**, which contains the analyzer.</span></span>
- <span data-ttu-id="b1d33-130">Kod düzeltmesini içeren **Makeconst. Codedüzeltmeleriyle**.</span><span class="sxs-lookup"><span data-stu-id="b1d33-130">**MakeConst.CodeFixes**, which contains the code fix.</span></span>
- <span data-ttu-id="b1d33-131">Çözümleyici ve kod düzeltilmesi için NuGet paketini üretmek için kullanılan **Makeconst. Package**.</span><span class="sxs-lookup"><span data-stu-id="b1d33-131">**MakeConst.Package**, which is used to produce NuGet package for the analyzer and code fix.</span></span>
- <span data-ttu-id="b1d33-132">Bir birim testi projesi olan **Makeconst. test**.</span><span class="sxs-lookup"><span data-stu-id="b1d33-132">**MakeConst.Test**, which is a unit test project.</span></span>
- <span data-ttu-id="b1d33-133">Yeni çözümleyicinizi yükleyen ikinci bir Visual Studio örneğini başlatan varsayılan başlangıç projesi olan **Makeconst. vsix**.</span><span class="sxs-lookup"><span data-stu-id="b1d33-133">**MakeConst.Vsix**, which is the default startup project that starts a second instance of Visual Studio that has loaded your new analyzer.</span></span> <span data-ttu-id="b1d33-134">VSıX projesini başlatmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-134">Press <kbd>F5</kbd> to start the VSIX project.</span></span>

> [!TIP]
> <span data-ttu-id="b1d33-135">Çözümleyicinizi çalıştırdığınızda, Visual Studio 'nun ikinci bir kopyasını başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-135">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="b1d33-136">Bu ikinci kopya ayarları depolamak için farklı bir kayıt defteri kovanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-136">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="b1d33-137">Bu, Visual Studio 'nun iki kopyasında görsel ayarları ayırt etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-137">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="b1d33-138">Visual Studio 'nun deneysel çalıştırması için farklı bir tema seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-138">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="b1d33-139">Ayrıca, Visual Studio 'nun deneysel çalıştırmasını kullanarak ayarlarınızı dolaşıyor veya Visual Studio hesabınızda oturum açmayın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-139">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="b1d33-140">Bu, ayarları farklı tutar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-140">That keeps the settings different.</span></span>

<span data-ttu-id="b1d33-141">Az önce başlattığınız ikinci Visual Studio örneğinde yeni bir C# konsol uygulaması projesi oluşturun (herhangi bir hedef çerçeve, kaynak düzeyinde çalışır.) Simgenin üzerine dalgalı alt çizgiyle gelin ve bir çözümleyici tarafından sunulan uyarı metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-141">In the second Visual Studio instance that you just started, create a new C# Console Application project (any target framework will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="b1d33-142">Şablon, aşağıdaki şekilde gösterildiği gibi tür adında küçük harfler içeren her tür bildiriminde uyarı raporlayan bir çözümleyici oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b1d33-142">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Çözümleyici raporlama uyarısı](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="b1d33-144">Şablon Ayrıca, küçük harf karakter içeren herhangi bir tür adını tüm büyük harflere değiştiren bir kod düzeltmesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-144">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="b1d33-145">Önerilen değişiklikleri görmek için uyarıyla birlikte görüntülenecek ampule tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-145">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="b1d33-146">Önerilen değişiklikler kabul edildiğinde, tür adı ve çözümdeki bu türe yapılan tüm başvurular güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-146">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="b1d33-147">İlk çözümleyici 'yi eylemde gördüğünüze göre, ikinci Visual Studio örneğini kapatın ve çözümleyici projenize geri dönün.</span><span class="sxs-lookup"><span data-stu-id="b1d33-147">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="b1d33-148">Visual Studio 'nun ikinci bir kopyasını başlatmanız ve çözümleyicinizdeki her değişikliği test etmek için yeni kod oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b1d33-148">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="b1d33-149">Şablon sizin için bir birim testi projesi de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-149">The template also creates a unit test project for you.</span></span> <span data-ttu-id="b1d33-150">Bu proje iki test içerir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-150">That project contains two tests.</span></span> <span data-ttu-id="b1d33-151">`TestMethod1` Bir tanılamayı tetiklemeden kodu çözümleyen testin tipik biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-151">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="b1d33-152">`TestMethod2` Bir tanılamayı tetikleyen testin biçimini gösterir ve ardından önerilen bir kod düzeltmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="b1d33-152">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="b1d33-153">Çözümleyicinizi ve kod düzeltmesini oluştururken, çalışmanızı doğrulamak üzere farklı kod yapıları için testler yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b1d33-153">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="b1d33-154">Çözümleyiciler için birim testleri, Visual Studio ile etkileşimli olarak test edilmesine kıyasla çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-154">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="b1d33-155">Çözümleyici birim testleri, hangi kod yapılarının çözümleyicinizi tetikleyemediğini bildiğiniz ve bu harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-155">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="b1d33-156">Visual Studio 'nun başka bir kopyasına çözümleyicinizi yüklemek, henüz düşünmemiş olan yapıları keşfetmeye ve bulmaya yönelik harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-156">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

<span data-ttu-id="b1d33-157">Bu öğreticide, kullanıcıya, yerel sabitlere dönüştürülebilen herhangi bir yerel değişken bildirimini raporlayan bir çözümleyici yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="b1d33-157">In this tutorial, you write an analyzer that reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="b1d33-158">Örneğin, aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b1d33-158">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b1d33-159">Yukarıdaki kodda `x` sabit bir değer atanır ve hiçbir şekilde değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="b1d33-159">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="b1d33-160">Değiştirici kullanılarak bildirilebilecek `const` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-160">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b1d33-161">Bir değişkenin sabit bir şekilde yapılıp yapılmayacağını belirleme, değişken için sözdizimi analizi, başlatıcı ifadesinin sabit Analizi ve değişkenin hiçbir şekilde yazılmaması için veri akışı analizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-161">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="b1d33-162">.NET Compiler Platform, bu çözümlemenin daha kolay hale getirebilmesini sağlayan API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-162">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="b1d33-163">Çözümleyici kayıtları oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1d33-163">Create analyzer registrations</span></span>

<span data-ttu-id="b1d33-164">Şablon, `DiagnosticAnalyzer` *MakeConstAnalyzer. cs* dosyasında başlangıç sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-164">The template creates the initial `DiagnosticAnalyzer` class, in the *MakeConstAnalyzer.cs* file.</span></span> <span data-ttu-id="b1d33-165">Bu ilk çözümleyici, her çözümleyici 'nin iki önemli özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-165">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="b1d33-166">Her Tanılama Çözümleyicisi `[DiagnosticAnalyzer]` , üzerinde çalıştığı dili açıklayan bir öznitelik sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-166">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="b1d33-167">Her Tanılama Çözümleyicisi sınıfından (doğrudan veya dolaylı olarak) türemelidir <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> .</span><span class="sxs-lookup"><span data-stu-id="b1d33-167">Every diagnostic analyzer must derive (directly or indirectly) from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="b1d33-168">Şablon, herhangi bir çözümleyici 'nin parçası olan temel özellikleri de gösterir:</span><span class="sxs-lookup"><span data-stu-id="b1d33-168">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="b1d33-169">Kaydetme eylemleri.</span><span class="sxs-lookup"><span data-stu-id="b1d33-169">Register actions.</span></span> <span data-ttu-id="b1d33-170">Eylemler, çözümleyicinizi ihlalleri için kodu incelemek üzere tetiklemesi gereken kod değişikliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1d33-170">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="b1d33-171">Visual Studio, kayıtlı bir eylemle eşleşen kod düzenlemeleri algıladığında, çözümleyici 'nin kayıtlı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-171">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="b1d33-172">Tanılama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-172">Create diagnostics.</span></span> <span data-ttu-id="b1d33-173">Çözümleyicisi bir ihlal algıladığında, bu, ihlalin kullanıcısına bildirimde bulunan Visual Studio 'Nun kullandığı bir tanılama nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-173">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="b1d33-174">Eylemini geçersiz kılmanızda kaydedebilirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b1d33-174">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b1d33-175">Bu öğreticide, yerel bildirimleri arayan **sözdizimi düğümlerini** ziyaret edeceğiz ve hangilerinin sabit değerlere sahip olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-175">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="b1d33-176">Bir bildirim sabitlenebilir, çözümleyici bir tanılama oluşturup rapor eder.</span><span class="sxs-lookup"><span data-stu-id="b1d33-176">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="b1d33-177">İlk adım, kayıt sabitlerini ve yöntemini güncelleştirmek ve `Initialize` Bu sabitler "const yap" çözümleyicisini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-177">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="b1d33-178">Dize sabitlerinin çoğu dize kaynak dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-178">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="b1d33-179">Daha kolay yerelleştirme için bu uygulamayı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-179">You should follow that practice for easier localization.</span></span> <span data-ttu-id="b1d33-180">**Makeconst** çözümleyici projesi için *Resources. resx* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-180">Open the *Resources.resx* file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="b1d33-181">Bu, kaynak düzenleyicisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="b1d33-181">This displays the resource editor.</span></span> <span data-ttu-id="b1d33-182">Dize kaynaklarını aşağıdaki gibi güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-182">Update the string resources as follows:</span></span>

- <span data-ttu-id="b1d33-183">`AnalyzerDescription`"" Olarak değiştirin :::no-loc text="Variables that are not modified should be made constants."::: .</span><span class="sxs-lookup"><span data-stu-id="b1d33-183">Change `AnalyzerDescription` to ":::no-loc text="Variables that are not modified should be made constants.":::".</span></span>
- <span data-ttu-id="b1d33-184">`AnalyzerMessageFormat`"" Olarak değiştirin :::no-loc text="Variable '{0}' can be made constant"::: .</span><span class="sxs-lookup"><span data-stu-id="b1d33-184">Change `AnalyzerMessageFormat` to ":::no-loc text="Variable '{0}' can be made constant":::".</span></span>
- <span data-ttu-id="b1d33-185">`AnalyzerTitle`"Olarak değiştirin :::no-loc text="Variable can be made constant"::: .</span><span class="sxs-lookup"><span data-stu-id="b1d33-185">Change `AnalyzerTitle` to ":::no-loc text="Variable can be made constant":::.</span></span>

<span data-ttu-id="b1d33-186">İşiniz bittiğinde, kaynak Düzenleyicisi aşağıdaki şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="b1d33-186">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Dize kaynaklarını Güncelleştir](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="b1d33-188">Geri kalan değişiklikler çözümleyici dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-188">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="b1d33-189">Visual Studio 'da *MakeConstAnalyzer. cs* ' i açın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-189">Open *MakeConstAnalyzer.cs* in Visual Studio.</span></span> <span data-ttu-id="b1d33-190">Semboller üzerinde çalışan bir eylemden, söz dizimi üzerinde davranan bir eylemi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-190">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="b1d33-191">`MakeConstAnalyzerAnalyzer.Initialize`Yönteminde, simgeleri üzerinde eylemi kaydeden satırı bulun:</span><span class="sxs-lookup"><span data-stu-id="b1d33-191">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="b1d33-192">Aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-192">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="b1d33-193">Bu değişiklikten sonra `AnalyzeSymbol` yöntemini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-193">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="b1d33-194">Bu çözümleyici <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> , deyimleri inceler <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b1d33-194">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="b1d33-195">`AnalyzeNode`Altında Red dalgalı çizgiler olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-195">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="b1d33-196">Az önce eklediğiniz kod `AnalyzeNode` bildirilmemiş bir yönteme başvurur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-196">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="b1d33-197">Aşağıdaki kodu kullanarak bu yöntemi bildirin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-197">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="b1d33-198">`Category` :::no-loc text="Usage"::: Aşağıdaki kodda gösterildiği gibi, *MakeConstAnalyzer. cs* içinde "" olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-198">Change the `Category` to ":::no-loc text="Usage":::" in *MakeConstAnalyzer.cs* as shown in the following code:</span></span>

[!code-csharp[Category constant](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#Category  "Change category to Usage")]

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="b1d33-199">Const olabilecek yerel bildirimleri bul</span><span class="sxs-lookup"><span data-stu-id="b1d33-199">Find local declarations that could be const</span></span>

<span data-ttu-id="b1d33-200">Yöntemin ilk sürümünü yazmak zaman `AnalyzeNode` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-200">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="b1d33-201">Bu, `const` Aşağıdaki kod gibi olabilecek, ancak olmayan tek bir yerel bildirime bakmalıdır:</span><span class="sxs-lookup"><span data-stu-id="b1d33-201">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b1d33-202">İlk adım, yerel bildirimleri bulledir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-202">The first step is to find local declarations.</span></span> <span data-ttu-id="b1d33-203">Aşağıdaki kodu `AnalyzeNode` *MakeConstAnalyzer. cs* içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-203">Add the following code to `AnalyzeNode` in *MakeConstAnalyzer.cs*:</span></span>

[!code-csharp[localDeclaration variable](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#LocalDeclaration  "Add localDeclaration variable")]

<span data-ttu-id="b1d33-204">Bu atama, çözümleyici yerel bildirimlerinizde değişiklikler ve yalnızca yerel bildirimler için kaydedildiği için her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-204">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="b1d33-205">Başka hiçbir düğüm türü, yönteminiz için bir çağrı tetiklemiyor `AnalyzeNode` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-205">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="b1d33-206">Sonra, herhangi bir değiştiricinin bildirimini kontrol edin `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-206">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="b1d33-207">Bunları bulursanız anında geri dönün.</span><span class="sxs-lookup"><span data-stu-id="b1d33-207">If you find them, return immediately.</span></span> <span data-ttu-id="b1d33-208">Aşağıdaki kod, `const` Yerel bildirimde herhangi bir değiştirici arar:</span><span class="sxs-lookup"><span data-stu-id="b1d33-208">The following code looks for any `const` modifiers on the local declaration:</span></span>

[!code-csharp[bail-out on const keyword](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#BailOutOnConst  "bail-out on const keyword")]

<span data-ttu-id="b1d33-209">Son olarak, değişkenin olup olmadığını kontrol etmeniz gerekir `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-209">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="b1d33-210">Bu, başlatıldıktan sonra hiçbir şekilde atanmadığından emin olmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-210">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="b1d33-211">Kullanarak bazı semantik analizler gerçekleştirirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> .</span><span class="sxs-lookup"><span data-stu-id="b1d33-211">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="b1d33-212">`context`Yerel değişken bildiriminin yapılıp yapılmayacağını anlamak için bağımsız değişkenini kullanırsınız `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-212">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="b1d33-213"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>Tek bir kaynak dosyasındaki tüm anlam bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1d33-213">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="b1d33-214">[Anlam modellerini](../work-with-semantics.md)içeren makalede daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-214">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="b1d33-215"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>' Yi, yerel bildirim deyimindeki veri akışı analizini gerçekleştirmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b1d33-215">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="b1d33-216">Ardından, bu veri akışı analizinin sonuçlarını kullanarak yerel değişkenin başka bir yerde yeni bir değerle yazılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-216">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="b1d33-217"><xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A>Değişkenini almak için genişletme yöntemini çağırın <xref:Microsoft.CodeAnalysis.ILocalSymbol> ve <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> veri akışı analizinin koleksiyonuna dahil olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-217">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="b1d33-218">Yönteminin sonuna aşağıdaki kodu ekleyin `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-218">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
VariableDeclaratorSyntax variable = localDeclaration.Declaration.Variables.Single();
ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="b1d33-219">Yeni eklenen kod, değişkenin değiştirilmediğinden emin olur ve bu nedenle yapılabilir `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-219">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="b1d33-220">Tanılamayı yükseltme zamanı.</span><span class="sxs-lookup"><span data-stu-id="b1d33-220">It's time to raise the diagnostic.</span></span> <span data-ttu-id="b1d33-221">Aşağıdaki kodu içine son satır olarak ekleyin `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-221">Add the following code as the last line in `AnalyzeNode`:</span></span>

[!code-csharp[Call ReportDiagnostic](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#ReportDiagnostic  "Call ReportDiagnostic")]

<span data-ttu-id="b1d33-222"><kbd>F5</kbd> 'e basarak çözümleyicinizi çalıştırmak için ilerleme durumunu kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-222">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="b1d33-223">Daha önce oluşturduğunuz konsol uygulamasını yükleyebilir ve sonra şu test kodunu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b1d33-223">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b1d33-224">Ampul görünmelidir ve çözümleyici 'niz bir tanılama raporlemelidir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-224">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="b1d33-225">Ancak ampul, şablon tarafından oluşturulan kod düzeltmesini hala kullanır ve bunun büyük bir durum oluşturabileceklerini söyler.</span><span class="sxs-lookup"><span data-stu-id="b1d33-225">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="b1d33-226">Sonraki bölümde, kod düzeltmesinin nasıl yazılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-226">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="b1d33-227">Kod düzeltmesini yazın</span><span class="sxs-lookup"><span data-stu-id="b1d33-227">Write the code fix</span></span>

<span data-ttu-id="b1d33-228">Bir çözümleyici, bir veya daha fazla kod düzeltmesi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-228">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="b1d33-229">Kod onarımı, bildirilen sorunu ele alan bir düzenleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b1d33-229">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="b1d33-230">Oluşturduğunuz çözümleyici için, const anahtar sözcüğünü ekleyen bir kod düzeltmesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b1d33-230">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```diff
- int x = 0;
+ const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="b1d33-231">Kullanıcı onu düzenleyicide ampul kullanıcı arabiriminden seçer ve Visual Studio kodu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-231">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="b1d33-232">*Codefixresources. resx* dosyasını açın ve `CodeFixTitle` "" olarak değiştirin :::no-loc text="Make constant"::: .</span><span class="sxs-lookup"><span data-stu-id="b1d33-232">Open *CodeFixResources.resx* file and change `CodeFixTitle` to ":::no-loc text="Make constant":::".</span></span>

<span data-ttu-id="b1d33-233">Şablon tarafından eklenen *MakeConstCodeFixProvider. cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-233">Open the *MakeConstCodeFixProvider.cs* file added by the template.</span></span> <span data-ttu-id="b1d33-234">Bu kod onarımı, tanılama çözümleyici 'niz tarafından üretilen tanılama KIMLIĞI 'ne zaten kablolu, ancak doğru kod dönüşümünü uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="b1d33-234">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span>

<span data-ttu-id="b1d33-235">Sonra, yöntemini silin `MakeUppercaseAsync` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-235">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="b1d33-236">Artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-236">It no longer applies.</span></span>

<span data-ttu-id="b1d33-237">Tüm kod onarma sağlayıcıları öğesinden türetilir <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> .</span><span class="sxs-lookup"><span data-stu-id="b1d33-237">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="b1d33-238">Bunlar, <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmelerini raporlamak için tüm geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-238">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="b1d33-239">' De `RegisterCodeFixesAsync` , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tanı ile eşleştirmek için Aradığınız üst düğüm türünü bir olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-239">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="b1d33-240">Sonra, bir kod düzeltmesini kaydetmek için son satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-240">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="b1d33-241">Bu değişiklik, değiştiricinin mevcut bir bildirime eklenmesinin sonucu olan yeni bir belge oluşturur `const` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-241">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="b1d33-242">Simgenin üzerine yeni eklediğiniz kodda kırmızı dalgalı çizgiler fark edeceksiniz `MakeConstAsync` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-242">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="b1d33-243">`MakeConstAsync`Aşağıdaki kodu beğenmek için bir bildirim ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-243">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private static async Task<Document> MakeConstAsync(Document document,
    LocalDeclarationStatementSyntax localDeclaration,
    CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="b1d33-244">Yeni `MakeConstAsync` yönteminiz, <xref:Microsoft.CodeAnalysis.Document> kullanıcının kaynak dosyasını temsil eden yeni bir bildirim içeren yeni bir öğesine dönüştürür <xref:Microsoft.CodeAnalysis.Document> `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-244">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="b1d33-245">`const`Bildirim ifadesinin önüne eklemek için yeni bir anahtar sözcük belirteci oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-245">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="b1d33-246">Önce bildirim bildiriminin ilk belirtecinden önde gelen her türlü boşluğu kaldırmak ve belirtece eklemek konusunda dikkatli olun `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-246">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="b1d33-247">`MakeConstAsync` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-247">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="b1d33-248">Ardından, `const` aşağıdaki kodu kullanarak belirteci bildirime ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-248">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
SyntaxTokenList newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
LocalDeclarationStatementSyntax newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="b1d33-249">Ardından, yeni bildirimi C# biçimlendirme kurallarıyla eşleşecek şekilde biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-249">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="b1d33-250">Değişikliklerinizi varolan kodla eşleşecek şekilde biçimlendirmek daha iyi bir deneyim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-250">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="b1d33-251">Mevcut koddan hemen sonra aşağıdaki ifadeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-251">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="b1d33-252">Bu kod için yeni bir ad alanı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-252">A new namespace is required for this code.</span></span> <span data-ttu-id="b1d33-253">Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-253">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="b1d33-254">Son adım, düzenlemenizi yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-254">The final step is to make your edit.</span></span> <span data-ttu-id="b1d33-255">Bu işlemin üç adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="b1d33-255">There are three steps to this process:</span></span>

1. <span data-ttu-id="b1d33-256">Mevcut belgeye yönelik bir tanıtıcı alın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-256">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="b1d33-257">Mevcut bildirimi yeni bildirimle değiştirerek yeni bir belge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-257">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="b1d33-258">Yeni belgeyi döndür.</span><span class="sxs-lookup"><span data-stu-id="b1d33-258">Return the new document.</span></span>

<span data-ttu-id="b1d33-259">Yönteminin sonuna aşağıdaki kodu ekleyin `MakeConstAsync` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-259">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="b1d33-260">Kod düzeltmeizin denemeye hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="b1d33-260">Your code fix is ready to try.</span></span>  <span data-ttu-id="b1d33-261">Visual Studio 'nun ikinci bir örneğinde çözümleyici projesini çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-261">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="b1d33-262">İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve Main yöntemine sabit değerlerle başlatılan birkaç yerel değişken bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-262">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="b1d33-263">Bunların uyarı olarak raporlandıklarından aşağıda gösterildiği gibi göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-263">You'll see that they are reported as warnings as below.</span></span>

![Const uyarıları yapabilir](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="b1d33-265">Çok sayıda ilerleme yaptınız.</span><span class="sxs-lookup"><span data-stu-id="b1d33-265">You've made a lot of progress.</span></span> <span data-ttu-id="b1d33-266">Bildirimlerin altında dalgalı çizgiler vardır `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-266">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="b1d33-267">Ancak yine de devam eden bir iş var.</span><span class="sxs-lookup"><span data-stu-id="b1d33-267">But there is still work to do.</span></span> <span data-ttu-id="b1d33-268">Bu `const` `i` , sonrasında `j` ve son olarak bulunan bildirimlere eklerseniz bu işe yarar `k` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-268">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="b1d33-269">Ancak, `const` değiştiricisini ile başlayarak farklı bir sırada eklerseniz `k` , çözümleyici 'niz hata oluşturuyor: `k` `const` `i` ve ikisi birden olmadığı için bildirilemez `j` `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-269">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="b1d33-270">Değişkenlerin bildirilebilecek ve başlatılabileceği farklı yolları işlediğinizden emin olmak için daha fazla analiz yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-270">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-unit-tests"></a><span data-ttu-id="b1d33-271">Derleme birimi testleri</span><span class="sxs-lookup"><span data-stu-id="b1d33-271">Build unit tests</span></span>

<span data-ttu-id="b1d33-272">Çözümleyici ve kod düzeltmesizin const hale getirilebilir tek bir bildirimin basit bir durumunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-272">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="b1d33-273">Bu uygulamanın hata yaptığı çok sayıda olası bildirim deyimi vardır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-273">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="b1d33-274">Şablon tarafından yazılan birim testi kitaplığıyla çalışarak bu durumları ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="b1d33-274">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="b1d33-275">Visual Studio 'nun ikinci bir kopyasını art arda açmadan çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-275">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="b1d33-276">Birim testi projesinde *MakeConstUnitTests. cs* dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-276">Open the *MakeConstUnitTests.cs* file in the unit test project.</span></span> <span data-ttu-id="b1d33-277">Şablon, bir çözümleyici ve kod düzelme birimi testi için iki ortak deseni izleyen iki test oluşturmuştur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-277">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="b1d33-278">`TestMethod1` çözümleyicinin ne zaman bir tanılama bildirmemesini sağlayan bir testin modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-278">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="b1d33-279">`TestMethod2` Bir tanılamayı raporlamak ve kod düzeltmesini çalıştırmak için bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-279">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="b1d33-280">Şablon, birim testi için [Microsoft. CodeAnalysis. Testing](https://github.com/dotnet/roslyn-sdk/blob/main/src/Microsoft.CodeAnalysis.Testing/README.md) paketlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-280">The template uses [Microsoft.CodeAnalysis.Testing](https://github.com/dotnet/roslyn-sdk/blob/main/src/Microsoft.CodeAnalysis.Testing/README.md) packages for unit testing.</span></span>

> [!TIP]
> <span data-ttu-id="b1d33-281">Sınama kitaplığı, aşağıdakiler de dahil olmak üzere özel bir biçimlendirme söz dizimini destekler:</span><span class="sxs-lookup"><span data-stu-id="b1d33-281">The testing library supports a special markup syntax, including the following:</span></span>
>
> - <span data-ttu-id="b1d33-282">`[|text|]`: için bir tanılayıcı rapor olduğunu gösterir `text` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-282">`[|text|]`: indicates that a diagnostic is reported for `text`.</span></span> <span data-ttu-id="b1d33-283">Bu form, varsayılan olarak yalnızca tarafından sağlanmış olan Çözümleyicileri test etmek için kullanılabilir `DiagnosticDescriptor` `DiagnosticAnalyzer.SupportedDiagnostics` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-283">By default, this form may only be used for testing analyzers with exactly one `DiagnosticDescriptor` provided by `DiagnosticAnalyzer.SupportedDiagnostics`.</span></span>
> - <span data-ttu-id="b1d33-284">`{|ExpectedDiagnosticId:text|}`: ile bir Tanılamanın rapor olduğunu gösterir <xref:Microsoft.CodeAnalysis.Diagnostic.Id> `ExpectedDiagnosticId` `text` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-284">`{|ExpectedDiagnosticId:text|}`: indicates that a diagnostic with <xref:Microsoft.CodeAnalysis.Diagnostic.Id> `ExpectedDiagnosticId` is reported for `text`.</span></span>

<span data-ttu-id="b1d33-285">Aşağıdaki test yöntemini `MakeConstUnitTest` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-285">Add the following test method to the `MakeConstUnitTest` class:</span></span>

[!code-csharp[test method for fix test](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "test method for fix test")]

<span data-ttu-id="b1d33-286">Geçirdiklerinden emin olmak için bu iki testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-286">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="b1d33-287">Visual Studio 'da **, test**   >  **Windows**  >  **Test Gezgini**' ni seçerek test Gezginini açın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-287">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="b1d33-288">Ardından **Tümünü Çalıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-288">Then select **Run All**.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="b1d33-289">Geçerli bildirimler için testler oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1d33-289">Create tests for valid declarations</span></span>

<span data-ttu-id="b1d33-290">Genel bir kural olarak, çözümleyicilerin olabildiğince çabuk çıkması gerekir ve en az iş yapılır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-290">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="b1d33-291">Visual Studio, Kullanıcı kodu düzenlediği için kayıtlı çözümleyiciler çağırır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-291">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="b1d33-292">Yanıt verme bir anahtar gereksinimidir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-292">Responsiveness is a key requirement.</span></span> <span data-ttu-id="b1d33-293">Tanılamasını yükseltmemelidir kod için birkaç test çalışması vardır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-293">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="b1d33-294">Çözümleyicisi zaten bu testlerin birini, bir değişkenin başlatıldıktan sonra atandığı durumu işler.</span><span class="sxs-lookup"><span data-stu-id="b1d33-294">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="b1d33-295">Bu durumu göstermek için aşağıdaki test yöntemini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-295">Add the following test method to represent that case:</span></span>

[!code-csharp[variable assigned](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="b1d33-296">Bu test da geçer.</span><span class="sxs-lookup"><span data-stu-id="b1d33-296">This test passes as well.</span></span> <span data-ttu-id="b1d33-297">Daha sonra, henüz işlenmeyen koşullar için test yöntemleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-297">Next, add test methods for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="b1d33-298">Zaten const olduklarından, zaten sabit olan bildirimler `const` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-298">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="b1d33-299">Başlatıcısı olmayan bildirimler, kullanılacak bir değer yoktur:</span><span class="sxs-lookup"><span data-stu-id="b1d33-299">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="b1d33-300">Başlatıcıya bir sabit olmadığı ve derleme zamanı sabitleri olmadıkları için bildirim:</span><span class="sxs-lookup"><span data-stu-id="b1d33-300">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="b1d33-301">C# birden çok bildirime tek bir bildirimde Izin verdiğinden daha karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-301">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="b1d33-302">Aşağıdaki test çalışması dize sabitini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="b1d33-302">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="b1d33-303">Değişken `i` sabit hale getirilebilir, ancak değişken `j` olamaz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-303">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="b1d33-304">Bu nedenle, bu ifade bir const bildirimi yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-304">Therefore, this statement cannot be made a const declaration.</span></span>

<span data-ttu-id="b1d33-305">Testlerinizi yeniden çalıştırın ve bu yeni test çalışmalarını başarısız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-305">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="b1d33-306">Çözümleyicinizi doğru bildirimleri yoksayacak şekilde güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="b1d33-306">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="b1d33-307">`AnalyzeNode`Bu koşullara uyan kodu filtrelemek için çözümleyicinizdeki bazı geliştirmeler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-307">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="b1d33-308">Bunlar ilgili tüm koşullardır, böylece benzer değişiklikler bu koşulların tümünü düzeltir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-308">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="b1d33-309">Aşağıdaki değişiklikleri yapın `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-309">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="b1d33-310">Anlam analiziniz tek bir değişken bildirimi inceledi.</span><span class="sxs-lookup"><span data-stu-id="b1d33-310">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="b1d33-311">Bu kodun, `foreach` aynı bildirimde belirtilen tüm değişkenleri inceleyen bir döngüde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-311">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="b1d33-312">Her beyan edilen değişkenin bir başlatıcıya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-312">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="b1d33-313">Her bir derlenen değişkenin başlatıcısı bir derleme zamanı sabiti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-313">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="b1d33-314">`AnalyzeNode`Yöntemdeki özgün anlam analizini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-314">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
VariableDeclaratorSyntax variable = localDeclaration.Declaration.Variables.Single();
ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="b1d33-315">Aşağıdaki kod parçacığı ile:</span><span class="sxs-lookup"><span data-stu-id="b1d33-315">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (VariableDeclaratorSyntax variable in localDeclaration.Declaration.Variables)
{
    EqualsValueClauseSyntax initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    Optional<object> constantValue = context.SemanticModel.GetConstantValue(initializer.Value, context.CancellationToken);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
DataFlowAnalysis dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (VariableDeclaratorSyntax variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    ISymbol variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable, context.CancellationToken);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="b1d33-316">İlk `foreach` döngü, söz dizimi analizini kullanarak her bir değişken bildirimini inceler.</span><span class="sxs-lookup"><span data-stu-id="b1d33-316">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="b1d33-317">İlk denetim, değişkenin bir başlatıcıya sahip olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="b1d33-317">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="b1d33-318">İkinci denetim, başlatıcının bir sabit olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="b1d33-318">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="b1d33-319">İkinci döngünün özgün anlam analizi vardır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-319">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="b1d33-320">Performans üzerinde daha fazla etkisi olduğundan anlam denetimleri ayrı bir döngüde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-320">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="b1d33-321">Testlerinizi yeniden çalıştırın ve hepsini bir kez görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-321">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="b1d33-322">Son Lehçe 'ı ekleyin</span><span class="sxs-lookup"><span data-stu-id="b1d33-322">Add the final polish</span></span>

<span data-ttu-id="b1d33-323">Neredeyse bitti.</span><span class="sxs-lookup"><span data-stu-id="b1d33-323">You're almost done.</span></span> <span data-ttu-id="b1d33-324">Çözümleyicinizi işlemek için birkaç koşul daha vardır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-324">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="b1d33-325">Visual Studio, Kullanıcı kod yazarken Çözümleyicileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-325">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="b1d33-326">Bu durum genellikle çözümleyicinizi derlenmeyen kod için çağrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-326">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="b1d33-327">Tanılama Çözümleyicisi yöntemi, `AnalyzeNode` sabit değerin değişken türüne dönüştürülebilir olup olmadığını kontrol etmez.</span><span class="sxs-lookup"><span data-stu-id="b1d33-327">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="b1d33-328">Bu nedenle, geçerli uygulama int ı = "abc" ' gibi yanlış bir bildirimi yerel bir sabit 'e dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-328">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="b1d33-329">Bu durum için bir test yöntemi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-329">Add a test method for this case:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="b1d33-330">Ayrıca, başvuru türleri düzgün işlenmez.</span><span class="sxs-lookup"><span data-stu-id="b1d33-330">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="b1d33-331">Bir başvuru türü için izin verilen tek sabit değeri, `null` Bu durum dışında, <xref:System.String?displayProperty=nameWithType> dize değişmezine izin verir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-331">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="b1d33-332">Diğer bir deyişle, geçerlidir `const string s = "abc"` ancak `const object s = "abc"` değildir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-332">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="b1d33-333">Bu kod parçacığı bu durumu doğrular:</span><span class="sxs-lookup"><span data-stu-id="b1d33-333">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="b1d33-334">Tam olarak, bir dize için sabit bildirim oluşturabilmeniz için başka bir test eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-334">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="b1d33-335">Aşağıdaki kod parçacığı, hem tanılamayı başlatan kodu hem de düzeltilme uygulandıktan sonra kodu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="b1d33-335">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="b1d33-336">Son olarak, bir değişken `var` anahtar sözcükle bildirilirse, kod düzeltilmesi yanlış şeyi yapar ve `const var` C# dili tarafından desteklenmeyen bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-336">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="b1d33-337">Bu hatayı onarmak için, kod düzeltmesinin `var` anahtar sözcüğünün çıkarılan türün adıyla yerine gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="b1d33-337">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="b1d33-338">Neyse ki, yukarıdaki hataların tümü, az önce öğrendiğiniz tekniklerin kullanılmasıyla çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-338">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="b1d33-339">İlk hatayı onarmak için öncelikle *Diagnosticanalyzer. cs* ' yi açın ve her bir yerel bildirimin başlatıcılarının her birinin, sabit değerlerle atanmasını sağlamak için her birinin kontrol edildiği foreach döngüsünü bulun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-339">To fix the first bug, first open *DiagnosticAnalyzer.cs* and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="b1d33-340">İlk foreach döngüsünden hemen _önce_ , `context.SemanticModel.GetTypeInfo()` Yerel bildirimin belirtilen türü hakkında ayrıntılı bilgi almak için çağırın:</span><span class="sxs-lookup"><span data-stu-id="b1d33-340">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

[!code-csharp[Retrieve type information](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#VariableConvertedType "Retrieve type information")]

<span data-ttu-id="b1d33-341">Sonra, `foreach` döngünüz içinde, değişken türüne dönüştürülebilir olduğundan emin olmak için her başlatıcıyı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-341">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="b1d33-342">Başlatıcının bir sabit olduğundan emin olduktan sonra aşağıdaki denetimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-342">Add the following check after ensuring that the initializer is a constant:</span></span>

[!code-csharp[Ensure non-user-defined conversion](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#BailOutOnUserDefinedConversion "Bail-out on user-defined conversion")]

<span data-ttu-id="b1d33-343">Sonraki değişiklik, son bir üzerinde derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-343">The next change builds upon the last one.</span></span> <span data-ttu-id="b1d33-344">İlk foreach döngüsünün kapanış küme ayracından önce, sabit bir dize veya null olduğunda yerel bildirimin türünü denetlemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-344">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

[!code-csharp[Handle special cases](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst/MakeConstAnalyzer.cs#HandleSpecialCases "Handle special cases")]

<span data-ttu-id="b1d33-345">Anahtar sözcüğünü doğru tür adıyla değiştirmek için kod düzeltme sağlayıcınızda bir bit daha daha kod yazmalısınız `var` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-345">You must write a bit more code in your code fix provider to replace the `var` keyword with the correct type name.</span></span> <span data-ttu-id="b1d33-346">*MakeConstCodeFixProvider. cs*' ye geri dönün.</span><span class="sxs-lookup"><span data-stu-id="b1d33-346">Return to *MakeConstCodeFixProvider.cs*.</span></span> <span data-ttu-id="b1d33-347">Ekleyeceğiniz kod aşağıdaki adımları yapar:</span><span class="sxs-lookup"><span data-stu-id="b1d33-347">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="b1d33-348">Bildirimin bir bildirim olup olmadığını `var` ve şu şekilde olduğunu kontrol edin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-348">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="b1d33-349">Çıkarsanan tür için yeni bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-349">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="b1d33-350">Tür bildiriminin bir diğer ad olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-350">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="b1d33-351">Varsa, bildirim için geçerlidir `const var` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-351">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="b1d33-352">`var`Bunun, bu programda bir tür adı olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="b1d33-352">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="b1d33-353">(Varsa, `const var` geçerlidir).</span><span class="sxs-lookup"><span data-stu-id="b1d33-353">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="b1d33-354">Tam tür adını basitleştirme</span><span class="sxs-lookup"><span data-stu-id="b1d33-354">Simplify the full type name</span></span>

<span data-ttu-id="b1d33-355">Bu çok fazla kod gibi seslerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="b1d33-355">That sounds like a lot of code.</span></span> <span data-ttu-id="b1d33-356">Bu değildir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-356">It's not.</span></span> <span data-ttu-id="b1d33-357">Bildiren ve Başlatan satırı `newLocal` aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-357">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="b1d33-358">Başlatma işleminden hemen sonra geçer `newModifiers` :</span><span class="sxs-lookup"><span data-stu-id="b1d33-358">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](snippets/how-to-write-csharp-analyzer-code-fix/MakeConst/MakeConst.CodeFixes/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="b1d33-359">`using`Türünü kullanmak için bir yönerge eklemeniz gerekir <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> :</span><span class="sxs-lookup"><span data-stu-id="b1d33-359">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="b1d33-360">Testlerinizi çalıştırın ve hepsi başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b1d33-360">Run your tests, and they should all pass.</span></span> <span data-ttu-id="b1d33-361">Tamamlanmış çözümleyicinizi çalıştırarak kendiniz kutlama yapın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-361">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="b1d33-362"><kbd></kbd> + Visual Studio 'nun ikinci bir örneğinde, Roslyn önizleme uzantısı yüklenmiş olarak çözümleyici projesini çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-362">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="b1d33-363">İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve `int x = "abc";` Main yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-363">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="b1d33-364">İlk hata düzelttiğinde, bu yerel değişken bildirimi için hiçbir uyarı bildirilmemelidir (ancak beklenen bir derleyici hatası var).</span><span class="sxs-lookup"><span data-stu-id="b1d33-364">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="b1d33-365">Sonra `object s = "abc";` Main yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b1d33-365">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="b1d33-366">İkinci hata düzelttiğinden uyarı bildirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="b1d33-366">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="b1d33-367">Son olarak, anahtar sözcüğünü kullanan başka bir yerel değişken ekleyin `var` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-367">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="b1d33-368">Bir uyarının bildirilmekte olduğunu ve sol tarafta bir öneri göründüğünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-368">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="b1d33-369">Düzenleyici giriş işaretini dalgalı alt çizginin üzerine taşıyın ve <kbd>CTRL</kbd>tuşuna basın + <kbd>.</kbd></span><span class="sxs-lookup"><span data-stu-id="b1d33-369">Move the editor caret over the squiggly underline and press <kbd>Ctrl</kbd>+<kbd>.</kbd>.</span></span> <span data-ttu-id="b1d33-370">önerilen kod düzeltmesini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="b1d33-370">to display the suggested code fix.</span></span> <span data-ttu-id="b1d33-371">Kod düzeltmesini seçtikten sonra `var` anahtar sözcüğünün artık doğru şekilde işlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b1d33-371">Upon selecting your code fix, note that the `var` keyword is now handled correctly.</span></span>

<span data-ttu-id="b1d33-372">Son olarak, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b1d33-372">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="b1d33-373">Bu değişikliklerden sonra, yalnızca ilk iki değişkene kırmızı dalgalı çizgiler alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b1d33-373">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="b1d33-374">Hem hem de `const` ' ye ekleyin `i` `j` , artık bu şekilde bir uyarı alabilirsiniz `k` `const` .</span><span class="sxs-lookup"><span data-stu-id="b1d33-374">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="b1d33-375">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="b1d33-375">Congratulations!</span></span> <span data-ttu-id="b1d33-376">Bir sorunu tespit etmek ve düzeltmek için hızlı bir düzeltme sağlamak üzere anında çalıştırılan kod analizini gerçekleştiren ilk .NET Compiler Platform uzantınızı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-376">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="b1d33-377">Bu şekilde, .NET Compiler Platform SDK 'nın (Roslyn API 'Ler) parçası olan kod API 'lerinin birçoğunu öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-377">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="b1d33-378">Çalışmalarımızı örnek GitHub deponuzdaki [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/Tutorials/MakeConst) karşı denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1d33-378">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/main/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="b1d33-379">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b1d33-379">Other resources</span></span>

- [<span data-ttu-id="b1d33-380">Sözdizimi analizini kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="b1d33-380">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="b1d33-381">Anlamsal analiz ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="b1d33-381">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
