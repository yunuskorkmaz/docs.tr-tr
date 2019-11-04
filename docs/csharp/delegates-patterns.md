---
title: Temsilciler için Ortak Desenler
description: Bileşenleriniz arasında güçlü bir kuponu önlemek için kodunuzda temsilcilerin kullanılmasına yönelik yaygın desenler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: 174ae4129464c9d2e787048793cec764121ca4aa
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454075"
---
# <a name="common-patterns-for-delegates"></a>Temsilciler için Ortak Desenler

[Öncekini](delegates-strongly-typed.md)

Temsilciler, bileşenler arasında çok az sayıda bağlantısı olan yazılım tasarımlarını sağlayan bir mekanizma sağlar.

Bu tür bir tasarıma yönelik harika bir örnek LINQ 'dir. LINQ sorgu Ifade deseninin tüm özellikleri için temsilcileri temel alır. Şu basit örneği göz önünde bulundurun:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Bu, sayı dizisini yalnızca 10 ' dan küçük bir değere filtreler.
`Where` yöntemi, bir dizinin hangi öğelerin filtreyi geçiğini belirleyen bir temsilci kullanır. Bir LINQ sorgusu oluşturduğunuzda, bu belirli amaçla temsilci uygulamasını sağlarsınız.

WHERE yönteminin prototipi:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Bu örnek, LINQ 'ın parçası olan tüm yöntemlerle yinelenir. Bunlar, belirli sorguyu yöneten kod için temsilcileri kullanır. Bu API tasarım deseninin öğrenilmesinde ve anlaşılması çok güçlü bir araçtır.

Bu basit örnek, temsilcilerin bileşenler arasında çok az eşlenme gerektirdiğini gösterir. Belirli bir taban sınıftan türetilen bir sınıf oluşturmanız gerekmez. Belirli bir arabirim uygulamanız gerekmez.
Tek gereksinim, her seferinde görev için temel olan bir yöntemin uygulanmasını sağlamaktır.

## <a name="building-your-own-components-with-delegates"></a>Temsilcilerle kendi bileşenlerinizi oluşturma

Temsilcilere dayalı bir tasarım kullanarak bir bileşen oluşturarak bu örneği oluşturalım.

Büyük bir sistemde günlük iletilerinde kullanılabilecek bir bileşen tanımlayalim. Kitaplık bileşenleri, birden çok farklı platformda birçok farklı ortamda kullanılabilir. Bileşende günlükleri yöneten çok sayıda ortak özellik vardır. Sistemdeki herhangi bir bileşenden iletileri kabul etmesi gerekir. Bu iletiler, çekirdek bileşenin yönetebileceği farklı önceliklere sahip olacaktır. İletilerde, son Arşivlenen form zamandamgaları olmalıdır. Daha gelişmiş senaryolar için, iletileri kaynak bileşene göre filtreleyebilirsiniz.

Özelliğin her zaman değiştirecek bir özelliği vardır: iletiler yazıldığı yer. Bazı ortamlarda, bunlar hata konsoluna yazılabilir. Diğer bir deyişle, bir dosya. Diğer olanaklar veritabanı depolama, işletim sistemi olay günlükleri veya diğer belge depolama alanı içerir.

Ayrıca, farklı senaryolarda kullanılabilecek çıkış bileşimleri de vardır. Konsola ve bir dosyaya ileti yazmak isteyebilirsiniz.

Temsilcilere dayalı bir tasarım harika bir esneklik sağlar ve gelecekte eklenebilecek depolama mekanizmalarını desteklemeyi kolaylaştırır.

Bu tasarımın altında, birincil günlük bileşeni sanal olmayan, hatta kapalı bir sınıf olabilir. İletileri farklı depolama medyasına yazmak için herhangi bir temsilci kümesini takabilirsiniz. Çok noktaya yayın temsilcileri için yerleşik destek, iletilerin birden çok konuma (bir dosya ve bir konsol) yazılması gerektiği senaryoları desteklemeyi kolaylaştırır.

## <a name="a-first-implementation"></a>Ilk uygulama

Küçük bir başlangıç: ilk uygulama yeni iletileri kabul edecek ve ekli temsilciden yazacak. Konsola ileti yazan bir temsilciyle başlayabilirsiniz.

