---
title: Null yapılabilir başvuru türleriyle tasarım
description: Bu gelişmiş öğretici, null yapılabilir başvuru türlerine giriş sağlar. Başvuru değerleri null olduğunda ve derleyicinin null olmadıklarında zorunlu olmadığı durumlarda tasarım amacınızı ifade etmek için bilgi edineceksiniz.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 5327a9babdf080a535e292cdcefba6da9d0a725b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834065"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Öğretici: tasarım amacınızı null olabilen ve null yapılamayan başvuru türleriyle daha net bir şekilde Ifade edin

C#8, null olabilen değer türleri için aynı şekilde, başvuru türlerini tamamlayan **null yapılabilir başvuru türlerini**tanıtır. Türe bir `?` ekleyerek **null olabilen bir başvuru türü** olarak bir değişken bildirirsiniz. Örneğin `string?`, Nullable `string` temsil eder. Tasarım amacınızı daha net bir şekilde ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olması gerekir*, bazılarında *bir değer eksik*olabilir.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Null yapılabilir ve null yapılamayan başvuru türlerini tasarımlarınız içine ekleyin
> - Kodunuzun tamamında null yapılabilir başvuru türü denetimlerini etkinleştirin.
> - Derleyicinin bu tasarım kararlarını zorladığı kodu yazın.
> - Kendi tasarımlarınızın Nullable başvuru özelliğini kullanın

## <a name="prerequisites"></a>Önkoşullar

Makinenizi, C# 8,0 derleyicisi dahil .NET Core çalıştıracak şekilde ayarlamanız gerekir. C# 8 Beta derleyicisi, [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.

Bu öğreticide, Visual Studio veya C# .NET Core CLI dahil olmak üzere, .net hakkında bilgi sahibi olduğunuz varsayılır.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Tasarımlarınız için null yapılabilir başvuru türleri ekleyin

Bu öğreticide, bir anketi çalıştıran modellerle ilgili bir kitaplık oluşturacaksınız. Kod, gerçek dünya kavramlarını temsil etmek için hem Nullable başvuru türlerini hem de null değer atanamaz başvuru türlerini kullanır. Anket soruları hiçbir şekilde null olamaz. Bir yanıtlayanın soru cevaplanmayı tercih edemeyebilir. Bu durumda yanıtlar null olabilir.

Bu örnek için yazdığınız kod, amacı ifade eder ve derleyici bu amacı zorunlu kılar.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Uygulamayı oluşturun ve null yapılabilir başvuru türlerini etkinleştirin

Visual Studio 'da ya da `dotnet new console` kullanarak komut satırından yeni bir konsol uygulaması oluşturun. @No__t-0 ' a kadar uygulamayı adlandırın. Uygulamayı oluşturduktan sonra 8 Beta özelliklerini etkinleştirmeniz C# gerekir. @No__t-0 dosyasını açın ve `PropertyGroup` öğesine bir `LangVersion` öğesi ekleyin. 8 projesinde bile **null yapılabilir başvuru türleri** özelliğini kabul etmeniz gerekir. C# Bunun nedeni, özellik açık olduğunda, mevcut başvuru değişkeni bildirimleri **null yapılamayan başvuru türleri**haline gelir. Bu karar, mevcut kodun doğru null denetimleri olmayan sorunları bulmaya yardımcı olur, ancak özgün tasarım amacınızı doğru bir şekilde yansıtmayabilir. @No__t-0 öğesini `enable` olarak ayarlayarak özelliği açabilirsiniz:

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

- Anketin parçası olan sorular hiçbir şekilde null olamaz: boş bir soru sormasına hiçbir fikir vermez.
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

Yazacağınız ilk kod anketi oluşturur. Bir anket sorusu ve bir anket çalıştırması modellemek için sınıflar yazacaksınız. Anketiniz, yanıtın biçimine göre ayırt edilen üç tür soru içerir: Evet/Hayır yanıt, sayı yanıtı ve metin yanıtları. @No__t-0 `SurveyQuestion` sınıfı oluşturun:

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

@No__t-0 ' ı başlamadıysanız, derleyici null yapılamayan bir özelliğin başlatılmadığını belirten bir uyarı verir. Tasarımınız, soru metninin null olmasını gerektirir, bu nedenle onu başlatmak için bir Oluşturucu ve `QuestionType` değeri de ekleyebilirsiniz. Tamamlanmış sınıf tanımı aşağıdaki kod gibi görünür:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Oluşturucuyu eklemek uyarıyı kaldırır. Oluşturucu bağımsız değişkeni aynı zamanda null atanamaz bir başvuru türüdür, bu nedenle derleyici hiçbir uyarı vermez.

Sonra, `SurveyRun` adlı `public` sınıfı oluşturun. Bu sınıf, aşağıdaki kodda gösterildiği gibi `SurveyQuestion` nesnelerinin ve ankete soru ekleme yöntemlerinin bir listesini içerir:

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

Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmalısınız veya derleyici bir uyarı yayınlar. @No__t-0 ' ın ikinci aşırı yüklemesiyle ilgili hiçbir null denetim yoktur çünkü bunlar gerekli değildir: Bu değişkenin null değer atanamaz olduğunu bildirdiniz. Değeri `null` olamaz.

Düzenleyicinizde `Program.cs` ' a geçin ve `Main` ' in içeriğini aşağıdaki kod satırlarıyla değiştirin:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Projenin tamamı null yapılabilir etkin bir bağlamda olduğundan, null olamayan bir başvuru türü bekleyen herhangi bir yönteme `null` geçirdiğinizde uyarılar alırsınız. @No__t-0 ' a aşağıdaki satırı ekleyerek deneyin:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Katılımcıları oluşturun ve ankete yanıt alın

