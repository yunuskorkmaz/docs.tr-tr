---
title: 'Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma'
description: Bu öğretici, .NET derleyici SDK 'sını (Roslyn API 'Ler) kullanarak bir çözümleyici ve kod düzeltmesini oluşturmak için adım adım yönergeler sağlar.
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: e79907f364939462b7d0d5814c4752be23bcfdf3
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381599"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="e0389-103">Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma</span><span class="sxs-lookup"><span data-stu-id="e0389-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="e0389-104">.NET Compiler Platform SDK, C# veya Visual Basic kodunu hedefleyen özel uyarılar oluşturmak için ihtiyacınız olan araçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0389-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="e0389-105">**Çözümleyici** , kuralınızın ihlallerini algılayan kod içerir.</span><span class="sxs-lookup"><span data-stu-id="e0389-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="e0389-106">**Kod düzeltmenizi** ihlalin giderdiği kodu içerir.</span><span class="sxs-lookup"><span data-stu-id="e0389-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="e0389-107">Uyguladığınız kurallar, kod yapısından, adlandırma kurallarına ve daha fazlasına yönelik kodlama stiline kadar herhangi bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="e0389-108">.NET Compiler Platform, geliştiricilerin kod yazmakta olduğu ve kodu düzeltmek için tüm Visual Studio Kullanıcı arabirimi özelliklerinin yanı sıra kodu çözmede, Visual Studio Hata Listesi, "ampul" önerilerini oluşturarak ve önerilen düzeltmelerin zengin önizlemesini göstererek, analiz çalıştırma çerçevesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0389-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="e0389-109">Bu öğreticide, bir **çözümleyici** oluşturmayı ve Roslyn API 'lerini kullanarak bir **kod düzeltmesini** inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="e0389-110">Çözümleyici, kaynak kodu analizini gerçekleştirmek ve kullanıcıya bir sorun bildirmek için bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="e0389-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="e0389-111">İsteğe bağlı olarak, bir çözümleyici kullanıcının kaynak kodunda bir değişikliği temsil eden bir kod düzeltmesini de sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="e0389-112">Bu öğreticide, değiştirici kullanılarak bildirilebilecek ancak olmayan yerel değişken bildirimlerini bulan bir çözümleyici oluşturulur `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="e0389-113">Eşlik eden kod düzeltilmesi, değiştiriciyi eklemek için bu bildirimleri değiştirir `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0389-114">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="e0389-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="e0389-115">Visual Studio **Analyzer with Code düzeltmesini (.NET Standard)** şablonunda, içinde bilinen bir hata var ve visual Studio 2019 sürüm 16,7 ' de düzeltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="e0389-116">Aşağıdaki değişiklikler yapılmadığı takdirde şablondaki projeler derlenmeyecektir:</span><span class="sxs-lookup"><span data-stu-id="e0389-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="e0389-117">**Araç**  >  **seçenekleri**  >  **NuGet Paket Yöneticisi**  >  **paket kaynakları** ' nı seçin</span><span class="sxs-lookup"><span data-stu-id="e0389-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="e0389-118">Yeni bir kaynak eklemek için artı düğmesini seçin:</span><span class="sxs-lookup"><span data-stu-id="e0389-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="e0389-119">**Kaynağı** olarak ayarlayın `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` ve **Güncelle** 'yi seçin</span><span class="sxs-lookup"><span data-stu-id="e0389-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="e0389-120">**Çözüm Gezgini**, **Makeconst. vsix** projesine sağ tıklayın ve **Proje dosyasını Düzenle** ' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="e0389-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="e0389-121">`<AssemblyName>`Soneki eklemek için düğümü güncelleştirin `.Visx` :</span><span class="sxs-lookup"><span data-stu-id="e0389-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="e0389-122">`<ProjectReference>`Değeri değiştirmek için 41 satırındaki düğümü güncelleştirin `TargetFramework` :</span><span class="sxs-lookup"><span data-stu-id="e0389-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="e0389-123">*MakeConstUnitTests.cs* dosyasını *makeconst. test* projesinde güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="e0389-124">9. satırı aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="e0389-125">Aşağıdaki yönteme göre satırı 24 ' ü değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="e0389-126">62 satırını aşağıdaki yönteme değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="e0389-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="e0389-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="e0389-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e0389-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="e0389-129">**.Net Compiler Platform SDK 'sını** Visual Studio yükleyicisi aracılığıyla yüklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="e0389-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="e0389-130">Çözümleyicinizi oluşturmak ve doğrulamak için birkaç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="e0389-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="e0389-131">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0389-131">Create the solution.</span></span>
1. <span data-ttu-id="e0389-132">Çözümleyici adını ve açıklamasını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e0389-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="e0389-133">Rapor çözümleyici uyarıları ve önerileri.</span><span class="sxs-lookup"><span data-stu-id="e0389-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="e0389-134">Önerileri kabul etmek için kod düzeltmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e0389-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="e0389-135">Birim testler aracılığıyla Analizi geliştirme.</span><span class="sxs-lookup"><span data-stu-id="e0389-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="e0389-136">Çözümleyici şablonunu keşfet</span><span class="sxs-lookup"><span data-stu-id="e0389-136">Explore the analyzer template</span></span>

