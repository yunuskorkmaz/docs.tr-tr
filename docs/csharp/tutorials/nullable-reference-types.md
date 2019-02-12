---
title: Null başvuru türleri için Tasarım
description: Gelişmiş Bu öğretici, bir null başvuru türlerine giriş sağlar. Tasarımınız ne zaman başvuru değeri null ve boş olamaz yürüttüğünde derleyici sahip hedefi express öğreneceksiniz.
ms.date: 12/03/2018
ms.custom: mvc
ms.openlocfilehash: 535efcdc303c17a55f6a4054ea3f5e5ed87e5f28
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092208"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="681fa-104">Öğretici: Tasarım amacınızla daha net bir şekilde boş değer atanabilir ve NULL olmayan bir başvuru türleri için express</span><span class="sxs-lookup"><span data-stu-id="681fa-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="681fa-105">C#8 tanıtır **null başvuru türleri**, boş değer atanabilen değer türleri tamamlar değer türleri aynı şekilde hangi tamamlayıcı başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="681fa-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="681fa-106">Olması için bir değişken bildirmek bir **boş değer atanabilir bir başvuru türü** ekleyerek bir `?` türü.</span><span class="sxs-lookup"><span data-stu-id="681fa-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="681fa-107">Örneğin, `string?` temsil eden bir boş değer atanabilir `string`.</span><span class="sxs-lookup"><span data-stu-id="681fa-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="681fa-108">Bu yeni türleri tasarım amacınızla daha net bir şekilde ifade etmek için kullanabilirsiniz: bazı değişkenler *her zaman bir değere sahip olmalıdır*, diğerleri *bir değer eksik*.</span><span class="sxs-lookup"><span data-stu-id="681fa-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="681fa-109">Bu öğreticide şunları öğrenirsiniz nasıl yapılır:</span><span class="sxs-lookup"><span data-stu-id="681fa-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="681fa-110">Boş değer atanabilir ve NULL olmayan bir başvuru türleri tasarımlarınızı dahil edilip derecelendirilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> * <span data-ttu-id="681fa-111">Kod boyunca boş değer atanabilir bir başvuru türü denetimlerini etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="681fa-111">Enable nullable reference type checks throughout your code.</span></span>
> * <span data-ttu-id="681fa-112">Burada bu tasarım kararları derleyici zorlar kod yazın.</span><span class="sxs-lookup"><span data-stu-id="681fa-112">Write code where the compiler enforces those design decisions.</span></span>
> * <span data-ttu-id="681fa-113">Kendi tasarımlarında null başvuru özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="681fa-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="681fa-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="681fa-114">Prerequisites</span></span>

<span data-ttu-id="681fa-115">.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 beta derleyici.</span><span class="sxs-lookup"><span data-stu-id="681fa-115">You’ll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="681fa-116">C# 8 beta derleyici, kullanılabilir [Visual Studio 2019 Önizleme 1](https://visualstudio.microsoft.com/vs/preview/), veya [.NET Core 3.0 Önizleme 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="681fa-116">The C# 8 beta compiler is available with [Visual Studio 2019 preview 1](https://visualstudio.microsoft.com/vs/preview/), or [.NET Core 3.0 preview 1](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="681fa-117">Bu öğreticide, aşina olduğunuz varsayılır C# ve .NET, Visual Studio veya .NET Core CLI gibi.</span><span class="sxs-lookup"><span data-stu-id="681fa-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="681fa-118">Null başvuru türleri tasarımlarınızı dahil edilip derecelendirilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="681fa-119">Bu öğreticide, bir anket çalışan modeller bir kitaplık oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="681fa-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="681fa-120">Kod, gerçek hayatta kullanılan kavramları göstermek için null başvuru türleri hem atanamayan başvuru türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="681fa-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="681fa-121">Anket sorularını hiçbir zaman null olabilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-121">The survey questions can never be null.</span></span> <span data-ttu-id="681fa-122">Yanıtlayan bir sorusunun yanıtını değil tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="681fa-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="681fa-123">Yanıtlar, bu durumda null olabilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-123">The responses might be null in this case.</span></span>

