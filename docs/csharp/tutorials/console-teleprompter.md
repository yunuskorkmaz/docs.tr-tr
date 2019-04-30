---
title: Konsol Uygulaması
description: Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 3ac4312ba5d6088826fdf151609f6693a265e5a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706474"
---
# <a name="console-application"></a>Konsol Uygulaması

Bu öğretici, .NET Core ve C# dili özellikleri sayısı öğretir. Şunları öğreneceksiniz:

- Temel .NET Core komut satırı arabirimi (CLI)
- Bir C# konsol uygulaması yapısı
- Konsol g/ç
- .NET içindeki dosya g/ç API'leri temelleri
- Görev tabanlı zaman uyumsuz programlama .NET temelleri

Bir metin dosyasını okur ve konsola, metin dosyasının içeriğini yankılayan bir uygulama oluşturacaksınız. Konsola çıktı yüksek sesle okumak eşleştirmek için adım adım. Hız performansındaki veya uygun bir hızda tuşlarına basarak yavaş ' <' (küçüktür) veya ' >' (büyüktür) anahtarları.

Bu öğreticide birçok özellik vardır. Bunları tek tek oluşturalım.

## <a name="prerequisites"></a>Önkoşullar

.NET Core çalıştırmak için makinenizi ayarlamak gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz.
Sık kullandığınız Kod Düzenleyicisi'ni yüklemeniz gerekir.

## <a name="create-the-application"></a>Uygulama oluşturma

İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bu, geçerli bir dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

Bir değişiklik yapmadan başlamadan önce basit bir Hello World uygulamasını çalıştırmak için adımlara Bahsedelim. Uygulamayı oluşturduktan sonra yazın `dotnet restore` komut isteminde. Bu komut, NuGet paket geri yükleme işlemi çalıştırır. NuGet, .NET paket yöneticisidir. Bu komut tüm projeniz için eksik bağımlılıkların indirir. Bu yeni bir proje olduğundan, ilk çalıştırma .NET Core framework yükleyecek şekilde bağımlılıkları hiçbiri yerde değil. Bu ilk adımdan sonra yalnızca çalıştırmanız gerekir `dotnet restore` yeni bağımlı paketler eklediğinizde, veya herhangi birini bağımlılıklarınızı sürümlerini güncelleştirin.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketleri geri yükledikten sonra çalıştırmanız `dotnet build`. Bu yapı altyapısının yürütür ve uygulamanızın yürütülebilir oluşturur. Son olarak, yürüttüğünüz `dotnet run` uygulamanızı çalıştırmak için.

Basit bir Hello World uygulama kodu, Program.cs içinde tüm ' dir. Bu dosyayı sevdiğiniz bir metin düzenleyici ile açın. İlk değişiklikler yapmak üzere çalışıyoruz.
Kullanarak bir dosyanın üst kısmında görmek deyimi:

```csharp
using System;
```

Bu ifade herhangi türlerini, derleyiciye `System` ad alanı kapsamında olan. Kullanmış diğer nesne yönelimli diller gibi C# ad alanlarında türleri düzenlemek için kullanır. Bu Hello World programı farklı değildir. Program ad alanında geçerli dizin adını temel alarak adı alınmış görebilirsiniz. Bu öğreticide, ad alanına adı değiştirelim `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Okuma ve dosyaya Yankı

