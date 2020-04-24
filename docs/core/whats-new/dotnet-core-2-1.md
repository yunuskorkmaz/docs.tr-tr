---
title: ​.NET Core 2.1’deki yenilikler
description: .NET Core 2.1'de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 78d9a6490c0479d9c21e01d0bcba41294d674a5c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644376"
---
# <a name="whats-new-in-net-core-21"></a>​.NET Core 2.1’deki yenilikler

.NET Core 2.1 aşağıdaki alanlardaki geliştirmeleri ve yeni özellikleri içerir:

- [Araçlar](#tooling)
- [İleri yuvarlan](#roll-forward)
- [Dağıtım](#deployment)
- [Windows Uyumluluk Paketi](#windows-compatibility-pack)
- [JIT derleme geliştirmeleri](#jit-compiler-improvements)
- [API değişiklikleri](#api-changes)

## <a name="tooling"></a>Araçlar

.NET Core 2.1 SDK (v 2.1.300), .NET Core 2.1 ile birlikte araç, aşağıdaki değişiklikleri ve geliştirmeleri içerir:

### <a name="build-performance-improvements"></a>Performans iyileştirmeleri oluşturun

.NET Core 2.1'in ana odak noktası, özellikle artımlı yapılar için yapı zamanı performansını geliştirmektir. Bu performans iyileştirmeleri, Visual Studio'da `dotnet build` hem komut satırı kullanarak hem de oluşturmalar için geçerlidir. Bazı bireysel iyileştirme alanları şunlardır:

- Paket kıymet çözümü için, tüm varlıklar yerine yalnızca bir yapı tarafından kullanılan varlıkları çözümleme.

- Derleme başvurularının önbelleğe alma.

- Uzun süredir çalışan SDK yapı sunucularının kullanımı, `dotnet build` tek tek çağrıları kapsayan işlemlerdir. Her çalıştırılışta `dotnet build` büyük kod bloklarını JIT derleme gereksinimini ortadan kaldırırlar. Yapı sunucusu işlemleri aşağıdaki komutla otomatik olarak sonlandırılabilir:

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Yeni CLI komutları

Sadece proje bazında `DotnetCliToolReference` kullanılabilen bir dizi araç artık .NET Core SDK'nın bir parçası olarak kullanılabilir. Bu araçlar şunları içerir:

- `dotnet watch`belirlenmiş bir komut kümesini yürütmeden önce bir dosyanın değişmesini bekleyen bir dosya sistemi izleyicisi sağlar. Örneğin, aşağıdaki komut geçerli projeyi otomatik olarak yeniden oluşturur ve içinde bir dosya değiştiğinde ayrıntılı çıktı oluşturur:

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   Seçenekten `--` önce gelen `--verbose` seçeneği not edin. Alt `dotnet watch` `dotnet` işleme geçirilen bağımsız değişkenlerden doğrudan komuta geçirilen seçenekleri sınırlandırmaktadır. Onsuz, `--verbose` seçenek `dotnet watch` `dotnet build` komut için değil, komut için geçerlidir.
  
   Daha fazla bilgi için [dotnet watch kullanarak ASP.NET Core uygulamaları geliştir'e](/aspnet/core/tutorials/dotnet-watch)bakın.

- `dotnet dev-certs`ASP.NET Core uygulamalarında geliştirme sırasında kullanılan sertifikaları oluşturur ve yönetir.

- `dotnet user-secrets`ASP.NET Core uygulamalarında bir kullanıcı gizli mağazasında sırları yönetir.

- `dotnet sql-cache`dağıtılmış önbelleğe alma için kullanılmak üzere Microsoft SQL Server veritabanında bir tablo ve dizinler oluşturur.

- `dotnet ef`Varlık Framework Core uygulamalarındaki <xref:Microsoft.EntityFrameworkCore.DbContext> veritabanlarını, nesneleri ve geçişleri yönetmek için bir araçtır. Daha fazla bilgi için [BKZ.](/ef/core/miscellaneous/cli/dotnet)

### <a name="global-tools"></a>Genel Araçlar

.NET Core 2.1, *Genel Araçları* destekler -- yani komut satırından küresel olarak kullanılabilen özel araçlar. .NET Core'un önceki sürümlerindeki genişletilebilirlik modeli, özel araçları yalnızca `DotnetCliToolReference`proje bazında kullanılabilir hale getirdi.

Genel Bir Araç yüklemek için [dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutunu kullanırsınız. Örneğin:

```dotnetcli
dotnet tool install -g dotnetsay
```

Yüklendikten sonra, araç komut satırından araç adını belirterek çalıştırılabilir. Daha fazla bilgi için [.NET Core Global Tools genel bakış](../tools/global-tools.md)bilgisine bakın.

### <a name="tool-management-with-the-dotnet-tool-command"></a>`dotnet tool` Komut ile araç yönetimi

.NET Core 2.1 SDK'da tüm `dotnet tool` araçlar işlemleri komutu kullanır. Aşağıdaki seçenekler mevcuttur:

- [`dotnet tool install`](../tools/dotnet-tool-install.md)bir araç yüklemek için.

- [`dotnet tool update`](../tools/dotnet-tool-update.md)etkili bir şekilde güncelleyen bir aracı kaldırmak ve yeniden yüklemek için.

- [`dotnet tool list`](../tools/dotnet-tool-list.md)şu anda yüklü araçları listeleyin.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)şu anda yüklü araçları kaldırmak için.

## <a name="roll-forward"></a>İleri yuvarlan

.NET Core 2.0 ile başlayan tüm .NET Core uygulamaları otomatik olarak bir sisteme yüklenen en son *küçük sürüme* doğru ilerler.

.NET Core 2.0 ile başlayarak, bir uygulamanın birlikte üretilmiş olduğu .NET Core sürümü çalışma zamanında yoksa, uygulama otomatik olarak .NET Core'un en son yüklenen *küçük sürümüne* göre çalışır. Başka bir deyişle, bir uygulama .NET Core 2.0 ile oluşturulmuşsa ve .NET Core 2.0 ana bilgisayar sisteminde yoksa,.NET Core 2.1 ise, uygulama .NET Core 2.1 ile çalışır.

> [!IMPORTANT]
> Bu roll-forward davranışı önizleme sürümleri için geçerli değildir. Varsayılan olarak, büyük sürümler için de geçerli değildir, ancak bu aşağıdaki ayarlarla değiştirilebilir.

Bu davranışı, aday paylaşılan bir çerçevede yuvarlanmayın ayarını değiştirerek değiştirebilirsiniz. Kullanılabilir ayarlar şunlardır:

- `0`- küçük sürüm roll-forward davranışını devre dışı kılabilir. Bu ayar ile .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 2.0.1'e doğru iletilir, ancak .NET Core 2.2.0 veya .NET Core 3.0.0'a değil.
- `1`- küçük sürüm roll-forward davranışını etkinleştirin. Bu, ayar için varsayılan değerdir. Bu ayar ile .NET Core 2.0.0 için oluşturulmuş bir uygulama,.NET Core 2.0.1 veya .NET Core 2.2.0'a, hangisinin yüklendiğine bağlı olarak ileri ye doğru yuvarlanır, ancak .NET Core 3.0.0'a doğru yuvarlanmayacaktır.
- `2`- küçük ve ana sürüm roll-forward davranışını etkinleştirin. Ayarlanırsa, farklı ana sürümler bile dikkate alınır, bu nedenle .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 3.0.0'a doğru yuvarlanır.

Bu ayarı üç şekilde değiştirebilirsiniz:

- Ortam `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` değişkenini istenilen değere ayarlayın.

- *.runtimeconfig.json* dosyasına istenilen değere sahip aşağıdaki satırı ekleyin:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- [.NET Core CLI](../tools/index.md)kullanırken, aşağıdaki seçeneği istenilen değere sahip bir `run`.NET Core komutu gibi ekleyin:

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Patch sürüm roll forward bu ayarınbağımsızdır ve herhangi bir potansiyel küçük veya ana sürüm roll forward uygulandıktan sonra yapılır.

## <a name="deployment"></a>Dağıtım

### <a name="self-contained-application-servicing"></a>Bağımsız uygulama hizmeti

`dotnet publish`şimdi hizmet eken çalışma zamanı sürümüyle bağımsız uygulamalar yayımlar. .NET Core 2.1 SDK (v 2.1.300) ile bağımsız bir uygulama yayımladığınızda, uygulamanız bu SDK tarafından bilinen en son servisli çalışma zamanı sürümünü içerir. En son SDK'ya yükselttiğinde, en son .NET Core çalışma zamanı sürümüyle yayımlarsınız. Bu, .NET Core 1.0 çalışma saatleri ve sonrası için geçerlidir.

Bağımsız yayımlama, NuGet.org'daki çalışma zamanı sürümlerine dayanır. Makinenizde servis edilen çalışma süresine sahip olmanız gerekmez.

.NET Core 2.0 SDK kullanılarak, `RuntimeFrameworkVersion` özellik üzerinden farklı bir sürüm belirtilmedikçe,.NET Core 2.0.0 çalışma süresi ile bağımsız uygulamalar yayınlanır. Bu yeni davranışla, artık bu özelliği, bağımsız bir uygulama için daha yüksek bir çalışma zamanı sürümü seçecek şekilde ayarlamanız gerekmez. İleriye dönük en kolay yaklaşım her zaman .NET Core 2.1 SDK (v 2.1.300) ile yayınlamaktır.

Daha fazla bilgi için bkz: [Bağımsız dağıtım çalışma zamanı ileri sarma.](../deploying/runtime-patch-selection.md)
## <a name="windows-compatibility-pack"></a>Windows Uyumluluk Paketi

Varolan kodu .NET Framework'den .NET Core'a taşımadığınızda, [Windows Uyumluluk Paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)kullanabilirsiniz. .NET Core'da bulunandan 20.000 daha fazla API'ye erişim sağlar. Bu API'ler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıf, WMI, Performans Sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri türleri içerir.

## <a name="jit-compiler-improvements"></a>JIT derleyici geliştirmeleri

.NET Core, performansı önemli ölçüde artırabilen *katmanlı derleme* *(uyarlamalı optimizasyon*olarak da bilinir) adı verilen yeni bir JIT derleyici sİstemi içerir. Katmanlı derleme bir opt-in ayarıdır.

JIT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri kod yürütmeyi en iyi duruma getirmektir. Ancak az kullanılan kod yolları için derleyici, en iyi duruma getirilmemiş kodu çalıştırmak için çalışma süresi harcadığından daha fazla zaman geçirebilir. Katmanlı derleme JIT derlemesinde iki aşama yı tanıtır:

- Kodu mümkün olduğunca çabuk üreten **birinci katman.**

- Sık sık yürütülen bu yöntemler için en iyi duruma getirilmiş kod üreten ikinci bir **katman.** İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.

Katmanlı derlemeyi iki şekilde de seçebilirsiniz.

- .NET Core 2.1 SDK kullanan tüm projelerde katmanlı derleme kullanmak için aşağıdaki ortam değişkenini ayarlayın:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Katmanlı derlemeyi proje başına kullanmak için, aşağıdaki `<TieredCompilation>` örnekte `<PropertyGroup>` görüldüğü gibi özelliği MSBuild proje dosyasının bölümüne ekleyin:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>API değişiklikleri

### <a name="spant-and-memoryt"></a>`Span<T>` ve `Memory<T>`

.NET Core 2.1 dizileri ve bellek diğer türleri ile çalışma çok daha verimli hale bazı yeni türleri içerir. Yeni türleri şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bu türler olmadan, bu tür öğeleri bir dizinin bölümü veya bellek arabelleği bölümü olarak geçerken, bir yönteme geçirmeden önce verilerin bir bölümünün bir kopyasını oluşturmanız gerekir. Bu türler, ek bellek ayırma ve kopyalama işlemleri gereksinimini ortadan kaldıran bu verilerin sanal bir görünümünü sağlar.

Aşağıdaki örnek, <xref:System.Span%601> bir <xref:System.Memory%601> dizinin 10 öğesinin sanal görünümünü sağlamak için bir ve örnek kullanır.

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Brotli sıkıştırma

.NET Core 2.1 Brotli sıkıştırma ve dekompresyon desteği ekler. Brotli, [RFC 7932'de](https://www.ietf.org/rfc/rfc7932.txt) tanımlanan ve çoğu web tarayıcısı ve büyük web sunucuları tarafından desteklenen genel amaçlı kayıpsız sıkıştırma algoritmasıdır. Akış tabanlı <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfı veya yüksek performanslı yayılma tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> ve sınıfları kullanabilirsiniz. Aşağıdaki örnek, sınıfla <xref:System.IO.Compression.BrotliStream> sıkıştırmayı göstermektedir:

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

Davranış <xref:System.IO.Compression.BrotliStream> aynıdır <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, bu API'leri <xref:System.IO.Compression.BrotliStream>çağıran kodu dönüştürmeyi kolaylaştırır.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Yeni şifreleme API'leri ve şifreleme geliştirmeleri

.NET Core 2.1 şifreleme API'leri için çok sayıda geliştirme içerir:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>System.Security.Cryptography.Pkcs paketinde mevcuttur. Uygulama .NET Framework'deki <xref:System.Security.Cryptography.Pkcs.SignedCms> sınıfla aynıdır.

- Yeni aşırı yükler <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> ve yöntemler, arayanların SHA-1 dışındaki algoritmaları kullanarak sertifika parmak izi değerlerini almalarını sağlamak için karma algoritma tanımlayıcısını kabul eder.

- Karma, HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifrelemesi için yeni <xref:System.Span%601>tabanlı şifreleme API'leri mevcuttur.

- Performans, <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> tabanlı bir <xref:System.Span%601>uygulama kullanılarak yaklaşık %15 oranında iyileşmiştir.

- Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıf iki yeni yöntem içerir:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>aynı uzunluktaki iki giriş için döndürülmesi için belirli bir süre alır, bu da yan kanal bilgilerinin zamanlamasına katkıda bulunmaktan kaçınmak için şifreleme doğrulamada kullanıma uygun hale getirir.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>en iyi duruma getirilen bir bellek temizleme yordamıdır.

- Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntem a'yı <xref:System.Span%601> rasgele değerlerle doldurur.

- Şimdi <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve macOS üzerinde desteklenir.

- Eliptik-Eğri Diffie-Hellman (ECDH) artık <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesinde mevcuttur. Yüzey alanı .NET Framework ile aynıdır.

- Döndürülen <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> örnek, SHA-2 özeti kullanarak OAEP ile şifrelenebilir veya şifresini çözebilir ve RSA-PSS kullanarak imza oluşturabilir veya doğrulayabilir.

### <a name="sockets-improvements"></a>Soket iyileştirmeleri

.NET Core, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>üst düzey ağ API'lerinin temelini oluşturan yeni bir tür ve yeniden yazılmış <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>bir tür içerir.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, uygulamanın <xref:System.Net.Http.HttpClient> temelidir. .NET Core'un önceki sürümlerinde, üst düzey API'ler yerel ağ uygulamalarını temel alıyordu.

.NET Core 2.1'de tanıtılan soket uygulamasının bir takım avantajları vardır:

- Önceki uygulamaile karşılaştırıldığında önemli bir performans artışı.

- Dağıtım ve servis işlemlerini kolaylaştıran platform bağımlılıklarının ortadan kaldırılması.

- Tüm .NET Core platformlarında tutarlı davranış.

<xref:System.Net.Http.SocketsHttpHandler>.NET Core 2.1'deki varsayılan uygulamadır. Ancak, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi çağırarak uygulamanızı eski <xref:System.Net.Http.HttpClientHandler> sınıfı kullanacak şekilde yapılandırabilirsiniz:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Soket uygulamalarını temel alan uygulamadan çıkmak için bir <xref:System.Net.Http.SocketsHttpHandler>ortam değişkeni de kullanabilirsiniz. Bunu yapmak için, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya `false` da 0 ayarlayın.

Windows'da, sınıfın bir <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>örneğini <xref:System.Net.Http.HttpClient> oluşturucuya geçirerek yerel <xref:System.Net.Http.SocketsHttpHandler> bir uygulamaya veya sınıfa dayanan bir sınıfı kullanmayı da seçebilirsiniz.

Linux ve macOS'ta yalnızca <xref:System.Net.Http.HttpClient> işlem başına göre yapılandırabilirsiniz. Linux'ta, eski <xref:System.Net.Http.HttpClient> uygulamayı kullanmak istiyorsanız [libcurl](https://curl.haxx.se/libcurl/) dağıtmanız gerekir. (.NET Core 2.0 ile yüklenir.)

### <a name="breaking-changes"></a>Yeni değişiklikler

Değişiklikleri kesme hakkında bilgi için, [sürüm 2.0'dan 2.1'e geçiş için Kesme değişikliklerine](../compatibility/2.0-2.1.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [​.NET Core 3.1’deki yenilikler](dotnet-core-3-1.md)
- [EF Core 2.1'deki yeni özellikler](/ef/core/what-is-new/ef-core-2.1)
- [ASP.NET Core 2.1'deki yenilikler](/aspnet/core/aspnetcore-2.1)
