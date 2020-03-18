---
title: Nullable referans türleri ile tasarım
description: Bu gelişmiş öğretici, nullable başvuru türlerine giriş sağlar. Başvuru değerlerinin ne zaman null olabileceği konusunda tasarım niyetinizi ifade etmeyi ve derleyicinin null olamadığında uygulamasını öğreneceksiniz.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: b00050c1d151b95e330f94eb9393a4031e47d5a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240073"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="f9757-104">Öğretici: Tasarım niyetinizi nullable ve nullable olmayan referans türleri ile daha net ifade edin</span><span class="sxs-lookup"><span data-stu-id="f9757-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="f9757-105">C# 8.0, başvuru türlerini, nullable değer türlerinin tamamladığı şekilde tamamlayan [nullable başvuru türlerini](../nullable-references.md)tanır.</span><span class="sxs-lookup"><span data-stu-id="f9757-105">C# 8.0 introduces [nullable reference types](../nullable-references.md), which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="f9757-106">Bir değişkeni, a **nullable reference type** `?` türünü ekleyerek geçersiz bir başvuru türü olarak beyan elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9757-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="f9757-107">Örneğin, `string?` nullable `string`temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f9757-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="f9757-108">Tasarım amacınızı daha net ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olmalıdır,* diğerleri bir değer eksik *olabilir.*</span><span class="sxs-lookup"><span data-stu-id="f9757-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="f9757-109">Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="f9757-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="f9757-110">Nullable ve nullable olmayan referans türlerini tasarımlarınıza dahil edin</span><span class="sxs-lookup"><span data-stu-id="f9757-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="f9757-111">Kodunuz boyunca geçersiz başvuru türü denetimlerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f9757-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="f9757-112">Derleyicinin bu tasarım kararlarını uyguladığı kod yazın.</span><span class="sxs-lookup"><span data-stu-id="f9757-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="f9757-113">Kendi tasarımlarınızda geçersiz referans özelliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="f9757-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f9757-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="f9757-114">Prerequisites</span></span>

<span data-ttu-id="f9757-115">C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9757-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="f9757-116">C# 8.0 derleyicisi [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f9757-116">The C# 8.0 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="f9757-117">Bu öğretici, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET'e aşina olduğunuzu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f9757-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="f9757-118">Nullable referans türlerini tasarımlarınıza dahil edin</span><span class="sxs-lookup"><span data-stu-id="f9757-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="f9757-119">Bu öğreticide, anket çalıştıran modelleri içeren bir kitaplık oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f9757-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="f9757-120">Kod, gerçek dünya kavramlarını temsil etmek için hem geçersiz başvuru türlerini hem de nullable olmayan başvuru türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="f9757-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="f9757-121">Anket soruları asla geçersiz olamaz.</span><span class="sxs-lookup"><span data-stu-id="f9757-121">The survey questions can never be null.</span></span> <span data-ttu-id="f9757-122">Yanıtlayan bir soruya cevap vermemeyi tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="f9757-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="f9757-123">Yanıtlar bu `null` durumda olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9757-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="f9757-124">Bu örnek için yazacağınız kod bu amacı ifade eder ve derleyici bu amacı uygular.</span><span class="sxs-lookup"><span data-stu-id="f9757-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="f9757-125">Uygulamayı oluşturun ve nullable başvuru türlerini etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="f9757-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="f9757-126">Visual Studio'da veya komut satırından yeni `dotnet new console`bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9757-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="f9757-127">Uygulamayı adlandırın. `NullableIntroduction`</span><span class="sxs-lookup"><span data-stu-id="f9757-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="f9757-128">Uygulamayı oluşturduktan sonra, tüm projenin etkin **geçersiz ek açıklama bağlamında**derlediğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9757-128">Once you've created the application, you'll need to specify that the entire project compiles in an enabled **nullable annotation context**.</span></span> <span data-ttu-id="f9757-129">*.csproj* dosyasını açın `Nullable` ve `PropertyGroup` öğeye bir öğe ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f9757-129">Open the *.csproj* file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="f9757-130">Değerini `enable` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f9757-130">Set its value to `enable`.</span></span> <span data-ttu-id="f9757-131">C# 8.0 projelerinde bile **geçersiz başvuru türleri** özelliğini tercih etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9757-131">You must opt into the **nullable reference types** feature, even in C# 8.0 projects.</span></span> <span data-ttu-id="f9757-132">Bunun nedeni, özellik açık olduktan sonra varolan başvuru değişken iatürleri' nin **geçersiz başvuru türleri**haline gelmesidir.</span><span class="sxs-lookup"><span data-stu-id="f9757-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="f9757-133">Bu karar, varolan kodun uygun null-checks olmayabilir sorunları bulmanıza yardımcı olsa da, doğru orijinal tasarım amacı yansıtmayabilir:</span><span class="sxs-lookup"><span data-stu-id="f9757-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="f9757-134">Uygulama türlerini tasarla</span><span class="sxs-lookup"><span data-stu-id="f9757-134">Design the types for the application</span></span>

