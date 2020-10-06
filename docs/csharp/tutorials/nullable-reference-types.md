---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: 70e6a7a906bc9a35918cf3e26c3e23bd0cfdafde
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91755856"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Öğretici: tasarım amacınızı null olabilen ve null yapılamayan başvuru türleriyle daha net bir şekilde Ifade edin

C# 8,0, null olabilen değer türlerindeki değer türlerini tamamlayan aynı şekilde başvuru türlerini tamamlayan [null yapılabilir başvuru türlerini](../nullable-references.md)tanıtır. Bir değişkeni türüne ekleyerek **null atanabilir bir başvuru türü** olarak bildirirsiniz `?` . Örneğin, `string?` null yapılabilen bir değeri temsil eder `string` . Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir.

Bu öğreticide aşağıdakilerin nasıl yapılacağını öğreneceksiniz:

> [!div class="checklist"]
>
> - Null yapılabilir ve null yapılamayan başvuru türlerini tasarımlarınız içine ekleyin
> - Kodunuzun tamamında null yapılabilir başvuru türü denetimlerini etkinleştirin.
> - Derleyicinin bu tasarım kararlarını zorladığı kodu yazın.
> - Kendi tasarımlarınızın Nullable başvuru özelliğini kullanın

## <a name="prerequisites"></a>Ön koşullar

C# 8,0 derleyicisi dahil olmak üzere makinenizi .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8,0 derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.

Bu öğreticide, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Tasarımlarınız için null yapılabilir başvuru türleri ekleyin

Bu öğreticide, bir anketi çalıştıran modellerle ilgili bir kitaplık oluşturacaksınız. Kod, gerçek dünya kavramlarını temsil etmek için hem Nullable başvuru türlerini hem de null değer atanamaz başvuru türlerini kullanır. Anket soruları hiçbir şekilde null olamaz. Bir yanıtlayanın soru cevaplanmayı tercih edemeyebilir. Yanıtlar `null` Bu durumda olabilir.

Bu örnek için yazdığınız kod, amacı ifade eder ve derleyici bu amacı zorunlu kılar.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Uygulamayı oluşturun ve null yapılabilir başvuru türlerini etkinleştirin

Visual Studio 'da ya da kullanarak komut satırından yeni bir konsol uygulaması oluşturun `dotnet new console` . Uygulamayı adlandırın `NullableIntroduction` . Uygulamayı oluşturduktan sonra, tüm projenin etkinleştirilmiş bir **null yapılabilir ek açıklama bağlamında**derlendiğini belirtmeniz gerekir. *. Csproj* dosyasını açın ve öğesine bir `Nullable` öğesi ekleyin `PropertyGroup` . Değerini `enable` olarak ayarlayın. C# 8,0 projelerinde bile **null yapılabilir başvuru türleri** özelliğini kabul etmeniz gerekir. Bunun nedeni, özellik açık olduğunda, mevcut başvuru değişkeni bildirimleri **null yapılamayan başvuru türleri**haline gelir. Bu karar, var olan kodun doğru null denetimleri olmayan sorunları bulmaya yardımcı olur, ancak özgün tasarım hedefini doğru bir şekilde yansıtmayabilir:

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Uygulama için türleri tasarlama

Bu anket uygulaması için birkaç sınıf oluşturulması gerekir:

- Soruların listesini modelleyen bir sınıf.
- Anket için iletişim kurulan kişilerin listesini modelleyen sınıf.
- Anketi geçen bir kişiden yanıtları modelleyen sınıf.

Bu türler, hangi üyelerin gerekli olduğunu ve hangi üyelerin isteğe bağlı olduğunu ifade etmek için hem null yapılabilir hem de null yapılamayan başvuru türlerini kullanır. Null yapılabilir başvuru türleri, tasarım amacını açıkça iletir:

- Anketin parçası olan sorular hiçbir şekilde null olamaz: boş bir soru sormasına hiçbir fikir vermez.
- Yanıtlayanlar hiçbir şekilde null olamaz. Görüştüğünüz kişileri, hatta katılmayı reddeden yanıt verenleri izlemek isteyeceksiniz.
- Bir soruya herhangi bir yanıt null olabilir. Yanıtlayanlar bazı veya tüm soruları yanıtlamak için reddedebilirler.

C# dilinde programlediyseniz, `null` null olamayan örnekleri bildirmek için diğer fırsatlara kaçırmış olabilecek değerlere izin veren başvuru türlerine alışkın olabilirsiniz:

- Soruların toplanması null atanamaz olmalıdır.
- Yanıtlayanlar koleksiyonu null atanamaz olmalıdır.