<span data-ttu-id="681fa-124">Bu amaç için bu örnek yazacaksınız kod ifade eder ve o hedefi derleyici zorlar.</span><span class="sxs-lookup"><span data-stu-id="681fa-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="681fa-125">Uygulama oluşturma ve null başvuru türleri etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="681fa-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="681fa-126">Visual Studio veya komut satırı kullanarak yeni bir konsol uygulaması oluşturma `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="681fa-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="681fa-127">Uygulama adı `NullableIntroduction`.</span><span class="sxs-lookup"><span data-stu-id="681fa-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="681fa-128">Uygulamayı oluşturduktan sonra etkinleştirmeniz gerekir C# 8 beta özellikleri.</span><span class="sxs-lookup"><span data-stu-id="681fa-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="681fa-129">Açık `csproj` dosya ve ekleme bir `LangVersion` öğesine `PropertyGroup` öğesi:</span><span class="sxs-lookup"><span data-stu-id="681fa-129">Open the `csproj` file, and add a `LangVersion` element to the `PropertyGroup` element:</span></span>

```xml
<LangVersion>8.0</LangVersion>
```

<span data-ttu-id="681fa-130">Alternatif olarak, etkinleştirmek için Visual Studio Proje özelliklerini kullanabilirsiniz C# 8.</span><span class="sxs-lookup"><span data-stu-id="681fa-130">Alternatively, you can use the Visual Studio project properties to enable C# 8.</span></span> <span data-ttu-id="681fa-131">Çözüm Gezgini'nde proje düğümünüze sağ tıklayın **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="681fa-131">In Solution Explorer, right click on the project node, select **Properties**.</span></span> <span data-ttu-id="681fa-132">Ardından, **derleme** sekmesine ve tıklayın **Gelişmiş...** . Dil sürümü için açılır listede seçin  **C# 8.0 (beta)**.</span><span class="sxs-lookup"><span data-stu-id="681fa-132">Then, select the **build** tab, and click **Advanced...**. In the dropdown for language version, select **C# 8.0 (beta)**.</span></span>

<span data-ttu-id="681fa-133">Katılmayı gerekir **null başvuru türleri** bile, özellik C# 8 projeleri.</span><span class="sxs-lookup"><span data-stu-id="681fa-133">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="681fa-134">Bu özellik etkinleştirildikten sonra mevcut başvuru değişken bildirimlerini olur çünkü **atanamayan başvuru türleri**.</span><span class="sxs-lookup"><span data-stu-id="681fa-134">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="681fa-135">Bu kararı uygun null denetimlerini varolan kodu nerede olmayabilir sorunları bulmanıza yardımcı olur, ancak özgün tasarım amacınızla doğru şekilde yansıtmaz.</span><span class="sxs-lookup"><span data-stu-id="681fa-135">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="681fa-136">Yeni bir pragma özelliğiyle açın:</span><span class="sxs-lookup"><span data-stu-id="681fa-136">You turn on the feature with a new pragma:</span></span>

```csharp
#nullable enable
```

<span data-ttu-id="681fa-137">Önceki pragma kaynak dosyada herhangi bir yere ekleyebilirsiniz ve o noktadan itibaren boş değer atanabilir bir başvuru türü özelliği etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-137">You can add the preceding pragma anywhere in a source file, and the nullable reference type feature is turned on from that point.</span></span> <span data-ttu-id="681fa-138">Pragma da destekler `disable` özelliği devre dışı bırakmak için bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="681fa-138">The pragma also supports the `disable` argument to turn off the feature.</span></span>

<span data-ttu-id="681fa-139">Ayrıca etkinleştirebilirsiniz **null başvuru türleri** şu öğe için .csproj dosyasını ekleyerek tüm proje için örneğin, hemen ardından `LangVersion` etkin öğe C# 8.0:</span><span class="sxs-lookup"><span data-stu-id="681fa-139">You can also turn on **nullable reference types** for an entire project by adding the following element to your .csproj file, for example, immediately following the `LangVersion` element that enabled C# 8.0:</span></span>

```xml
<NullableContextOptions>enable</NullableContextOptions>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="681fa-140">Uygulama türleri tasarımı</span><span class="sxs-lookup"><span data-stu-id="681fa-140">Design the types for the application</span></span>

