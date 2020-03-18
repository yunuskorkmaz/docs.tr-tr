---
title: Konsol Uygulaması
description: Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921130"
---
# <a name="console-app"></a>Konsol uygulaması

Bu öğretici size .NET Core ve C# dillerinde bir dizi özellik öğretir. Şunları öğreneceksiniz:

- .NET Çekirdek CLI'nin temelleri
- C# Console Uygulamasının yapısı
- Konsol I/O
- .NET'teki Dosya G/Ç API'lerinin temelleri
- .NET'te Görev Tabanlı Eşzamanlı Programlamanın temelleri

Metin dosyasını okuyan ve bu metin dosyasının içeriğini konsola yansıtan bir uygulama oluşturursunuz. Konsola çıkış yüksek sesle okuma maç için tempolu. '<' (daha az) veya '>' (büyük) tuşlarına basarak hızı hızlandırabilir veya yavaşlatabilirsiniz.

Bu öğretici özellikleri bir yeri vardır. Onları teker teker inşa edelim.

## <a name="prerequisites"></a>Önkoşullar

- Makinenizi .NET Core'u çalıştıracak şekilde ayarlayın. Yükleme yönergelerini [.NET Core indirme sayfasında](https://dotnet.microsoft.com/download) bulabilirsiniz. Bu uygulamayı Windows, Linux, macOS veya Docker kapsayıcısında çalıştırabilirsiniz.

- En sevdiğiniz kod düzenleyicisini yükleyin.

## <a name="create-the-app"></a>Uygulama oluşturma

İlk adım yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Bunu geçerli dizini yapın. Komut istemine komut `dotnet new console` yazın. Bu, temel bir "Hello World" uygulaması için başlangıç dosyalarını oluşturur.

Değişiklikler yapmaya başlamadan önce, basit Hello World uygulamasını çalıştırmak için gereken adımları gözden geçirelim. Uygulamayı oluşturduktan sonra `dotnet restore` komut istemine yazın. Bu komut NuGet paket geri yükleme işlemini çalıştırAr. NuGet bir .NET paket yöneticisidir. Bu komut, projeniz için eksik bağımlılıklardan herhangi birini karşıdan yükler. Bu yeni bir proje olduğundan, bağımlılıkların hiçbiri yerinde değildir, bu nedenle ilk çalıştırma .NET Core çerçevesini karşıdan yüklez. Bu ilk adımdan sonra, yalnızca `dotnet restore` yeni bağımlı paketler eklediğinizde veya bağımlılıklarınızın sürümlerini güncelleştirdiğinizde çalışmanız gerekir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Paketleri geri aldıktan sonra, `dotnet build`çalıştırın. Bu, yapı altyapısını yürütür ve uygulamanızın çalıştırılabilir hale getirmesini oluşturur. Son olarak, `dotnet run` uygulamanızı çalıştırmak için çalıştırın.

Basit Hello World uygulama kodu tüm Program.cs. Bu dosyayı en sevdiğiniz metin düzenleyicisiyle açın. İlk değişikliklerimizi yapmak üzereyiz. Dosyanın üst kısmında, aşağıdakileri kullanarak bir ifadeye bakın:

```csharp
using System;
```

Bu deyim derleyiciye `System` ad alanından herhangi bir türün kapsam içinde olduğunu bildirir. Kullanmış olabileceğiniz diğer Nesne Yönelimli diller gibi, C# türleri düzenlemek için ad alanlarını kullanır. Bu Hello World programı da farklı değil. Programın ad alanına, geçerli dizinin adını temel alan bir şekilde ekte olduğunu görebilirsiniz. Bu öğretici için, ad alanının adını şu `TeleprompterConsole`şekilde değiştirelim:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Dosyayı Okuma ve Yankılama