<span data-ttu-id="f9757-135">Bu anket uygulaması bir dizi sınıf oluşturmayı gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f9757-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="f9757-136">Soru listesini modelleyen bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="f9757-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="f9757-137">Anket için temasa geçilen kişilerin listesini modelleyen bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="f9757-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="f9757-138">Anketi alan bir kişinin yanıtlarını modelleyen bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="f9757-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="f9757-139">Bu türler, hangi üyelerin gerekli olduğunu ve hangi üyelerin isteğe bağlı olduğunu ifade etmek için hem geçersiz hem de geçersiz referans türlerinden yararlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="f9757-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="f9757-140">Nullable başvuru türleri bu tasarım amacını açıkça bildirir:</span><span class="sxs-lookup"><span data-stu-id="f9757-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="f9757-141">Anketin bir parçası olan sorular asla geçersiz olamaz: Boş bir soru sormak anlamsızdır.</span><span class="sxs-lookup"><span data-stu-id="f9757-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="f9757-142">Yanıtlayanlar asla geçersiz olamaz.</span><span class="sxs-lookup"><span data-stu-id="f9757-142">The respondents can never be null.</span></span> <span data-ttu-id="f9757-143">Bağlantı kurduğunuz kişileri, hatta katılmayı reddeden yanıtlayanları izlemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="f9757-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="f9757-144">Bir soruya verilen herhangi bir yanıt geçersiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9757-144">Any response to a question may be null.</span></span> <span data-ttu-id="f9757-145">Yanıtlayanlar bazı veya tüm soruları yanıtlamayı reddedebilir.</span><span class="sxs-lookup"><span data-stu-id="f9757-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="f9757-146">C#'da programlandıysanız, `null` değer veren başvuru türlerine o kadar alışmış olabilirsiniz ki, geçersiz olmayan örnekleri bildirmek için diğer fırsatları kaçırmış olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9757-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="f9757-147">Sorular topluluğu geçersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9757-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="f9757-148">Yanıtlayanların koleksiyonu geçersiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9757-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="f9757-149">Kodu yazdıkça, başvurular için varsayılan olarak nullable olmayan bir başvuru türü <xref:System.NullReferenceException>s yol açabilecek yaygın hatalar önler görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="f9757-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="f9757-150">Bu öğretici bir ders hangi değişkenler olabilir ya da olamazdı `null`hakkında kararlar olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f9757-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="f9757-151">Dil bu kararları ifade etmek için sözdizimi sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="f9757-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="f9757-152">Şimdi oldu.</span><span class="sxs-lookup"><span data-stu-id="f9757-152">Now it does.</span></span>

