---
title: Temsilciler için ortak desenler
description: Güçlü bir bağ bileşenleriniz arasındaki önlemek için kodunuzda temsilcileri kullanma için ortak desenler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: ea0e0b7af361b76c4b46b0a180e07b44c1fa07e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646689"
---
# <a name="common-patterns-for-delegates"></a>Temsilciler için ortak desenler

[Önceki](delegates-strongly-typed.md)

Temsilciler, bileşenler arasındaki en az bir bağlantı içeren yazılım tasarımı sağlayan bir mekanizma sağlar.

Bu tür bir tasarım için mükemmel örnek LINQ verilebilir. LINQ Sorgu ifade deseninin tüm özellikleri için temsilcileri kullanır. Bu basit örnek göz önünde bulundurun:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Bu, yalnızca'den az değerin 10 sayılara dizisini filtreler.
`Where` Filtre hangi öğelerin bir dizisi geçirin belirleyen bir temsilci yöntemi kullanır. Bir LINQ sorgu oluşturduğunuzda, bu belirli bir amaca yönelik temsilci uygulamasını sağlayın.

Prototip için Where yöntemdir:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Bu örnekte, LINQ parçası olan tüm yöntemleri ile tekrarlanır. Bunların tümü, özel bir sorgu tarafından yönetilen kod için temsilciler dayanır. Bu API tasarım öğrenin ve anlaşılmasını çok güçlü bir desendir.

Bu basit örnekte, nasıl temsilciler bileşenleri arasında çok az bağlantı gerektiren gösterilmektedir. Belirli bir taban sınıftan türetilen bir sınıf oluşturmanız gerekmez. Belirli bir arabirim uygulamak gerekmez.
Eldeki göreve temel bir yöntemin uygulanmasını sağlamak için tek gereksinim olmasıdır.

## <a name="building-your-own-components-with-delegates"></a>Temsilciler ile kendi bileşenleri oluşturma

Temsilciler üzerinde dayanan bir tasarım kullanarak bir bileşen oluşturarak bu örneği temel oluşturalım.

Günlük iletileri için büyük bir sistemde kullanılabilir bir bileşen tanımlayalım. Kitaplığı bileşenlerini birden çok farklı platformlarda birçok farklı ortamlarda kullanılabiliyordu. Birçok ortak özellik günlükleri yöneten bileşende vardır. Sistemde bir bileşenden alınan iletileri kabul etmek gerekir. Bu iletileri çekirdek bileşeni yönetebilirsiniz farklı önceliklere sahip olur. İletileri zaman damgası, son arşivlenmiş biçiminde olması gerekir. Daha Gelişmiş senaryolar için kaynak bileşen tarafından iletileri filtre uygulayabilirsiniz.

Sık sık değişen özelliği tek bir yönüne yoktur: iletileri yazıldığı. Bazı ortamlarda oldukları hata konsola yazılabilir. Bazı durumlarda, bir dosya. Veritabanı depolama, işletim sistemi olay günlüklerini veya başka bir belge depolama diğer olanaklar içerir.

Farklı senaryolarda kullanılabilecek çıkış birleşimleri de vardır. İletileri konsola ve bir dosyaya yazmak isteyebilirsiniz.

Temsilciler hakkında temel bir tasarım büyük ölçüde esneklik sağlar ve gelecekte eklenebilir destek depolama mekanizmasını kolaylaştırır.

Bu tasarım, bir sanal olmayan, hatta sınıfı korumalı birincil günlük bileşeni olabilir. Herhangi bir kümesi için farklı depolama medyası ileti yazmak için temsilciler takabilirsiniz. Çok noktaya yayın temsilcileri için yerleşik destek, iletileri birden fazla konuma (dosya ve bir konsoldan) burada yazılmalıdır destek senaryoları kolaylaştırır.

## <a name="a-first-implementation"></a>İlk uygulama

Küçük başlayalım: ilk uygulama yeni iletileri kabul edin ve herhangi bir ekli temsilci kullanarak bunları yazın. İletileri konsola bir temsilci ile başlayabilirsiniz.

