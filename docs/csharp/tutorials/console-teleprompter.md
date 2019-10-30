---
title: Konsol Uygulaması
description: Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 2b9948ce22eb221d9d757fcec4c556d365469fdf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039258"
---
# <a name="console-application"></a>Konsol Uygulaması

Bu öğretici, .NET Core ve bu C# dilin çeşitli özelliklerini öğretir. Şunları öğreneceksiniz:

- .NET Core komut satırı arabirimi (CLı) temelleri
- C# Konsol uygulamasının yapısı
- Konsol g/ç
- .NET 'teki dosya g/ç API 'Lerinin temelleri
- .NET ' te görev tabanlı zaman uyumsuz programlama temelleri

Bir metin dosyasını okuyan ve bu metin dosyasının içeriğini konsola yansıtan bir uygulama oluşturacaksınız. Konsola giden çıkış, okumayı yüksek sesle eşleştirmeye yönelik olarak ilerleyebileceğiniz bir adım adım olur. ' < ' (Küçüktür) veya ' > ' (büyüktür) anahtarlarına basarak hızla hızlandıramaz veya azaltabilirsiniz.

Bu öğreticide birçok özellik vardır. Bunları birer birer oluşturalım.

## <a name="prerequisites"></a>Prerequisites

.NET Core 'u çalıştırmak için makinenizi ayarlamanız gerekir. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya bir Docker kapsayıcısında çalıştırabilirsiniz.
En sevdiğiniz kod düzenleyicinizi yüklemeniz gerekir.

## <a name="create-the-application"></a>Uygulamayı oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizini oluşturun. Komut istemine komut `dotnet new console` yazın. Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.

Değişiklik yapmaya başlamadan önce, basit Merhaba Dünya uygulamasını çalıştırmak için adımları ilerlim. Uygulamayı oluşturduktan sonra komut istemine `dotnet restore` yazın. Bu komut NuGet paketi geri yükleme işlemini çalıştırır. NuGet bir .NET paket yöneticisidir. Bu komut, projeniz için eksik bağımlılıkları indirir. Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core çerçevesini indirir. Bu ilk adımdan sonra, yalnızca yeni bağımlı paketler eklediğinizde `dotnet restore` çalıştırmanız veya bağımlılıklarınızın herhangi birinin sürümlerini güncelleştirmeniz gerekir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketleri geri yükledikten sonra `dotnet build`çalıştırırsınız. Bu, yapı altyapısını yürütür ve uygulamanızı çalıştırılabilir olarak oluşturur. Son olarak, uygulamanızı çalıştırmak için `dotnet run` yürütün.

Basit Merhaba Dünya uygulama kodu Program.cs ' de bulunur. Bu dosyayı en sevdiğiniz metin düzenleyicinizle açın. İlk değişikliklerimizi yapmak bizim için çalışıyoruz.
Dosyanın en üstünde, bkz. using deyimleri:

```csharp
using System;
```

Bu ifade, derleyiciye `System` ad alanındaki herhangi bir türün kapsam içinde olduğunu söyler. Kullandığınız diğer nesne yönelimli diller gibi, C# türleri düzenlemek için ad alanlarını kullanır. Bu Merhaba Dünya program farklı değildir. Programın adı ile geçerli dizinin adına bağlı olarak ad alanı içinde bulunduğunu görebilirsiniz. Bu öğretici için ad alanının adını `TeleprompterConsole`olarak değiştirelim:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Dosyayı okuma ve Yankılandırın