<span data-ttu-id="f9757-153">Oluşturacağınız uygulama aşağıdaki adımları yapar:</span><span class="sxs-lookup"><span data-stu-id="f9757-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="f9757-154">Bir anket oluşturur ve ankete sorular ekler.</span><span class="sxs-lookup"><span data-stu-id="f9757-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="f9757-155">Anket için sözde rasgele yanıtlayanlar kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9757-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="f9757-156">Tamamlanan anket boyutu hedef numarasına ulaşana kadar yanıtlayanlara bağlantı kurur.</span><span class="sxs-lookup"><span data-stu-id="f9757-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="f9757-157">Anket yanıtları ile ilgili önemli istatistikleri yazar.</span><span class="sxs-lookup"><span data-stu-id="f9757-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="f9757-158">Anketi geçersiz ve nullable olmayan türlerle oluşturun</span><span class="sxs-lookup"><span data-stu-id="f9757-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="f9757-159">Yazacağınız ilk kod anketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f9757-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="f9757-160">Bir anket sorusunu ve anket çalışmasını modellemek için sınıflar yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="f9757-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="f9757-161">Anketinizin yanıtının biçimine göre ayırt edilen üç tür sorusu vardır: Evet/Hayır yanıtları, sayı yanıtları ve metin yanıtları.</span><span class="sxs-lookup"><span data-stu-id="f9757-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="f9757-162">Bir `public SurveyQuestion` sınıf oluşturun:</span><span class="sxs-lookup"><span data-stu-id="f9757-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="f9757-163">Derleyici, her başvuru türü değişken bildirimini etkin bir nullable ek açıklama bağlamında kod için **nullable** olmayan bir başvuru türü olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="f9757-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in an enabled nullable annotation context.</span></span> <span data-ttu-id="f9757-164">Aşağıdaki kodda gösterildiği gibi, soru metni ve soru türü için özellikler ekleyerek ilk uyarınızı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f9757-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="f9757-165">Başharfe para vermediniz, `QuestionText`derleyici geçersiz bir özelliğin başharflere alınamadığını belirten bir uyarı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="f9757-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="f9757-166">Tasarımınız soru metninin null'suz olmasını gerektirir, bu nedenle onu ve `QuestionType` değeri de başlatması için bir oluşturucu eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="f9757-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="f9757-167">Bitmiş sınıf tanımı aşağıdaki kod gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="f9757-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="f9757-168">Oluşturucu ekleme uyarı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f9757-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="f9757-169">Oluşturucu bağımsız değişkeni de nullable olmayan bir başvuru türüdür, bu nedenle derleyici herhangi bir uyarı vermez.</span><span class="sxs-lookup"><span data-stu-id="f9757-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="f9757-170">Ardından, adlı `public` `SurveyRun`bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9757-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="f9757-171">Bu sınıf, aşağıdaki `SurveyQuestion` kodda gösterildiği gibi, ankete soru eklemek için nesnelerin ve yöntemlerin bir listesini içerir:</span><span class="sxs-lookup"><span data-stu-id="f9757-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="f9757-172">Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmanız gerekir veya derleyici bir uyarı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="f9757-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="f9757-173">İkinci aşırı yüklemede geçersiz denetim `AddQuestion` ler yoktur, çünkü bunlar gerekli değildir: Bu değişkeni nullable olarak beyan emtersiniz.</span><span class="sxs-lookup"><span data-stu-id="f9757-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="f9757-174">Değeri olamaz. `null`</span><span class="sxs-lookup"><span data-stu-id="f9757-174">Its value can't be `null`.</span></span>

