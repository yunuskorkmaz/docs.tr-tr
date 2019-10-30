---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 3ee5e50cf889dd0e02bf58f1e3471fc709b729cd
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039708"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a><span data-ttu-id="a40c3-104">Öğretici: tasarım amacınızı null olabilen ve null yapılamayan başvuru türleriyle daha net bir şekilde Ifade edin</span><span class="sxs-lookup"><span data-stu-id="a40c3-104">Tutorial: Express your design intent more clearly with nullable and non-nullable reference types</span></span>

<span data-ttu-id="a40c3-105">C#8,0, null olabilen değer türleri olan değer türlerini tamamlayan aynı şekilde başvuru türlerini tamamlayan [null yapılabilir başvuru türlerini](../nullable-references.md)tanıtır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-105">C# 8.0 introduces [nullable reference types](../nullable-references.md), which complement reference types the same way nullable value types complement value types.</span></span> <span data-ttu-id="a40c3-106">Türe bir `?` ekleyerek **null olabilen bir başvuru türü** olarak bir değişken bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-106">You declare a variable to be a **nullable reference type** by appending a `?` to the type.</span></span> <span data-ttu-id="a40c3-107">Örneğin `string?`, Nullable `string` temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a40c3-107">For example, `string?` represents a nullable `string`.</span></span> <span data-ttu-id="a40c3-108">Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-108">You can use these new types to more clearly express your design intent: some variables *must always have a value*, others *may be missing a value*.</span></span>

<span data-ttu-id="a40c3-109">Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:</span><span class="sxs-lookup"><span data-stu-id="a40c3-109">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a40c3-110">Null yapılabilir ve null yapılamayan başvuru türlerini tasarımlarınız içine ekleyin</span><span class="sxs-lookup"><span data-stu-id="a40c3-110">Incorporate nullable and non-nullable reference types into your designs</span></span>
> - <span data-ttu-id="a40c3-111">Kodunuzun tamamında null yapılabilir başvuru türü denetimlerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-111">Enable nullable reference type checks throughout your code.</span></span>
> - <span data-ttu-id="a40c3-112">Derleyicinin bu tasarım kararlarını zorladığı kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="a40c3-112">Write code where the compiler enforces those design decisions.</span></span>
> - <span data-ttu-id="a40c3-113">Kendi tasarımlarınızın Nullable başvuru özelliğini kullanın</span><span class="sxs-lookup"><span data-stu-id="a40c3-113">Use the nullable reference feature in your own designs</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a40c3-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a40c3-114">Prerequisites</span></span>

<span data-ttu-id="a40c3-115">Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-115">You'll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="a40c3-116">C# 8,0 derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-116">The C# 8.0 compiler is available with [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), or [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="a40c3-117">Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-117">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="incorporate-nullable-reference-types-into-your-designs"></a><span data-ttu-id="a40c3-118">Tasarımlarınız için null yapılabilir başvuru türleri ekleyin</span><span class="sxs-lookup"><span data-stu-id="a40c3-118">Incorporate nullable reference types into your designs</span></span>

<span data-ttu-id="a40c3-119">Bu öğreticide, bir anketi çalıştıran modellerle ilgili bir kitaplık oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a40c3-119">In this tutorial, you'll build a library that models running a survey.</span></span> <span data-ttu-id="a40c3-120">Kod, gerçek dünya kavramlarını temsil etmek için hem Nullable başvuru türlerini hem de null değer atanamaz başvuru türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-120">The code uses both nullable reference types and non-nullable reference types to represent the real-world concepts.</span></span> <span data-ttu-id="a40c3-121">Anket soruları hiçbir şekilde null olamaz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-121">The survey questions can never be null.</span></span> <span data-ttu-id="a40c3-122">Bir yanıtlayanın soru cevaplanmayı tercih edemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-122">A respondent might prefer not to answer a question.</span></span> <span data-ttu-id="a40c3-123">Yanıtlar bu durumda `null` olabilir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-123">The responses might be `null` in this case.</span></span>

<span data-ttu-id="a40c3-124">Bu örnek için yazdığınız kod, amacı ifade eder ve derleyici bu amacı zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="a40c3-124">The code you'll write for this sample expresses that intent, and the compiler enforces that intent.</span></span>

