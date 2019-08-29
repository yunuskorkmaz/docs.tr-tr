---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 570d071172c4048adfddfd55a5e38556e7fd7c69
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105849"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="e0dc9-104">Öğretici: Null yapılabilir ve null yapılamayan başvuru türleriyle tasarım amacınızı daha net bir şekilde ifade edin</span><span class="sxs-lookup"><span data-stu-id="e0dc9-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="e0dc9-105">C#8, null olabilen değer türleri için aynı şekilde, başvuru türlerini tamamlayan **null yapılabilir başvuru türlerini**tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-105">C# 8 introduces **nullable reference types**, which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="e0dc9-106">Bir`?` değişkeni türüne ekleyerek **null atanabilir bir başvuru türü** olarak bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="e0dc9-107">Örneğin, `string?` null yapılabilen bir değeri `string`temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="e0dc9-108">Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="e0dc9-109">Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> - <span data-ttu-id="e0dc9-110">Null yapılabilir ve null yapılamayan başvuru türlerini tasarımlarınız içine ekleyin</span><span class="sxs-lookup"><span data-stu-id="e0dc9-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="e0dc9-111">Kodunuzun tamamında null yapılabilir başvuru türü denetimlerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="e0dc9-112">Derleyicinin bu tasarım kararlarını zorladığı kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="e0dc9-113">Kendi tasarımlarınızın Nullable başvuru özelliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="e0dc9-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0dc9-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="e0dc9-114">Prerequisites</span></span>

<span data-ttu-id="e0dc9-115">C# 8,0 Beta derleyicisi dahil olmak üzere, makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 beta compiler.</span></span> <span data-ttu-id="e0dc9-116">C# 8 Beta derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya en son [.NET Core 3,0 Önizleme](https://dotnet.microsoft.com/download/dotnet-core/3.0)sürümü ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-116">The C# 8 beta compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or the latest [.NET Core 3.0 preview](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="e0dc9-117">Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="e0dc9-118">Tasarımlarınız için null yapılabilir başvuru türleri ekleyin</span><span class="sxs-lookup"><span data-stu-id="e0dc9-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="e0dc9-119">Bu öğreticide, bir anketi çalıştıran modellerle ilgili bir kitaplık oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="e0dc9-120">Kod, gerçek dünya kavramlarını temsil etmek için hem Nullable başvuru türlerini hem de null değer atanamaz başvuru türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="e0dc9-121">Anket soruları hiçbir şekilde null olamaz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-121">The survey questions can never be null.</span></span> <span data-ttu-id="e0dc9-122">Bir yanıtlayanın soru cevaplanmayı tercih edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="e0dc9-123">Bu durumda yanıtlar null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-123">The responses might be null in this case.</span></span>

<span data-ttu-id="e0dc9-124">Bu örnek için yazdığınız kod, amacı ifade eder ve derleyici bu amacı zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="e0dc9-125">Uygulamayı oluşturun ve null yapılabilir başvuru türlerini etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="e0dc9-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="e0dc9-126">Visual Studio 'da ya da kullanarak `dotnet new console`komut satırından yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="e0dc9-127">Uygulamayı `NullableIntroduction`adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="e0dc9-128">Uygulamayı oluşturduktan sonra 8 Beta özelliklerini etkinleştirmeniz C# gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-128">Once you've created the application, you'll need to enable C# 8 beta features.</span></span> <span data-ttu-id="e0dc9-129">Dosyasını açın ve `PropertyGroup` öğeye bir `LangVersion` öğe ekleyin. `csproj`</span><span class="sxs-lookup"><span data-stu-id="e0dc9-129">Open the `csproj` file and add a `LangVersion` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="e0dc9-130">8 projesinde bile **null yapılabilir başvuru türleri** özelliğini kabul etmeniz gerekir. C#</span><span class="sxs-lookup"><span data-stu-id="e0dc9-130">You must opt into the **nullable reference types** feature, even in C# 8 projects.</span></span> <span data-ttu-id="e0dc9-131">Bunun nedeni, özellik açık olduğunda, mevcut başvuru değişkeni bildirimleri **null yapılamayan başvuru türleri**haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-131">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="e0dc9-132">Bu karar, mevcut kodun doğru null denetimleri olmayan sorunları bulmaya yardımcı olur, ancak özgün tasarım amacınızı doğru bir şekilde yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-132">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent.</span></span> <span data-ttu-id="e0dc9-133">`Nullable` Öğesiniöğesiniöğesine`enable`ayarlayarak özelliğini açın:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-133">You turn on the feature by setting the `Nullable` element to `enable`:</span></span>

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