<span data-ttu-id="f9757-175">Düzenleyicinizde *Program.cs'a* geçin ve `Main` içeriğini aşağıdaki kod satırlarıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="f9757-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="f9757-176">Projenin tamamı etkin geçersiz ek açıklama bağlamında olduğundan, nullable olmayan bir `null` başvuru türü bekleyen herhangi bir yönteme geçtiğiniz zaman uyarılar alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f9757-176">Because the entire project is in an enabled nullable annotation context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="f9757-177">Aşağıdaki satırı ekleyerek `Main`deneyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="f9757-178">Yanıtlayanlar oluşturun ve ankete yanıt alın</span><span class="sxs-lookup"><span data-stu-id="f9757-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="f9757-179">Ardından, ankete yanıt üreten kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="f9757-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="f9757-180">Bu işlem birkaç küçük görev içerir:</span><span class="sxs-lookup"><span data-stu-id="f9757-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="f9757-181">Yanıtlayan nesneleri oluşturan bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9757-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="f9757-182">Bunlar, anketi doldurmaları istenen kişileri temsil ediyor.</span><span class="sxs-lookup"><span data-stu-id="f9757-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="f9757-183">Soruları yanıtlayana sormayı ve yanıt ları toplamak veya yanıtlayanın yanıtlaşmadığına dikkat etmek için mantık oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f9757-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="f9757-184">Ankete yeteri kadar yanıtlayan yanıtlayana kadar tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="f9757-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="f9757-185">Bir anket yanıtını temsil etmek için bir sınıfa ihtiyacınız olacak, bu nedenle bunu şimdi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f9757-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="f9757-186">Nullable desteği etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="f9757-186">Enable nullable support.</span></span> <span data-ttu-id="f9757-187">Aşağıdaki `Id` kodda gösterildiği gibi, bir özellik ve onu başlatılmasını sağlayan bir oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="f9757-188">Ardından, rasgele `static` bir kimlik oluşturarak yeni katılımcılar oluşturmak için bir yöntem ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="f9757-189">Bu sınıfın temel sorumluluğu, anketteki sorulara katılan bir katılımcıiçin yanıt oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="f9757-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="f9757-190">Bu sorumluluğun birkaç adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="f9757-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="f9757-191">Ankete katılım isteyin.</span><span class="sxs-lookup"><span data-stu-id="f9757-191">Ask for participation in the survey.</span></span> <span data-ttu-id="f9757-192">Kişi izin vermezse, eksik (veya null) yanıtı döndürün.</span><span class="sxs-lookup"><span data-stu-id="f9757-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="f9757-193">Her soruyu sorun ve cevabı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f9757-193">Ask each question and record the answer.</span></span> <span data-ttu-id="f9757-194">Her yanıt da eksik (veya null) olabilir.</span><span class="sxs-lookup"><span data-stu-id="f9757-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="f9757-195">Sınıfınıza `SurveyResponse` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="f9757-196">Anket yanıtları için depolama `Dictionary<int, string>?`bir , null olabileceğini belirten.</span><span class="sxs-lookup"><span data-stu-id="f9757-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="f9757-197">Tasarım amacınızı hem derleyiciye hem de daha sonra kodunuzu okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="f9757-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="f9757-198">Değeri kontrol etmeden `surveyResponses` önce başvurudan `null` çıkarsanız, derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="f9757-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="f9757-199">Derleyici değişkenin `surveyResponses` yukarıdaki null `AnswerSurvey` olmayan bir değere ayarlandığını belirleyebileceğinden, yöntemde bir uyarı alamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f9757-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="f9757-200">Eksik `null` yanıtlar için kullanmak, geçersiz başvuru türleri ile çalışmak için önemli bir `null` noktayı vurgular: amacınız programınızdaki tüm değerleri kaldırmak değildir.</span><span class="sxs-lookup"><span data-stu-id="f9757-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="f9757-201">Bunun yerine, amacınız yazdığınız kodun tasarımınızın amacını ifade etmesini sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="f9757-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="f9757-202">Eksik değerler, kodunuzda ifade etmek için gerekli bir kavramdır.</span><span class="sxs-lookup"><span data-stu-id="f9757-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="f9757-203">Değer, `null` eksik değerleri ifade etmenin açık bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="f9757-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="f9757-204">Tüm `null` değerleri kaldırmaya çalışmak, yalnızca eksik değerleri ' siz `null`olmadan ifade etmek için başka bir yol tanımlamaya yol açar.</span><span class="sxs-lookup"><span data-stu-id="f9757-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="f9757-205">Sonra, `PerformSurvey` `SurveyRun` sınıfta yöntem yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f9757-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="f9757-206">Sınıfa `SurveyRun` aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="f9757-207">Burada yine, nullable `List<SurveyResponse>?` seçiminiz yanıtın null olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9757-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="f9757-208">Bu, anketin henüz herhangi bir yanıtlayana verilmediğini gösteriyor.</span><span class="sxs-lookup"><span data-stu-id="f9757-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="f9757-209">Yeterli izin alana kadar yanıtlayanların eklenmiş olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f9757-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="f9757-210">Anketi çalıştırmak için son adım, `Main` yöntemin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:</span><span class="sxs-lookup"><span data-stu-id="f9757-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="f9757-211">Anket yanıtlarını inceleyin</span><span class="sxs-lookup"><span data-stu-id="f9757-211">Examine survey responses</span></span>