## <a name="create-the-application-and-enable-nullable-reference-types"></a><span data-ttu-id="a40c3-125">Uygulamayı oluşturun ve null yapılabilir başvuru türlerini etkinleştirin</span><span class="sxs-lookup"><span data-stu-id="a40c3-125">Create the application and enable nullable reference types</span></span>

<span data-ttu-id="a40c3-126">Visual Studio 'da ya da `dotnet new console` kullanarak komut satırından yeni bir konsol uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a40c3-126">Create a new console application either in Visual Studio or from the command line using `dotnet new console`.</span></span> <span data-ttu-id="a40c3-127">Uygulamayı `NullableIntroduction`olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a40c3-127">Name the application `NullableIntroduction`.</span></span> <span data-ttu-id="a40c3-128">Uygulamayı oluşturduktan sonra, tüm projenin etkinleştirilmiş bir **null yapılabilir ek açıklama bağlamında**derlendiğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-128">Once you've created the application, you'll need to specify that the entire project compiles in an enabled **nullable annotation context**.</span></span> <span data-ttu-id="a40c3-129">*. Csproj* dosyasını açın ve `PropertyGroup` öğesine `Nullable` öğesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-129">Open the *.csproj* file and add a `Nullable` element to the `PropertyGroup` element.</span></span> <span data-ttu-id="a40c3-130">Değerini `enable`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a40c3-130">Set its value to `enable`.</span></span> <span data-ttu-id="a40c3-131">8,0 projesinde bile **null yapılabilir başvuru türleri** özelliğini kabul etmeniz gerekir. C#</span><span class="sxs-lookup"><span data-stu-id="a40c3-131">You must opt into the **nullable reference types** feature, even in C# 8.0 projects.</span></span> <span data-ttu-id="a40c3-132">Bunun nedeni, özellik açık olduğunda, mevcut başvuru değişkeni bildirimleri **null yapılamayan başvuru türleri**haline gelir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-132">That's because once the feature is turned on, existing reference variable declarations become **non-nullable reference types**.</span></span> <span data-ttu-id="a40c3-133">Bu karar, var olan kodun doğru null denetimleri olmayan sorunları bulmaya yardımcı olur, ancak özgün tasarım hedefini doğru bir şekilde yansıtmayabilir:</span><span class="sxs-lookup"><span data-stu-id="a40c3-133">While that decision will help find issues where existing code may not have proper null-checks, it may not accurately reflect your original design intent:</span></span>

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a><span data-ttu-id="a40c3-134">Uygulama için türleri tasarlama</span><span class="sxs-lookup"><span data-stu-id="a40c3-134">Design the types for the application</span></span>

<span data-ttu-id="a40c3-135">Bu anket uygulaması için birkaç sınıf oluşturulması gerekir:</span><span class="sxs-lookup"><span data-stu-id="a40c3-135">This survey application requires creating a number of classes:</span></span>

- <span data-ttu-id="a40c3-136">Soruların listesini modelleyen bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="a40c3-136">A class that models the list of questions.</span></span>
- <span data-ttu-id="a40c3-137">Anket için iletişim kurulan kişilerin listesini modelleyen sınıf.</span><span class="sxs-lookup"><span data-stu-id="a40c3-137">A class that models a list of people contacted for the survey.</span></span>
- <span data-ttu-id="a40c3-138">Anketi geçen bir kişiden yanıtları modelleyen sınıf.</span><span class="sxs-lookup"><span data-stu-id="a40c3-138">A class that models the answers from a person that took the survey.</span></span>

<span data-ttu-id="a40c3-139">Bu türler, hangi üyelerin gerekli olduğunu ve hangi üyelerin isteğe bağlı olduğunu ifade etmek için hem null yapılabilir hem de null yapılamayan başvuru türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-139">These types will make use of both nullable and non-nullable reference types to express which members are required and which members are optional.</span></span> <span data-ttu-id="a40c3-140">Null yapılabilir başvuru türleri, tasarım amacını açıkça iletir:</span><span class="sxs-lookup"><span data-stu-id="a40c3-140">Nullable reference types communicate that design intent clearly:</span></span>