[!code-csharp[LoggerImplementation](../../samples/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Yukarıdaki statik sınıf çalışabileceği en basit bir şeydir. İletileri konsola yazar yöntemi için tek uygulama yazmak gerekir: 

[!code-csharp[LogToConsole](../../samples/csharp/delegates-and-events/Program.cs#LogToConsole "A Console logger.")]

Son olarak, temsilci temsilcinin Günlükçü içinde bildirilen WriteMessage ekleyerek bağlama yapmanız gerekir:

[!code-csharp[ConnectDelegate](../../samples/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Uygulamalar

Örneğimizi şimdiye de oldukça basittir, ancak bu yine de temsilciler içeren tasarımları için önemli yönergeleri bazılarını gösterir.

Çekirdek Framework'te tanımlanan temsilci türleri, temsilciler ile çalışmak kullanıcıların kolaylaştırır. Yeni türleri tanımlamanız gerekmez ve kitaplığınızı kullanan geliştiriciler yeni, özelleştirilmiş temsilci türleri öğrenmek gerekmez.

En düşük düzeyde ve kadar esnek kullanılan arabirimlere şunlardır: Yeni bir çıktı Günlükçü oluşturmak için bir yöntem oluşturmanız gerekir. Bu yöntem, statik bir yöntem veya bir örnek yöntemi olabilir. Bu erişime sahip olabilir.

## <a name="formatting-output"></a>Çıktı biçimlendirme

Bu ilk sürümü bit daha sağlam ve diğer günlük mekanizmaları oluşturmayı başlatın olalım.

Ardından, bazı bağımsız değişkenler ekleyelim `LogMessage()` yöntemi, böylece günlük sınıfınıza daha fazla yapılandırılmış iletileri oluşturur:

[!code-csharp[Severity](../../samples/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Ardından, olalım kullanan `Severity` ' ına gönderilen iletileri filtrelemek için bağımsız değişken çıkış. 

[!code-csharp[FinalLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Uygulamalar

Günlük kaydı altyapısı için yeni özellikler ekledik. Günlükçü bileşen herhangi bir çıktı mekanizma gevşek çok sıkı bağlı olduğundan, bu yeni özellikleri, herhangi bir Günlükçü temsilci uygulayan kod herhangi bir etkisi eklenebilir.

Bu oluşturmaya devam etmek gibi daha fazla örnek nasıl bu sıkı bağ sitenin herhangi bir değişiklik yapmadan bölümlerini diğer konumlara güncelleştirme esneklik sağladığını görürsünüz. Aslında, daha büyük bir uygulamada Günlükçü çıktı sınıfları farklı bir derlemede olması ve bile yeniden derlenmesi gerekiyor.

## <a name="building-a-second-output-engine"></a>İkinci bir çıkış altyapısı oluşturma

Günlük bileşeni de kullanıma sunulacaktır. İletiler bir dosyaya kaydeden bir daha fazla çıkış altyapısı ekleyelim. Bu işlem biraz daha karmaşık bir çıkış altyapısı olacaktır. Bu dosya işlemlerini kapsüller ve sağlar dosyanın her zaman her Yazımdan sonra kapalı sınıf olacaktır. Sağlar, tüm veri Temizlenen her ileti oluşturulduktan sonra diske.

Bu dosya tabanlı Günlükçü şu şekildedir:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Bu sınıf oluşturduktan sonra örneği oluşturabilir ve bunu kendi LogMessage yöntemi Günlükçü bileşenine ekler:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Bu iki birbirini dışlamaz. Her iki günlük yöntemlerini ve iletileri konsolu ve bir dosya oluşturur:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

Daha sonra aynı uygulamada bile sisteme herhangi bir sorun olmadan temsilcileri birini kaldırabilirsiniz:

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>Uygulamalar

Şimdi, günlük alt sistemi için ikinci bir çıkış işleyicisi ekledik.
Bu bir dosya sistemi doğru desteklemek için biraz daha fazla altyapı gerekir. Bir örnek yöntemi temsilcisidir. Bu aynı zamanda özel bir yöntemdir.
Temsilci altyapıyı temsilcileri bağlanabilir olduğundan daha büyük düzeyde erişilebilirlik için gerek yoktur.

İkinci olarak, temsilci tabanlı tasarım, ek bir kod olmadan birden çok çıktı yöntemlerini sağlar. Birden çok çıktı yöntemlerini desteklemek için ek altyapı oluşturmanız gerekmez. Bunlar yalnızca başka bir yöntemi çağırma listesi haline gelir.

Özel kodu çıktı yöntemi günlük dosyasında dikkat edin. Özel durumlar oluşturmadığını emin olmak için kodlanmıştır. Bu her zaman kesinlikle gerekli olmasa da, bunu genellikle iyi bir uygulamadır. Temsilci yöntemlerine ya da bir özel durum oluşturursa, çağrıda bulunan kalan temsilcileri çağrılan olmaz.

Son Not olarak, dosya günlükçüsünün, açma ve kapatma dosyada her günlük iletisi tarafından kaynaklarını yönetmeniz gerekir. Dosya açık tutmak ve dosyanın, tamamlandığında kapatmak için IDisposable seçebilirsiniz.
Her iki yöntem kendi avantajları ve dezavantajları vardır. Her ikisi de, sınıflar arasında biraz daha fazla bağlantı oluşturun.

Günlükçü sınıfı kodda hiçbiri, her iki senaryoyu desteklemek için güncelleştirilmesi gerekir.

## <a name="handling-null-delegates"></a>İşleme Null temsilciler

Son olarak, böylece bir mekanizma bulunmadığından çıktı seçildiğinde bu gibi durumlarda sağlam LogMessage yöntemi güncelleştirelim. Geçerli uygulama oluşturmaz bir `NullReferenceException` olduğunda `WriteMessage` temsilci bağlı çağrı listesine sahip değil.
Yöntemlerin hiçbiri eklendiğinde sessizce devam eder tasarım tercih edebilirsiniz. Bu birlikte null koşullu işleci kullanılarak kolaydır `Delegate.Invoke()` yöntemi:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Null koşullu işleci (`?.`) ne zaman short-circuits sol işleneni (`WriteMessage` bu durumda) çalışılmayacak bir iletiyi günlüğe kaydetmek için yapıldığı anlamına gelir, null.

Arama yapmaz `Invoke()` yöntemi listelenen belgelerindeki `System.Delegate` veya `System.MulticastDelegate`. Derleyici, tür güvenli oluşturur `Invoke` herhangi metodunuza aşağıdakini bildirilen türü. Bu örnekte, yani `Invoke` tek bir alan `string` bağımsız değişken ve void dönüş türüne sahip.

## <a name="summary-of-practices"></a>Uygulamaların özeti

Bir günlük bileşeninin genişletilemiyor beginnings diğer Yazıcılar ve diğer özellikleri ile gördünüz. Tasarımı, temsilciler kullanılarak bu farklı bileşenlerden çok birbirine sıkı şekilde bağlı. Bu, çeşitli avantajlar sağlar. Yeni çıkış mekanizmaları oluşturup bunları sisteme eklemek çok kolaydır. Bu diğer mekanizmalar yalnızca bir yöntem gerekir: yöntemin günlük iletisi yazar. Bu yeni özellikler eklendiğinde, çok esnek bir tasarım olur. Herhangi bir yazıcı için gereken yöntemini uygulamak için sözleşmedir. Bu yöntem, statik olması veya yöntemi örneği. Genel, özel veya herhangi bir yasal erişimi olabilir.

Günlükçü sınıfı, bozucu değişiklikleri oluşturmaksızın herhangi bir sayıda yenilikleri veya değişiklikleri yapabilirsiniz. Herhangi bir sınıf gibi genel API riskini önemli değişiklikler olmadan değiştirilemiyor. Ancak, yalnızca temsilci Günlükçü herhangi bir çıktı altyapıları arasındaki bağ olduğundan, hiçbir diğer türleri (gibi arabirimler veya temel sınıflar) ilgilidir. Eşleştirmeye kadar küçük.

[Next](events-overview.md)
