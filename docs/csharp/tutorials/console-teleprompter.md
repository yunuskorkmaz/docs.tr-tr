---
title: Konsol Uygulaması
description: Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 4c32b08c3e7eeaedce687ea5bc572e6a7bee0d3e
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804900"
---
# <a name="console-app"></a>Konsol uygulaması

Bu öğretici, .NET Core ve C# dilinde birçok özellik öğretir. Şunları öğreneceksiniz:

- .NET Core CLI temel kavramları
- C# konsol uygulamasının yapısı
- Konsol g/ç
- .NET 'teki dosya g/ç API 'Lerinin temelleri
- .NET ' te görev tabanlı zaman uyumsuz programlama temelleri

Bir metin dosyasını okuyan ve bu metin dosyasının içeriğini konsola yansıtan bir uygulama oluşturacaksınız. Konsola giden çıkış, okumayı yüksek sesle eşleştirmeye yönelik olarak ilerleyebileceğiniz bir adım adım olur. ' < ' (küçüktür) veya ' > ' (büyüktür) anahtarlarına basarak hızla hızlandıramaz veya azaltabilirsiniz.

Bu öğreticide birçok özellik vardır. Bunları birer birer oluşturalım.

## <a name="prerequisites"></a>Önkoşullar

- Makinenizi .NET Core çalıştıracak şekilde ayarlayın. Yükleme yönergelerini [.NET Core İndirmeleri](https://dotnet.microsoft.com/download) sayfasında bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.

- En sevdiğiniz kod düzenleyicinizi yükler.

## <a name="create-the-app"></a>Uygulama oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizini oluşturun. Komutu `dotnet new console` komut istemine yazın. Bu, temel bir "Merhaba Dünya" uygulaması için başlangıç dosyalarını oluşturur.

Değişiklik yapmaya başlamadan önce, basit Merhaba Dünya uygulamasını çalıştırmak için adımları ilerlim. Uygulamayı oluşturduktan sonra `dotnet restore` komut istemine yazın. Bu komut NuGet paketi geri yükleme işlemini çalıştırır. NuGet bir .NET paket yöneticisidir. Bu komut, projeniz için eksik bağımlılıkları indirir. Bu yeni bir proje olduğundan, bağımlılıklardan hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core çerçevesini indirir. Bu ilk adımdan sonra yalnızca `dotnet restore` yeni bağımlı paketler eklediğinizde veya bağımlılıklarınızın herhangi birinin sürümlerini güncelleştirdiğinizde çalıştırmanız gerekir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketleri geri yükledikten sonra çalıştırın `dotnet build` . Bu, yapı altyapısını yürütür ve uygulamanızı çalıştırılabilir olarak oluşturur. Son olarak, `dotnet run` uygulamanızı çalıştırmak için yürütün.

Basit Merhaba Dünya uygulama kodu Program.cs ' de bulunur. Bu dosyayı en sevdiğiniz metin düzenleyicinizle açın. İlk değişikliklerimizi yapmak bizim için çalışıyoruz. Dosyanın en üstünde, bkz. using deyimleri:

```csharp
using System;
```

Bu ifade, derleyiciye ad alanındaki herhangi bir türün `System` kapsam içinde olduğunu söyler. Kullandığınız diğer nesne yönelimli diller gibi, C#, türleri düzenlemek için ad alanlarını kullanır. Bu Merhaba Dünya program farklı değildir. Programın adı ile geçerli dizinin adına bağlı olarak ad alanı içinde bulunduğunu görebilirsiniz. Bu öğretici için ad alanının adını şu şekilde değiştirelim `TeleprompterConsole` :

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Dosyayı okuma ve Yankılandırın

Eklenecek ilk özellik, bir metin dosyasını okuma ve bu metnin tümünü konsola görüntüleme olanağıdır. İlk olarak bir metin dosyası ekleyelim. Bu [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) için GitHub deposundan [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) dosyasını proje dizininize kopyalayın. Bu, uygulamanız için komut dosyası olarak görev yapar. Bu konu için örnek uygulamanın nasıl indirileceği hakkında bilgi isterseniz, [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#view-and-download-samples) konusundaki yönergelere bakın.

Sonra, sınıfınıza aşağıdaki yöntemi ekleyin `Program` (yöntemin altına doğru `Main` ):

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

<xref:System.Collections.Generic.IEnumerable%601>Arabirim <xref:System.Collections.Generic> ad alanında tanımlanır. <xref:System.IO.File>Sınıf <xref:System.IO> ad alanında tanımlanır.

Bu yöntem, *yineleyici yöntemi*olarak adlandırılan özel bir C# yöntemi türüdür. Numaralandırıcı yöntemleri değerlendirilen dizileri döndürür geç. Bu, dizideki her öğe, diziyi kullanan kod tarafından istenerek oluşturulduğu anlamına gelir. Numaralandırıcı yöntemleri bir veya daha fazla deyim içeren yöntemlerdir [`yield return`](../language-reference/keywords/yield.md) . Yöntemi tarafından döndürülen nesne, `ReadFrom` dizideki her bir öğeyi oluşturmak için kodu içerir. Bu örnekte, kaynak dosyadaki bir sonraki metin satırını okumayı ve bu dizeyi döndürmeyle ilgilidir. Çağıran kod, sıradaki bir sonraki öğeyi her istediğinde, kod dosyadaki metnin bir sonraki satırını okur ve döndürür. Dosya tamamen okunmadığında, dizi daha fazla öğe olmadığını gösterir.

Sizin için yeni olabilecek iki C# sözdizimi öğesi vardır. [`using`](../language-reference/keywords/using-statement.md)Bu yöntemdeki deyimin kaynağı temizleme işlemini yönetir. İfadesinde başlatılan değişken `using` ( `reader` Bu örnekte) <xref:System.IDisposable> arabirimini uygulamalıdır. Bu arabirim, `Dispose` kaynak yayımlanacaksa çağrılması gereken tek bir yöntemini tanımlar. , Yürütme deyimin kapanış ayracına ulaştığında derleyici bu çağrıyı oluşturur `using` . Derleyici tarafından oluşturulan kod, using ifadesiyle tanımlanan bloktaki koddan bir özel durum oluşsa bile kaynağın serbest bırakılacağını sağlar.

`reader`Değişkeni, anahtar sözcüğü kullanılarak tanımlanır `var` . [`var`](../language-reference/keywords/var.md)*örtük olarak yazılmış bir yerel değişken*tanımlar. Bu, değişkenin türü değişkene atanan nesnenin derleme zamanı türü tarafından belirlendiği anlamına gelir. Burada, <xref:System.IO.File.OpenText(System.String)> bir nesnesi olan yönteminden döndürülen değer <xref:System.IO.StreamReader> .

Şimdi, yöntemi içindeki dosyayı okumak için kodu dolduralım `Main` :

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Programı çalıştırın (kullanarak `dotnet run` ) ve konsolda yazdırılan her satırı görebilirsiniz.

## <a name="adding-delays-and-formatting-output"></a>Gecikme ve biçimlendirme çıktısı ekleme

Ne kadar hızlı görüntülendikleriniz çok yüksek. Şimdi çıktıdaki gecikmeleri eklemeniz gerekir. Başladığınızda, zaman uyumsuz işleme sağlayan çekirdek koddan bazılarını oluşturacaksınız. Bununla birlikte, bu ilk adımlar birkaç tane kenar deseninden daha izlenecek. Siz kodu eklerken yorumlara desenler görüntülenir ve kod sonraki adımlarda güncelleştirilir.

Bu bölümde iki adım vardır. İlk olarak, yineleyici yöntemini tüm satırlar yerine tek bir sözcük döndürecek şekilde güncelleştireceksiniz. Bu değişiklikler bu değişikliklerle yapılır. `yield return line;`İfadesini aşağıdaki kodla değiştirin:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Ardından, dosyanın satırlarını nasıl kullanacağınızı değiştirmeniz ve her bir kelime yazıldıktan sonra bir gecikme eklemeniz gerekir. `Console.WriteLine(line)`Yöntemi içindeki ifadesini `Main` aşağıdaki bloğa değiştirin:

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

<xref:System.Threading.Tasks.Task>Sınıf <xref:System.Threading.Tasks> ad alanında olduğundan, bu `using` ifadeyi dosyanın en üstüne eklemeniz gerekir:

```csharp
using System.Threading.Tasks;
```

Örneği çalıştırın ve çıktıyı denetleyin. Şimdi, her bir sözcük yazdırılır ve ardından 200 ms gecikme gelir. Ancak, görüntülenen çıktıda bazı sorunlar gösterilmektedir çünkü kaynak metin dosyasında satır sonu olmadan 80 ' ten fazla karakter içeren birkaç satır vardır. Bu, kaydırma sırasında okunması zor olabilir. Bu, düzeltilmesi kolay bir işlemdir. Her satırın uzunluğunu takip edersiniz ve satır uzunluğu belirli bir eşiğe ulaştığında yeni bir satır oluşturacaksınız. `words`Satır uzunluğunu tutan yöntemde öğesinin bildiriminden sonra bir yerel değişken bildirin `ReadFrom` :

```csharp
var lineLength = 0;
```

Sonra, deyimden sonra aşağıdaki kodu ekleyin `yield return word + " ";` (kapanış ayracından önce):

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

Bu son adımda, çıktıyı zaman uyumsuz olarak bir görevde yazacak şekilde, Ayrıca metin görüntüsünü hızlandırmak veya yavaşlatacak şekilde Kullanıcı girişini okumak için başka bir görevi çalıştırırken, metin görüntülemeyi tamamen durdurmak için kodu ekleyeceksiniz. Bunun içinde ve sonunda birkaç adım vardır, ihtiyacınız olan tüm güncelleştirmelere sahip olacaksınız. İlk adım, <xref:System.Threading.Tasks.Task> dosyayı okuyup görüntülemesi için oluşturduğunuz kodu temsil eden zaman uyumsuz bir döndürme yöntemi oluşturmaktır.

Bu yöntemi `Program` sınıfınıza ekleyin (yönteminizin gövdesinden alınır `Main` ):

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

İki değişiklik fark edeceksiniz. İlk olarak, yöntemin gövdesinde, <xref:System.Threading.Tasks.Task.Wait> bir görevin bitmesini zaman uyumlu olarak beklemek yerine, bu sürüm `await` anahtar sözcüğünü kullanır. Bunu yapmak için, `async` Yöntem imzasına değiştiricisini eklemeniz gerekir. Bu yöntem bir döndürür `Task` . Bir nesne döndüren return deyimi olmadığına dikkat edin `Task` . Bunun yerine, `Task` işleci kullandığınızda derleyicinin oluşturduğu kodla bu nesne oluşturulur `await` . Bu yöntemin bir öğesine ulaştığında geri döndüğünü hayal edebilirsiniz `await` . Döndürülen `Task` iş tamamlanmadığını gösterir. Yöntemi, beklenen görev tamamlandığında devam eder. Tamamlanmayı yürütüldüğünde, döndürülen `Task` bunun tamamlandığını gösterir.
Çağıran kod, `Task` ne zaman tamamlandığını anlamak için döndürülen ' i izleyebilir.

Bu yeni yöntemi, yönteyinizdeki çağırabilirsiniz `Main` :

```csharp
ShowTeleprompter().Wait();
```

Burada, ' de, `Main` kod zaman uyumlu olarak bekler. `await`Mümkün olduğunca zaman uyumlu bekleme yerine işlecini kullanmanız gerekir. Ancak, bir konsol uygulamasının `Main` yönteminde `await` işlecini kullanamazsınız. Bu, uygulamanın tüm görevler tamamlanmadan çıkılması ile sonuçlanır.

> [!NOTE]
> C# 7,1 veya sonraki bir sürümünü kullanıyorsanız, [ `async` `Main` yöntemiyle](../whats-new/csharp-7.md#async-main)konsol uygulamaları oluşturabilirsiniz.

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

Bu, konsolundan bir anahtarı okuyan bir temsilciyi temsil eden bir lambda ifadesi oluşturur <xref:System.Action> ve Kullanıcı ' < ' (küçüktür) veya ' > ' (büyüktür) anahtarlarına bastığında gecikmeyi temsil eden yerel bir değişkeni değiştirir. Temsilci yöntemi, Kullanıcı ' X ' veya ' x ' tuşlarına bastığında sona erdiğinde, kullanıcının metin görüntüsünü istediğiniz zaman durdurmasına izin verir. Bu yöntem <xref:System.Console.ReadKey> engellemek için kullanır ve kullanıcının bir tuşa basması için bekler.

Bu özelliği bitirebilmeniz için, bu `async Task` görevlerin her ikisini de (ve) Başlatan yeni bir döndürme yöntemi oluşturmanız `GetInput` `ShowTeleprompter` ve ayrıca bu iki görev arasındaki paylaşılan verileri de yönetmesi gerekir.

Bu iki görev arasında paylaşılan verileri işleyebilen bir sınıf oluşturmak zaman alabilir. Bu sınıf iki genel özellik içerir: gecikme ve `Done` dosyanın tamamen okunduğunu belirten bir bayrak:

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

Bu sınıfı yeni bir dosyaya yerleştirin ve bu sınıfı `TeleprompterConsole` yukarıda gösterildiği gibi ad alanına iliştirin. Ayrıca `using static` , `Min` `Max` kapsayan sınıf veya ad alanı adları olmadan ve yöntemlerine başvurabilmeniz için bir ifade eklemeniz gerekecektir. Bir [`using static`](../language-reference/keywords/using-static.md) ifade yöntemleri bir sınıftan içeri aktarır. Bu, `using` bir ad alanından tüm sınıfları içeri aktarmış olan bu noktaya kadar kullanılan deyimlerle aynıdır.

```csharp
using static System.Math;
```

Ardından, `ShowTeleprompter` `GetInput` Yeni nesnesini kullanmak için ve yöntemlerini güncelleştirmeniz gerekir `config` . `Task` `async` Her iki görevi başlatmak için bir son döndürme yöntemi yazın ve ilk görev tamamlandığında çıkış yapın:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Çağrı burada yeni bir yöntemdir <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> . Bu, `Task` bağımsız değişken listesindeki görevlerden herhangi biri tamamlandıktan hemen sonra tamamlanmış bir oluşturur.

Sonra, `ShowTeleprompter` `GetInput` gecikme için nesnesini kullanmak üzere hem hem de yöntemlerini güncelleştirmeniz gerekir `config` :

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

Bu yeni sürümü `ShowTeleprompter` , sınıfında yeni bir yöntemi çağırır `TeleprompterConfig` . Şimdi aşağıdakileri `Main` yerine çağırmak için güncelleştirmeniz gerekir `RunTeleprompter` `ShowTeleprompter` :

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Sonuç

Bu öğretici, C# dili ve konsol uygulamalarında çalışmaya yönelik .NET Core kitaplıkları etrafında birçok özellik olduğunu gösterdi. Bu bilgiyi, dil ve burada tanıtılan sınıflar hakkında daha fazla bilgi için oluşturabilirsiniz. Dosya ve konsol g/ç ile ilgili temel bilgileri, görev tabanlı zaman uyumsuz programlamayı engelleme ve engellemeyen kullanımı, C# dilinin bir turu ve C# programlarının nasıl düzenlendiğini ve .NET Core CLI olduğunu gördünüz.

Dosya g/ç hakkında daha fazla bilgi için bkz. [dosya ve akış g/ç](../../standard/io/index.md) konusu. Bu öğreticide kullanılan zaman uyumsuz programlama modeli hakkında daha fazla bilgi için [görev tabanlı zaman uyumsuz programlama](../../standard/parallel-programming/task-based-asynchronous-programming.md) konusuna ve [zaman uyumsuz programlama](../async.md) konusuna bakın.