- <span data-ttu-id="a40c3-141">Anketin parçası olan sorular hiçbir şekilde null olamaz: boş bir soru sormasına hiçbir fikir vermez.</span><span class="sxs-lookup"><span data-stu-id="a40c3-141">The questions that are part of the survey can never be null: It makes no sense to ask an empty question.</span></span>
- <span data-ttu-id="a40c3-142">Yanıtlayanlar hiçbir şekilde null olamaz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-142">The respondents can never be null.</span></span> <span data-ttu-id="a40c3-143">Görüştüğünüz kişileri, hatta katılmayı reddeden yanıt verenleri izlemek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-143">You'll want to track people you contacted, even respondents that declined to participate.</span></span>
- <span data-ttu-id="a40c3-144">Bir soruya herhangi bir yanıt null olabilir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-144">Any response to a question may be null.</span></span> <span data-ttu-id="a40c3-145">Yanıtlayanlar bazı veya tüm soruları yanıtlamak için reddedebilirler.</span><span class="sxs-lookup"><span data-stu-id="a40c3-145">Respondents can decline to answer some or all questions.</span></span>

<span data-ttu-id="a40c3-146">İçinde C#programlamış olmanız durumunda, null olamayan örnekleri bildirmek için diğer fırsatları kaçırmış olabilecek `null` değerlerine izin veren başvuru türlerine alışkın olabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a40c3-146">If you've programmed in C#, you may be so accustomed to reference types that allow `null` values that you may have missed other opportunities to declare non-nullable instances:</span></span>

- <span data-ttu-id="a40c3-147">Soruların toplanması null atanamaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-147">The collection of questions should be non-nullable.</span></span>
- <span data-ttu-id="a40c3-148">Yanıtlayanlar koleksiyonu null atanamaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-148">The collection of respondents should be non-nullable.</span></span>

<span data-ttu-id="a40c3-149">Kodu yazarken, başvurular için varsayılan olarak null yapılamayan bir başvuru türünün, <xref:System.NullReferenceException>s ' y e yol açabilecek yaygın hataları önleyip bu şekilde olduğunu göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-149">As you write the code, you'll see that a non-nullable reference type as the default for references avoids common mistakes that could lead to <xref:System.NullReferenceException>s.</span></span> <span data-ttu-id="a40c3-150">Bu öğreticiden bir derste, hangi değişkenlerin `null`, hangilerinin olmadığı hakkında kararlar vermezsiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-150">One lesson from this tutorial is that you made decisions about which variables could or could not be `null`.</span></span> <span data-ttu-id="a40c3-151">Dil, bu kararları ifade etmek için sözdizimi sağlamadı.</span><span class="sxs-lookup"><span data-stu-id="a40c3-151">The language didn't provide syntax to express those decisions.</span></span> <span data-ttu-id="a40c3-152">Şimdi.</span><span class="sxs-lookup"><span data-stu-id="a40c3-152">Now it does.</span></span>

<span data-ttu-id="a40c3-153">Derlenecek uygulama aşağıdaki adımları yapar:</span><span class="sxs-lookup"><span data-stu-id="a40c3-153">The app you'll build does the following steps:</span></span>

1. <span data-ttu-id="a40c3-154">Bir anket oluşturur ve ona sorular ekler.</span><span class="sxs-lookup"><span data-stu-id="a40c3-154">Creates a survey and adds questions to it.</span></span>
1. <span data-ttu-id="a40c3-155">Anket için sahte rastgele bir yanıt veren kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a40c3-155">Creates a pseudo-random set of respondents for the survey.</span></span>
1. <span data-ttu-id="a40c3-156">Tamamlanan anket boyutu hedef numarasına ulaşıncaya kadar kişilere yanıtlayanlar.</span><span class="sxs-lookup"><span data-stu-id="a40c3-156">Contacts respondents until the completed survey size reaches the goal number.</span></span>
1. <span data-ttu-id="a40c3-157">Anket yanıtlarına önemli istatistikleri yazar.</span><span class="sxs-lookup"><span data-stu-id="a40c3-157">Writes out important statistics on the survey responses.</span></span>

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a><span data-ttu-id="a40c3-158">Null yapılabilir ve null yapılamayan türler ile anketi oluşturun</span><span class="sxs-lookup"><span data-stu-id="a40c3-158">Build the survey with nullable and non-nullable types</span></span>