<span data-ttu-id="681fa-141">Bir dizi sınıfları oluşturmak için bu anket uygulaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="681fa-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="681fa-142">Soruların listesini modeller bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="681fa-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="681fa-143">Anket için Görüşülen kişi listesini modeller bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="681fa-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="681fa-144">Anket geçen bir kişiden yanıtlarını modeller bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="681fa-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="681fa-145">Bu tür üyeleri gereklidir ve hangi üyelerin isteğe bağlı ifade etmek için alamayan başvuru türleri ve her ikisi de boş değer atanabilir kullanımını hale getirir.</span><span class="sxs-lookup"><span data-stu-id="681fa-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="681fa-146">Null başvuru türleri iletişim amacı açıkça tasarlama:</span><span class="sxs-lookup"><span data-stu-id="681fa-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="681fa-147">Anket parçası olan soruları hiçbir zaman null olabilir: Boş bir soru sormak için hiçbir mantıklı.</span><span class="sxs-lookup"><span data-stu-id="681fa-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="681fa-148">Katılımcıları hiçbir zaman null olabilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-148">The respondents can never be null.</span></span> <span data-ttu-id="681fa-149">Bu izleme, Görüşülen kişi, katılmak için reddedilen bile katılımcıları olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="681fa-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="681fa-150">Soru için herhangi bir yanıt null olabilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-150">Any response to a question may be null.</span></span> <span data-ttu-id="681fa-151">Katılımcıların bazı veya tüm soruları yanıtlamak reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="681fa-152">Programlanmış varsa C#, diğer fırsatları atanamayan örnekleri bildirmek için eksik olabilir, null değerlere izin türlerine başvurmak bu nedenle alışkın olabilir:</span><span class="sxs-lookup"><span data-stu-id="681fa-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="681fa-153">Sorular koleksiyonunu atanamayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="681fa-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="681fa-154">Katılımcıların koleksiyonunu atanamayan olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="681fa-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="681fa-155">Kod yazarken, başvurular için varsayılan olarak bir NULL olmayan bir başvuru türü, null başvuru özel durumu neden olabilecek yaygın hataları önler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="681fa-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="681fa-156">Bu öğreticiden bir ders, değişkenleri bulunamadı veya null olabilir değil, hakkında kararlar yapılan ' dir.</span><span class="sxs-lookup"><span data-stu-id="681fa-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="681fa-157">Dil sözdiziminin bu kararları express için sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="681fa-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="681fa-158">Artık bunu yapar.</span><span class="sxs-lookup"><span data-stu-id="681fa-158">Now it does.</span></span>