<span data-ttu-id="e0389-137">Çözümleyici, kullanıcıya yerel sabitlere dönüştürülebileceği herhangi bir yerel değişken bildirimi bildirir.</span><span class="sxs-lookup"><span data-stu-id="e0389-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="e0389-138">Örneğin, aşağıdaki kodu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e0389-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e0389-139">Yukarıdaki kodda `x` sabit bir değer atanır ve hiçbir şekilde değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="e0389-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="e0389-140">Değiştirici kullanılarak bildirilebilecek `const` :</span><span class="sxs-lookup"><span data-stu-id="e0389-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e0389-141">Bir değişkenin sabit bir şekilde yapılıp yapılmayacağını belirleme, değişken için sözdizimi analizi, başlatıcı ifadesinin sabit Analizi ve değişkenin hiçbir şekilde yazılmaması için veri akışı analizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e0389-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="e0389-142">.NET Compiler Platform, bu çözümlemenin daha kolay hale getirebilmesini sağlayan API 'Ler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0389-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="e0389-143">İlk adım, **kod düzeltilme projesi ile** yeni bir C# Çözümleyicisi oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e0389-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="e0389-144">Visual Studio 'da yeni proje iletişim kutusunu göstermek için **dosya > yeni > proje..** . öğesini seçin.</span><span class="sxs-lookup"><span data-stu-id="e0389-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="e0389-145">**Visual C# > genişletilebilirlik**altında, **kod düzeltmesine sahip çözümleyici 'yi (.NET Standard)** seçin.</span><span class="sxs-lookup"><span data-stu-id="e0389-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="e0389-146">Projenizi "**Makeconst**" olarak adlandırın ve Tamam ' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e0389-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="e0389-147">Code düzeltmesini içeren çözümleyici, üç proje oluşturur: biri çözümleyici ve kod düzeltmesini içerir, ikincisi bir birim testi projisidir ve üçüncüsü VSıX projisidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="e0389-148">Varsayılan başlangıç projesi VSıX projem ' dir.</span><span class="sxs-lookup"><span data-stu-id="e0389-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="e0389-149">VSıX projesini başlatmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e0389-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="e0389-150">Bu, yeni çözümleyicinizi yükleyen ikinci bir Visual Studio örneğini başlatır.</span><span class="sxs-lookup"><span data-stu-id="e0389-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="e0389-151">Çözümleyicinizi çalıştırdığınızda, Visual Studio 'nun ikinci bir kopyasını başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="e0389-152">Bu ikinci kopya ayarları depolamak için farklı bir kayıt defteri kovanı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0389-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="e0389-153">Bu, Visual Studio 'nun iki kopyasında görsel ayarları ayırt etmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0389-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="e0389-154">Visual Studio 'nun deneysel çalıştırması için farklı bir tema seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="e0389-155">Ayrıca, Visual Studio 'nun deneysel çalıştırmasını kullanarak ayarlarınızı dolaşıyor veya Visual Studio hesabınızda oturum açmayın.</span><span class="sxs-lookup"><span data-stu-id="e0389-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="e0389-156">Bu, ayarları farklı tutar.</span><span class="sxs-lookup"><span data-stu-id="e0389-156">That keeps the settings different.</span></span>

<span data-ttu-id="e0389-157">Az önce başlattığınız ikinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun (.NET Core veya .NET Framework Project, kaynak düzeyinde çalışır.) Simgenin üzerine dalgalı alt çizgiyle gelin ve bir çözümleyici tarafından sunulan uyarı metni görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e0389-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="e0389-158">Şablon, aşağıdaki şekilde gösterildiği gibi tür adında küçük harfler içeren her tür bildiriminde uyarı raporlayan bir çözümleyici oluşturur:</span><span class="sxs-lookup"><span data-stu-id="e0389-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![Çözümleyici raporlama uyarısı](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="e0389-160">Şablon Ayrıca, küçük harf karakter içeren herhangi bir tür adını tüm büyük harflere değiştiren bir kod düzeltmesini de sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0389-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="e0389-161">Önerilen değişiklikleri görmek için uyarıyla birlikte görüntülenecek ampule tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="e0389-162">Önerilen değişiklikler kabul edildiğinde, tür adı ve çözümdeki bu türe yapılan tüm başvurular güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="e0389-163">İlk çözümleyici 'yi eylemde gördüğünüze göre, ikinci Visual Studio örneğini kapatın ve çözümleyici projenize geri dönün.</span><span class="sxs-lookup"><span data-stu-id="e0389-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="e0389-164">Visual Studio 'nun ikinci bir kopyasını başlatmanız ve çözümleyicinizdeki her değişikliği test etmek için yeni kod oluşturmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e0389-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="e0389-165">Şablon sizin için bir birim testi projesi de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0389-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="e0389-166">Bu proje iki test içerir.</span><span class="sxs-lookup"><span data-stu-id="e0389-166">That project contains two tests.</span></span> <span data-ttu-id="e0389-167">`TestMethod1`Bir tanılamayı tetiklemeden kodu çözümleyen testin tipik biçimini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0389-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="e0389-168">`TestMethod2`Bir tanılamayı tetikleyen testin biçimini gösterir ve ardından önerilen bir kod düzeltmesini uygular.</span><span class="sxs-lookup"><span data-stu-id="e0389-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="e0389-169">Çözümleyicinizi ve kod düzeltmesini oluştururken, çalışmanızı doğrulamak üzere farklı kod yapıları için testler yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e0389-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="e0389-170">Çözümleyiciler için birim testleri, Visual Studio ile etkileşimli olarak test edilmesine kıyasla çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0389-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="e0389-171">Çözümleyici birim testleri, hangi kod yapılarının çözümleyicinizi tetikleyemediğini bildiğiniz ve bu harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e0389-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="e0389-172">Visual Studio 'nun başka bir kopyasına çözümleyicinizi yüklemek, henüz düşünmemiş olan yapıları keşfetmeye ve bulmaya yönelik harika bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e0389-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="e0389-173">Çözümleyici kayıtları oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0389-173">Create analyzer registrations</span></span>