<span data-ttu-id="a40c3-159">Yazacağınız ilk kod anketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a40c3-159">The first code you'll write creates the survey.</span></span> <span data-ttu-id="a40c3-160">Bir anket sorusu ve bir anket çalıştırması modellemek için sınıflar yazacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a40c3-160">You'll write classes to model a survey question and a survey run.</span></span> <span data-ttu-id="a40c3-161">Anketiniz, yanıtın biçimine göre ayırt edilen üç tür soru içerir: Evet/Hayır yanıt, sayı yanıtı ve metin yanıtları.</span><span class="sxs-lookup"><span data-stu-id="a40c3-161">Your survey has three types of questions, distinguished by the format of the answer: Yes/No answers, number answers, and text answers.</span></span> <span data-ttu-id="a40c3-162">`public SurveyQuestion` sınıfı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="a40c3-162">Create a `public SurveyQuestion` class:</span></span>

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

<span data-ttu-id="a40c3-163">Derleyici, her başvuru türü değişkeni bildirimini, etkin bir Nullable ek açıklama bağlamındaki kod için **null yapılamayan** bir başvuru türü olarak yorumlar.</span><span class="sxs-lookup"><span data-stu-id="a40c3-163">The compiler interprets every reference type variable declaration as a **non-nullable** reference type for code in an enabled nullable annotation context.</span></span> <span data-ttu-id="a40c3-164">Aşağıdaki kodda gösterildiği gibi soru metni ve soru türü için özellikler ekleyerek ilk uyarılarınızı görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a40c3-164">You can see your first warning by adding properties for the question text and the type of question, as shown in the following code:</span></span>

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

<span data-ttu-id="a40c3-165">`QuestionText`başlatılamadığından, derleyici null yapılamayan bir özelliğin başlatılmadığını belirten bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-165">Because you haven't initialized `QuestionText`, the compiler issues a warning that a non-nullable property hasn't been initialized.</span></span> <span data-ttu-id="a40c3-166">Tasarımınız, soru metninin null olmasını gerektirir, bu nedenle onu başlatmak için bir Oluşturucu ve `QuestionType` değeri de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-166">Your design requires the question text to be non-null, so you add a constructor to initialize it and the `QuestionType` value as well.</span></span> <span data-ttu-id="a40c3-167">Tamamlanmış sınıf tanımı aşağıdaki kod gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="a40c3-167">The finished class definition looks like the following code:</span></span>

