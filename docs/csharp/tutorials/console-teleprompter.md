---
title: "Konsol Uygulaması"
description: "Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 08dab8e7b210ab5159645563cd381d50145d764b
ms.sourcegitcommit: be7862cac09066bc505586cbf071d0e2c8fb1508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2017
---
# <a name="console-application"></a>Konsol Uygulaması

## <a name="introduction"></a>Giriş
Bu öğretici bir dizi özellik .NET Core ve C# dili öğretir. Şunları öğreneceksiniz:
*   .NET Core komut satırı arabirimi (CLI) Temelleri
*   Bir C# konsol uygulaması yapısı
*   Konsol g/ç
*   Dosya g/ç API'leri .NET Core temelleri
*   Görev zaman uyumsuz programlama modeli .NET Core temelleri

Bir metin dosyasını okur ve konsola, metin dosyasının içeriğini görüntülemektedir bir uygulama oluşturmak. Konsola çıktı sesli okuma eşleşecek şekilde hızını belirleyebileceği. Hızlandırma ya da hızınıza tuşlarına basarak yavaş ' <' veya ' >' anahtarları.

Bu öğreticide birçok özellik vardır. Şimdi bunları tek tek oluşturun. 
## <a name="prerequisites"></a>Önkoşullar
.NET core çalışmasına, makine Kurulum gerekir. Yükleme yönergelerini bulabilirsiniz [.NET Core](https://www.microsoft.com/net/core) sayfası. Bu uygulama, Windows, Linux, macOS veya Docker kapsayıcısı çalıştırabilirsiniz. Sık kullanılan Kod Düzenleyicisi'ni yüklemeniz gerekir. 
## <a name="create-the-application"></a>Uygulama oluşturma
İlk adım, yeni bir uygulama oluşturmaktır. Bir komut istemi açın ve uygulamanız için yeni bir dizin oluşturun. Geçerli dizin oluşturun. Komut türü `dotnet new console` komut isteminde. Bu, temel bir "Hello World" uygulaması için başlangıç dosyaları oluşturur.

Değişiklik yapmaya başlamadan önce basit Hello World uygulamasını çalıştırmak için adımlara edelim. Uygulamayı oluşturduktan sonra yazın `dotnet restore` ([bkz. Not](#dotnet-restore-note)) komut isteminde. Bu komut, NuGet paket geri yükleme işlemi çalıştırır. NuGet, bir .NET paketi yöneticisidir. Bu komut, projeniz için eksik bağımlılıklar hiçbirini indirir. Yeni bir proje olarak ilk çalıştırmada .NET Core framework yükleyecek şekilde bağımlılıkları yerinde yok. Bu ilk adımı tamamlandıktan sonra yalnızca çalıştırmanız gerekir `dotnet restore` ([bkz. Not](#dotnet-restore-note)) yeni bağımlı paketler eklediğinizde, veya bağımlılıklarınızı hiçbirini sürümlerini güncelleştirin. Bu işlem ayrıca proje dizininde proje kilit dosyası (böylece project.lock.json) oluşturur. Bu dosya, proje bağımlılıklarını yönetmek için yardımcı olur. Tüm proje bağımlılıkları yerel konumunu içerir. Dosyanın kaynak denetiminde put gerekmez; çalıştırdığınızda oluşturulmayacak `dotnet restore` ([bkz. Not](#dotnet-restore-note)). 

Paketler geri yükledikten sonra çalıştırmanız `dotnet build`. Bu yapı altyapısı yürütür ve uygulamanızın yürütülebilir oluşturur. Son olarak, yürütme `dotnet run` uygulamanızı çalıştırmak için.  

Basit Hello World uygulama tüm Program.cs içinde kodudur. Bu dosya, sık kullandığınız metin düzenleyicisiyle açın. İlk değişikliklerimizi yapmak üzere çalışıyoruz.
Kullanarak bir dosyanın üst kısmında, bkz: deyimi:

```csharp
using System;
```

Bu deyim herhangi yazdığı gelen derleyici söyler `System` ad alanı olan kapsam içinde. Kullanmış diğer nesne yönelimli diller gibi C# ad alanları türleri düzenlemek için kullanır. Bu hello world programı farklı değildir. Program içindeki başvurudur görebilirsiniz `ConsoleApplication` ad alanı. Bu çok açıklayıcı bir ad değil, bu nedenle şekilde değiştirin `TeleprompterConsole`:

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a>Okuma ve dosyayı Yankı
Metin dosyası okuma ve tüm metni konsola görüntüleme olanağı eklemek için ilk özelliğidir. İlk olarak, bir metin dosyası ekleyelim. Kopya [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) GitHub deposuna bir dosyadan bu [örnek](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter) proje dizinine. Bu, uygulamanız için komut dosyası olarak hizmet verecektir. Bu konu için örnek uygulama indirme hakkında bilgi edinmek istiyorsanız deki yönergelere bakın [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) konu.

Ardından, programı sınıfınıza aşağıdaki yöntemi ekleyin (hemen altında `Main` yöntemi):

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

Bu yöntem, iki yeni ad alanı türlerinden kullanır. Bu, derlemek aşağıdaki iki satırı dosyanın en üstüne ekleyin yapmanız gerekir:

```csharp
using System.Collections.Generic;
using System.IO;
```

`IEnumerable<T>` Arabirimi tanımlanmış `System.Collections.Generic` ad alanı. <xref:System.IO.File> Sınıfı tanımlanmış `System.IO` ad alanı.

Bu yöntem çağrılır C# yöntemi özel türünde bir *Numaralandırıcı yöntemi*. Numaralandırıcı yöntemleri gevşek değerlendirilir dizilerini döndürür. Dizideki her öğe dizisi kullanan kodu tarafından istenen şekilde oluşturulan anlamına gelir. Numaralandırıcı yöntemlerden birini veya daha fazlasını içeren yöntemlerdir `yield return` deyimleri. Tarafından döndürülen nesne `ReadFrom` yöntemi dizideki her öğe oluşturmak için kodunu içerir. Bu örnekte, metnin sonraki satırı kaynak dosyadan okunuyor ve bu dizeyi döndürme içerir. Çağıran kodun sonraki öğe dizisinden istekleri her zaman kodu metnin sonraki satırı dosyadan okur ve döndürür. Dosyayı tamamen okuma, daha fazla öğe yok dizisini gösterir.

Size yeni olabilecek iki C# sözdizimi öğe vardır. `using` Bu yöntem deyiminde kaynak temizleme yönetir. İçinde başlatılan değişkeni `using` deyimi (`reader`, bu örnekte) uygulamalıdır `IDisposable` arabirimi. <xref:System.IDisposable> Arabirimi tanımlar tek bir yöntem `Dispose`, çağrılabilir kaynak yayımlandığı zaman. Yürütme kapanış ayracı ulaştığında derleyici bu çağrı üretir `using` deyimi. Derleyici tarafından üretilen kod kullanılarak tanımlanmış bloğundaki koddan bir özel durum olsa bile, kaynak yayımlanan sağlar deyimi.

`reader` Değişkeni kullanılarak tanımlanmış `var` anahtar sözcüğü. `var`tanımlayan bir *türü örtük olarak belirlenmiş yerel değişken*. Değişken türü, derleme zamanı tür değişkenine atanan nesnesinin tarafından belirlenir anlamına gelir. Dönüş değeri Buraya, <xref:System.IO.File.OpenText(System.String)> olan yöntemini bir <xref:System.IO.StreamReader> nesnesi.
 
Şimdi, şimdi dosyayı okumak için kod doldurun `Main` yöntemi: 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

Program çalıştır (kullanarak `dotnet run` ve konsola yazdırılır her satırı görebilirsiniz).  

## <a name="adding-delays-and-formatting-output"></a>Gecikme ekleme ve çıktı biçimlendirmesi
Sahip olduğunuz ne kadar çok hızlı sesli okumak için görüntülenmektedir. Şimdi çıktıda gecikmeleri eklemeniz gerekir. Başladığınızda, zaman uyumsuz işleme sağlayan çekirdek kodu bazılarını oluşturmakta. Ancak, ilk adımları birkaç koruma desenlerini izleyin. Koruma desenleri açıklamaları kodu ekleyin ve daha sonraki adımlarda kod güncelleştirilecek işaret.

Bu bölüm için iki adım vardır. İlk olarak, tüm satırlar yerine tek tek sözcükleri döndürmek için yineleyici yöntemini güncelleştirin. Bu değişiklikler ile gerçekleştirilir. Değiştir `yield return line;` deyimi aşağıdaki kod ile:

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

Ardından, nasıl satırlık bir dosyayı kullanmak ve her sözcüğün yazdıktan sonra bir gecikme ekleme değiştirmeniz gerekir. Değiştir `Console.WriteLine(line)` deyiminde `Main` yöntemi aşağıdaki bloğu ile:

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

`Task` Sınıfı olan `System.Threading.Tasks` eklemek gereken şekilde ad alanı, `using` deyimini dosyanın üst kısmındaki:

```csharp
using System.Threading.Tasks;
```

Örneği çalıştırmak ve çıktısını denetleyin. Şimdi, her tek sözcüklük bir 200 ms gecikmeyle tarafından izlenen yazdırılır. Ancak, kaynak metin dosyası 80 karakterden fazla satır sonu olmadan sahip birden fazla satır içerdiğinden görüntülenen çıktının bazı sorunları gösterir. Tarafından kaydırma sırasında okunması zor olabilir. Düzeltmek kolay olmasıdır. Yalnızca her bir satır uzunluğu izlemek ve satır uzunluğu belirli bir eşiği eriştiğinde yeni bir satır oluşturmak. Bir yerel değişken bildirimi sonra bildirip `words` satır uzunluğu tutar:

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
 
Örneği çalıştırmak ve sesli önceden yapılandırılmış sırasında okuma kullanabileceksiniz hızınıza.

## <a name="async-tasks"></a>Zaman uyumsuz görevleri
Bu son adımda, zaman uyumsuz olarak çıkışını hızlandırmak veya metin görüntüle aşağı yavaş istiyorsanız aynı zamanda okumak için başka bir görev giriş kullanıcıdan çalıştırılırken bir görevde yazmak için kod ekleyeceksiniz. Bu da ve son birkaç adım sahip, gerek duyduğunuz tüm güncelleştirmeleri gerekir.
Zaman uyumsuz bir oluşturmak için ilk adımdır <xref:System.Threading.Tasks.Task> okumak ve dosyayı görüntülemek için oluşturduğunuz kadarki kodunu temsil eder yöntemi döndürüyor.

Bu yöntemine ekleyin, `Program` sınıfı (gövdesinden alınır, `Main` yöntemi):

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

İki değişiklikler fark edeceksiniz. İlk çağırmak yerine yöntemin gövdesine <xref:System.Threading.Tasks.Task.Wait> eşzamanlı olarak bir görevi tamamlamak için beklemek için bu sürümü kullanan `await` anahtar sözcüğü. Bunu yapmak için eklemeniz gerekir `async` değiştirici yöntem imzası. Bu yöntem bir `Task`. Dönüş hiçbir return deyimlerinde olduğunu fark bir `Task` nesnesi. Bunun yerine, `Task` nesne derleyici oluşturur kullandığınızda kodla oluşturulur `await` işleci. Bu yöntem ulaştığında döndürür düşünün bir `await`. Döndürülen `Task` iş tamamlanmadı gösterir.
Awaited görev tamamlandığında yöntemi sürdürür. Ne zaman çalıştırılmadan tamamlanıncaya kadar döndürülen `Task` tam olduğunu gösterir.
Kodu çağırma izleyebilirsiniz döndürülen `Task` zaman tamamlandı belirlemek için.

Bu yeni yöntemi çağırabilirsiniz, `Main` yöntemi:

```csharp
ShowTeleprompter().Wait();
```

Burada, `Main`, kod zaman uyumlu olarak bekleyin. Kullanmanız gereken `await` zaman uyumlu olarak mümkün olduğunca beklemek yerine işleci. Ancak, bir konsol uygulamasının `Main` yöntemini kullanamaz `await` işleci. Bu, tüm görevler tamamlandığında önce uygulama çıkma içinde neden olur.

Ardından, konsoldan okunan ve izlemesi için ikinci zaman uyumsuz yöntem yazmanız gerekir ' <' ve ' >' anahtarları. Bu görev için eklediğiniz yöntemi şöyledir:

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
        } while (true);
    };
    await Task.Run(work);
}
```

Bu temsil eden bir lambda ifadesi oluşturur bir <xref:System.Action> bir anahtar konsoldan okuyan ve kullanıcı bastığında gecikmesini temsil eden bir yerel değişken değiştirir temsilci ' <' veya ' >' anahtarları. Bu yöntem <xref:System.Console.ReadKey> engellemek ve kullanıcının herhangi bir tuşa basın için bekleyin.

Bu özellik tamamlamak için yeni bir oluşturmanız gerekir `async Task` hem de bu görevleri başlatır yöntemi döndürme (`GetInput` ve `ShowTeleprompter`) ve ayrıca bu iki görevler arasında paylaşılan veri yönetir.
 
Bu iki görevler arasında paylaşılan veri işleyebilir bir sınıf oluşturmak için zaman yapılır. Bu sınıf, iki genel özellikleri içerir: gecikme süresini ve dosyanın tamamen Okunmuş belirten bir bayrak:

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

Bu sınıfın yeni bir dosyaya yerleştirin ve bu sınıfta içine `TeleprompterConsole` yukarıda gösterildiği gibi ad alanı. Ayrıca eklemeniz gerekir bir `using static` deyimi, başvurabilmek `Min` ve `Max` kapsayan sınıfı veya ad alanı adları olmadan yöntemi. A `using static` deyimi bir sınıftan yöntemleri alır. Tersine ile budur `using` bu noktaya kadar kullanılan ifadeleri, bir ad alanındaki tüm sınıfları aldınız.

```csharp
using static System.Math;
```

Yeni bir dil özelliği `lock` deyimi. Bu deyim yalnızca tek bir iş parçacığı herhangi bir zamanda bu kodu olabilir sağlar. Bir iş parçacığı kilitli bölümünde ise başka bir iş parçacığı bu bölümün çıkmak ilk iş parçacığı için beklemeniz gerekir. `lock` Deyimini kullanan bölümü kilitle korur bir nesne. Bu sınıf, özel bir nesne sınıfında kilitlemek için standart bir deyim izler.

Ardından, güncelleştirmeniz gerekir `ShowTeleprompter` ve `GetInput` yeni kullanılacak yöntemleri `config` nesnesi. Bir son yazma `Task` döndüren `async` hem görevlerini başlatmak ve ilk görev tamamlandığında çıkmak için yöntem:

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

Yeni yöntemi burada <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> çağırın. Oluşturan bir `Task` kendi bağımsız değişken listesinde görevlerden herhangi birini tamamlandıktan hemen sonra tamamlanır.

Ardından, her ikisi de güncelleştirmeniz gerekir `ShowTeleprompter` ve `GetInput` kullanılacak yöntemleri `config` nesne gecikme için:

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
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
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

Bu yeni sürümü `ShowTeleprompter` yeni bir yöntem çağrıları `TeleprompterConfig` sınıfı. Şimdi güncelleştirmeniz gerekir `Main` çağırmak için `RunTeleprompter` yerine `ShowTeleprompter`:

```csharp
RunTeleprompter().Wait();
```

Tamamlamak için eklemeniz gerekir `SetDone` yöntemi ve `Done` özelliğine `TelePrompterConfig` sınıfı:

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a>Sonuç
Bu öğretici, bir dizi özellik C# dili ve .NET Core kitaplıkları geçici konsol uygulamaları çalışmayla ilgili gösterdi.
Dili ve burada sunulan sınıfları hakkında daha fazla araştırmak için bu bilgilerine oluşturabilirsiniz. Dosya ve konsol g/ç temelleri görüyorsanız, zaman uyumsuz programlama modeli, C# dili turu C# programları nasıl düzenlendiği ve .NET Core komut satırı arabirimi ve araçları bağlı olarak görev engelleme ve engelleyici olmayan kullanın.
 
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]