<span data-ttu-id="681fa-159">Oluşturacağınız uygulama aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="681fa-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="681fa-160">Anket oluşturmak ve sorular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="681fa-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="681fa-161">Anket yanıt veren bir sözde rastgele dizi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="681fa-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="681fa-162">Hedef numara tamamlanan anket boyutuna erişene kadar yanıt verenler başvurun.</span><span class="sxs-lookup"><span data-stu-id="681fa-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="681fa-163">Önemli istatistikleri anket yanıtları yazın.</span><span class="sxs-lookup"><span data-stu-id="681fa-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="681fa-164">Boş değer atanabilir ve atanamayan türleriyle anket oluşturun</span><span class="sxs-lookup"><span data-stu-id="681fa-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="681fa-165">Anket, yazacaksınız ilk kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="681fa-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="681fa-166">Anket sorusuna ve çalıştırma araştırma modeli için sınıflar yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="681fa-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="681fa-167">Clearfit'in soru, yanıt biçimi göre ayırt edilen üç türü vardır: Sayı yanıtlar ve metin yanıtlar Evet/Hayır yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="681fa-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="681fa-168">Oluşturma bir `public` `SurveyQuestion` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="681fa-168">Create a `public` `SurveyQuestion` class.</span></span> <span data-ttu-id="681fa-169">Dahil `#nullable enable` pragma hemen sonra `using` ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="681fa-169">Include the `#nullable enable` pragma immediately after the `using` statements:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="681fa-170">Ekleme `#nullable enable` pragma anlamına gelir derleyici, her başvuru türü değişken bildirimi olarak yorumlar bir **atanamayan** başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="681fa-170">Adding the `#nullable enable` pragma means the compiler interprets every reference type variable declaration as a **non-nullable** reference type.</span></span> <span data-ttu-id="681fa-171">Aşağıdaki kodda gösterildiği gibi Soru metni ve soru türü özellikleri ekleyerek, ilk uyarı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="681fa-171">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public enum QuestionType
    {
        YesNo,
        Number,
        Text
    }

    public class SurveyQuestion
    {
        public string QuestionText { get; }
        public QuestionType TypeOfQuestion { get; }
    }
}
```

<span data-ttu-id="681fa-172">Henüz başlatılmamış olduğundan `QuestionText`, derleyici atanamayan bir özellik başlatılmamış bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="681fa-172">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="681fa-173">Tasarımınızı başlatmak üzere bir oluşturucu ekleyin için null olmayan, Soru metni gerektirir ve `QuestionType` değeri de.</span><span class="sxs-lookup"><span data-stu-id="681fa-173">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="681fa-174">Tamamlanmış sınıf tanımını şu kod gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="681fa-174">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="681fa-175">Oluşturucu eklemesini uyarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="681fa-175">Adding the constructor removes the warning.</span></span> <span data-ttu-id="681fa-176">Derleyici Uyarı vermek değil oluşturucu bağımsız değişkeni de bir NULL olmayan bir başvuru türü olduğundan.</span><span class="sxs-lookup"><span data-stu-id="681fa-176">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="681fa-177">Ardından, oluşturun bir `public` adlı sınıfı `SurveyRun`.</span><span class="sxs-lookup"><span data-stu-id="681fa-177">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="681fa-178">Dahil `#nullable enable` pragması şu `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="681fa-178">Include the `#nullable enable` pragma following the `using` statements.</span></span> <span data-ttu-id="681fa-179">Bu sınıf bir listesini içeren `SurveyQuestion` nesneleri ve yöntemleri aşağıdaki kodda gösterildiği gibi ankete sorularınızı eklemek için:</span><span class="sxs-lookup"><span data-stu-id="681fa-179">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

#nullable enable
namespace NullableIntroduction
{
    public class SurveyRun
    {
        private List<SurveyQuestion> surveyQuestions = new List<SurveyQuestion>();

        public void AddQuestion(QuestionType type, string question) =>
            AddQuestion(new SurveyQuestion(type, question));
        public void AddQuestion(SurveyQuestion surveyQuestion) => surveyQuestions.Add(surveyQuestion);
    }
}
```

<span data-ttu-id="681fa-180">Önceki örneklerde olduğu gibi bir null olmayan değer Liste nesnesine başlatması gerekir veya derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="681fa-180">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="681fa-181">İkinci aşırı yüklemesi, null denetimi yoktur `AddQuestion` gerekli değildir çünkü: Bu değişken null yapılamaz bildirdikten.</span><span class="sxs-lookup"><span data-stu-id="681fa-181">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="681fa-182">Değeri olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="681fa-182">Its value can't be `null`.</span></span>

<span data-ttu-id="681fa-183">Geçiş `Program.cs` düzenleyicinizde ve içeriklerini `Main` aşağıdaki kod satırlarını ile:</span><span class="sxs-lookup"><span data-stu-id="681fa-183">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="681fa-184">Olmadan `#nullable enable` pragma dosyanın üst derleyici değil sorun bir uyarı geçirdiğinizde `null` metni olarak `AddQuestion` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="681fa-184">Without the `#nullable enable` pragma at the top of the file, the compiler doesn't issue a warning when you pass `null` as the text for the `AddQuestion` argument.</span></span> <span data-ttu-id="681fa-185">Ekleyerek düzeltmeyi `#nullable enable` aşağıdaki `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="681fa-185">Fix that by adding `#nullable enable` following the `using` statement.</span></span> <span data-ttu-id="681fa-186">Aşağıdaki satırı ekleyerek deneyin `Main`:</span><span class="sxs-lookup"><span data-stu-id="681fa-186">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="681fa-187">Katılımcıların oluşturun ve anket yanıtlarını alın</span><span class="sxs-lookup"><span data-stu-id="681fa-187">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="681fa-188">Ardından, anket yanıtlarını oluşturan kod yazın.</span><span class="sxs-lookup"><span data-stu-id="681fa-188">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="681fa-189">Bu, birkaç küçük görevleri içerir:</span><span class="sxs-lookup"><span data-stu-id="681fa-189">This involves several small tasks:</span></span>