Kodu yazarken, başvurular için varsayılan olarak null yapılamayan bir başvuru türünün, s 'ye neden olabilecek yaygın hataları önleyip görebilineceksiniz <xref:System.NullReferenceException> . Bu öğreticiden bir derste, hangi değişkenlerin veya olmaması gerektiğine dair kararlar vermezsiniz `null` . Dil, bu kararları ifade etmek için sözdizimi sağlamadı. Şimdi.

Derlenecek uygulama aşağıdaki adımları yapar:

1. Bir anket oluşturur ve ona sorular ekler.
1. Anket için sahte rastgele bir yanıt veren kümesi oluşturur.
1. Tamamlanan anket boyutu hedef numarasına ulaşıncaya kadar kişilere yanıtlayanlar.
1. Anket yanıtlarına önemli istatistikleri yazar.

## <a name="build-the-survey-with-nullable-and-non-nullable-reference-types"></a>Null yapılabilir ve null yapılamayan başvuru türleriyle anketi oluşturun

Yazacağınız ilk kod anketi oluşturur. Bir anket sorusu ve bir anket çalıştırması modellemek için sınıflar yazacaksınız. Anketiniz, yanıtın biçimine göre ayırt edilen üç tür soru içerir: Evet/Hayır yanıt, sayı yanıtı ve metin yanıtları. Sınıf oluşturun `public SurveyQuestion` :

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Derleyici, her başvuru türü değişkeni bildirimini, etkin bir Nullable ek açıklama bağlamındaki kod için **null yapılamayan** bir başvuru türü olarak yorumlar. Aşağıdaki kodda gösterildiği gibi soru metni ve soru türü için özellikler ekleyerek ilk uyarılarınızı görebilirsiniz:

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

Başlatılamamış `QuestionText` , derleyici null yapılamayan bir özelliğin başlatılmadığını belirten bir uyarı verir. Tasarımınız, soru metninin null olmasını gerektirir, bu nedenle onu ve değeri başlatmak için bir Oluşturucu eklersiniz `QuestionType` . Tamamlanmış sınıf tanımı aşağıdaki kod gibi görünür:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Oluşturucuyu eklemek uyarıyı kaldırır. Oluşturucu bağımsız değişkeni aynı zamanda null atanamaz bir başvuru türüdür, bu nedenle derleyici hiçbir uyarı vermez.

Ardından `public` adlı bir sınıf oluşturun `SurveyRun` . Bu sınıf, `SurveyQuestion` aşağıdaki kodda gösterildiği gibi ankete soru eklemek için nesnelerin ve yöntemlerin bir listesini içerir:

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

Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmalısınız veya derleyici bir uyarı yayınlar. İkinci aşırı yüklemesi için gerekli olmadıkları için null denetimleri yok `AddQuestion` : Bu değişkenin null değer atanamaz olduğunu bildirdiniz. Değeri olamaz `null` .

Düzenleyicinizde *program.cs* 'e geçin ve içeriğini `Main` Aşağıdaki kod satırlarıyla değiştirin:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Projenin tamamı etkinleştirilmiş bir null yapılabilir ek açıklama bağlamında olduğundan, `null` null olamayan bir başvuru türü bekleyen bir yönteme geçiş yaptığınızda uyarılar alırsınız. Aşağıdaki satırı öğesine ekleyerek deneyin `Main` :

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Katılımcıları oluşturun ve ankete yanıt alın

Sonra, ankete yanıtlar üreten kodu yazın. Bu işlem birkaç küçük görevi kapsar:

1. Yanıtlayanın nesneleri üreten bir yöntem oluşturun. Bu kişiler, anketi doldurduonları temsil eder.
1. Bir yanıtlayanın sorularını sormasına, yanıtları toplamaya veya bir yanıtlayanın yanıt vermedi olduğunu benzetmek için mantığı oluşturun.
1. Ankete yanıt veren yeterli sayıda yanıt verene kadar tekrarlayın.

Bir anket yanıtını temsil eden bir sınıfa ihtiyacınız vardır, bu nedenle şimdi ekleyin. Null yapılabilir desteğini etkinleştirin. `Id`Aşağıdaki kodda gösterildiği gibi, bir özellik ve onu başlatan bir Oluşturucu ekleyin:

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

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Bu sınıfın ana sorumluluğu, bir katılımcının yanıtlarını Anketteki sorulara üretmesidir. Bu sorumluluk birkaç adımdan daha sahiptir:

1. Ankete katılım isteyin. Kişi onay vermezse, eksik (veya null) bir yanıt döndürün.
1. Her soruyu sorun ve yanıtı kaydedin. Her cevap da eksik olabilir (veya null).

Sınıfınıza aşağıdaki kodu ekleyin `SurveyResponse` :

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Anket yanıtlarının depolaması `Dictionary<int, string>?` , null olabileceğini belirten bir ' dır. Tasarım amacınızı, her ikisi de derleyiciye ve kodunuzu daha sonra okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz. `surveyResponses`Önce değeri denetlemeden başvuru yaptıysanız `null` bir derleyici uyarısı alırsınız. `AnswerSurvey`Derleyici, `surveyResponses` değişkenin, yukarıda null olmayan bir değere ayarlandığını belirleyebildiğinden, yöntemde uyarı almanız gerekmez.

`null`Eksik yanıtlar için kullanmak, null yapılabilir başvuru türleriyle çalışmak için bir anahtar noktası vurgular: Amacınız tüm `null` değerleri programınızdan kaldırmıyor. Bunun yerine amacınız, yazdığınız kodun tasarımınızın amacını ifade etmek için gereklidir. Eksik değerler kodunuzda ifade etmek için gerekli bir kavramdır. `null`Bu değer, eksik değerleri ifade etmenin açık bir yoludur. Tüm değerleri kaldırmaya çalışmak, `null` yalnızca bu eksik değerleri olmadan ifade etmek için başka bir yol tanımlamaya yönlendirir `null` .

Daha sonra, yöntemi sınıfına yazmanız gerekir `PerformSurvey` `SurveyRun` . Sınıfına aşağıdaki kodu ekleyin `SurveyRun` :

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Burada, null yapılabilir seçiminiz, `List<SurveyResponse>?` yanıtın null olabileceğini gösterir. Bu, anketin henüz herhangi bir yanıtlayanlara verilmediğini belirtir. Yanıt verenlerin yeterli olana kadar eklendiğine dikkat edin.

Anketi çalıştırmanın son adımı, yöntemin sonunda anketi gerçekleştirmek için bir çağrı eklemektir `Main` :

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Anket yanıtlarını İnceleme

Son adım, anket sonuçlarını görüntülemektir. Yazdığınız sınıfların çoğuna kod ekleyeceksiniz. Bu kod, null yapılabilir ve null yapılamayan başvuru türlerini ayırt etme değerini gösterir. Aşağıdaki iki Expression-Bodied member öğesini ekleyerek başlatın `SurveyResponse` :

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Null `surveyResponses` olabilen bir başvuru türü olduğundan, null denetimleri buna başvurulmadan önce gereklidir. `Answer`Yöntemi null yapılamayan bir dize döndürür. bu nedenle, null birleşim işlecini kullanarak eksik bir yanıtın durumunu kapsaymalıdır.

Ardından, bu üç Expression-Bodied üyelerini `SurveyRun` sınıfına ekleyin:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

`AllParticipants`Üye, `respondents` değişkenin null olabileceğini, ancak dönüş değerinin null olduğunu dikkate almalıdır. Bu ifadeyi `??` ve aşağıdaki boş diziyi kaldırarak değiştirirseniz, derleyici yöntemin döndürebileceğini `null` ve dönüş imzası null yapılamayan bir tür döndürdüğünü uyarır.

Son olarak, aşağıdaki döngüyü yönteminin altına ekleyin `Main` :

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Bu kodda herhangi bir `null` Denetim yapmanız gerekmez, çünkü hepsi null yapılamayan başvuru türleri döndürecek şekilde temel arabirimleri tasarlamış oldunuz.

## <a name="get-the-code"></a>Kodu alma

Örnek deponuzdan, [CSharp/Nullabletanıtım](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründe bulunan [örnek](https://github.com/dotnet/samples) depomuza yönelik kodu alabilirsiniz.

Null atanabilir ve null yapılamayan başvuru türleri arasında tür bildirimleri değiştirerek deneyin. Bunun, yanlışlıkla başvurmayabilmeniz için farklı uyarılar üretmesinin nasıl yapıldığını öğrenin `null` .

## <a name="next-steps"></a>Sonraki adımlar

Mevcut bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirerek daha fazla bilgi edinin:
> [!div class="nextstepaction"]
> [Bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde yükseltme](upgrade-to-nullable-references.md)

Entity Framework kullanırken null yapılabilir başvuru türü kullanmayı öğrenin:
> [Entity Framework Core temelleri: null yapılabilir başvuru türleriyle çalışma](https://docs.microsoft.com/en-us/ef/core/miscellaneous/nullable-reference-types)