<span data-ttu-id="e0389-174">Şablon, `DiagnosticAnalyzer` **MakeConstAnalyzer.cs** dosyasında başlangıç sınıfını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0389-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="e0389-175">Bu ilk çözümleyici, her çözümleyici 'nin iki önemli özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0389-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="e0389-176">Her Tanılama Çözümleyicisi `[DiagnosticAnalyzer]` , üzerinde çalıştığı dili açıklayan bir öznitelik sağlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0389-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="e0389-177">Her Tanılama Çözümleyicisi <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> sınıfından türetilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="e0389-178">Şablon, herhangi bir çözümleyici 'nin parçası olan temel özellikleri de gösterir:</span><span class="sxs-lookup"><span data-stu-id="e0389-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="e0389-179">Kaydetme eylemleri.</span><span class="sxs-lookup"><span data-stu-id="e0389-179">Register actions.</span></span> <span data-ttu-id="e0389-180">Eylemler, çözümleyicinizi ihlalleri için kodu incelemek üzere tetiklemesi gereken kod değişikliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0389-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="e0389-181">Visual Studio, kayıtlı bir eylemle eşleşen kod düzenlemeleri algıladığında, çözümleyici 'nin kayıtlı yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e0389-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="e0389-182">Tanılama oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0389-182">Create diagnostics.</span></span> <span data-ttu-id="e0389-183">Çözümleyicisi bir ihlal algıladığında, bu, ihlalin kullanıcısına bildirimde bulunan Visual Studio 'Nun kullandığı bir tanılama nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0389-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="e0389-184">Eylemini geçersiz kılmanızda kaydedebilirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e0389-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e0389-185">Bu öğreticide, yerel bildirimleri arayan **sözdizimi düğümlerini** ziyaret edeceğiz ve hangilerinin sabit değerlere sahip olduğunu görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e0389-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="e0389-186">Bir bildirim sabitlenebilir, çözümleyici bir tanılama oluşturup rapor eder.</span><span class="sxs-lookup"><span data-stu-id="e0389-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="e0389-187">İlk adım, kayıt sabitlerini ve yöntemini güncelleştirmek ve `Initialize` Bu sabitler "const yap" çözümleyicisini göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0389-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="e0389-188">Dize sabitlerinin çoğu dize kaynak dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0389-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="e0389-189">Daha kolay yerelleştirme için bu uygulamayı izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="e0389-190">**Makeconst** çözümleyici projesi için **Resources. resx** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e0389-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="e0389-191">Bu, kaynak düzenleyicisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e0389-191">This displays the resource editor.</span></span> <span data-ttu-id="e0389-192">Dize kaynaklarını aşağıdaki gibi güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="e0389-193">`AnalyzerTitle`"Değişken sabit hale getirilebilir" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="e0389-194">`AnalyzerMessageFormat`"Sabit yapılabilir" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="e0389-195">`AnalyzerDescription`"Sabit yap" olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="e0389-196">Ayrıca, **erişim değiştirici** açılan öğesini olarak değiştirin `public` .</span><span class="sxs-lookup"><span data-stu-id="e0389-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="e0389-197">Bu, birim testlerinde bu sabitleri kullanmayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e0389-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="e0389-198">İşiniz bittiğinde, kaynak Düzenleyicisi aşağıdaki şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="e0389-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![Dize kaynaklarını Güncelleştir](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="e0389-200">Geri kalan değişiklikler çözümleyici dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e0389-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="e0389-201">Visual Studio 'da **MakeConstAnalyzer.cs** açın.</span><span class="sxs-lookup"><span data-stu-id="e0389-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="e0389-202">Semboller üzerinde çalışan bir eylemden, söz dizimi üzerinde davranan bir eylemi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="e0389-203">`MakeConstAnalyzerAnalyzer.Initialize`Yönteminde, simgeleri üzerinde eylemi kaydeden satırı bulun:</span><span class="sxs-lookup"><span data-stu-id="e0389-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="e0389-204">Aşağıdaki satırla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="e0389-205">Bu değişiklikten sonra `AnalyzeSymbol` yöntemini silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="e0389-206">Bu çözümleyici <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> , deyimleri inceler <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e0389-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="e0389-207">`AnalyzeNode`Altında Red dalgalı çizgiler olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e0389-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="e0389-208">Az önce eklediğiniz kod `AnalyzeNode` bildirilmemiş bir yönteme başvurur.</span><span class="sxs-lookup"><span data-stu-id="e0389-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="e0389-209">Aşağıdaki kodu kullanarak bu yöntemi bildirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="e0389-210">`Category`Aşağıdaki kodda gösterildiği gibi, **MakeConstAnalyzer.cs** içinde "kullanım" olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="e0389-211">Const olabilecek yerel bildirimleri bul</span><span class="sxs-lookup"><span data-stu-id="e0389-211">Find local declarations that could be const</span></span>