<span data-ttu-id="f9757-212">Son adım anket sonuçlarını görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="f9757-212">The last step is to display survey results.</span></span> <span data-ttu-id="f9757-213">Yazdığınız birçok sınıfa kod eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="f9757-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="f9757-214">Bu kod, nullable ve nullable olmayan başvuru türlerini ayırt değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f9757-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="f9757-215">`SurveyResponse` Sınıfa aşağıdaki iki ifade gövdeli üye ekleyerek başlayın:</span><span class="sxs-lookup"><span data-stu-id="f9757-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="f9757-216">Nullable başvuru türü `surveyResponses` olduğundan, null denetimleri de-referencing önce gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f9757-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="f9757-217">Yöntem `Answer` nullable olmayan bir dize döndürür, bu yüzden null-coalescing işleci kullanarak eksik bir cevap durumda kapsayacak şekilde var.</span><span class="sxs-lookup"><span data-stu-id="f9757-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="f9757-218">Ardından, bu üç ifade gövdeli `SurveyRun` üyeyi sınıfa ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="f9757-219">Üye, `AllParticipants` değişkenin `respondents` null olabileceğini, ancak geri dönüş değerinin null olabileceğini göz önünde bulundurmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f9757-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="f9757-220">Bu ifadeyi, izleyen boş `??` sırayı kaldırarak değiştirirseniz, derleyici yöntemin `null` dönebileceği ve iade imzasının nullable olmayan bir türü döndürebileceği konusunda sizi uyarır.</span><span class="sxs-lookup"><span data-stu-id="f9757-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="f9757-221">Son olarak, yöntemin altına aşağıdaki `Main` döngüyü ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f9757-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="f9757-222">Temel arabirimleri, `null` hepsinin geçersiz olmayan başvuru türlerini döndürebilmesi için tasarladığınız için bu kodda herhangi bir denetime gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="f9757-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="f9757-223">Kodu alma</span><span class="sxs-lookup"><span data-stu-id="f9757-223">Get the code</span></span>

<span data-ttu-id="f9757-224">Bitmiş öğreticinin kodunu [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründeki [numune](https://github.com/dotnet/samples) deposumuzdan alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9757-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="f9757-225">Nullable ve nullable olmayan başvuru türleri arasındaki tür bildirimleri değiştirerek deneme.</span><span class="sxs-lookup"><span data-stu-id="f9757-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="f9757-226">Yanlışlıkla bir `null`' nin dereference'Ini göndermemeniz için bunun nasıl farklı uyarılar oluşturduğunu görün</span><span class="sxs-lookup"><span data-stu-id="f9757-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f9757-227">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="f9757-227">Next steps</span></span>

<span data-ttu-id="f9757-228">Nullable başvuru türlerini kullanmak için varolan bir uygulamayı geçirerek daha fazla bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="f9757-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f9757-229">Nullable başvuru türlerini kullanmak için bir uygulamayı yükseltme</span><span class="sxs-lookup"><span data-stu-id="f9757-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