> [!IMPORTANT]
> <span data-ttu-id="e0dc9-134">Öğe daha önce adlandırılmıştı `NullableContextOptions`. `Nullable`</span><span class="sxs-lookup"><span data-stu-id="e0dc9-134">The `Nullable` element was previously named `NullableContextOptions`.</span></span> <span data-ttu-id="e0dc9-135">Yeniden adlandırma, Visual Studio 2019, 16,2-P1 ile birlikte gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-135">The rename ships with Visual Studio 2019, 16.2-p1.</span></span> <span data-ttu-id="e0dc9-136">3\.0.100-preview5-011568 .NET Core SDK bu değişikliğe sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-136">The .NET Core SDK 3.0.100-preview5-011568 does not have this change.</span></span> <span data-ttu-id="e0dc9-137">.NET Core CLI kullanıyorsanız, sonraki önizleme kullanılabilir olana kadar kullanmanız `NullableContextOptions` gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-137">If you are using the .NET Core CLI, you'll need to use `NullableContextOptions` until the next preview is available.</span></span>

> [!NOTE]
> <span data-ttu-id="e0dc9-138">C# 8 serbest bırakıldığında (Önizleme modunda değil), `Nullable` bu öğe yeni proje şablonları tarafından eklenir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-138">When C# 8 is released (not in preview mode), the `Nullable` element will be added by new project templates.</span></span> <span data-ttu-id="e0dc9-139">Bu şekilde, el ile eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-139">Until then, you'll need to add it manually.</span></span>

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="e0dc9-140">Uygulama için türleri tasarlama</span><span class="sxs-lookup"><span data-stu-id="e0dc9-140">Design the types for the application</span></span>

<span data-ttu-id="e0dc9-141">Bu anket uygulaması için birkaç sınıf oluşturulması gerekir:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-141">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="e0dc9-142">Soruların listesini modelleyen bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-142">A class that models the list of questions.</span></span>
- <span data-ttu-id="e0dc9-143">Anket için iletişim kurulan kişilerin listesini modelleyen sınıf.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-143">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="e0dc9-144">Anketi geçen bir kişiden yanıtları modelleyen sınıf.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-144">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="e0dc9-145">Bu türler, hangi üyelerin gerekli olduğunu ve hangi üyelerin isteğe bağlı olduğunu ifade etmek için hem null yapılabilir hem de null yapılamayan başvuru türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-145">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="e0dc9-146">Null yapılabilir başvuru türleri, tasarım amacını açıkça iletir:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-146">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="e0dc9-147">Anketin parçası olan sorular hiçbir şekilde null olamaz: Boş bir soru sormasına hiçbir fikir vermez.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-147">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="e0dc9-148">Yanıtlayanlar hiçbir şekilde null olamaz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-148">The respondents can never be null.</span></span> <span data-ttu-id="e0dc9-149">Görüştüğünüz kişileri, hatta katılmayı reddeden yanıt verenleri izlemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-149">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="e0dc9-150">Bir soruya herhangi bir yanıt null olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-150">Any response to a question may be null.</span></span> <span data-ttu-id="e0dc9-151">Yanıtlayanlar bazı veya tüm soruları yanıtlamak için reddedebilirler.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-151">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="e0dc9-152">İçinde C#programlamış olmanız durumunda, null olamayan örnekleri bildirmek için diğer fırsatlara kaçırmış olabilecek null değerlere izin veren başvuru türlerine alışkın olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-152">If you've programmed in C#, you may be so accustomed to reference types that allow null values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="e0dc9-153">Soruların toplanması null atanamaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-153">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="e0dc9-154">Yanıtlayanlar koleksiyonu null atanamaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-154">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="e0dc9-155">Kodu yazarken, başvurular için varsayılan olarak null yapılamayan bir başvuru türünün, null başvuru özel durumlarına yol açabilecek yaygın hataları önlediği görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-155">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to null reference exceptions.</span></span> <span data-ttu-id="e0dc9-156">Bu öğreticiden bir derste, hangi değişkenlerin null olması gerektiğine dair kararlar vermezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-156">One lesson from this tutorial is that you made decisions about which variables could or could not be null.</span></span> <span data-ttu-id="e0dc9-157">Dil, bu kararları ifade etmek için sözdizimi sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-157">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="e0dc9-158">Şimdi.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-158">Now it does.</span></span>

