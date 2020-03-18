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
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Öğretici: Tasarım niyetinizi nullable ve nullable olmayan referans türleri ile daha net ifade edin

C# 8.0, başvuru türlerini, nullable değer türlerinin tamamladığı şekilde tamamlayan [nullable başvuru türlerini](../nullable-references.md)tanır. Bir değişkeni, a **nullable reference type** `?` türünü ekleyerek geçersiz bir başvuru türü olarak beyan elabilirsiniz. Örneğin, `string?` nullable `string`temsil eder. Tasarım amacınızı daha net ifade etmek için bu yeni türleri kullanabilirsiniz: bazı değişkenlerin *her zaman bir değeri olmalıdır,* diğerleri bir değer eksik *olabilir.*

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
>
> - Nullable ve nullable olmayan referans türlerini tasarımlarınıza dahil edin
> - Kodunuz boyunca geçersiz başvuru türü denetimlerini etkinleştirin.
> - Derleyicinin bu tasarım kararlarını uyguladığı kod yazın.
> - Kendi tasarımlarınızda geçersiz referans özelliğini kullanın

## <a name="prerequisites"></a>Önkoşullar

C# 8.0 derleyicisi de dahil olmak üzere .NET Core'u çalıştıracak şekilde makinenizi ayarlamanız gerekir. C# 8.0 derleyicisi [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)veya [.NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0)ile kullanılabilir.

Bu öğretici, Visual Studio veya .NET Core CLI dahil olmak üzere C# ve .NET'e aşina olduğunuzu varsayar.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Nullable referans türlerini tasarımlarınıza dahil edin

Bu öğreticide, anket çalıştıran modelleri içeren bir kitaplık oluşturursunuz. Kod, gerçek dünya kavramlarını temsil etmek için hem geçersiz başvuru türlerini hem de nullable olmayan başvuru türlerini kullanır. Anket soruları asla geçersiz olamaz. Yanıtlayan bir soruya cevap vermemeyi tercih edebilir. Yanıtlar bu `null` durumda olabilir.

Bu örnek için yazacağınız kod bu amacı ifade eder ve derleyici bu amacı uygular.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Uygulamayı oluşturun ve nullable başvuru türlerini etkinleştirin

Visual Studio'da veya komut satırından yeni `dotnet new console`bir konsol uygulaması oluşturun. Uygulamayı adlandırın. `NullableIntroduction` Uygulamayı oluşturduktan sonra, tüm projenin etkin **geçersiz ek açıklama bağlamında**derlediğini belirtmeniz gerekir. *.csproj* dosyasını açın `Nullable` ve `PropertyGroup` öğeye bir öğe ekleyin. Değerini `enable` olarak ayarlayın. C# 8.0 projelerinde bile **geçersiz başvuru türleri** özelliğini tercih etmeniz gerekir. Bunun nedeni, özellik açık olduktan sonra varolan başvuru değişken iatürleri' nin **geçersiz başvuru türleri**haline gelmesidir. Bu karar, varolan kodun uygun null-checks olmayabilir sorunları bulmanıza yardımcı olsa da, doğru orijinal tasarım amacı yansıtmayabilir:

```xml
<Nullable>enable</Nullable>
```

### <a name="design-the-types-for-the-application"></a>Uygulama türlerini tasarla

Bu anket uygulaması bir dizi sınıf oluşturmayı gerektirir:

- Soru listesini modelleyen bir sınıf.
- Anket için temasa geçilen kişilerin listesini modelleyen bir sınıf.
- Anketi alan bir kişinin yanıtlarını modelleyen bir sınıf.

Bu türler, hangi üyelerin gerekli olduğunu ve hangi üyelerin isteğe bağlı olduğunu ifade etmek için hem geçersiz hem de geçersiz referans türlerinden yararlanacaktır. Nullable başvuru türleri bu tasarım amacını açıkça bildirir:

- Anketin bir parçası olan sorular asla geçersiz olamaz: Boş bir soru sormak anlamsızdır.
- Yanıtlayanlar asla geçersiz olamaz. Bağlantı kurduğunuz kişileri, hatta katılmayı reddeden yanıtlayanları izlemek isteyeceksiniz.
- Bir soruya verilen herhangi bir yanıt geçersiz olabilir. Yanıtlayanlar bazı veya tüm soruları yanıtlamayı reddedebilir.

C#'da programlandıysanız, `null` değer veren başvuru türlerine o kadar alışmış olabilirsiniz ki, geçersiz olmayan örnekleri bildirmek için diğer fırsatları kaçırmış olabilirsiniz:

- Sorular topluluğu geçersiz olmalıdır.
- Yanıtlayanların koleksiyonu geçersiz olmalıdır.