Eklenecek ilk özellik, bir metin dosyasını okuma ve bu metnin tümünü konsola görüntüleme olanağıdır. İlk olarak bir metin dosyası ekleyelim. Bu [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) için GitHub deposundan [samplequotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) dosyasını proje dizininize kopyalayın. Bu, uygulamanız için komut dosyası olarak görev yapar. Bu konu için örnek uygulamanın nasıl indirileceği hakkında bilgi isterseniz, [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konusundaki yönergelere bakın.

Sonra, `Program` Sınıfınıza aşağıdaki yöntemi ekleyin (`Main` yönteminin hemen altına):

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

Bu yöntem iki yeni ad alanından türler kullanır. Bu derleme için, dosyanın en üstüne aşağıdaki iki satırı eklemeniz gerekir:

```csharp
using System.Collections.Generic;
using System.IO;
```

<xref:System.Collections.Generic.IEnumerable%601> arabirimi <xref:System.Collections.Generic> ad alanında tanımlanmıştır. <xref:System.IO.File> sınıfı, <xref:System.IO> ad alanında tanımlanmıştır.

Bu yöntem, *yineleyici yöntemi*olarak adlandırılan C# özel bir yöntem türüdür. Numaralandırıcı yöntemleri değerlendirilen dizileri döndürür geç. Bu, dizideki her öğe, diziyi kullanan kod tarafından istenerek oluşturulduğu anlamına gelir. Numaralandırıcı yöntemleri bir veya daha fazla [`yield return`](../language-reference/keywords/yield.md) deyimi içeren yöntemlerdir. `ReadFrom` yöntemi tarafından döndürülen nesne, dizideki her bir öğeyi oluşturmak için kodu içerir. Bu örnekte, kaynak dosyadaki bir sonraki metin satırını okumayı ve bu dizeyi döndürmeyle ilgilidir. Çağıran kod, sıradaki bir sonraki öğeyi her istediğinde, kod dosyadaki metnin bir sonraki satırını okur ve döndürür. Dosya tamamen okunmadığında, dizi daha fazla öğe olmadığını gösterir.

Size yeni olabilecek iki C# farklı sözdizimi öğesi vardır. Bu yöntemdeki [`using`](../language-reference/keywords/using-statement.md) ifadesinin kaynağı temizleme işlemini yönetir. `using` bildiriminde (`reader`, bu örnekte) başlatılan değişken <xref:System.IDisposable> arabirimini gerçekleştirmelidir. Bu arabirim, kaynak yayınlanacaksa çağrılması gereken tek bir yöntemi `Dispose`tanımlar. , Yürütme `using` deyimin kapanış ayracına ulaştığında derleyici bu çağrıyı oluşturur. Derleyici tarafından oluşturulan kod, using ifadesiyle tanımlanan bloktaki koddan bir özel durum oluşsa bile kaynağın serbest bırakılacağını sağlar.

`reader` değişkeni `var` anahtar sözcüğü kullanılarak tanımlanır. [`var`](../language-reference/keywords/var.md) *örtük olarak yazılmış bir yerel değişkeni*tanımlar. Bu, değişkenin türü değişkene atanan nesnenin derleme zamanı türü tarafından belirlendiği anlamına gelir. Burada, bir <xref:System.IO.StreamReader> nesnesi olan <xref:System.IO.File.OpenText(System.String)> yönteminin dönüş değeridir.

Şimdi de `Main` yönteminde dosyayı okumak için kodu dolduralım:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Programı çalıştırın (`dotnet run`kullanarak) ve konsolda yazdırılan her satırı görebilirsiniz.

## <a name="adding-delays-and-formatting-output"></a>Gecikme ve biçimlendirme çıktısı ekleme

Ne kadar hızlı görüntülendikleriniz çok yüksek. Şimdi çıktıdaki gecikmeleri eklemeniz gerekir. Başladığınızda, zaman uyumsuz işleme sağlayan çekirdek koddan bazılarını oluşturacaksınız. Bununla birlikte, bu ilk adımlar birkaç tane kenar deseninden daha izlenecek. Siz kodu eklerken yorumlara desenler görüntülenir ve kod sonraki adımlarda güncelleştirilir.

Bu bölümde iki adım vardır. İlk olarak, yineleyici yöntemini tüm satırlar yerine tek bir sözcük döndürecek şekilde güncelleştireceksiniz. Bu değişiklikler bu değişikliklerle yapılır. `yield return line;` ifadesini aşağıdaki kodla değiştirin:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Ardından, dosyanın satırlarını nasıl kullanacağınızı değiştirmeniz ve her bir kelime yazıldıktan sonra bir gecikme eklemeniz gerekir. `Main` yöntemindeki `Console.WriteLine(line)` ifadesini aşağıdaki blokla değiştirin:

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

<xref:System.Threading.Tasks.Task> sınıfı <xref:System.Threading.Tasks> ad alanında olduğundan, bu `using` ifadesini dosyanın en üstüne eklemeniz gerekir:

```csharp
using System.Threading.Tasks;
```

Örneği çalıştırın ve çıktıyı denetleyin. Şimdi, her bir sözcük yazdırılır ve ardından 200 ms gecikme gelir. Ancak, görüntülenen çıktıda bazı sorunlar gösterilmektedir çünkü kaynak metin dosyasında satır sonu olmadan 80 ' ten fazla karakter içeren birkaç satır vardır. Bu, kaydırma sırasında okunması zor olabilir. Bu, düzeltilmesi kolay bir işlemdir. Her satırın uzunluğunu takip edersiniz ve satır uzunluğu belirli bir eşiğe ulaştığında yeni bir satır oluşturacaksınız. Satır uzunluğunu tutan `ReadFrom` yönteminde `words` bildiriminden sonra yerel bir değişken bildirin:

```csharp
var lineLength = 0;
```

Sonra, `yield return word + " ";` deyiminden sonra aşağıdaki kodu ekleyin (kapatma küme ayracından önce):

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Örneği çalıştırın, daha önceden yapılandırılmış hızda sesli okuyabileceksiniz.

## <a name="async-tasks"></a>Zaman uyumsuz görevler

Bu son adımda, çıktıyı zaman uyumsuz olarak bir görevde yazacak şekilde, Ayrıca metin görüntüsünü hızlandırmak veya yavaşlatacak şekilde Kullanıcı girişini okumak için başka bir görevi çalıştırırken, metin görüntülemeyi tamamen durdurmak için kodu ekleyeceksiniz. Bunun içinde ve sonunda birkaç adım vardır, ihtiyacınız olan tüm güncelleştirmelere sahip olacaksınız.
İlk adım, dosyayı okuyup görüntülemesi için oluşturduğunuz kodu temsil eden zaman uyumsuz <xref:System.Threading.Tasks.Task> döndüren bir yöntem oluşturmaktır.

Bu yöntemi `Program` sınıfa ekleyin (`Main` yönteminizin gövdesinden alınır):

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

İki değişiklik fark edeceksiniz. İlk olarak, yöntemin gövdesinde, bir görevin bitmesini zaman uyumlu olarak beklemek <xref:System.Threading.Tasks.Task.Wait> yerine, bu sürüm `await` anahtar sözcüğünü kullanır. Bunu yapmak için yöntem imzasına `async` değiştiricisini eklemeniz gerekir. Bu yöntem bir `Task`döndürür. `Task` nesnesi döndüren bir dönüş deyimi olmadığına dikkat edin. Bunun yerine, `Task` nesnesi, `await` işlecini kullandığınızda derleyicinin oluşturduğu kodla oluşturulur. Bu yöntemin, bir `await`ulaştığında döndürdüğünü düşünün. Döndürülen `Task`, çalışmanın tamamlanmadığını gösterir.
Yöntemi, beklenen görev tamamlandığında devam eder. Tamamlanmayı yürütüldüğünde, döndürülen `Task` tamamlandığını gösterir.
Çağıran kod, ne zaman tamamlandığını öğrenmek için döndürülen `Task` izleyebilir.

`Main` yönteminde bu yeni yöntemi çağırabilirsiniz:

```csharp
ShowTeleprompter().Wait();
```

Burada `Main`, kod zaman uyumlu olarak bekler. Mümkün olduğunca zaman uyumlu bekleme yerine `await` işlecini kullanmanız gerekir. Ancak, bir konsol uygulamasının `Main` yönteminde `await` işlecini kullanamazsınız. Bu, uygulamanın tüm görevler tamamlanmadan çıkılması ile sonuçlanır.

> [!NOTE]
> C# 7,1 veya sonraki bir sürümü kullanıyorsanız, [`async` `Main` yöntemiyle](../whats-new/csharp-7-1.md#async-main)konsol uygulamaları oluşturabilirsiniz.

Sonra, konsolundan okumak için ikinci zaman uyumsuz yöntemi yazmanız ve ' < ' (küçüktür), ' > ' (büyüktür) ve ' x ' veya ' x ' tuşlarından daha fazla bilgi almanız gerekir. Bu görev için eklediğiniz yöntem aşağıda verilmiştir:

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

Bu, konsolundan bir anahtar okuyan bir <xref:System.Action> temsilcisini temsil eden bir lambda ifadesi oluşturur ve Kullanıcı ' < ' (küçüktür) veya ' > ' (büyüktür) tuşlarından sonra gelen gecikmeyi temsil eden yerel bir değişkeni değiştirir. Temsilci yöntemi, Kullanıcı ' X ' veya ' x ' tuşlarına bastığında sona erdiğinde, kullanıcının metin görüntüsünü istediğiniz zaman durdurmasına izin verir.
Bu yöntem, engellemek için <xref:System.Console.ReadKey> kullanır ve kullanıcının bir tuşa basması için bekleyin.

Bu özelliği bitirebilmeniz için, bu görevlerin her ikisini de (`GetInput` ve `ShowTeleprompter`) Başlatan yeni bir `async Task` döndürme yöntemi oluşturmanız ve ayrıca bu iki görev arasındaki paylaşılan verileri de yönetmesi gerekir.

Bu iki görev arasında paylaşılan verileri işleyebilen bir sınıf oluşturmak zaman alabilir. Bu sınıf iki genel özellik içerir: gecikme ve bir bayrak, dosyanın tamamen okunduğunu göstermek için `Done`:

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

Bu sınıfı yeni bir dosyaya yerleştirin ve bu sınıfı yukarıda gösterildiği gibi `TeleprompterConsole` ad alanına iliştirin. Ayrıca, kapsayan sınıf veya ad alanı adları olmadan `Min` ve `Max` yöntemlerine başvurabilmeniz için `using static` bir ifade eklemeniz gerekir. [`using static`](../language-reference/keywords/using-static.md) bir ifade, bir sınıftan yöntemleri içeri aktarır. Bu, bir ad alanından tüm sınıfları içeri aktarmış olan bu noktaya kadar kullanılan `using` deyimlerinden farklıdır.

```csharp
using static System.Math;
```

Sonra, yeni `config` nesnesini kullanmak için `ShowTeleprompter` ve `GetInput` yöntemlerini güncelleştirmeniz gerekir. Her iki görevi başlatmak ve ilk görev tamamlandığında çıkış yapmak için `async` yöntemi döndüren bir son `Task` yazın:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Burada yeni bir yöntem <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağrıdır. Bu, bağımsız değişken listesindeki görevlerden herhangi biri tamamlandıktan hemen sonra sona erbir `Task` oluşturur.

Sonra, gecikme için `config` nesnesini kullanmak üzere hem `ShowTeleprompter` hem de `GetInput` yöntemlerini güncelleştirmeniz gerekir:

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

`ShowTeleprompter` yeni sürümü `TeleprompterConfig` sınıfında yeni bir yöntemi çağırır. Şimdi, `ShowTeleprompter`yerine `RunTeleprompter` çağırmak için `Main` güncelleştirmeniz gerekir:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Sonuç

Bu öğreticide, C# dil etrafındaki ve konsol uygulamalarında çalışmaya yönelik .NET Core kitaplıklarının çeşitli özellikleri gösterildi.
Bu bilgiyi, dil ve burada tanıtılan sınıflar hakkında daha fazla bilgi için oluşturabilirsiniz. Dosya ve konsol g/ç, görev tabanlı zaman uyumsuz programlama ile ilgili temel bilgileri, C# dilin bir turuna ve programların nasıl C# düzenlendiğini ve .NET Core komut satırı arabirimini ve araçlarını gördünüz.

Dosya g/ç hakkında daha fazla bilgi için bkz. [dosya ve akış g/ç](../../standard/io/index.md) konusu. Bu öğreticide kullanılan zaman uyumsuz programlama modeli hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz programlama](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konusuna ve [zaman uyumsuz programlama](../async.md) konusuna bakın.