<span data-ttu-id="e0389-212">Yöntemin ilk sürümünü yazmak zaman `AnalyzeNode` .</span><span class="sxs-lookup"><span data-stu-id="e0389-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="e0389-213">Bu, `const` Aşağıdaki kod gibi olabilecek, ancak olmayan tek bir yerel bildirime bakmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e0389-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e0389-214">İlk adım, yerel bildirimleri bulledir.</span><span class="sxs-lookup"><span data-stu-id="e0389-214">The first step is to find local declarations.</span></span> <span data-ttu-id="e0389-215">Aşağıdaki kodu `AnalyzeNode` **MakeConstAnalyzer.cs**içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="e0389-216">Bu atama, çözümleyici yerel bildirimlerinizde değişiklikler ve yalnızca yerel bildirimler için kaydedildiği için her zaman başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="e0389-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="e0389-217">Başka hiçbir düğüm türü, yönteminiz için bir çağrı tetiklemiyor `AnalyzeNode` .</span><span class="sxs-lookup"><span data-stu-id="e0389-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="e0389-218">Sonra, herhangi bir değiştiricinin bildirimini kontrol edin `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="e0389-219">Bunları bulursanız anında geri dönün.</span><span class="sxs-lookup"><span data-stu-id="e0389-219">If you find them, return immediately.</span></span> <span data-ttu-id="e0389-220">Aşağıdaki kod, `const` Yerel bildirimde herhangi bir değiştirici arar:</span><span class="sxs-lookup"><span data-stu-id="e0389-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="e0389-221">Son olarak, değişkenin olup olmadığını kontrol etmeniz gerekir `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="e0389-222">Bu, başlatıldıktan sonra hiçbir şekilde atanmadığından emin olmak anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e0389-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="e0389-223">Kullanarak bazı semantik analizler gerçekleştirirsiniz <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> .</span><span class="sxs-lookup"><span data-stu-id="e0389-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="e0389-224">`context`Yerel değişken bildiriminin yapılıp yapılmayacağını anlamak için bağımsız değişkenini kullanırsınız `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="e0389-225"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>Tek bir kaynak dosyasındaki tüm anlam bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0389-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="e0389-226">[Anlam modellerini](../work-with-semantics.md)içeren makalede daha fazla bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="e0389-227"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType>' Yi, yerel bildirim deyimindeki veri akışı analizini gerçekleştirmek için kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e0389-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="e0389-228">Ardından, bu veri akışı analizinin sonuçlarını kullanarak yerel değişkenin başka bir yerde yeni bir değerle yazılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0389-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="e0389-229"><xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A>Değişkenini almak için genişletme yöntemini çağırın <xref:Microsoft.CodeAnalysis.ILocalSymbol> ve <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> veri akışı analizinin koleksiyonuna dahil olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="e0389-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="e0389-230">Yönteminin sonuna aşağıdaki kodu ekleyin `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="e0389-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

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

<span data-ttu-id="e0389-231">Yeni eklenen kod, değişkenin değiştirilmediğinden emin olur ve bu nedenle yapılabilir `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="e0389-232">Tanılamayı yükseltme zamanı.</span><span class="sxs-lookup"><span data-stu-id="e0389-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="e0389-233">Aşağıdaki kodu içine son satır olarak ekleyin `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="e0389-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="e0389-234"><kbd>F5</kbd> 'e basarak çözümleyicinizi çalıştırmak için ilerleme durumunu kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="e0389-235">Daha önce oluşturduğunuz konsol uygulamasını yükleyebilir ve sonra şu test kodunu ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0389-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e0389-236">Ampul görünmelidir ve çözümleyici 'niz bir tanılama raporlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="e0389-237">Ancak ampul, şablon tarafından oluşturulan kod düzeltmesini hala kullanır ve bunun büyük bir durum oluşturabileceklerini söyler.</span><span class="sxs-lookup"><span data-stu-id="e0389-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="e0389-238">Sonraki bölümde, kod düzeltmesinin nasıl yazılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0389-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="e0389-239">Kod düzeltmesini yazın</span><span class="sxs-lookup"><span data-stu-id="e0389-239">Write the code fix</span></span>

<span data-ttu-id="e0389-240">Bir çözümleyici, bir veya daha fazla kod düzeltmesi sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="e0389-241">Kod onarımı, bildirilen sorunu ele alan bir düzenleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0389-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="e0389-242">Oluşturduğunuz çözümleyici için, const anahtar sözcüğünü ekleyen bir kod düzeltmesini sağlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0389-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="e0389-243">Kullanıcı onu düzenleyicide ampul kullanıcı arabiriminden seçer ve Visual Studio kodu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e0389-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="e0389-244">Şablon tarafından eklenen **MakeConstCodeFixProvider.cs** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e0389-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="e0389-245">Bu kod onarımı, tanılama çözümleyici 'niz tarafından üretilen tanılama KIMLIĞI 'ne zaten kablolu, ancak doğru kod dönüşümünü uygulamıyor.</span><span class="sxs-lookup"><span data-stu-id="e0389-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="e0389-246">Öncelikle bazı şablon kodunu kaldırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="e0389-246">First you should remove some of the template code.</span></span> <span data-ttu-id="e0389-247">Başlık dizesini "sabit yap" olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="e0389-248">Sonra, yöntemini silin `MakeUppercaseAsync` .</span><span class="sxs-lookup"><span data-stu-id="e0389-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="e0389-249">Artık geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e0389-249">It no longer applies.</span></span>

<span data-ttu-id="e0389-250">Tüm kod onarma sağlayıcıları öğesinden türetilir <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> .</span><span class="sxs-lookup"><span data-stu-id="e0389-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="e0389-251">Bunlar, <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> kullanılabilir kod düzeltmelerini raporlamak için tüm geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="e0389-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="e0389-252">' De `RegisterCodeFixesAsync` , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> tanı ile eşleştirmek için Aradığınız üst düğüm türünü bir olarak değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="e0389-253">Sonra, bir kod düzeltmesini kaydetmek için son satırı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="e0389-254">Bu değişiklik, değiştiricinin mevcut bir bildirime eklenmesinin sonucu olan yeni bir belge oluşturur `const` :</span><span class="sxs-lookup"><span data-stu-id="e0389-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="e0389-255">Simgenin üzerine yeni eklediğiniz kodda kırmızı dalgalı çizgiler fark edeceksiniz `MakeConstAsync` .</span><span class="sxs-lookup"><span data-stu-id="e0389-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="e0389-256">`MakeConstAsync`Aşağıdaki kodu beğenmek için bir bildirim ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="e0389-257">Yeni `MakeConstAsync` yönteminiz, <xref:Microsoft.CodeAnalysis.Document> kullanıcının kaynak dosyasını temsil eden yeni bir bildirim içeren yeni bir öğesine dönüştürür <xref:Microsoft.CodeAnalysis.Document> `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="e0389-258">`const`Bildirim ifadesinin önüne eklemek için yeni bir anahtar sözcük belirteci oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="e0389-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="e0389-259">Önce bildirim bildiriminin ilk belirtecinden önde gelen her türlü boşluğu kaldırmak ve belirtece eklemek konusunda dikkatli olun `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="e0389-260">`MakeConstAsync` yöntemine aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="e0389-261">Ardından, `const` aşağıdaki kodu kullanarak belirteci bildirime ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="e0389-262">Ardından, yeni bildirimi C# biçimlendirme kurallarıyla eşleşecek şekilde biçimlendirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="e0389-263">Değişikliklerinizi varolan kodla eşleşecek şekilde biçimlendirmek daha iyi bir deneyim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0389-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="e0389-264">Mevcut koddan hemen sonra aşağıdaki ifadeyi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="e0389-265">Bu kod için yeni bir ad alanı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-265">A new namespace is required for this code.</span></span> <span data-ttu-id="e0389-266">Aşağıdaki `using` yönergeyi dosyanın en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="e0389-267">Son adım, düzenlemenizi yapmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e0389-267">The final step is to make your edit.</span></span> <span data-ttu-id="e0389-268">Bu işlemin üç adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="e0389-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="e0389-269">Mevcut belgeye yönelik bir tanıtıcı alın.</span><span class="sxs-lookup"><span data-stu-id="e0389-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="e0389-270">Mevcut bildirimi yeni bildirimle değiştirerek yeni bir belge oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0389-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="e0389-271">Yeni belgeyi döndür.</span><span class="sxs-lookup"><span data-stu-id="e0389-271">Return the new document.</span></span>