Eklemek için ilk özellik bir metin dosyası okumak ve konsola tüm bu metni görüntülemek için yeteneğidir. Önce bir metin dosyası ekleyelim. Bu [örnek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) için github deposundan [örnekQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) dosyasını proje dizininize kopyalayın. Bu, uygulamanız için komut dosyası görevi göreceksiniz. Bu konu yla ilgili örnek uygulamayı nasıl indireceğiniz hakkında bilgi almak istiyorsanız, [Örnekler ve Öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konusundaki talimatlara bakın.

Ardından, sınıfınızda `Program` aşağıdaki yöntemi ekleyin (yöntemin `Main` hemen altında):

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

Bu yöntem, iki yeni ad alanı nın türlerini kullanır. Bunun derlemesi için dosyanın üst bölümüne aşağıdaki iki satırı eklemeniz gerekir:

```csharp
using System.Collections.Generic;
using System.IO;
```

Arabirim <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic> ad alanında tanımlanır. Sınıf <xref:System.IO.File> <xref:System.IO> ad alanında tanımlanır.

Bu yöntem, *Bir Iterator yöntemi*olarak adlandırılan C# yönteminin özel bir türüdür. Enumerator yöntemleri tembel olarak değerlendirilen dizileri döndürer. Bu, dizideki her öğenin, sırayı tüketen kod tarafından istendiği gibi oluşturulduğu anlamına gelir. Sayısallaştırıcı yöntemler, bir veya daha fazla [`yield return`](../language-reference/keywords/yield.md) ifade içeren yöntemlerdir. `ReadFrom` Yöntem tarafından döndürülen nesne, dizideki her öğeyi oluşturmak için kodu içerir. Bu örnekte, kaynak dosyadan sonraki metin satırını okuma ve bu dizeyi döndürme içerir. Arama kodu diziden bir sonraki öğeyi her istediğinde, kod dosyadaki bir sonraki metin satırını okur ve döndürür. Dosya tamamen okunduğunda, sıra başka öğe olmadığını gösterir.

Sizin için yeni olabilecek iki C# sözdizimi öğesi daha vardır. Bu [`using`](../language-reference/keywords/using-statement.md) yöntemdeki deyim, kaynak temizlemeyi yönetir. `using` İfadede`reader`(, bu örnekte) başlan değişken <xref:System.IDisposable> arabirimi uygulamalıdır. Bu arabirim, `Dispose`kaynağın serbest bırakılması gerektiğinde çağrılması gereken tek bir yöntem tanımlar. Derleyici, yürütme deyiminin kapanış ayracına `using` ulaştığında bu çağrıyı oluşturur. Derleyici tarafından oluşturulan kod, kullanarak ifade tarafından tanımlanan bloktaki koddan bir özel durum atılsa bile kaynağın serbest bırakılmasını sağlar.

Değişken `reader` `var` anahtar kelime kullanılarak tanımlanır. [`var`](../language-reference/keywords/var.md)*örtülü olarak yazılan yerel değişkeni*tanımlar. Bu, değişkenin türü değişkene atanan nesnenin derleme zamanı türüne göre belirlenir anlamına gelir. Burada, bir <xref:System.IO.StreamReader> nesne olan <xref:System.IO.File.OpenText(System.String)> yöntemin iade değeridir.

Şimdi, `Main` yöntemde dosyayı okumak için kodu dolduralım:

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

Programı çalıştırın `dotnet run`(kullanarak) ve konsola yazdırılan her satırı görebilirsiniz.

## <a name="adding-delays-and-formatting-output"></a>Gecikmeler ekleme ve çıktıyı biçimlendirme

Sahip olduğunuz şey yüksek sesle okunamayacak kadar hızlı görüntüleniyor. Şimdi çıkışgecikmeler eklemeniz gerekir. Başladığınızda, eşzamanlı işleme sağlayan bazı çekirdek kodu oluşturuyor olacaksınız. Ancak, bu ilk adımlar birkaç anti-desenler ilerler. Kodu eklerken anti-desenler yorumlarda işaret edilir ve kod sonraki adımlarda güncelleştirilir.

Bu bölümün iki adımı vardır. İlk olarak, tüm satırlarıyerine tek sözcük döndürmek için yineleyici yöntemini güncelleştirebilirsiniz. Bu modifikasyonlarla yapıldı. İfadeyi `yield return line;` aşağıdaki kodla değiştirin:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Ardından, dosyanın satırlarını nasıl tükettiğinizi değiştirmeniz ve her sözcüğü yazdıktan sonra gecikme eklemeniz gerekir. Yöntemdeki `Console.WriteLine(line)` `Main` deyimi aşağıdaki blokla değiştirin:

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

Sınıf <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks> ad alanındaolduğundan, bu `using` ifadeyi dosyanın en üstüne eklemeniz gerekir:

```csharp
using System.Threading.Tasks;
```

Örneği çalıştırın ve çıktıyı kontrol edin. Şimdi, her bir kelime yazdırılır, ardından 200 ms gecikme. Ancak, kaynak metin dosyasında satır sonu olmayan 80'den fazla karaktere sahip birkaç satır olduğundan, görüntülenen çıktı bazı sorunları gösterir. Kaydırma yaparken bunu okumak zor olabilir. Bunu düzeltmek kolay. Yalnızca her satırın uzunluğunu izleyecek ve satır uzunluğu belirli bir eşiğe ulaştığında yeni bir satır oluşturacaksınız. Satır uzunluğunu tutan `words` `ReadFrom` yöntemde beyanı sonra yerel bir değişken bildirin:

```csharp
var lineLength = 0;
```

Ardından, deyimden `yield return word + " ";` sonra (kapanış ayracından önce) aşağıdaki kodu ekleyin:

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

Örneği çalıştırın ve önceden yapılandırılmış hızında yüksek sesle okuyabilirsiniz.

## <a name="async-tasks"></a>Async Görevleri

Bu son adımda, çıktıyı eşit bir şekilde bir göreve yazmak için kodu eklersiniz, aynı zamanda metin ekranını hızlandırmak veya yavaşlatmak veya metin görüntülemeyi tamamen durdurmak istiyorlarsa kullanıcıdan gelen girişi okumak için başka bir görev çalıştırın. Bu birkaç adım vardır ve sonunda, ihtiyacınız olan tüm güncelleştirmeleri olacak. İlk adım, dosyayı okumak ve <xref:System.Threading.Tasks.Task> görüntülemek için şimdiye kadar oluşturduğunuz kodu temsil eden eşzamanlı bir döndürme yöntemi oluşturmaktır.

Bu yöntemi sınıfınıza `Program` ekleyin (yönteminizin `Main` gövdesinden alınır):

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

İki değişiklik fark edeceksiniz. İlk olarak, yöntemin gövdesinde, <xref:System.Threading.Tasks.Task.Wait> eşzamanlı olarak bir görevin tamamlanmasını beklemek için `await` arama yapmak yerine, bu sürüm anahtar sözcüğü kullanır. Bunu yapmak için, yöntem imzasına `async` değiştirici eklemeniz gerekir. Bu yöntem `Task`bir . Bir `Task` nesneyi döndüren iade ifadeleri olmadığına dikkat edin. Bunun yerine, bu `Task` `await` nesne, işleci kullandığınızda derleyicinin oluşturduğu kod la oluşturulur. Bu yöntemin bir `await`. Döndürülen `Task` çalışma tamamlanmadı gösterir. Beklenen görev tamamlandığında yöntem devam eder. Tamamlanmak üzere yürütüldüğünde, `Task` döndürülen tamamlanmış olduğunu gösterir.
Arama kodu, ne `Task` zaman tamamlandığını belirlemek için döndürülenleri izleyebilir.

Bu yeni yöntemi yönteminizde `Main` arayabilirsiniz:

```csharp
ShowTeleprompter().Wait();
```

Burada, `Main`içinde , kod eşzamanlı olarak bekler. Mümkün olduğunda `await` eşzamanlı olarak beklemek yerine işleci kullanmalısınız. Ancak, bir konsol uygulamasının `Main` `await` yönteminde, işleci kullanamazsınız. Bu, tüm görevler tamamlanmadan uygulamanın çıkmasına neden olur.

> [!NOTE]
> C# 7.1 veya daha yeni kullanırsanız, [ `async` `Main` yöntemle](../whats-new/csharp-7-1.md#async-main)konsol uygulamaları oluşturabilirsiniz.

Daha sonra, Konsol'dan okumak ve '<' (daha az), '>' (büyüktür) ve 'X' veya 'x' tuşlarını izlemek için ikinci eşzamanlı yöntemi yazmanız gerekir. Bu görev için eklediğiniz yöntem şunlardır:

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

Bu, Konsol'dan bir anahtarı <xref:System.Action> okuyan bir temsilciyi temsil eden bir lambda ifadesi oluşturur ve kullanıcı '<' (daha az) veya '>' (büyüktür) tuşlarına bastığında gecikmeyi temsil eden yerel bir değişkeni değiştirir. Temsilci yöntemi, kullanıcının metin ekranını istediği zaman durdurmasına olanak tanıyan 'X' veya 'x' tuşlarına bastığında sona eler. Bu yöntem, kullanıcının bir tuşa basmasını engellemek ve beklemek için kullanır. <xref:System.Console.ReadKey>

Bu özelliği tamamlamak için, bu `async Task` görevlerin her ikisini de başlatan`GetInput` `ShowTeleprompter`(ve) ve bu iki görev arasındaki paylaşılan verileri yöneten yeni bir dönen yöntem oluşturmanız gerekir.

Bu iki görev arasında paylaşılan verileri işleyebilir bir sınıf oluşturma nın zamanı. Bu sınıf iki ortak özellik içerir: `Done` gecikme ve dosyanın tamamen okunduğunu gösteren bir bayrak:

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

Bu sınıfı yeni bir dosyaya koyun ve `TeleprompterConsole` bu sınıfı yukarıda gösterildiği gibi ad alanına bürün. Ayrıca, ekleyen sınıf `using static` veya ad alanı adları `Min` `Max` olmadan ve yöntemlere başvuru yapabilmeniz için bir deyim eklemeniz gerekir. Bir [`using static`](../language-reference/keywords/using-static.md) deyim yöntemleri bir sınıftan içeri yedirer. Bu, bu noktaya `using` kadar kullanılan ve tüm sınıfları bir ad alanından alan ifadelerle zıttır.

```csharp
using static System.Math;
```

Ardından, yeni `ShowTeleprompter` `config` nesneyi `GetInput` kullanmak için yöntemleri ve yöntemleri güncelleştirmeniz gerekir. Her iki `Task` görevi `async` başlatmak ve ilk görev tamamlandığında çıkmak için son bir dönen yöntem yazın:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Burada yeni bir yöntem <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağrıdır. Bu, bağımsız `Task` değişken listesindeki görevlerden herhangi biri tamamlanır tamamlanmaz sona erdirilen bir sonuç oluşturur.

Ardından, gecikme için `ShowTeleprompter` `GetInput` `config` nesneyi kullanmak için hem yöntemleri hem de yöntemleri güncelleştirmeniz gerekir:

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

Bu yeni `ShowTeleprompter` sürüm `TeleprompterConfig` sınıfta yeni bir yöntem çağırır. Şimdi, yerine aramak `Main` `RunTeleprompter` için güncelleştirmeniz `ShowTeleprompter`gerekir:

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a>Sonuç

Bu öğretici, C# dili ve Konsol uygulamalarında çalışmakla ilgili .NET Core kitaplıkları ile ilgili bir dizi özelliği size göstermiştir. Dil ve burada tanıtılan sınıflar hakkında daha fazla bilgi keşfetmek için bu bilgiyi üzerine inşa edebilirsiniz. Dosya ve Console G/Ç'nin temellerini, Görev tabanlı eşzamanlı programlamanın kullanımını engellemeyi ve engellemeyenleri, C# dilini ve C# programlarının nasıl düzenlendiğini ve .NET Core CLI'yi gördünüz.

Dosya G/Ç hakkında daha fazla bilgi için [Dosya ve Akış G/Ç](../../standard/io/index.md) konusuna bakın. Bu eğitimde kullanılan eşzamanlı programlama modeli hakkında daha fazla bilgi için [Görev tabanlı Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) konusuna ve [Asynchronous programlama](../async.md) konusuna bakın.