Metin dosyası okuma ve bu metin konsoluna görüntüleme olanağı eklemek için ilk özelliğidir. İlk olarak, bir metin dosyasına ekleyelim. Kopyalama [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) bu GitHub deposundan dosya [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) , proje dizinine. Bu, uygulamanız için betik olarak hizmet verecektir. Bu konu için örnek uygulamasını indirme hakkında bilgi isterseniz, yönergelere bakın [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konu.

Ardından, aşağıdaki yöntemi ekleyin, `Program` sınıfı (hemen altına `Main` yöntemi):

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

Bu yöntem, iki yeni ad alanı türlerinden kullanır. Bu derleme aşağıdaki iki satırı dosyasının en üstüne eklemeniz gerekir:

```csharp
using System.Collections.Generic;
using System.IO;
```

<xref:System.Collections.Generic.IEnumerable%601> Arabirimi içinde tanımlanan <xref:System.Collections.Generic> ad alanı. <xref:System.IO.File> Sınıfı içinde tanımlanan <xref:System.IO> ad alanı.

Bu yöntem çağrılır C# yöntemi özel türüdür bir *yineleyici yöntem*. Numaralandırıcı yöntemleri gevşek değerlendirilir dizilerini döndürür. Dizideki her öğe dizisi kullanan kod tarafından istendiği oluşturulan anlamına gelir. Numaralandırıcı yöntemlerden birini veya daha fazlasını içeren yöntemlerdir [ `yield return` ](../language-reference/keywords/yield.md) deyimleri. Tarafından döndürülen nesne `ReadFrom` yöntem dizideki her öğe oluşturmak için kod içeriyor. Bu örnekte, metnin bir sonraki satırı kaynak dosyadan okuma ve o dizeyi döndüren içerir. Çağıran kod dizisinden bir sonraki öğeye istekleri her zaman kod sonraki satıra bir metin dosyasından verileri okur ve döndürür. Dosya tamamen okunduğunda, daha fazla öğe yok dizisini gösterir.

Sizin için yeni olabilecek diğer iki C# sözdizimi öğe vardır. [ `using` ](../language-reference/keywords/using-statement.md) Bu yöntem deyiminde kaynak temizleme yönetir. İçinde başlatılan değişkeni `using` deyimi (`reader`, bu örnekte) uygulamalıdır <xref:System.IDisposable> arabirimi. Bu arabirim, tek bir yöntemi tanımlar `Dispose`, çağrılabilir kaynak yayınlandığı zaman. Yürütme kapanış ayracı ulaştığında, derleyici bu çağrı oluşturur `using` deyimi. Derleyicinin ürettiği kodu kullanılarak tanımlanmış bloğundaki kodun bir özel durum olsa bile kaynak serbest bırakılmasını sağlar. deyimi.

`reader` Değişkeni kullanılarak tanımlanmış `var` anahtar sözcüğü. [`var`](../language-reference/keywords/var.md) tanımlayan bir *türü örtük olarak belirlenmiş yerel değişken*. Değişkeninin türü değişkenine atanan nesnenin derleme zamanı türü tarafından belirlenir anlamına gelir. Dönüş değeri olan burada <xref:System.IO.File.OpenText(System.String)> olan yöntemini bir <xref:System.IO.StreamReader> nesne.

Şimdi, dosyayı okumayı kod şimdi doldurun `Main` yöntemi:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Programı çalıştırın (kullanarak `dotnet run`) konsola yazdırılabilir her satırı görebilirsiniz.

## <a name="adding-delays-and-formatting-output"></a>Gecikme ekleme ve çıkışı biçimlendirme

Sahip olduğunuz çok hızlı yüksek sesle okumak için görüntülenmektedir. Şimdi gecikmeleri çıktısında eklemek gerekir. Başladığınızda, siz bazı zaman uyumsuz işleme etkinleştirir çekirdek kodu oluşturuyor olacaksınız. Ancak, ilk adımları bazı ters desenler izler. Ters desenler açıklamalar kodu ekleyin ve daha sonraki adımlarda kod güncelleştirilecek belirtildiği.

Bu bölüm için iki adım vardır. İlk olarak, tüm satırlar yerine tek sözcük döndürülecek yineleyici yöntem güncelleştireceksiniz. Bu değişiklikler ile gerçekleştirilir. Değiştirin `yield return line;` deyimi aşağıdaki kod ile:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Ardından, dosyayı satırlarını kullanma ve nasıl her sözcüğün yazıldıktan sonra gecikme ekleme değiştirmeniz gerekir. Değiştirin `Console.WriteLine(line)` deyiminde `Main` aşağıdaki bloğu ile yöntemi:

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<xref:System.Threading.Tasks.Task> Sınıfı <xref:System.Threading.Tasks> ad alanı, eklemek istediğiniz şekilde `using` deyimini dosyanın üst:

```csharp
using System.Threading.Tasks;
```

Örneği çalıştırın ve çıktıyı denetleyin. Artık, bir 200 ms gecikmeyle tarafından izlenen her bir sözcüğe yazdırılır. Ancak, kaynak metin dosyası 80 karakterden uzun olmayan bir satır sonu sahip birden çok satıra sahip olduğundan görüntülenen çıktının bazı sorunları gösterir. Tarafından kaydırma sırasında okunması zor olabilir. Bu düzeltmek kolay bir işlemdir. Yalnızca her satır uzunluğu izlemek ve yeni bir satır satır uzunluğu belirli bir eşiği eriştiğinde oluşturmak. Bir yerel değişken bildirimi sonra bildirip `words` içinde `ReadFrom` satır uzunluğu tutan yöntemi:

```csharp
var lineLength = 0;
```

Ardından, sonra aşağıdaki kodu ekleyin `yield return word + " ";` deyimi (önce kapanış ayracı):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Örneği çalıştırmak ve sesli okunabilir önceden yapılandırılmış tutulacak uygun bir hızda.

## <a name="async-tasks"></a>Zaman uyumsuz görevleri

Bu son adımda, çıkış hızlandırmak istiyorsanız bir kullanıcıdan giriş veya metin görüntüleme yavaşlamasına okumak için başka bir görev ayrıca çalıştırılırken bir görevde zaman uyumsuz olarak yazmak için kod ekleyin veya metin görüntülemeyi tamamen durdurmak. Bu da ve sonuna birkaç adım vardır, ihtiyacınız olan tüm güncelleştirmeleri gerekir.
Zaman uyumsuz oluşturmak için ilk adımıdır <xref:System.Threading.Tasks.Task> okumak ve dosyayı görüntülemek için oluşturduğunuz şimdiye kodunu temsil eden yöntemi döndürüyor.

Bu yöntemi ekleyin, `Program` sınıfı (gövdesinden alınır, `Main` yöntemi):

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

İki değişiklikler fark edeceksiniz. İlk çağırmak yerine yöntemin gövdesinde <xref:System.Threading.Tasks.Task.Wait> zaman uyumlu olarak bir görevin bitmesini beklemek için bu sürümü kullanan `await` anahtar sözcüğü. Bunu yapabilmek için eklemeniz gerekir `async` değiştiricisi metodu imzası. Bu yöntem döndürür bir `Task`. Geri dönüş deyim olduğuna dikkat edin bir `Task` nesne. Bunun yerine, `Task` nesne kullandığınızda derleyici üretir kod tarafından oluşturulan `await` işleci. Bu yöntem ulaştığında döndürür hayal edebileceğiniz bir `await`. Döndürülen `Task` iş değil tamamlandığını gösterir.
Yöntemi, beklenen görev tamamlandığında sürdürür. Ne zaman yürütülen tamamlanana kadar döndürülen `Task` tam olduğunu gösterir.
Kodu çağırma izlemek için kullanabileceğiniz döndürülen `Task` zaman tamamlandı belirlemek için.

Bu yeni yöntemini çağırabilirsiniz, `Main` yöntemi:

```csharp
ShowTeleprompter().Wait();
```

Burada, `Main`, kod zaman uyumlu olarak bekleyin. Kullanmanız gereken `await` mümkün olduğunda eşzamanlı olarak beklemek yerine işleci. Ancak, bir konsol uygulamasının `Main` yöntemi kullanamaz `await` işleci. Bu, tüm görevleri tamamlanmadan uygulamadan çıkmak içinde neden olur.

> [!NOTE]
> C# 7.1 kullandığınız ya da daha sonra konsol uygulamaları ile oluşturabileceğiniz [ `async` `Main` yöntemi](../whats-new/csharp-7-1.md#async-main).

Konsoldan okunan ve izlemek için ikinci zaman uyumsuz yöntem yazmanıza gerek ardından, ' <' (küçüktür), ' >' (büyüktür) ve 'X' veya 'x' anahtarları. Bu görev için eklediğiniz yöntemi aşağıda verilmiştir:

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

Bu bir lambda ifadesini göstermek için oluşturur bir <xref:System.Action> konsoldan bir anahtar okuyan ve kullanıcının bastığında gecikmesini temsil eden yerel bir değişken değiştirir temsilci ' <' (küçüktür) veya ' >' (büyüktür) anahtarları. Temsilci yöntemi, kullanıcının bastığında 'X' veya 'x' metin görüntülemeyi dilediğiniz zaman durdurmak kullanıcı izin veren anahtarları tamamlanır.
Bu yöntemde <xref:System.Console.ReadKey> engelleyin ve kullanıcıyı bir tuşa basın.

Bu özellik tamamlamak için yeni bir gereksinim `async Task` bu görevlerin her ikisi de başlatan yöntem döndüren (`GetInput` ve `ShowTeleprompter`) ve bu iki görevler arasında paylaşılan veri da yönetir.

Bu iki görevler arasında paylaşılan veri işleyen bir sınıf oluşturmak için zaman var. Bu sınıfı iki genel özellikleri içerir: gecikme ve bayrak `Done` dosya tamamen Okunmuş olduğunu belirtmek için:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

Bu sınıfın yeni bir dosya yerleştirin ve bu sınıfta içine `TeleprompterConsole` yukarıda da gösterildiği gibi bir ad alanı. Eklemeniz gerekecektir bir `using static` deyimi, başvuru `Min` ve `Max` kapsayan sınıf veya ad alanı adları olmadan yöntemleri. A [ `using static` ](../language-reference/keywords/using-static.md) deyimi bir sınıftan yöntemleri alır. Tersine ile budur `using` bu noktaya kadar kullanılan deyimleri, bir ad alanındaki tüm sınıfları aldınız.

```csharp
using static System.Math;
```

Ardından, güncelleştirmeye gerek duyduğunuz `ShowTeleprompter` ve `GetInput` yeni yöntemleri `config` nesne. Bir son yazma `Task` döndüren `async` her iki görevi başlatmak ve ilk görev tamamlandığında çıkmak için yöntemi:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Burada bir yeni yöntem <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağırın. Oluşturan bir `Task` kendi bağımsız değişken listesindeki görevleri tamamladıktan hemen sonra tamamlanır.

Ardından, her ikisi de güncelleştirmeye gerek duyduğunuz `ShowTeleprompter` ve `GetInput` kullanılacak yöntemleri `config` nesne gecikme için:

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Bu yeni sürümü `ShowTeleprompter` yeni bir yöntem çağrıları `TeleprompterConfig` sınıfı. Şimdi, güncelleştirmeye gerek duyduğunuz `Main` çağrılacak `RunTeleprompter` yerine `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Sonuç

Bu öğreticide, bir dizi özellik C# dili ve .NET Core kitaplıkları'ta konsol uygulamaları çalışmayla ilgili gösterdi.
Dil ve burada sunulan sınıfları hakkında daha fazla araştırmak için bu bilgilerine oluşturabilirsiniz. Dosya ve konsol g/ç, görev tabanlı zaman uyumsuz programlama, gezdiriyor C# dili ve C# programları nasıl düzenlendiği ve .NET Core komut satırı arabirimi ve araçları engelleyici ve engelleyici olmayan kullanımı hakkındaki temel bilgileri öğrendiniz.

Dosya g/ç hakkında daha fazla bilgi için bkz: [dosya ve Stream g/ç](../../standard/io/index.md) konu. Bu öğreticide kullanılan zaman uyumsuz programlama modeli hakkında daha fazla bilgi için bkz. [görev tabanlı zaman uyumsuz programlama](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konu ve [zaman uyumsuz programlama](../async.md) konu.
