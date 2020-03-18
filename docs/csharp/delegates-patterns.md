---
title: Temsilciler için Ortak Desenler
description: Bileşenleriniz arasında güçlü bir bağlantı dan kaçınmak için kodunuzda temsilci kullanmanın yaygın desenleri hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 22ab88e5b139381e3a8921baa20df035f1405146
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399667"
---
# <a name="common-patterns-for-delegates"></a>Temsilciler için Ortak Desenler

[Önceki](delegates-strongly-typed.md)

Temsilciler, bileşenler arasında en az bağlantı içeren yazılım tasarımlarını etkinleştiren bir mekanizma sağlar.

Bu tür bir tasarım için mükemmel bir örnek LINQ olduğunu. LINQ Sorgu İfade Sseni tüm özellikleri için temsilcilere dayanır. Bu basit örneği göz önünde bulundurun:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Bu, sayıların sırasını yalnızca 10 değerinden küçük olanlara filtreler.
Yöntem, `Where` filtreden hangi dizinin öğelerinin geçtiğini belirleyen bir temsilci kullanır. Bir LINQ sorgusu oluşturduğunuzda, bu özel amaç için temsilcinin uygulanmasını sağlarsınız.

Nerede yöntemi için prototip:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Bu örnek, LINQ'nin bir parçası olan tüm yöntemlerle yinelenir. Bunların tümü, belirli sorguyu yöneten kod için temsilcilere güvenir. Bu API tasarım deseni öğrenmek ve anlamak için çok güçlü bir tanesidir.

Bu basit örnek, temsilcilerin bileşenler arasında çok az bağlantı gerektirdiğini göstermektedir. Belirli bir taban sınıftan türeyen bir sınıf oluşturmanız gerekmez. Belirli bir arabirim uygulamanız gerekmez.
Tek gereksinim, eldeki göreviçin temel olan bir yöntemin uygulanmasını sağlamaktır.

## <a name="building-your-own-components-with-delegates"></a>Temsilcilerle Kendi Bileşenlerinizi Oluşturma

Bu örneği, temsilcilere dayanan bir tasarım kullanarak bir bileşen oluşturarak oluşturalım.

Büyük bir sistemde günlük iletileri için kullanılabilecek bir bileşen tanımlayalım. Kitaplık bileşenleri birçok farklı ortamlarda, birden çok farklı platformda kullanılabilir. Günlükleri yöneten bileşende birçok ortak özellik vardır. Sistemdeki herhangi bir bileşenden gelen iletileri kabul etmesi gerekir. Bu iletilerin, temel bileşenin yönetebileceği farklı öncelikleri olacaktır. İletilerin son arşivlenmiş biçiminde zaman damgaları olmalıdır. Daha gelişmiş senaryolar için iletileri kaynak bileşene göre filtrelendirebilirsiniz.

Özelliğin sık sık değişecek bir yönü vardır: iletilerin yazıldığı yer. Bazı ortamlarda hata konsoluna yazılabilirler. Diğerlerinde, bir dosya. Diğer olasılıklar veritabanı depolama, işletim sistemi olay günlükleri veya diğer belge depolama içerir.

Farklı senaryolarda kullanılabilecek çıktı kombinasyonları da vardır. Konsola ve dosyaya ileti yazmak isteyebilirsiniz.

Delegelere dayalı bir tasarım büyük bir esneklik sağlar ve gelecekte eklenebilir depolama mekanizmaları desteklemek için kolaylaştırır.

Bu tasarım altında, birincil günlük bileşeni sanal olmayan, hatta mühürlü bir sınıf olabilir. İletileri farklı depolama ortamlarına yazmak için istediğiniz temsilci kümesini takabilirsiniz. Çok noktaya yayın temsilcilerinin desteğiyle, iletilerin birden çok konuma (dosya ve konsol) yazılması gereken senaryoları desteklemeyi kolaylaştırır.

## <a name="a-first-implementation"></a>İlk Uygulama

Küçük başlayalım: ilk uygulama yeni iletileri kabul eder ve ekli temsilci kullanarak bunları yazar. Konsola ileti yazan bir temsilciyle başlayabilirsiniz.