1. <span data-ttu-id="681fa-190">Katılımcı nesneleri oluşturan bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="681fa-190">Build a method that generates respondent objects.</span></span> <span data-ttu-id="681fa-191">Bu kişiler anketini doldurmanız istenir temsil eder.</span><span class="sxs-lookup"><span data-stu-id="681fa-191">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="681fa-192">Soruları yanıtlayan isteyen ve yanıtları toplamak veya bir katılımcı yanıt Alamadığınız belirtmeye benzetimini yapmak için mantıksal oluşturun.</span><span class="sxs-lookup"><span data-stu-id="681fa-192">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="681fa-193">Yeterli katılımcıları anket ın kadar yineleyin.</span><span class="sxs-lookup"><span data-stu-id="681fa-193">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="681fa-194">Bir anket yanıtı temsil eder, bu nedenle şimdi eklemek için bir sınıf gerekir.</span><span class="sxs-lookup"><span data-stu-id="681fa-194">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="681fa-195">Boş değer atanabilir desteğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="681fa-195">Enable nullable support.</span></span> <span data-ttu-id="681fa-196">Ekleme bir `Id` özelliği ve bunu, aşağıdaki kodda gösterildiği gibi başlatan bir oluşturucu:</span><span class="sxs-lookup"><span data-stu-id="681fa-196">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
#nullable enable
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="681fa-197">Ardından, ekleme bir `static` yöntemi rastgele bir kimlik oluşturarak yeni katılımcı oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="681fa-197">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="681fa-198">Ana Bu sınıf için sorulara katılımcı anket yanıtları oluşturmak için sorumluluğundadır.</span><span class="sxs-lookup"><span data-stu-id="681fa-198">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="681fa-199">Bu sorumluluk birkaç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="681fa-199">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="681fa-200">Anket katılım isteyin.</span><span class="sxs-lookup"><span data-stu-id="681fa-200">Ask for participation in the survey.</span></span> <span data-ttu-id="681fa-201">Kişi onayı değil eksik (veya boş) bir yanıt döndürür.</span><span class="sxs-lookup"><span data-stu-id="681fa-201">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="681fa-202">Her bir soru sorun ve yanıt kaydedin.</span><span class="sxs-lookup"><span data-stu-id="681fa-202">Ask each question and record the answer.</span></span> <span data-ttu-id="681fa-203">Her yanıt, ayrıca eksik (veya null) olabilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-203">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="681fa-204">Aşağıdaki kodu ekleyin, `SurveyResponse` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="681fa-204">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="681fa-205">Anket yanıtları için depolama bir `Dictionary<int, string>?`, gösteren null olabilir.</span><span class="sxs-lookup"><span data-stu-id="681fa-205">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="681fa-206">Yeni dil özelliği tasarım hedefi, derleyici ve daha sonra Kodunuzu okuyan herkese bildirmek için kullanmakta olduğunuz.</span><span class="sxs-lookup"><span data-stu-id="681fa-206">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="681fa-207">Şimdiye kadar başvuru değilse `surveyResponses` null değeri ilk denetlemeden bir derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="681fa-207">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="681fa-208">Bir uyarı elde etmezsiniz `AnswerSurvey` yöntemi derleyici çünkü `surveyResponses` değişkeni, bir null olmayan değer yukarıdaki ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="681fa-208">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="681fa-209">Ardından, yazmanız gereken `PerformSurvey` yönteminde `SurveyRun` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="681fa-209">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="681fa-210">Aşağıdaki kodu ekleyin `SurveyRun` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="681fa-210">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="681fa-211">Yeniden Buraya, kendi seçtiğiniz bir boş değer atanabilir `List<SurveyResponse>?` yanıt null gösterir.</span><span class="sxs-lookup"><span data-stu-id="681fa-211">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="681fa-212">Bu anketi tüm katılımcılara henüz verilen taşınmadığından gösterir.</span><span class="sxs-lookup"><span data-stu-id="681fa-212">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="681fa-213">Yeterli onaylı kadar katılımcıların eklenen dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="681fa-213">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="681fa-214">Anket çalıştırmak için son adımı sonunda anket gerçekleştirmek için bir çağrı eklemektir `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="681fa-214">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="681fa-215">Anket yanıtlarını inceleyin</span><span class="sxs-lookup"><span data-stu-id="681fa-215">Examine survey responses</span></span>

