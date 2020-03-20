---
title: .NET Framework’teki yenilikler
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: fa7138127379b069b646c4b2488d1973a3ddd628
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143323"
---
# <a name="whats-new-in-net-framework"></a>.NET Framework'deki yenilikler

Bu makalede, .NET Framework'ün aşağıdaki sürümlerindeki önemli yeni özellikler ve geliştirmeler özetlenmiştir:

- [.NET Çerçeve 4.8](#v48)
- [.NET Çerçeve 4.7.2](#v472)
- [.NET Çerçeve 4.7.1](#v471)
- [.NET Çerçeve 4.7](#v47)
- [.NET Framework 4.6.2](#v462)
- [.NET Framework 4.6.1](#v461)
- [.NET 2015 ve .NET Çerçeve 4.6](#v46)
- [.NET Framework 4.5.2](#v452)
- [.NET Framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Bu makalede, her yeni özellik hakkında kapsamlı bilgi sağlamaz ve değiştirilebilir. .NET Framework hakkında genel bilgi için [bkz.](../get-started/index.md) Desteklenen platformlar için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md)bakın. İndirme bağlantıları ve yükleme yönergeleri için [Kurulum Kılavuzu'na](../install/guide-for-developers.md)bakın.

> [!NOTE]
> .NET Framework ekibi ayrıca platform desteğini genişletmek ve değişmez koleksiyonlar ve SIMD özellikli vektör türleri gibi yeni işlevleri tanıtmak için NuGet ile bant dışı özellikler de yayımlar. Daha fazla bilgi için [ek sınıf kitaplıkları ve API'ler ve](../additional-apis/index.md) [.NET Framework ve Out-of-Band Sürümleri'ne](../get-started/the-net-framework-and-out-of-band-releases.md)bakın.
> .NET Framework için [NuGet paketlerinin tam listesine](https://www.nuget.org/profiles/dotnetframework) bakın.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>.NET Framework 4.8 Tanıtımı

.NET Framework 4.8, .NET Framework 4.x'in önceki sürümlerine, çok kararlı bir ürün olarak kalırken birçok yeni düzeltme ve birkaç yeni özellik ekleyerek temel oluşturur.

### <a name="downloading-and-installing-net-framework-48"></a>.NET Framework 4.8'i indirme ve yükleme

.NET Framework 4.8'i aşağıdaki konumlardan indirebilirsiniz:

- [.NET Framework 4.8 Web Yükleyici](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [NET Framework 4.8 Çevrimdışı Yükleyici](https://dotnet.microsoft.com/download/dotnet-framework/net48)

.NET Framework 4.8, Windows 10, Windows 8.1, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayan ilgili sunucu platformlarına yüklenebilir. .NET Framework 4.8'i web yükleyicisini veya çevrimdışı yükleyiciyi kullanarak yükleyebilirsiniz. Çoğu kullanıcı için önerilen yol web yükleyicisini kullanmaktır.

.NET Framework 4.8'i Visual Studio 2012'de veya daha sonra [.NET Framework 4.8 Geliştirici Paketini](https://go.microsoft.com/fwlink/?LinkId=2085167)yükleyerek hedefleyebilirsiniz.

### <a name="whats-new-in-net-framework-48"></a>.NET Framework 4.8'deki yenilikler

.NET Framework 4.8 aşağıdaki alanlarda yeni özellikler sunar:

- [Taban sınıflar](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Ortak dil çalışma zamanı](#clr48)

Bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sunmasına olanak tanıyan gelişmiş erişilebilirlik, .NET Framework 4.8'in ana odak noktası olmaya devam etmektedir. .NET Framework 4.8'deki erişilebilirlik geliştirmeleri hakkında bilgi için [.NET Framework'deki erişilebilirlikte yeniliklere](whats-new-in-accessibility.md)bakın.

<a name="core48" />

#### <a name="base-classes"></a>Temel sınıflar

**Şifreleme üzerinde azaltılmış FIPS etkisi.** .NET Framework'ün önceki sürümlerinde, sistem şifreleme <xref:System.Security.Cryptography.SHA256Managed> kitaplıklarının "FIPS modunda" yapılandırıldığı zaman <xref:System.Security.Cryptography.CryptographicException> atma gibi yönetilen şifreleme sağlayıcısı sınıfları. Bu özel durumlar, sistem şifreleme kitaplıklarının aksine, şifreleme sağlayıcı sınıflarının yönetilen sürümleri FIPS (Federal Bilgi İşlem Standartları) 140-2 sertifikasına sahip olmadığından atılmıştır. Çok az geliştiricinin GELIŞTIRME makineleri FIPS modunda olduğundan, özel durumlar genellikle üretim sistemlerine atılır.

.NET Framework 4.8'i hedefleyen uygulamalarda varsayılan olarak, aşağıdaki yönetilen <xref:System.Security.Cryptography.CryptographicException> şifreleme sınıfları artık bu durumda bir şey atmamaktadır:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Bunun yerine, bu sınıflar şifreleme işlemlerini bir sistem şifreleme kitaplığına yönlendirir. Bu değişiklik, geliştirici ortamları ile üretim ortamları arasındaki olası kafa karıştırıcı farkı etkili bir şekilde ortadan kaldırır ve yerel bileşenlerin ve yönetilen bileşenlerin aynı şifreleme ilkesi altında çalışmasını sağlar. Bu özel durumlara bağlı uygulamalar, AppContext anahtarını `Switch.System.Security.Cryptography.UseLegacyFipsThrow` `true`'da ayarlayarak önceki davranışı geri yükleyebilir. Daha fazla bilgi için bkz: [Yönetilen şifreleme sınıfları FIPS modunda ŞifrelemeÖzel Durum'u atmayın.](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode)

**ZLib'in güncelleştirilmiş sürümünün kullanımı**

.NET Framework 4.5 ile başlayarak, clrcompression.dll derlemesi, söndürme algoritması için bir uygulama sağlamak için veri sıkıştırma için yerel bir dış kitaplık olan [ZLib'i](https://www.zlib.net)kullanır. .NET Framework 4.8, clrcompression.dll, birkaç önemli iyileştirme ve düzeltme içeren ZLib Sürüm 1.2.11'i kullanacak şekilde güncelleştirilir.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**Hizmet EkiHizmetSağlık Davranışı**

Sistem durumu uç noktaları, hizmetleri sağlık durumuna göre yönetmek için düzenleme araçları tarafından yaygın olarak kullanılır. Sistem durumu denetimleri, bir hizmetin kullanılabilirliği ve performansı hakkında bildirimleri izlemek ve sağlamak için izleme araçları tarafından da kullanılabilir.

**ServiceHealthBehavior** genişleten <xref:System.ServiceModel.Description.IServiceBehavior>bir WCF hizmet davranışıdır.  Koleksiyona <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> eklendiğinde, bir hizmet davranışı aşağıdakileri yapar:

- HIZMET durumu durumunu HTTP yanıt kodlarıyla döndürür. Bir http/GET sistem durumu sondası isteği için http durum kodunu sorgu dizesinde belirtebilirsiniz.

- Hizmet durumu yla ilgili bilgileri yayımlar. Hizmet durumu, gaz sayımı ve kapasite gibi hizmete özgü ayrıntılar sorgu dizesi ile `?health` bir HTTP/GET isteği kullanılarak görüntülenebilir. Bir yanlış davranan WCF hizmetini gidermede bu tür bilgilere erişim kolaylığı önemlidir.

Sistem durumu bitiş noktasını ortaya çıkarmanın ve WCF hizmet sistem durumu bilgilerini yayımlamanın iki yolu vardır:

- Kod aracılığıyla. Örnek:

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- Yapılandırma dosyası kullanarak. Örnek:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

`OnServiceFailure`Bir hizmetin sistem durumu, , , , `OnDispatcherFailure` `OnListenerFailure` `OnThrottlePercentExceeded`gibi sorgu parametreleri kullanılarak sorgulanabilir ve her sorgu parametresi için bir HTTP yanıt kodu belirtilebilir. Bir sorgu parametresi için HTTP yanıt kodu atlanırsa, varsayılan olarak 503 HTTP yanıt kodu kullanılır. Örnek:

- OnServiceFailure:`https://contoso:81/Service1?health&OnServiceFailure=450`

  [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) daha <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>büyük olduğunda 450 HTTP yanıt durum kodu döndürülür.
Sorgu parametreleri ve örnekler:

- OnDispatcherFailure:`https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Kanal gönderenlerden herhangi birinin durumu 'ndan <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>büyük olduğunda 455 HTTP yanıt durum kodu döndürülür.

- OnListenerFailure:`https://contoso:81/Service1?health&OnListenerFailure=465`

  Kanal dinleyicilerinden herhangi birinin durumu daha büyük olduğunda 465 HTTP <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>yanıt durum kodu döndürülür.

- OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Yanıtı tetikleyen {1 – 100} yüzdesini ve HTTP yanıt kodunu {200 – 599} belirtir. Bu örnekte:

  - Yüzde 95'ten büyükse, 500 HTTP yanıt kodu döndürülür.

  - Yüzde veya 70 ile 95 arasındaysa, 350 döndürülür.

  - Aksi takdirde, 200 döndürülür.

Hizmet durumu durumu, XML gibi `https://contoso:81/Service1?health` bir sorgu dizesi belirterek HTML'de `https://contoso:81/Service1?health&Xml`görüntülenebilir. Gibi `https://contoso:81/Service1?health&NoContent` bir sorgu dizesi boş bir HTML sayfasını döndürür.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Yüksek DPI geliştirmeleri**

.NET Framework 4.8'de WPF, Per-Monitor V2 DPI Bilinirliği ve Karma ModLU DPI ölçeklendirmesi için destek ekler. Yüksek DPI geliştirme hakkında ek bilgi için [Windows'da Yüksek DPI Masaüstü Uygulama Geliştirme'ye](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) bakın.

.NET Framework 4.8, Karma Mod DPI ölçeklemeişlemini destekleyen platformlarda Yüksek DPI WPF uygulamalarında barındırılan HWND'ler ve Windows Formlar ara çalışması için desteği artırır (Windows 10 Nisan 2018 Güncelleştirmesi'nden başlayarak). Barındırılan HWND'ler veya Windows Formları denetimleri [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) ve [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext)çağırarak Karışık Mod DPI ölçekli pencereler olarak oluşturulduğunda, bir Per-Monitor V2 WPF uygulamasında barındırılabilir ve uygun şekilde boyutlandırılır ve ölçeklendirilir. Bu tür barındırılan içerik yerel DPI'da işlenmez; bunun yerine, işletim sistemi barındırılan içeriği uygun boyuta ölçeklendiriyor. Per-Monitor v2 DPI bilinirlik modu desteği, WPF denetimlerinin yüksek DPI uygulamasında yerel bir pencerede barındırılmasına (örneğin, ebeveynli) izin verir.

Karışık Mod yüksek DPI ölçekleme desteği etkinleştirmek için, aşağıdaki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarları uygulama yapılandırma dosyası ayarlayabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Ortak dil çalışma zamanı

.NET Framework 4.8'deki çalışma süresi aşağıdaki değişiklikleri ve iyileştirmeleri içerir:

**JIT derleyicisi için iyileştirmeler**. .NET Framework 4.8'deki Just-in-time (JIT) derleyicisi ,NET Core 2.1'deki JIT derleyicisini temel adatır. .NET Core 2.1 JIT derleyicisine yapılan optimizasyonların ve tüm hata düzeltmelerinin çoğu .NET Framework 4.8 JIT derleyicisine dahildir.

**NGEN iyileştirmeler**. Çalışma süresi, NGEN görüntülerinden eşlenen verilerin bellekte yerleşik olmaması için [Yerel Görüntü Üreteci](../tools/ngen-exe-native-image-generator.md) (NGEN) görüntüleri için bellek yönetimini geliştirmiştir. Bu, yürütülecek belleği değiştirerek rasgele kod yürütmeye çalışan saldırıların kullanabileceği yüzey alanını azaltır.

**Tüm derlemeler için antimalware tarama**. .NET Framework'ün önceki sürümlerinde, çalışma zamanı, Windows Defender veya üçüncü taraf kötü amaçlı yazılımdan koruma yazılımını kullanarak diskten yüklenen tüm derlemeleri tarar. Ancak, <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> yöntem gibi diğer kaynaklardan yüklenen derlemeler taranır ve algılanmayan kötü amaçlı yazılımlar içerebilir. Windows 10'da çalışan .NET Framework 4.8 ile başlayan çalışma zamanı, kötü amaçlı yazılımdan koruma çözümleriyle kötü [amaçlı yazılımdan koruma arabirimini (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal)uygulayan bir taramaya neden olur.

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>.NET Framework 4.7.2'deki yenilikler

.NET Framework 4.7.2 aşağıdaki alanlarda yeni özellikler içerir:

- [Taban sınıflar](#core-472)
- [ASP.NET](#asp-net472)
- [Ağ](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

.NET Framework 4.7.2'de devam eden bir odak noktası, bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sunmasına olanak tanıyan gelişmiş erişilebilirliktir. .NET Framework 4.7.2'deki erişilebilirlik geliştirmeleri hakkında bilgi için [.NET Framework'de erişilebilirlikte yenilikler](whats-new-in-accessibility.md)egörebilirsiniz.

<a name="core-472" />

#### <a name="base-classes"></a>Temel sınıflar

.NET Framework 4.7.2 çok sayıda şifreleme geliştirmesi, ZIP arşivleri için daha iyi dekompresyon desteği ve ek toplama API'leri sunar.

**RsA yeni aşırı yükleri. Oluştur ve DSA. Oluşturmak**

Ve <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> yöntemler, yeni <xref:System.Security.Cryptography.DSA> veya <xref:System.Security.Cryptography.RSA> anahtarı anında alırken anahtar parametreleri sağlamanıza izin sağlar. Aşağıdaki gibi kodu değiştirmenize izin verirler:

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
```

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

bu gibi kod ile:

```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
```

```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

Ve <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> yöntemler, belirli <xref:System.Security.Cryptography.DSA> bir <xref:System.Security.Cryptography.RSA> anahtar boyutuna sahip yeni veya anahtarlar oluşturmanıza izin sağlar. Örnek:

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
```

```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
```

**Rfc2898DeriveBayt yapıcılar karma algoritma adı kabul**

Sınıfın, <xref:System.Security.Cryptography.Rfc2898DeriveBytes> anahtarları türeterken kullanmak <xref:System.Security.Cryptography.HashAlgorithmName> üzere Kullanılacak HMAC algoritmasını tanımlayan bir parametreye sahip üç yeni oluşturucusu vardır. Bunun yerine SHA-1 kullanarak, geliştiriciler sha-256 gibi sha-2 tabanlı HMAC kullanmanız gerekir, aşağıdaki örnekte gösterildiği gibi:

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt,
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize,
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
}
```

```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer,
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function
```

**Geçici anahtarlar için destek**

PFX alma işlemi, sabit sürücüyü atlayarak özel anahtarları doğrudan bellekten yükleyebilir.Yeni <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> bayrak bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> oluşturucuda veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> yöntemin aşırı yüklerinden birinde belirtildiğinde, özel anahtarlar geçici anahtarlar olarak yüklenir. Bu, anahtarların diskte görünmesini önler. Ancak:

- Anahtarlar diske kalıcı olmadığından, bu bayrakla yüklenen sertifikalar X509Store'a eklemek için iyi adaylar değildir.

- Bu şekilde yüklenen anahtarlar hemen hemen her zaman Windows CNG üzerinden yüklenir. Bu nedenle, arayanlar ın sertifika gibi uzantı yöntemlerini arayarak özel anahtara erişmesi [gerekir. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). Özellik <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> çalışmıyor.

- Eski <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> özellik sertifikalarla çalışmadığından, geliştiriciler geçici anahtarlara geçmeden önce zorlu sınamalar gerçekleştirmelidir.

**PKCS#10 sertifika imzalama isteklerinin ve X.509 ortak anahtar sertifikalarının programlı oluşturulması**

.NET Framework 4.7.2 ile başlayarak, iş yükleri sertifika isteği oluşturmanın varolan takım oluşturmaya olanak tanıyan sertifika imzalama istekleri (CSR) oluşturabilir. Bu, test senaryolarında sık sık yararlıdır.

Daha fazla bilgi ve kod örnekleri için [,.NET blogunda](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"PKCS#10 sertifika imzalama isteklerinin ve X.509 ortak anahtar sertifikalarının programlı oluşturulması" bölümüne bakın.

**Yeni SignerInfo üyeleri**

.NET Framework 4.7.2 ile <xref:System.Security.Cryptography.Pkcs.SignerInfo> başlayarak, sınıf imza hakkında daha fazla bilgi ortaya çıkarır. İmzalayıcı tarafından kullanılan <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> imza algoritmasını belirlemek için özelliğin değerini alabilirsiniz. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>bu imzalayan için şifreleme imzasının bir kopyasını almak için çağrılabilir.

**CryptoStream imha edildikten sonra sarılmış bir akışı açık bırakma**

.NET Framework 4.7.2 ile <xref:System.Security.Cryptography.CryptoStream> başlayarak, sınıf sarılmış <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> akışı kapatmamaya izin veren ek bir oluşturucuya sahiptir.Paketlenmiş akışı <xref:System.Security.Cryptography.CryptoStream> örnek bertaraf edildikten sonra açık bırakmak <xref:System.Security.Cryptography.CryptoStream> için, yeni oluşturucuyu aşağıdaki gibi arayın:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**DeflateStream'de dekompresyon değişiklikleri**

.NET Framework 4.7.2 ile başlayarak, <xref:System.IO.Compression.DeflateStream> sınıfta dekompresyon işlemlerinin uygulanması varsayılan olarak yerel Windows API'lerini kullanacak şekilde değiştirildi. Genellikle, bu önemli bir performans artışı ile sonuçlanır.

.NET Framework 4.7.2'yi hedefleyen uygulamalar için varsayılan olarak Windows API'leri kullanılarak dekompresyon desteği sağlanır. .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 altında çalışan uygulamalar, uygulama yapılandırma dosyasına aşağıdaki [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu davranışı seçebilir:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Ek toplama API'leri**

.NET Framework 4.7.2, bu <xref:System.Collections.Generic.SortedSet%601> tür ve <xref:System.Collections.Generic.HashSet%601> türlere bir dizi yeni API ekler. Bunlar:

- `TryGetValue`diğer toplama türlerinde kullanılan try deseni bu iki türe genişleten yöntemler. Yöntemler şunlardır:

  - [kamu bool HashSet\<T>. TryGetValue(T equalValue, çıkış T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [kamu bool SortedSet\<T>. TryGetValue(T equalValue, çıkış T actualValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*`bir koleksiyonu bir: <xref:System.Collections.Generic.HashSet%601>

  - [kamu statik HashSet\<TSource>\<ToHashSet TSource>\<(Bu Ayrılmaz TSource> kaynak)](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [kamu\<statik HashSet TSource>\<ToHashSet TSource>\<(Bu Ayrılmaz TSource>\<kaynak, IEqualityComparer TSource> comparer)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Koleksiyonun kapasitesini ayarlamanıza izin veren yeni <xref:System.Collections.Generic.HashSet%601> yapıcılar, önceden boyutu bildiğinizde <xref:System.Collections.Generic.HashSet%601> performans avantajı sağlar:

  - [kamu HashSet(int kapasitesi)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
  - [kamu HashSet(int kapasitesi, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

Sınıf, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sözlükten bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> değer <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> almak veya bulunamazsa eklemek ve sözlükte bir değer eklemek veya zaten varsa güncelleştirmek için yeni aşırı yüklemeler ve yöntemler içerir.

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a>ASP.NET

**Web Formlarında bağımlılık enjeksiyonu desteği**

[Bağımlılık enjeksiyonu (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) nesneleri ve bunların bağımlılıklarını birbirinden ayırarak, yalnızca bağımlılık değiştiği için nesnenin kodunun değiştirilmesine gerek kalmamasını engeller. .NET Framework 4.7.2'yi hedefleyen ASP.NET uygulamalar geliştirirken şunları yapabilirsiniz:

- İşleyici [ve modüllerde,](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)) [Sayfa örneklerinde](xref:System.Web.UI.Page)ve ASP.NET web uygulama projelerinin [kullanıcı denetimlerinde](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ayarlayıcı tabanlı, arayüz tabanlı ve yapıcı tabanlı enjeksiyon kullanın.

- [Işleyicive modüllerde,](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)) [Sayfa örneklerinde](xref:System.Web.UI.Page)ve ASP.NET web sitesi projelerinin [kullanıcı denetimlerinde](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ayarlayıcı tabanlı ve arayüz tabanlı enjeksiyon kullanın.

- Farklı bağımlılık enjeksiyon çerçevelerini takın.

**Aynı site çerezleri için destek**

[SameSite,](https://tools.ietf.org/html/draft-west-first-party-cookies-07) bir tarayıcının site ler arası istekle birlikte çerez göndermesini engeller. .NET Framework 4.7.2 <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> değeri numaralandırma <xref:System.Web.SameSiteMode?displayProperty=nameWithType> üyesi olan bir özellik ekler. Değeri <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> veya <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET ayarlı çerez üstbilgiözözek. `SameSite` SameSite desteği nesneler, tanımlama bilgileri <xref:System.Web.HttpCookie> ve <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> nesneler için de geçerlidir.

SameSite'yi bir <xref:System.Web.HttpCookie> nesne için aşağıdaki gibi ayarlayabilirsiniz:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Ayrıca web.config dosyasını değiştirerek uygulama düzeyinde SameSite çerezleri yapılandırabilirsiniz:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

Web config dosyasını değiştirerek SameSite for <xref:System.Web.Security.FormsAuthentication> ve <xref:System.Web.SessionState> cookies ekleyebilirsiniz:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Ağ

**HttpClientHandler özelliklerinin uygulanması**

.NET Framework 4.7.1 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> sınıfa sekiz özellik ekledi. Ancak, iki <xref:System.PlatformNotSupportedException>attı . .NET Framework 4.7.2 şimdi bu özellikler için bir uygulama sağlar. Özellikler şunlardır:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Azure Active Directory Evrensel Kimlik Doğrulaması ve Çok Faktörlü Kimlik Doğrulaması desteği**

Artan uyumluluk ve güvenlik talepleri, birçok müşterinin çok faktörlü kimlik doğrulaması (MFA) kullanmasını gerektirir. Buna ek olarak, geçerli en iyi uygulamalar doğrudan bağlantı dizeleri kullanıcı parolaları da dahil olmak üzere cesaretini. Bu değişiklikleri desteklemek için .NET Framework 4.7.2, MFA ve [Azure AD Kimlik Doğrulaması'nı](/azure/sql-database/sql-database-aad-authentication-configure)desteklemek için varolan "Kimlik Doğrulama" anahtar sözcüğü için yeni bir değer olan "Active Directory Interactive" ekleyerek [SQLClient bağlantı dizelerini](xref:System.Data.SqlClient.SqlConnection.ConnectionString) genişletir. Yeni etkileşimli yöntem, yerel ve federe Azure AD kullanıcılarının yanı sıra Azure AD konuk kullanıcılarını da destekler. Bu yöntem kullanıldığında, Azure AD tarafından dayatılan MFA kimlik doğrulaması SQL veritabanları için desteklenir. Buna ek olarak, kimlik doğrulama işlemi güvenlik en iyi uygulamalarına uymak için bir kullanıcı parolası ister.

.NET Framework'ün önceki sürümlerinde, SQL bağlantısı <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> yalnızca seçenekleri ve seçenekleri desteklenebildi. Bunların her ikisi de MFA'yı desteklemeyen etkileşimli olmayan [ADAL protokolünün](/azure/active-directory/develop/active-directory-authentication-libraries)bir parçasıdır. Yeni <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> seçenekle, SQL bağlantısı MFA'nın yanı sıra kullanıcıların bağlantı dizesinde parolaları kalıcı hale getirilmeden etkileşimli olarak kullanıcı parolalarını girmelerine olanak tanıyan mevcut kimlik doğrulama yöntemlerini (parola ve tümleşik kimlik doğrulama) destekler.

Daha fazla bilgi ve örnek için [,.NET blogundaki](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"SQL -- Azure AD Evrensel ve Çok Faktörlü Kimlik Doğrulama Desteği" başlıklı bakın.

**Her Zaman Şifrelenmiş sürüm 2 desteği**

NET Framework 4.7.2, her zaman şifrelenmiş enklav tabanlı destekler ekler. Always Encrypted'ın özgün sürümü, şifreleme anahtarlarının istemciden asla ayrılmadığı istemci tarafı şifreleme teknolojisidir. Enklav tabanlı Her Zaman Şifrelenmiş'te istemci, şifreleme anahtarlarını isteğe bağlı olarak, SQL Server'ın bir parçası olarak kabul edilebilen ancak SQL Server kodunun kurcalayamayacağı güvenli bir işlem varlığı olan güvenli bir enklava gönderebilir. Her Zaman Şifrelenmiş yerleşim bölgesini desteklemek için,.NET Framework 4.7.2 <xref:System.Data.SqlClient> ad alanına aşağıdaki türleri ve üyeleri ekler:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, enklav tabanlı Her Zaman Şifreli uri belirtir.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, tüm enklav sağlayıcılarıtüretildiği soyut bir sınıftır.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, hangi belirli bir enklav oturumu için devlet kapsüller.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, belirli bir Attestation Protokolü yürütmek için gerekli bilgileri almak için SQL Server tarafından kullanılan attestation parametrelerini sağlar.

Uygulama yapılandırma dosyası daha sonra enklav <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> sağlayıcısı için işlevselliği sağlayan soyut sınıfın somut bir uygulama belirtir. Örnek:

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

Her Zaman Şifrelenmiş enklav tabanlı temel akışı:

1. Kullanıcı, enklav tabanlı Her Zaman Şifrelenmiş'i destekleyen SQL Server'a AlwaysEncrypted bağlantısı oluşturur. Sürücü, doğru yerleşim bölgesine bağlandığından emin olmak için attestation hizmetiyle bağlantı kurar.

1. Enklav kanıtlandıktan sonra, sürücü SQL Server'da barındırılan güvenli enklavile güvenli bir kanal kurar.

1. Sürücü, istemci tarafından yetkilendirilen şifreleme anahtarlarını SQL bağlantısı süresince güvenli enklavla paylaşır.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Kaynağa Göre KaynakDictionaries bulma**

.NET Framework 4.7.2 ile başlayarak, <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> bir tanı asistanı belirli bir kaynak Uri oluşturulan yerini bulabilir.(Bu özellik üretim uygulamaları tarafından değil, tanı asistanları tarafından kullanılmak üzeredir.) Visual Studio'nun "Edit-and-Continue" tesisi gibi bir tanı asistanı, kullanıcının, değişikliklerin çalışan uygulamaya uygulanması amacıyla bir Kaynak Sözlüğü'nü yönetmesine olanak tanır. Bunu başarmanın bir adımı, çalışan uygulamanın düzenlenen sözlükten oluşturduğu tüm KaynakDictions'ları bulmaktır. Örneğin, bir uygulama, içeriği belirli bir kaynak URI'den kopyalanan bir Kaynak Sözlüğü'nü bildirebilir:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

*MyRD.xaml'da* orijinal biçimlendirmeyi ayarlayan bir tanı asistanı, sözlüğü bulmak için yeni özelliği kullanabilir.Özellik yeni bir statik yöntem ile <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>uygulanır. Tanıasistanı, aşağıdaki kodda gösterildiği gibi, özgün biçimlendirmeyi tanımlayan mutlak bir Uri kullanarak yeni yöntemi çağırır:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Yöntem etkinleştirilmedikçe ve <xref:System.Windows.Diagnostics.VisualDiagnostics> [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ortam değişkeni ayarlı olmadıkça boş bir sayısal akçe döndürür.

**Kaynak BulmaSözlük sahipleri**

.NET Framework 4.7.2 ile başlayarak, bir tanı <xref:Windows.UI.Xaml.ResourceDictionary>asistanı belirli bir .(Bu özellik üretim uygulamaları tarafından değil, tanı asistanları tarafından kullanılmak üzeredir.) Bir <xref:Windows.UI.Xaml.ResourceDictionary>değişiklik yapıldığında , WPF değişiklikten etkilenebilecek tüm [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvurularını otomatik olarak bulur.

Visual Studio'nun "Edit-and-Continue" tesisi gibi bir tanı [asistanı, Statik Kaynak](../wpf/advanced/staticresource-markup-extension.md) başvurularını işlemek için bunu genişletmek isteyebilir. Bu işlemin ilk adımı sözlük sahiplerini bulmaktır; diğer bir deyişle, özelliği sözlüğe atıfta bulunan `Resources` tüm nesneleri bulmak için <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> (doğrudan veya dolaylı olarak özellik üzerinden). <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> Sınıfa uygulanan üç yeni statik yöntem, bir özelliği olan `Resources` temel türlerin her biri için bir, bu adımı destekler:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Bu yöntemler etkinleştirilmedikçe ve <xref:System.Windows.Diagnostics.VisualDiagnostics> ortam değişkeni [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ayarlınca boş bir sayısal adedi döndürün.

**StaticResource başvurularını bulma**

Bir tanılama yardımcısı artık [statik](../wpf/advanced/staticresource-markup-extension.md) kaynak başvurusu çözüldüğünde bir bildirim alabilir.(Özellik, üretim uygulamaları tarafından değil, tanı asistanları tarafından kullanılmak üzeredir.) Visual Studio'nun "Edit-and-Continue" tesisi gibi bir <xref:Windows.UI.Xaml.ResourceDictionary> tanı asistanı, bir kaynağın değeri değiştiğinde tüm kullanımlarını güncelleştirmek isteyebilir. WPF bunu [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvuruları için otomatik olarak yapar, ancak [bunu statik](../wpf/advanced/staticresource-markup-extension.md) kaynak başvuruları için kasıtlı olarak yapmaz. .NET Framework 4.7.2 ile başlayarak, tanılama asistanı statik kaynağın bu kullanımlarını bulmak için bu bildirimleri kullanabilir.

Bildirim yeni <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> olay tarafından uygulanır:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Bu olay, çalışma zamanı statik [kaynak](../wpf/advanced/staticresource-markup-extension.md) başvurusu çözdüğünde yükseltilir.Bağımsız <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> değişkenler çözünürlüğü açıklar ve Statik [Kaynak](../wpf/advanced/staticresource-markup-extension.md) başvuruyu <xref:Windows.UI.Xaml.ResourceDictionary> ve çözünürlük için kullanılan ve anahtar da barındıran nesneyi ve özelliği gösterir:

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

Olay etkinleştirilmedikçe ve `add` ortam <xref:System.Windows.Diagnostics.VisualDiagnostics> değişkeni [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ayarlanmadıkça olay yükseltilmez (ve erişime giren yoksayılır).

#### <a name="clickonce"></a>ClickOnce

Windows Forms, Windows Presentation Foundation (WPF) ve Office için Visual Studio Tools (VSTO) için HDPI'ye duyarlı uygulamalar ClickOnce kullanılarak dağıtılabilir. Uygulama bildiriminde aşağıdaki giriş bulunursa, dağıtım .NET Framework 4.7.2 altında başarılı olur:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Windows Forms uygulaması için, uygulama bildirimi yerine uygulama yapılandırma dosyasında DPI bilinirliği ayarlamanın önceki geçici çözümünün ClickOnce dağıtımının başarılı olması için artık gerekli değildir.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>.NET Framework 4.7.1'deki yenilikler

.NET Framework 4.7.1 aşağıdaki alanlarda yeni özellikler içerir:

- [Taban sınıflar](#core471)
- [Ortak dil çalışma zamanı (CLR)](#clr)
- [Ağ](#net471)
- [ASP.NET](#asp-net471)

Buna ek olarak, .NET Framework 4.7.1'deki önemli bir odak noktası, bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sağlamasına olanak tanıyan gelişmiş erişilebilirliktir. .NET Framework 4.7.1'deki erişilebilirlik geliştirmeleri hakkında bilgi için [.NET Framework'de erişilebilirlikte yenilikler](whats-new-in-accessibility.md)egörebilirsiniz.

<a name="core471" />

#### <a name="base-classes"></a>Temel sınıflar

**.NET Standard 2.0 desteği**

[.NET Standard,](../../standard/net-standard.md) standardın bu sürümünü destekleyen her .NET uygulamasında bulunması gereken bir API kümesi tanımlar. .NET Framework 4.7.1 .NET Standard 2.0'ı tam olarak destekler ve .NET Standart 2.0'da tanımlanan ve .NET Framework 4.6.1, 4.6.2 ve 4.7'den eksik olan [yaklaşık 200 API](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) ekler. (.NET Framework'ün bu sürümlerinin .NET Standard 2.0'ı yalnızca hedef sistemde ek .NET Standart destek dosyaları da dağıtılırsa desteklediğini unutmayın.) Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "BCL - .NET Standart 2.0 Desteği" başlıklı yazıya bakın.

**Yapılandırma oluşturucuları için destek**

Yapılandırma oluşturucuları, geliştiricilerin çalışma zamanında uygulamalar için dinamik olarak yapılandırma ayarları enjekte etmesine ve oluşturmasına olanak tanır. Özel yapılandırma oluşturucuları, yapılandırma bölümündeki varolan verileri değiştirmek veya tamamen sıfırdan bir yapılandırma bölümü oluşturmak için kullanılabilir. Yapılandırma oluşturucuları olmadan,.config dosyaları statiktir ve ayarları uygulama başlatılmadan bir süre önce tanımlanır.

Özel bir yapılandırma oluşturucu oluşturmak için, soyut <xref:System.Configuration.ConfigurationBuilder> sınıftan oluşturucu türetmek ve onun <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> ve <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>geçersiz kılmak. Ayrıca .config dosyanızda oluşturucularınızı tanımlarsınız. Daha fazla bilgi için [.NET Framework 4.7.1 ASP.NET ve Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisindeki "Yapılandırma Oluşturucuları" bölümüne bakın.

**Çalışma zamanı özellik algılama**

Sınıf, <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> önceden tanımlanmış bir özelliğin derleme zamanında veya çalışma zamanında belirli bir .NET uygulamasında desteklenip desteklenmediğini belirlemek için bir mekanizma sağlar. Derleme zamanında, bir derleyici özelliğin desteklenip desteklenmediğini belirlemek için belirli bir alanın var olup olmadığını denetleyebilir; eğer öyleyse, bu özellik yararlanır kod yatabilir. Çalışma zamanında, bir uygulama <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> çalışma zamanında kod yaymadan önce yöntemi çağırabilir. Daha fazla bilgi için çalışma [zamanı tarafından desteklenen özellikleri açıklamak için yardımcı ekle yöntemine](https://github.com/dotnet/corefx/issues/17116)bakın.

**Değer tuple türleri serileştirilebilir**

.NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> ile başlayarak ve ilişkili genel türleri [serileştirilebilir](xref:System.SerializableAttribute)olarak işaretlenir, bu da ikili serileştirmeyi sağlar. Bu, tuple türlerini daha <xref:System.Tuple%603> kolay <xref:System.Tuple%604>değer vermek gibi ve , geçiş yapan Tuple türlerini kolaylaştırmalıdır. Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "Derleyici -- ValueTuple Serializable"a bakın.

**Salt okunur başvurular için destek**

.NET Framework 4.7.1 <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>ekler. Bu öznitelik, yalnızca okunan ref return türleri veya parametreleri olan üyeleri işaretlemek için dil derleyicileri tarafından kullanılır. Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "Derleyici -- ReadOnlyReferences desteği" başlıklı yazıya bakın. Ref iade değerleri hakkında bilgi için ref [iade değerleri ve ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) ve Ref dönüş değerleri [(Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md)bakın.

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Ortak dil çalışma zamanı (CLR)

**Çöp toplama performans iyileştirmeleri**

.NET Framework 4.7.1'deki çöp toplama (GC) değişiklikleri, özellikle büyük nesne yığını (LOH) ayırmaları için genel performansı artırır. .NET Framework 4.7.1'de, küçük nesne yığını (SOH) ve LOH ayırmaları için ayrı kilitler kullanılır ve bu da arka plan GC'nin SOH'u süpürmesinde LOH ayırmalarının gerçekleşmesine olanak tanır. Sonuç olarak, çok sayıda LOH ayırması yapan uygulamalarda ayırma kilidi çekişmesinde bir azalma ve geliştirilmiş performans görünmelidir. Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisindeki "Çalışma Zamanı -- GC Performans Geliştirmeleri" bölümüne bakın.

<a name="net471"/>

#### <a name="networking"></a>Ağ

**Message.HashAlgorithm için SHA-2 desteği**

.NET Framework 4.7 ve önceki <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> sürümlerde, <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> özellik <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> yalnızca ve yalnızca değerleri desteklenir. .NET Framework 4.7.1 <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>ile başlayarak ve aynı zamanda <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> desteklenir. Bu değerin <xref:System.Messaging.Message> gerçekten kullanılıp kullanılmadığı MSMQ'ya bağlıdır, çünkü örneğin kendisi karma yapmaz, ancak değerleri yalnızca MSMQ'ya aktarAbilir. Daha fazla bilgi için [,.NET Framework 4.7.1 ASP.NET ve Configuration özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisindeki "Message.HashAlgorithm için SHA-2 desteği" bölümüne bakın.

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**ASP.NET uygulamalarında yürütme adımları**

ASP.NET, 23 olay içeren önceden tanımlanmış bir ardışık ardışık işlemde istekleri işler. ASP.NET, her olay işleyicisi bir yürütme adımı olarak yürütür. .NET Framework 4.7'ye kadar olan ASP.NET sürümlerinde, ASP.NET, yerel ve yönetilen iş parçacıkları arasında geçiş nedeniyle yürütme bağlamını akıtamaz. Bunun yerine, ASP.NET seçici <xref:System.Web.HttpContext>olarak yalnızca . .NET Framework 4.7.1 <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> ile başlayan yöntem, modüllerin ortam verilerini geri yüklemesine de olanak tanır. Bu özellik, örneğin uygulamanın yürütme akışını önemseyen izleme, profil oluşturma, tanılama veya işlemlerle ilgili kitaplıkları hedeflemeye yöneliktir. Daha fazla bilgi için [.NET Framework 4.7.1 ASP.NET ve Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinde yer alan "ASP.NET Yürütme Adımı Özelliği"ne bakın.

**ASP.NET HttpCookie ayrışma**

.NET Framework 4.7.1, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>bir dizeden bir <xref:System.Web.HttpCookie> nesne oluşturmak ve son kullanma tarihi ve yol gibi çerez değerlerini doğru bir şekilde atamak için standartlaştırılmış bir yol sağlayan yeni bir yöntem içerir. Daha fazla bilgi için [.NET Framework 4.7.1 ASP.NET ve Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinde "ASP.NET HttpCookie ayrıştırma" başlıklı yazıya bakın.

**ASP.NET formlar kimlik doğrulama kimlik bilgileri için SHA-2 karma seçenekleri**

.NET Framework 4.7 ve önceki sürümlerde, ASP.NET geliştiricilerin MD5 veya SHA1 kullanarak yapılandırma dosyalarında hashed parolalarla kullanıcı kimlik bilgilerini depolamasına izin verdi. .NET Framework 4.7.1 ile başlayan ASP.NET, SHA256, SHA384 ve SHA512 gibi yeni güvenli SHA-2 karma seçeneklerini de destekler. SHA1 varsayılan olarak kalır ve varsayılan olmayan karma algoritması web yapılandırma dosyasında tanımlanabilir. Örnek:

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47" />

## <a name="whats-new-in-net-framework-47"></a>.NET Framework 4.7'deki yenilikler

.NET Framework 4.7 aşağıdaki alanlarda yeni özellikler içerir:

- [Taban sınıflar](#Core47)
- [Ağ](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

.NET Framework 4.7'ye eklenen yeni API'lerin listesi için GitHub'daki [.NET Framework 4.7 API Değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) bölümüne bakın. .NET Framework 4.7'deki özellik geliştirmeleri ve hata düzeltmeleri listesi için [bkz.](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) Daha fazla bilgi için [bkz.](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/)

<a name="Core47" />

#### <a name="base-classes"></a>Temel sınıflar

.NET Framework 4.7 aşağıdakiler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ile serileştirmeyi geliştirir:

**Eliptik Eğri Şifrelemesi (ECC) ile geliştirilmiş işlevsellik***

.NET Framework 4.7'de, `ImportParameters(ECParameters)` bir <xref:System.Security.Cryptography.ECDsa> <xref:System.Security.Cryptography.ECDiffieHellman> nesnenin zaten kurulmuş bir anahtarı temsil etmesine izin vermek için ve sınıflara yöntemler eklendi. Açık `ExportParameters(Boolean)` eğri parametreleri kullanılarak anahtarı dışa aktarmak için bir yöntem de eklendi.

.NET Framework 4.7 ayrıca ek eğriler (Brainpool eğrisi paketi dahil) için destek ekler ve yeni <xref:System.Security.Cryptography.ECDsa.Create%2A> ve <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> fabrika yöntemleri yle oluşturma kolaylığı için önceden tanımlanmış tanımlar ekler.

[GitHub'da .NET Framework 4.7 şifreleme geliştirmelerine bir örnek](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) görebilirsiniz.

**DataContractJsonSerializer tarafından kontrol karakterleri için daha iyi destek**

.NET Framework 4.7'de, kontrol karakterlerini <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript 6 standardına uygun olarak serihale sağlar. Bu davranış, .NET Framework 4.7'yi hedefleyen uygulamalar için varsayılan olarak etkinleştirilir ve .NET Framework 4.7 altında çalışan ancak .NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için bir tercih özelliğidir. Daha fazla bilgi için bkz: [.NET Framework 4.7'deki Değişiklikleri Yeniden Hedefleme.](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

<a name="net47" />

#### <a name="networking"></a>Ağ

.NET Framework 4.7 ağla ilgili aşağıdaki özelliği ekler:

**TLS protokolleri için varsayılan işletim sistemi desteği***

HTTP, FTP ve SMTP gibi bileşenler tarafından <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve yukarı yığında kullanılan TLS yığını, geliştiricilerin işletim sistemi tarafından desteklenen varsayılan TLS protokollerini kullanmasına olanak tanır. Geliştiriciler artık bir TLS sürümü sabit kod gerekir.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

.NET Framework 4.7'de ASP.NET aşağıdaki yeni özellikleri içerir:

**Nesne Önbellek Genişletilebilirlik**

ASP.NET,.NET Framework 4.7 ile başlayarak, geliştiricilerin bellek içi nesne önbelleğe alma ve bellek izleme için varsayılan ASP.NET uygulamalarını değiştirmelerine olanak tanıyan yeni bir API kümesi ekler. ASP.NET uygulaması yeterli değilse, geliştiriciler artık aşağıdaki üç bileşenden herhangi birini değiştirebilir:

- **Nesne Önbellek Deposu**. Geliştiriciler, yeni önbellek sağlayıcıları yapılandırma bölümünü kullanarak, yeni **ICacheStoreProvider** arabirimini kullanarak ASP.NET bir uygulama için nesne önbelleğinin yeni uygulamalarını takabilir.

- **Bellek izleme**. ASP.NET'daki varsayılan bellek monitörü, işlem için yapılandırılan özel bayt sınırına yakın çalıştıklarında veya makinenin kullanılabilir toplam fiziksel RAM'i düşük olduğunda uygulamaları haber eder. Bu sınırlar yaklaştığında, bildirimler ateşlenir. Bazı uygulamalariçin bildirimler, yararlı reaksiyonlara izin vermek için yapılandırılan sınırlara çok yakın ateşlenir. Geliştiriciler artık <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> özelliği kullanarak varsayılan değiştirmek için kendi bellek monitörleri yazabilirsiniz.

- **Bellek Limit Reaksiyonları**. Varsayılan olarak, ASP.NET nesne önbelleğini kırpmaya <xref:System.GC.Collect%2A?displayProperty=nameWithType> çalışır ve özel bayt işlem sınırı yaklaştığında düzenli olarak arama yapılır. Bazı uygulamalariçin, yapılan aramaların <xref:System.GC.Collect%2A?displayProperty=nameWithType> sıklığı veya kırpılan önbellek miktarı verimsizdir. Geliştiriciler artık Uygulamanın bellek monitörüne **IObserver** uygulamalarını abone ederek varsayılan davranışı değiştirebilir veya tamamlayabilir.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF) aşağıdaki özellikleri ve değişiklikleri ekler:

**Varsayılan ileti güvenlik ayarlarını TLS 1.1 veya TLS 1.2 olarak yapılandırabilme**

.NET Framework 4.7 ile başlayan WCF, varsayılan ileti güvenlik protokolü olarak SSL 3.0 ve TSL 1.0'a ek olarak TSL 1.1 veya TLS 1.2 yapılandırmanızı sağlar. Bu bir opt-in ayarıdır; etkinleştirmek için, uygulama yapılandırma dosyanıza aşağıdaki girişi eklemeniz gerekir:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**WCF uygulamalarının ve WCF serileştirmesinin geliştirilmiş güvenilirliği**

WCF, yarış koşullarını ortadan kaldıran ve performansı ve serileştirme seçeneklerinin güvenilirliğini artıran bir dizi kod değişikliği içerir. Bunlar:

- **SocketConnection.BeginRead** ve **SocketConnection.Read**aramalarında asynchronous ve senkron kodu karıştırmak için daha iyi destek.
- **SharedConnectionListener** ve **DuplexChannelBinder**ile bağlantıyı iptal ederken geliştirilmiş güvenilirlik.
- Yöntemi ararken serileştirme işlemlerinin <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> güvenilirliği artırıldı.
- **ChannelSynchronizer.RemoveWaiter** yöntemini arayarak bir garsonu kaldırırken daha iyi güvenilirlik.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

.NET Framework 4.7'de, Windows Forms yüksek DPI monitörleri için desteği artırır.

**Yüksek DPI desteği**

.NET Framework 4.7'yi hedefleyen uygulamalardan başlayarak,.NET Framework, Windows Forms uygulamaları için yüksek DPI ve dinamik DPI desteği ne sahiptir. Yüksek DPI desteği, yüksek DPI monitörlerde formların ve denetimlerin düzenini ve görünümünü geliştirir. Dinamik DPI, kullanıcı çalışan bir uygulamanın DPI veya ekran ölçek faktörünün değiştirdiğinde formların ve denetimlerin düzenini ve görünümünü değiştirir.

Yüksek DPI desteği, uygulama yapılandırma dosyanızdaki [ \<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) bölümünü tanımlayarak yapılandırdığınız bir tercih özelliğidir. Windows Forms uygulamanıza yüksek DPI desteği ve dinamik DPI desteği ekleme hakkında daha fazla bilgi için [Windows Formlarında Yüksek DPI Desteği'ne](../winforms/high-dpi-support-in-windows-forms.md)bakın.

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.7'de WPF aşağıdaki geliştirmeleri içerir:

**Windows WM_POINTER iletilerine dayalı dokunma/kalem yığını desteği**

Artık Windows Mürekkep Hizmetleri Platformu (WISP) yerine [WM_POINTER iletilerine](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) dayalı bir dokunma/kalem yığını kullanma seçeneğiniz vardır. Bu, .NET Framework'de yer alan bir tercih özelliğidir. Daha fazla bilgi için bkz: [.NET Framework 4.7'deki Değişiklikleri Yeniden Hedefleme.](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)

**WPF yazdırma API'leri için yeni uygulama**

WPF'nin sınıftaki <xref:System.Printing.PrintQueue?displayProperty=nameWithType> yazdırma API'leri, amortismana kalanmış [XPS Print API](/windows/desktop/printdocs/xps-printing)yerine Windows [Print Document Package API'yi](/windows/desktop/printdocs/tailored-app-printing-api) çağırır. Bu değişikliğin uygulama uyumluluğu üzerindeki etkisi [için](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)bkz.

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>.NET Framework 4.6.2'deki yenilikler

.NET Framework 4.6.2 aşağıdaki alanlarda yeni özellikler içerir:

- [ASP.NET](#ASPNET462)

- [Karakter kategorileri](#Strings)

- [Şifreleme](#Crypto462)

- [Sqlclient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Windows Formlarını ve WPF uygulamalarını UWP uygulamalarına dönüştürme](#UWPConvert)

- [Hata ayıklama iyileştirmeleri](#Debug462)

.NET Framework 4.6.2'ye eklenen yeni API'lerin listesi için GitHub'daki [.NET Framework 4.6.2 API Değişiklikleri'ne](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) bakın. .NET Framework 4.6.2'deki özellik geliştirmeleri ve hata düzeltmeleri listesi için [bkz.](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) Daha fazla bilgi için .NET blogunda [.NET Framework 4.6.2'yi duyurmak](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) için bkz.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

.NET Framework 4.6.2'de ASP.NET aşağıdaki geliştirmeleri içerir:

**Veri ek açıklama doğrulayıcılarında yerelleştirilmiş hata iletileri için geliştirilmiş destek**

Veri ek açıklama doğrulayıcıları, bir sınıf özelliğine bir veya daha fazla öznitelik ekleyerek doğrulama gerçekleştirmenizi sağlar. Öznitelik <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> öğesi doğrulama başarısız olursa hata iletisinin metnini tanımlar. .NET Framework 4.6.2 ile başlayarak, ASP.NET hata iletilerini yerelleştirmeyi kolaylaştırır. Hata iletileri:

1. Doğrulama <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> özniteliği sağlanmaktadır.

2. Kaynak dosyası App_LocalResources klasöründe depolanır.

3. Yerelleştirilmiş kaynaklar dosyasının `DataAnnotation.Localization.{` *adı,*`}.resx` *ad* biçimi *languageCode*`-`*ülke /regionCode* veya *languageCode*bir kültür adı dır form adı vardır.

4. Kaynağın anahtar adı öznitelik atanan <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> dize ve değeri yerelleştirilmiş hata iletisi.

Örneğin, aşağıdaki veri ek açıklama özniteliği geçersiz bir derecelendirme için varsayılan kültürün hata iletisini tanımlar.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

Daha sonra, anahtarı hata iletisi dizesi olan ve değeri yerelleştirilmiş hata iletisi olan DataAnnotation.Localization.fr.resx( Dosya `App.LocalResources` klasörde bulunmalıdır. Örneğin, yerelleştirilmiş bir Fransızca (fr) dil hata iletisinde anahtar ve değeri aşağıdakigibidir:

| Adı                                 | Değer                                     |
| ------------------------------------ | ----------------------------------------- |
| Derecelendirme 1 ile 10 arasında olmalıdır. | La not doit être entre 1 et 10 oluşur. |

 Buna ek olarak, veri ek açıklama yerelleştirme genişletilebilir. Geliştiriciler, yerelleştirme dizesini <xref:System.Web.Globalization.IStringLocalizerProvider> kaynak dosyasıdışında başka bir yerde depolamak için arabirimi uygulayarak kendi dize yerelleştirici sağlayıcısını takabilir.

 **Oturum durumu mağaza sağlayıcılarıyla async desteği**

 ASP.NET artık görev döndürme yöntemlerinin oturum durumu mağaza sağlayıcılarında kullanılmasına izin vererek ASP.NET uygulamalarının async'in ölçeklenebilirlik avantajlarından yararlanmasına olanak sağlıyor. Oturum durum deposu sağlayıcıları ile eşzamanlı işlemleri destekler ASP.NET, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>devralır <xref:System.Web.IHttpModule> ve geliştiriciler kendi oturum durumu modülü ve async oturum deposu sağlayıcıları uygulamak için izin veren yeni bir arabirim içerir. Arabirim aşağıdaki gibi tanımlanır:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 Buna ek <xref:System.Web.SessionState.SessionStateUtility> olarak, sınıf iki <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>yeni yöntem içerir ve , bu eşzamanlı işlemleri desteklemek için kullanılabilir.

 **Çıktı önbellek sağlayıcıları için async desteği**

 .NET Framework 4.6.2 ile başlayarak, görev döndürme yöntemleri, async'in ölçeklenebilirlik avantajlarını sağlamak için çıktı önbellek sağlayıcılarıyla kullanılabilir.  Bu yöntemleri uygulayan sağlayıcılar, bir web sunucusunda iş parçacığı engellemeyi azaltır ve ASP.NET bir hizmetin ölçeklenebilirliğini artırır.

 Eşzamanlı çıktı önbellek sağlayıcılarını desteklemek için aşağıdaki API'ler eklenmiştir:

- Geliştiricilerin <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> bir eşzamanlı <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> çıktı önbelleği sağlayıcısı nı uygulamasına olanak tanıyan sınıf.

- Çıktı <xref:System.Web.Caching.OutputCacheUtility> önbelleğini yapılandırmak için yardımcı yöntemler sağlayan sınıf.

- <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> Sınıfta 18 yeni yöntem. Bunlar <xref:System.Web.HttpCachePolicy.GetCacheability%2A>arasında <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>, , , , , , ve .

- <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> Sınıfta 2 yeni yöntem: <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A> <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> ve .

- <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> Sınıfta 2 yeni yöntem: <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A> <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> ve .

- <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> Sınıfta 2 yeni yöntem: <xref:System.Web.HttpCacheVaryByParams.SetParams%2A> <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> ve .

- <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> Sınıfta, <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> yöntem.

- ' <xref:System.Web.Caching.CacheDependency> <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> de, yöntem.

<a name="Strings" />

### <a name="character-categories"></a>Karakter kategorileri

.NET Framework 4.6.2'deki karakterler [Unicode Standardı, Sürüm 8.0.0'a](https://www.unicode.org/versions/Unicode8.0.0/)göre sınıflandırılır. .NET Framework 4.6 ve .NET Framework 4.6.1'de karakterler Unicode 6.3 karakter kategorilerine göre sınıflandırıldı.

Unicode 8.0 desteği, karakterlerin <xref:System.Globalization.CharUnicodeInfo> sınıfa göre sınıflandırılması ve ona dayanan tür ve yöntemlerle sınırlıdır. Bunlar <xref:System.Globalization.StringInfo> sınıf, aşırı yüklenen <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> yöntem ve .NET Framework düzenli ifade altyapısı tarafından tanınan [karakter sınıflarını](../../standard/base-types/character-classes-in-regular-expressions.md) içerir.  Karakter ve dize karşılaştırması ve sıralama bu değişiklikten etkilenmez ve altta yatan işletim sistemine veya Windows 7 sistemlerinde .NET Framework tarafından sağlanan karakter verilerine güvenmeye devam eder.

Unicode 6.0'dan Unicode 7.0'a kadar karakter kategorilerinde yapılan değişiklikler için Unicode Konsorsiyumu web [sitesindeun Unicode Standardı, Sürüm 7.0.0'a](https://www.unicode.org/versions/Unicode7.0.0/) bakın. Unicode 7.0'dan Unicode 8.0'a değişiklikler için Unicode Konsorsiyumu web [sitesindeki Unicode Standard, Sürüm 8.0.0'a](https://www.unicode.org/versions/Unicode8.0.0/) bakın.

<a name="Crypto462" />

### <a name="cryptography"></a>Şifreleme

**FIPS 186-3 DSA içeren X509 sertifikaları için destek**

.NET Framework 4.6.2, anahtarları FIPS 186-2 1024 bit sınırını aşan DSA (Dijital İmza Algoritması) X509 sertifikaları için destek ekler.

.NET Framework 4.6.2, FIPS 186-3'ün daha büyük anahtar boyutlarını desteklemenin yanı sıra SHA-2 karma algoritmaailesi (SHA256, SHA384 ve SHA512) ile hesaplama imzalarına olanak tanır. FIPS 186-3 desteği yeni <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> sınıf tarafından sağlanmaktadır.

.NET Framework 4.6'daki <xref:System.Security.Cryptography.RSA> sınıf ve .NET <xref:System.Security.Cryptography.ECDsa> Framework 4.6.1'deki sınıfa yapılan son değişikliklere uygun olarak, .NET Framework 4.6.2'deki <xref:System.Security.Cryptography.DSA> soyut taban sınıfı, arayanların bu işlevselliği döküm yapmadan kullanmalarına olanak tanıyan ek yöntemlere sahiptir. Aşağıdaki örnekte <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> görüldüğü gibi, verileri imzalamak için uzantı yöntemini çağırabilirsiniz.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

İmzalı verileri <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> doğrulamak için uzantı yöntemini aşağıdaki örnekte gösterdiği gibi arayabilirsiniz.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

**ECDiffieHellman anahtar türetme rutinlerine girişler için artırılmış netlik**

.NET Framework 3.5, üç farklı Anahtar Türetme Fonksiyonu (KDF) yordamı yla Eliptik Eğri Diffie-Hellman Anahtar Anlaşması'na destek ekledi. Yordamlara girişler ve yordamların kendileri, <xref:System.Security.Cryptography.ECDiffieHellmanCng> nesneüzerindeki özellikler aracılığıyla yapılandırıldı. Ama her rutin her giriş özelliği okumak bu yana, geliştirici geçmiş karışıklık için yeterli oda vardı.

.NET Framework 4.6.2'de bu sorunu gidermek için, bu <xref:System.Security.Cryptography.ECDiffieHellman> KDF yordamlarını ve girişlerini daha net bir şekilde temsil etmek için taban sınıfa aşağıdaki üç yöntem eklenmiştir:

|ECDiffieHellman yöntemi|Açıklama|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Formülü kullanarak anahtar malzeme türler<br /><br /> HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HASH(secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> *x,* EC Diffie-Hellman algoritmasının hesaplanmış sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Formülü kullanarak anahtar malzeme türler<br /><br /> HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)<br /><br /> HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> *x,* EC Diffie-Hellman algoritmasının hesaplanmış sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|TLS sözde rasgele fonksiyon (PRF) türetme algoritması kullanarak anahtar malzeme türetir.|

**Kalıcı anahtar simetrik şifreleme desteği**

Windows şifreleme kitaplığı (CNG), kalıcı simetrik tuşları depolamak ve donanımda depolanan simetrik anahtarları kullanmak için destek ekledi ve .NET Framework 4.6.2 geliştiricilerin bu özelliği kullanmasını mümkün kıldı.  Anahtar adlar ve anahtar sağlayıcılar kavramı uygulamaya özgü olduğundan, bu özelliği kullanmak, tercih edilen fabrika yaklaşımı (arama `Aes.Create`gibi) yerine somut uygulama türlerinin oluşturucusu kullanılmasını gerektirir.

AES ( ) ve 3DES (<xref:System.Security.Cryptography.AesCng><xref:System.Security.Cryptography.TripleDESCng>) algoritmaları için kalıcı anahtar simetrik şifreleme desteği vardır. Örnek:

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

**SHA-2 karma için SignedXml desteği**

.NET Framework 4.6.2, RSA-SHA256, RSA-SHA384 ve RSA-SHA512 PKCS#1 imza yöntemleri ve SHA256, SHA384 ve SHA512 referans özet algoritmaları için <xref:System.Security.Cryptography.Xml.SignedXml> sınıfa destek ekler.

URI sabitlerinin tümü şu <xref:System.Security.Cryptography.Xml.SignedXml>şekilde açıktadır:

|SignedXml alanı|Sabit|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Bu algoritmalar için <xref:System.Security.Cryptography.SignatureDescription> destek eklemek <xref:System.Security.Cryptography.CryptoConfig> için özel bir işleyici kaydetmiş olan tüm programlar geçmişte olduğu gibi çalışmaya devam <xref:System.Security.Cryptography.CryptoConfig> edecektir, ancak artık platform varsayılanları olduğundan, kayıt artık gerekli değildir.

<a name="SQLClient" />

### <a name="sqlclient"></a>Sqlclient

.NET Framework Data Provider<xref:System.Data.SqlClient?displayProperty=nameWithType>for SQL Server ( ) .NET Framework 4.6.2'de aşağıdaki yeni özellikleri içerir:

**Azure SQL veritabanları ile bağlantı havuzu ve zaman ekmeleri**

Bağlantı havuzu etkinleştirildiğinde ve bir zaman ekme veya başka bir oturum açma hatası oluştuğunda, önbelleğe alınan özel durum önbelleğe alınır ve önbelleğe alınan özel durum sonraki 5 saniye ile 1 dakika arasında sonraki herhangi bir bağlantı denemesine atılır. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md)adresine bakın.

Bağlantı denemeleri genellikle hızlı bir şekilde kurtarılan geçici hatalarla başarısız olabileceğinden, bu davranış Azure SQL Veritabanlarına bağlanırken istenmez. Bağlantı yeniden deneme deneyimini daha iyi en iyi duruma getirmek için, Azure SQL Veritabanlarına bağlantılar başarısız olduğunda bağlantı havuzu engelleme dönemi davranışı kaldırılır.

Yeni `PoolBlockingPeriod` anahtar kelimenin eklenmesi, uygulamanız için en uygun engelleme dönemini seçmenize olanak tanır. Değerlere şunlar dahildir:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Azure SQL Veritabanı'na bağlanan bir uygulamanın bağlantı havuzu engelleme süresi devre dışı bırakılır ve başka bir SQL Server örneğine bağlanan bir uygulamanın bağlantı havuzu engelleme süresi etkinleştirilir. Varsayılan değer budur. Sunucu bitiş noktası adı aşağıdakilerden biriyle biterse, Azure SQL Veritabanları olarak kabul edilir:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Bağlantı havuzu engelleme süresi her zaman etkinleştirilir.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Bağlantı havuzu engelleme süresi her zaman devre dışı bırakılır.

**Her Zaman Şifrelenenler için Geliştirmeler**

SQLClient Her Zaman Şifrelenmiş için iki geliştirme sunar:

- Parametreli sorguların şifrelenmiş veritabanı sütunlarına karşı performansını artırmak için, sorgu parametreleri için şifreleme meta verileri artık önbelleğe alındı. <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> Özellik ayarlandığı `true` (varsayılan değer olan) ile, aynı sorgu birden çok kez çağrılırsa, istemci sunucudan yalnızca bir kez parametre meta verilerini alır.

- Anahtar önbelleğindeki sütun şifreleme anahtarı girişleri, <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> özelliği kullanılarak ayarlanan, yapılandırılabilir bir zaman aralığından sonra şimdi tahliye edilir.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

.NET Framework 4.6.2'de Windows Communication Foundation aşağıdaki alanlarda geliştirilmiştir:

**CNG kullanılarak depolanan sertifikalar için WCF taşıma güvenliği desteği**

WCF aktarım güvenliği, Windows şifreleme kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler. .NET Framework 4.6.2'de bu destek, 32 bitten fazla olmayan bir üse sahip ortak anahtara sahip sertifikaları kullanmakla sınırlıdır. Bir uygulama .NET Framework 4.6.2'yi hedefaldığında, bu özellik varsayılan olarak açıktır.

.NET Framework 4.6.1 ve daha öncesini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalariçin bu özellik, app.config veya web.config dosyasının [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satır eklenerek etkinleştirilebilir.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Bu, aşağıdaki gibi kodla programlı olarak da yapılabilir:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**DataContractJsonSerializer sınıfı tarafından birden fazla gün ışığından yararlanma saati ayarlama kuralları için daha iyi destek**

Müşteriler, sınıfın tek bir saat <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dilimi için birden çok ayarlama kuralını destekleyip desteklemediğini belirlemek için bir uygulama yapılandırma ayarını kullanabilir. Bu bir tercih özelliğidir. Etkinleştirmek için app.config dosyanıza aşağıdaki ayarı ekleyin:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Bu özellik etkinleştirildiğinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir <xref:System.TimeZoneInfo> nesne tarih <xref:System.TimeZone> ve saat verilerini deserialize etmek için türü yerine kullanır. <xref:System.TimeZoneInfo>geçmiş saat dilimi verileriyle çalışmayı mümkün kılan birden çok ayarlama kuralını destekler;   <xref:System.TimeZone> değildir.

<xref:System.TimeZoneInfo> Yapı ve saat dilimi ayarlamaları hakkında daha fazla bilgi için Saat [Dilimine Genel Bakış'a](../../standard/datetime/time-zone-overview.md)bakın.

**NetNamedPipeBinding en iyi maç**

WCF, istedikleri uygulamayla en iyi eşleşen URI dinleme hizmetine her zaman bağlanmalarını sağlamak için istemci uygulamalarında ayarlanabilen yeni bir uygulama ayarına sahiptir. Bu uygulama ayarı `false` (varsayılan) olarak ayarlandığı <xref:System.ServiceModel.NetNamedPipeBinding> için, kullanan istemcilerin istenen URI'nin bir alt parçası olan URI'yi dinleyen bir hizmete bağlanmaya çalışması mümkündür.

Örneğin, bir istemci dinleme bir hizmete `net.pipe://localhost/Service1`bağlanmaya çalışır, ancak yönetici ayrıcalığı ile `net.pipe://localhost`çalışan bu makinede farklı bir hizmet dinliyor . Bu uygulama ayarı `false`ayarlandığı için, istemci yanlış hizmete bağlanmayı dener. Uygulama ayarını ayarladıktan `true`sonra, istemci her zaman en iyi eşleşen hizmete bağlanır.

> [!NOTE]
> Tam <xref:System.ServiceModel.NetNamedPipeBinding> bitiş noktası adresi yerine hizmetin temel adresine (varsa) dayalı hizmetleri kullanan istemciler. Bu ayarın her zaman çalıştığından emin olmak için hizmetin benzersiz bir temel adres kullanması gerekir.

Bu değişikliği etkinleştirmek için, istemci uygulamanızın App.config veya Web.config dosyasına aşağıdaki uygulama ayarını ekleyin:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3.0 varsayılan bir protokol değildir**

Aktarım güvenliği ve kimlik bilgisi sertifikası türüyle NetTcp kullanılırken, SSL 3.0 artık güvenli bir bağlantı için kullanılan varsayılan bir protokol değildir. TlS 1.0 NetTcp için protokol listesine dahil olduğundan, çoğu durumda, varolan uygulamalar üzerinde hiçbir etkisi olmamalıdır. Mevcut tüm istemciler en az TLS 1.0 kullanarak bir bağlantı üzerinde anlaşma yapabilmelidir. Ssl3 gerekiyorsa, anlaşmalı protokoller listesine eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.

- Özellik <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType>

- Özellik <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType>

- [ \<](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) [ \<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) bölümünün taşıma>bölümü

- [ \<ÖzelBağlayıcı](../configure-apps/file-schema/wcf/custombinding.md) [ \<](../configure-apps/file-schema/wcf/sslstreamsecurity.md)>bölümünün sslStreamSecurity>bölümü

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.6.2'de, Windows Sunu Vakfı aşağıdaki alanlarda geliştirilmiştir:

**Grup sıralama**

Verileri gruplandırmak <xref:System.Windows.Data.CollectionView> için bir nesne kullanan bir uygulama artık grupları nasıl sıralayacak açık bir şekilde bildirebilir. Açık sıralama, bir uygulama dinamik olarak gruplar eklendiğinde veya kaldırdığında veya gruplandırmada yer alan madde özelliklerinin değerini değiştirdiğinde ortaya çıkan sezgisel olmayan sıralama sorununu gidermektedir. Ayrıca, gruplandırma özelliklerinin karşılaştırmalarını tam koleksiyon türünden grupların türüne taşıyarak grup oluşturma işleminin performansını artırabilir.

Grup sıralamasını desteklemek için, yeni <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> ve <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> özellikler nesne tarafından üretilen <xref:System.ComponentModel.GroupDescription> grupların koleksiyonunu nasıl sıralayacaklarını açıklar. Bu, aynı adlandırılmış <xref:System.Windows.Data.ListCollectionView> özelliklerin veri öğelerini nasıl sıralayacaklarını açıklama şekline benzer.

<xref:System.Windows.Data.PropertyGroupDescription> Sınıfın iki yeni statik <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> özellikleri <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>ve , en sık karşılaşılan durumlar için kullanılabilir.

Örneğin, aşağıdaki XAML verileri yaşa göre gruplandırmak, artan sırada yaş gruplarını sıralamak ve her yaş grubundaki öğeleri soyadına göre gruplandırmak.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription
         PropertyName="Age"
         CustomSort=
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

**Dokunmatik klavye desteği**

Dokunmatik klavye desteği, metin girişi alabilen bir denetim tarafından dokunmatik giriş yapıldığında Windows 10'daki dokunmatik Klavyeyi otomatik olarak çağırArak ve reddederek WPF uygulamalarında odak izleme sağlar.

.NET Framework'ün önceki sürümlerinde, WPF uygulamaları WPF kalem/dokunma hareketi desteğini devre dışı bırakmadan odak izlemeyi seçemez. Sonuç olarak, WPF uygulamaları tam WPF dokunmatik desteği arasında seçim yapmalı veya Windows fare promosyonuna güvenmelidir.

**Monitör başına DPI**

WPF uygulamaları için yüksek DPI ve hibrit DPI ortamlarının yakın zamanda yayılmasını desteklemek için,.NET Framework 4.6.2'deki WPF, monitör başına farkındalık sağlar. WPF uygulamanızın monitör başına DPI farkında olmasını nasıl sağlayacağınız hakkında daha fazla bilgi için GitHub'daki [örneklere ve geliştirici kılavuzuna](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) bakın.

.NET Framework'ün önceki sürümlerinde, WPF uygulamaları sistem-DPI farkındadır. Başka bir deyişle, uygulamanın Kullanıcı UI'si, uygulamanın işlendiği monitörün DPI'sına bağlı olarak, uygun şekilde OS tarafından ölçeklendirilir.

.NET Framework 4.6.2 altında çalışan uygulamalar için, uygulama yapılandırma dosyanızın [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki gibi bir yapılandırma bildirimi ekleyerek WPF uygulamalarındaki DPI değişikliklerini izlemek başına devre dışı kullanabilirsiniz:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

.NET Framework 4.6.2'de, Windows İş Akışı Temeli aşağıdaki alanda geliştirilmiştir:

**Yeniden Barındırılan WF Tasarımcısı'nda C# ifadeleri ve IntelliSense desteği**

.NET Framework 4.5 ile başlayan WF, Hem Visual Studio Designer'da hem de kod iş akışlarında C# ifadelerini destekler. Yeniden Barındırılan İş Akışı Tasarımcısı, İş Akışı Tasarımcısı'nın Visual Studio dışındaki bir uygulamada (örneğin, WPF'de) olmasını sağlayan WF'nin önemli bir özelliğidir.  Windows İş Akışı Temeli, Yeniden Barındırılan İş Akışı Tasarımcısı'nda C# ifadelerini ve IntelliSense'i destekleme olanağı sağlar. Daha fazla bilgi için [Windows İş Akışı Vakfı bloguna](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer)bakın.

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`4.6.2'den önceki .NET Framework sürümlerinde, Bir müşteri Visual Studio'dan bir iş akışı projesi yeniden inşa ettiğinde WF Designer IntelliSense bozulur. Proje yapısı başarılı olsa da, tasarımcıda iş akışı türleri bulunmaz ve eksik iş akışı türleri için IntelliSense'den gelen uyarılar **Hata Listesi** penceresinde görünür. .NET Framework 4.6.2 bu sorunu gideriyor ve IntelliSense'i kullanılabilir hale getiriyor.

**İş Akışı İzleme ile İş Akışı V1 uygulamaları artık FIPS modu altında çalıştırıl**

FIPS Uyumluluk Modu etkin leştirilmiş makineler artık iş akışı Sürüm 1 tarzı bir uygulamayı İş Akışı izleme üzerinde başarıyla çalıştırabiliyor. Bu senaryoyu etkinleştirmek için app.config dosyanızda aşağıdaki değişikliği yapmalısınız:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Bu senaryo etkinleştirilmezse, uygulamayı çalıştıran ileti ile bir özel durum oluşturmaya devam ediyor, "Bu uygulama Windows Platformu FIPS doğrulanmış şifreleme algoritmaları parçası değildir."

**Visual Studio İş Akışı Tasarımcısı ile Dinamik Güncelleme kullanırken İş Akışı Geliştirmeleri**

İş Akışı Tasarımcısı, FlowChart Etkinlik Tasarımcısı ve diğer İş Akışı Etkinlik Tasarımcıları artık <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi aradıktan sonra kaydedilen iş akışlarını başarıyla yükler ve görüntüler. .NET Framework 4.6.2'den önceki .NET Framework sürümlerinde, arama <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> dan sonra kaydedilen bir iş akışı için Visual Studio'da bir XAML dosyasının yüklenmesi aşağıdaki sorunlara neden olabilir:

- İş Akışı Tasarımcısı XAML dosyasını doğru yükleyemez <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> (satırın sonundayken).

- Akış Şeması Etkinlik Tasarımcısı veya diğer İş Akışı Etkinlik Tasarımcıları, ekli özellik değerlerinin aksine tüm nesneleri varsayılan konumlarında görüntüleyebilir.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

ClickOnce, zaten desteklediği 1.0 protokolüne ek olarak TLS 1.1 ve TLS 1.2'yi destekleyecek şekilde güncellendi. ClickOnce hangi protokolün gerekli olduğunu otomatik olarak algılar; TLS 1.1 ve 1.2 desteğini etkinleştirmek için ClickOnce uygulamasında ek adım gerekmez.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Windows Formlarını ve WPF uygulamalarını UWP uygulamalarına dönüştürme

Windows artık WPF ve Windows Forms uygulamaları da dahil olmak üzere mevcut Windows masaüstü uygulamalarını Evrensel Windows Platformu'na (UWP) getirme özellikleri sunuyor. Bu teknoloji, mevcut kod tabanınızı kademeli olarak UWP'ye geçirmenizi sağlayarak uygulamanızı tüm Windows 10 aygıtlarına getirerek bir köprü görevi görür.

Dönüştürülmüş masaüstü uygulamaları, UWP uygulamalarının uygulama kimliğine benzer bir uygulama kimliği kazanır ve bu da UWP API'lerinin Canlı Kutucuklar ve bildirimler gibi özellikleri etkinleştirmesini sağlar. Uygulama eskisi gibi olmaya devam ediyor ve tam bir güven uygulaması olarak çalışır. Uygulama dönüştürüldükten sonra, uyarlanabilir bir kullanıcı arabirimi eklemek için varolan tam güven işlemine bir uygulama kapsayıcı işlemi eklenebilir. Tüm işlevler uygulama kapsayıcı işlemine taşındığında, tam güven işlemi kaldırılabilir ve yeni UWP uygulaması tüm Windows 10 aygıtları tarafından kullanılabilir hale getirilebilir.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Hata ayıklama iyileştirmeleri

*Yönetilmeyen hata ayıklama API* kaynak kodu tek bir satırda hangi değişkenbelirlemek mümkün <xref:System.NullReferenceException> böylece bir atıldığında ek analiz gerçekleştirmek için .NET `null`Framework 4.6.2 geliştirilmiştir.   Bu senaryoyu desteklemek için, yönetilmeyen hata ayıklama API'sine aşağıdaki API'ler eklendi.

- [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), ve [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arayüzleri, yönetilen değişkenlerin yerli evleri ortaya çıkarmak. Bu, hata ayıklayıcıların bir <xref:System.NullReferenceException> olay olduğunda bazı kod akış çözümlemesi yapmalarını ve yerel konuma karşılık `null`gelen yönetilen değişkeni belirlemek için geriye doğru çalışmalarını sağlar.

- [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi, hata ayıklayıcının ICorDebugType örneği olmadan [bir COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) elde etmesini sağlayan iCorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md)için bir eşleme sağlar. [COR_TYPEID'daki](../unmanaged-api/debugging/cor-typeid-structure.md) varolan API'ler daha sonra türün sınıf düzenini belirlemek için kullanılabilir.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>.NET Framework 4.6.1'deki yenilikler

.NET Framework 4.6.1 aşağıdaki alanlarda yeni özellikler içerir:

- [Şifreleme](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profil oluşturma](#Profile461)

- [Ngen](#NGEN461)

.NET Framework 4.6.1 hakkında daha fazla bilgi için aşağıdaki konulara bakın:

- [.NET Framework 4.6.1 değişiklik listesi](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [4.6.1'de Uygulama Uyumluluğu](../migration-guide/application-compatibility.md)

- [.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (GitHub'da)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Şifreleme: ECDSA içeren X509 sertifikaları için destek

.NET Framework 4.6 X509 sertifikaları için RSACng desteği eklendi. .NET Framework 4.6.1, ECDSA (Eliptik Eğri Dijital İmza Algoritması) X509 sertifikaları için destek ekler.

ECDSA daha iyi performans sunar ve RSA'dan daha güvenli bir şifreleme algoritmasıdır ve Taşıma Katmanı Güvenliği (TLS) performansı ve ölçeklenebilirliğinin bir sorun olduğu mükemmel bir seçim sunar. .NET Framework uygulaması çağrıları varolan Windows işlevlerine sarar.

Aşağıdaki örnek kod, .NET Framework 4.6.1'de yer alan ECDSA X509 sertifikaları için yeni desteği kullanarak bir bayt akışı için imza oluşturmanın ne kadar kolay olduğunu gösterir.

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

Bu, .NET Framework 4.6'da imza oluşturmak için gereken kodla belirgin bir kontrast sunar.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

ADO.NET aşağıdakiler eklendi:

**Donanım korumalı anahtarlar için her zaman Şifrelenmiş destek**

ADO.NET artık Her Zaman Şifrelenmiş sütun ana anahtarlarını Donanım Güvenlik Modüllerinde (HSM) doğal olarak depolamayı destekler. Bu destekle, müşteriler özel sütun ana anahtar deposu sağlayıcıları yazmak ve bunları uygulamalara kaydettirmek zorunda kalmadan HSM'lerde depolanan asimetrik anahtarlardan yararlanabilirler.

Müşterilerin HSM'de depolanan sütun ana anahtarlarıyla korunan Her Zaman Şifrelenmiş verilere erişmek için hsm satıcı tarafından sağlanan CSP sağlayıcısını veya CNG anahtar mağaza sağlayıcılarını uygulama sunucularına veya istemci bilgisayarlara yüklemeleri gerekir.

**AlwaysOn için geliştirilmiş <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> bağlantı davranışı**

SqlClient artık bir AlwaysOn Kullanılabilirlik Grubu'na (AG) otomatik olarak daha hızlı bağlantı sağlar. Uygulamanızın farklı bir alt ağdaki bir AlwaysOn kullanılabilirlik grubuna (AG) bağlanıp bağlanmadığını saydam olarak algılar ve geçerli etkin sunucuyu hızla keşfeder ve sunucuya bağlantı sağlar. Bu sürümden önce, bir uygulamanın bir `"MultisubnetFailover=true"` AlwaysOn Kullanılabilirlik Grubuna bağlandığını belirtmek için bağlantı dizesini eklemesi gerekiyordu. Bağlantı anahtar sözcükünü `true`ayarlamadan, bir uygulama Bir AlwaysOn Kullanılabilirlik Grubuna bağlanırken bir zaman ayarı yaşayabilir. Bu sürümle, bir uygulamanın `true` <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> artık ayarlanmaması *gerekmez.* Her Zaman Kullanılabilirlik Grupları için SqlClient desteği hakkında daha fazla bilgi için, [Yüksek Kullanılabilirlik için SqlClient Desteği, Olağanüstü Durum Kurtarma'ya](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)bakın.

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Sunu Temeli bir dizi geliştirme ve değişiklik içerir.

**Geliştirilmiş performans**

Dokunma olaylarının ateşlemedeki gecikmesi .NET Framework 4.6.1'de giderilmiştir. Buna ek olarak, <xref:System.Windows.Controls.RichTextBox> bir denetim de yazma artık hızlı giriş sırasında render iş parçacığı bağlar.

**Yazım denetimi geliştirmeleri**

WPF'deki yazım denetleyicisi, yazım denetimi ek dilleri için işletim sistemi desteğinden yararlanmak için Windows 8.1 ve sonraki sürümlerde güncelleştirildi.  Windows 8.1'den önce Windows sürümlerinde işlevsellik değişikliği yoktur.

.NET Framework'ün önceki sürümlerinde olduğu <xref:System.Windows.Controls.TextBox> gibi, <xref:System.Windows.Controls.RichTextBox> bir denetim ora bloğunun dili aşağıdaki sırayla bilgi arayarak algılanır:

- `xml:lang`, varsa.

- Geçerli giriş dili.

- Geçerli iş parçacığı kültürü.

WPF'de dil desteği hakkında daha fazla bilgi için [.NET Framework 4.6.1 özelliklerindeki WPF blog](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)gönderisine bakın.

**Kullanıcı başına özel sözlükler için ek destek**

.NET Framework 4.6.1'de WPF, genel olarak kayıtlı özel sözlükleri tanır. Bu özellik, bunları denetim başına kaydetme özelliğine ek olarak kullanılabilir.

WPF'nin önceki sürümlerinde, özel sözlükler Dışlanmış Sözcükler i ve Otomatik Düzeltme listelerini tanımadı. Bunlar, `%AppData%\Microsoft\Spelling\<language tag>` dizin altına yerleştirilebilen dosyaların kullanımı yoluyla Windows 8.1 ve Windows 10'da desteklenir.  Aşağıdaki kurallar bu dosyalar için geçerlidir:

- Dosyalarda .dic (eklenen sözcükler için), .exc (dışlanmış sözcükler için) veya .acl (Otomatik Düzeltme için) uzantıları olmalıdır.

- Dosyalar Byte Order Mark (BOM) ile başlayan UTF-16 LE düz metin olmalıdır.

- Her satır bir sözcükten (eklenen ve dışlanan sözcük listelerinde) veya sözcükleri dikey çubukla ("&#124;") (Otomatik Düzeltme sözcük listesinde) ayrılmış otomatik düzeltme çiftinden oluşmalıdır.

- Bu dosyalar salt okunur olarak kabul edilir ve sistem tarafından değiştirilmez.

> [!NOTE]
> Bu yeni dosya biçimleri doğrudan WPF yazım denetimi API'leri tarafından desteklenmez ve uygulamalarda WPF'ye verilen özel sözlükler .lex dosyalarını kullanmaya devam etmelidir.

**Örnekler**

[Microsoft/WPF-Örnekleri](https://github.com/Microsoft/WPF-Samples) GitHub deposunda birkaç WPF örneği vardır. Bize bir çekme isteği göndererek veya bir [GitHub sorunu](https://github.com/Microsoft/WPF-Samples/issues)açarak örneklerimizi geliştirmemize yardımcı olun.

**DirectX uzantıları**

WPF, DX10 ve Dx11 içeriğiyle birlikte çalışmanızı kolaylaştıran yeni uygulamalar <xref:System.Windows.Interop.D3DImage> sağlayan bir [NuGet paketi](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) içerir. Bu paketin kodu açık kaynaklı olmuştur ve [GitHub'da](https://github.com/Microsoft/WPFDXInterop)kullanılabilir.

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows İş Akışı Temeli: İşlemler

Yöntem <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> artık hareketi tanıtmak için MSDTC dışında dağıtılmış bir işlem yöneticisi kullanabilir. Bunu, yeni <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yüke guid işlem organizatörü tanımlayıcısı belirterek yaparsınız. Bu işlem başarılı olursa, işlemin yeteneklerine sınırlamalar yerleştirilir. MSDTC olmayan bir işlem organizatörü kaydolduktan sonra, bu <xref:System.Transactions.TransactionPromotionException> yöntemler MSDTC'ye terfi etmeyi gerektirdiğinden aşağıdaki yöntemler bir yöntem atar:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

MSDTC olmayan bir işlem organizatörü kaydolduktan sonra, tanımladığı protokoller kullanılarak gelecekteki dayanıklı listments için kullanılmalıdır. İşlem <xref:System.Guid> organizatörü <xref:System.Transactions.Transaction.PromoterType%2A> özelliği kullanılarak elde edilebilir. Hareket teşvik edildiğinde, hareket organizatörü tanıtılan belirteci temsil eden bir <xref:System.Byte> dizi sağlar. Bir uygulama <xref:System.Transactions.Transaction.GetPromotedToken%2A> yöntemi ile MSDTC olmayan bir hareket için terfi jeton elde edebilirsiniz.

Promosyon işleminin <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> başarıyla tamamlanması için yeni aşırı yüklemenin kullanıcılarının belirli bir çağrı sırasını izlemesi gerekir. Bu kurallar yöntemin belgelerinde belgelenmiştir.

<a name="Profile461" />

### <a name="profiling"></a>Profil oluşturma

Yönetilmeyen profil oluşturma API'si aşağıdaki gibi geliştirilmiştir:

- [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabiriminde PDB'lere erişmek için daha iyi destek.

  ASP.NET Core'da, derlemelerin Roslyn tarafından hafızalarda derlenmeleri çok daha yaygın hale gelmektedir. Profil oluşturma araçları yapan geliştiriciler için bu, geçmişte diskte seri hale getirilen PDB'lerin artık bulunamayacağı anlamına gelir. Profiler araçları genellikle kod kapsamı veya satır satır performans analizi gibi görevler için kodu kaynak satırlarına yeniden eşlemek için PDB'leri kullanır. [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arayüzü şimdi iki yeni yöntem içerir, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) ve [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), bellek PDB verilere erişim ile bu profilci araçları sağlamak için, yeni API'ler kullanarak, bir profilci bir bayt dizisi olarak bellek tep pdb içeriğini elde edebilirsiniz ve sonra işleyebilir veya disk için seri.

- ICorProfiler arabirimi ile daha iyi enstrümantasyon.

  Dinamik enstrümantasyon `ICorProfiler` için API'ler ReJit işlevini kullanan profilciler artık bazı meta verileri değiştirebilir. Daha önce bu tür araçlar herhangi bir zamanda IL enstrüman olabilir, ancak meta veriler yalnızca modül yükleme zamanında değiştirilebilir. IL meta verilere atıfta bulunduğundan, bu yapılabilecek enstrümantasyon türlerini sınırlandırmaktadır. Biz ICorProfilerInfo7 ekleyerek bu sınırların bazılarını [kaldırdık::UygulamaMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) yöntemi modül yükleri sonra meta veri düzenlemebir alt `AssemblyRef`kümesi `TypeRef` `TypeSpec`desteklemek `MemberRef` `MemberSpec`için, `UserString` özellikle ekleyerek , , , , , ve kayıtlar. Bu değişiklik, çok daha geniş bir anında enstrümantasyon yelpazesini mümkün kılmasıdır.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Yerli Görüntü Jeneratörü (NGEN) PDB'leri

Makineler arası olay izleme, müşterilerin Machine A'daki bir programın profilini çıkarmalarına ve Makine B'deki kaynak çizgi eşlemesiyle profil oluşturma verilerine bakmalarını sağlar. kaynaktan yerel eşleme oluşturmak için IL PDB içeren analiz makinesine makine. Dosyalar telefon uygulamaları gibi nispeten küçük olduğunda bu işlem iyi çalışabilir, ancak dosyalar masaüstü sistemlerinde çok büyük olabilir ve kopyalamak için önemli bir zaman gerektirebilir.

Ngen PDB'leri ile NGen, IL PDB'ye bağımlı olmadan IL-to-native eşlemi içeren bir PDB oluşturabilir. Makineler arası olay izleme senaryomuzda, tek gereken Makine A'dan Makine B'ye oluşturulan yerel görüntü PDB'yi kopyalamak ve IL PDB'nin kaynaktan IL'e eşleğesini ve pdb'nin IL-yerel eşlemasını okumak için [Hata Ayık Arabirim Erişim API'lerini](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) kullanmaktır. Her iki eşlemenin birleştirilmesi kaynaktan yereleşleme sağlar. Yerel görüntü PDB tüm modüllerden ve yerel görüntülerden çok daha küçük olduğundan, Makine A'dan Makine B'ye kopyalama işlemi çok daha hızlıdır.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>.NET 2015'teki yenilikler

.NET 2015 .NET Framework 4.6 ve .NET Core'u tanıttı. Bazı yeni özellikler her ikisi için de geçerlidir ve diğer özellikler .NET Framework 4.6 veya .NET Core'a özgüdir.

- **ASP.NET Core**

  .NET 2015, modern bulut tabanlı uygulamalar oluşturmak için yalın bir .NET uygulaması olan ASP.NET Core'u içerir. ASP.NET Core modülerdir, böylece yalnızca uygulamanızda gereken özellikleri ekleyebilirsiniz. IIS'de barındırılabilir veya özel bir işlemle kendi kendine barındırılabilir ve .NET Framework'ün farklı sürümlerine sahip uygulamaları aynı sunucuda çalıştırabilirsiniz. Bulut dağıtımı için tasarlanmış yeni bir ortam yapılandırma sistemi içerir.

  MVC, Web API ve Web Sayfaları, MVC 6 adı verilen tek bir çerçevede birleştirilir. Visual Studio 2015 veya sonraki araçlar aracılığıyla ASP.NET Core uygulamaları oluşturursunuz. Mevcut uygulamalarınız yeni .NET Framework üzerinde çalışacaktır; ancak MVC 6 veya SignalR 3 kullanan bir uygulama oluşturmak için Visual Studio 2015 veya sonraki yıllarda proje sistemini kullanmanız gerekir.

  Bilgi için [ASP.NET Core'a](/aspnet/core/)bakın.

- **ASP.NET Güncellemeler**

  - **Asynchronous Yanıt Yıkama için Görev Tabanlı API**

    ASP.NET şimdi asynchronous yanıt yıkama için basit bir <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>görev tabanlı API sağlar, bu yanıtları eşit sizde dil `async/await` desteği kullanarak floş sağlar.

  - **Model bağlama görev döndürme yöntemlerini destekler**

    .NET Framework 4.5'te ASP.NET, Web Formları sayfalarında ve kullanıcı denetimlerinde CRUD tabanlı veri işlemlerine genişletilebilir, kod odaklı bir yaklaşım sağlayan Model Bağlama özelliğini ekledi. Model Bağlama sistemi <xref:System.Threading.Tasks.Task>artık model bağlama yöntemlerini destekler. Bu özellik, Web Forms geliştiricilerinin Varlık Çerçevesi de dahil olmak üzere ORM'lerin yeni sürümlerini kullanırken veri bağlama sisteminin kolaylığıyla async'in ölçeklenebilirlik avantajlarını elde etmesine olanak tanır.

    Async modeli bağlama `aspnet:EnableAsyncModelBinding` yapılandırma ayarı tarafından denetlenir.

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    Uygulamalarda hedef .NET Framework 4.6, varsayılan `true`olarak . .NET Framework 4.6 üzerinde çalışan ve .NET Framework'ün önceki `false` bir sürümünü hedefleyen uygulamalarda varsayılan olarak bu durum dur. Yapılandırma ayarını `true`.

  - **HTTP/2 Desteği (Windows 10)**

    [HTTP/2,](https://www.wikipedia.org/wiki/HTTP/2) çok daha iyi bağlantı kullanımı (istemci ve sunucu arasında daha az gidiş-dönüş) sağlayan ve kullanıcılar için daha düşük gecikmeli web sayfası yüklemesi sağlayan HTTP protokolünün yeni bir sürümüdür.  Web sayfaları (hizmetlerin aksine) http/2'den en çok yararlanan, protokol tek bir deneyimin bir parçası olarak istenen birden çok eser için optimize edildiğinden. .NET Framework 4.6'daki ASP.NET http/2 desteği eklenmiştir. Ağ işlevi birden çok katmanda olduğundan, HTTP/2'yi etkinleştirmek için Windows' da, IIS' de ve ASP.NET'da yeni özellikler gerekiyordu. ASP.NET ile HTTP/2'yi kullanmak için Windows 10'da çalışıyor olmalısınız.

    HTTP/2, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API'yi kullanan Windows 10 Evrensel Windows Platformu (UWP) uygulamaları için de desteklenir ve varsayılan olarak açık ta.

    ASP.NET uygulamalarda [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) özelliğini kullanmanın bir yolunu sağlamak için, iki <xref:System.Web.HttpResponse.PushPromise%28System.String%29> aşırı <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>yükleme içeren yeni <xref:System.Web.HttpResponse> bir yöntem sınıfa eklendi.

    > [!NOTE]
    > ASP.NET Core HTTP/2'yi desteklerken, PUSH PROMISE özelliği için destek henüz eklenmedi.

    Tarayıcı ve web sunucusu (Windows'da IIS) tüm işi yapmak. Kullanıcılarınız için herhangi bir ağır kaldırma yapmak zorunda değilsiniz.

    Büyük tarayıcıların çoğu [HTTP/2'yi destekler,](https://www.wikipedia.org/wiki/HTTP/2)bu nedenle sunucunuz destekliyorsa kullanıcılarınızın HTTP/2 desteğinden yararlanmaolasılığı yüksektir.

  - **Belirteç Bağlama Protokolü Desteği**

    Microsoft ve Google, [Token Bağlama Protokolü](https://github.com/TokenBinding/Internet-Drafts)adı verilen kimlik doğrulamasına yönelik yeni bir yaklaşım üzerinde işbirliği içindedir. Öncül kimlik doğrulama belirteçleri (tarayıcı önbelleğinde) çalınabilir ve şifrenizi veya başka herhangi bir ayrıcalıklı bilgi gerektirmeden başka güvenli kaynaklara (örneğin, banka hesabınız) erişmek için suçlular tarafından kullanılabilir. Yeni protokol, bu sorunu azaltmayı amaçlıyor.

    Belirteç Bağlama Protokolü, Windows 10'da tarayıcı özelliği olarak uygulanacaktır. ASP.NET uygulamalar protokole katılır, böylece kimlik doğrulama belirteçleri yasal olarak doğrulanır. İstemci ve sunucu uygulamaları protokolü tarafından belirtilen uçlardan uca korumayı kurar.

  - **Randomize dize karma algoritmaları**

    .NET Framework 4.5 [randomize dize karma algoritması](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)tanıttı. Ancak, bazı ASP.NET özellikleri kararlı bir karma koduna bağlı olduğu için ASP.NET tarafından desteklenmedi. .NET Framework 4.6'da randomize dize karma algoritmaları artık desteklenmiştir. Bu özelliği etkinleştirmek `aspnet:UseRandomizedStringHashAlgorithm` için config ayarını kullanın.

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- **ADO.NET**

  ADO .NET artık SQL Server 2016 Topluluk Teknolojisi Önizleme 2'de (CTP2) bulunan Her Zaman Şifrelenmiş özelliğini destekliyor. Her Zaman Şifrelenmiş ile, SQL Server şifreli veriler üzerinde işlem yapabilir ve en iyisi şifreleme anahtarı sunucuda değil, müşterinin güvendiği ortamda uygulamayla birlikte bulunur. Her zaman Şifrelenmiş müşteri verilerini güvenli hale getirmekte, böylece DBA'ların düz metin verilerine erişimi yoktur. Verilerin şifrelemesi ve şifre çözmesi, sürücü düzeyinde saydam bir şekilde gerçekleşir ve varolan uygulamalarda yapılması gereken değişiklikleri en aza indirir. Ayrıntılar için her [zaman şifrelenmiş (Veritabanı Altyapısı)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) ve [Her Zaman Şifrelenmiş (istemci geliştirme)](/sql/relational-databases/security/encryption/always-encrypted-client-development)bakın.

- **Yönetilen kod için 64 bit JIT Derleyicisi**

  .NET Framework 4.6, 64 bit JIT derleyicisinin (orijinal olarak RyuJIT kod adı verilen) yeni bir sürümünü sunar. Yeni 64 bit derleyici, eski 64 bit JIT derleyicisi üzerinde önemli performans iyileştirmeleri sağlar. Yeni 64 bit derleyici,.NET Framework 4.6'nın üzerinde çalışan 64 bit işlemler için etkinleştirilir. Uygulamanız 64 bit veya AnyCPU olarak derlenmişse ve 64 bit işletim sistemiyle çalışıyorsa 64 bit işlemle çalışır. Yeni derleyiciye geçişi mümkün olduğunca saydam hale getirmek için özen gösterilmiştir, ancak davranış değişiklikleri mümkündür.

  Yeni 64 bit JIT derleyicisi, <xref:System.Numerics> iyi performans iyileştirmeleri sağlayabilen ad alanında SIMD özellikli tiplerle birleştiğinde donanım SIMD hızlandırma özellikleri de içerir.

- **Montaj yükleyici iyileştirmeleri**

  Montaj yükleyicisi, ilgili NGEN görüntüsü yüklendikten sonra IL derlemelerini boşaltarak belleği daha verimli kullanır. Bu değişiklik, özellikle büyük 32 bit uygulamalar (Visual Studio gibi) için yararlı olan sanal belleği azaltır ve aynı zamanda fiziksel bellek tasarrufu sağlar.

- **Taban sınıf kitaplığı değişiklikleri**

  Önemli senaryoları etkinleştirmek için .NET Framework 4.6'ya birçok yeni API eklendi. Bunlar aşağıdaki değişiklikleri ve eklemeleri içerir:

  - **IReadOnlyCollection\<T> uygulamaları**

    Ek koleksiyonlar <xref:System.Collections.Generic.IReadOnlyCollection%601> gibi <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601>uygulamak ve .

  - **CultureInfo.CurrentKültür ve KültürInfo.CurrentUICulture**

    <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri artık salt okunur değil, okuma-yazma vardır. Bu özelliklere yeni <xref:System.Globalization.CultureInfo> bir nesne atarsanız, `Thread.CurrentThread.CurrentCulture` özellik tarafından tanımlanan geçerli iş parçacığı kültürü ve `Thread.CurrentThread.CurrentUICulture` özellikler tarafından tanımlanan geçerli UI iş parçacığı kültürü de değişir.

  - **Çöp toplama geliştirmeleri (GC)**

    Sınıf <xref:System.GC> şimdi <xref:System.GC.TryStartNoGCRegion%2A> içerir <xref:System.GC.EndNoGCRegion%2A> ve kritik bir yol yürütülmesi sırasında çöp toplama izin vermeizni yöntemleri.

    <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> Yöntemin yeni bir aşırı hem küçük nesne yığını ve büyük nesne yığını süpürüldü ve sıkıştırılmış veya yalnızca süpürüldü olup olmadığını kontrol etmenizi sağlar.

  - **SIMD özellikli türleri**

    Ad <xref:System.Numerics> alanı artık SIMD özellikli bir dizi tür <xref:System.Numerics.Matrix3x2>içerir, <xref:System.Numerics.Quaternion> <xref:System.Numerics.Vector2>gibi <xref:System.Numerics.Vector3>, <xref:System.Numerics.Vector4>, <xref:System.Numerics.Matrix4x4> <xref:System.Numerics.Plane>, , , , ve .

    Yeni 64 bit JIT derleyicisi donanım SIMD hızlandırma özellikleri de içerdiğinden, yeni 64 bit JIT derleyicisi ile SIMD özellikli türleri kullanırken özellikle önemli performans iyileştirmeleri vardır.

  - **Şifreleme güncellemeleri**

    [API, Windows CNG şifreleme API'lerini](/windows/desktop/SecCNG/cng-reference)destekleyecek şekilde güncelleştiriliyor. <xref:System.Security.Cryptography?displayProperty=nameWithType> .NET Framework'ün önceki sürümleri, uygulamanın temeli olarak [tamamen Windows Şifreleme API'lerinin önceki](/windows/desktop/SecCrypto/cryptography-portal) bir sürümüne <xref:System.Security.Cryptography?displayProperty=nameWithType> dayanıyordu. Belirli uygulama kategorileri için önemli olan modern [şifreleme algoritmalarını](/windows/desktop/SecCNG/cng-features#suite-b-support)desteklediği için CNG API'yi desteklemek için talepler aldık.

    .NET Framework 4.6, Windows CNG şifreleme API'lerini desteklemek için aşağıdaki yeni geliştirmeleri içerir:

    - X509 Sertifikaları için bir dizi `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` uzatma `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`yöntemi ve mümkün olduğunda CAPI tabanlı bir uygulama yerine CNG tabanlı bir uygulama döndürür. (Bazı akıllı kartlar, vb, hala CAPI gerektirir ve API'ler geri dönüş işlemek).

    - RSA algoritmasının CNG uygulamasını sağlayan <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> sınıf.

    - Yaygın eylemlerin artık döküm gerektirmemesi için RSA API'deki geliştirmeler. Örneğin, bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nesneyi kullanarak verileri şifrelemek, .NET Framework'ün önceki sürümlerinde aşağıdaki gibi kod gerektirir.

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      .NET Framework 4.6'da yeni şifreleme API'lerini kullanan kod, dökümü önlemek için aşağıdaki gibi yeniden yazılabilir.

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - **Tarihleri ve saatleri Unix zamanına veya unix saatine dönüştürme desteği**

    Tarih ve saat değerlerinin <xref:System.DateTimeOffset> Unix zamanına veya Unix zamanına dönüştürülmesini desteklemek için yapıya aşağıdaki yeni yöntemler eklendi:

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - **Uyumluluk anahtarları**

    Sınıf, <xref:System.AppContext> kitaplık yazarlarının kullanıcıları için yeni işlevler için tek tip bir devre dışı bırakma mekanizması sağlamalarını sağlayan yeni bir uyumluluk özelliği ekler. Bir opt-out isteğini iletmek için bileşenler arasında gevşek bir leştirilmiş bir sözleşme kurar. Varolan işlevde değişiklik yapıldığında bu özellik genellikle önemlidir. Tersine, yeni işlevler için zaten örtülü bir opt-in vardır.

    Ile, <xref:System.AppContext>kitaplıklar tanımlamak ve uyumluluk anahtarları ortaya çıkarır, onlara bağlı kod kitaplık davranışını etkileyecek şekilde bu anahtarları ayarlayabilirsiniz. Varsayılan olarak, kitaplıklar yeni işlevselliği sağlar ve yalnızca anahtar ayarlanırsa onu değiştirirler (diğer bir şekilde önceki işlevselliği sağlarlar).

    Bir uygulama (veya kitaplık), bağımlı kitaplığın tanımladığı bir <xref:System.Boolean> anahtarın (her zaman bir değer olan) değerini bildirebilir. Anahtar her zaman `false`örtülüdür. Anahtarı etkinleştirmek `true` için ayarlama. Anahtarı açıkça yeni `false` davranış sağlamak için ayarlamak.

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    Kitaplık, bir tüketicinin anahtarın değerini beyan edip olmadığını kontrol etmeli ve ardından uygun şekilde hareket etmelidir.

    ```csharp
    if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))
    {
        // This is the case where the switch value was not set by the application.
        // The library can choose to get the value of shouldThrow by other means.
        // If no overrides nor default values are specified, the value should be 'false'.
        // A false value implies the latest behavior.
    }

    // The library can use the value of shouldThrow to throw exceptions or not.
    if (shouldThrow)
    {
        // old code
    }
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    Bir kitaplık tarafından ortaya çıkarılan resmi bir sözleşme olduğundan, anahtarlar için tutarlı bir biçim kullanmak yararlıdır. Aşağıdaki iki açık biçimleri vardır.

    - *Değiştir*. *ad alanı*. *anahtar adı*

    - *Değiştir*. *kütüphane*. *anahtar adı*

  - **Görev tabanlı eşsenkronize desendeki değişiklikler (TAP)**

    .NET Framework 4.6'yı hedefleyen <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> uygulamalar için ve nesneler çağrı iş parçacığının kültür ve ui kültürünü devralır. .NET Framework'ün önceki sürümlerini hedefleyen veya .NET Framework'ün belirli bir sürümünü hedeflemeyen uygulamaların davranışı etkilenmez. Daha fazla bilgi için sınıf konusunun "Kültür ve görev tabanlı <xref:System.Globalization.CultureInfo> eşzamanlı işlemler" bölümüne bakın.

    Sınıf, <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> `async` yöntem gibi belirli bir eşzamanlı denetim akışına yerel ortam verilerini temsil etmenizi sağlar. Verileri iş parçacıkları arasında kalıcı hale getirmek için kullanılabilir. Ayrıca, <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> ortam verileri ne zaman değiştirilse, özellik açıkça değiştirildi, ya da iş parçacığı bir bağlam geçişiyle karşılaştığından bildirilen bir geri arama yöntemi de tanımlayabilirsiniz.

    Tamamlanan görevleri <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>belirli <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>bir <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>durumda döndürmek için görev tabanlı eşsenkronize desene (TAP) üç kolaylık yöntemi eklendi.

    Sınıf <xref:System.IO.Pipes.NamedPipeClientStream> şimdi yeni <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>ile asynchronous iletişim destekler. Yöntem.

  - **EventSource artık Olay günlüğüne yazmayı destekler**

    Artık <xref:System.Diagnostics.Tracing.EventSource> sınıfı, makinede oluşturulan mevcut ETW oturumlarına ek olarak, olay günlüğüne yönetim veya operasyonel iletileri günlüğe kaydetmek için kullanabilirsiniz. Geçmişte, bu işlevsellik için Microsoft.Diagnostics.Tracing.EventSource NuGet paketini kullanmanız gerekiyordu. Bu işlevsellik artık yerleşik .NET Framework 4.6'dır.

    Hem NuGet paketi hem de .NET Framework 4.6 aşağıdaki özelliklerle güncellenmiştir:

    - **Dinamik olaylar**

      Olay yöntemleri oluşturmadan "anında" tanımlanan olaylara izin verir.

    - **Zengin yükler**

      Özel olarak atfedilen sınıfların ve dizilerin yanı sıra ilkel türlerin yük olarak geçirilmesine izin verir

    - **Etkinlik izleme**

      Tüm şu anda etkin olan etkinlikleri temsil eden bir kimlikle aralarındaki olayları etiketlemek için Başlat ve Durdur olaylarının başlatılmasına neden olur.

    Bu özellikleri desteklemek için, <xref:System.Diagnostics.Tracing.EventSource.Write%2A> aşırı yüklenen yöntem <xref:System.Diagnostics.Tracing.EventSource> sınıfa eklendi.

- **Windows Presentation Foundation (WPF)**

  - **HDPI iyileştirmeler**

    WPF'de HDPI desteği artık .NET Framework 4.6'da daha iyi. Kenarlıklı denetimlerde kırpma örneklerini azaltmak için düzen yuvarlamada değişiklikler yapıldı. Varsayılan olarak, bu özellik yalnızca <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET 4.6 olarak ayarlanmışsa etkinleştirilir.  Çerçevenin önceki sürümlerini hedefleyen ancak .NET Framework 4.6 üzerinde çalışan uygulamalar, app.config dosyasının [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek yeni davranışı seçebilir:

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    Farklı DPI ayarlarına (Multi-DPI kurulumu) sahip birden fazla monitörü saran WPF pencereleri artık tamamen karartılmış bölgeler olmadan işleniyor. Bu yeni davranışı devre dışı bırakmak için `<appSettings>` app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu davranışı devre dışı bırakmak:

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    DPI ayarına göre sağ imlecin otomatik olarak <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>yüklenmesi için destek eklendi.

  - **Dokunma kiyidir daha iyidir**

    [Connect'in](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) ,.NET Framework 4.6'da öngörülemeyen davranışlar ürettiğine ilişkin müşteri raporları ele alınmıştır. Windows Mağazası uygulamaları ve WPF uygulamaları için çift dokunma eşiği artık Windows 8.1 ve üzeri için aynıdır.

  - **Saydam alt pencere desteği**

    .NET Framework 4.6'daki WPF, Windows 8.1 ve üzeri saydam alt pencereleri destekler. Bu, üst düzey pencerelerinizde dikdörtgen olmayan ve saydam alt pencereler oluşturmanıza olanak tanır. Özelliği `true`' ne ayarlayarak <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> bu özelliği etkinleştirebilirsiniz.

- **Windows Communication Foundation (WCF)**

  - **SSL desteği**

    WCF, artık Aktarım güvenliği ve müşteri kimlik doğrulaması ile NetTcp kullanırken SSL 3.0 ve TLS 1.0'a ek olarak SSL 1.1 ve TLS 1.2 sürümünü desteklemektedir. Artık hangi protokolün kullanılacağını seçmek veya eski daha az güvenli protokolleri devre dışı kullanabilirsiniz. Bu özellik ayarı <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> veya bir yapılandırma dosyasına aşağıdaki ekleyerek yapılabilir.

    ```xml
    <netTcpBinding>
        <binding>
          <security mode= "None|Transport|Message|TransportWithMessageCredential" >
              <transport clientCredentialType="None|Windows|Certificate"
                        protectionLevel="None|Sign|EncryptAndSign"
                        sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                </transport>
          </security>
        </binding>
    </netTcpBinding>
    ```

  - **Farklı HTTP bağlantılarını kullanarak ileti gönderme**

    WCF artık kullanıcıların bazı iletilerin temeldeki farklı HTTP bağlantıları kullanılarak gönderilmesini sağlar. Bunu yapmak için iki yol vardır:

    - **Bağlantı grubu adı öneki kullanma**

      Kullanıcılar, WCF'nin bağlantı grubu adı için önek olarak kullanacağı bir dize belirtebilir. Farklı öneklere sahip iki ileti, temeldeki farklı HTTP bağlantıları kullanılarak gönderilir. İletinin <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> özelliğine bir anahtar/değer çifti ekleyerek önek ayarlayın. Anahtar "HttpTransportConnectionGroupNamePrefix"; değeri istenilen önektir.

    - **Farklı kanal fabrikalarını kullanma**

      Kullanıcılar ayrıca, farklı kanal fabrikaları tarafından oluşturulan kanallar kullanılarak gönderilen iletilerin farklı temel HTTP bağlantılarını kullanmasını sağlayan bir özelliği de etkinleştirebilir. Bu özelliği etkinleştirmek için, `appSetting` `true`kullanıcıların aşağıdakileri ayarlamaları gerekir:

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- **Windows İş Akışı Vakfı (WWF)**

  Artık, isteği zamanlamadan önce olağanüstü bir "protokol dışı" yer imi olduğunda, bir iş akışı hizmetinin sıra dışı bir işlem isteğine tutunacağı saniye sayısını belirtebilirsiniz. "Protokol dışı" yer imi, olağanüstü Alma etkinlikleriile ilgili olmayan bir yer imidir. Bazı etkinlikler, uygulamaları içinde protokol dışı yer imleri oluşturur, bu nedenle protokol dışı bir yer imi olduğu açık olmayabilir. Bunlar arasında Durum ve Seç yer alır. Bu nedenle, bir durum makinesiyle uygulanan veya bir Çekme etkinliği içeren bir iş akışı hizmetiniz varsa, büyük olasılıkla protokol dışı yer imleri olacaktır. App.config dosyanızın `appSettings` bölümüne aşağıdaki gibi bir satır ekleyerek aralığı belirtirsiniz:

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  Varsayılan değer 60 saniyedir. 0 `value` olarak ayarlanırsa, sıra dışı istekler hemen aşağıdaki gibi görünen metinile bir hata ile reddedilir:

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  Bu, sıra dışı bir işlem iletisi alınırsa ve protokol dışı yer imleri yoksa aldığınız iletiyle aynıdır.

  `FilterResumeTimeoutInSeconds` Öğenin değeri sıfır değilse, protokol dışı yer imleri vardır ve zaman aşımı aralığı sona ererse, işlem bir zaman aşımı iletisiyle başarısız olur.

- **İşlemler**

  Artık, atılması <xref:System.Transactions.TransactionException> için türetilen bir özel durum neden olan hareket için dağıtılmış hareket tanımlayıcısı ekleyebilirsiniz. Bunu app.config dosyanızın `appSettings` bölümüne aşağıdaki anahtarı ekleyerek yaparsınız:

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  Varsayılan değer: `false`.

- **Ağ**

  - **Soket yeniden kullanımı**

    Windows 10, giden TCP bağlantıları için yerel bağlantı noktalarını yeniden kullanarak makine kaynaklarını daha iyi kullanan yeni bir yüksek ölçeklenebilirlik ağ algoritması içerir. .NET Framework 4.6 yeni algoritmayı destekleyerek .NET uygulamalarının yeni davranıştan yararlanmasını sağlar. Windows'un önceki sürümlerinde, yük altındayken bağlantı noktası tükenmesine neden olarak bir hizmetin ölçeklenebilirliğini sınırlandırabilecek yapay bir eşzamanlı bağlantı sınırı (genellikle dinamik bağlantı noktası aralığının varsayılan boyutu olan 16.384) vardı.

    .NET Framework 4.6'da, eşzamanlı bağlantılardaki 64 KB sınırını etkili bir şekilde kaldıran bağlantı noktasının yeniden kullanılmasını sağlamak için iki API eklenmiştir:

    - Numaralandırma <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> değeri.

    - Mülk. <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType>

    Varsayılan olarak, <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` kayıt `false` defteri `HWRPortReuseOnSocketBind` anahtarının değeri 0x1 olarak ayarlı değilse, özellik. HTTP bağlantılarında yerel bağlantı noktasının yeniden <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> kullanılmasını `true`etkinleştirmek için özelliği ' ye göre ayarlayın. Bu, yerel bağlantı noktasının yeniden <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest> kullanılmasını sağlayan, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options)yeni bir Windows 10 soketi seçeneğinden gelen ve kullanan tüm Giden TCP soket bağlantılarına neden olur.

    Yalnızca soketlere ait bir <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> uygulama yazan geliştiriciler, <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> giden soketlerin bağlama sırasında yerel bağlantı noktalarını yeniden kullanması için bir yöntem ararken seçeneği belirtebilir.

  - **Uluslararası alan adları ve PunyCode desteği**

    Uluslararası alan <xref:System.Uri.IdnHost%2A>adlarını ve PunyCode'u daha iyi desteklemek için <xref:System.Uri> sınıfa yeni bir özellik eklendi.

- **Windows Forms denetimlerinde yeniden boyutlandırma.**

  Bu özellik .NET Framework 4.6'da <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.ToolStripSplitButton> ve türleri ve <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> bir <xref:System.Drawing.Design.UITypeEditor>.

  Bu bir tercih özelliğidir. Etkinleştirmek için, `EnableWindowsFormsHighDpiAutoResizing` öğeyi `true` uygulama yapılandırmasında (app.config) dosyaya ayarlayın:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Kod sayfası kodlamaları için destek**

  .NET Core öncelikle Unicode kodlamalarını destekler ve varsayılan olarak kod sayfası kodlamaları için sınırlı destek sağlar. .NET Framework'de bulunan ancak .NET Core'da desteklenmeyen kod sayfası kodlamaları için destek <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> ekleyebilir, kod sayfası kodlamalarını yöntemle kaydedebilirsiniz. Daha fazla bilgi için bkz. <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Yerel**

  .NET Core'u hedefleyen ve C# veya Visual Basic ile yazılan Windows 10 için Windows uygulamaları, uygulamaları IL yerine yerel koda derleyen yeni bir teknolojiden yararlanabilir. Daha hızlı başlatma ve yürütme süreleri ile karakterize uygulamalar üretirler. Daha fazla bilgi için [bkz.](../net-native/index.md) Hem JIT derlemesi hem de NGEN'den nasıl farklı olduğunu ve bunun kodunuz için ne anlama geldiğini inceleyen [.NET Native'e](../net-native/net-native-and-compilation.md)genel bir bakış için bkz.

  Uygulamalarınız Visual Studio 2015 veya sonraki yollarla derlediğinizde varsayılan olarak yerel koda göre derlenir. Daha fazla bilgi için [.NET Native ile Başlarken'e](../net-native/getting-started-with-net-native.md)bakın.

  .NET Yerel uygulamaları hata ayıklamayı desteklemek için, yönetilmeyen hata ayıklama API'sine bir dizi yeni arabirim ve numaralandırma eklendi. Daha fazla bilgi için [Hata Ayıklama (Yönetilmeyen API Başvurusu)](../unmanaged-api/debugging/index.md) konusuna bakın.

- **Açık kaynak .NET Framework paketleri**

  .NET Core paketleri gibi değişmez koleksiyonlar, [SIMD API'ler](https://www.nuget.org/packages/Microsoft.Bcl.Simd)ve <xref:System.Net.Http> ağ API'leri gibi ad alanında bulunanlar artık [GitHub'da](https://github.com/)açık kaynak paketleri olarak kullanılabilir. Koda erişmek için [GitHub'daki .NET'e](https://github.com/dotnet/runtime)bakın. Daha fazla bilgi ve bu paketlere nasıl katkıda bulunabilirsiniz, [github'daki](https://github.com/dotnet/home) [.NET Core ve Open-Source](../get-started/net-core-and-open-source.md), .NET Giriş Sayfası'na bakın.

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>.NET Framework 4.5.2'deki yenilikler

- **ASP.NET uygulamalar için yeni API'ler.** Yeni <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> yöntemler, yanıt istemci uygulamasına atılırken yanıt üstbilgilerini ve durum kodunu incelemenize ve değiştirmenize izin sağlar. Olaylar <xref:System.Web.HttpApplication.PreSendRequestHeaders> ve <xref:System.Web.HttpApplication.PreSendRequestContent> olaylar yerine bu yöntemleri kullanmayı düşünün; daha verimli ve güvenilirdirler.

  Yöntem, <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> küçük arka plan çalışma öğeleri zamanlamanızı sağlar. ASP.NET bu öğeleri izler ve IIS'nin tüm arka plan çalışma öğeleri tamamlanana kadar alt işlemi aniden sona erdirmesini engeller. Bu yöntem, ASP.NET yönetilen bir uygulama etki alanının dışında çağrılamaz.

  Yeni <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> özellikler, yanıt üstbilgisinin yazılıp yazılmadığını gösteren Boolean değerlerini döndürür. Bu özellikleri, (üstbilgi yazılmışsa özel <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> durumlar atan) gibi API'lere yapılan çağrıların başarılı olacağından emin olmak için kullanabilirsiniz.

- **Windows Forms denetimlerinde yeniden boyutlandırma.** Bu özellik genişletildi. Şimdi sistem DPI ayarını, aşağıdaki ek denetimlerin bileşenlerini yeniden boyutlandırmak için kullanabilirsiniz (örneğin, açılan kutulardaki açılır ok):

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  Bu bir tercih özelliğidir. Etkinleştirmek için, `EnableWindowsFormsHighDpiAutoResizing` öğeyi `true` uygulama yapılandırmasında (app.config) dosyaya ayarlayın:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- **Yeni iş akışı özelliği.** <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Yöntemi kullanan (ve bu nedenle <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi uygulayan) bir kaynak yöneticisi aşağıdakileri istemek için yeni <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> yöntemi kullanabilir:

  - Hareketi bir Microsoft Dağıtılmış Hareket Koordinatörü (MSDTC) hareketine tanıtın.

  - Tek <xref:System.Transactions.IPromotableSinglePhaseNotification> faz <xref:System.Transactions.ISinglePhaseNotification>taahhüt destekleyen dayanıklı bir listment ile değiştirin.

  Bu, aynı uygulama etki alanı içinde yapılabilir ve promosyongerçekleştirmek için MSDTC ile etkileşim için herhangi bir ekstra yönetilmeyen kod gerektirmez. Yeni yöntem, yalnızca teşvik edilebilir listment tarafından <xref:System.Transactions?displayProperty=nameWithType> uygulanan <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` yönteme olağanüstü bir çağrı olduğunda çağrılabilir.

- **Profil geliştirmeleri.** Aşağıdaki yeni yönetilmeyen profil oluşturma API'leri daha sağlam profil oluşturma sağlar:

  - [COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [COR_PRF_HIGH_MONITOR Sabit Listesi](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [GetAssemblyReferences Yöntemi](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [GetEventMask2 Yöntemi](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [SetEventMask2 Yöntemi](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [AddAssemblyReference Yöntemi](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  Önceki `ICorProfiler` uygulamalar bağımlı derlemelerin tembel yüklenmesi desteklenir. Yeni profil oluşturma API'leri, profil oluşturucu tarafından enjekte edilen bağımlı derlemelerin uygulama tamamen başlatıldıktan sonra yüklenmek yerine hemen yüklenebilmelerini gerektirir. Bu değişiklik, varolan `ICorProfiler` API kullanıcılarını etkilemez.

- **Hata ayıklama iyileştirmeleri.** Aşağıdaki yeni yönetilmeyen hata ayıklama API'leri bir profil oluşturucuyla daha iyi tümleştirme sağlar. Artık profil oluşturucu tarafından eklenen meta verilere ve hata ayıklama yaparken derleyici ReJIT istekleri tarafından üretilen yerel değişkenlere ve koda erişebilirsiniz.

  - [SetWriteableMetadataUpdateMode Yöntemi](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [EnumerateLocalVariablesEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [GetLocalVariableEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [GetCodeEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [GetActiveReJitRequestILCode Yöntemi](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [GetInstrumentedILMap Yöntemi](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Olay izleme değişiklikleri.** .NET Framework 4.5.2, daha büyük bir yüzey alanı için Windows için Olay İzleme (ETW) tabanlı etkinlik izleme işleminin dışında olmasını sağlar. Bu, Gelişmiş Güç Yönetimi (APM) satıcılarının, iş parçacığı arasında tek tek istek ve etkinliklerin maliyetlerini doğru bir şekilde izleyen hafif araçlar sağlamasına olanak tanır.  Bu olaylar yalnızca ETW denetleyicileri etkinleştirildiğinde yükseltilir; bu nedenle, değişiklikler daha önce yazılmış ETW kodunu veya ETW devre dışı ile çalışan kodu etkilemez.

- **Bir işlemin tanıtımı ve dayanıklı bir listeye dönüştürülmesi**

  <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>.NET Framework 4.5.2 ve 4.6'ya eklenen yeni bir API'dir:

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  Yöntem, <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> yönteme yanıt olarak daha önce oluşturulan <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> bir listment tarafından kullanılabilir. Bir `System.Transactions` MSDTC işlemine hareketi tanıtmak ve teşvik edilebilir listeyi dayanıklı bir listeye "dönüştürmek" ister. Bu yöntem başarıyla tamamlandıktan <xref:System.Transactions.IPromotableSinglePhaseNotification> sonra, arabirim artık `System.Transactions`başvurulan olacak ve gelecekteki bildirimler <xref:System.Transactions.ISinglePhaseNotification> sağlanan arabirimde gelecektir. Söz konusu askere alma, işlem günlüğü ve kurtarmayı destekleyen dayanıklı bir liste görevi almalıdır. Ayrıntılar <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> için bakın. Buna ek olarak, askere <xref:System.Transactions.ISinglePhaseNotification>destek olmalıdır.  Bu yöntem *yalnızca* bir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> aramayı işlerken çağrılabilir. Bu durumda değilse, bir <xref:System.Transactions.TransactionException> özel durum atılır.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>.NET Framework 4.5.1'deki yenilikler

**Nisan 2014 güncelleştirmeleri**:

- [Visual Studio 2013 Güncelleştirmesi,](https://go.microsoft.com/fwlink/p/?LinkId=393658) bu senaryoları desteklemek için Taşınabilir Sınıf Kitaplığı şablonlarında güncelleştirmeler içerir:

  - Windows 8.1, Windows Phone 8.1 ve Windows Phone Silverlight 8.1'i hedefleyen taşınabilir kitaplıklarda Windows Runtime API'lerini kullanabilirsiniz.

  - Windows 8.1 veya Windows Phone 8.1'i hedeflediğinizde taşınabilir kitaplıklarda XAML (Windows.UI.XAML türleri) ekleyebilirsiniz. Aşağıdaki XAML şablonları desteklenir: Boş Sayfa, Kaynak Sözlüğü, Şablonlu Denetim ve Kullanıcı Denetimi.

  - Windows 8.1 ve Windows Phone 8.1'i hedefleyen Mağaza uygulamalarında kullanılmak üzere taşınabilir bir Windows Runtime bileşeni (.winmd dosyası) oluşturabilirsiniz.

  - Taşınabilir Sınıf Kitaplığı gibi bir Windows Mağazası veya Windows Phone Mağazası sınıf kitaplığını yeniden hedefleyebilirsiniz.

  Bu değişiklikler hakkında daha fazla bilgi için [Bkz. Taşınabilir Sınıf Kitaplığı.](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)

- .NET Framework içerik kümesi artık Windows uygulamaları oluşturmak ve dağıtmak için bir ön derleme teknolojisi olan .NET Native için belgeler içerir. .NET Native, daha iyi performans için uygulamalarınızı ara dile (IL) değil, doğrudan yerel koda derler. Ayrıntılar için [.NET Native ile Uygulamaları Derleme'ye](../net-native/index.md)bakın.

- [.NET Framework Reference Source](https://referencesource.microsoft.com/) yeni bir tarama deneyimi ve gelişmiş işlevsellik sağlar. Artık .NET Framework kaynak koduna çevrimiçi olarak göz atabilir, çevrimdışı görüntüleme için [başvuruyu indirebilir](https://referencesource.microsoft.com/download.html) ve hata ayıklama sırasında kaynaklara (düzeltme ekinler ve güncelleştirmeler dahil) adım atabilirsiniz. Daha fazla bilgi için blog girişine bakın [.NET Referans Kaynağı için yeni bir görünüm.](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)

.NET Framework 4.5.1'deki temel sınıflardaki yeni özellikler ve geliştirmeler şunlardır:

- Derlemeler için otomatik bağlama yeniden yönlendirme. Visual Studio 2013'ten başlayarak,.NET Framework 4.5.1'i hedefleyen bir uygulamayı derlediğinizde, uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvuruyorsa, uygulama yapılandırma dosyasına bağlama yönlendirmeleri eklenebilir. Bu özelliği,.NET Framework'ün eski sürümlerini hedefleyen projeler için de etkinleştirebilirsiniz. Daha fazla bilgi için [bkz: Otomatik Bağlama Yönlendirmesini Etkinleştirme ve Devre Dışı Kaldırma.](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)

- Geliştiricilerin sunucu ve bulut uygulamalarının performansını artırmasına yardımcı olmak için tanılama bilgilerini toplama becerisi. Daha fazla bilgi <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> için, sınıftaki yöntemlere ve <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metotlara <xref:System.Diagnostics.Tracing.EventSource> bakın.

- Çöp toplama sırasında büyük nesne yığınını (LOH) açıkça sıkıştırma yeteneği. Daha fazla bilgi <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> için tesise bakın.

- ASP.NET uygulama süspansiyonu, çok çekirdekli JIT iyileştirmeleri ve .NET Framework güncellemeden sonra daha hızlı uygulama başlatma gibi ek performans iyileştirmeleri. Ayrıntılar için [.NET Framework 4.5.1 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) bakın ve ASP.NET uygulaması blog gönderisini [askıya alın.](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/)

Windows Formlarında iyileştirmeler şunlardır:

- Windows Forms denetimlerinde yeniden boyutlandırma. Uygulama yapılandırma dosyasındaki (app.config) bir girişi uygulama yapılandırma dosyasında (app.config) seçerek denetimbileşenlerini (örneğin, özellik ızgarasında görünen simgeler) yeniden boyutlandırmak için sistem DPI ayarını kullanabilirsiniz. Bu özellik şu anda aşağıdaki Windows Forms denetimlerinde desteklenir:

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - Bazı yönleri <xref:System.Windows.Forms.DataGridView> (desteklenen ek denetimler için [4.5.2'deki yeni özelliklere](#v452) bakın)

  Bu özelliği etkinleştirmek için \<yapılandırma dosyasına (app.config) yeni bir `EnableWindowsFormsHighDpiAutoResizing` uygulama `true`Ayarlar> öğesi ekleyin ve öğeyi şu şekilde ayarlayın:

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

Visual Studio 2013'te .NET Framework uygulamalarınızı hata ayıklarken ki geliştirmeler şunlardır:

- Visual Studio hata ayıklamasında değerleri döndürün. Visual Studio 2013'te yönetilen bir uygulamayı hata ayıklamayaptığınızda, Otomatik ler penceresi yöntemler için iade türlerini ve değerlerini görüntüler. Bu bilgiler masaüstü, Windows Mağazası ve Windows Phone uygulamaları için kullanılabilir. Daha fazla bilgi için bkz. [yöntem çağrılarının return değerlerini incele.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120))

- 64 bit uygulamalar için edit ve devam et. Visual Studio 2013, masaüstü, Windows Mağazası ve Windows Phone için 64 bit yönetilen uygulamalar için Edit ve Continue özelliğini destekler. Varolan sınırlamalar hem 32 bit hem de 64 bit uygulamalar için geçerli liğini korur [(Desteklenen Kod Değişiklikleri (C#)](/visualstudio/debugger/supported-code-changes-csharp) makalesinin son bölümüne bakın).

- Async-aware hata ayıklama. Visual Studio 2013'te eşzamanlı uygulamaları hata ayıklamayı kolaylaştırmak için çağrı yığını, toplayıcılar tarafından sağlanan altyapı kodunu gizleyerek eşzamanlı programlamayı destekler ve mantıksal üst çerçevelerde zincirler oluşturarak mantıksal program yürütmesini daha fazla takip edebilirsiniz Açıkça. Görevler penceresi Paralel Görevler penceresinin yerini alır ve belirli bir kesme noktasıyla ilgili görevleri görüntüler ve uygulamada şu anda etkin veya zamanlanmış diğer görevleri görüntüler. Bu özelliği [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"Async-aware hata ayıklama" bölümünde n için okuyabilirsiniz.

- Windows Runtime bileşenleri için daha iyi özel durum desteği. Windows 8.1'de, Windows Mağazası uygulamalarından kaynaklanan özel durumlar, dil sınırları nın ötesinde bile özel durumlara neden olan hata yla ilgili bilgileri korur. Bu özelliği [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"Windows Mağazası uygulama geliştirme" bölümünden okuyabilirsiniz.

Visual Studio 2013'ten itibaren, Windows 8.x Store uygulamalarının yanı sıra masaüstü uygulamalarını optimize etmek için [Yönetilen Profil Destekli Optimizasyon Aracı'nı (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) kullanabilirsiniz.

ASP.NET 4.5.1'deki yeni özellikler [için Visual Studio 2013 Sürüm Notları için ASP.NET ve Web Araçları'na](/aspnet/visual-studio/overview/2013/release-notes)bakın.

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>.NET Framework 4.5'teki yenilikler

### <a name="base-classes"></a>Temel sınıflar

- Dağıtım sırasında .NET Framework 4 uygulamalarını algılayıp kapatarak sistemin yeniden başlatılmasını azaltma becerisi. Bkz. [.NET Framework 4.5 Kurulumları Sırasında Sistem Yeniden Başlatma](../deployment/reducing-system-restarts.md).

- 64 bit platformlarda 2 gigabayttan (GB) daha büyük diziler için destek. Bu özellik uygulama yapılandırma dosyasında etkinleştirilebilir. Ayrıca nesne boyutu ve dizi boyutu diğer kısıtlamaları listeler [gcAllowVeryLargeObjects> öğesi ne bakın. \<](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)

- Sunucular için arka plan çöp toplama yoluyla daha iyi performans. .NET Framework 4.5'te sunucu çöp toplama yı kullandığınızda, arka plan çöp toplama otomatik olarak etkinleştirilir. Çöp Toplama konusunun [Temelleri](../../standard/garbage-collection/fundamentals.md) bölümüne bakınız.

- Uygulama performansını artırmak için isteğe bağlı olarak çok çekirdekli işlemcilerde kullanılabilen tam zamanında (JIT) derleme. Bkz. <xref:System.Runtime.ProfileOptimization>.

- Normal ifade altyapısının ne kadar süreyle normal bir ifadeyi zaman ları aşmadan önce çözmeye çalışacağını sınırlama yeteneği. Araziyi <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> görün.

- Bir uygulama etki alanı için varsayılan kültürü tanımlama yeteneği. Sınıfa <xref:System.Globalization.CultureInfo> bak.

- Unicode (UTF-16) kodlaması için konsol desteği. Sınıfa <xref:System.Console> bak.

- Kültürel dize sıralama ve karşılaştırma verilerinin sürümü için destek. Sınıfa <xref:System.Globalization.SortVersion> bak.

- Kaynakları alırken daha iyi performans. Bkz. [Kaynakları Paketleme ve Dağıtma.](../resources/packaging-and-deploying-resources-in-desktop-apps.md)

- Sıkıştırılmış bir dosyanın boyutunu azaltmak için zip sıkıştırma iyileştirmeleri. <xref:System.IO.Compression?displayProperty=nameWithType> Ad alanına bakın.

- Sınıf boyunca varsayılan yansıma davranışını geçersiz kılmak <xref:System.Reflection.Context.CustomReflectionContext> için yansıma bağlamını özelleştirme yeteneği.

- Sınıf Windows 8'de kullanıldığında Uygulamalarda UluslararasıLaştırılmış Alan Adları (IDNA) <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> standardının 2008 sürümü için destek.

- .NET Framework Windows 8'de kullanıldığında Unicode 6.0'ı uygulayan işletim sistemiyle string karşılaştırması delegasyonu. Diğer platformlarda çalışırken,.NET Framework, Unicode 5.x'i uygulayan kendi dize karşılaştırma verilerini içerir. <xref:System.String> Sınıfın sınıf ve Açıklamalar bölümüne <xref:System.Globalization.SortVersion> bakın.

- Uygulama etki alanı bazında dizeleri için karma kodları hesaplama yeteneği. [ \<Bkz. UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Tür yansıma desteği <xref:System.Type> <xref:System.Reflection.TypeInfo> ve sınıflar arasında bölünmüş. [Windows Mağazası Uygulamaları için .NET Çerçevesi'ndeki Yansıma'ya](../reflection-and-codedom/reflection-for-windows-store-apps.md)bakın.

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

.NET Framework 4.5'te Yönetilen Genişletilebilirlik Çerçevesi (MEF) aşağıdaki yeni özellikleri sağlar:

- Genel türleri için destek.

- Öznitelikler yerine adlandırma geleneklerine dayalı parçalar oluşturmanıza olanak tanıyan kural kuralı tabanlı programlama modeli.

- Birden fazla kapsam.

- Windows 8.x Store uygulamaları oluştururken kullanabileceğiniz MEF alt kümesi. Bu alt küme NuGet Galerisi'nden [indirilebilir](https://www.nuget.org/packages/Microsoft.Composition) paket olarak kullanılabilir. Paketi yüklemek için Projenizi Visual Studio'da açın, **Proje** menüsünden `Microsoft.Composition` **NuGet Paketlerini Yönet'i** seçin ve paketi çevrimiçi arayın.

Daha fazla bilgi için Yönetilen [Genişletilebilirlik Çerçevesi 'ne (MEF)](../mef/index.md)bakın.

### <a name="asynchronous-file-operations"></a>Asynchronous dosya işlemleri

.NET Framework 4.5'te C# ve Visual Basic dillerine yeni eşzamanlı özellikler eklendi. Bu özellikler, eşzamanlı işlemleri gerçekleştirmek için görev tabanlı bir model ekler. Bu yeni modeli kullanmak için G/Ç sınıflarında eşzamanlı yöntemleri kullanın. Bkz. [Eşzamanlı Dosya I/O](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Araçlar

.NET Framework 4.5'te, Kaynak Dosya Oluşturucusu (Resgen.exe), Windows 8.x Store uygulamalarında kullanılmak üzere bir .resw dosyası oluşturmanıza olanak tanır. Daha fazla bilgi için Bkz. [Resgen.exe (Kaynak Dosya Üreteci)](../tools/resgen-exe-resource-file-generator.md).

Yönetilen Profil Destekli Optimizasyon (Mpgo.exe), uygulama başlangıç süresini, bellek kullanımını (çalışma kümesi boyutunu) ve yerel görüntü derlemelerini optimize ederek iş oluşturmayı geliştirmenizi sağlar. Komut satırı aracı, yerel görüntü uygulama derlemeleri için profil verileri oluşturur. Bkz. [Mpgo.exe (Yönetilen Profil Güdümlü Optimizasyon Aracı)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Visual Studio 2013'ten itibaren, Windows 8.x Store uygulamalarının yanı sıra masaüstü uygulamalarını optimize etmek için Mpgo.exe'yi kullanabilirsiniz.

<a name="parallel" />

### <a name="parallel-computing"></a>Paralel bilgi işlem

.NET Framework 4.5, paralel bilgi işlem için çeşitli yeni özellikler ve geliştirmeler sağlar. Bunlar arasında geliştirilmiş performans, artırılmış denetim, eşzamanlı programlama için geliştirilmiş destek, yeni bir veri akışı kitaplığı ve paralel hata ayıklama ve performans çözümlemesi için geliştirilmiş destek yer almaktadır. .NET blogu ile [Paralel Programlama'da .NET 4.5'te Paralellik için Yenilikler](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) girişine bakın.

<a name="web" />

### <a name="web"></a>Web

ASP.NET 4.5 ve 4.5.1 Web Formları, WebSocket desteği, eşzamanlı işleyiciler, performans geliştirmeleri ve diğer birçok özellik için model bağlama ekleyin. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [ASP.NET 4.5 ve Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [Visual Studio 2013 için ASP.NET and Web Tools Sürüm Notları](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a>Ağ<a name="networking" />

.NET Framework 4.5, HTTP uygulamaları için yeni bir programlama arabirimi sağlar. Daha fazla bilgi için <xref:System.Net.Http?displayProperty=nameWithType> <xref:System.Net.Http.Headers?displayProperty=nameWithType> yeni ve ad alanlarına bakın.

Mevcut ve ilgili sınıfları kullanarak <xref:System.Net.HttpListener> bir WebSocket bağlantısını kabul etmek ve onlarla etkileşimde bulunan yeni bir programlama arabirimi için destek de dahildir. Daha fazla bilgi için <xref:System.Net.WebSockets> yeni ad <xref:System.Net.HttpListener> alanına ve sınıfa bakın.

Buna ek olarak, .NET Framework 4.5 aşağıdaki ağ geliştirmelerini içerir:

- RFC uyumlu URI desteği. Daha fazla bilgi <xref:System.Uri> için bkz.

- Uluslararası Alan Adı (IDN) ayrıştırma desteği. Daha fazla bilgi <xref:System.Uri> için bkz.

- E-posta Adresi Uluslararasılaştırma (EAI) desteği. Daha fazla bilgi <xref:System.Net.Mail> için ad alanına bakın.

- Geliştirilmiş IPv6 desteği. Daha fazla bilgi <xref:System.Net.NetworkInformation> için ad alanına bakın.

- Çift modlu soket desteği. Daha fazla bilgi <xref:System.Net.Sockets.Socket> için <xref:System.Net.Sockets.TcpListener> sınıflara ve sınıflara bakın.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.5'te, Windows Sunu Vakfı (WPF) aşağıdaki alanlarda değişiklikler ve iyileştirmeler içerir:

- Hızlı <xref:System.Windows.Controls.Ribbon.Ribbon> Erişim Araç Çubuğu, Uygulama Menüsü ve sekmeler barındıran bir şerit kullanıcı arabirimi uygulamanızı sağlayan yeni denetim.

- Senkron <xref:System.ComponentModel.INotifyDataErrorInfo> ve eşzamanlı veri doğrulamayı destekleyen yeni arabirim.

- <xref:System.Windows.Controls.VirtualizingPanel> Ve <xref:System.Windows.Threading.Dispatcher> sınıflar için yeni özellikler.

- Büyük gruplanmış veri kümelerini görüntülerken ve UI dışı iş parçacıklarındaki koleksiyonlara erişerek performansı artırıldı.

- Statik özelliklere veri bağlama, <xref:System.Reflection.ICustomTypeProvider> arabirimi uygulayan özel türlere veri bağlama ve bağlayıcı bir ifadeden veri bağlama bilgisi alma.

- Değerler değiştikçe verilerin yeniden konumlandırılması (canlı şekillendirme).

- Madde kapsayıcısının veri bağlamınının kesilip kesilmediğini denetleme yeteneği.

- Özellik değişiklikleri ve veri kaynağı güncelleştirmeleri arasında zaman dilimini ayarlama yeteneği.

- Zayıf olay kalıplarını uygulamak için geliştirilmiş destek. Ayrıca, olaylar artık biçimlendirme uzantılarını kabul edebilir.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

.NET Framework 4.5'te, Windows Communication Foundation (WCF) uygulamalarının yazılması ve sürdürülmesini kolaylaştırmak için aşağıdaki özellikler eklenmiştir:

- Oluşturulan yapılandırma dosyalarının basitleştirilmesi.

- Sözleşmenin ilk geliştirilmesi için destek.

- uyumluluk modunu daha kolay yapılandırma ASP.NET.

- Bunları ayarlamak zorunda kalma olasılığını azaltmak için varsayılan aktarım özelliği değerlerinde değişiklikler.

- XML <xref:System.Xml.XmlDictionaryReaderQuotas> sözlük okuyucuları için kotaları el ile yapılandırmanız gereken olasılığı azaltmak için sınıfa yapılan güncelleştirmeler.

- WCF yapılandırma dosyalarının Visual Studio tarafından yapı işleminin bir parçası olarak doğrulanması, böylece uygulamanızı çalıştırmadan önce yapılandırma hatalarını algılayabilirsiniz.

- Yeni asynchronous akış desteği.

- Internet Information Services (IIS) ile HTTPS üzerinden bir bitiş noktasını ortaya çıkarmak için yeni HTTPS protokolü eşlemi.

- Hizmet URL'sine ekleyerek `?singleWSDL` tek bir WSDL belgesinde meta veri oluşturma yeteneği.

- Websockets, TCP taşımasına benzer performans özellikleriyle 80 ve 443 bağlantı noktaları üzerinden gerçek çift yönlü iletişimi etkinleştirmek için destek sağlar.

- Hizmetleri kodda yapılandırma desteği.

- XML Düzenleyici araç ipuçları.

- <xref:System.ServiceModel.ChannelFactory>önbelleğe alma desteği.

- İkili kodlayıcı sıkıştırma desteği.

- Geliştiricilerin "yangın ve unut" iletisi kullanan hizmetler yazmalarını sağlayan bir UDP aktarım desteği. İstemci bir hizmete ileti gönderir ve hizmetten yanıt beklemez.

- HTTP aktarım ve aktarım güvenliğini kullanırken tek bir WCF bitiş noktasında birden çok kimlik doğrulama modunu destekleme yeteneği.

- Uluslararası etki alanı adları (IDN' ler) kullanan WCF hizmetleri için destek.

Daha fazla bilgi için [Windows Communication Foundation'da Yenilikler](../wcf/whats-new.md)bölümüne bakın.

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

.NET Framework 4.5'te, Windows İş Akışı Temeli'ne (WF) aşağıdakiler dahil olmak üzere birçok yeni özellik eklendi:

- İlk olarak .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1)](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)kapsamında tanıtılan devlet makine iş akışları. Bu güncelleştirme, geliştiricilerin durum makine iş akışları oluşturmasına olanak sağlayan birkaç yeni sınıf ve etkinlik içeriyordu. Bu sınıflar ve etkinlikler .NET Framework 4.5 için aşağıdakileri içerecek şekilde güncelleştirildi:

  - Devletlerüzerinde kesme noktaları ayarlama yeteneği.

  - İş akışı tasarımcısındaki geçişleri kopyalama ve yapıştırabilme yeteneği.

  - Paylaşılan tetikleyici geçiş oluşturma için tasarımcı desteği.

  - Devlet makine iş akışları oluşturmak için <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State>etkinlikler, <xref:System.Activities.Statements.Transition>dahil: , , ve .

- Aşağıdakiler gibi geliştirilmiş İş Akışı Tasarımcısı özellikleri:

  - Visual Studio'da **Hızlı Bul** ve **Dosyalarda Bul**dahil olmak üzere gelişmiş iş akışı arama özellikleri.

  - Bir kapsayıcı etkinliğine ikinci bir alt etkinlik eklendiğinde otomatik olarak Sıra etkinliği oluşturma ve her iki etkinliği de Sıra lı etkinliklere dahil etme yeteneği.

  - Kaydırma çubukları kullanmadan iş akışının görünür bölümünün değiştirilmesini sağlayan kaydırma desteği.

  - Ağaç stili anahat görünümünde iş akışının bileşenlerini gösteren ve **Belge Anahat** görünümünde bir bileşen seçmenize olanak tanıyan yeni bir Belge **Anahat** görünümü.

  - Etkinliklere ek açıklamalar ekleme yeteneği.

  - İş akışı tasarımcısını kullanarak etkinlik temsilcilerini tanımlama ve tüketme becerisi.

  - Durum makinesi ve akış şeması iş akışlarındaki etkinlikler ve geçişler için otomatik bağlanma ve otomatik ekleme.

- XAML dosyasındaki tek bir öğedeki iş akışı için görünüm durumu bilgilerinin depolanması, böylece görünüm durumu bilgilerini kolayca bulabilir ve edebilirsiniz.

- Alt etkinliklerin devam etmesini önlemek için Bir NoPersistScope kapsayıcı etkinliği.

- C# ifadeleri için destek:

  - Visual Basic kullanan iş akışı projeleri Visual Basic ifadelerini, C# iş akışı projeleri ise C# ifadelerini kullanır.

  - Visual Studio 2010'da oluşturulan ve Visual Basic ifadelerine sahip C# iş akışı projeleri, C# ifadelerini kullanan C# iş akışı projeleri ile uyumludur.

- Sürüm geliştirmeleri:

  - Kalıcı <xref:System.Activities.WorkflowIdentity> iş akışı örneği ile iş akışı tanımı arasında eşleme sağlayan yeni sınıf.

  - Aynı ana bilgisayarda birden çok iş akışı sürümü de <xref:System.ServiceModel.Activities.WorkflowServiceHost>dahil olmak üzere yan yana yürütme.

  - Dinamik Güncelleştirme'de, kalıcı iş akışı örneğinin tanımını değiştirme yeteneği.

- Varolan bir hizmet sözleşmesiyle eşleşecek otomatik olarak oluşturma etkinlikleri için destek sağlayan sözleşmeye bağlı ilk iş akışı hizmeti geliştirme.

Daha fazla bilgi için [Windows İş Akışı Temelinde Yeniliklere](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)bakın.

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a>Windows 8.x Mağazası uygulamaları için .NET

Windows 8.x Store uygulamaları belirli form faktörleri için tasarlanmıştır ve Windows işletim sisteminin gücünden yararlanır. .NET Framework 4.5 veya 4.5.1 alt kümesi, C# veya Visual Basic kullanarak Windows 8.x Store uygulamalarını oluşturmak için kullanılabilir. Bu alt küme, Windows 8.x Store uygulamaları için .NET olarak adlandırılır ve [genel bir bakışta](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))tartışılır.

### <a name="portable-class-libraries"></a>Taşınabilir Sınıf Kütüphaneleri<a name="portable" />

Visual Studio 2012'deki Taşınabilir Sınıf Kitaplığı projesi (ve sonraki sürümler) birden çok .NET Framework platformunda çalışan yönetilen derlemeler yazmanızı ve oluşturmanızı sağlar. Taşınabilir Sınıf Kitaplığı projesini kullanarak, hedeflemek için platformları (Windows Phone ve .NET windows 8.x Store uygulamaları için) seçersiniz. Projenizdeki kullanılabilir türler ve üyeler, bu platformlardaki ortak türler ve üyelerle otomatik olarak sınırlıdır. Daha fazla bilgi için Bkz. [Taşınabilir Sınıf Kitaplığı.](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ve Bant Dışı Yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
- [.NET Framework'de erişilebilirlikte yenilikler](whats-new-in-accessibility.md)
- [Visual Studio 2017'de Yenilikler](/visualstudio/ide/whats-new-visual-studio-2017)
- [Visual Studio 2019'da Yenilikler](/visualstudio/ide/whats-new-visual-studio-2019)
- [ASP.NET](/aspnet)
- [Visual Studio'da C++ İçin Yenilikler](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