Kodu yazdıkça, başvurular için varsayılan olarak nullable olmayan bir başvuru türü <xref:System.NullReferenceException>s yol açabilecek yaygın hatalar önler görürsünüz. Bu öğretici bir ders hangi değişkenler olabilir ya da olamazdı `null`hakkında kararlar olmasıdır. Dil bu kararları ifade etmek için sözdizimi sağlamadı. Şimdi oldu.

Oluşturacağınız uygulama aşağıdaki adımları yapar:

1. Bir anket oluşturur ve ankete sorular ekler.
1. Anket için sözde rasgele yanıtlayanlar kümesi oluşturur.
1. Tamamlanan anket boyutu hedef numarasına ulaşana kadar yanıtlayanlara bağlantı kurur.
1. Anket yanıtları ile ilgili önemli istatistikleri yazar.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Anketi geçersiz ve nullable olmayan türlerle oluşturun

Yazacağınız ilk kod anketi oluşturur. Bir anket sorusunu ve anket çalışmasını modellemek için sınıflar yazarsınız. Anketinizin yanıtının biçimine göre ayırt edilen üç tür sorusu vardır: Evet/Hayır yanıtları, sayı yanıtları ve metin yanıtları. Bir `public SurveyQuestion` sınıf oluşturun:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Derleyici, her başvuru türü değişken bildirimini etkin bir nullable ek açıklama bağlamında kod için **nullable** olmayan bir başvuru türü olarak yorumlar. Aşağıdaki kodda gösterildiği gibi, soru metni ve soru türü için özellikler ekleyerek ilk uyarınızı görebilirsiniz:

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

Başharfe para vermediniz, `QuestionText`derleyici geçersiz bir özelliğin başharflere alınamadığını belirten bir uyarı yayınlar. Tasarımınız soru metninin null'suz olmasını gerektirir, bu nedenle onu ve `QuestionType` değeri de başlatması için bir oluşturucu eklersiniz. Bitmiş sınıf tanımı aşağıdaki kod gibi görünür:

