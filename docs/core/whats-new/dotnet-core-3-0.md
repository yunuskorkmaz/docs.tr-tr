---
title: .NET Core 3. 0'yenilikler nelerdir?
description: .NET Core 3. 0 ' bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 26fb7cb25b9bf7f00f87059fbe1848763f7f175d
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415552"
---
# <a name="whats-new-in-net-core-30-preview-1"></a>.NET Core 3.0 (Önizleme 1) yenilikler

Bu makalede, .NET Core 3.0 (Önizleme 1) Yenilikler açıklanır. Büyük iyileştirmeler Windows Masaüstü uygulamaları (yalnızca Windows) için destek biridir. Windows Masaüstü adlı bir .NET Core 3.0 bileşen yararlanarak uygulamalarınızı Windows Formları Windows Presentation Foundation (WPF) bağlantı noktası. Gerekirse Windows Masaüstü bileşeni yalnızca Windows üzerinde desteklenir. Daha fazla bilgi için konudaki [Windows Masaüstü](#windows-desktop) aşağıda.

.NET core 3.0 için destek ekler C# 8.0.

[İndirin ve .NET Core 3 Önizleme 1 ile çalışmaya başlama](https://aka.ms/netcore3download) şu anda Windows, Mac ve Linux üzerinde. Yayın içinde tüm ayrıntılarını görebilirsiniz [.NET Core 3 Önizleme 1 sürüm notları](https://aka.ms/netcore3releasenotes).

Daha fazla bilgi için [.NET Core 3.0 Önizleme 1 Duyurusu](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).

## <a name="net-standard-21"></a>.NET standard 2.1

.NET core 3.0 .NET standart 2.1 uygular.

## <a name="default-executables"></a>Varsayılan yürütülebilir dosyalar

.NET core artık derler [framework bağımlı yürütülebilir dosyaları](../deploying/index.md#framework-dependent-executables-fde) varsayılan olarak. .NET Core genel olarak yüklenmiş bir sürümünü kullanan uygulamalar için yeni bir özelliktir. Şimdiye kadar yalnızca [müstakil dağıtımları](../deploying/index.md#self-contained-deployments-scd) yürütülebilir bir dosya oluşturur.

Sırasında `dotnet build` veya `dotnet publish`, kullanmakta olduğunuz SDK platform ve ortam ile eşleşen sağlanan yürütülebilir bir dosya oluşturulur. Diğer yerel yürütülebilir dosyalar gibi olduğu gibi bu yürütülebilir dosyaları ile aynı şey geçerli olacaktır:

* Yürütülebilir dosya üzerine çift tıklayabilirsiniz.
* Doğrudan bir komut isteminden uygulama başlatma gibi `myapp.exe` Windows, şirket ve `./myapp` Linux ve Macos'ta.

## <a name="build-copies-dependencies"></a>Derleme bağımlılıkları kopyalar.

`dotnet build` artık uygulamanız için NuGet bağımlılıklarını NuGet önbellekten yapı çıktı klasörüne kopyalar. Daha önce bağımlılıkları parçası olarak yalnızca kopyalanan `dotnet publish`. 

Yayımlama, yayınlama, bağlama ve razor sayfası hala gerektirir gibi bazı işlemler vardır.


## <a name="local-dotnet-tools"></a>Yerel dotnet araçları

.NET Core 2.1 genel araçları destekleniyorsa, .NET Core 3.0 artık yerel araçlara sahiptir. Yerel Araçlar genel araçları benzerdir, ancak disk üzerindeki belirli bir konum ile ilişkilidir. Bu, proje başına ve havuz başına araçlar sağlar. Yerel olarak yüklü herhangi bir aracı genel olarak kullanılabilir değil.

Yerel Araçlar kullanan bir bildirim dosyası adına `dotnet-tools.json` geçerli dizininizde. Bu bildirim dosyası, kullanılabilir olması için Araçlar tanımlar. Bu bildirim dosyası, depo kökünde oluşturarak, herkesin kodunuzu kopyalama geri yükleyebilir ve başarıyla kodunuzla çalışmak için gereken araçları kullanmanız emin olun.

Bildirim dosyası yerel Araçlar kullanılabilir olduğunda otomatik olarak indirip yerel olarak bu araçları yüklemek için aşağıdaki komutu kullanın:

```console
dotnet tool restore
```

Yerel bir aracı ile aşağıdaki komutu çalıştırın:

```console
dotnet tool run <tool-command-name>
```

Dotnet, yerel aracı çağrıldığında, dizin yapısını bildirim arar. Bir aracı bildirim dosyası bulunduğunda, için istenen aracı aranır. Aracı tespit edilirse, aracı NuGet genel paketleri konumu bulmak için gereken bilgileri içerir. 

Aracı bildirimi, ancak önbellek bulunursa, kullanıcı hata alır. Kullanıcının çalıştırmasını istemek için Önizleme 1 ileti geliştirilecektir `dotnet tool restore`.

Bir dizine yerel araçları eklemek için ilk olarak aracı bildirim dosyası oluşturmanız gerekir. Preview 1'den sonra aracı gibi dotnet yeni bir şablon bildirim dosyalarını oluşturmak için bir mekanizma sunacağız. Preview 1'için adlı bir dosya oluşturmalısınız `dotnet-tools.json` aşağıdaki içeriklerle:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

Bildirim oluşturulduktan sonra yerel araçlarını kullanarak ekleyebilirsiniz:

```console
dotnet tool install <toolPackageId>
```

Bu komut, başka bir sürümü belirtilmediği sürece aracı en son sürümünü yükler.  En son sürüme otomatik olarak seçilmiş olsa bile, Aracı'nın sürümü geri veya çalıştırmak için aracının doğru sürümü izin vermek için aracı bildirim dosyasına yazılır.

Aracı bildirim dosyasını elle düzenlemeye – izin vermek için deposuyla çalışmak için gerekli sürümü güncelleştirmek için bunu tasarlanmıştır.

İşte bir örnek `dotnet-tools.json` dosyası:

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

Bir aracı aracı bildirim dosyasından kaldırmak için aşağıdaki komutu çalıştırın:

```console
dotnet tool uninstall <toolPackageId>
```

Hem genel hem de yerel araçları için çalışma zamanı'nın uyumlu bir sürümü gereklidir. Birçok araç NuGet.org üzerinde şu anda .NET Core çalışma zamanı 2.1 hedefleyin. Bu genel olarak veya yerel olarak yüklemek için yükleme yine [NET Core 2.1 çalışma zamanı](https://dotnet.microsoft.com/download/dotnet-core/2.1).

Daha fazla bilgi için [yerel Araçlar erken Önizleme belgeleri](https://github.com/dotnet/cli/issues/10288).

## <a name="windows-desktop"></a>Windows masaüstü

.NET Core 3.0 Önizleme 1'den başlayarak, WPF ve Windows Forms kullanılarak Windows Masaüstü uygulamaları oluşturabilirsiniz. Bu çerçeveler ile modern denetimleri ve Windows kullanıcı Arabirimi XAML kitaplığından (WinUI) Fluent stil kullanarak da destekler [XAML Adaları](/windows/uwp/xaml-platform/xaml-host-controls).

Windows Masaüstü bileşen Windows parçasıdır .NET Core 3.0 SDK.

Şunlarla birlikte yeni bir Windows Forms ve WPF uygulaması oluşturabilirsiniz `dotnet` komutları:

```console
dotnet new wpf
dotnet new winforms
```

Açmak, başlatmak ve .NET Core 3.0 WPF ve Windows Forms projeleri Visual Studio 2019 Önizleme 1 hata ayıklama. Visual Studio 2017 15.9 içinde bu projeleri açmak şu anda mümkündür, ancak bu desteklenen bir senaryo değildir (ve gerekiyorsa [önizlemelerini etkinleştir](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).

Yeni Proje birkaç eklemelerle mevcut .NET Core projeleri ile aynıdır. Temel .NET Core konsol projesi ve temel bir Windows Forms ve WPF projesi bir karşılaştırması aşağıdadır.

Bir .NET Core konsol projesi kullandığından `Microsoft.NET.Sdk` SDK ve .NET Core 3.0 üzerinden üzerinde bir bağımlılık bildirir `netcoreapp3.0` hedef çerçeve. Bir Windows masaüstü uygulaması oluşturmak için kullanın `Microsoft.NET.Sdk.WindowsDesktop` SDK ve kullanmak için hangi UI çerçevesi seçin:

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

Windows Forms, WPF seçmek için ayarlanmış `UseWindowsForms` yerine `UseWPF`:

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

Her ikisi de `UseWPF` ve `UseWindowsForms` ayarlanabilir `true` uygulama için bir Windows Forms iletişim kutusu, bir WPF denetimi barındırmayla örnek her iki çerçeveleri kullanıyorsa.

Geri bildiriminizi Lütfen paylaşım [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) ve [dotnet/core](https://github.com/dotnet/core/issues) depolar.

## <a name="fast-built-in-json-support"></a>Hızlı yerleşik JSON desteği

`System.Text.Json.Utf8JsonReader` yüksek performanslı, düşük ayırma, yalnızca iletme Okuyucu için UTF-8 kodlamalı JSON metin okuma, bir `ReadOnlySpan<byte>`. `Utf8JsonReader` Özel çözümleyiciler ve deserializers oluşturmak için kullanılan bir temel, alt düzey, türüdür. Kullanarak yeni bir JSON yükü okuma `Utf8JsonReader` reader'ı kullanarak daha hızlı bir şekilde x 2 [Json.NET](https://www.newtonsoft.com/json). JSON belirteçleri (UTF-16) dizeler olarak actualize gerekene kadar bırakmaz.

Bu yeni API'yi aşağıdaki bileşenleri içerir:

* Önizleme 1'de: JSON Okuyucu (sıralı erişim)
* Sonraki yakında: JSON yazıcısı, DOM (rastgele erişim) poco serileştirici poco seri durumdan çıkarıcının

Temel bir okuyucu döngü için işte `Utf8JsonReader` başlangıç noktası olarak kullanılabilir:

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

.NET ekosisteminin yararlandı [Json.NET](https://www.newtonsoft.com/json) ve iyi seçenekleri olmaya devam diğer popüler JSON kitaplıkları. JSON.NET UTF-16 başlık altında olan kendi taban datatype .NET dizeleri kullanır. 

.NET Core 2.1 ve 3.0, JSON API yazmayı mümkün kılan yeni API ekledik (gibi `Utf8JsonReader`) kullanarak bağlı olarak, daha az bellek gerektiren `Span<T>` ve UTF-8 dizeleri ve hizmet Kestrel, ASP gibi yüksek performanslı uygulamaları ihtiyaçlarını daha iyi. NET Core web sunucusu.

## <a name="ranges-and-indices"></a>Aralıkları ve dizinler

Yeni `Index` türü, dizin oluşturma işlemi için kullanılabilir. Birinden oluşturabileceğiniz bir `int` baştan ya da öneki sayar `^` işleci (C#) sonundan sayar:

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

Ayrıca bir `Range` oluşan iki tür `Index` bir başlangıç ve bitiş için bir değer ve ile yazılmış bir `x..y` aralık ifade (C#). Ardından ile dizinleyebilirsiniz bir `Range` dilim oluşturmak için:

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> Yalnızca [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) sözdizimini destekler `Range` ve `Index`.

## <a name="async-streams"></a>Zaman uyumsuz akışlar

`IAsyncEnumerable<T>` Türüdür, yeni bir zaman uyumsuz sürümü `IEnumerable<T>`. Dil sağlar `await foreach` üzerinden bu öğeleri, kullanma ve `yield return` öğeleri oluşturmak için onlara.

Aşağıdaki örnek, hem üretim hem de zaman uyumsuz akışlar kullanımını gösterir. `foreach` Deyimi, async ve kendisini kullanan `yield return` arayanlar için zaman uyumsuz bir akış oluşturmak için. Bu düzen (kullanarak `yield return`) zaman uyumsuz akışlar oluşturmayı için önerilen modelidir.

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> Şu anda sahip bir hata ile .NET core 3.0 Önizleme 1 `await foreach`. Bunun yerine, `GetEnumerator` ve `MoveNext` işlem öğeleri. Daha fazla bilgi için [roslyn / #31268](https://github.com/dotnet/roslyn/issues/31268).

İmkanına yanı sıra `await foreach`, zaman uyumsuz yineleyiciler, örneğin, döndüren bir yineleyicinin oluşturabilirsiniz bir `IAsyncEnumerable/IAsyncEnumerator` her ikisini yapabilirsiniz `await` ve `yield` içinde. Çıkarılması gereken nesneler için kullanabileceğiniz `IAsyncDisposable`, çeşitli BCL türleri uygulayan, gibi `Stream` ve `Timer`.

> [!NOTE]
> Yalnızca [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) destekler `await foreach` söz dizimi.

## <a name="type-sequencereader"></a>Tür: SequenceReader

.NET Core 3. 0'da, `System.Buffers.SequenceReader` Okuyucu için olarak kullanılabilecek eklendi `ReadOnlySequence<T>`. Hızlı, yüksek performanslı, böylece düşük ayırma çözümlenmesi `System.IO.Pipelines` birden çok yedekleme arabellekler çapraz veri. 

Aşağıdaki örnek bir girişi sonu `Sequence` geçerli içine `CR/LF` satırları ayrılmış:

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a>Tür: MetadataLoadContext

`MetadataLoadContext` Türü okuma derleme sağlayan eklenmiş yapanın uygulama etki alanı etkilemeden meta verileri. Derlemeleri farklı mimariler ve geçerli çalışma zamanı ortamı daha platformlar için oluşturulmuş derlemeler de dahil olmak üzere veriler olarak okunur. `MetadataLoadContext` ile çakışıyor <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, hangi, yalnızca .NET Framework içinde kullanılabilir.

`MetdataLoadContext` kullanılabilir [System.Reflection.MetadataLoadContext paket](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext). .NET Standard 2.0 bir pakettir.

`MetadataLoadContext` Benzer olan API'leri gösterir <xref:System.Runtime.Loader.AssemblyLoadContext> yazın, ancak bu türüne göre değil. Benzer şekilde <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` evreni yükleniyor yalıtılmış bir derlemenin içinden yükleme derlemelerini etkinleştirir. `MetdataLoadContext` API'leri dönüş <xref:System.Reflection.Assembly> bilinen yansıma API'leri kullanımını etkinleştirme nesneleri. Yürütme API'leri gibi odaklı [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), izin verilmeyen ve InvalidOperationException oluşturur.

Aşağıdaki örnek, belirli bir arabirimi uygulayan bir derlemede somut tür bulmak gösterilmektedir:

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

Senaryolar için `MetadataLoadContext` tasarım zamanı özellikleri, araçları, derleme zamanı ve çalışma zamanı açık'li veri olarak bir derleme kümesi inceleyin ve tüm dosya kilitleri olması gereken özellikleri ve İnceleme sonra serbest bırakılan bellek gerçekleştirilir.

`MetadataLoadContext` Çözümleyici sınıfı geçirilen yapıcısına sahiptir. Çözümleyici'nin iş yüklenmesidir bir `Assembly` verilen kendi `AssemblyName`. Özet çözümleyici sınıfı türetilen `MetadataAssemblyResolver` sınıfı. Yol tabanlı senaryoları için çözümleyici uygulaması ile sağlanan `PathAssemblyResolver`.

[MetadataLoadContext testleri](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) birçok kullanım durumları gösterir. [Derleme testleri](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) başlatmak için iyi bir yerdir.

## <a name="tls-13--openssl-111-on-linux"></a>TLS 1.3 & Linux'ta OpenSSL 1.1.1

.NET core artık avantajlarından yararlanın [OpenSSL 1.1.1 TLS 1.3 desteği](https://www.openssl.org/blog/blog/2018/09/11/release111/), verilen ortamda kullanılabilir olduğunda. Her TLS 1,3 birden çok avantaj vardır [OpenSSL takım](https://www.openssl.org/blog/blog/2018/09/11/release111/):

* Geliştirilmiş bağlantı süreleri nedeniyle bir azalma istemci ve sunucu arasında gerekli gidiş dönüş sayısı.

* Geliştirilmiş güvenlik çeşitli eski ve güvenli şifreleme algoritmaları kaldırılmasını ve daha fazla bağlantı el sıkışması şifrelenmesi nedeniyle.

.NET core 3.0 Önizleme 1 yararlanarak özellikli **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, veya **OpenSSL 1.0.2** (ne olursa olsun bulunan en iyi, bir Linux sisteminde sürümüdür).  Zaman **OpenSSL 1.1.1** olduğu SslStream ve HttpClient türleri kullanılabilir kullanacağı **TLS 1.3** kullanırken `SslProtocols.None` (sistem varsayılan protokol), istemci ve sunucu desteği varsayılarak**TLS 1.3**.

.NET Core 3.0 Önizleme 1 Ubuntu 18.10 bağlanmak için aşağıdaki örnekte gösterilmiştir <https://www.cloudflare.com>:

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
>Windows ve macOS henüz desteklemediği **TLS 1.3**. .NET core 3.0 destekleyeceği **TLS 1.3** desteği kullanılabilir olduğunda bu işletim sistemlerinde.

## <a name="cryptography"></a>Şifreleme

İçin destek eklenmiştir **AES GCM** ve **AES-CCM** aracılığıyla uygulanan şifrelemeleri, `System.Security.Cryptography.AesGcm` ve `System.Security.Cryptography.AesCcm`. Her ikisi de bu algoritmalar olan [ilişkilendirme veri (AEAD) algoritmaları ile kimliği doğrulanmış şifreleme](https://en.wikipedia.org/wiki/Authenticated_encryption)ve .NET Core için eklenen ilk kimliği doğrulanmış şifreleme (AE) algoritmaları.

Aşağıdaki kodu **AesGcm** şifrelemek ve rastgele verilerin şifresini çözmek için şifre.

Kodu **AesCcm** (sınıf değişken adları farklı olacaktır yalnızca) neredeyse aynı görünür.

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a>Şifreleme anahtarı içeri/dışarı aktarma

.NET core 3.0 Önizleme 1 içeri ve dışarı aktarmayı asimetrik ortak ve özel anahtarlar standart biçimlerinden bir X.509 sertifikası kullanmak zorunda kalmadan destekler.

Tüm anahtar türleri (RSA, DSA, ECDsa, ECDiffieHellman) desteği **X.509 SubjectPublicKeyInfo** biçimi için ortak anahtarları ve **PKCS #8 PrivateKeyInfo** ve **PKCS #8 EncryptedPrivateKeyInfo**  biçimleri özel anahtarlar için. RSA ayrıca destekler **PKCS #1 RSAPublicKey** ve **PKCS #1 RSAPrivateKey**. Tüm verme yöntemleri DER ile kodlanmış ikili verileri oluşturmak ve içeri aktarma metotları aynı beklerler. Bir anahtar metin dostu PEM biçiminde depolanır, çağırana base64 gerekir-içerik alma yöntemini çağırmadan önce kod çözme.

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

PKCS #8 dosya inceledi ile `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` sınıfı.

PFX/PKCS #12 dosyaları inceledi ve ile yönetilebilir `System.Security.Cryptography.Pkcs.Pkcs12Info` ve `System.Security.Cryptography.Pkcs.Pkcs12Builder`sırasıyla.

## <a name="serialport-for-linux"></a>Linux için çevirmek için SerialPort

.NET core 3.0 destekler <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux üzerinde.

Daha önce yalnızca kullanarak desteklenen .NET Core `SerialPort` Windows türü.

## <a name="more-bcl-improvements"></a>Daha fazla BCL geliştirmeleri

`Span<T>`, `Memory<T>`, Ve .NET Core 2.1 içinde tanıtılan ilgili türleri de .NET Core 3.0 için iyileştirilmiş. Sık kullanılan işlemler gibi yapı span, dilimleme, ayrıştırma ve biçimlendirme artık daha iyi gerçekleştirin. 

Ayrıca, türleri ister `String` anahtarlarla olarak kullanıldığında daha verimli hale getirmek için altında--kapak geliştirmeleri gördünüz `Dictionary<TKey, TValue>` ve diğer koleksiyonları. Kod değişikliği olmadan bu iyileştirmeleri yararlanmak için gereklidir.

Aşağıdaki geliştirmeler de .NET Core 3 Önizleme 1'de yenidir:

* HttpClient için yerleşik Brotli desteği
* ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)
* Unsafe.Unbox
* CancellationToken.Unregister
* Karmaşık aritmetik işleçler
* TCP için yuva API'leri Canlı
* StringBuilder.GetChunks
* Ayrıştırma IPEndPoint
* RandomNumberGenerator.GetInt32

## <a name="tiered-compilation"></a>Katmanlı derleme

[Katmanlı derleme](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) .NET Core 3.0 ile varsayılan olarak açıktır. Daha fazla Desenlerinizi başlangıçta hem de daha iyi performans almak ve aktarım hızını en üst düzeye çıkarmak için tam zamanında (JIT) derleyici kullanmak çalışma zamanı sağlayan bir özelliktir.

Bu özellik bir Tercihli özellik olarak eklenmiştir [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) ve varsayılan olarak etkinleştirildi [.NET Core 2.2 Önizleme 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/). Daha sonra yeniden oturum .NET Core 2.2 sürüm geri çevirmek için döndürüldü.

## <a name="arm64-linux-support"></a>ARM64 Linux desteği

ARM64 Linux bu yayın için destek ekliyoruz. Bağlam için .NET Core 2.1 ile Linux ve Windows ile .NET Core 2.2 ARM32 için destek ekledik. ARM64 için birincil kullanım durumu şu anda IOT senaryoları ile aşamasındadır.

Alpine, Debian ve Ubuntu [ARM64 için .NET Core için Docker görüntüleri kullanılabilir](https://hub.docker.com/r/microsoft/dotnet/).

Lütfen denetleyin [.NET Core ARM64 durumu](https://github.com/dotnet/announcements/issues/82) daha fazla bilgi için.

>[!NOTE]
> **ARM64** Windows Destek işlemi henüz kullanılamıyor.