[!code-csharp[LoggerImplementation](../../samples/csharp/delegates-and-events/Logger.cs#FirstImplementation "A first Logger implementation.")]

Yukarıdaki statik sınıf, kullanılabilecek en basit şeydir. Konsola ileti yazan Yöntem için tek bir uygulama yazmaları gerekir: 

[!code-csharp[LogToConsole](../../samples/csharp/delegates-and-events/LoggingMethods.cs#LogToConsole "A Console logger.")]

Son olarak, bir temsilciyi, günlükçü içinde belirtilen WriteMessage temsilcisine ekleyerek yedeklemeniz gerekir:

[!code-csharp[ConnectDelegate](../../samples/csharp/delegates-and-events/Program.cs#ConnectDelegate "Connect to the delegate")]

## <a name="practices"></a>Uygulamalarından

Bizim örneğimiz oldukça basittir, ancak temsilcilerin bulunduğu tasarımların bazı önemli yönergelerinden bazılarını göstermektedir.

Çekirdek çerçevede tanımlanan temsilci türlerinin kullanılması, kullanıcıların temsilcilerle çalışmasını kolaylaştırır. Yeni türler tanımlamanız gerekmez ve kitaplığınızı kullanan geliştiricilerin yeni, özelleştirilmiş temsilci türleri öğrenmelerine gerek yoktur.

Kullanılan arabirimler olabildiğince az ve esnek olarak kullanılabilir: yeni bir çıktı günlükçüsü oluşturmak Için bir yöntem oluşturmanız gerekir. Bu yöntem bir statik yöntem veya bir örnek yöntemi olabilir. Herhangi bir erişim sahibi olabilir.

## <a name="formatting-output"></a>Çıktıyı biçimlendirme

Bu ilk sürümü biraz daha sağlam hale gedelim ve ardından diğer günlük mekanizmalarını oluşturmaya başlayalim.

Daha sonra, günlük sınıfınızın daha yapılandırılmış iletiler oluşturması için `LogMessage()` yöntemine birkaç bağımsız değişken ekleyelim:

[!code-csharp[Severity](../../samples/csharp/delegates-and-events/Logger.cs#Severity "Define severities")]
[!code-csharp[NextLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerTwo "Refine the Logger")]

Daha sonra, günlük çıktısına gönderilen iletileri filtrelemek için bu `Severity` bağımsız değişkenini kullanalım. 

[!code-csharp[FinalLogger](../../samples/csharp/delegates-and-events/Logger.cs#LoggerFinal "Finish the Logger")]

## <a name="practices"></a>Uygulamalarından

Günlük altyapısına yeni özellikler eklediniz. Günlükçü bileşeni herhangi bir çıkış mekanizmasına çok esnek bir şekilde bağlanmış olduğundan, bu yeni özellikler, günlükçü temsilcisini uygulayan kodun herhangi bir etkisi olmadan eklenebilir.

Bunu oluştururken, bu gevşek bir şekilde, diğer konumlarda herhangi bir değişiklik yapmadan sitenin parçalarını güncelleştirme konusunda daha fazla esneklik sağlayabilme hakkında daha fazla örnek görürsünüz. Aslında daha büyük bir uygulamada, günlükçü çıkış sınıfları farklı bir derlemede olabilir, hatta yeniden oluşturulması gerekmez.

## <a name="building-a-second-output-engine"></a>Ikinci bir çıkış altyapısı oluşturma

Günlük bileşeni de birlikte geliyor. İletileri bir dosyaya kaydeden bir çıkış altyapısı ekleyelim. Bu, biraz daha ilgili çıkış altyapısı olacaktır. Dosya işlemlerini kapsülleyen bir sınıf olur ve her yazma işleminden sonra dosyanın her zaman kapatılmasını sağlar. Bu, her ileti oluşturulduktan sonra tüm verilerin diske temizlendiğinden emin olmanızı sağlar.

Dosya tabanlı günlükçü şu şekildedir:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/FileLogger.cs#FileLogger "Log to files")]

Bu sınıfı oluşturduktan sonra, onu örnekleyebilirsiniz ve LogMessage metodunu günlükçü bileşenine iliştirir:

[!code-csharp[FileLogger](../../samples/csharp/delegates-and-events/Program.cs#FileLogger "Log to files")]

Bu ikisi birbirini dışlamalı değildir. Her iki günlük yöntemini iliştirebilir ve konsola ve bir dosyaya ileti oluşturabilirsiniz:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LoggingMethods.LogToConsole; // LoggingMethods is the static class we utilized earlier
```

Daha sonra aynı uygulamada bile, temsilcilerden birini sisteme başka herhangi bir sorun olmadan kaldırabilirsiniz:

```csharp
Logger.WriteMessage -= LoggingMethods.LogToConsole;
```

## <a name="practices"></a>Uygulamalarından

Şimdi günlüğe kaydetme alt sistemi için ikinci bir çıkış işleyicisi eklediniz.
Bu, dosya sistemini doğru şekilde desteklemeye yönelik bir bit daha daha altyapı gerektirir. Temsilci bir örnek yöntemidir. Aynı zamanda özel bir yöntemdir.
Temsilci altyapısı temsilcileri bağlayabildiğinden, daha fazla erişilebilirlik gerekmez.

İkinci olarak, temsilci tabanlı tasarım, ek kod olmadan birden çok çıktı yöntemi sunar. Birden çok çıkış yöntemini desteklemek için ek altyapı oluşturmanız gerekmez. Bunlar, çağırma listesinde yalnızca başka bir yöntem haline gelir.

Dosya günlüğü çıkış yönteminde koda özel bir dikkat ödeyin. Özel durum oluşturmadığından emin olmak için kodlanır. Her zaman kesinlikle gerekli olmasa da, genellikle iyi bir uygulamadır. Temsilci yöntemlerinden biri bir özel durum oluşturursa, Çağrılı kalan temsilciler çağrılmaz.

Son bir notta, dosya günlükçüsü, her günlük iletisindeki dosyayı açıp kapatarak kaynaklarını yönetmesi gerekir. Dosyayı açık tutmayı ve siz bitirdiğinizde dosyayı kapatmak için IDisposable 'yi uygulamayı seçebilirsiniz.
Her iki yöntemin da avantajları ve dezavantajları vardır. Her ikisi de sınıflar arasında biraz daha fazla eşlenme oluşturur.

Her iki senaryoyu desteklemek için günlükçü sınıfındaki kodların hiçbirinin güncellenmesi gerekmez.

## <a name="handling-null-delegates"></a>Null temsilcileri işleme

Son olarak, LogMessage yöntemini, hiçbir çıkış mekanizması seçili olmadığında bu durumlar için sağlam olacak şekilde güncelleştirlim. `WriteMessage` temsilcisinin ekli bir çağırma listesi olmadığında geçerli uygulama bir `NullReferenceException` oluşturur.
Hiçbir yöntem ekli olmadığında sessizce devam eden bir tasarım tercih edebilirsiniz. Bu, `Delegate.Invoke()` yöntemiyle birlikte boş koşullu işleç kullanılarak kolaydır:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Sol işlenen (Bu durumda`WriteMessage`) null olduğunda, null koşullu işleç (`?.`) kısa devrelerinin boş olması, bir iletiyi günlüğe kaydetmek için denenmediği anlamına gelir.

`System.Delegate` veya `System.MulticastDelegate`belgelerinde listelenen `Invoke()` yöntemini bulamayamayacağız. Derleyici, belirtilen herhangi bir temsilci türü için tür güvenli `Invoke` yöntemi oluşturur. Bu örnekte, `Invoke` tek bir `string` bağımsız değişkeni alır ve void dönüş türü vardır.

## <a name="summary-of-practices"></a>Uygulamaların Özeti

Diğer yazarlar ve diğer özelliklerle genişletilebilen bir günlük bileşeni Beginnings ' yi gördünüz. Tasarımdaki temsilcileri kullanarak bu farklı bileşenler çok esnek bir şekilde bağlanmış. Bu, çeşitli avantajlar sağlar. Yeni çıkış mekanizmaları oluşturmak ve bunları sisteme eklemek çok kolaydır. Bu diğer mekanizmaların yalnızca bir yöntemi olmalıdır: günlük iletisini yazan yöntem. Yeni özellikler eklendiğinde çok dayanıklı bir tasarımdır. Herhangi bir yazıcı için gereken sözleşme, bir yöntemi uygulamaktır. Bu yöntem bir statik veya örnek yöntemi olabilir. Ortak, özel veya başka bir yasal erişim olabilir.

Günlükçü sınıfı, önemli değişikliklere bildirmeden herhangi bir sayıda geliştirme veya değişiklik yapabilir. Her sınıf gibi, değişiklikleri bozmadan genel API 'yi değiştiremezsiniz. Ancak, günlükçü ve herhangi bir çıkış motoru arasındaki kuponu yalnızca temsilci aracılığıyla aldığından, başka hiçbir tür (arabirimler veya temel sınıflar gibi) dahil değildir. Kuponu mümkün olduğunca küçük.

[Next](events-overview.md)