[!code-csharp[DefineQuestion](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Oluşturucu ekleme uyarı kaldırır. Oluşturucu bağımsız değişkeni de nullable olmayan bir başvuru türüdür, bu nedenle derleyici herhangi bir uyarı vermez.

Ardından, adlı `public` `SurveyRun`bir sınıf oluşturun. Bu sınıf, aşağıdaki `SurveyQuestion` kodda gösterildiği gibi, ankete soru eklemek için nesnelerin ve yöntemlerin bir listesini içerir:

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

Daha önce olduğu gibi, liste nesnesini null olmayan bir değere başlatmanız gerekir veya derleyici bir uyarı yayınlar. İkinci aşırı yüklemede geçersiz denetim `AddQuestion` ler yoktur, çünkü bunlar gerekli değildir: Bu değişkeni nullable olarak beyan emtersiniz. Değeri olamaz. `null`

Düzenleyicinizde *Program.cs'a* geçin ve `Main` içeriğini aşağıdaki kod satırlarıyla değiştirin:

[!code-csharp[AddQuestions](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Projenin tamamı etkin geçersiz ek açıklama bağlamında olduğundan, nullable olmayan bir `null` başvuru türü bekleyen herhangi bir yönteme geçtiğiniz zaman uyarılar alırsınız. Aşağıdaki satırı ekleyerek `Main`deneyin:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Yanıtlayanlar oluşturun ve ankete yanıt alın

Ardından, ankete yanıt üreten kodu yazın. Bu işlem birkaç küçük görev içerir:

1. Yanıtlayan nesneleri oluşturan bir yöntem oluşturun. Bunlar, anketi doldurmaları istenen kişileri temsil ediyor.
1. Soruları yanıtlayana sormayı ve yanıt ları toplamak veya yanıtlayanın yanıtlaşmadığına dikkat etmek için mantık oluşturun.
1. Ankete yeteri kadar yanıtlayan yanıtlayana kadar tekrarlayın.

Bir anket yanıtını temsil etmek için bir sınıfa ihtiyacınız olacak, bu nedenle bunu şimdi ekleyin. Nullable desteği etkinleştirin. Aşağıdaki `Id` kodda gösterildiği gibi, bir özellik ve onu başlatılmasını sağlayan bir oluşturucu ekleyin:

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

Ardından, rasgele `static` bir kimlik oluşturarak yeni katılımcılar oluşturmak için bir yöntem ekleyin:

[!code-csharp[GenerateRespondents](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Bu sınıfın temel sorumluluğu, anketteki sorulara katılan bir katılımcıiçin yanıt oluşturmaktır. Bu sorumluluğun birkaç adımı vardır:

1. Ankete katılım isteyin. Kişi izin vermezse, eksik (veya null) yanıtı döndürün.
1. Her soruyu sorun ve cevabı kaydedin. Her yanıt da eksik (veya null) olabilir.

Sınıfınıza `SurveyResponse` aşağıdaki kodu ekleyin:

[!code-csharp[AnswerSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Anket yanıtları için depolama `Dictionary<int, string>?`bir , null olabileceğini belirten. Tasarım amacınızı hem derleyiciye hem de daha sonra kodunuzu okuyan herkese bildirmek için yeni dil özelliğini kullanıyorsunuz. Değeri kontrol etmeden `surveyResponses` önce başvurudan `null` çıkarsanız, derleyici uyarısı alırsınız. Derleyici değişkenin `surveyResponses` yukarıdaki null `AnswerSurvey` olmayan bir değere ayarlandığını belirleyebileceğinden, yöntemde bir uyarı alamazsınız.

Eksik `null` yanıtlar için kullanmak, geçersiz başvuru türleri ile çalışmak için önemli bir `null` noktayı vurgular: amacınız programınızdaki tüm değerleri kaldırmak değildir. Bunun yerine, amacınız yazdığınız kodun tasarımınızın amacını ifade etmesini sağlamaktır. Eksik değerler, kodunuzda ifade etmek için gerekli bir kavramdır. Değer, `null` eksik değerleri ifade etmenin açık bir yoludur. Tüm `null` değerleri kaldırmaya çalışmak, yalnızca eksik değerleri ' siz `null`olmadan ifade etmek için başka bir yol tanımlamaya yol açar.

Sonra, `PerformSurvey` `SurveyRun` sınıfta yöntem yazmanız gerekir. Sınıfa `SurveyRun` aşağıdaki kodu ekleyin:

[!code-csharp[PerformSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Burada yine, nullable `List<SurveyResponse>?` seçiminiz yanıtın null olabileceğini gösterir. Bu, anketin henüz herhangi bir yanıtlayana verilmediğini gösteriyor. Yeterli izin alana kadar yanıtlayanların eklenmiş olduğuna dikkat edin.

Anketi çalıştırmak için son adım, `Main` yöntemin sonunda anketi gerçekleştirmek için bir çağrı eklemektir:

[!code-csharp[RunSurvey](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Anket yanıtlarını inceleyin

Son adım anket sonuçlarını görüntülemektir. Yazdığınız birçok sınıfa kod eklersiniz. Bu kod, nullable ve nullable olmayan başvuru türlerini ayırt değerini gösterir. `SurveyResponse` Sınıfa aşağıdaki iki ifade gövdeli üye ekleyerek başlayın:

[!code-csharp[ReportResponses](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Nullable başvuru türü `surveyResponses` olduğundan, null denetimleri de-referencing önce gereklidir. Yöntem `Answer` nullable olmayan bir dize döndürür, bu yüzden null-coalescing işleci kullanarak eksik bir cevap durumda kapsayacak şekilde var.

Ardından, bu üç ifade gövdeli `SurveyRun` üyeyi sınıfa ekleyin:

[!code-csharp[ReportResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

Üye, `AllParticipants` değişkenin `respondents` null olabileceğini, ancak geri dönüş değerinin null olabileceğini göz önünde bulundurmalıdır. Bu ifadeyi, izleyen boş `??` sırayı kaldırarak değiştirirseniz, derleyici yöntemin `null` dönebileceği ve iade imzasının nullable olmayan bir türü döndürebileceği konusunda sizi uyarır.

Son olarak, yöntemin altına aşağıdaki `Main` döngüyü ekleyin:

[!code-csharp[DisplaySurveyResults](~/samples/snippets/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Temel arabirimleri, `null` hepsinin geçersiz olmayan başvuru türlerini döndürebilmesi için tasarladığınız için bu kodda herhangi bir denetime gerek yoktur.

## <a name="get-the-code"></a>Kodu alma

Bitmiş öğreticinin kodunu [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasöründeki [numune](https://github.com/dotnet/samples) deposumuzdan alabilirsiniz.

Nullable ve nullable olmayan başvuru türleri arasındaki tür bildirimleri değiştirerek deneme. Yanlışlıkla bir `null`' nin dereference'Ini göndermemeniz için bunun nasıl farklı uyarılar oluşturduğunu görün

## <a name="next-steps"></a>Sonraki adımlar

Nullable başvuru türlerini kullanmak için varolan bir uygulamayı geçirerek daha fazla bilgi edinin:
> [!div class="nextstepaction"]
> [Nullable başvuru türlerini kullanmak için bir uygulamayı yükseltme](upgrade-to-nullable-references.md)