<span data-ttu-id="e0dc9-159">Derlenecek uygulama aşağıdaki adımları kullanacaktır:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-159">The app you'll build will do the following steps:</span></span>

1. <span data-ttu-id="e0dc9-160">Bir anket oluşturun ve buna sorular ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-160">Create a survey and add questions to it.</span></span>
1. <span data-ttu-id="e0dc9-161">Anket için sahte rastgele bir yanıt veren kümesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-161">Create a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="e0dc9-162">Tamamlanan anket boyutu hedef numarasına ulaşıncaya kadar yanıtlayanların iletişim kurun.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-162">Contact respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="e0dc9-163">Anket yanıtlarına önemli istatistikler yazın.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-163">Write out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="e0dc9-164">Null yapılabilir ve null yapılamayan türler ile anketi oluşturun</span><span class="sxs-lookup"><span data-stu-id="e0dc9-164">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="e0dc9-165">Yazacağınız ilk kod anketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-165">The first code you'll write creates the survey.</span></span> <span data-ttu-id="e0dc9-166">Bir anket sorusu ve bir anket çalıştırması modellemek için sınıflar yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-166">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="e0dc9-167">Anketiniz, yanıt biçimiyle ayırt edilen üç tür soru içerir: Evet/Hayır yanıt, sayı yanıtı ve metin yanıtı.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-167">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="e0dc9-168">`public` Sınıf oluşturun`SurveyQuestion` :</span><span class="sxs-lookup"><span data-stu-id="e0dc9-168">Create a `public` `SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="e0dc9-169">Derleyici, her başvuru türü değişken bildirimini, null yapılabilir etkin bağlamdaki kod için **null yapılamayan** bir başvuru türü olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-169">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in a nullable enabled context.</span></span> <span data-ttu-id="e0dc9-170">Aşağıdaki kodda gösterildiği gibi soru metni ve soru türü için özellikler ekleyerek ilk uyarılarınızı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-170">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

```csharp
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

<span data-ttu-id="e0dc9-171">Başlatılamamış `QuestionText`, derleyici null yapılamayan bir özelliğin başlatılmadığını belirten bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-171">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="e0dc9-172">Tasarımınız, soru metninin null olmasını gerektirir, bu nedenle onu ve `QuestionType` değeri başlatmak için bir Oluşturucu eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-172">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="e0dc9-173">Tamamlanmış sınıf tanımı aşağıdaki kod gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-173">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="e0dc9-174">Oluşturucuyu eklemek uyarıyı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-174">Adding the constructor removes the warning.</span></span> <span data-ttu-id="e0dc9-175">Oluşturucu bağımsız değişkeni aynı zamanda null atanamaz bir başvuru türüdür, bu nedenle derleyici hiçbir uyarı vermez.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-175">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="e0dc9-176">Ardından adlı `public` `SurveyRun`bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-176">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="e0dc9-177">Bu sınıf, aşağıdaki kodda gösterildiği `SurveyQuestion` gibi ankete soru eklemek için nesnelerin ve yöntemlerin bir listesini içerir:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-177">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

```csharp
using System.Collections.Generic;

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

<span data-ttu-id="e0dc9-178">Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmalısınız veya derleyici bir uyarı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-178">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="e0dc9-179">İkinci aşırı yüklemesi `AddQuestion` için gerekli olmadıklarından null denetimleri yok: Bu değişkenin null değer atanamayan olduğunu bildirdiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-179">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="e0dc9-180">Değeri olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-180">Its value can't be `null`.</span></span>