[!code-csharp[LoggerImplementation](../../samples/snippets/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Yukarıdaki statik sınıf işe yada bilen en basit şeydir. Konsola mesaj yazan yöntem için tek bir uygulama yazmamız gerekir:

[!code-csharp[LogToConsole](../../samples/snippets/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Son olarak, temsilciyi logger'da bildirilen WriteMessage temsilcisine ekleyerek bağlamanız gerekir:

[!code-csharp[ConnectDelegate](../../samples/snippets/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Uygulama

Bizim örnek şimdiye kadar oldukça basit, ama yine de bazı delegeler içeren tasarımlar için önemli kurallar göstermektedir.

Çekirdek Çerçeve'de tanımlanan temsilci türlerinin kullanılması, kullanıcıların temsilcilerle çalışmasını kolaylaştırır. Yeni türleri tanımlamanız gerekmez ve kitaplığınızı kullanan geliştiricilerin yeni, özel leştirilmiş temsilci türlerini öğrenmesi gerekmez.

Kullanılan arabirimler olabildiğince az ve esnektir: Yeni bir çıktı kaydedici oluşturmak için bir yöntem oluşturmanız gerekir. Bu yöntem statik bir yöntem veya örnek bir yöntem olabilir. Herhangi bir erişimi olabilir.

## <a name="formatting-output"></a>Çıktıyı Biçimlendirme

Bu ilk sürümü biraz daha sağlam hale getirelim ve sonra diğer günlük mekanizmaları oluşturmaya başlayalım.

Ardından, günlük sınıfınızın daha yapılandırılmış `LogMessage()` iletiler oluşturması için yönteme birkaç bağımsız değişken ekleyelim:

[!code-csharp[Severity](../../samples/snippets/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Ardından, günlüğün çıktısına gönderilen `Severity` iletileri filtrelemek için bu bağımsız değişkenden yararlanalım.

[!code-csharp[FinalLogger](../../samples/snippets/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Uygulama

Günlük altyapısına yeni özellikler eklediniz. Logger bileşeni çok gevşek herhangi bir çıktı mekanizması ile birleştiğinden, bu yeni özellikler logger temsilcisi ni uygulayan kodun herhangi biri üzerinde hiçbir etkisi olmadan eklenebilir.

Bunu oluşturmaya devam ettikçe, bu gevşek bağlantının sitenin bölümlerini diğer konumlarda değişiklik yapmadan daha fazla esneklik sağladığına dair daha fazla örnek görürsünüz. Aslında, daha büyük bir uygulamada, kaydedici çıktı sınıfları farklı bir derleme de olabilir ve hatta yeniden olması gerekmez.

## <a name="building-a-second-output-engine"></a>İkinci Çıkış Motoru Oluşturma

Log bileşeni iyi geliyor. İletileri bir dosyaya kaydeden bir çıktı motoru daha ekleyelim. Bu biraz daha ilgili çıkış motoru olacak. Dosya işlemlerini kapsülleyen ve her yazıdan sonra dosyanın her zaman kapalı olmasını sağlayan bir sınıf olacaktır. Bu, her ileti oluşturulduktan sonra tüm verilerin diske atilmesini sağlar.

İşte bu dosya tabanlı logger:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Bu sınıfı oluşturduktan sonra, bu sınıfı anında atabilirsiniz ve logileti yöntemini Logger bileşenine bağlar:

[!code-csharp[FileLogger](../../samples/snippets/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Bu ikisi birbirini dışlamıyor. Hem günlük yöntemleriek hem de konsola ve dosyaya iletiler oluşturabilirsiniz:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Daha sonra, aynı uygulamada bile, sisteme başka bir sorun olmadan temsilcilerden birini kaldırabilirsiniz:

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Uygulama

Şimdi, günlük alt sistemi için ikinci bir çıktı işleyicisi eklediniz.
Bu doğru dosya sistemini desteklemek için biraz daha fazla altyapı gerekir. Temsilci bir örnek yöntemidir. Aynı zamanda özel bir yöntem.
Temsilci altyapısı temsilcileri bağlayabildiği için daha fazla erişilebilirliğe gerek yoktur.

İkinci olarak, temsilci tabanlı tasarım, herhangi bir ek kod olmadan birden çok çıkış yöntemi sağlar. Birden çok çıktı yöntemini desteklemek için ek altyapı oluşturmanız gerekmez. Onlar sadece çağırma listesinde başka bir yöntem haline gelir.

Dosya günlüğe kaydetme çıktısı yöntemindeki koda özellikle dikkat edin. Herhangi bir özel durum atmaması için kodlanır. Bu her zaman kesinlikle gerekli olmasa da, genellikle iyi bir uygulamadır. Temsilci yöntemlerinden biri özel durum oluşturursa, çağrı üzerinde kalan temsilciler çağrılmaz.

Son not olarak, dosya kaydedicisi her günlük iletisindeki dosyayı açıp kapatarak kaynaklarını yönetmelidir. Dosyayı açık tutmayı ve tamamlandığında dosyayı kapatmak için IDisposable'i uygulamayı seçebilirsiniz.
Her iki yöntemin de avantajları ve dezavantajları vardır. Her ikisi de sınıflar arasında biraz daha bağlantı oluşturmak yok.

Logger sınıfındaki kodun her iki senaryoyu da desteklemek için güncelleştirilmemesi gerekir.

## <a name="handling-null-delegates"></a>Null Delegeleri Taşıma

Son olarak, Çıkış Mekanizması seçilmediğinde bu gibi durumlar için sağlam olacak şekilde LogMessage yöntemini güncelleştirelim. Geçerli uygulama, temsilcinin `NullReferenceException` `WriteMessage` eklenmiş bir davet listesi yoksa bir atma olacaktır.
Hiçbir yöntem eklenmediğinde sessizce devam eden bir tasarımı tercih edebilirsiniz. Bu `Delegate.Invoke()` yöntem ile birlikte, null koşullu işleci kullanarak kolaydır:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Null koşullu işleç (`?.`) kısa devreler sol`WriteMessage` operand (bu durumda) null, hangi hiçbir girişimi bir mesaj günlük için yapılır anlamına gelir.

Belgelerde listelenen `Invoke()` yöntemi bulamazsınız `System.Delegate` veya `System.MulticastDelegate`. Derleyici, bildirilen herhangi `Invoke` bir temsilci türü için güvenli bir tür yöntemi oluşturur. Bu örnekte, `Invoke` bu tek `string` bir bağımsız değişken alır ve geçersiz bir dönüş türü vardır anlamına gelir.

## <a name="summary-of-practices"></a>Uygulamaların Özeti

Diğer yazarlar ve diğer özelliklerle genişletilebilen bir günlük bileşeninin başlangıcını gördünüz. Tasarımda temsilciler kullanılarak bu farklı bileşenler çok gevşek bir şekilde birleşir. Bu çeşitli avantajlar sağlar. Yeni çıkış mekanizmaları oluşturmak ve bunları sisteme eklemek çok kolaydır. Bu diğer mekanizmalar yalnızca bir yöntem gerekir: günlük iletisi yazan yöntem. Yeni özellikler eklendiğinde çok esnek bir tasarımdır. Herhangi bir yazar için gerekli sözleşme bir yöntem uygulamaktır. Bu yöntem statik veya örnek yöntemi olabilir. Bu kamu, özel veya başka bir yasal erişim olabilir.

Logger sınıfı, son kesme değişiklikleri getirmeden herhangi bir sayıda geliştirme veya değişiklik yapabilir. Herhangi bir sınıf gibi, değişiklikleri bozma riski olmadan ortak API değiştiremezsiniz. Ancak, kaydedici ve herhangi bir çıkış motorları arasındaki bağlantı yalnızca temsilci aracılığıyla olduğundan, başka türleri (arabirimler veya temel sınıflar gibi) dahil. Bağlantı mümkün olduğunca küçük.

[Sonraki](events-overview.md)
