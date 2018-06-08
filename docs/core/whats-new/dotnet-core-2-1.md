---
title: .NET Core 2.1 yenilikler nelerdir?
description: .NET Core 2.1 içinde bulunan yeni özellikler hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 241ac0195e5edcd17ac67ea7ea0fac159af97414
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826938"
---
# <a name="whats-new-in-net-core-21"></a>.NET Core 2.1 yenilikler nelerdir?

.NET core 2.1 aşağıdaki alanlarda geliştirmeler ve yeni özellikleri içerir:

- [Araçları](#tooling)
- [İleri alma](#roll-forward)
- [Dağıtım](#deployment)
- [Windows Uyumluluk Paketi](#windows-compatibility-pack)
- [JIT derleme geliştirmeleri](#jit-compiler-improvements)
- [API değişiklikleri](#api-changes)

## <a name="tooling"></a>Araçları

.NET Core 2.1 SDK (v 2.1.300), .NET Core 2.1 ile dahil araç aşağıdaki değişiklikler ve geliştirmeler içerir:

### <a name="build-performance-improvements"></a>Derleme performans geliştirmeleri

.NET Core 2.1 bir ana odağını özellikle artımlı derlemeler için derleme zamanı performans artırma. Bu performans iyileştirmeleri kullanarak her iki komut satırı derlemeleri uygulama `dotnet build` ve Visual Studio derlemelerde. Geliştirme, tek tek bazı alanlar şunlardır:

- Paket varlık çözümlemesi için tüm varlıkları yerine bir yapı tarafından kullanılan varlıklar çözümleniyor.

- Derleme referanslarını önbelleğe alma.

- Uzun süre çalışan SDK kullanımını yapı arasında tek span işlemler sunucuları `dotnet build` çağrılarını. Her zaman olan JIT derleme büyük kod bloklarını gerek ortadan `dotnet build` çalıştırılır. İşlemleri otomatik olarak aşağıdaki komutla sonlandırılabilir sunucu oluşturun:

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Yeni CLI komutları

Yalnızca bir başına proje temel kullanarak kullanılabilir araçları sayısı [ `DotnetCliToolReference` ](../tools/extensibility.md) artık kullanılabilir .NET Core SDK'ın bir parçası olarak. Bu araçlar içerir:

- `dotnet watch` belirlenen bir dizi komut yürütülmeden önce değiştirmek bir dosya bekler bir dosya sistemi İzleyicisi sağlar. Örneğin, aşağıdaki komutu otomatik olarak geçerli projenin yeniden oluşturur ve bir dosyada değiştiğinde ayrıntılı çıktı üretir:

   ```console
   dotnet watch -- --verbose build
   ```
  
   Not `--` önündeki seçeneği `--verbose` seçeneği. Doğrudan geçirilen seçenekleri sınırlandırır `dotnet watch` alt öğesi olarak geçirilen bağımsız değişken komutunu `dotnet` işlemi. Bu olmadan, `--verbose` seçeneği uygulandığı `dotnet watch` komutu, `dotnet build` komutu.
  
   Daha fazla bilgi için bkz: [dotnet Gözcü kullanarak geliştirme ASP.NET Core uygulamaları](/aspnet/core/tutorials/dotnet-watch)

- `dotnet dev-certs` oluşturur ve ASP.NET Core uygulamaları geliştirme sırasında kullanılan sertifikaları yönetir.

- `dotnet user-secrets` ASP.NET Core uygulamaları kullanıcı gizli deposunda gizli anahtarları yönetir.

- `dotnet sql-cache` Dağıtılmış önbelleğe alma işlemi için kullanılacak bir Microsoft SQL Server veritabanındaki bir tablo ve dizinler oluşturur.

- `dotnet ef` veritabanlarını yönetmek için bir araçtır <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve Entity Framework Çekirdek uygulamalarında geçişleri. Daha fazla bilgi için bkz: [EF çekirdek .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Genel araçları

.NET core 2.1 destekler *genel Araçları* --genel komut satırından kullanılabilir diğer bir deyişle, özel araçlar. Önceki sürümlerinde .NET Core, genişletilebilirlik modeli özel araçlar kullanılabilir bir proje başına temelinde yalnızca kullanılarak yapılan [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).

Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](..\tools\dotnet-tool-install.md) komutu. Örneğin:

```console
dotnet tool install -g dotnetsay
```

Bir kez yüklendikten sonra aracı adı belirterek aracını komut satırından çalıştırılabilir. Daha fazla bilgi için bkz: [.NET Core genel araçlarına genel bakış](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Aracı yönetimi ile `dotnet tool` komutu

.NET Core SDK 2.1 (v 2.1.300), tüm araçlar işlemlerini kullanmak `dotnet tool` komutu. Aşağıdaki seçenekler mevcuttur:

- [`dotnet tool install`](../tools/dotnet-tool-install.md) bir aracı yüklemek için.

- [`dotnet tool update`](../tools/dotnet-tool-update.md) etkili bir şekilde güncelleştiren bir aracı kaldırıp için.

- [`dotnet tool list`](../tools/dotnet-tool-list.md) şu anda yüklü listesinde Araçları'na gidin.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) şu anda yüklü araçlarını kaldırmak için.

## <a name="roll-forward"></a>İleri alma

En son sürüme otomatik olarak .NET Core 2. 0'ile başlayan tüm .NET Core uygulamaları ileriye *alt sürüm* bir sistemde yüklü. 

Bir uygulama ile oluşturulan .NET Core sürümü çalışma zamanında mevcut değilse .NET Core 2.0 ile başlayarak, uygulama otomatik olarak en son yüklenen karşı çalışır *alt sürüm* .NET Core. Diğer bir deyişle, .NET Core 2. 0 ile uygulamanın oluşturulmuştur ve .NET Core 2.0 konak sisteminde mevcut değil ancak .NET Core 2.1, uygulama .NET Core 2.1 ile çalışır.

> [!IMPORTANT]
> Bu İleri alma davranışını Önizleme sürümleri için geçerli değildir. Ya da ana sürümleri için geçerlidir. Örneğin, bir .NET Core 1.0 uygulaması .NET Core 2.0 veya .NET Core 2.1 ileriye olmayacaktır.

Alt sürüm toplama İleri herhangi üç yolla devre dışı bırakabilirsiniz:

- Ayarlama `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkeni 0.

- Aşağıdaki satırı runtimeconfig.json dosyasına ekleyin:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Kullanırken [.NET Core CLI araçlarını](../tools/index.md), .NET Core komutu aşağıdaki seçeneğiyle gibi içeren `run`:

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a>Dağıtım

### <a name="self-contained-application-servicing"></a>Kendi içinde bulunan uygulama hizmeti

`dotnet publish` Şimdi bir hizmet verilen çalışma zamanı sürümü müstakil uygulamalarla yayımlar. .NET Core 2.1 SDK (v 2.1.300) ile kendi içinde bulunan bir uygulama yayımladığınızda, uygulamanız bu SDK'sı tarafından bilinen en son hizmet verilen çalışma zamanı sürümü içerir. Son SDK'sını yükselttiğinizde, en son .NET çekirdeği çalışma zamanı sürümü ile yayımlama. Bu, .NET Core 1.0 çalışma zamanları ve sonraki sürümleri için geçerlidir.

NuGet.org sürümlerinde çalışma zamanı müstakil yayımlama kullanır. Hizmet verilen çalışma zamanı makinenizde olması gerekmez.

Farklı bir sürümü aracılığıyla belirtilmediği sürece .NET Core 2.0 SDK'yı kullanarak, kendi içinde bulunan uygulamalar .NET Core 2.0.0 çalışma zamanı ile yayımlanan `RuntimeFrameworkVersion` özelliği. Bu yeni davranış ile artık kendi başına bir uygulama için daha yüksek bir çalışma zamanı sürümü seçmek için bu özelliği ayarlamak gerekir. İleride en kolay yaklaşım .NET Core 2.1 SDK (v 2.1.300) her zaman yayımlamaktır.

## <a name="windows-compatibility-pack"></a>Windows Uyumluluk Paketi

.NET Framework var olan koddan .NET Core için bağlantı noktası olduğunda, kullanabileceğiniz [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). .NET Core bulunandan daha fazla API'leri 20.000 erişim sağlar. Bu API'leri türler <xref:System.Drawing?displayProperty="nameWithType"> ad alanı, <xref:System.Diagnostics.EventLog> sınıfı, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri.

## <a name="jit-compiler-improvements"></a>JIT Derleyici geliştirmeleri

.NET core içerir adlı yeni bir JIT Derleyici teknoloji *katmanlı derleme* (olarak da bilinen *Uyarlamalı iyileştirme*), önemli ölçüde performansı geliştirebilir. Katmanlı derleme, bir katılımı ayarıdır.

JIT Derleyici tarafından gerçekleştirilen önemli görevlerden birini kod yürütmeyi en iyi duruma getiriyor. Az kullanılan kod yolları için ancak, çalışma zamanı iyileştirilmemiş kod çalıştırmasını harcadığı daha kodu en iyi duruma getirme daha uzun derleyici harcayabilir. Katmanlı derleme JIT derleme iki aşamada sunar:

- A **ilk katmanı**, hangi oluşturur kod mümkün olan en kısa sürede.

- A **ikinci katman**, iyileştirilmiş kodda sık gerçekleştirilen bu yöntemleri için hangi oluşturur. İkinci katmanın derlemesinin paralel Gelişmiş performans için gerçekleştirilir.

İki yöntemden biriyle katmanlı derleme içine tercih edebilirsiniz.

- .NET Core 2.1 SDK'yı tüm projelerde katmanlı derleme kullanmak için aşağıdaki ortam değişkeni ayarlayın:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Katmanlı derleme bir proje başına temelinde kullanılacak eklemek `<TieredCompilation>` özelliğine `<PropertyGroup>` MSBuild proje dosyası, aşağıdaki örnekte gösterildiği gibi bölümünü:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>API değişiklikleri

### <a name="spant-and-memoryt"></a>`Span<T>` Ve `Memory<T>`

.NET core 2.1 çalışma dizilerine sahip olun bazı yeni türleri ve çok daha verimli bellek diğer türleri içerir. Yeni türleri şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Böyle öğeleri bir dizi bir kısmı veya bir bölümünü bellek arabelleği olarak geçirirken bu türleri, bir yönteme geçirmeden önce verileri kısmı bir kopyasını yapmanız gerekir. Bu tür ek bellek ayırma ve kopyalama işlemleri ortadan kaldırır, veriler sanal bir görünümünü sağlar.

Aşağıdaki örnek kullanan bir <xref:System.Span%601> örneği dizi 10 öğelerini sanal bir görünümünü sağlar.

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a>Brotli sıkıştırma

.NET core 2.1 Brotli sıkıştırma ve açma desteğini ekler. Brotli tanımlanan bir genel amaçlı kayıpsız sıkıştırma algoritması olan [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ve birçok web tarayıcıları ve önde gelen web sunucusu tarafından desteklenir. Akış tabanlı kullanabilirsiniz <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıf veya yüksek performanslı Yayılma temelli <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıfları. Aşağıdaki örnek ile sıkıştırma gösterilmektedir <xref:System.IO.Compression.BrotliStream> sınıfı:

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<xref:System.IO.Compression.BrotliStream> Davranıştır aynı <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, hangi kolaylaştırır bu API'leri çağıran dönüştürme kodu <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Yeni şifreleme API'leri ve şifreleme geliştirmeleri

.NET core 2.1 API şifreleme çeşitli geliştirmeler içerir:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> System.Security.Cryptography.Pkcs paketinde kullanılabilir. Aynı uygulamasıdır <xref:System.Security.Cryptography.Pkcs.SignedCms> .NET Framework sınıf.

- Yeni aşırı <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemleri kabul dışında SHA-1 algoritmaları kullanarak sertifika parmak izi değerleri almak arayanlar etkinleştirmek için bir karma algoritması tanımlayıcısı.

- Yeni <xref:System.Span%601>-tabanlı şifreleme API'leri karma için HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifreleme kullanılabilir.

- Performansını <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> % 15'hakkında kullanılarak geliştirilmiş bir <xref:System.Span%601>-temel.

- Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı, iki yeni yöntemleri içerir:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> bir sabit için herhangi iki giriş kullanmaya uygun yan kanal bilgilerini zamanlama için katkıda bulunan önlemek için şifreleme doğrulamasında kolaylaştırır aynı uzunlukta döndürmek için gereken süre.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> iyileştirilemiyor bir bellek temizleme yordamdır.

- Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> yöntemi dolgular bir <xref:System.Span%601> rastgele değerlere sahip.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve maxOS artık desteklenmektedir.

- Eliptik Eğri Diffie-Hellman (ECDH) bulunan şimdi <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesi. Yüzey alanını .NET Framework ile aynı değil.

- Tarafından döndürülen örnek <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> şifrelemek veya SHA-2 özet kullanarak OAEP ile şifresini yanı sıra oluşturabilir veya RSA-PSS kullanarak imzaları doğrular.

### <a name="sockets-improvements"></a>Yuva geliştirmeleri

.NET core içeren yeni bir tür <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>ve bir yeniden <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, üst düzey ağ API'leri temelini oluşturur.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, temelini <xref:System.Net.Http.HttpClient> uygulaması. .NET Core önceki sürümlerinde, üst düzey API'leri yerel ağ uygulamalarında temel alınmıştır.

.NET Core 2.1 içinde sunulan yuva uygulaması, çok sayıda avantaj vardır:

- Önceki bir uygulama ile karşılaştırıldığında önemli performans geliştirmesi.

- Dağıtım ve Bakım kolaylaştıran eleme platform bağımlılıkları.

- Tüm .NET Core platformlar genelinde tutarlı davranışı.

<xref:System.Net.Http.SocketsHttpHandler> .NET Core 2.1 içinde varsayılan uygulamadır. Ancak, eski kullanmak için uygulamanızı yapılandırabilirsiniz <xref:System.Net.Http.HttpClientHandler> çağırarak sınıfı <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> yöntemi:

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", False)
```

Bir ortam de kullanabilirsiniz kullanarak dışında tercih değişkeni yuva göre uygulamaları <xref:System.Net.Http.SocketsHttpHandler>. Bunu yapmak için ayarlayın `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya da `false` veya 0.

Windows, ayrıca kullanmayı tercih edebilirsiniz <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, yerel bir uygulama üzerinde kullanır veya <xref:System.Net.Http.SocketsHttpHandler> sınıfının bir örneğini geçirerek sınıfı <xref:System.Net.Http.HttpClient> Oluşturucusu.

Linux ve macOS, yalnızca yapılandırabilirsiniz <xref:System.Net.Http.HttpClient> işlem başına temelinde. Linux üzerinde dağıtmanız gerekir. [libcurl](https://curl.haxx.se/libcurl/) eski kullanmak istiyorsanız, <xref:System.Net.Http.HttpClient> uygulaması. (.NET Core 2.0 ile yüklenir.)

## <a name="see-also"></a>Ayrıca bkz.

[​.NET Core'daki Yenilikler](index.md)  
[EF çekirdek 2.1 yeni özellikler](/ef/core/what-is-new/ef-core-2.1)  
[ASP.NET Core 2.1 yenilikler nelerdir?](/aspnet/core/aspnetcore-2.1)