<span data-ttu-id="e0389-272">Yönteminin sonuna aşağıdaki kodu ekleyin `MakeConstAsync` :</span><span class="sxs-lookup"><span data-stu-id="e0389-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="e0389-273">Kod düzeltmeizin denemeye hazırlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e0389-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="e0389-274">Visual Studio 'nun ikinci bir örneğinde çözümleyici projesini çalıştırmak için <kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e0389-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="e0389-275">İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve Main yöntemine sabit değerlerle başlatılan birkaç yerel değişken bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0389-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="e0389-276">Bunların uyarı olarak raporlandıklarından aşağıda gösterildiği gibi göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-276">You'll see that they are reported as warnings as below.</span></span>

![Const uyarıları yapabilir](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="e0389-278">Çok sayıda ilerleme yaptınız.</span><span class="sxs-lookup"><span data-stu-id="e0389-278">You've made a lot of progress.</span></span> <span data-ttu-id="e0389-279">Bildirimlerin altında dalgalı çizgiler vardır `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="e0389-280">Ancak yine de devam eden bir iş var.</span><span class="sxs-lookup"><span data-stu-id="e0389-280">But there is still work to do.</span></span> <span data-ttu-id="e0389-281">Bu `const` `i` , sonrasında `j` ve son olarak bulunan bildirimlere eklerseniz bu işe yarar `k` .</span><span class="sxs-lookup"><span data-stu-id="e0389-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="e0389-282">Ancak, `const` değiştiricisini ile başlayarak farklı bir sırada eklerseniz `k` , çözümleyici 'niz hata oluşturuyor: `k` `const` `i` ve ikisi birden olmadığı için bildirilemez `j` `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="e0389-283">Değişkenlerin bildirilebilecek ve başlatılabileceği farklı yolları işlediğinizden emin olmak için daha fazla analiz yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="e0389-284">Veri odaklı testler oluşturun</span><span class="sxs-lookup"><span data-stu-id="e0389-284">Build data driven tests</span></span>

<span data-ttu-id="e0389-285">Çözümleyici ve kod düzeltmesizin const hale getirilebilir tek bir bildirimin basit bir durumunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="e0389-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="e0389-286">Bu uygulamanın hata yaptığı çok sayıda olası bildirim deyimi vardır.</span><span class="sxs-lookup"><span data-stu-id="e0389-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="e0389-287">Şablon tarafından yazılan birim testi kitaplığıyla çalışarak bu durumları ele alacağız.</span><span class="sxs-lookup"><span data-stu-id="e0389-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="e0389-288">Visual Studio 'nun ikinci bir kopyasını art arda açmadan çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0389-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="e0389-289">Birim testi projesinde **MakeConstUnitTests.cs** dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="e0389-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="e0389-290">Şablon, bir çözümleyici ve kod düzelme birimi testi için iki ortak deseni izleyen iki test oluşturmuştur.</span><span class="sxs-lookup"><span data-stu-id="e0389-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="e0389-291">`TestMethod1`çözümleyicinin ne zaman bir tanılama bildirmemesini sağlayan bir testin modelini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0389-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="e0389-292">`TestMethod2`Bir tanılamayı raporlamak ve kod düzeltmesini çalıştırmak için bir model gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0389-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="e0389-293">Çözümleyicinizi neredeyse her test için kod, bu iki desenden birini izler.</span><span class="sxs-lookup"><span data-stu-id="e0389-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="e0389-294">İlk adımda, bu testlerin veri odaklı testler olarak yeniden kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="e0389-295">Daha sonra, farklı test girişlerini temsil etmek için yeni dize sabitleri ekleyerek yeni testlerin oluşturulması kolay olur.</span><span class="sxs-lookup"><span data-stu-id="e0389-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="e0389-296">Verimlilik için ilk adım, veri odaklı testlerde iki testi yeniden düzenleme.</span><span class="sxs-lookup"><span data-stu-id="e0389-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="e0389-297">Ardından, her yeni test için yalnızca birkaç dize sabiti tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="e0389-298">Yeniden düzenleme yaparken her iki yöntemi de daha iyi adlarla yeniden adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e0389-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="e0389-299">`TestMethod1`Herhangi bir tanılama işlemi yapılmasını sağlayan bu testle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="e0389-300">Tanılamanın bir uyarı tetiklemesine neden olmaması gereken herhangi bir kod parçasını tanımlayarak, bu test için yeni bir veri satırı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="e0389-301">`VerifyCSharpDiagnostic`Kaynak kod parçası için hiçbir Tanılama tetikleniyorsa, bu geçiş yükü geçer.</span><span class="sxs-lookup"><span data-stu-id="e0389-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="e0389-302">Sonra, `TestMethod2` bir Tanılamanın ortaya çıkarılmasını ve kaynak kod parçası için bir kod düzeltmesinin uygulanmasını sağlayan bu testle değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

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

<span data-ttu-id="e0389-303">Yukarıdaki kod ayrıca, beklenen tanılama sonucunu oluşturan kodda birkaç değişiklik yaptı.</span><span class="sxs-lookup"><span data-stu-id="e0389-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="e0389-304">Çözümleyici 'de kayıtlı olan genel sabitleri kullanır `MakeConst` .</span><span class="sxs-lookup"><span data-stu-id="e0389-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="e0389-305">Ayrıca, giriş ve sabit kaynak için iki dize sabiti kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0389-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="e0389-306">Sınıfına aşağıdaki dize sabitlerini ekleyin `UnitTest` :</span><span class="sxs-lookup"><span data-stu-id="e0389-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="e0389-307">Geçirdiklerinden emin olmak için bu iki testi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e0389-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="e0389-308">Visual Studio 'da **, test** **Test Explorer**  >  **Windows**  >  **Test Gezgini**' ni seçerek test Gezginini açın.</span><span class="sxs-lookup"><span data-stu-id="e0389-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="e0389-309">Ardından **Tümünü Çalıştır** bağlantısını seçin.</span><span class="sxs-lookup"><span data-stu-id="e0389-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="e0389-310">Geçerli bildirimler için testler oluşturma</span><span class="sxs-lookup"><span data-stu-id="e0389-310">Create tests for valid declarations</span></span>

<span data-ttu-id="e0389-311">Genel bir kural olarak, çözümleyicilerin olabildiğince çabuk çıkması gerekir ve en az iş yapılır.</span><span class="sxs-lookup"><span data-stu-id="e0389-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="e0389-312">Visual Studio, Kullanıcı kodu düzenlediği için kayıtlı çözümleyiciler çağırır.</span><span class="sxs-lookup"><span data-stu-id="e0389-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="e0389-313">Yanıt verme bir anahtar gereksinimidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="e0389-314">Tanılamasını yükseltmemelidir kod için birkaç test çalışması vardır.</span><span class="sxs-lookup"><span data-stu-id="e0389-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="e0389-315">Çözümleyicisi zaten bu testlerin birini, bir değişkenin başlatıldıktan sonra atandığı durumu işler.</span><span class="sxs-lookup"><span data-stu-id="e0389-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="e0389-316">Bu durumu göstermek için testlerinize aşağıdaki dize sabitini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="e0389-317">Ardından, aşağıdaki kod parçacığında gösterildiği gibi bu test için bir veri satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="e0389-318">Bu test da geçer.</span><span class="sxs-lookup"><span data-stu-id="e0389-318">This test passes as well.</span></span> <span data-ttu-id="e0389-319">Daha sonra, henüz işlememiş olan koşullar için sabitler ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="e0389-320">Zaten const olduklarından, zaten sabit olan bildirimler `const` :</span><span class="sxs-lookup"><span data-stu-id="e0389-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="e0389-321">Başlatıcısı olmayan bildirimler, kullanılacak bir değer yoktur:</span><span class="sxs-lookup"><span data-stu-id="e0389-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="e0389-322">Başlatıcıya bir sabit olmadığı ve derleme zamanı sabitleri olmadıkları için bildirim:</span><span class="sxs-lookup"><span data-stu-id="e0389-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="e0389-323">C# birden çok bildirime tek bir bildirimde Izin verdiğinden daha karmaşık olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="e0389-324">Aşağıdaki test çalışması dize sabitini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e0389-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="e0389-325">Değişken `i` sabit hale getirilebilir, ancak değişken `j` olamaz.</span><span class="sxs-lookup"><span data-stu-id="e0389-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="e0389-326">Bu nedenle, bu ifade bir const bildirimi yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="e0389-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="e0389-327">`DataRow`Tüm bu testler için bildirimleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-327">Add the `DataRow` declarations for all these tests:</span></span>

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

<span data-ttu-id="e0389-328">Testlerinizi yeniden çalıştırın ve bu yeni test çalışmalarını başarısız görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e0389-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="e0389-329">Çözümleyicinizi doğru bildirimleri yoksayacak şekilde güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e0389-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="e0389-330">`AnalyzeNode`Bu koşullara uyan kodu filtrelemek için çözümleyicinizdeki bazı geliştirmeler yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="e0389-331">Bunlar ilgili tüm koşullardır, böylece benzer değişiklikler bu koşulların tümünü düzeltir.</span><span class="sxs-lookup"><span data-stu-id="e0389-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="e0389-332">Aşağıdaki değişiklikleri yapın `AnalyzeNode` :</span><span class="sxs-lookup"><span data-stu-id="e0389-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="e0389-333">Anlam analiziniz tek bir değişken bildirimi inceledi.</span><span class="sxs-lookup"><span data-stu-id="e0389-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="e0389-334">Bu kodun, `foreach` aynı bildirimde belirtilen tüm değişkenleri inceleyen bir döngüde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="e0389-335">Her beyan edilen değişkenin bir başlatıcıya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="e0389-336">Her bir derlenen değişkenin başlatıcısı bir derleme zamanı sabiti olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0389-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="e0389-337">`AnalyzeNode`Yöntemdeki özgün anlam analizini değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0389-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

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

<span data-ttu-id="e0389-338">Aşağıdaki kod parçacığı ile:</span><span class="sxs-lookup"><span data-stu-id="e0389-338">with the following code snippet:</span></span>

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

<span data-ttu-id="e0389-339">İlk `foreach` döngü, söz dizimi analizini kullanarak her bir değişken bildirimini inceler.</span><span class="sxs-lookup"><span data-stu-id="e0389-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="e0389-340">İlk denetim, değişkenin bir başlatıcıya sahip olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="e0389-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="e0389-341">İkinci denetim, başlatıcının bir sabit olduğunu garanti eder.</span><span class="sxs-lookup"><span data-stu-id="e0389-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="e0389-342">İkinci döngünün özgün anlam analizi vardır.</span><span class="sxs-lookup"><span data-stu-id="e0389-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="e0389-343">Performans üzerinde daha fazla etkisi olduğundan anlam denetimleri ayrı bir döngüde bulunur.</span><span class="sxs-lookup"><span data-stu-id="e0389-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="e0389-344">Testlerinizi yeniden çalıştırın ve hepsini bir kez görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="e0389-345">Son Lehçe 'ı ekleyin</span><span class="sxs-lookup"><span data-stu-id="e0389-345">Add the final polish</span></span>

<span data-ttu-id="e0389-346">Neredeyse bitti.</span><span class="sxs-lookup"><span data-stu-id="e0389-346">You're almost done.</span></span> <span data-ttu-id="e0389-347">Çözümleyicinizi işlemek için birkaç koşul daha vardır.</span><span class="sxs-lookup"><span data-stu-id="e0389-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="e0389-348">Visual Studio, Kullanıcı kod yazarken Çözümleyicileri çağırır.</span><span class="sxs-lookup"><span data-stu-id="e0389-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="e0389-349">Bu durum genellikle çözümleyicinizi derlenmeyen kod için çağrılacaktır.</span><span class="sxs-lookup"><span data-stu-id="e0389-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="e0389-350">Tanılama Çözümleyicisi yöntemi, `AnalyzeNode` sabit değerin değişken türüne dönüştürülebilir olup olmadığını kontrol etmez.</span><span class="sxs-lookup"><span data-stu-id="e0389-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="e0389-351">Bu nedenle, geçerli uygulama int ı = "abc" ' gibi yanlış bir bildirimi yerel bir sabit 'e dönüştürmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="e0389-352">Bu koşul için bir kaynak dize sabiti ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="e0389-353">Ayrıca, başvuru türleri düzgün işlenmez.</span><span class="sxs-lookup"><span data-stu-id="e0389-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="e0389-354">Bir başvuru türü için izin verilen tek sabit değeri, `null` Bu durum dışında, <xref:System.String?displayProperty=nameWithType> dize değişmezine izin verir.</span><span class="sxs-lookup"><span data-stu-id="e0389-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="e0389-355">Diğer bir deyişle, geçerlidir `const string s = "abc"` ancak `const object s = "abc"` değildir.</span><span class="sxs-lookup"><span data-stu-id="e0389-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="e0389-356">Bu kod parçacığı bu durumu doğrular:</span><span class="sxs-lookup"><span data-stu-id="e0389-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="e0389-357">Tam olarak, bir dize için sabit bildirim oluşturabilmeniz için başka bir test eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0389-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="e0389-358">Aşağıdaki kod parçacığı, hem tanılamayı başlatan kodu hem de düzeltilme uygulandıktan sonra kodu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="e0389-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="e0389-359">Son olarak, bir değişken `var` anahtar sözcükle bildirilirse, kod düzeltilmesi yanlış şeyi yapar ve `const var` C# dili tarafından desteklenmeyen bir bildirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0389-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="e0389-360">Bu hatayı onarmak için, kod düzeltmesinin `var` anahtar sözcüğünün çıkarılan türün adıyla yerine gelmelidir:</span><span class="sxs-lookup"><span data-stu-id="e0389-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="e0389-361">Bu değişiklikler her iki test için de veri satırı bildirimlerini güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="e0389-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="e0389-362">Aşağıdaki kod, tüm veri satırı öznitelikleriyle bu testleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="e0389-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="e0389-363">Neyse ki, yukarıdaki hataların tümü, az önce öğrendiğiniz tekniklerin kullanılmasıyla çözülebilir.</span><span class="sxs-lookup"><span data-stu-id="e0389-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="e0389-364">İlk hatayı onarmak için önce **DiagnosticAnalyzer.cs** açın ve her bir yerel bildirimin başlatıcılarının her birinin, sabit değerlerle atanmasını sağlamak için her birinin kontrol edildiği foreach döngüsünü bulun.</span><span class="sxs-lookup"><span data-stu-id="e0389-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="e0389-365">İlk foreach döngüsünden hemen _önce_ , `context.SemanticModel.GetTypeInfo()` Yerel bildirimin belirtilen türü hakkında ayrıntılı bilgi almak için çağırın:</span><span class="sxs-lookup"><span data-stu-id="e0389-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="e0389-366">Sonra, `foreach` döngünüz içinde, değişken türüne dönüştürülebilir olduğundan emin olmak için her başlatıcıyı kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="e0389-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="e0389-367">Başlatıcının bir sabit olduğundan emin olduktan sonra aşağıdaki denetimi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="e0389-368">Sonraki değişiklik, son bir üzerinde derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0389-368">The next change builds upon the last one.</span></span> <span data-ttu-id="e0389-369">İlk foreach döngüsünün kapanış küme ayracından önce, sabit bir dize veya null olduğunda yerel bildirimin türünü denetlemek için aşağıdaki kodu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0389-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

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

<span data-ttu-id="e0389-370">Anahtar sözcüğünü doğru tür adıyla değiştirmek için kod düzeltme sağlayıcınızda bir bit daha daha kod yazmalısınız `var` .</span><span class="sxs-lookup"><span data-stu-id="e0389-370">You must write a bit more code in your code fix provider to replace the `var` keyword with the correct type name.</span></span> <span data-ttu-id="e0389-371">**CodeFixProvider.cs**'e geri dönün.</span><span class="sxs-lookup"><span data-stu-id="e0389-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="e0389-372">Ekleyeceğiniz kod aşağıdaki adımları yapar:</span><span class="sxs-lookup"><span data-stu-id="e0389-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="e0389-373">Bildirimin bir bildirim olup olmadığını `var` ve şu şekilde olduğunu kontrol edin:</span><span class="sxs-lookup"><span data-stu-id="e0389-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="e0389-374">Çıkarsanan tür için yeni bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0389-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="e0389-375">Tür bildiriminin bir diğer ad olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0389-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="e0389-376">Varsa, bildirim için geçerlidir `const var` .</span><span class="sxs-lookup"><span data-stu-id="e0389-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="e0389-377">`var`Bunun, bu programda bir tür adı olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="e0389-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="e0389-378">(Varsa, `const var` geçerlidir).</span><span class="sxs-lookup"><span data-stu-id="e0389-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="e0389-379">Tam tür adını basitleştirme</span><span class="sxs-lookup"><span data-stu-id="e0389-379">Simplify the full type name</span></span>

<span data-ttu-id="e0389-380">Bu çok fazla kod gibi seslerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e0389-380">That sounds like a lot of code.</span></span> <span data-ttu-id="e0389-381">Bu değildir.</span><span class="sxs-lookup"><span data-stu-id="e0389-381">It's not.</span></span> <span data-ttu-id="e0389-382">Bildiren ve Başlatan satırı `newLocal` aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e0389-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="e0389-383">Başlatma işleminden hemen sonra geçer `newModifiers` :</span><span class="sxs-lookup"><span data-stu-id="e0389-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="e0389-384">`using`Türünü kullanmak için bir yönerge eklemeniz gerekir <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> :</span><span class="sxs-lookup"><span data-stu-id="e0389-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="e0389-385">Testlerinizi çalıştırın ve hepsi başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0389-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="e0389-386">Tamamlanmış çözümleyicinizi çalıştırarak kendiniz kutlama yapın.</span><span class="sxs-lookup"><span data-stu-id="e0389-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="e0389-387"><kbd>Ctrl</kbd> + Visual Studio 'nun ikinci bir örneğinde, Roslyn önizleme uzantısı yüklenmiş olarak çözümleyici projesini çalıştırmak için CTRL<kbd>F5</kbd> tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e0389-387">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="e0389-388">İkinci Visual Studio örneğinde, yeni bir C# konsol uygulaması projesi oluşturun ve `int x = "abc";` Main yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0389-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="e0389-389">İlk hata düzelttiğinde, bu yerel değişken bildirimi için hiçbir uyarı bildirilmemelidir (ancak beklenen bir derleyici hatası var).</span><span class="sxs-lookup"><span data-stu-id="e0389-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="e0389-390">Sonra `object s = "abc";` Main yöntemine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0389-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="e0389-391">İkinci hata düzelttiğinden uyarı bildirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="e0389-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="e0389-392">Son olarak, anahtar sözcüğünü kullanan başka bir yerel değişken ekleyin `var` .</span><span class="sxs-lookup"><span data-stu-id="e0389-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="e0389-393">Bir uyarının bildirilmekte olduğunu ve sol tarafta bir öneri göründüğünü görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e0389-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="e0389-394">Düzenleyici giriş işaretini dalgalı alt çizginin üzerine taşıyın ve <kbd>CTRL</kbd>tuşuna basın + <kbd>.</kbd></span><span class="sxs-lookup"><span data-stu-id="e0389-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl</kbd>+<kbd>.</kbd>.</span></span> <span data-ttu-id="e0389-395">önerilen kod düzeltmesini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="e0389-395">to display the suggested code fix.</span></span> <span data-ttu-id="e0389-396">Kod düzeltmesini seçtikten sonra `var` anahtar sözcüğünün artık doğru şekilde işlendiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e0389-396">Upon selecting your code fix, note that the `var` keyword is now handled correctly.</span></span>

<span data-ttu-id="e0389-397">Son olarak, aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0389-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="e0389-398">Bu değişikliklerden sonra, yalnızca ilk iki değişkene kırmızı dalgalı çizgiler alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e0389-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="e0389-399">Hem hem de `const` ' ye ekleyin `i` `j` , artık bu şekilde bir uyarı alabilirsiniz `k` `const` .</span><span class="sxs-lookup"><span data-stu-id="e0389-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="e0389-400">Tebrikler!</span><span class="sxs-lookup"><span data-stu-id="e0389-400">Congratulations!</span></span> <span data-ttu-id="e0389-401">Bir sorunu tespit etmek ve düzeltmek için hızlı bir düzeltme sağlamak üzere anında çalıştırılan kod analizini gerçekleştiren ilk .NET Compiler Platform uzantınızı oluşturdunuz.</span><span class="sxs-lookup"><span data-stu-id="e0389-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="e0389-402">Bu şekilde, .NET Compiler Platform SDK 'nın (Roslyn API 'Ler) parçası olan kod API 'lerinin birçoğunu öğrendiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="e0389-403">Çalışmalarımızı örnek GitHub deponuzdaki [tamamlanmış örnekle](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) karşı denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0389-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="e0389-404">Diğer kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0389-404">Other resources</span></span>

- [<span data-ttu-id="e0389-405">Sözdizimi analizini kullanmaya başlayın</span><span class="sxs-lookup"><span data-stu-id="e0389-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="e0389-406">Anlamsal analiz ile çalışmaya başlama</span><span class="sxs-lookup"><span data-stu-id="e0389-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
