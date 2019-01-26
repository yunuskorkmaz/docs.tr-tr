---
title: .NET Core 2.1 yenilikler nelerdir?
description: .NET Core 2.1 içinde bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 10/10/2018
ms.openlocfilehash: 589d268e937cc9cbd37e88a53fb9e00935d19f55
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066358"
---
# <a name="whats-new-in-net-core-21"></a>.NET Core 2.1 yenilikler nelerdir?

.NET core 2.1 aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:

- [Araç kullanımı](#tooling)
- [İleri Sarma](#roll-forward)
- [Dağıtım](#deployment)
- [Windows Uyumluluk Paketi](#windows-compatibility-pack)
- [JIT derleme geliştirmeleri](#jit-compiler-improvements)
- [API değişiklikleri](#api-changes)

## <a name="tooling"></a>Araç kullanımı

.NET Core 2.1 SDK'sı (v 2.1.300), .NET Core 2.1 ile dahil olan araçları, aşağıdaki değişiklikler ve iyileştirmeler içerir:

### <a name="build-performance-improvements"></a>Derleme performans geliştirmeleri

Özellikle, artımlı derlemeleri için derleme zamanında kalkış performansı önemli bir .NET Core 2.1 odağı gelişiyor. Bu performans geliştirmelerine kullanarak her iki komut satırı derlemeleri uygulama `dotnet build` ve Visual Studio'daki derlemeler. Tek tek bazı geliştirilecek alanlar şunlardır:

- Paket varlık çözümlemesi için yalnızca tüm varlıkları yerine bir derleme tarafından kullanılan varlıklar çözümleniyor.

- Derleme başvuruları önbelleğe alma.

- Uzun süre çalışan SDK kullanımı arasında bireysel kapsayan süreçleri sunucuları, derleme `dotnet build` çağrıları. Bunlar her zaman büyük kod bloklarını JIT derleme gereksinimi ortadan `dotnet build` çalıştırılır. Derleme işlemlerini otomatik olarak aşağıdaki komutla sonlandırılabilir sunucusu:

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a>Yeni CLI komutları

Yalnızca bir proje kullanarak mevcut Araçlar [ `DotnetCliToolReference` ](../tools/extensibility.md) artık .NET Core SDK'sını bir parçası olarak. Bu araçlar şunları içerir:

- `dotnet watch` belirlenmiş bir komut kümesini çalıştırmadan önce değiştirmek bir dosya için bekleyen bir dosya sistemi İzleyicisi sağlar. Örneğin, aşağıdaki komutu otomatik olarak geçerli proje oluşturur ve bir dosyada her değiştiğinde ayrıntılı çıktıyı üretir:

   ```console
   dotnet watch -- --verbose build
   ```

   Not `--` önündeki seçeneği `--verbose` seçeneği. Doğrudan geçirilen seçenekleri sınırlandırır `dotnet watch` alt öğesine geçirilen bağımsız değişkenler komutunu `dotnet` işlem. Bu olmadan, `--verbose` seçeneği uygulandığı `dotnet watch` komutu, `dotnet build` komutu.
  
   Daha fazla bilgi için [dotnet izleme kullanarak ASP.NET Core geliştirme uygulamaları](/aspnet/core/tutorials/dotnet-watch)

- `dotnet dev-certs` oluşturur ve ASP.NET Core uygulamaları geliştirme sırasında kullanılan sertifikalar yönetir.

- `dotnet user-secrets` ASP.NET Core uygulamalarında kullanıcı bir gizli dizi deposu gizli yönetir.

- `dotnet sql-cache` Dağıtılmış önbelleğe alma işlemi için kullanılacak bir Microsoft SQL Server veritabanındaki bir tablo ve dizin oluşturur.

- `dotnet ef` veritabanlarını yönetmek için bir araçtır <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve Entity Framework Core uygulamalarında geçişler. Daha fazla bilgi için [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).

### <a name="global-tools"></a>Genel araçları

.NET core 2.1 destekler *genel Araçları* --genel olarak komut satırından kullanılabilen diğer bir deyişle, özel araçlar. Genişletilebilirlik modeli '.NET Core önceki sürümlerinde özel araçlarla proje bazında yalnızca kullanarak sunulan [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).

Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutu. Örneğin:

```console
dotnet tool install -g dotnetsay
```

Yüklendikten sonra aracı komut satırından aracı adı belirtilerek çalıştırılabilir. Daha fazla bilgi için [.NET Core Araçları Genel genel bakış](../tools/global-tools.md).

### <a name="tool-management-with-the-dotnet-tool-command"></a>Aracı ile Yönetim `dotnet tool` komutu

.NET Core 2.1 SDK tüm araçları işlemler kullanın `dotnet tool` komutu. Aşağıdaki seçenekler mevcuttur:

- [`dotnet tool install`](../tools/dotnet-tool-install.md) bir aracı yüklemek için.

- [`dotnet tool update`](../tools/dotnet-tool-update.md) etkili bir şekilde güncelleştiren bir aracı kaldırıp için.

- [`dotnet tool list`](../tools/dotnet-tool-list.md) şu anda listelemek için araçları yüklü.

- [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) şu anda yüklü araçları kaldırmak için.

## <a name="roll-forward"></a>İleri Sarma

.NET Core 2.0 ile otomatik olarak itibaren tüm .NET Core uygulamaları en son İleri sarmanın *podverze* bir sisteme yüklenmiş.

Bir uygulamanın derlendiği .NET Core sürümü çalışma zamanında mevcut değilse, .NET Core 2.0 ile başlayarak, uygulama otomatik olarak en son yüklenen karşı çalışır *podverze* .NET core'un. Diğer bir deyişle, .NET Core 2.0 ile bir uygulama oluşturulur ve .NET Core 2.1 .NET Core 2.0, ana sistemde mevcut değil. ancak, uygulama .NET Core 2.1 ile çalışır.

> [!IMPORTANT]
> Bu sarma davranışı Önizleme sürümleri için geçerli değildir. Varsayılan olarak, ana sürümler için de geçerli değildir, ancak bu ayarlarla değiştirilebilir.

Hiçbir aday paylaşılan Framework sarma ayarını değiştirerek bu davranışı değiştirebilirsiniz. Kullanılabilir ayarlar şunlardır:
- `0` -ikincil sürüm sarma davranışı devre dışı bırakın. Bu ayar, .NET Core 2.0.0 için oluşturulmuş bir uygulamada İleri .NET Core 2.0.1, ancak .NET Core 2.2.0 veya .NET Core 3.0.0 dökümünü yapar.
- `1` -ikincil sürüm sarma davranışı etkinleştirin. Bu ayar için varsayılan değerdir. Bu ayar, .NET Core 2.0.0 için oluşturulmuş bir uygulamada ileriye ya da .NET Core için 2.0.1 veya .NET Core hangisini seçtiğinize bağlı olarak yüklü, ancak bunu İleri 3.0.0 .NET Core için döküm değil 2.2.0 dökümünü yapar.
- `2` -küçük ve büyük sürüm sarma davranışı etkinleştirin. .NET Core 2.0.0 için oluşturulmuş bir uygulama için .NET Core 3.0.0 İleri sarmanın şekilde ayarlanmışsa, hatta farklı ana sürümleri kabul edilir

Bu ayarı üç yoldan herhangi birini değiştirebilirsiniz:

- Ayarlama `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkeni istenen değeri.

- İstenen değeri içeren aşağıdaki satırı ekleyin `runtimeconfig.json` dosyası:

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- Kullanırken [.NET Core CLI Araçları](../tools/index.md), istenen değeri aşağıdaki seçenek gibi .NET Core komut ekleme `run`:

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

Düzeltme eki sürümü alma İleri bu ayarı bağımsızdır ve tüm olası ikincil sonra Bitti veya ana sürüm ileri sarma uygulanır.

## <a name="deployment"></a>Dağıtım

### <a name="self-contained-application-servicing"></a>Kendi içinde Uygulama Bakımı

`dotnet publish` artık kendi başına bir hizmet verilen çalışma zamanı sürümü uygulamalarla yayımlar. .NET Core 2.1 SDK'sı (v 2.1.300) kendi içinde bir uygulama yayımladığınızda, uygulamanız bu SDK'sı tarafından bilinen en son hizmet verilen çalışma zamanı sürümünü içerir. En son SDK'yı yükselttiğinizde, en son .NET Core çalışma zamanı sürümüyle yayımlama. Bu .NET Core 1.0 çalışma zamanları ve sonrası için geçerlidir.

Çalışma zamanı sürümleri nuget.org müstakil yayımlama kullanır. Hizmet verilen çalışma zamanı, makinenizdeki gerekmez.

Farklı bir sürümü aracılığıyla belirtilmediği sürece .NET Core 2.0 SDK'sını kullanarak kendi içindeki uygulamaları .NET Core 2.0.0 çalışma zamanı ile yayımlanan `RuntimeFrameworkVersion` özelliği. Bu yeni davranış artık kendi içinde bir uygulama için daha yüksek bir çalışma zamanı sürümünü seçmek için bu özelliği ayarlayın gerekir. İleriye dönük en kolay yaklaşım .NET Core 2.1 SDK (v 2.1.300) her zaman yayımlamaktır.

Daha fazla bilgi için [müstakil azure'daki çalışma zamanı, ileri sarma](../deploying/runtime-patch-selection.md).
## <a name="windows-compatibility-pack"></a>Windows Uyumluluk Paketi

.NET Framework mevcut koddan .NET Core için bağlantı noktası, kullanabileceğiniz [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility). ' De .NET Core bulunandan daha fazla API 20.000 erişim sağlar. Bu API'ler türler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıf, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri.

## <a name="jit-compiler-improvements"></a>JIT Derleyici iyileştirmeleri

.NET core içerir adlı yeni bir JIT derleyicisi teknoloji *katmanlı derleme* (olarak da bilinen *Uyarlamalı iyileştirme*), önemli ölçüde performansı geliştirebilir. Katmanlı derleme, bir katılım ayarıdır.

JIT derleyicisi tarafından gerçekleştirilen önemli görevlerinden birini ve kod yürütme en iyi duruma getiriyor. Az kullanılan kodu yolları için ancak derleyici iyileştirilmemiş kod çalıştırma, çalışma zamanı geçirdiği daha kodu en iyi duruma getirme daha fazla zaman harcayabilir. Katmanlı bir derleme JIT derlemesi iki aşamada sunar:

- A **ilk katman**, mümkün olan en kısa sürede kod oluşturduğu.

- A **ikinci katman**, oluşturduğu kodu sık yürütülen bu yöntemleri için en iyi duruma getirilmiş. Derleme, ikinci katman, Gelişmiş performans için paralel gerçekleştirilir.

İki yöntemden biriyle katmanlı derleme kabul edebileceğiniz.

- .NET Core 2.1 SDK'sını kullanan tüm projelerde katmanlı derleme kullanmak için aşağıdaki ortam değişkenlerini ayarlayın:

  ```console
  COMPlus_TieredCompilation="1"
  ```

- Katmanlı derleme proje başına temelinde kullanılacak ekleme `<TieredCompilation>` özelliğini `<PropertyGroup>` MSBuild proje dosyası, aşağıdaki örnekte gösterildiği gibi bir bölümünü:

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a>API değişiklikleri

### <a name="spant-and-memoryt"></a>`Span<T>` ve `Memory<T>`

.NET core 2.1 dizileri ile çalışmayı kolaylaştıran bazı yeni türlerini ve çok daha verimli bellek diğer türleri içerir. Yeni türleri şunlardır:

- <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.

- <xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.

Bu tür öğeleri dizi değerinin bir bölümü veya bir bölümünü bellek arabelleği olarak geçirirken bu türleri, bir yönteme iletmeden önce bölümü verilerin bir kopyasını yapmanız gerekir. Bu türler ek bellek ayırma ve kopyalama işlemleri ihtiyacını ortadan kaldırır, verilerin sanal bir görünümünü sağlar.

Aşağıdaki örnekte bir <xref:System.Span%601> ve <xref:System.Memory%601> dizi 10 öğelerini sanal bir görünümünü sağlamak için örneği.

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!CODE-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a>Brotli sıkıştırma

.NET core 2.1 Brotli sıkıştırma ve açma desteğini ekler. Brotli tanımlanan bir genel amaçlı kayıpsız sıkıştırma algoritması olan [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ve web tarayıcıları ve ana web sunucuları tarafından desteklenir. Akış tabanlı kullanabileceğiniz <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfı veya yüksek performanslı aralık tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıfları. Sıkıştırmasıyla aşağıdaki örnekte <xref:System.IO.Compression.BrotliStream> sınıfı:

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<xref:System.IO.Compression.BrotliStream> Davranışı aynıdır <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, kolaylaştıran için bu API'leri çağıran koda dönüştürme <xref:System.IO.Compression.BrotliStream>.

### <a name="new-cryptography-apis-and-cryptography-improvements"></a>Yeni şifreleme API'leri ve şifreleme geliştirmeleri

.NET core 2.1 şifreleme API'leri için çeşitli iyileştirmeler içerir:

- <xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> System.Security.Cryptography.Pkcs pakette kullanılabilir. Uygulama ile aynı olduğu <xref:System.Security.Cryptography.Pkcs.SignedCms> .NET Framework sınıfı.

- Yeni aşırı yüklemeleri <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemleri dışında SHA-1 algoritmaları kullanarak sertifika parmak izi değerleri almak çağıranlar etkinleştirmek için bir karma algoritması tanımlayıcı kabul edin.

- Yeni <xref:System.Span%601>-karma işlevi için HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifreleme tabanlı şifreleme API'leri kullanılabilir.

- Performansını <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> yaklaşık 15 oranında kullanılarak geliştirilmiş bir <xref:System.Span%601>-uygulama tabanlı.

- Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı iki yeni yöntemler içerir:

  - <xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> Bu kullanım için uygun yan kanal bilgileri zamanlama için katkıda bulunan önlemek için şifreleme doğrulama yapar aynı uzunlukta iki tüm girişleri için döndürülecek sabit bir süre sürer.

  - <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> hale getirilemeyen bir bellek temizleme yordamdır.

- Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntemi dolduran bir <xref:System.Span%601> rasgele değerlere sahip.

- <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve maxOS artık desteklenmektedir.

- Eliptik Eğri Diffie-Hellman (ECDH) içinde kullanıma sunuldu <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesi. Yüzey alanı .NET Framework olduğu gibi aynıdır.

- Tarafından döndürülen örneği <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> şifrelemek veya şifresini bir SHA-2 özet kullanarak OAEP ile hem de oluşturabilir veya kullanılarak RSA-PSS imza doğrulama.

### <a name="sockets-improvements"></a>Yuva geliştirmeleri

.NET core içeren yeni bir tür <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>ve bir yeniden <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, üst düzey ağ API'leri temelini oluşturur.  <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, temelidir <xref:System.Net.Http.HttpClient> uygulaması. .NET Core önceki sürümlerinde, yerel ağ uygulamalarında üst düzey API'ler temel alınmıştır.

.NET Core 2.1 içinde tanıtılan bir yuva uygulaması, çok sayıda avantaj vardır:

- Önceki bir uygulama ile karşılaştırıldığında önemli bir performans geliştirmesi.

- Dağıtımı ve bakımı kolaylaştıran eleme, platform bağımlılıkları.

- Tüm .NET Core platformlar genelinde tutarlı davranışı.

<xref:System.Net.Http.SocketsHttpHandler> .NET Core 2.1 içinde varsayılan uygulamasıdır. Ancak, eski kullanmak için uygulamanızı yapılandırabileceğiniz <xref:System.Net.Http.HttpClientHandler> çağırarak sınıfı <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi:

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

Bir ortam kullanabilirsiniz kullanarak dışında kabul etmek için değişken yuva göre uygulamaları <xref:System.Net.Http.SocketsHttpHandler>. Bunu yapmak için ayarlanmış `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya da `false` veya 0.

Windows üzerinde de kullanmayı seçebilirsiniz <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, yerel bir uygulama üzerinde kullanır veya <xref:System.Net.Http.SocketsHttpHandler> sınıfı örneğini geçirerek sınıf <xref:System.Net.Http.HttpClient> Oluşturucusu.

Linux ve Macos'ta, yalnızca yapılandırabilirsiniz <xref:System.Net.Http.HttpClient> işlem başına temelinde. Linux üzerinde dağıtmanız gerekir. [libcurl](https://curl.haxx.se/libcurl/) eski kullanmak istiyorsanız <xref:System.Net.Http.HttpClient> uygulaması. (.NET Core 2.0 ile yüklenir.)

## <a name="see-also"></a>Ayrıca bkz.

- [​.NET Core'daki Yenilikler](index.md)
- [EF Core 2.1 yeni özellikler](/ef/core/what-is-new/ef-core-2.1)
- [ASP.NET Core 2.1 yenilikler nelerdir?](/aspnet/core/aspnetcore-2.1)