[!code-csharp[DefineQuestion](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

<span data-ttu-id="a40c3-168">Oluşturucuyu eklemek uyarıyı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-168">Adding the constructor removes the warning.</span></span> <span data-ttu-id="a40c3-169">Oluşturucu bağımsız değişkeni aynı zamanda null atanamaz bir başvuru türüdür, bu nedenle derleyici hiçbir uyarı vermez.</span><span class="sxs-lookup"><span data-stu-id="a40c3-169">The constructor argument is also a non-nullable reference type, so the compiler doesn't issue any warnings.</span></span>

<span data-ttu-id="a40c3-170">Sonra, `SurveyRun` adlı `public` sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a40c3-170">Next, create a `public` class named `SurveyRun`.</span></span> <span data-ttu-id="a40c3-171">Bu sınıf, aşağıdaki kodda gösterildiği gibi `SurveyQuestion` nesnelerinin ve ankete soru ekleme yöntemlerinin bir listesini içerir:</span><span class="sxs-lookup"><span data-stu-id="a40c3-171">This class contains a list of `SurveyQuestion` objects and methods to add questions to the survey, as shown in the following code:</span></span>

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

<span data-ttu-id="a40c3-172">Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmalısınız veya derleyici bir uyarı yayınlar.</span><span class="sxs-lookup"><span data-stu-id="a40c3-172">As before, you must initialize the list object to a non-null value or the compiler issues a warning.</span></span> <span data-ttu-id="a40c3-173">`AddQuestion` ikinci aşırı yüklerinde hiçbir null denetim yoktur çünkü bunlar gerekli değildir: Bu değişkenin null değer atanamaz olduğunu bildirdiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-173">There are no null checks in the second overload of `AddQuestion` because they aren't needed: You've declared that variable to be non-nullable.</span></span> <span data-ttu-id="a40c3-174">Değeri `null` olamaz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-174">Its value can't be `null`.</span></span>

<span data-ttu-id="a40c3-175">Düzenleyicinizde *program.cs* 'e geçin ve `Main` ' in içeriğini aşağıdaki kod satırlarıyla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-175">Switch to *Program.cs* in your editor and replace the contents of `Main` with the following lines of code:</span></span>

[!code-csharp[AddQuestions](~/samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

<span data-ttu-id="a40c3-176">Projenin tamamı etkin bir null yapılabilir ek açıklama bağlamında olduğundan, null olamayan bir başvuru türü bekleyen herhangi bir yönteme `null` geçirdiğinizde uyarılar alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a40c3-176">Because the entire project is in an enabled nullable annotation context, you'll get warnings when you pass `null` to any method expecting a non-nullable reference type.</span></span> <span data-ttu-id="a40c3-177">`Main`için aşağıdaki satırı ekleyerek deneyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-177">Try it by adding the following line to `Main`:</span></span>

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a><span data-ttu-id="a40c3-178">Katılımcıları oluşturun ve ankete yanıt alın</span><span class="sxs-lookup"><span data-stu-id="a40c3-178">Create respondents and get answers to the survey</span></span>

<span data-ttu-id="a40c3-179">Sonra, ankete yanıtlar üreten kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="a40c3-179">Next, write the code that generates answers to the survey.</span></span> <span data-ttu-id="a40c3-180">Bu işlem birkaç küçük görevi kapsar:</span><span class="sxs-lookup"><span data-stu-id="a40c3-180">This process involves several small tasks:</span></span>

1. <span data-ttu-id="a40c3-181">Yanıtlayanın nesneleri üreten bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a40c3-181">Build a method that generates respondent objects.</span></span> <span data-ttu-id="a40c3-182">Bu kişiler, anketi doldurduonları temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a40c3-182">These represent people asked to fill out the survey.</span></span>
1. <span data-ttu-id="a40c3-183">Bir yanıtlayanın sorularını sormasına, yanıtları toplamaya veya bir yanıtlayanın yanıt vermedi olduğunu benzetmek için mantığı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a40c3-183">Build logic to simulate asking the questions to a respondent and collecting answers or noting that a respondent didn't answer.</span></span>
1. <span data-ttu-id="a40c3-184">Ankete yanıt veren yeterli sayıda yanıt verene kadar tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="a40c3-184">Repeat until enough respondents have answered the survey.</span></span>

<span data-ttu-id="a40c3-185">Bir anket yanıtını temsil eden bir sınıfa ihtiyacınız vardır, bu nedenle şimdi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-185">You'll need a class to represent a survey response, so add that now.</span></span> <span data-ttu-id="a40c3-186">Null yapılabilir desteğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-186">Enable nullable support.</span></span> <span data-ttu-id="a40c3-187">Aşağıdaki kodda gösterildiği gibi `Id` özelliği ve onu başlatan bir Oluşturucu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-187">Add an `Id` property and a constructor that initializes it, as shown in the following code:</span></span>

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

<span data-ttu-id="a40c3-188">Sonra, rastgele bir KIMLIK oluşturarak yeni katılımcılar oluşturmak için `static` yöntemi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-188">Next, add a `static` method to create new participants by generating a random ID:</span></span>

[!code-csharp[GenerateRespondents](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

<span data-ttu-id="a40c3-189">Bu sınıfın ana sorumluluğu, bir katılımcının yanıtlarını Anketteki sorulara üretmesidir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-189">The main responsibility of this class is to generate the responses for a participant to the questions in the survey.</span></span> <span data-ttu-id="a40c3-190">Bu sorumluluk birkaç adımdan daha sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a40c3-190">This responsibility has a few steps:</span></span>

1. <span data-ttu-id="a40c3-191">Ankete katılım isteyin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-191">Ask for participation in the survey.</span></span> <span data-ttu-id="a40c3-192">Kişi onay vermezse, eksik (veya null) bir yanıt döndürün.</span><span class="sxs-lookup"><span data-stu-id="a40c3-192">If the person doesn't consent, return a missing (or null) response.</span></span>
1. <span data-ttu-id="a40c3-193">Her soruyu sorun ve yanıtı kaydedin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-193">Ask each question and record the answer.</span></span> <span data-ttu-id="a40c3-194">Her cevap da eksik olabilir (veya null).</span><span class="sxs-lookup"><span data-stu-id="a40c3-194">Each answer may also be missing (or null).</span></span>

<span data-ttu-id="a40c3-195">`SurveyResponse` Sınıfınıza aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-195">Add the following code to your `SurveyResponse` class:</span></span>

[!code-csharp[AnswerSurvey](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

<span data-ttu-id="a40c3-196">Anket yanıtlarının depolaması, null olabileceğini belirten bir `Dictionary<int, string>?` ' dır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-196">The storage for the survey answers is a `Dictionary<int, string>?`, indicating that it may be null.</span></span> <span data-ttu-id="a40c3-197">Tasarım amacınızı, her ikisi de derleyiciye ve kodunuzu daha sonra okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-197">You're using the new language feature to declare your design intent, both to the compiler and to anyone reading your code later.</span></span> <span data-ttu-id="a40c3-198">Önce `null` değerini denetlemeden `surveyResponses` başvuru yaptıysanız bir derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a40c3-198">If you ever dereference `surveyResponses` without checking for the `null` value first, you'll get a compiler warning.</span></span> <span data-ttu-id="a40c3-199">Derleyici `surveyResponses` değişkeninin yukarıda null olmayan bir değere ayarlandığını belirleyebileceğinden `AnswerSurvey` yönteminde uyarı almanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a40c3-199">You don't get a warning in the `AnswerSurvey` method because the compiler can determine the `surveyResponses` variable was set to a non-null value above.</span></span>

<span data-ttu-id="a40c3-200">Eksik yanıtlar için `null` kullanmak, null yapılabilir başvuru türleriyle çalışmak için bir anahtar noktası vurgular: Amacınız tüm `null` değerlerini programınızdan kaldırmıyor.</span><span class="sxs-lookup"><span data-stu-id="a40c3-200">Using `null` for missing answers highlights a key point for working with nullable reference types: your goal isn't to remove all `null` values from your program.</span></span> <span data-ttu-id="a40c3-201">Bunun yerine amacınız, yazdığınız kodun tasarımınızın amacını ifade etmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-201">Rather, your goal is to ensure that the code you write expresses the intent of your design.</span></span> <span data-ttu-id="a40c3-202">Eksik değerler kodunuzda ifade etmek için gerekli bir kavramdır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-202">Missing values are a necessary concept to express in your code.</span></span> <span data-ttu-id="a40c3-203">`null` değeri, eksik değerleri ifade etmenin açık bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="a40c3-203">The `null` value is a clear way to express those missing values.</span></span> <span data-ttu-id="a40c3-204">Tüm `null` değerleri kaldırılmaya çalışılması, yalnızca `null`olmayan eksik değerleri ifade etmek için başka bir yol tanımlamaya neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="a40c3-204">Trying to remove all `null` values only leads to defining some other way to express those missing values without `null`.</span></span>

<span data-ttu-id="a40c3-205">Sonra, `SurveyRun` sınıfına `PerformSurvey` yöntemini yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-205">Next, you need to write the `PerformSurvey` method in the `SurveyRun` class.</span></span> <span data-ttu-id="a40c3-206">`SurveyRun` sınıfına aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-206">Add the following code in the `SurveyRun` class:</span></span>

[!code-csharp[PerformSurvey](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

<span data-ttu-id="a40c3-207">Burada, null yapılabilir `List<SurveyResponse>?` seçiminiz yanıtın null olabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-207">Here again, your choice of a nullable `List<SurveyResponse>?` indicates the response may be null.</span></span> <span data-ttu-id="a40c3-208">Bu, anketin henüz herhangi bir yanıtlayanlara verilmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-208">That indicates the survey hasn't been given to any respondents yet.</span></span> <span data-ttu-id="a40c3-209">Yanıt verenlerin yeterli olana kadar eklendiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-209">Notice that respondents are added until enough have consented.</span></span>

<span data-ttu-id="a40c3-210">Anketi çalıştırmanın son adımı, `Main` yönteminin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:</span><span class="sxs-lookup"><span data-stu-id="a40c3-210">The last step to run the survey is to add a call to perform the survey at the end of the `Main` method:</span></span>

[!code-csharp[RunSurvey](~/samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a><span data-ttu-id="a40c3-211">Anket yanıtlarını İnceleme</span><span class="sxs-lookup"><span data-stu-id="a40c3-211">Examine survey responses</span></span>

<span data-ttu-id="a40c3-212">Son adım, anket sonuçlarını görüntülemektir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-212">The last step is to display survey results.</span></span> <span data-ttu-id="a40c3-213">Yazdığınız sınıfların çoğuna kod ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-213">You'll add code to many of the classes you've written.</span></span> <span data-ttu-id="a40c3-214">Bu kod, null yapılabilir ve null yapılamayan başvuru türlerini ayırt etme değerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-214">This code demonstrates the value of distinguishing nullable and non-nullable reference types.</span></span> <span data-ttu-id="a40c3-215">Aşağıdaki iki Expression-Bodied üyesini `SurveyResponse` sınıfına ekleyerek başlayın:</span><span class="sxs-lookup"><span data-stu-id="a40c3-215">Start by adding the following two expression-bodied members to the `SurveyResponse` class:</span></span>

[!code-csharp[ReportResponses](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

<span data-ttu-id="a40c3-216">`surveyResponses` Nullable bir başvuru türü olduğundan, null denetimleri buna başvurulmadan önce gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a40c3-216">Because `surveyResponses` is a nullable reference type, null checks are necessary before de-referencing it.</span></span> <span data-ttu-id="a40c3-217">`Answer` yöntemi null yapılamayan bir dize döndürür. bu nedenle, null birleşim işlecini kullanarak eksik bir yanıtın durumunu kapsamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-217">The `Answer` method returns a non-nullable string, so we have to cover the case of a missing answer by using the null-coalescing operator.</span></span>

<span data-ttu-id="a40c3-218">Ardından, bu üç Expression-Bodied üyelerini `SurveyRun` sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-218">Next, add these three expression-bodied members to the `SurveyRun` class:</span></span>

[!code-csharp[ReportResults](~/samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

<span data-ttu-id="a40c3-219">`AllParticipants` üye, `respondents` değişkeninin null olabileceğini, ancak dönüş değerinin null olduğunu dikkate almalıdır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-219">The `AllParticipants` member must take into account that the `respondents` variable might be null, but the return value can't be null.</span></span> <span data-ttu-id="a40c3-220">`??` ve aşağıdaki boş diziyi kaldırarak bu ifadeyi değiştirirseniz, derleyici yöntemi `null` döndürebileceğini ve dönüş imzası null yapılamayan bir tür döndürdüğünü uyarır.</span><span class="sxs-lookup"><span data-stu-id="a40c3-220">If you change that expression by removing the `??` and the empty sequence that follows, the compiler warns you the method might return `null` and its return signature returns a non-nullable type.</span></span>

<span data-ttu-id="a40c3-221">Son olarak, aşağıdaki döngüyü `Main` yönteminin altına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-221">Finally, add the following loop at the bottom of the `Main` method:</span></span>

[!code-csharp[DisplaySurveyResults](~/samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

<span data-ttu-id="a40c3-222">Bu kodda `null` denetimleri gerekmez, çünkü hepsi null yapılamayan başvuru türleri döndürecek şekilde temel arabirimleri tasarlamış oldunuz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-222">You don't need any `null` checks in this code because you've designed the underlying interfaces so that they all return non-nullable reference types.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="a40c3-223">Kodu alın</span><span class="sxs-lookup"><span data-stu-id="a40c3-223">Get the code</span></span>

<span data-ttu-id="a40c3-224">Örnek deponuzdan, [CSharp/Nullabletanıtım](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründe bulunan [örnek](https://github.com/dotnet/samples) depomuza yönelik kodu alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a40c3-224">You can get the code for the finished tutorial from our [samples](https://github.com/dotnet/samples) repository in the [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) folder.</span></span>

<span data-ttu-id="a40c3-225">Null atanabilir ve null yapılamayan başvuru türleri arasında tür bildirimleri değiştirerek deneyin.</span><span class="sxs-lookup"><span data-stu-id="a40c3-225">Experiment by changing the type declarations between nullable and non-nullable reference types.</span></span> <span data-ttu-id="a40c3-226">Bunun, yanlışlıkla `null`başvurmamasını sağlamak için farklı uyarılar üretmesinin nasıl yapıldığını görün.</span><span class="sxs-lookup"><span data-stu-id="a40c3-226">See how that generates different warnings to ensure you don't accidentally dereference a `null`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a40c3-227">Sonraki adımlar</span><span class="sxs-lookup"><span data-stu-id="a40c3-227">Next steps</span></span>

<span data-ttu-id="a40c3-228">Mevcut bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirerek daha fazla bilgi edinin:</span><span class="sxs-lookup"><span data-stu-id="a40c3-228">Learn more by migrating an existing application to use nullable reference types:</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a40c3-229">Bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde yükseltme</span><span class="sxs-lookup"><span data-stu-id="a40c3-229">Upgrade an application to use nullable reference types</span></span>](upgrade-to-nullable-references.md)