<span data-ttu-id="681fa-216">Son adım, anket sonuçlarını görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="681fa-216">The last step is to display survey results.</span></span> <span data-ttu-id="681fa-217">Yazdığınız sınıfların çoğu için kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="681fa-217">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="681fa-218">Bu kod, boş değer atanabilir ve NULL olmayan bir başvuru türleri ayrım değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="681fa-218">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="681fa-219">Aşağıdaki iki ifade gövdeli üyeler için ekleyerek başlangıç `SurveyResponse` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="681fa-219">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="681fa-220">Çünkü `surveyResponses` bir NULL olmayan bir başvuru türü seri durumdan başvurmadan önce hiçbir denetim gereklidir.</span><span class="sxs-lookup"><span data-stu-id="681fa-220">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="681fa-221">`Answer` Yöntemi null olmayan bir dize döndürür, bu nedenle, aşırı yüklemesini seçin `GetValueOrDefault` , varsayılan değer için ikinci bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="681fa-221">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="681fa-222">Ardından, bu üç ifade gövdeli üyeler ekleyin `SurveyRun` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="681fa-222">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="681fa-223">`AllParticipants` Üye dikkate almak gerekir, `respondents` değişkeni null olabilir, ancak dönüş değeri null olamaz.</span><span class="sxs-lookup"><span data-stu-id="681fa-223">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="681fa-224">Bu ifade kaldırarak değiştirirseniz `??` ve yöntem döndürebilir izleyen boş dizi derleyici sizi uyarır `null` ve dönüş imzası-boş değer atanabilir olmayan türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="681fa-224">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="681fa-225">Son olarak, pencerenin şu döngüyü ekleyin `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="681fa-225">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="681fa-226">Herhangi bir ihtiyaç duymazsanız `null` tüm NULL olmayan bir başvuru türleri döndürmeleri, temel alınan arabirimler tasarladığınız olduğundan bu kod, denetler.</span><span class="sxs-lookup"><span data-stu-id="681fa-226">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="681fa-227">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="681fa-227">Get the code</span></span>

<span data-ttu-id="681fa-228">Öğreticinin tamamlanan kodu alabilirsiniz bizim [örnekleri](https://github.com/dotnet/samples) depoda [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasör.</span><span class="sxs-lookup"><span data-stu-id="681fa-228">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="681fa-229">Boş değer atanabilir ve NULL olmayan bir başvuru türleri arasında tür bildirimleri değiştirerek denemeler yapın.</span><span class="sxs-lookup"><span data-stu-id="681fa-229">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="681fa-230">Yanlışlıkla başvuru olmayan emin olmak için farklı uyarıları oluşturan nasıl bkz bir `null`.</span><span class="sxs-lookup"><span data-stu-id="681fa-230">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="681fa-231">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="681fa-231">Next steps</span></span>

<span data-ttu-id="681fa-232">Null başvuru türlerine genel bakış okuyarak daha fazla bilgi edinin...</span><span class="sxs-lookup"><span data-stu-id="681fa-232">Learn more by reading an overview of nullable reference types..</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="681fa-233">Boş değer atanabilir başvuruları genel bakış</span><span class="sxs-lookup"><span data-stu-id="681fa-233">An overview of nullable references</span></span>](../nullable-references.md)
