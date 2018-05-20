---
title: Temsilciler için ortak desenler
description: Temsilciler kodunuzda güçlü bileşeniniz arasında Kaçın kullanmayı için ortak desenler hakkında bilgi edinin.
ms.date: 06/20/2016
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.openlocfilehash: b9762841656aa362589d01ed011407aeedfe4a20
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2018
---
# <a name="common-patterns-for-delegates"></a>Temsilciler için ortak desenler

[Önceki](delegates-strongly-typed.md)

Temsilciler bileşenler arasındaki en az bağlantı içeren yazılım tasarımları sağlayan bir mekanizma sağlar.

Bu tür bir tasarım için mükemmel bir örnek LINQ ' dir. LINQ Sorgu ifade deseni özelliklerinin tümünü temsilcileri kullanır. Bu basit örnekte göz önünde bulundurun:

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

Bu, yalnızca değerinden 10 sayılara dizisini filtreler.
`Where` Yöntemi kullanan bir dizi hangi öğeleri filtre geçip belirler bir temsilci. LINQ sorgu oluşturduğunuzda, bu belirli bir amaca yönelik temsilci uyarlamasını sağlayın.

Prototip yerdir yöntemi için:

```csharp
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Bu örnek LINQ parçası olan tüm yöntemleri ile yinelenir. Tüm temsilcileri belirli sorgu yönetir kodu güvenirler. Bu API tasarım deseni öğrenin ve anlamak için çok güçlü bir adrestir.

Bu basit örnekte, nasıl temsilciler bileşenleri arasında çok az bağlantı gerektiren gösterilmektedir. Belirli bir taban sınıftan türeyen bir sınıf oluşturmanız gerekmez. Belirli bir arabirim uygulamanız gerekmez.
Tek gereksinim elinizdeki için temel bir yöntemin kullanımı sağlamaktır.

## <a name="building-your-own-components-with-delegates"></a>Temsilcileri kendi bileşenleriyle oluşturma

Şimdi bu örneğinde yetkililer güvenen bir tasarım kullanarak bir bileşeni oluşturarak oluşturun.

Şimdi, büyük bir sistemde günlüğü iletileri için kullanılabilecek bir bileşen tanımlayın. Kitaplığı bileşenlerini birden çok farklı platformlarda birçok farklı ortamlarda kullanılabilir. Birçok ortak özellik günlüklerini yönetir bileşeninde vardır. Sistemde herhangi bir bileşenin gelen iletileri kabul etmesi gerekir. Bu iletiler çekirdek bileşeni yönetebilirsiniz farklı önceliklere sahip olur. İletileri zaman damgaları kendi son arşivlenmiş biçiminde olması gerekir. Daha Gelişmiş senaryolar için kaynak bileşen tarafından iletileri filtre uygulayabilirsiniz.

Genellikle değiştirecek özelliği tek bir yönüne yoktur: iletileri yazıldığı. Bazı ortamlarda, bunlar hata konsola yazılabilir. Bazı durumlarda, bir dosya. Diğer olasılıklar veritabanı depolama, işletim sistemi olay günlüklerini veya başka bir belge depolama içerir.

Farklı senaryolarda kullanılabilir çıktı birleşimlerini vardır. İletilerini konsola ve bir dosyaya yazmak isteyebilirsiniz.

Temsilciler üzerinde temel tasarım esneklik büyük bir bölümünü sağlayın ve gelecekte eklenebilir destek depolama mekanizmaları kolaylaştırır.

Bu tasarım altında birincil günlük bileşeni bir sanal olmayan, hatta sınıf korumalı olabilir. Farklı depolama ortamına ileti yazmak için temsilciler kümesinden ekleyebilirsiniz. Çok noktaya yayın temsilcileri için yerleşik destek iletileri birden fazla konuma (bir dosya ve bir konsol) burada yazılmalıdır destek senaryoları kolay hale getirir.

## <a name="a-first-implementation"></a>İlk uygulama

Küçük başlayalım: ilk uygulama yeni iletileri kabul edin ve herhangi bir ekli temsilci kullanarak bunları yazma. İletilerini konsola yazar bir temsilci ile başlatabilirsiniz.

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

Yukarıdaki statik sınıf çalışabileceği en basit bir şeydir. İletilerini konsola yazar yöntemi için tek uygulama yazmak ihtiyacımız var: 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

Son olarak, temsilci Günlükçü bildirilen WriteMessage ekleyerek temsilci bağlama gerekir:

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a>Yöntemler

Bizim örnek kadarki de oldukça basittir, ancak bunu hala temsilciler içeren tasarımları için önemli yönergeleri bazılarını göstermektedir.

Çekirdek çerçevesinde tanımlanan temsilci türleri, temsilci ile çalışmak kullanıcıların kolaylaştırır. Yeni türlerini tanımlamak üzere gerekmez ve yeni, özelleştirilmiş temsilci türleri öğrenmek kitaplığınızın kullanan geliştiriciler gerekmez.

Kullanılan arabirimlere olarak minimal ve kadar esnek: yeni bir çıkış Günlükçü oluşturmak için bir yöntem oluşturmanız gerekir. Bu yöntem, bir statik yöntem veya örnek yöntemi olabilir. Herhangi bir erişim olabilir.

## <a name="formatting-output"></a>Çıktı biçimlendirmesi

Bu ilk sürüm bir bit daha sağlam ve diğer günlük mekanizmaları oluşturma başlatın olalım.

Ardından, birkaç bağımsız değişkenleri ekleyelim `LogMessage()` yöntemi günlük sınıfınıza daha fazla yapılandırılmış ileti oluşturur, böylece:

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

Ardından, olalım kullanan `Severity` animasyonun günlüğüne gönderilen iletilere filtre uygulamak için bağımsız değişken çıktı. 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a>Yöntemler

Günlük altyapısı yeni özellik ekledik. Günlükçü bileşeni çok herhangi bir çıktı mekanizma gevşek için herhangi bir Günlükçü temsilci uygulama kodu hiçbir etkisi olmadan bu yeni özellikler eklenebilir.

Bu derleme tutmak gibi daha fazla örnekleri bu gevşek bağlantı herhangi bir değişiklik yapılmadan sitesinin bölümlerini başka konumlara güncelleştirme esneklik nasıl sağladığını görürsünüz. Aslında, daha büyük bir uygulamanın Günlükçü çıktı sınıfları farklı bir derlemede olması ve bile yeniden oluşturulması gerekir.

## <a name="building-a-second-output-engine"></a>İkinci bir çıktı altyapısı oluşturma

Günlük bileşeni iyi geliyor. İletiler bir dosyaya kaydeder bir daha fazla çıkış altyapısı ekleyelim. Bu biraz daha karmaşık bir çıkış altyapısı olacaktır. Dosya işlemleri yalıtır ve dosyayı her zaman sonra her bir yazma kapalı sağlar bir sınıf olacaktır. Sağlar, tüm verileri Temizlenen her ileti oluşturulduktan sonra disk.

Bu dosya tabanlı Günlükçü şöyledir:

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

Bu sınıf oluşturduktan sonra örneğini oluşturabilir ve kendi LogMessage yöntemi Günlükçü bileşenine ekler:

```csharp
var file = new FileLogger("log.txt");
```

Bu iki birbirini dışlamaz. Her iki günlük yöntemleri ekleyin ve iletileri konsolu ve bir dosya oluşturmak:

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

Daha sonra bile aynı uygulamada sisteme herhangi bir sorun olmadan temsilcileri birini kaldırabilirsiniz:

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a>Yöntemler

Şimdi, günlük alt sistemi için ikinci bir çıktı işleyici ekledik.
Bunun doğru dosya sistemi desteklemek için biraz daha fazla altyapı gerekir. Temsilci bir örnek yöntemidir. Bu da özel bir yöntemdir.
Temsilci altyapısını temsilcileri bağlanabildiğinden büyük erişilebilirlik gerek yoktur.

İkinci olarak, temsilci tabanlı tasarım herhangi bir ek kod olmadan birden çok çıktı yöntemlerini sağlar. Birden çok çıktı yöntemlerini desteklemek için herhangi bir ek altyapı yapılandırmanız gerekmez. Bunlar yalnızca başka bir yöntem çağırma listesinde haline gelir.

Özel çıkış yöntemi günlük dosyasındaki kodu dikkat edin. Özel durumlar oluşturmadığını emin olmak için kodlanmıştır. Bu her zaman kesinlikle gerekli olmasa da, genellikle iyi bir uygulama olur. Temsilci yöntemlerinden birini bir özel durum oluşturursa, çağrısının olan kalan temsilcileri çağrılan olmaz.

Son Not Dosya Günlükçü, açma ve kapama dosyanın her günlüğü iletisine göre kaynaklarını yönetmeniz gerekir. Dosya açık tutmak ve size tamamlandığında dosyasını kapatmaya IDisposable uygulayan tercih edebilirsiniz.
Her iki yöntem, avantajları ve dezavantajları vardır. Her ikisi de sınıflar arasında biraz daha fazla bağlantı oluşturun.

Günlükçü sınıfı kodda hiçbiri, her iki senaryoyu desteklemek için güncelleştirilmesi gerekir.

## <a name="handling-null-delegates"></a>İşleme Null temsilciler

Son olarak, böylece hiçbir çıktı mekanizması seçildiğinde bu gibi durumlarda sağlam şimdi LogMessage yöntemi güncelleştirin. Geçerli uygulama özel durum oluşturacak bir `NullReferenceException` zaman `WriteMessage` temsilci bağlı bir çağrı listesi yok.
Hiçbir yöntemi eklendiğinde sessizce devam bir tasarım tercih edebilirsiniz. Bu birlikte null koşullu işlecini kullanarak kolaydır `Delegate.Invoke()` yöntemi:

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

Null koşullu işleç (`?.`) ne zaman short-circuits sol işleneni (`WriteMessage` bu durumda) herhangi bir deneme yapılır bir ileti günlüğe anlamına gelir null.

Bulamaz `Invoke()` yöntemi listelenen belgelerindeki `System.Delegate` veya `System.MulticastDelegate`. Tür uyumlu derleyici oluşturur `Invoke` yöntemi herhangi temsilci bildirilen türü. Bu örnekte, yani `Invoke` tek bir alan `string` bağımsız değişkeni, ve geçersiz bir dönüş türüne sahip.

## <a name="summary-of-practices"></a>Yöntemler özeti

Genişletilemiyor günlük bileşeni beginnings diğer yazarlar ve diğer özellikleri ile gördünüz. Tasarımda temsilciler kullanarak farklı bu bileşenlerin çok gevşek. Bu, birkaç avantaj sağlar. Yeni çıkış mekanizmaları oluşturmak ve bunları sisteme eklemek çok kolaydır. Bu diğer mekanizmalar yalnızca bir yöntem gerekir: günlük iletisi Yazar yöntemi. Bu yeni özellikler eklendiğinde çok esnek bir tasarımdır. Tüm yazan bir yöntem uygulamak için gereken sözleşme. Bu yöntem, bir statik olarak veya yöntemi örneği. Genel, özel veya herhangi bir yasal erişim olabilir.

Günlükçü sınıfı, önemli değişiklikler oluşturmaksızın herhangi bir sayıda yenilikleri veya değişiklikleri yapabilirsiniz. Herhangi bir sınıf gibi önemli değişiklikler riski olmadan ortak API değiştiremezsiniz. Ancak, Günlükçü ve herhangi bir çıktı motorları arasında bağ yalnızca temsilci olduğundan (arabirimleri veya temel sınıflar gibi) diğer türü yok ilgilidir. Bağ olabildiğince küçük.

[Next](events-overview.md)
