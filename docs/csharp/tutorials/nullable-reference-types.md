---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.technology: csharp-null-safety
ms.custom: mvc
ms.openlocfilehash: b00050c1d151b95e330f94eb9393a4031e47d5a8
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240073"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Öğretici: tasarım amacınızı null olabilen ve null yapılamayan başvuru türleriyle daha net bir şekilde Ifade edin

C#8,0, null olabilen değer türleri olan değer türlerini tamamlayan aynı şekilde başvuru türlerini tamamlayan [null yapılabilir başvuru türlerini](../nullable-references.md)tanıtır. Türe bir `?` ekleyerek **null olabilen bir başvuru türü** olarak bir değişken bildirirsiniz. Örneğin `string?`, null yapılabilir bir `string`temsil eder. Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Null yapılabilir ve null yapılamayan başvuru türlerini tasarımlarınız içine ekleyin
> - Kodunuzun tamamında null yapılabilir başvuru türü denetimlerini etkinleştirin.
> - Derleyicinin bu tasarım kararlarını zorladığı kodu yazın.
> - Kendi tasarımlarınızın Nullable başvuru özelliğini kullanın

## <a name="prerequisites"></a>Önkoşullar

Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8,0 derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Tasarımlarınız için null yapılabilir başvuru türleri ekleyin

Bu öğreticide, bir anketi çalıştıran modellerle ilgili bir kitaplık oluşturacaksınız. Kod, gerçek dünya kavramlarını temsil etmek için hem Nullable başvuru türlerini hem de null değer atanamaz başvuru türlerini kullanır. Anket soruları hiçbir şekilde null olamaz. Bir yanıtlayanın soru cevaplanmayı tercih edemeyebilir. Yanıtlar bu durumda `null` olabilir.

Bu örnek için yazdığınız kod, amacı ifade eder ve derleyici bu amacı zorunlu kılar.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Uygulamayı oluşturun ve null yapılabilir başvuru türlerini etkinleştirin

`dotnet new console`kullanarak, Visual Studio 'da veya komut satırından yeni bir konsol uygulaması oluşturun. Uygulamayı `NullableIntroduction`olarak adlandırın. Uygulamayı oluşturduktan sonra, tüm projenin etkinleştirilmiş bir **null yapılabilir ek açıklama bağlamında**derlendiğini belirtmeniz gerekir. *. Csproj* dosyasını açın ve `PropertyGroup` öğesine bir `Nullable` öğesi ekleyin. Değerini `enable` olarak ayarlayın. 8,0 projesinde bile **null yapılabilir başvuru türleri** özelliğini kabul etmeniz gerekir. C# Bunun nedeni, özellik açık olduğunda, mevcut başvuru değişkeni bildirimleri **null yapılamayan başvuru türleri**haline gelir. Bu karar, var olan kodun doğru null denetimleri olmayan sorunları bulmaya yardımcı olur, ancak özgün tasarım hedefini doğru bir şekilde yansıtmayabilir:

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

İçinde C#programlamış olmanız durumunda, null olamayan örnekleri bildirmek için diğer fırsatlara kaçırmış olabilecek `null` değerlerine izin veren başvuru türlerine alışkın olabilirsiniz:

- Soruların toplanması null atanamaz olmalıdır.
- Yanıtlayanlar koleksiyonu null atanamaz olmalıdır.

Kodu yazarken, başvurular için varsayılan olarak null yapılamayan bir başvuru türünün, <xref:System.NullReferenceException>s 'ye neden olabilecek yaygın hataları önleyip görebilineceksiniz. Bu öğreticiden bir derste, hangi değişkenlerin `null`, hangilerinin olmadığı hakkında kararlar vermezsiniz. Dil, bu kararları ifade etmek için sözdizimi sağlamadı. Şimdi.

Derlenecek uygulama aşağıdaki adımları yapar:

1. Bir anket oluşturur ve ona sorular ekler.
1. Anket için sahte rastgele bir yanıt veren kümesi oluşturur.
1. Tamamlanan anket boyutu hedef numarasına ulaşıncaya kadar kişilere yanıtlayanlar.
1. Anket yanıtlarına önemli istatistikleri yazar.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Null yapılabilir ve null yapılamayan türler ile anketi oluşturun

Yazacağınız ilk kod anketi oluşturur. Bir anket sorusu ve bir anket çalıştırması modellemek için sınıflar yazacaksınız. Anketiniz, yanıtın biçimine göre ayırt edilen üç tür soru içerir: Evet/Hayır yanıt, sayı yanıtı ve metin yanıtları. `public SurveyQuestion` sınıfı oluşturun:

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

`QuestionText`başlatılamadığından, derleyici null yapılamayan bir özelliğin başlatılmadığını belirten bir uyarı verir. Tasarımınız, soru metninin null olmasını gerektirir, bu nedenle onu başlatmak için bir Oluşturucu ve `QuestionType` değeri de ekleyebilirsiniz. Tamamlanmış sınıf tanımı aşağıdaki kod gibi görünür:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Oluşturucuyu eklemek uyarıyı kaldırır. Oluşturucu bağımsız değişkeni aynı zamanda null atanamaz bir başvuru türüdür, bu nedenle derleyici hiçbir uyarı vermez.

Sonra, `SurveyRun`adlı bir `public` sınıfı oluşturun. Bu sınıf, aşağıdaki kodda gösterildiği gibi `SurveyQuestion` nesne ve ankete soru ekleme yöntemlerinin bir listesini içerir:

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

Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmalısınız veya derleyici bir uyarı yayınlar. `AddQuestion` ikinci aşırı yüklerinde hiçbir null denetim yoktur çünkü bunlar gerekli değildir: Bu değişkenin null değer atanamaz olduğunu bildirdiniz. Değeri `null`olamaz.

Düzenleyicinizde *program.cs* 'e geçin ve `Main` içeriğini aşağıdaki kod satırlarıyla değiştirin:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Projenin tamamı etkin bir null yapılabilir ek açıklama bağlamında olduğundan, null olamayan bir başvuru türü bekleyen bir yönteme `null` geçirdiğinizde uyarılar alırsınız. `Main`için aşağıdaki satırı ekleyerek deneyin:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Katılımcıları oluşturun ve ankete yanıt alın

Sonra, ankete yanıtlar üreten kodu yazın. Bu işlem birkaç küçük görevi kapsar:

1. Yanıtlayanın nesneleri üreten bir yöntem oluşturun. Bu kişiler, anketi doldurduonları temsil eder.
1. Bir yanıtlayanın sorularını sormasına, yanıtları toplamaya veya bir yanıtlayanın yanıt vermedi olduğunu benzetmek için mantığı oluşturun.
1. Ankete yanıt veren yeterli sayıda yanıt verene kadar tekrarlayın.

Bir anket yanıtını temsil eden bir sınıfa ihtiyacınız vardır, bu nedenle şimdi ekleyin. Null yapılabilir desteğini etkinleştirin. Aşağıdaki kodda gösterildiği gibi, bir `Id` özelliği ve onu başlatan bir Oluşturucu ekleyin:

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

Sonra, rastgele bir KIMLIK oluşturarak yeni katılımcılar oluşturmak için bir `static` yöntemi ekleyin:

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Bu sınıfın ana sorumluluğu, bir katılımcının yanıtlarını Anketteki sorulara üretmesidir. Bu sorumluluk birkaç adımdan daha sahiptir:

1. Ankete katılım isteyin. Kişi onay vermezse, eksik (veya null) bir yanıt döndürün.
1. Her soruyu sorun ve yanıtı kaydedin. Her cevap da eksik olabilir (veya null).

