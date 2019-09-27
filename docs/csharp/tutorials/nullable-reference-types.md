---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 6b127cce66f2f9ced3cee29336b39e2976e03619
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332338"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Öğretici: Null yapılabilir ve null yapılamayan başvuru türleriyle tasarım amacınızı daha net bir şekilde ifade edin

C#8, null olabilen değer türleri için aynı şekilde, başvuru türlerini tamamlayan **null yapılabilir başvuru türlerini**tanıtır. Bir`?` değişkeni türüne ekleyerek **null atanabilir bir başvuru türü** olarak bildirirsiniz. Örneğin, `string?` null yapılabilen bir değeri `string`temsil eder. Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir.

Bu öğreticide, aşağıdakileri nasıl yapacağınızı öğreneceksiniz:

> [!div class="checklist"]
>
> - Null yapılabilir ve null yapılamayan başvuru türlerini tasarımlarınız içine ekleyin
> - Kodunuzun tamamında null yapılabilir başvuru türü denetimlerini etkinleştirin.
> - Derleyicinin bu tasarım kararlarını zorladığı kodu yazın.
> - Kendi tasarımlarınızın Nullable başvuru özelliğini kullanın

## <a name="prerequisites"></a>Önkoşullar

C# 8,0 Beta derleyicisi dahil olmak üzere, makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8 Beta derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Tasarımlarınız için null yapılabilir başvuru türleri ekleyin

Bu öğreticide, bir anketi çalıştıran modellerle ilgili bir kitaplık oluşturacaksınız. Kod, gerçek dünya kavramlarını temsil etmek için hem Nullable başvuru türlerini hem de null değer atanamaz başvuru türlerini kullanır. Anket soruları hiçbir şekilde null olamaz. Bir yanıtlayanın soru cevaplanmayı tercih edemeyebilir. Bu durumda yanıtlar null olabilir.

Bu örnek için yazdığınız kod, amacı ifade eder ve derleyici bu amacı zorunlu kılar.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Uygulamayı oluşturun ve null yapılabilir başvuru türlerini etkinleştirin

Visual Studio 'da ya da kullanarak `dotnet new console`komut satırından yeni bir konsol uygulaması oluşturun. Uygulamayı `NullableIntroduction`adlandırın. Uygulamayı oluşturduktan sonra 8 Beta özelliklerini etkinleştirmeniz C# gerekir. Dosyasını açın ve `PropertyGroup` öğeye bir `LangVersion` öğe ekleyin. `csproj` 8 projesinde bile **null yapılabilir başvuru türleri** özelliğini kabul etmeniz gerekir. C# Bunun nedeni, özellik açık olduğunda, mevcut başvuru değişkeni bildirimleri **null yapılamayan başvuru türleri**haline gelir. Bu karar, mevcut kodun doğru null denetimleri olmayan sorunları bulmaya yardımcı olur, ancak özgün tasarım amacınızı doğru bir şekilde yansıtmayabilir. `Nullable` Öğesiniöğesiniöğesine`enable`ayarlayarak özelliğini açın:

```xml
<LangVersion>8.0</LangVersion>
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Uygulama için türleri tasarlama

Bu anket uygulaması için birkaç sınıf oluşturulması gerekir:

- Soruların listesini modelleyen bir sınıf.
- Anket için iletişim kurulan kişilerin listesini modelleyen sınıf.
- Anketi geçen bir kişiden yanıtları modelleyen sınıf.

Bu türler, hangi üyelerin gerekli olduğunu ve hangi üyelerin isteğe bağlı olduğunu ifade etmek için hem null yapılabilir hem de null yapılamayan başvuru türlerini kullanır. Null yapılabilir başvuru türleri, tasarım amacını açıkça iletir:

- Anketin parçası olan sorular hiçbir şekilde null olamaz: Boş bir soru sormasına hiçbir fikir vermez.
- Yanıtlayanlar hiçbir şekilde null olamaz. Görüştüğünüz kişileri, hatta katılmayı reddeden yanıt verenleri izlemek isteyeceksiniz.
- Bir soruya herhangi bir yanıt null olabilir. Yanıtlayanlar bazı veya tüm soruları yanıtlamak için reddedebilirler.

İçinde C#programlamış olmanız durumunda, null olamayan örnekleri bildirmek için diğer fırsatlara kaçırmış olabilecek null değerlere izin veren başvuru türlerine alışkın olabilirsiniz:

- Soruların toplanması null atanamaz olmalıdır.
- Yanıtlayanlar koleksiyonu null atanamaz olmalıdır.

Kodu yazarken, başvurular için varsayılan olarak null yapılamayan bir başvuru türünün, null başvuru özel durumlarına yol açabilecek yaygın hataları önlediği görürsünüz. Bu öğreticiden bir derste, hangi değişkenlerin null olması gerektiğine dair kararlar vermezsiniz. Dil, bu kararları ifade etmek için sözdizimi sağlamadı. Şimdi.

Derlenecek uygulama aşağıdaki adımları kullanacaktır:

1. Bir anket oluşturun ve buna sorular ekleyin.
1. Anket için sahte rastgele bir yanıt veren kümesi oluşturun.
1. Tamamlanan anket boyutu hedef numarasına ulaşıncaya kadar yanıtlayanların iletişim kurun.
1. Anket yanıtlarına önemli istatistikler yazın.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Null yapılabilir ve null yapılamayan türler ile anketi oluşturun

Yazacağınız ilk kod anketi oluşturur. Bir anket sorusu ve bir anket çalıştırması modellemek için sınıflar yazacaksınız. Anketiniz, yanıt biçimiyle ayırt edilen üç tür soru içerir: Evet/Hayır yanıt, sayı yanıtı ve metin yanıtı. `public` Sınıf oluşturun`SurveyQuestion` :

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Derleyici, her başvuru türü değişken bildirimini, null yapılabilir etkin bağlamdaki kod için **null yapılamayan** bir başvuru türü olarak yorumlar. Aşağıdaki kodda gösterildiği gibi soru metni ve soru türü için özellikler ekleyerek ilk uyarılarınızı görebilirsiniz:

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

Başlatılamamış `QuestionText`, derleyici null yapılamayan bir özelliğin başlatılmadığını belirten bir uyarı verir. Tasarımınız, soru metninin null olmasını gerektirir, bu nedenle onu ve `QuestionType` değeri başlatmak için bir Oluşturucu eklersiniz. Tamamlanmış sınıf tanımı aşağıdaki kod gibi görünür:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Oluşturucuyu eklemek uyarıyı kaldırır. Oluşturucu bağımsız değişkeni aynı zamanda null atanamaz bir başvuru türüdür, bu nedenle derleyici hiçbir uyarı vermez.

Ardından adlı `public` `SurveyRun`bir sınıf oluşturun. Bu sınıf, aşağıdaki kodda gösterildiği `SurveyQuestion` gibi ankete soru eklemek için nesnelerin ve yöntemlerin bir listesini içerir:

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

Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmalısınız veya derleyici bir uyarı yayınlar. İkinci aşırı yüklemesi `AddQuestion` için gerekli olmadıklarından null denetimleri yok: Bu değişkenin null değer atanamayan olduğunu bildirdiniz. Değeri olamaz `null`.

Düzenleyicinizde `Program.cs` öğesine geçin ve `Main` içeriğini aşağıdaki kod satırlarıyla değiştirin:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Projenin tamamı null yapılabilir etkin bir bağlamda olduğundan, null olamayan bir başvuru türü bekleyen bir yönteme geçiş `null` yaptığınızda uyarılar alırsınız. Aşağıdaki satırı öğesine `Main`ekleyerek deneyin:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Katılımcıları oluşturun ve ankete yanıt alın

Sonra, ankete yanıtlar üreten kodu yazın. Bu işlem birkaç küçük görevi kapsar:

1. Yanıtlayanın nesneleri üreten bir yöntem oluşturun. Bu kişiler, anketi doldurduonları temsil eder.
1. Bir yanıtlayanın sorularını sormasına, yanıtları toplamaya veya bir yanıtlayanın yanıt vermedi olduğunu benzetmek için mantığı oluşturun.
1. Ankete yanıt veren yeterli sayıda yanıt verene kadar tekrarlayın.

Bir anket yanıtını temsil eden bir sınıfa ihtiyacınız vardır, bu nedenle şimdi ekleyin. Null yapılabilir desteğini etkinleştirin. Aşağıdaki kodda `Id` gösterildiği gibi, bir özellik ve onu başlatan bir Oluşturucu ekleyin:

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

Sonra, rastgele bir `static` kimlik oluşturarak yeni katılımcılar oluşturmak için bir yöntem ekleyin:

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Bu sınıfın ana sorumluluğu, bir katılımcının yanıtlarını Anketteki sorulara üretmesidir. Bu sorumluluk birkaç adımdan daha sahiptir:

1. Ankete katılım isteyin. Kişi onay vermezse, eksik (veya null) bir yanıt döndürün.
1. Her soruyu sorun ve yanıtı kaydedin. Her cevap da eksik olabilir (veya null).

Sınıfınıza `SurveyResponse` aşağıdaki kodu ekleyin:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Anket yanıtlarının depolaması, null olabileceğini belirten bir `Dictionary<int, string>?`' dır. Tasarım amacınızı, her ikisi de derleyiciye ve kodunuzu daha sonra okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz. İlk olarak null değeri `surveyResponses` denetlemeden başvuru yaptıysanız bir derleyici uyarısı alırsınız. Derleyici, değişkenin, `AnswerSurvey` `surveyResponses` yukarıda null olmayan bir değere ayarlandığını belirleyebildiğinden, yöntemde uyarı almanız gerekmez.

Eksik `null` yanıtlar için kullanmak, null yapılabilir başvuru türleriyle çalışmak için bir anahtar noktası vurgular: Amacınız tüm `null` değerleri programınızdan kaldırmıyor. Bunun yerine amacınız, yazdığınız kodun tasarımınızın amacını ifade etmek için gereklidir. Eksik değerler kodunuzda ifade etmek için gerekli bir kavramdır. Bu `null` değer, eksik değerleri ifade etmenin açık bir yoludur. Tüm `null` değerleri kaldırmaya çalışmak, yalnızca bu eksik değerleri olmadan `null`ifade etmek için başka bir yol tanımlamaya yönlendirir.

Daha sonra, `PerformSurvey` yöntemi `SurveyRun` sınıfına yazmanız gerekir. `SurveyRun` Sınıfına aşağıdaki kodu ekleyin:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Burada, null yapılabilir `List<SurveyResponse>?` seçiminiz, yanıtın null olabileceğini gösterir. Bu, anketin henüz herhangi bir yanıtlayanlara verilmediğini belirtir. Yanıt verenlerin yeterli olana kadar eklendiğine dikkat edin.

Anketi çalıştırmanın son adımı, `Main` yöntemin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Anket yanıtlarını İnceleme

Son adım, anket sonuçlarını görüntülemektir. Yazdığınız sınıfların çoğuna kod ekleyeceksiniz. Bu kod, null yapılabilir ve null yapılamayan başvuru türlerini ayırt etme değerini gösterir. Aşağıdaki iki Expression-Bodied member `SurveyResponse` öğesini ekleyerek başlatın:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

`surveyResponses` Null olamayan bir başvuru türü olduğundan, kendisine başvurulmadan önce hiçbir denetim gerekli değildir. Yöntemi null yapılamayan bir dize döndürür, `GetValueOrDefault` bu nedenle varsayılan değer için ikinci bir bağımsız değişken alan aşırı yüklemesini seçin. `Answer`

Ardından, bu üç Expression-Bodied üyelerini `SurveyRun` sınıfına ekleyin:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Üye, `respondents` değişkenin null olabileceğini, ancak dönüş değerinin null olduğunu dikkate almalıdır. `AllParticipants` Bu ifadeyi `??` ve aşağıdaki boş diziyi kaldırarak değiştirirseniz, derleyici yöntemin döndürebileceğini `null` ve dönüş imzası null yapılamayan bir tür döndürdüğünü uyarır.

Son olarak, aşağıdaki döngüyü `Main` yönteminin altına ekleyin:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Bu kodda herhangi bir `null` denetim yapmanız gerekmez, çünkü hepsi null yapılamayan başvuru türleri döndürecek şekilde temel arabirimleri tasarlamış oldunuz.

## <a name="get-the-code"></a>Kodu alın

Örnek deponuzdan, [CSharp/Nullabletanıtım](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründe bulunan [örnek](https://github.com/dotnet/samples) depomuza yönelik kodu alabilirsiniz.

Null atanabilir ve null yapılamayan başvuru türleri arasında tür bildirimleri değiştirerek deneyin. Bunun, yanlışlıkla `null`başvurmayabilmeniz için farklı uyarılar üretmesinin nasıl yapıldığını öğrenin.

## <a name="next-steps"></a>Sonraki adımlar

Mevcut bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirerek daha fazla bilgi edinin:
> [!div class="nextstepaction"]
> [Bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde yükseltme](upgrade-to-nullable-references.md)