<span data-ttu-id="e0dc9-181">Düzenleyicinizde `Program.cs` öğesine geçin ve `Main` içeriğini aşağıdaki kod satırlarıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-181">Switch to `Program.cs` in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="e0dc9-182">Projenin tamamı null yapılabilir etkin bir bağlamda olduğundan, null olamayan bir başvuru türü bekleyen bir yönteme geçiş `null` yaptığınızda uyarılar alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-182">Because the entire project is in a nullable enabled context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="e0dc9-183">Aşağıdaki satırı öğesine `Main`ekleyerek deneyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-183">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="e0dc9-184">Katılımcıları oluşturun ve ankete yanıt alın</span><span class="sxs-lookup"><span data-stu-id="e0dc9-184">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="e0dc9-185">Sonra, ankete yanıtlar üreten kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-185">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="e0dc9-186">Bu işlem birkaç küçük görevi kapsar:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-186">This process involves several small tasks:</span></span>

1. <span data-ttu-id="e0dc9-187">Yanıtlayanın nesneleri üreten bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-187">Build a method that generates respondent objects.</span></span> <span data-ttu-id="e0dc9-188">Bu kişiler, anketi doldurduonları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-188">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="e0dc9-189">Bir yanıtlayanın sorularını sormasına, yanıtları toplamaya veya bir yanıtlayanın yanıt vermedi olduğunu benzetmek için mantığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-189">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="e0dc9-190">Ankete yanıt veren yeterli sayıda yanıt verene kadar tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-190">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="e0dc9-191">Bir anket yanıtını temsil eden bir sınıfa ihtiyacınız vardır, bu nedenle şimdi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-191">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="e0dc9-192">Null yapılabilir desteğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-192">Enable nullable support.</span></span> <span data-ttu-id="e0dc9-193">Aşağıdaki kodda `Id` gösterildiği gibi, bir özellik ve onu başlatan bir Oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-193">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyResponse
    {
        public int Id { get; }

        public SurveyResponse(int id) => Id = id;
    }
}
```

<span data-ttu-id="e0dc9-194">Sonra, rastgele bir `static` kimlik oluşturarak yeni katılımcılar oluşturmak için bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-194">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="e0dc9-195">Bu sınıfın ana sorumluluğu, bir katılımcının yanıtlarını Anketteki sorulara üretmesidir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-195">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="e0dc9-196">Bu sorumluluk birkaç adımdan daha sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-196">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="e0dc9-197">Ankete katılım isteyin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-197">Ask for participation in the survey.</span></span> <span data-ttu-id="e0dc9-198">Kişi onay vermezse, eksik (veya null) bir yanıt döndürün.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-198">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="e0dc9-199">Her soruyu sorun ve yanıtı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-199">Ask each question and record the answer.</span></span> <span data-ttu-id="e0dc9-200">Her cevap da eksik olabilir (veya null).</span><span class="sxs-lookup"><span data-stu-id="e0dc9-200">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="e0dc9-201">Sınıfınıza `SurveyResponse` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-201">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="e0dc9-202">Anket yanıtlarının depolaması, null olabileceğini belirten bir `Dictionary<int, string>?`' dır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-202">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="e0dc9-203">Tasarım amacınızı, her ikisi de derleyiciye ve kodunuzu daha sonra okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-203">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="e0dc9-204">İlk olarak null değeri `surveyResponses` denetlemeden başvuru yaptıysanız bir derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-204">If you ever dereference `surveyResponses` without checking for the null value first, you'll get a compiler warning.</span></span> <span data-ttu-id="e0dc9-205">Derleyici, değişkenin, `AnswerSurvey` `surveyResponses` yukarıda null olmayan bir değere ayarlandığını belirleyebildiğinden, yöntemde uyarı almanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-205">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="e0dc9-206">Eksik `null` yanıtlar için kullanmak, null yapılabilir başvuru türleriyle çalışmak için bir anahtar noktası vurgular: Amacınız tüm `null` değerleri programınızdan kaldırmıyor.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-206">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="e0dc9-207">Bunun yerine amacınız, yazdığınız kodun tasarımınızın amacını ifade etmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-207">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="e0dc9-208">Eksik değerler kodunuzda ifade etmek için gerekli bir kavramdır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-208">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="e0dc9-209">Bu `null` değer, eksik değerleri ifade etmenin açık bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-209">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="e0dc9-210">Tüm `null` değerleri kaldırmaya çalışmak, yalnızca bu eksik değerleri olmadan `null`ifade etmek için başka bir yol tanımlamaya yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-210">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="e0dc9-211">Daha sonra, `PerformSurvey` yöntemi `SurveyRun` sınıfına yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-211">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="e0dc9-212">`SurveyRun` Sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-212">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="e0dc9-213">Burada, null yapılabilir `List<SurveyResponse>?` seçiminiz, yanıtın null olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-213">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="e0dc9-214">Bu, anketin henüz herhangi bir yanıtlayanlara verilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-214">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="e0dc9-215">Yanıt verenlerin yeterli olana kadar eklendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-215">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="e0dc9-216">Anketi çalıştırmanın son adımı, `Main` yöntemin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-216">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="e0dc9-217">Anket yanıtlarını İnceleme</span><span class="sxs-lookup"><span data-stu-id="e0dc9-217">Examine survey responses</span></span>

<span data-ttu-id="e0dc9-218">Son adım, anket sonuçlarını görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-218">The last step is to display survey results.</span></span> <span data-ttu-id="e0dc9-219">Yazdığınız sınıfların çoğuna kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-219">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="e0dc9-220">Bu kod, null yapılabilir ve null yapılamayan başvuru türlerini ayırt etme değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-220">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="e0dc9-221">Aşağıdaki iki Expression-Bodied member `SurveyResponse` öğesini ekleyerek başlatın:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-221">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="e0dc9-222">`surveyResponses` Null olamayan bir başvuru türü olduğundan, kendisine başvurulmadan önce hiçbir denetim gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-222">Because `surveyResponses` is a non-nullable reference type, no checks are necessary before de-referencing it.</span></span> <span data-ttu-id="e0dc9-223">Yöntemi null yapılamayan bir dize döndürür, `GetValueOrDefault` bu nedenle varsayılan değer için ikinci bir bağımsız değişken alan aşırı yüklemesini seçin. `Answer`</span><span class="sxs-lookup"><span data-stu-id="e0dc9-223">The `Answer` method returns a non-nullable string, so choose the overload of `GetValueOrDefault` that takes a second argument for the default value.</span></span>

<span data-ttu-id="e0dc9-224">Ardından, bu üç Expression-Bodied üyelerini `SurveyRun` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-224">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="e0dc9-225">Üye, `respondents` değişkenin null olabileceğini, ancak dönüş değerinin null olduğunu dikkate almalıdır. `AllParticipants`</span><span class="sxs-lookup"><span data-stu-id="e0dc9-225">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="e0dc9-226">Bu ifadeyi `??` ve aşağıdaki boş diziyi kaldırarak değiştirirseniz, derleyici yöntemin döndürebileceğini `null` ve dönüş imzası null yapılamayan bir tür döndürdüğünü uyarır.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-226">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="e0dc9-227">Son olarak, aşağıdaki döngüyü `Main` yönteminin altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-227">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="e0dc9-228">Bu kodda herhangi bir `null` denetim yapmanız gerekmez, çünkü hepsi null yapılamayan başvuru türleri döndürecek şekilde temel arabirimleri tasarlamış oldunuz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-228">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="e0dc9-229">Kodu alın</span><span class="sxs-lookup"><span data-stu-id="e0dc9-229">Get the code</span></span>

<span data-ttu-id="e0dc9-230">Örnek deponuzdan, [CSharp/Nullabletanıtım](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründe bulunan [örnek](https://github.com/dotnet/samples) depomuza yönelik kodu alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-230">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="e0dc9-231">Null atanabilir ve null yapılamayan başvuru türleri arasında tür bildirimleri değiştirerek deneyin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-231">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="e0dc9-232">Bunun, yanlışlıkla `null`başvurmayabilmeniz için farklı uyarılar üretmesinin nasıl yapıldığını öğrenin.</span><span class="sxs-lookup"><span data-stu-id="e0dc9-232">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e0dc9-233">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="e0dc9-233">Next steps</span></span>

<span data-ttu-id="e0dc9-234">Mevcut bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirerek daha fazla bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="e0dc9-234">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e0dc9-235">Bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde yükseltme</span><span class="sxs-lookup"><span data-stu-id="e0dc9-235">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