`SurveyResponse` Sınıfınıza aşağıdaki kodu ekleyin:

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Anket yanıtları için depolama, null olabileceğini belirten bir `Dictionary<int, string>?`. Tasarım amacınızı, her ikisi de derleyiciye ve kodunuzu daha sonra okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz. Önce `null` değerini denetlemeden `surveyResponses` başvuru yaptıysanız bir derleyici uyarısı alırsınız. Derleyici `surveyResponses` değişkeninin yukarıda null olmayan bir değere ayarlandığını belirleyebileceğinden `AnswerSurvey` yönteminde uyarı almanız gerekmez.

Eksik yanıtlar için `null` kullanmak, null yapılabilir başvuru türleriyle çalışmak için bir anahtar noktası vurgular: Amacınız tüm `null` değerlerini programınızdan kaldırmıyor. Bunun yerine amacınız, yazdığınız kodun tasarımınızın amacını ifade etmek için gereklidir. Eksik değerler kodunuzda ifade etmek için gerekli bir kavramdır. `null` değeri, eksik değerleri ifade etmenin açık bir yoludur. Tüm `null` değerleri kaldırılmaya çalışılması, yalnızca `null`olmayan eksik değerleri ifade etmek için başka bir yol tanımlamaya neden oluyor.

Sonra, `SurveyRun` sınıfında `PerformSurvey` yöntemini yazmanız gerekir. `SurveyRun` sınıfına aşağıdaki kodu ekleyin:

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Burada, null yapılabilir `List<SurveyResponse>?` seçiminiz yanıtın null olabileceğini gösterir. Bu, anketin henüz herhangi bir yanıtlayanlara verilmediğini belirtir. Yanıt verenlerin yeterli olana kadar eklendiğine dikkat edin.

Anketi çalıştırmanın son adımı, `Main` yönteminin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Anket yanıtlarını İnceleme

Son adım, anket sonuçlarını görüntülemektir. Yazdığınız sınıfların çoğuna kod ekleyeceksiniz. Bu kod, null yapılabilir ve null yapılamayan başvuru türlerini ayırt etme değerini gösterir. Aşağıdaki iki Expression-Bodied üyesini `SurveyResponse` sınıfına ekleyerek başlayın:

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

`surveyResponses` Nullable bir başvuru türü olduğundan, null denetimleri buna başvurulmadan önce gereklidir. `Answer` yöntemi null yapılamayan bir dize döndürür. bu nedenle, null birleşim işlecini kullanarak eksik bir yanıtın durumunu kapsamalıdır.

Ardından, bu üç Expression-Bodied üyelerini `SurveyRun` sınıfına ekleyin:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

`AllParticipants` üye, `respondents` değişkeninin null olabileceğini, ancak dönüş değerinin null olduğunu dikkate almalıdır. `??` ve aşağıdaki boş diziyi kaldırarak bu ifadeyi değiştirirseniz, derleyici yöntemi `null` döndürebileceğini ve dönüş imzası null yapılamayan bir tür döndürdüğünü uyarır.

Son olarak, aşağıdaki döngüyü `Main` yönteminin altına ekleyin:

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Bu kodda herhangi bir `null` denetim gerekmez, çünkü hepsi null yapılamayan başvuru türleri döndürecek şekilde temel arabirimleri tasarlamış oldunuz.

## <a name="get-the-code"></a>Kodu alma

Örnek deponuzdan, [CSharp/Nullabletanıtım](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründe bulunan [örnek](https://github.com/dotnet/samples) depomuza yönelik kodu alabilirsiniz.

Null atanabilir ve null yapılamayan başvuru türleri arasında tür bildirimleri değiştirerek deneyin. Bunun, yanlışlıkla `null`başvurmamasını sağlamak için farklı uyarılar üretmesinin nasıl yapıldığını görün.

## <a name="next-steps"></a>Sonraki adımlar

Mevcut bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirerek daha fazla bilgi edinin:
> [!div class="nextstepaction"]
> [Bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde yükseltme](upgrade-to-nullable-references.md)
