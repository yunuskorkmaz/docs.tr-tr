---
title: Null başvuru türleri için Tasarım
description: Gelişmiş Bu öğretici, bir null başvuru türlerine giriş sağlar. Tasarımınız ne zaman başvuru değeri null ve boş olamaz yürüttüğünde derleyici sahip hedefi express öğreneceksiniz.
ms.date: 02/19/2019
ms.custom: mvc
ms.openlocfilehash: 7f071dedd2e7a611b08a3fd37a7c0b3182be049b
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57846590"
---
# <a name="tutorial-express-your-design-intent-more-clearly-with-nullable-and-non-nullable-reference-types"></a>Öğretici: Tasarım amacınızla daha net bir şekilde boş değer atanabilir ve NULL olmayan bir başvuru türleri için express

C#8 tanıtır **null başvuru türleri**, boş değer atanabilen değer türleri tamamlar değer türleri aynı şekilde hangi tamamlayıcı başvuru türleri. Olması için bir değişken bildirmek bir **boş değer atanabilir bir başvuru türü** ekleyerek bir `?` türü. Örneğin, `string?` temsil eden bir boş değer atanabilir `string`. Bu yeni türleri tasarım amacınızla daha net bir şekilde ifade etmek için kullanabilirsiniz: bazı değişkenler *her zaman bir değere sahip olmalıdır*, diğerleri *bir değer eksik*.

Bu öğreticide şunları öğrenirsiniz nasıl yapılır:

> [!div class="checklist"]
> * Boş değer atanabilir ve NULL olmayan bir başvuru türleri tasarımlarınızı dahil edilip derecelendirilir.
> * Kod boyunca boş değer atanabilir bir başvuru türü denetimlerini etkinleştir.
> * Burada bu tasarım kararları derleyici zorlar kod yazın.
> * Kendi tasarımlarında null başvuru özelliğini kullanma

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak ihtiyacınız olacak dahil olmak üzere C# 8.0 beta derleyici. C# 8 beta derleyici, kullanılabilir [Visual Studio 2019 Önizleme 4](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019+preview), veya [.NET Core 3.0 Önizleme 3](https://dotnet.microsoft.com/download/dotnet-core/3.0).

Bu öğreticide, aşina olduğunuz varsayılır C# ve .NET, Visual Studio veya .NET Core CLI gibi.

## <a name="incorporate-nullable-reference-types-into-your-designs"></a>Null başvuru türleri tasarımlarınızı dahil edilip derecelendirilir.

Bu öğreticide, bir anket çalışan modeller bir kitaplık oluşturacaksınız. Kod, gerçek hayatta kullanılan kavramları göstermek için null başvuru türleri hem atanamayan başvuru türleri kullanır. Anket sorularını hiçbir zaman null olabilir. Yanıtlayan bir sorusunun yanıtını değil tercih edebilirsiniz. Yanıtlar, bu durumda null olabilir.

Bu amaç için bu örnek yazacaksınız kod ifade eder ve o hedefi derleyici zorlar.

## <a name="create-the-application-and-enable-nullable-reference-types"></a>Uygulama oluşturma ve null başvuru türleri etkinleştirme

Visual Studio veya komut satırı kullanarak yeni bir konsol uygulaması oluşturma `dotnet new console`. Uygulama adı `NullableIntroduction`. Uygulamayı oluşturduktan sonra etkinleştirmeniz gerekir C# 8 beta özellikleri. Açık `csproj` dosya ve ekleme bir `LangVersion` öğesine `PropertyGroup` öğesi. Katılmayı gerekir **null başvuru türleri** bile, özellik C# 8 projeleri. Bu özellik etkinleştirildikten sonra mevcut başvuru değişken bildirimlerini olur çünkü **atanamayan başvuru türleri**. Bu kararı uygun null denetimlerini varolan kodu nerede olmayabilir sorunları bulmanıza yardımcı olur, ancak özgün tasarım amacınızla doğru şekilde yansıtmaz. Özelliğini ayarlayarak açmak `NullableContextOptions` öğesine `enable`:

```xml
<LangVersion>8.0</LangVersion>
<NullableContextOptions>enable</NullableContextOptions>
```

> [!NOTE]
> Zaman C# 8 (değil önizleme modunda), yayımlanan `NullableContextOptions` öğesi yeni proje şablonları tarafından eklenir. O zamana kadar el ile eklemeniz gerekir.


### <a name="design-the-types-for-the-application"></a>Uygulama türleri tasarımı

Bir dizi sınıfları oluşturmak için bu anket uygulaması gerekir:

- Soruların listesini modeller bir sınıf.
- Anket için Görüşülen kişi listesini modeller bir sınıf.
- Anket geçen bir kişiden yanıtlarını modeller bir sınıf.

Bu tür üyeleri gereklidir ve hangi üyelerin isteğe bağlı ifade etmek için alamayan başvuru türleri ve her ikisi de boş değer atanabilir kullanımını hale getirir. Null başvuru türleri iletişim amacı açıkça tasarlama:

- Anket parçası olan soruları hiçbir zaman null olabilir: Boş bir soru sormak için hiçbir mantıklı.
- Katılımcıları hiçbir zaman null olabilir. Bu izleme, Görüşülen kişi, katılmak için reddedilen bile katılımcıları olmanız gerekir.
- Soru için herhangi bir yanıt null olabilir. Katılımcıların bazı veya tüm soruları yanıtlamak reddedebilir.

Programlanmış varsa C#, diğer fırsatları atanamayan örnekleri bildirmek için eksik olabilir, null değerlere izin türlerine başvurmak bu nedenle alışkın olabilir:

- Sorular koleksiyonunu atanamayan olmalıdır.
- Katılımcıların koleksiyonunu atanamayan olmalıdır.

Kod yazarken, başvurular için varsayılan olarak bir NULL olmayan bir başvuru türü, null başvuru özel durumu neden olabilecek yaygın hataları önler görürsünüz. Bu öğreticiden bir ders, değişkenleri bulunamadı veya null olabilir değil, hakkında kararlar yapılan ' dir. Dil sözdiziminin bu kararları express için sağlamadı. Artık bunu yapar.

Oluşturacağınız uygulama aşağıdakileri yapar:

1. Anket oluşturmak ve sorular ekleyin.
1. Anket yanıt veren bir sözde rastgele dizi oluşturun.
1. Hedef numara tamamlanan anket boyutuna erişene kadar yanıt verenler başvurun.
1. Önemli istatistikleri anket yanıtları yazın.

## <a name="build-the-survey-with-nullable-and-non-nullable-types"></a>Boş değer atanabilir ve atanamayan türleriyle anket oluşturun

Anket, yazacaksınız ilk kod oluşturur. Anket sorusuna ve çalıştırma araştırma modeli için sınıflar yazacaksınız. Clearfit'in soru, yanıt biçimi göre ayırt edilen üç türü vardır: Sayı yanıtlar ve metin yanıtlar Evet/Hayır yanıtlar. Oluşturma bir `public` `SurveyQuestion` sınıfı:

```csharp
namespace NullableIntroduction
{
    public class SurveyQuestion
    {
    }
}
```

Derleyici, her başvuru türü değişken bildirimi olarak yorumlar bir **atanamayan** başvuru türü için boş değer atanabilir bir etkin bağlamında kod. Aşağıdaki kodda gösterildiği gibi Soru metni ve soru türü özellikleri ekleyerek, ilk uyarı görebilirsiniz:

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

Henüz başlatılmamış olduğundan `QuestionText`, derleyici atanamayan bir özellik başlatılmamış bir uyarı verir. Tasarımınızı başlatmak üzere bir oluşturucu ekleyin için null olmayan, Soru metni gerektirir ve `QuestionType` değeri de. Tamamlanmış sınıf tanımını şu kod gibi görünür:

[!code-csharp[DefineQuestion](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyQuestion.cs)]

Oluşturucu eklemesini uyarı kaldırır. Derleyici Uyarı vermek değil oluşturucu bağımsız değişkeni de bir NULL olmayan bir başvuru türü olduğundan.

Ardından, oluşturun bir `public` adlı sınıfı `SurveyRun`. Bu sınıf bir listesini içeren `SurveyQuestion` nesneleri ve yöntemleri aşağıdaki kodda gösterildiği gibi ankete sorularınızı eklemek için:

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

Önceki örneklerde olduğu gibi bir null olmayan değer Liste nesnesine başlatması gerekir veya derleyici bir uyarı verir. İkinci aşırı yüklemesi, null denetimi yoktur `AddQuestion` gerekli değildir çünkü: Bu değişken null yapılamaz bildirdikten. Değeri olamaz `null`.

Geçiş `Program.cs` düzenleyicinizde ve içeriklerini `Main` aşağıdaki kod satırlarını ile:

[!code-csharp[AddQuestions](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#AddQuestions)]

Projenin tamamında boş değer atanabilir bir etkin bağlamında olduğundan, başarılı olduğunda uyarı alırsınız `null` herhangi bir yönteme bir değer atanamayan bir başvuru türü bekleniyor. Aşağıdaki satırı ekleyerek deneyin `Main`:

```csharp
surveyRun.AddQuestion(QuestionType.Text, default);
```

## <a name="create-respondents-and-get-answers-to-the-survey"></a>Katılımcıların oluşturun ve anket yanıtlarını alın

Ardından, anket yanıtlarını oluşturan kod yazın. Bu işlem, birkaç küçük görevleri içerir:

1. Katılımcı nesneleri oluşturan bir yöntem oluşturun. Bu kişiler anketini doldurmanız istenir temsil eder.
1. Soruları yanıtlayan isteyen ve yanıtları toplamak veya bir katılımcı yanıt Alamadığınız belirtmeye benzetimini yapmak için mantıksal oluşturun.
1. Yeterli katılımcıları anket ın kadar yineleyin.

Bir anket yanıtı temsil eder, bu nedenle şimdi eklemek için bir sınıf gerekir. Boş değer atanabilir desteğini etkinleştirin. Ekleme bir `Id` özelliği ve bunu, aşağıdaki kodda gösterildiği gibi başlatan bir oluşturucu:

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

Ardından, ekleme bir `static` yöntemi rastgele bir kimlik oluşturarak yeni katılımcı oluşturmak için:

[!code-csharp[GenerateRespondents](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#Random)]

Ana Bu sınıf için sorulara katılımcı anket yanıtları oluşturmak için sorumluluğundadır. Bu sorumluluk birkaç adım vardır:

1. Anket katılım isteyin. Kişi onayı değil eksik (veya boş) bir yanıt döndürür.
1. Her bir soru sorun ve yanıt kaydedin. Her yanıt, ayrıca eksik (veya null) olabilir.

Aşağıdaki kodu ekleyin, `SurveyResponse` sınıfı:

[!code-csharp[AnswerSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#AnswerSurvey)]

Anket yanıtları için depolama bir `Dictionary<int, string>?`, gösteren null olabilir. Yeni dil özelliği tasarım hedefi, derleyici ve daha sonra Kodunuzu okuyan herkese bildirmek için kullanmakta olduğunuz. Şimdiye kadar başvuru değilse `surveyResponses` null değeri ilk denetlemeden bir derleyici uyarısı alırsınız. Bir uyarı elde etmezsiniz `AnswerSurvey` yöntemi derleyici çünkü `surveyResponses` değişkeni, bir null olmayan değer yukarıdaki ayarlanmıştır.

Kullanarak `null` için yanıt eksik null başvuru türleriyle çalışmak için bir anahtar noktası vurgular: tümünü kaldırmak için amacınız değilse `null` programınızı değerleri. Bunun yerine, amacınız, kod tasarımınızı amacı ifade Yaz emin olmaktır. Eksik değerleri, kodunuzda ifade etmek için gerekli bir kavramdır. `null` Değeri, bu eksik değerleri ifade etmek için açık bir yoludur. Tüm kaldırmaya çalışırken `null` olmadan bu eksik değerleri ifade etmek için başka bir şekilde tanımlamak için yalnızca müşteri adaylarını değerleri `null`.

Ardından, yazmanız gereken `PerformSurvey` yönteminde `SurveyRun` sınıfı. Aşağıdaki kodu ekleyin `SurveyRun` sınıfı:

[!code-csharp[PerformSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#PerformSurvey)]

Yeniden Buraya, kendi seçtiğiniz bir boş değer atanabilir `List<SurveyResponse>?` yanıt null gösterir. Bu anketi tüm katılımcılara henüz verilen taşınmadığından gösterir. Yeterli onaylı kadar katılımcıların eklenen dikkat edin.

Anket çalıştırmak için son adımı sonunda anket gerçekleştirmek için bir çağrı eklemektir `Main` yöntemi:

[!code-csharp[RunSurvey](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#RunSurvey)]

## <a name="examine-survey-responses"></a>Anket yanıtlarını inceleyin

Son adım, anket sonuçlarını görüntülemektir. Yazdığınız sınıfların çoğu için kod ekleyeceksiniz. Bu kod, boş değer atanabilir ve NULL olmayan bir başvuru türleri ayrım değerini gösterir. Aşağıdaki iki ifade gövdeli üyeler için ekleyerek başlangıç `SurveyResponse` sınıfı:

[!code-csharp[ReportResponses](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyResponse.cs#SurveyStatus)]

Çünkü `surveyResponses` bir NULL olmayan bir başvuru türü seri durumdan başvurmadan önce hiçbir denetim gereklidir. `Answer` Yöntemi null olmayan bir dize döndürür, bu nedenle, aşırı yüklemesini seçin `GetValueOrDefault` , varsayılan değer için ikinci bir bağımsız değişken alır.

Ardından, bu üç ifade gövdeli üyeler ekleyin `SurveyRun` sınıfı:

[!code-csharp[ReportResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/SurveyRun.cs#RunReport)]

`AllParticipants` Üye dikkate almak gerekir, `respondents` değişkeni null olabilir, ancak dönüş değeri null olamaz. Bu ifade kaldırarak değiştirirseniz `??` ve yöntem döndürebilir izleyen boş dizi derleyici sizi uyarır `null` ve dönüş imzası-boş değer atanabilir olmayan türü döndürür.

Son olarak, pencerenin şu döngüyü ekleyin `Main` yöntemi:

[!code-csharp[DisplaySurveyResults](../../../samples/csharp/NullableIntroduction/NullableIntroduction/Program.cs#WriteAnswers)]

Herhangi bir ihtiyaç duymazsanız `null` tüm NULL olmayan bir başvuru türleri döndürmeleri, temel alınan arabirimler tasarladığınız olduğundan bu kod, denetler.

## <a name="get-the-code"></a>Kodu alma

Öğreticinin tamamlanan kodu alabilirsiniz bizim [örnekleri](https://github.com/dotnet/samples) depoda [csharp/NullableIntroduction](https://github.com/dotnet/samples/tree/master/csharp/NullableIntroduction) klasör.

Boş değer atanabilir ve NULL olmayan bir başvuru türleri arasında tür bildirimleri değiştirerek denemeler yapın. Yanlışlıkla başvuru olmayan emin olmak için farklı uyarıları oluşturan nasıl bkz bir `null`.

## <a name="next-steps"></a>Sonraki adımlar

Null başvuru türleri kullanmak için mevcut bir uygulamayı geçirme tarafından daha fazla bilgi edinin:
> [!div class="nextstepaction"]
> [Null başvuru türleri kullanmak için uygulama yükseltme](upgrade-to-nullable-references.md)