Sonra, ankete yanıtlar üreten kodu yazın. Bu işlem birkaç küçük görevi kapsar:

1. Yanıtlayanın nesneleri üreten bir yöntem oluşturun. Bu kişiler, anketi doldurduonları temsil eder.
1. Bir yanıtlayanın sorularını sormasına, yanıtları toplamaya veya bir yanıtlayanın yanıt vermedi olduğunu benzetmek için mantığı oluşturun.
1. Ankete yanıt veren yeterli sayıda yanıt verene kadar tekrarlayın.

Bir anket yanıtını temsil eden bir sınıfa ihtiyacınız vardır, bu nedenle şimdi ekleyin. Null yapılabilir desteğini etkinleştirin. Aşağıdaki kodda gösterildiği gibi `Id` özelliği ve onu başlatan bir Oluşturucu ekleyin:

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

Sonra, rastgele bir KIMLIK oluşturarak yeni katılımcılar oluşturmak için `static` yöntemi ekleyin:

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Bu sınıfın ana sorumluluğu, bir katılımcının yanıtlarını Anketteki sorulara üretmesidir. Bu sorumluluk birkaç adımdan daha sahiptir:

1. Ankete katılım isteyin. Kişi onay vermezse, eksik (veya null) bir yanıt döndürün.
1. Her soruyu sorun ve yanıtı kaydedin. Her cevap da eksik olabilir (veya null).

@No__t-0 sınıfına aşağıdaki kodu ekleyin:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Anket yanıtlarının depolaması, null olabileceğini belirten bir `Dictionary<int, string>?` ' dır. Tasarım amacınızı, her ikisi de derleyiciye ve kodunuzu daha sonra okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz. İlk olarak null değeri denetlemeden `surveyResponses` ' a başvurdıysanız, bir derleyici uyarısı alırsınız. Derleyici `surveyResponses` değişkeninin yukarıda null olmayan bir değere ayarlandığını belirleyebileceğinden `AnswerSurvey` yönteminde uyarı almanız gerekmez.

Eksik yanıtlar için `null` ' ı kullanmak, null yapılabilir başvuru türleriyle çalışmak için bir anahtar noktası vurgular: Amacınız, tüm @no__t 1 değerleri programınızdaki kaldırmıyor. Bunun yerine amacınız, yazdığınız kodun tasarımınızın amacını ifade etmek için gereklidir. Eksik değerler kodunuzda ifade etmek için gerekli bir kavramdır. @No__t-0 değeri, eksik değerleri ifade etmenin açık bir yoludur. Tüm @no__t kaldırılmaya çalışılıyor-0 değerleri yalnızca `null` olmadan eksik değerleri ifade etmek için başka bir yol tanımlamaya neden oluyor.

Sonra, `SurveyRun` sınıfına `PerformSurvey` yöntemini yazmanız gerekir. @No__t-0 sınıfına aşağıdaki kodu ekleyin:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Burada, null yapılabilir @no__t tercih ettiğiniz seçenek, yanıtın null olabileceğini gösterir. Bu, anketin henüz herhangi bir yanıtlayanlara verilmediğini belirtir. Yanıt verenlerin yeterli olana kadar eklendiğine dikkat edin.

Anketi çalıştırmanın son adımı, `Main` yönteminin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Anket yanıtlarını İnceleme

Son adım, anket sonuçlarını görüntülemektir. Yazdığınız sınıfların çoğuna kod ekleyeceksiniz. Bu kod, null yapılabilir ve null yapılamayan başvuru türlerini ayırt etme değerini gösterir. Aşağıdaki iki Expression-Bodied üyesini `SurveyResponse` sınıfına ekleyerek başlayın:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

@No__t-0 null yapılabilir bir başvuru türü olduğundan, buna başvurulmadan önce null denetimleri gereklidir. @No__t-0 yöntemi null yapılamayan bir dize döndürür. bu nedenle, null birleşim işlecini kullanarak eksik bir yanıtın durumunu kapsamamız gerekir.

Ardından, bu üç Expression-Bodied üyelerini `SurveyRun` sınıfına ekleyin:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

@No__t-0 üyesi, `respondents` değişkeninin null olabileceğini, ancak dönüş değerinin null olduğunu dikkate almalıdır. @No__t-0 ' ı ve aşağıdaki boş diziyi kaldırarak bu ifadeyi değiştirirseniz, derleyici yöntemi bir `null` döndürebilir ve dönüş imzası null yapılamayan bir tür döndürür.

Son olarak, aşağıdaki döngüyü `Main` yönteminin altına ekleyin:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Bu kodda `null` denetimleri gerekmez, çünkü hepsi null yapılamayan başvuru türleri döndürecek şekilde temel arabirimleri tasarlamış oldunuz.

## <a name="get-the-code"></a>Kodu edinin

Örnek deponuzdan, [CSharp/Nullabletanıtım](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründe bulunan [örnek](https://github.com/dotnet/samples) depomuza yönelik kodu alabilirsiniz.

Null atanabilir ve null yapılamayan başvuru türleri arasında tür bildirimleri değiştirerek deneyin. @No__t, yanlışlıkla bir başvurmamasını sağlamak için nasıl farklı uyarılar üretmediğini öğrenin.

## <a name="next-steps"></a>Sonraki adımlar

Mevcut bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde geçirerek daha fazla bilgi edinin:
> [!div class="nextstepaction"]
> [Bir uygulamayı null yapılabilir başvuru türlerini kullanacak şekilde yükseltme](upgrade-to-nullable-references.md)
