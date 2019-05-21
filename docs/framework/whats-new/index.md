---
title: .NET Framework'teki yenilikler
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81995d8003a9bb78f6a97ca7eadca94a2136c8a7
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960009"
---
# <a name="whats-new-in-the-net-framework"></a>.NET Framework'teki yenilikler

Bu makalede, önemli yeni özellikler ve geliştirmeler aşağıdaki .NET Framework sürümlerinde özetlenmektedir:

- [.NET framework 4.8](#v48)
- [.NET framework 4.7.2](#v472)
- [.NET framework 4.7.1](#v471)
- [.NET framework 4.7](#v47)
- [.NET framework 4.6.2](#v462)
- [.NET framework 4.6.1](#v461)
- [.NET 2015 ve .NET Framework 4.6](#v46)
- [.NET framework 4.5.2](#v452)
- [.NET framework 4.5.1](#v451)
- [.NET Framework 4.5](#v45)

Bu makale, her yeni özellik hakkında kapsamlı bilgi sağlamaz ve değiştirilebilir. .NET Framework hakkında genel bilgi için bkz. [Başlarken](../get-started/index.md). Desteklenen platformlar için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md). Yükleme yönergeleri ve indirme bağlantıları [Yükleme Kılavuzu](../install/guide-for-developers.md).

> [!NOTE]
> .NET Framwork takımındaki özellikleri ile NuGet platform desteğini artırmak ve değişmez koleksiyonlar ve SIMD etkin vektör türlerinin gibi yeni işlevleri tanıtmak için bant dışı da serbest bırakır. Daha fazla bilgi için [ek sınıf kitaplıkları ve API'ler](../additional-apis/index.md) ve [.NET Framework ve bant dışı yayınlar](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Bkz: bir [NuGet paketlerini tam listesi](https://www.nuget.org/profiles/dotnetframework) .NET Framework için.

<a name="v48" />

## <a name="introducing-net-framework-48"></a>.NET Framework 4.8 ile tanışın

.NET framework 4.8 derlemeler .NET Framework'ün önceki sürümlerinde çok kararlı bir ürüne kalan sırasında birçok yeni düzeltmeyi ve çeşitli yeni özellikler ekleyerek 4.x.

### <a name="downloading-and-installing-net-framework-48"></a>.NET Framework 4.8 yükleyip

.NET Framework 4.8 aşağıdaki konumlardan indirebilirsiniz:

- [.NET framework 4.8 Web yükleyicisi](https://go.microsoft.com/fwlink/?LinkId=2085155)

- [4.8 NET Framework çevrimdışı yükleyici](https://go.microsoft.com/fwlink/?linkid=2088631)

.NET framework 4.8 Windows 10, Windows 8.1, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak, karşılık gelen sunucu platformları yüklenebilir. Web yükleyicisini veya çevrimdışı yükleyiciyi kullanarak .NET Framework 4.8 yükleyebilirsiniz. Çoğu kullanıcı için önerilen yol, web yükleyicisi kullanmaktır.

.NET Framework 4.8 Visual Studio 2012 veya daha sonra yükleyerek hedefleyebilir [.NET Framework 4.8 Geliştirici paketi](https://go.microsoft.com/fwlink/?LinkId=2085167).

### <a name="whats-new-in-net-framework-48"></a>.NET Framework 4.8 yenilikler

.NET framework 4.8 aşağıdaki alanlarda yeni özellik bulunmaktadır:

- [Temel sınıflar](#core48)
- [Windows Communication Foundation (WCF)](#wcf48)
- [Windows Presentation Foundation (WPF)](#wpf48)
- [Ortak dil çalışma zamanı](#clr48)

Yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak için uygulamanın veren geliştirilmiş Erişilebilirlik önemli bir .NET Framework 4.8 odağı olmaya devam eder. .NET Framework 4.8'teki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik .NET Framework'teki yenilikler](whats-new-in-accessibility.md).

<a name="core48" />

#### <a name="base-classes"></a>Temel sınıflar

**Şifreleme için FIPS etkisi azaltılmış**. Önceki .NET Framework sürümlerinde şifreleme sağlayıcısı sınıfları gibi yönetilen <xref:System.Security.Cryptography.SHA256Managed> throw bir <xref:System.Security.Cryptography.CryptographicException> sistem şifreleme kitaplıklarını "FIPS modunda" yapılandırılmış zaman. Sistem şifreleme kitaplıkları, farklı bir şifreleme sağlayıcısı sınıfları yönetilen sürümleri (Federal Bilgi işleme standartları) FIPS 140-2 sertifikası yapılmamıştır çünkü bu özel durumlar. Bazı geliştiriciler, geliştirme makinelerinde FIPS modunda olduğundan, yaygın olarak üretim sistemlerine özel durumlar.

.NET Framework 4.8 hedefleyen uygulamalarda varsayılan olarak, artık aşağıdaki yönetilen şifreleme sınıflarını throw bir <xref:System.Security.Cryptography.CryptographicException> bu durumda:

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

Bunun yerine, bu sınıflar, sistem şifreleme kitaplığa şifreleme işlemleri yönlendirin. Bu değişikliğin etkili bir şekilde olası karmaşık birbirinden Geliştirici ortamlarını ve üretim ortamlarını kaldırır ve yerel bileşenlerin yapar ve yönetilen bileşenleri aynı şifreleme ilkesi altında çalışır. Bu özel durumları bağlı uygulamalar geri yükleyebilir, önceki davranışı AppContext anahtarı ayarlayarak `Switch.System.Security.Cryptography.UseLegacyFipsThrow` için `true`. Daha fazla bilgi için [yönetilen şifreleme sınıflarını değil throw bir CryptographyException FIPS modunda](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).

**ZLib güncelleştirilmiş sürümünü kullan**

.NET Framework 4.5 ile başlayarak, clrcompression.dll derlemeyi kullanacak [ZLib](https://www.zlib.net), veri sıkıştırma, deflate algoritmasını için bir uygulama sağlamak için yerel bir dış kitaplık. .NET Framework 4.8 clrcompression.dll ZLib birkaç önemli geliştirmeleri ve düzeltmeleri içeren sürümünü 1.2.11, kullanacak şekilde güncelleştirilir.

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

**ServiceHealthBehavior giriş**

Sistem durumu uç noktaları, düzenleme araçları tarafından sistem durumlarına göre hizmetleri yönetmek için yaygın olarak kullanılır. Sistem durumu denetimleri de izleme araçları tarafından izlemek ve hizmetin performans ve kullanılabilirlik ile ilgili bildirimleri sağlamak için kullanılabilir.

**ServiceHealthBehavior** genişleten bir WCF Hizmeti davranış <xref:System.ServiceModel.Description.IServiceBehavior>.  Eklenen <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> koleksiyonu, bir hizmet davranışını şunları yapar:

- HTTP yanıt kodları ile sistem durumu hizmeti, döndürür. Bir sorgu dizesinde HTTP/GET sistem durumu araştırması isteği için HTTP durum kodu belirtebilirsiniz.

- Hizmet durumu hakkında bilgileri yayımlar. Hizmet durumu dahil olmak üzere, hizmete özgü ayrıntıları kısıtlama sayıları ve kapasite ile bir HTTP/GET isteği kullanılarak görüntülenebilir `?health` sorgu dizesi. Bu bilgilere erişim kolaylığı davranan bir WCF hizmeti sorunlarını giderirken önemlidir.

Sistem durumu uç noktasını ortaya çıkarır ve WCF hizmet durumu bilgilerini yayımlamak için iki yolu vardır:

- Kod. Örneğin:

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  if (healthBehavior == null)
  {
     healthBehavior = new ServiceHealthBehavior();
  }
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

- Bir yapılandırma dosyası kullanarak. Örneğin:

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

Bir hizmetin sistem durumu gibi sorgu parametrelerini kullanarak sorgulanabilir `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), ve her bir sorgu parametresi için bir HTTP yanıt kodu belirtilebilir. 503 bir HTTP yanıt kodu, HTTP yanıt kodu için bir sorgu parametresi atlanırsa, varsayılan olarak kullanılır. Örneğin:

- OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`

  Ne zaman 450 bir HTTP yanıtı durum kodu döndürülür [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) büyüktür <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.
Sorgu parametreleri ve örnekleri:

- OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`

  Herhangi bir kanal dağıtıcıları durumunu daha büyük olduğunda 455 bir HTTP yanıtı durum kodu döndürülür <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`

  Herhangi bir kanal dinleyicileri durumunu daha büyük olduğunda 465 bir HTTP yanıtı durum kodu döndürülür <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.

- OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`

  Yanıt ve HTTP yanıt kodunu {200-599} tetikleyen {1: 100} yüzdesini belirtir. Bu örnekte:

    - Yüzde 95'ten büyükse, 500 bir HTTP yanıt kodu döndürülür.

    - Varsa yüzdesi veya 70 ila 95 arasında 350 döndürülür.

    - Aksi takdirde, 200 döndürülür.

Hizmet durumu olabilir ya da HTML gibi bir sorgu dizesi belirterek görüntülenen `https://contoso:81/Service1?health` veya XML gibi bir sorgu dizesi belirterek `https://contoso:81/Service1?health&Xml`. Bir sorgu dizesi ister `https://contoso:81/Service1?health&NoContent` boş HTML sayfası döndürür.

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Yüksek DPI geliştirmeleri**

.NET Framework 4.8 WPF, Windows V2 İzleyici başına DPI tanıma ve karma mod DPI ölçeklendirme desteği ekler. Bkz: [Windows üzerinde yüksek DPI Masaüstü uygulama geliştirme](/desktop/hidpi/high-dpi-desktop-application-development-on-windows) yüksek DPI geliştirme hakkında ek bilgi için.

.NET framework 4.8 artırır, karışık modlu DPI ölçeklendirme destekleyen platformlarda yüksek DPI WPF uygulamalarında barındırılan Cwnd'lerden ve Windows Forms olan birlikte çalışma için destek (başlatma ile Windows 10 Nisan 2018 güncelleştirmesi). Barındırılan Cwnd'lerden ya da Windows Formları denetimleri oluştururken karışık mod DPI ölçeklendirilmiş olarak windows çağırarak [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) ve [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), içinde barındırılabilen bir İzleyici başına V2 WPF uygulaması ve bu boyutlandırıldığından ve uygun şekilde ölçeklendirilebilir. Bu tür barındırılan içeriğin Yerel DPİ'de işlenmez; Bunun yerine, işletim sistemi barındırılan içerik uygun boyuta ölçeklendirir. Monitör başına v2 DPI tanıma modu desteği de barındırılacak bir WPF denetimleri sağlar (yani, shapemap) yerel bir yüksek DPI uygulama penceresinde.

Karma mod yüksek DPI ölçeklendirmesini desteğini etkinleştirmek için aşağıdakileri ayarlayabilirsiniz [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) uygulama yapılandırma dosyasına geçer:

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a>Ortak dil çalışma zamanı

Çalışma zamanı'nda .NET Framework 4.8 aşağıdaki değişiklikleri ve geliştirmeleri içerir:

**JIT derleyicisine yönelik geliştirmeler**. .NET Framework 4.8 olarak Just-ın-time (JIT) derleyici, JIT derleyicisi, .NET Core 2.1 dayanır. Birçok iyileştirmeleri ve hata düzeltmeleri için .NET Core 2.1 JIT derleyicisi yapılan tüm .NET Framework 4.8 JIT Derleyici dahil edilir.

**NGEN geliştirmeleri**. Çalışma zamanı için kendi bellek yönetimini geliştirdi [Native Image Generator](../tools/ngen-exe-native-image-generator.md) NGEN görüntülerinin eşlenen verilerin bellekte böylece (NGEN) görüntüler. Bu da, yürütülecek bellek değiştirerek rastgele kod yürütmek için deneyen saldırıları için kullanılabilir'ın yüzey alanını azaltır.

**Kötü amaçlı yazılımdan koruma için tüm bütünleştirilmiş kodları taranıyor**. Önceki .NET Framework sürümlerinde, Windows Defender'ı veya üçüncü taraf kötü amaçlı yazılımdan koruma yazılımları kullanarak diskten yüklenen tüm derlemeler çalışma zamanı tarar. Ancak, yüklenen derlemeleri diğer kaynaklardan gelen, gibi tarafından <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> yöntemi değil taranır ve potansiyel olarak algılanmayan kötü amaçlı yazılım içerebilir. Windows 10 üzerinde .NET Framework 4.8 ile başlayarak, çalışma zamanı bir tarama uygulayan kötü amaçlı yazılımdan koruma çözümleri tarafından tetikler [kötü amaçlı yazılımdan koruma tarama arabirimi (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a>4.7.2 .NET Framework'teki yenilikler

.NET framework 4.7.2 aşağıdaki alanlarda yeni özellikler içerir:

- [Temel sınıflar](#core-472)
- [ASP.NET](#asp-net472)
- [Ağ](#net472)
- [SQL](#sql472)
- [WPF](#wpf472)
- [ClickOnce](#clickonce)

Bir akışta 4.7.2 .NET Framework'teki yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak için uygulamanın veren geliştirilmiş erişilebilirlik biridir. .NET Framework'teki 4.7.2 erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik .NET Framework'teki yenilikler](whats-new-in-accessibility.md).

<a name="core-472" />

#### <a name="base-classes"></a>Temel sınıflar

.NET framework 4.7.2 çok sayıda şifreleme geliştirmelerinden, ZIP arşivlerini ve ek koleksiyon API'leri daha iyi sıkıştırma desteği sunar.

**RSA yeni aşırı yüklemeleri. Oluşturma ve DSA. Oluşturma**

<xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> Ve <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> yöntemleri, yeni bir örneği oluşturulurken anahtar parametreleri sağlamanıza olanak tanır <xref:System.Security.Cryptography.DSA> veya <xref:System.Security.Cryptography.RSA> anahtarı. Kod aşağıdaki gibi değiştirin olanak sağlar:

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

şunun gibi kod ile:

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

<xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> Ve <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> yöntemleri yeni oluşturmanıza izin <xref:System.Security.Cryptography.DSA> veya <xref:System.Security.Cryptography.RSA> belirli bir anahtar boyutu anahtarı. Örneğin:

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

**Rfc2898DeriveBytes oluşturucular bir karma algoritması adı kabul edin.**

<xref:System.Security.Cryptography.Rfc2898DeriveBytes> Sınıfında üç yeni oluşturucularla bir <xref:System.Security.Cryptography.HashAlgorithmName> anahtarları türetilirken kullanılacak HMAC algoritmasını tanımlar parametresi. SHA-1 kullanmak yerine, geliştiriciler gibi SHA-256, SHA-2 tabanlı bir HMAC aşağıdaki örnekte gösterildiği gibi kullanmanız gerekir:

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

**Kısa ömürlü anahtarlar için destek**

PFX alma, özel anahtarları isteğe bağlı olarak sabit sürücüyü atlayarak bellekten doğrudan yükleyebilirsiniz. Zaman yeni <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> bayrağı belirtilen bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> oluşturucu veya aşırı yüklemelerinden birini <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> yöntemi özel anahtarlar kısa ömürlü anahtarlar olarak yüklenir. Bu anahtarları diskte görünür olmasını önler. Ancak:

- Disk için sertifikalar ile yüklenen anahtarları sürdürülmeyen olduğundan bu bayrağı için bir X509Store eklemek için iyi adaylar değildir.

- Bu şekilde yüklenen anahtarları, neredeyse her zaman Windows CNG yüklenir. Bu nedenle, Arayanların özel anahtarı genişletme yöntemleri çağırarak erişmesi gereken [sertifika. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A). <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> Özelliği çalışmaz.

- Eski beri <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> özelliği sertifikalarla çalışmıyor, geliştiriciler için kısa ömürlü anahtarlar geçmeden önce sıkı testlerden gerçekleştirmesi gereken.

**PKCS #10 sertifika imzalama isteği X.509 ortak anahtar sertifikaları ve program oluşturma**

.NET Framework 4.7.2 ile başlayarak, iş yüklerini olanak sağlayan araçları içine aşamalandırılacak sertifika isteği oluşturma isteği (CSR) imzalama sertifikası oluşturabilirsiniz. Bu, sık test senaryolarda yararlıdır.

Daha fazla bilgi ve kod örnekleri için bkz. "programlı oluşturulmasını PKCS #10 sertifika imzalama istekleri ve ortak anahtar sertifikaları X.509" içinde [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Yeni SignerInfo üyeler**

4.7.2, .NET Framework ile başlayarak <xref:System.Security.Cryptography.Pkcs.SignerInfo> sınıfı imza hakkında daha fazla bilgi gösterir. Değerini alabilir <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> imzalayan tarafından kullanılan imza algoritmasını belirlemek için özellik. <xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> Bu imzalayan için şifreleme imzası bir kopyasını almak için çağrılabilir.

**Sarmalanan bir akış CryptoStream bırakıldıktan sonra açık bırakın**

4.7.2, .NET Framework ile başlayarak <xref:System.Security.Cryptography.CryptoStream> sınıfında sağlayan ek bir Oluşturucuda <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> Sarmalanan akış kapatmadığınızdan. Sarmalanan akış sonra açık bırakmak <xref:System.Security.Cryptography.CryptoStream> örneği kullanıldığında, yeni bir çağrı <xref:System.Security.Cryptography.CryptoStream> Oluşturucu aşağıdaki gibi:

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

**DeflateStream açma değişiklikleri**

.NET Framework 4.7.2, açma işlemleri uygulamasını başlayarak <xref:System.IO.Compression.DeflateStream> sınıfı, varsayılan olarak yerel Windows API'ları kullanacak şekilde değiştirildi. Genellikle, bu önemli performans geliştirmeyle sonuçlanır.

Windows API'leri kullanarak açma desteği, .NET Framework 4.7.2 hedefleyen uygulamalar için varsayılan olarak etkindir. .NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 altında çalışan uygulamalar özelliğini bu davranışı aşağıdakileri ekleyerek [AppContext anahtar](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) için uygulama yapılandırma dosyası:

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

**Ek koleksiyon API'leri**

.NET framework 4.7.2 ekler için yeni API'ler birkaç <xref:System.Collections.Generic.SortedSet%601> ve <xref:System.Collections.Generic.HashSet%601> türleri. Bu güncelleştirmeler şunlardır:

- `TryGetValue` Bu iki tür diğer koleksiyon türlerine kullanılan deneyin deseni genişletme yöntemleri. Yöntemler şunlardır:

   - [Genel bool HashSet\<T >. TryGetValue (T actualValue kullanıma T equalValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
   - [Genel bool SortedSet\<T >. TryGetValue (T actualValue kullanıma T equalValue)](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- `Enumerable.To*` bir koleksiyona Dönüştür genişletme yöntemleri, bir <xref:System.Collections.Generic.HashSet%601>:

   - [Genel statik HashSet\<Tkaynak > ToHashSet\<Tkaynak > (Bu IEnumerable\<Tkaynak > kaynak)](xref:System.Linq.Enumerable.ToHashSet%2A)
   - [Genel statik HashSet\<Tkaynak > ToHashSet\<Tkaynak > (Bu IEnumerable\<Tkaynak > kaynak IEqualityComparer\<Tkaynak > karşılaştırıcı)](xref:System.Linq.Enumerable.ToHashSet%2A)

- Yeni <xref:System.Collections.Generic.HashSet%601> olanak tanıyan oluşturucular bir performans kazancı boyutunu bildiğinizde veren koleksiyonun kapasitesi ayarlama <xref:System.Collections.Generic.HashSet%601> önceden:

   - [Genel HashSet (int Kapasite)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))
   - [Genel HashSet (int kapasite IEqualityComparer\<T > karşılaştırıcı)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))

<xref:System.Collections.Concurrent.ConcurrentDictionary%602> Sınıfı içeren yeni aşırı yüklemeleri <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> yöntemleri sözlükten bir değer almak veya değil bulunursa ve eklemek için sözlük veya zaten varsa güncelleştirmek için bir değer ekleyin.

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

**Web Forms bağımlılık ekleme desteği**

[Bağımlılık ekleme (dı)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) böylece nesnenin kod artık yalnızca bir bağımlılık değiştiği için değiştirilmesi gereken nesneleri ve bunların bağımlılıklarını ayırır. .NET Framework'ü 4.7.2 hedefleyen ASP.NET uygulamaları geliştirirken, aşağıdakileri yapabilirsiniz:

- Ayarlayıcı, arabirimi ve oluşturucu tabanlı yerleştirmeye kullanın [işleyicileri ve modülleri](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [sayfasında örnekleri](xref:System.Web.UI.Page), ve [kullanıcı denetimleri](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET web uygulaması projeleri.

- Ayarlayıcı ve arabirim tabanlı yerleştirmeye kullanın [işleyicileri ve modülleri](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [sayfasında örnekleri](xref:System.Web.UI.Page), ve [kullanıcı denetimleri](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ASP.NET web sitesi projeleri.

- Farklı bağımlılık ekleme çerçeveleri takın.

**Aynı sitede tanımlama bilgileri için destek**

[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) bir tarayıcı siteler arası istek birlikte bir tanımlama bilgisi göndermesini engeller. .NET framework 4.7.2 ekler bir <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> özellik değeri olan bir <xref:System.Web.SameSiteMode?displayProperty=nameWithType> numaralandırma üyesi. Öğenin değeri ise <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> veya <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET ekler `SameSite` özniteliği için set-cookie üstbilgisi. SameSite destek uygulandığı <xref:System.Web.HttpCookie> , de olarak nesneleri için <xref:System.Web.Security.FormsAuthentication> ve <xref:System.Web.SessionState> tanımlama bilgileri.

SameSite için ayarlayabileceğiniz bir <xref:System.Web.HttpCookie> gibi nesnesi:

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

Web.config dosyasını değiştirerek SameSite tanımlama bilgileri uygulama düzeyinde de yapılandırabilirsiniz:

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

SameSite için ekleyebilirsiniz <xref:System.Web.Security.FormsAuthentication> ve <xref:System.Web.SessionState> web yapılandırma dosyasını değiştirerek tanımlama bilgileri:

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   <authentication />
   <sessionSate cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a>Ağ Oluşturma

**Uygulama HttpClientHandler özellikleri**

.NET framework 4.7.1 eklenen sekiz özelliklerine <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> sınıfı. Ancak, iki oluşturdu bir <xref:System.PlatformNotSupportedException>. .NET framework 4.7.2, artık bu özellikleri bir uygulamasını sağlar. Özellikler şunlardır:

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a>SQLClient

**Azure Active Directory Evrensel kimlik doğrulaması ve çok faktörlü kimlik doğrulaması için destek**

Birçok müşteri, çok faktörlü kimlik doğrulaması (MFA) kullanır, büyüyen uyumluluk ve güvenlik taleplerini gerektirir. Ayrıca, kullanıcı parolalarını doğrudan bağlantı dizeleri dahil olmak üzere geçerli en iyi önleyin. Bu değişiklikleri desteklemek için .NET Framework 4.7.2 genişletir [SQLClient bağlantı dizeleri](xref:System.Data.SqlClient.SqlConnection.ConnectionString) , "Active Directory etkileşimli" mfa'yı desteklemek mevcut "Authentication" anahtar sözcüğü için yeni bir değer ekleyerek ve [Azure AD Kimlik doğrulaması](/azure/sql-database/sql-database-aad-authentication-configure). Yeni etkileşimli yöntem, yerel destekler ve Azure AD kullanıcıları, hem de Konuk kullanıcıları Azure AD Federasyon. Bu yöntem kullanıldığında, Azure AD tarafından uygulanan MFA kimlik doğrulaması SQL veritabanları için desteklenir. Ayrıca, kimlik doğrulama işlemi için en iyi güvenlik uygulamaları uyması için bir kullanıcı parolasını ister.

SQL bağlantısı yalnızca desteklenen .NET Framework'ün önceki sürümlerindeki <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> ve <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> seçenekleri. Bunların her ikisi de etkileşimli olmayan parçası olan [ADAL Protokolü](/azure/active-directory/develop/active-directory-authentication-libraries), mfa'yı desteklemez. Yeni <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> seçeneği, SQL Bağlantısı destekler MFA yanı sıra mevcut kimlik doğrulama yöntemleri (parola ve tümleşik kimlik doğrulaması), kullanıcıların etkileşimli olarak kalıcı bir parola olmadan kullanıcı parolalarını bağlantı girmesine izin veren dize.

Daha fazla bilgi ve örnek için "SQL--Azure AD evrensel ve çok faktörlü kimlik doğrulaması desteği" bölümüne bakın [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).

**Always Encrypted sürüm 2 için destek**

NET Framework 4.7.2 destekler, her zaman kuşatma tabanlı şifreli için ekler. Always Encrypted özgün sürümü, şifreleme anahtarları istemci hiçbir zaman ayrılmaz bir istemci tarafı şifreleme teknolojisidir. Kuşatma tabanlı Always Encrypted istemci isteğe bağlı olarak şifreleme anahtarlarını SQL sunucu kodunu değiştirmesine olamaz ancak bu bölümü SQL Server'ın kabul edilebilir bir güvenli bilgi işlem bir varlık bir güvenli kuşatma gönderebilirsiniz. Kuşatma tabanlı Always Encrypted desteklemek için .NET Framework 4.7.2 Aşağıdaki türler ve üyeler için ekler <xref:System.Data.SqlClient> ad alanı:

- <xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, her zaman kuşatma tabanlı şifreli için URI belirtir.

- <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, sağlayıcıları tüm hangi kuşatma türetilen bir soyut sınıf.

- <xref:System.Data.SqlClient.SqlEnclaveSession>, belirli kuşatma oturum açmak için durumu kapsüller.

- <xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, belirli bir kanıtlama protokol yürütmek için gerekli bilgileri almak için SQL Server tarafından kullanılan kanıtlama parametrelerini sağlar.

Uygulama yapılandırma dosyasına ardından Özet somut bir uyarlamasını belirtir <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> kuşatma sağlayıcı için işlevsellik sağlayan sınıf. Örneğin:

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

Kuşatma tabanlı Always Encrypted, temel akışı şöyledir:

1. Kullanıcı bir kuşatma tabanlı Always Encrypted'ı desteklenen bir SQL Server AlwaysEncrypted bağlantısı oluşturur. Sürücü için doğru kuşatma bağlandığını emin olmak için kanıtlama hizmeti ile iletişim kurar.

1. Kuşatma TPM'de sonra sürücü SQL sunucusu üzerinde barındırılan güvenli kuşatma ile güvenli bir kanal oluşturur.

1. Sürücü şifreleme anahtarlarını SQL Bağlantısı süresince güvenli kuşatma istemcisiyle yetkilendiren paylaşır.

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a>Windows Presentation Foundation

**Kaynağa göre ResourceDictionaries bulma**

.NET Framework 4.7.2 ile başlayarak, bir tanılama Yardımcısı bulabilirsiniz <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> belirli bir kaynaktan URI oluşturuldu. (Bu özellik için tanılama yardımcılar, üretim uygulamaları tarafından kullanılır.) Visual Studio'nun "Düzenle-ve devam et" tesisi gibi bir tanılama Yardımcısı, kendi kullanıcı değişiklik çalışan uygulamaya uygulanması amacıyla ResourceDictionary düzenleme olanak tanır. Bunu elde etmenin de tek bir adımda, uygulama çalışırken, düzenlenmekte olan sözlükten oluşturduğu tüm ResourceDictionaries buluyor. Örneğin, uygulama içeriği URI belirli bir kaynaktan kopyalanır ResourceDictionary bildirebilirsiniz:

```xml
<ResourceDictionary Source="MyRD.xaml">
```

Özgün işaretlemede düzenler bir tanılama Yardımcısı *MyRD.xaml* yeni özelliği sözlük bulmak için kullanabilirsiniz. Yeni bir statik yöntem tarafından uygulanan özellik <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>. Tanılama Yardımcısı özgün biçimlendirme tanımlayan bir mutlak URI aşağıdaki kodda gösterildiği gibi kullanarak yeni yöntemini çağırır:

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

Kullanıcı hikayesinin sürece yöntem boş bir numaralandırılabilir'e döndürür. <xref:System.Windows.Diagnostics.VisualDiagnostics> etkinleştirilir ve [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ortam değişkeninin ayarlı.

**Bulma ResourceDictionary sahipleri**

.NET Framework 4.7.2 ile başlayarak, bir tanılama Yardımcısı sahipleri bulabilirsiniz bir verilen <xref:Windows.UI.Xaml.ResourceDictionary>. (Özellik tanılama yardımcıları ve üretim uygulamaları tarafından kullanımı için geçerlidir.) Her bir değişiklik yapıldığında için bir <xref:Windows.UI.Xaml.ResourceDictionary>, WPF otomatik olarak bulur tüm [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) değişiklik tarafından etkilenebilecek başvuruları.

Visual Studio'nun "Düzenle-ve devam et" tesisi gibi bir tanılama Yardımcısı işlemek için bunu genişletmek isteyebilirsiniz [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvuruları. Bu işlem ilk adımında sözlük sahipleri bulun, diğer bir deyişle, tüm nesneleri bulmak için `Resources` özelliği sözlüğe başvurur (doğrudan veya dolaylı olarak aracılığıyla <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> özelliği). Üç yeni statik yöntemler üzerinde uygulanan <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> sınıfı, bir sahip temel türlerinin her biri için bir `Resources` özelliği, bu adımı destekler:

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

Kullanıcı hikayesinin sürece bu yöntemler boş numaralandırılabilir'e döndürür. <xref:System.Windows.Diagnostics.VisualDiagnostics> etkinleştirilir ve [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ortam değişkeninin ayarlı.

**StaticResource başvuruları bulma**

Tanılama Yardımcısı artık bildirim alabilir her bir [StaticResource](../wpf/advanced/staticresource-markup-extension.md) çözümlenen başvuru. (Özellik tanılama yardımcılar, üretim uygulamaları tarafından kullanımı için geçerlidir.) Bir tanılama Yardımcısı "Düzenle-ve devam et" Visual Studio'nun tesisi gibi bir kaynak tüm kullanımları güncelleştirmek isteyebilirsiniz, değeriyle bir <xref:Windows.UI.Xaml.ResourceDictionary> değişiklikler. WPF bunu otomatik olarak yapar [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvuruları, ancak isteyerek değil bunu [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvuruları. .NET Framework 4.7.2 ile başlayarak, tanılama Yardımcısı, bu kullanımları statik kaynak bulmak için bu bildirimleri kullanabilirsiniz.

Bildirim yeni tarafından uygulanan <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> olay:

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

Çalışma zamanı çözümler olduğunda bu olayı bir [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvuru. <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> Bağımsız değişkenleri çözümü açıklayın ve nesne ve özellik barındıran belirtmek [StaticResource](../wpf/advanced/staticresource-markup-extension.md) başvuru ve <xref:Windows.UI.Xaml.ResourceDictionary> ve çözümlemesi için kullanılan anahtarı:

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
Public Class StaticResourceResolvedEvcentArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

Olayı değil oluşturulur (ve kendi `add` erişimci göz ardı edilir) sürece <xref:System.Windows.Diagnostics.VisualDiagnostics> etkinleştirilir ve [ `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ortam değişkeninin ayarlı.

#### <a name="clickonce"></a>ClickOnce

HDPI kullanan uygulamalar için Office (VSTO) Windows Formları, Windows Presentation Foundation (WPF) ve Visual Studio Araçları için tüm ClickOnce kullanarak dağıtabilirsiniz. Dağıtım, uygulama bildiriminde şu girdiyi bulunursa, .NET Framework 4.7.2 altında başarılı olur:

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

Windows Forms uygulaması için uygulama yapılandırma dosyası uygulama bildirimi yerine DPI tanıma ayarı önceki çözümün artık başarılı olması ClickOnce dağıtımı için gerekli değildir.

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a>.NET Framework 4.7.1 yenilikler

.NET framework 4.7.1 aşağıdaki alanlarda yeni özellikler içerir:

- [Temel sınıflar](#core471)
- [Ortak dil çalışma zamanı (CLR)](#clr)
- [Ağ](#net471)
- [ASP.NET](#asp-net471)

Ayrıca, bir önemli .NET Framework 4.7.1 yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak için uygulamanın veren geliştirilmiş erişilebilirlik biridir. .NET Framework 4.7.1'teki erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik .NET Framework'teki yenilikler](whats-new-in-accessibility.md).

<a name="core471" />

#### <a name="base-classes"></a>Temel sınıflar

**.NET Standard 2.0 desteği**

[.NET standard](~/docs/standard/net-standard.md) bir standart sürümünün desteklediği her .NET uygulamasında kullanılabilir olması gereken bir API kümesi tanımlar. .NET framework 4.7.1 tam .NET Standard 2.0 destekler ve ekler [yaklaşık 200 API'leri](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) .NET Standard 2.0 içinde tanımlanır ve .NET Framework 4.6.1, 4.6.2 ve 4.7 eksik. (Yalnızca .NET Standard ek destek dosyalarını hedef sistem üzerinde de dağıtılıyorsa, .NET Framework'ün bu sürümlerini .NET Standard 2.0 desteklediğini unutmayın.) Daha fazla bilgi için "BCL – .NET Standard 2.0 desteği" bölümüne bakın. [.NET Framework 4.7.1 çalışma zamanı ve derleyici özelliklerini](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisi.

**Yapılandırma oluşturucular için destek**

Yapılandırma oluşturucular ekleme ve uygulamaları için yapılandırma ayarlarını çalışma zamanında dinamik olarak oluşturmak geliştiricilerin olanak tanır. Özel yapılandırma Oluşturucular, var olan bir yapılandırma bölümünü verileri değiştirmek için veya bir yapılandırma bölümü tamamen sıfırdan oluşturmak için kullanılabilir. Yapılandırma oluşturucular olmadan .config statik dosyalardır ve ayarlarını bir uygulama başlatılmadan önce biraz zaman tanımlanır.

Özel yapılandırma Oluşturucu oluşturmak için oluşturucu Özet türetilen <xref:System.Configuration.ConfigurationBuilder> sınıf ve geçersiz kılma kendi <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> ve <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Ayrıca, Oluşturucular, .config dosyasında tanımlayın. "Yapılandırma oluşturucular" bölümünde daha fazla bilgi için bkz. [.NET Framework 4.7.1 ASP.NET ve yapılandırma özelliklerine](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisi.

**Çalışma zamanı özelliği algılama**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> Sınıfı bir mekanizma sağlar önceden tanımlanmış bir özellik belirli bir .NET uygulaması derleme zamanı veya çalışma zamanı üzerinde desteklenip desteklenmediğini belirlemek için. Derleme zamanında derleyici, belirtilen bir alan özelliği desteklenip desteklenmediğini belirlemek için mevcut olup olmadığını kontrol edebilirsiniz; Bu durumda, bu özellik yararlanır kodu yayar. Çalışma zamanında bir uygulama çağırabilirsiniz <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> zamanında kodu yayan önce yöntemi. Daha fazla bilgi için [çalışma zamanı tarafından desteklenen özellikler açıklamak için yardımcı yöntemi ekleyin](https://github.com/dotnet/corefx/issues/17116).

**Değer Tanımlama grubu türleri, seri hale getirilebilir**

.NET Framework 4.7.1, ile başlayarak <xref:System.ValueTuple?displayProperty=nameWithType> ve onun ilişkili bir genel türler olarak işaretlenmiş [Serializable](xref:System.SerializableAttribute), ikili serileştirme sağlar. Bu geçişi tanımlama grubu türleri gibi yapmalısınız <xref:System.Tuple%603> ve <xref:System.Tuple%604>, daha kolay değer tanımlama grubu türleri için. Daha fazla bilgi için "Derleyici--ValueTuple olan seri hale getirilebilir" bölümüne bakın [.NET Framework 4.7.1 çalışma zamanı ve derleyici özelliklerini](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisi.

**Salt okunur başvurular için destek**

.NET framework 4.7.1 ekler <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>. Bu öznitelik, dil derleyiciler tarafından salt okunur başvuru dönüş türleri veya parametreleri sahip üyeler işaretlemek için kullanılır. Daha fazla bilgi için bkz: "Derleyici--desteği için ReadOnlyReferences" [.NET Framework 4.7.1 çalışma zamanı ve derleyici özelliklerini](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisi. Başvuru dönüş değerleri hakkında daha fazla bilgi için bkz: [Ref yerel öğeler (C# Kılavuzu) dönüş değerleri ve ref](~/docs/csharp/programming-guide/classes-and-structs/ref-returns.md) ve [başvuru dönüş değerleri (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />

#### <a name="common-language-runtime-clr"></a>Ortak dil çalışma zamanı (CLR)

**Çöp toplama performans geliştirmeleri**

.NET Framework 4.7.1 çöp toplama (GC) değişiklikleri özellikle büyük nesne yığını (LOH) ayırmalar için genel performansı iyileştirin. .NET Framework 4.7.1, farklı kilit LOH ayırmaları arka plan GC (BGC) SOH Süpürme saldırısı yapılabilir meydana gelmesini sağlayan küçük nesne yığını (SOH) ve LOH ayırmalar için kullanılır. Sonuç olarak, çok sayıda LOH ayırmaları uygulamalar ayırma kilit çakışması ve Gelişmiş performans azalmasına görmeniz gerekir. Daha fazla bilgi için bkz. "Çalışma zamanı--GC performans geliştirmeleri" bölümünde [.NET Framework 4.7.1 çalışma zamanı ve derleyici özelliklerini](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisi.

<a name="net471"/>

#### <a name="networking"></a>Ağ Oluşturma

**Message.HashAlgorithm SHA-2 desteği**

.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> desteklenen özellik değerlerini <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> ve <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> yalnızca. .NET Framework 4.7.1, ile başlayarak <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, ve <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> de desteklenir. Bu değeri gerçekten kullanılıp kullanılmadığını MSMQ üzerinde beri bağlıdır <xref:System.Messaging.Message> örneğin kendisini hiçbir karma yapar ancak yalnızca değerleri için MSMQ geçirir. Daha fazla bilgi için "Message.HashAlgorithm SHA-2 desteği" bölümüne bakın. [.NET Framework 4.7.1 ASP.NET ve yapılandırma özelliklerini](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisi.

<a name="asp-net471" />

#### <a name="aspnet"></a>ASP.NET

**ASP.NET uygulamalarında, yürütme adımları**

ASP.NET 23 olayları içeren önceden tanımlanmış bir işlem hattı isteklerini işler. ASP.NET her olay işleyicisi, bir yürütme adımı olarak yürütür. ASP.NET, ASP.NET, .NET Framework 4.7 kadar sürümlerinde, yerel ve yönetilen iş parçacıkları arasında geçiş nedeniyle yürütme bağlamı geçirilemez. Bunun yerine, ASP.NET seçmeli olarak yalnızca akış <xref:System.Web.HttpContext>. .NET Framework 4.7.1, ile başlayarak <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> yöntemi modülleri çevresel verileri geri yüklemek de sağlar. Bu özellik uygulama yürütme flow hakkında önemli izleme, profil oluşturma, tanılama veya işlemleri, örneğin, ilgili kitaplıkları hedef alır. Daha fazla bilgi için bkz: "ASP.NET yürütme adım özelliği" [.NET Framework 4.7.1 ASP.NET ve yapılandırma özelliklerine](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisi.

**ASP.NET HttpCookie ayrıştırma**

.NET framework 4.7.1 içeren yeni bir yöntem <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, oluşturmak için standartlaştırılmış bir yol sağlayan bir <xref:System.Web.HttpCookie> nesnesi bir dizeden ve doğru bir şekilde sona erme tarihi ve yol gibi tanımlama bilgisi değerleri atayın. Daha fazla bilgi için bkz: "ASP.NET ayrıştırma HttpCookie" [.NET Framework 4.7.1 ASP.NET ve yapılandırma özelliklerine](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisi.

**ASP.NET formları kimlik doğrulama bilgileri için SHA-2 karma seçenekleri**

.NET Framework 4.7 ve önceki sürümlerinde, ASP.NET geliştiricileri, yapılandırma dosyalarında MD5 veya SHA1 kullanarak kullanıcı kimlik bilgileriyle karma parolaları depolamak izin. .NET Framework 4.7.1 ile başlayarak, ASP.NET SHA256, SHA384 ve SHA512 gibi yeni güvenli SHA-2 karma seçeneklerini de destekler. Varsayılan olarak SHA1 kalır ve varsayılan olmayan karma algoritma web yapılandırma dosyası içinde tanımlanabilir. Örneğin:

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

## <a name="whats-new-in-net-framework-47"></a>.NET Framework 4.7 yenilikler

.NET framework 4.7, aşağıdaki alanlarda yeni özellikler içerir:

- [Temel sınıflar](#Core47)
- [Ağ](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Yeni API'lerin bir listesi için .NET Framework 4.7 eklediğiniz için bkz: [.NET Framework 4.7 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) GitHub üzerinde. Özellik geliştirmeleri ve .NET Framework 4.7 hata düzeltmelerinin listesi için bkz. [.NET Framework 4.7 değişiklikler listesi](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) GitHub üzerinde.  Ek bilgi için bkz: [.NET Framework 4.7 Duyurusu](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) .NET blogunda.

<a name="Core47" />

#### <a name="base-classes"></a>Temel sınıflar

.NET framework 4.7 artırır seri hale getirme tarafından <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Gelişmiş işlevler Eliptik Eğri Şifrelemesi (ECC)***

.NET Framework 4.7, `ImportParameters(ECParameters)` yöntemler eklendi <xref:System.Security.Cryptography.ECDsa> ve <xref:System.Security.Cryptography.ECDiffieHellman> zaten yerleşik bir anahtarını temsil eden bir nesne için izin vermek için sınıflar. Bir `ExportParameters(Boolean)` yöntemi, açık eğri parametreleri kullanarak anahtarı dışa aktarmak için de eklenmiştir.

.NET framework 4.7 ayrıca ek eğrileri (Brainpool eğri paketine dahil) için destek ekler ve kolay olan oluşturma yeni aracılığıyla önceden tanımlanmış tanımlarında eklemiştir <xref:System.Security.Cryptography.ECDsa.Create%2A> ve <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> Fabrika yöntemleri.

Gördüğünüz bir [.NET Framework 4.7 şifreleme geliştirmeleri örneği](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) GitHub üzerinde.

**DataContractJsonSerializer denetim karakterleriyle için daha iyi destek**

.NET Framework 4.7, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> denetim karakterleri ECMAScript 6 standart in conformity with serileştirir. Bu davranış, .NET Framework 4.7 hedefleyen uygulamalar için varsayılan olarak etkindir ve katılım özelliği, .NET Framework 4.7 altında çalışan ancak .NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için. Daha fazla bilgi için [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />

#### <a name="networking"></a>Ağ Oluşturma

.NET framework 4.7, aşağıdaki ağ ile ilgili özellik ekler:

**TLS protokolleri için varsayılan işletim sistemi desteği***

Tarafından kullanılan TLS yığın <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve HTTP, FTP ve SMTP gibi yukarı yığını bileşenlerini geliştiricilerin işletim sistemi tarafından desteklenen varsayılan TLS protokolleri kullanmasına olanak tanır. Geliştiriciler hiçbir uzun sabit kodlu bir TLS sürümü gerekir.

<a name="ASP-NET47" />

#### <a name="aspnet"></a>ASP.NET

.NET Framework 4.7 ASP.NET, aşağıdaki yeni özellikler içerir:

**Nesne önbelleği genişletilebilirliği**

ASP.NET, .NET Framework 4.7 ile başlayarak, yeni bir varsayılan ASP.NET uygulamaları'nesnesi bellek içi önbelleğe alma ve bellek izlemesi için değiştirilecek geliştiricilerin API kümesi ekler. ASP.NET uygulaması yeterli değilse, geliştiricilerin artık aşağıdaki üç bileşeni birini değiştirebilirsiniz:

- **Nesne önbelleği Store**. Yeni bir önbellek sağlayıcıları yapılandırması Bölümü'ı kullanarak, geliştiricilerin yeni bir ASP.NET uygulaması için bir nesne önbelleği uygulamalarında yeni kullanarak takılabilir **ICacheStoreProvider** arabirimi.

- **Bellek izlemesi**. ASP.NET'te varsayılan belleği izleme işlemi için yapılandırılmış özel bayt sınırına yakın çalışırken veya makine üzerinde kullanılabilir toplam fiziksel RAM'in düşük olduğunda uygulamalara bildirir. Bu sınırlar yaklaştığında bildirim tetiklenir. Bazı uygulamalar için bildirimler için yararlı tepkiler izin verecek şekilde yapılandırılmış sınırları çok yakın tetiklenir. Geliştiriciler artık varsayılan değiştirmek için kendi bellek izleyiciler yazma <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> özelliği.

- **Bellek sınırı tepkiler**. Varsayılan olarak, ASP.NET nesne önbelleği trim ve düzenli aralıklarla çağırmayı dener <xref:System.GC.Collect%2A?displayProperty=nameWithType> özel bayt işlem sınırına yakın olduğunda. Bazı uygulamalarda, çağrıları sıklığını <xref:System.GC.Collect%2A?displayProperty=nameWithType> veya verimsiz kırpılır önbellek miktarı. Geliştiriciler artık değiştirin veya varsayılan davranışı abone olarak ek **IObserver** uygulamanın bellek izleme uygulamaları.

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WCF), aşağıdaki özellikler ve değişiklikleri ekler:

**TLS 1.1 veya TLS 1.2 varsayılan ileti güvenlik ayarlarını yapılandırma yeteneği**

.NET Framework 4.7 ile başlayarak, WCF, TLS 1.1 veya ek olarak SSL 3.0 ve TLS 1.0, TLS 1.2 varsayılan ileti güvenlik protokolü olarak yapılandırmanıza olanak sağlar. Bu bir katılım ayardır; Bunu etkinleştirmek için şu girişi, uygulama yapılandırma dosyasına eklemeniz gerekir:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

**WCF serileştirme ile WCF uygulamaları ve güvenilirlik düzeyi artırıldı**

WCF yarış durumlarını engellemeye kod değişiklikleri, böylece performans ve güvenilirlik seri hale getirme seçeneklerinin iyileştirme içerir. Bu güncelleştirmeler şunlardır:

- Zaman uyumsuz ve zaman uyumlu kod çağrılarında karıştırmak için daha iyi destek **SocketConnection.BeginRead** ve **SocketConnection.Read**.
- Bir bağlantı ile iptal ediliyor, Gelişmiş güvenilirlik **SharedConnectionListener** ve **DuplexChannelBinder**.
- Geliştirilmiş Güvenilirlik seri hale getirme işlemlerinin çağrılırken <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> yöntemi.
- Geliştirilmiş Güvenilirlik bir garson çağırarak kaldırırken **ChannelSynchronizer.RemoveWaiter** yöntemi.

<a name="wf47" />

#### <a name="windows-forms"></a>Windows Forms

.NET Framework 4.7 Windows Forms yüksek DPI izleyiciler için desteği geliştirir.

**Yüksek DPI desteği**

.NET Framework 4.7, .NET Framework'ü hedefleyen uygulamalar ile başlayarak Windows Forms uygulamaları için yüksek DPI ve dinamik DPI özellikleri destekler. Yüksek DPI desteği düzeninin ve görünümünün formlar ve denetimler yüksek DPI monitörde artırır. Dinamik DPI düzeninin ve görünümünün biçimlerini değiştirir ve kullanıcı çalışan bir uygulamanın DPI veya görüntü ölçek faktörü değiştiğinde denetler.

Yüksek DPI desteği, tanımlayarak yapılandırdığınız bir katılım özelliğidir bir [ \<System.Windows.Forms.ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) uygulama yapılandırma dosyasının bir bölümünde. Yüksek DPI desteği ve dinamik DPI desteği, Windows Form uygulamanıza ekleme ile ilgili daha fazla bilgi için bkz: [Windows Forms'ta yüksek DPI desteği](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

WPF, .NET Framework 4.7 aşağıdaki geliştirmeleri içerir:

**Windows WM_POINTER iletileri dayalı bir dokunma/ekran kalemi yığını için destek**

Şimdi temel bir dokunma/ekran kalemi yığını kullanılarak seçeneğiniz [WM_POINTER iletileri](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) yerine Windows mürekkep Hizmetleri Platform'nı (WISP). Bu bir katılım .NET Framework'teki özelliğidir. Daha fazla bilgi için [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**WPF API'leri yazdırma için yeni uygulama**

WPF API'leri yazdırmak <xref:System.Printing.PrintQueue?displayProperty=nameWithType> çağrı Windows sınıfı [yazdırma belge paket API](/windows/desktop/printdocs/tailored-app-printing-api) kullanım dışı yerine [XPS yazdırma API](/windows/desktop/printdocs/xps-printing). Uygulama uyumluluğu üzerinde bu değişikliğin etkisini için bkz: [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a>.NET Framework 4.6.2 yenilikler

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Aşağıdaki alanlarda yeni özellikler içerir:

- [ASP.NET](#ASPNET462)

- [Karakter kategorileri](#Strings)

- [Şifreleme](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation'a](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#clickonce-1)

- [Windows Forms ve WPF uygulamaları UWP uygulamalarına dönüştürme](#UWPConvert)

- [Hata ayıklama iyileştirmeleri](#Debug462)

Yeni API'lerin bir listesi .NET Framework 4.6.2 eklediğiniz için bkz: [.NET Framework 4.6.2 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) GitHub üzerinde. Özellik geliştirmeleri ve hata düzeltmeleri .NET Framework 4.6.2 listesi için bkz: [değişiklikler listesi .NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=708778) GitHub üzerinde.  Ek bilgi için bkz: [Duyurusu .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) .NET blogunda.

<a name="ASPNET462" />

### <a name="aspnet"></a>ASP.NET

İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET, aşağıdaki geliştirmeleri içerir:

**Veri ek açıklama doğrulayıcıları yerelleştirilmiş hata iletileri için gelişmiş destek**

Veri ek açıklama doğrulayıcıları, bir sınıf özelliği için bir veya daha fazla öznitelik ekleyerek doğrulamayı gerçekleştirmek etkinleştirin. Özniteliğin <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> öğe doğrulama başarısız olursa hata iletisinin metni tanımlar. İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET hata iletilerini yerelleştirmeniz kolaylaştırır. Hata iletileri, yerelleştirilecek:

1. <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Doğrulama özniteliği sağlanır.

2. Kaynak dosyanın App_LocalResources klasöründe depolanır.

3. Yerelleştirilmiş kaynak dosyasının adını formundadır `DataAnnotation.Localization.{` *adı*`}.resx`burada *adı* bir kültür adı biçiminde *languageCode* `-` *ülke/regionCode* veya *languageCode*.

4. Anahtar adı kaynak atanan dizedir <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> özniteliği ve değerini olan yerelleştirilmiş hata iletisi.

Örneğin, aşağıdaki veri ek açıklama özniteliği için geçersiz bir derecelendirme varsayılan kültürün hata iletisini tanımlar.

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

Ardından, DataAnnotation.Localization.fr.resx, hata iletisi dizesi, anahtarıdır ve yerelleştirilmiş hata iletisi, değeri olan bir kaynak dosyası da oluşturabilirsiniz. Dosya içinde bulunması gereken `App.LocalResources` klasör. Örneğin, anahtarını ve değerini yerelleştirilmiş Fransızca (fr) dil hata iletisi şudur:

| Ad                                 | Değer                                     |
| ------------------------------------ | ----------------------------------------- |
| Derecelendirme, 1 ile 10 arasında olmalıdır. | La note doit être comprise entre 1 et 10. |

 Ayrıca, veri ek açıklama yerelleştirme genişletilebilir. Geliştiriciler eklenti kendi dize yerelleştiriciye sağlayıcısında uygulayarak <xref:System.Web.Globalization.IStringLocalizerProvider> yerelleştirme dize yere dışında bir kaynak dosyasında depolamak için arabirim.

 **Oturum durumu depolama sağlayıcıları ile zaman uyumsuz desteği**

 ASP.NET artık, böylece zaman uyumsuz ölçeklenebilirlik avantajlarını almak ASP.NET uygulamaları izin vererek, oturum durumu depolama sağlayıcıları ile kullanılacak görev döndüren yöntemler de sağlar. Desteklenenler sağlayıcıları Zamanuyumsuz işlemler yöneticisine oturum durumunu depolamak, ASP.NET içeren yeni bir arabirim <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, işlevinden devralan <xref:System.Web.IHttpModule> ve kendilerine ait oturum durumu modülü ve zaman uyumsuz oturum depolama sağlayıcıları uygulamak geliştiricilerin olanak tanır. Arabirim şu şekilde tanımlanır:

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

 Ayrıca, <xref:System.Web.SessionState.SessionStateUtility> sınıfı içeren iki yeni yöntem <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> ve <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, zaman uyumsuz işlemleri desteklemek için kullanılabilir.

 **Çıktı önbellek sağlayıcıları için zaman uyumsuz desteği**

 İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], görev döndüren-yöntemleri zaman uyumsuz ölçeklenebilirlik avantajlarını sağlayacak çıkış önbelleği sağlayıcıları ile kullanılabilir.  Bu yöntemleri uygulayan sağlayıcıları, bir web sunucusunda iş parçacığı engellemelerini azaltmak ve ASP.NET hizmeti olan ölçeklenebilirliği geliştirme.

 Aşağıdaki API'lar, zaman uyumsuz çıktı önbellek sağlayıcıları desteklemek için eklenmiştir:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> Öğesinden devralan sınıf <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> ve zaman uyumsuz bir çıkış önbelleği sağlayıcısı için uygulanacak olan geliştiriciler sağlar.

- <xref:System.Web.Caching.OutputCacheUtility> Çıkış önbelleğini yapılandırma için yardımcı yöntemleri sağlar sınıfını.

- 18 yeni yöntemleri <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> sınıfı. Bunlar <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, ve <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- 2 yeni yöntemleri <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> sınıfı: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> ve <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 yeni yöntemleri <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> sınıfı: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> ve <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 yeni yöntemleri <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> sınıfı: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> ve <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- İçinde <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> sınıfı <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> yöntemi.

- İçinde <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> yöntemi.

<a name="Strings" />

### <a name="character-categories"></a>Karakter kategorileri

Öğesindeki karakterler [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] göre sınıflandırılır [Unicode standardı, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/). İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], karakter sınıflandırılmış 6.3 Unicode karakter kategorilerine göre.

Unicode 8.0 için destek, karakter sınıflandırması sınırlı <xref:System.Globalization.CharUnicodeInfo> sınıf ve türleri ve yöntemleri için güvenin üzerinde. Bunlar <xref:System.Globalization.StringInfo> sınıfı, aşırı yüklenmiş <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> yöntemi ve [karakter sınıfları](../../standard/base-types/character-classes-in-regular-expressions.md) .NET Framework normal ifade motoru tarafından tanınır.  Karakter ve dize karşılaştırma ve sıralama bu değişiklikten etkilenmez ve temel alınan işletim sisteminde veya Windows 7 sistemlerinde, .NET Framework tarafından sağlanan karakter verileri yararlanmaya devam eder.

Unicode 6.0 karakter kategorilerden Unicode 7.0 değişiklikler için bkz: [Unicode standardı, sürüm 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) Unicode Consortium sitesinde. Değişiklikler için Unicode 7.0 Unicode 8.0 için bkz: [Unicode standardı, sürüm 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) Unicode Consortium sitesinde.

<a name="Crypto462" />

### <a name="cryptography"></a>Şifreleme

**X509 desteği içeren FIPS 186 3 DSA sertifikaları**

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] DSA (dijital imza algoritması) X509 anahtarları FIPS 186 2 1024 bit sınırı aşan sertifikalar için destek ekler.

FIPS 186-3, daha büyük anahtar boyutunu destekleme yanı sıra [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] imzaları SHA-2 karma algoritma ailesi, (SHA256, SHA384 ve SHA512) ile bilgi işlem sağlar. FIPS 186 3 desteği sağlanır yeni <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> sınıfı.

Yakın zamanda yapılan değişiklikler mantığıyla <xref:System.Security.Cryptography.RSA> sınıfı .NET Framework 4.6 ve <xref:System.Security.Cryptography.ECDsa> .NET Framework 4.6.1, sınıfta <xref:System.Security.Cryptography.DSA> soyut temel sınıf [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] bu işlevselliği kullanmak arayanlara izin vermek için ek yöntemler atama olmadan. Çağırabilirsiniz <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi verileri imzalamak için genişletme yöntemi.

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

Ve çağırabilirsiniz <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi imzalı verileri doğrulamak için genişletme yöntemi.

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

**Artan açıklık için girişleri ECDiffieHellman anahtar türetme rutinleri**

.NET framework 3.5 ile üç farklı anahtar türetme işlevi (KDF) yordamlarını Eliptik Eğri Diffie-Hellman anahtar anlaşması için destek eklendi. Özellikleri aracılığıyla girişleri yordamları ve yordamları kendileri için yapılandırılmış <xref:System.Security.Cryptography.ECDiffieHellmanCng> nesne. Ancak her yordam, her giriş özelliği okuma olduğundan, Karışıklığı önlemek için geçmişteki üzerinde geliştiricinin bol miktarda odası vardı.

Bu adres için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], aşağıdaki üç yöntemi eklenmiş <xref:System.Security.Cryptography.ECDiffieHellman> temel sınıfı daha net bir şekilde bu KDF yordamları ve bunların girişleri göstermek için:

|ECDiffieHellman yöntemi|Açıklama|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Türetilen formülünü kullanarak anahtar malzemesi<br /><br /> KARMA (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> KARMA (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> Burada *x* hesaplanan EC Diffie-Hellman algoritma sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Türetilen formülünü kullanarak anahtar malzemesi<br /><br /> HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> HMAC (hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> Burada *x* hesaplanan EC Diffie-Hellman algoritma sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|TLS sözde rastgele işlevi (PRF) türetme algoritması kullanarak anahtar malzemesi türetilir.|

**Kalıcı anahtar simetrik şifreleme desteği**

Windows şifreleme kitaplığı (CNG) kalıcı simetrik anahtarları depolamak için destek eklendi ve donanım depolanan simetrik anahtarlar kullanarak ve [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] yapmak, geliştiriciler için olası yapılan bu özelliği kullanın.  Anahtar adları ve anahtar sağlayıcıları kavramı uygulamaya özel olduğundan, bu özelliği kullanmaktan yerine tercih edilen Fabrika yaklaşım somut uygulama türlerinin Oluşturucu kullanan gerektirir (arama gibi `Aes.Create`).

Kalıcı anahtar simetrik şifreleme desteği için AES var (<xref:System.Security.Cryptography.AesCng>) ve 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algoritmaları. Örneğin:

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

**SHA-2 karma SignedXml desteği**

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] İçin destek ekler <xref:System.Security.Cryptography.Xml.SignedXml> Özet algoritmaları RSA SHA512 PKCS #1 RSA-SHA256 ve SHA384 RSA İmza yöntemleri ve SHA256, SHA384 ve SHA512 başvuru sınıfı.

URI sabitleri tüm üzerinde sunulan <xref:System.Security.Cryptography.Xml.SignedXml>:

|SignedXml alan|Sabit|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Özel bir kayıtlı tüm programları <xref:System.Security.Cryptography.SignatureDescription> işleyicisine <xref:System.Security.Cryptography.CryptoConfig> Bu algoritmalar geçmişte menülerin ancak olduğundan platformu artık varsayılan olarak, aynı kalacak için destek eklemek üzere <xref:System.Security.Cryptography.CryptoConfig> artık kayıt değil gerekli.

<a name="SQLClient" />

### <a name="sqlclient"></a>SqlClient

SQL Server için .NET framework veri sağlayıcısı (<xref:System.Data.SqlClient?displayProperty=nameWithType>) aşağıdaki yeni özellikleri içeren [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:

**Bağlantı havuzu ve Azure SQL veritabanları ile zaman aşımları**

Ne zaman bağlantı havuzu etkin ve bir zaman aşımı veya diğer oturum açma hatası oluşur bir özel durum önbelleğe alınır ve önbelleğe alınan sonraki bağlantı girişimleri sonraki beş saniye ila 1 dakika için üzerinde özel durum.  Daha fazla ayrıntı için [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).

Bu davranış, hızlı bir şekilde kurtarılmasını genellikle geçici hatalar ile bağlantı girişimleri başarısız olabilir beri Azure SQL veritabanlarına bağlanırken arzu değil. Daha iyi davranışı kaldırılır, Azure SQL veritabanlarına bağlantı başarısız olursa bağlantı havuzu engelleme süresi bağlantı yeniden deneme deneyimini iyileştirin.

Yeni eklenen `PoolBlockingPeriod` anahtar sözcüğü, uygulamanız için en uygun engelleme süresi seçmenize olanak sağlar. Değerler şunlardır:

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

Bir Azure SQL veritabanı'na bağlanan bir uygulama boyunca engelleme bağlantı havuzu devre dışı bırakıldı ve diğer herhangi bir SQL Server örneğine bağlanan bir uygulama boyunca engelleme bağlantı havuzu etkindir. Varsayılan değer budur. Sunucu uç noktası adı aşağıdakilerden birini ile bitiyorsa, Azure SQL veritabanları kabul edilir:

- .database.windows.net

- .database.chinacloudapi.cn

- .database.usgovcloudapi.net

- .database.cloudapi.de

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

Bağlantı havuzu engelleme süresi her zaman etkindir.

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

Bağlantı havuzu engelleme süresi her zaman devre dışı bırakıldı.

**İyileştirmeleri her zaman şifreli için**

SQLClient her zaman şifreli için iki geliştirmeleri sunar:

- Şifrelenmiş veritabanı sütunlarını Parametreli sorgu performansını artırmak için sorgu parametreleri için şifreleme meta verileri artık önbelleğe alınır. İle <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> özelliğini `true` (varsayılan değer olan), aynı sorgu birden çok kez çağrılırsa, istemci parametresi meta verileri sunucudan yalnızca bir kez alır.

- Sütun şifreleme anahtarı girişleri anahtar önbelleğinde artık yapılandırılabilir bir zaman aralığı kullanılarak ayarlanan sonra çıkarılacak <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> özelliği.

<a name="WCF" />

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation aşağıdaki alanlarda geliştirilmiştir:

**CNG kullanarak depolanan sertifikaları için WCF aktarma güvenlik desteği**

WCF aktarım güvenliği kullanarak Windows şifrelemesi kitaplığı (CNG) depolanan sertifikalarını destekler. İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bir üs en fazla 32 bit uzunluğunda bir ortak anahtar sertifikaları kullanarak bu destek sınırlıdır. Bir uygulama hedefleri olduğunda [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bu özellik varsayılan olarak açıktır.

Hedefleyen uygulamalar için [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki ancak üzerinde çalışan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bu özellik, aşağıdaki satırı ekleyerek etkinleştirilebilir [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) app.config veya web.config Bölümü dosya.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Bu ayrıca programlı bir şekilde aşağıdaki gibi kod ile yapılabilir:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

**DataContractJsonSerializer sınıfı tarafından birden çok gün ışığından yararlanma ayarlama kuralları için daha iyi destek**

Müşterilerin bir uygulama yapılandırma ayarı belirlemek için kullanabileceğiniz olmadığını <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfı, birden çok ayarlama kuralları için tek bir saat dilimi destekler. Bu bir katılım özelliğidir. Bunu etkinleştirmek için app.config dosyanıza aşağıdaki ayarı ekleyin:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Bu özellik etkinleştirildiğinde bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesne kullandığı <xref:System.TimeZoneInfo> türü yerine <xref:System.TimeZone> tarih ve saat verileri seri durumdan çıkarılacak türü. <xref:System.TimeZoneInfo> birden çok ayarlama kuralları ile geçmiş saat dilimi çalışmanızı mümkün destekler;   <xref:System.TimeZone> desteklemez.

Daha fazla bilgi için <xref:System.TimeZoneInfo> yapısı ve saat dilimi ayarlarını görmek [saat dilimine genel bakış](../../standard/datetime/time-zone-overview.md).

**NetNamedPipeBinding en iyi eşleşme**

WCF istemci uygulamalara istediklerinde bir en iyi şekilde eşleşen bir URI üzerinde dinleme hizmeti her zaman bağlantı sağlamak için ayarlanabilir yeni bir uygulama ayarı vardır. Ayarlamak bu uygulama ayarı ile `false` (varsayılan) kullanan istemciler için olası <xref:System.ServiceModel.NetNamedPipeBinding> istenilen URI'nin bir alt dizesi olan bir URI üzerinde dinleme bir hizmete bağlanmak için.

Örneğin, bir istemcinin bir servis konumunda dinleme bağlanmaya çalıştığı `net.pipe://localhost/Service1`, ancak farklı bir hizmet yönetici ayrıcalığıyla çalıştıran makinenin konumunda dinliyor `net.pipe://localhost`. Ayarlamak bu uygulama ayarı ile `false`, istemci yanlış hizmete bağlanma girişimi. Uygulama ayarı sonra `true`, istemci her zaman en iyi eşleşen hizmet için bağlanır.

> [!NOTE]
> Kullanan istemciler <xref:System.ServiceModel.NetNamedPipeBinding> (varsa) yerine tam uç nokta adresini hizmetin taban adresine göre hizmetleri bulun. Bu her zaman çalışır hizmet ayarı emin olmak için benzersiz bir taban adresi kullanmanız gerekir.

Bu değişiklik etkinleştirmek için aşağıdaki uygulama ayarı, istemci uygulamanızın App.config veya Web.config dosyasına ekleyin:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

**SSL 3.0 varsayılan protokol değil.**

SSL 3.0, artık NetTcp aktarım güvenliği ve sertifika kimlik bilgisi türü ile kullanırken, güvenli bağlantı anlaşması için kullanılan bir varsayılan protokol değil. Çoğu durumda olması gerekir mevcut uygulamalara herhangi bir etkisi NetTcp için TLS 1.0 protokolü listesinde yer aldığından. Var olan tüm istemciler bir bağlantı kullanarak en az TLS 1.0. Ssl3 gerekiyorsa, aşağıdaki yapılandırma mekanizmalardan biri üzerinde anlaşılan protokolleri listesine eklemek için kullanın.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Özelliği

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Özelliği

- [ \<Aktarım >](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) bölümünü [ \<netTcpBinding >](../configure-apps/file-schema/wcf/nettcpbinding.md) bölümü

- [ \<SslStreamSecurity >](../configure-apps/file-schema/wcf/sslstreamsecurity.md) bölümünü [ \<customBinding >](../configure-apps/file-schema/wcf/custombinding.md) bölümü

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation aşağıdaki alanlarda geliştirilmiştir:

**Grup sıralama**

Kullanan bir uygulamayı bir <xref:System.Windows.Data.CollectionView> verileri gruplandırmak için nesne artık açıkça bildirebilirsiniz nasıl sıralanacağını gruplar. Açık adresleri sıralama anlaşılamayacak sıralama sorununu ekler veya grupları kaldırır dinamik olarak bir uygulama ya da gruplandırma öğesi özellik değeri değiştiğinde gerçekleşir. Bu ayrıca Grup oluşturma işleminin karşılaştırmalar gruplandırma özelliklerinin tam koleksiyonu sıralamasını gruplarının sıralamanın taşıyarak performansını geliştirebilirsiniz.

Grup sıralama, desteklemek için yeni <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> ve <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> özellikleri açıklar tarafından üretilen Grup koleksiyonu sıralamak nasıl <xref:System.ComponentModel.GroupDescription> nesne. Bu şekilde aynı adlı benzer <xref:System.Windows.Data.ListCollectionView> özellikleri, veri öğeleri nasıl açıklar.

İki yeni statik özelliklerini <xref:System.Windows.Data.PropertyGroupDescription> sınıfı <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> ve <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, en yaygın örnekleri için kullanılabilir.

Örneğin, yaş, aşağıdaki XAML grupları verileri yaş gruplarını, artan düzende sıralamak ve soyadına göre her yaş grubu içindeki öğeler grubunda.

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

**Geçici klavye desteği**

Geçici klavye desteği tarafından otomatik olarak çağrılmasını ve Windows 10'daki yeni geçici klavye kapatılıyor, dokunma girişini metin girişi alabilir bir denetim tarafından alındığında bir WPF uygulamalarında izleme odağı sağlar.

Önceki .NET Framework sürümlerinde, WPF uygulamaları, WPF kalem/dokunma hareketi desteği devre dışı bırakmadan izleme odağa kapatılamaz.  Sonuç olarak, WPF uygulamaları tam WPF dokunma desteği seçin veya bu Windows üzerinde fare yükseltme kullanan gerekir.

**İzleyici başına DPI**

WPF içinde WPF uygulamaları için yüksek DPI ve karma DPI ortamları son çoğalan desteklemek için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] İzleyici başına farkındalık sağlar. Bkz: [örnekleri ve Geliştirici Kılavuzu](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) İzleyici başına DPI olacak WPF uygulamanızı etkinleştirme hakkında daha fazla bilgi için GitHub üzerindeki.

Önceki .NET Framework sürümlerinde, WPF sistem DPI kullanan uygulamalardır. Diğer bir deyişle, uygulamanın kullanıcı Arabiriminde uygulama işlenen izleyicinin DPI bağlı olarak uygun şekilde işletim sistemine göre ölçeklendirilir. ,

Altında çalışan uygulamalar için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bir yapılandırma deyimine ekleyerek WPF uygulamalarında İzleyici başına DPI değişiklikleri devre dışı bırakabilirsiniz [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) gibi Uygulama Yapılandırması bölümünde dosya:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Workflow Foundation aşağıdaki alanında geliştirilmiştir:

**C# ifadeleri ve Re-hosted WF Tasarımcısı'nda IntelliSense desteği**

İle başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF, hem bir Visual Studio Tasarımcısı'nda ve kod iş akışlarında C# ifadeleri destekler. Re-hosted iş akışı Tasarımcısı, WF iş akışı Tasarımcısı, Visual Studio'da (örneğin, WPF) dışında bir uygulamada olmasını sağlayan anahtar özelliğidir.  Windows Workflow Foundation, C# ifadeleri ve IntelliSense Re-hosted iş akışı Tasarımcısı'nda destekleme özelliği sağlar. Daha fazla bilgi için [Windows Workflow Foundation blog](https://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` Önceki .NET Framework sürümlerinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], WF Tasarımcısı IntelliSense olduğunda kopuk bir müşteri Visual Studio'dan bir iş akışı projesi oluşturur. Eksik iş akışı türlerini ıntellisense'ten uyarılarını görünür proje derlemesi başarılı olur ve iş akışı türlerini tasarımcıda bulunamadı ancak **hata listesi** penceresi. [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Bu sorunu giderir ve IntelliSense kullanılabilir hale getirir.

**Artık izleme iş akışını iş akışı V1 uygulamaları FIPS modunda çalıştırın.**

FIPS uyumluluk modu etkin makinelerle artık başarıyla bir iş akışı sürüm 1-stil uygulama iş akışı izleme çalıştırabilirsiniz. Bu senaryoyu etkinleştirmek için app.config dosyanıza aşağıdaki değişikliği yapmanız gerekir:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

Bu senaryo etkin değilse, uygulamayı çalıştıran bir özel durum iletisi oluşturmaya devam eder "Bu uygulama, Windows parçası değil platforma FIPS doğrulanmış şifreleme algoritmaları."

**Dinamik güncelleştirme ile Visual Studio iş akışı Tasarımcısı kullanarak iş akışı iyileştirmeleri**

İş Akışı Tasarımcısı, akış çizelgesi etkinlik Tasarımcısı ve diğer iş akışı etkinlik tasarımcıları artık başarıyla yüklemek ve çağırdıktan sonra kaydedilmiş iş akışları görüntüleme <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi. Önce .NET Framework sürümlerinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], çağırdıktan sonra kaydedilmiş bir iş akışı için Visual Studio'da bir XAML dosyası yüklenirken <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> aşağıdaki sorunları neden olabilir:

- İş Akışı Tasarımcısı XAML dosyası doğru şekilde yüklenemiyor (zaman <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> satırın sonunda olup).

- Flowchart etkinlik Tasarımcısı veya diğer iş akışı etkinlik tasarımcıları tüm nesneleri, varsayılan konumlarda aksine ekli özellik değerlerini görüntüleyebilir.

<a name="clickonce-1" />

### <a name="clickonce"></a>ClickOnce

ClickOnce, TLS 1.1 ve TLS 1.2 zaten destekleyen 1.0 protokol HTTP'ye ek olarak desteklemek için güncelleştirildi. ClickOnce, hangi protokolün gereklidir otomatik olarak algılar. ClickOnce Uygulama içinde hiçbir ek adımlar, TLS 1.1 ve 1.2 desteği etkinleştirmek için gereklidir.

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Windows Forms ve WPF uygulamaları UWP uygulamalarına dönüştürme

Windows, artık WPF ve Windows Forms uygulamaları Evrensel Windows Platformu (UWP) için de dahil olmak üzere var olan Windows Masaüstü uygulamaları getirmek için özellikleri sunar. Bu teknoloji, mevcut kod tabanınız UWP, böylece uygulamanız tüm Windows 10 cihazlarına getirme kademeli olarak geçiş olanak tanıyarak bir köprü görevi görür.

Dönüştürülen Masaüstü uygulamaları, UWP API'lerine Canlı kutucukları ve bildirimleri gibi özellikleri etkinleştirmek için erişilebilir hale getirir UWP uygulamaları, uygulama kimliğini benzer bir uygulama kimliği elde edin. Uygulama, önceki gibi davranmaya devam eder ve tam güven uygulaması olarak çalıştırılır. Uygulama dönüştürüldükten sonra bir uygulama kapsayıcı işlemi uyarlanabilir bir kullanıcı arabirimi eklemek için var olan tam güven işlem eklenebilir. Tüm işlevselliği uygulama kapsayıcı işleme taşındığında, tam güven işlem kaldırılabilir ve yeni bir UWP uygulaması tüm Windows 10 cihazlar için kullanılabilir hale getirilebilir.

<a name="Debug462" />

### <a name="debugging-improvements"></a>Hata ayıklama iyileştirmeleri

*Hata ayıklama API'si yönetilmeyen* içinde Gelişmiş [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ek analizler yapmak için bir <xref:System.NullReferenceException> hangi değişkendir kaynak kodu tek bir satırda belirlemek mümkün olması oluşturulur `null`.   Bu senaryoyu desteklemek için aşağıdaki API'leri için yönetilmeyen hata ayıklama API'si eklenmiştir.

- [Icordebugcode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [Icordebugvariablehome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), ve [Icordebugvariablehomeenum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) yönetilen değişkenlerin yerel havaalanlarından gösterdiğiniz arabirimleri. Bu, bazı kod akış analizi yapmak hata ayıklayıcıları sağlar, bir <xref:System.NullReferenceException> gerçekleşir ve, yerel konumuna karşılık gelen yönetilen değişkeni belirlemek için geriye doğru çalışması için `null`.

- [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi Icordebugtype için bir eşleme sağlayan [cor_typeıd](../unmanaged-api/debugging/cor-typeid-structure.md), elde etmek hata ayıklayıcı sağlayan bir [cor_typeıd](../unmanaged-api/debugging/cor-typeid-structure.md) bir örneği olmadan Icordebugtype. Var olan API'leri [cor_typeıd](../unmanaged-api/debugging/cor-typeid-structure.md) türü sınıf düzenini belirlemek için kullanılabilir.

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a>.NET Framework 4.6.1 yenilikler

[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Aşağıdaki alanlarda yeni özellikler içerir:

- [Şifreleme](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profil Oluşturma](#Profile461)

- [NGen](#NGEN461)

Daha fazla bilgi için [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], aşağıdaki konulara bakın:

- [.NET framework 4.6.1 değişikliklerin listesi](https://go.microsoft.com/fwlink/?LinkId=622964)

- [4.6.1 uygulama uyumluluğu](../migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [.NET framework API diff](https://go.microsoft.com/fwlink/?LinkId=622989) (github'da)

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Şifreleme: X509 desteği içeren ECDSA sertifikaları

.NET framework 4.6 X509 RSACng desteği eklendi sertifikaları. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ECDSA (Eliptik Eğri Dijital imza algoritması) X509 için destek ekler sertifikaları.

ECDSA daha iyi performans sunar ve RSA, Aktarım Katmanı Güvenliği (TLS) performans ve ölçeklenebilirlik olduğu önemli bir mükemmel seçim sağlayarak daha daha güvenli bir şifreleme algoritması. .NET Framework uygulaması mevcut Windows işlevselliğine çağrılarını sarmalar.

Aşağıdaki kod örneği, X 509 sertifikalarını dahil ECDSA için yeni destek kullanarak imza bayt akışı olarak oluşturmak için ne kadar kolay olduğunu gösteren [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

Bu, .NET Framework 4. 6 ' bir imza oluşturmak için gereken kod için işaretli bir Karşıtlık sunuyor.

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a>ADO.NET

Aşağıdakiler için ADO.NET eklenmiştir:

**Her zaman şifreli desteği donanım korumalı anahtarlar**

ADO.NET artık depolama Always Encrypted sütun ana anahtarları yerel olarak donanım güvenlik modülleri (HSM'ler) destekler. Bu destek sayesinde, özel sütun ana anahtar depolama sağlayıcıları yazmak zorunda ve onlara uygulamaları kaydetme olmadan Hsm'lerde saklanan asimetrik anahtarlar müşteriler yararlanabilir.

Müşteriler HSM satıcısı tarafından sağlanan CSP sağlayıcısı veya CNG Anahtar depolama sağlayıcıları sütun ana bir HSM'de depolanan anahtarlar korunan verileri her zaman şifreli erişmek için uygulama sunucuları veya istemci bilgisayarlara yüklemeniz gerekir.

**Geliştirilmiş <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> AlwaysOn bağlantı davranışları**

SqlClient artık otomatik olarak daha hızlı bağlantıları bir AlwaysOn Kullanılabilirlik Grubu (ağ) sağlar. Şeffaf bir şekilde uygulamanızı farklı bir alt ağdaki bir AlwaysOn Kullanılabilirlik Grubu (ağ) bağlanma ve hızlı bir şekilde geçerli etkin sunucunun bulur ve sunucunun bir bağlantı sağlar olup olmadığını algılar. Bu sürümden önce bir uygulama eklemek için bağlantı dizesini ayarlayalım gerekiyordu `"MultisubnetFailover=true"` bir AlwaysOn Kullanılabilirlik grubuna bağlanan belirtmek için. Bağlantı anahtar sözcüğü ayarını olmadan `true`, bir uygulama için bir AlwaysOn Kullanılabilirlik grubuna bağlanırken zaman aşımı karşılaşabilirsiniz. Bu sürümle birlikte, bir uygulama mu *değil* yapmanız <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> için `true` artık. Always On kullanılabilirlik grupları için SqlClient desteği hakkında daha fazla bilgi için bkz: [yüksek kullanılabilirlik, olağanüstü durum kurtarma için SqlClient desteği](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

Windows Presentation Foundation yenilikleri ve değişiklikleri içerir.

**Geliştirilmiş performans**

Dokunma olayları tetikleme gecikme de çözülmüştür [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Ayrıca, yazarak bir <xref:System.Windows.Controls.RichTextBox> denetimi artık Hızlı Giriş sırasında işleme iş parçacığını bağlar.

**Yazım denetimi iyileştirmeleri**

Windows 8.1 üzerinde yazım denetleyicisi ' WPF'de güncelleştirildi ve yazım denetimi ek diller için işletim sisteminden yararlanmak için sonraki sürümleri destekler.  Windows 8.1 ve önceki Windows sürümlerinde işlevsellikte değişiklik yoktur.

Dil için .NET Framework'ün önceki sürümlerinde olduğu gibi bir <xref:System.Windows.Controls.TextBox> denetim ora <xref:System.Windows.Controls.RichTextBox> blok bilgi aşağıdaki sırayla bakarak algılandı:

- `xml:lang`, varsa.

- Geçerli giriş dili.

- Geçerli iş parçacığı kültürü.

WPF dil desteği hakkında ek bilgi için bkz: [.NET Framework 4.6.1 özellikleri WPF Web günlüğü gönderisini](https://go.microsoft.com/fwlink/?LinkID=691819).

**Ek kullanıcı başına özel sözlük desteği**

İçinde [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF, küresel olarak kayıtlı özel sözlükleri tanır. Bu özellik, Denetim başına kaydedilecek özelliğine ek olarak kullanılabilir.

WPF önceki sürümleri, özel sözlükleri sözcükleri hariç tutulan ve Otomatik Düzeltme listeleri tanıyamadı. Bunlar Windows 8.1 ve Windows 10'da altında yerleştirilebileceği dosya kullanımı desteklenir `%AppData%\Microsoft\Spelling\<language tag>` dizin.  Bu dosyalar için aşağıdaki kurallar geçerlidir:

- Dosya uzantıları .dic (için eklenen sözcükleri), .exc (için hariç tutulan sözcükler) veya .acl (için otomatik düzeltme) olmalıdır.

- Dosyaları bayt sırası işareti (BOM) ile başlayan bir UTF-16 LE düz metin olması gerekir.

- Satır sonundaki bir sözcük (Word'ün eklendi ve dışlanan listelerinde) oluşmalıdır veya bir düzeltme çifti sözcüklerini içeren bir çubukla ayrılan ("&#124;") (listedeki düzeltme sözcük).

- Bu dosyalar salt okunur olarak kabul edilir ve sistem tarafından değiştirilmez.

> [!NOTE]
> Bu yeni dosya biçimleri WPF yazım denetimi API'leri tarafından doğrudan desteklenmeyen ve WPF uygulamalarında sağlanan özel sözlükleri .lex dosyaları kullanmaya devam etmeniz gerekir.

**Örnekler**

WPF örnek sayısı vardır [WPF/Microsoft-Samples](https://github.com/Microsoft/WPF-Samples) GitHub deposu. Bize bir çekme isteği veya açılış göndererek örneklerimizi geliştirmemize yardımcı olun bir [GitHub sorunu](https://github.com/Microsoft/WPF-Samples/issues).

**DirectX uzantıları**

WPF içeren bir [NuGet paketini](https://go.microsoft.com/fwlink/?LinkID=691342) yeni uygulamaları sağlayan <xref:System.Windows.Interop.D3DImage> kolaylaştıran, Dx11 DX10 ile çalışmak içerik. Kod için bu paket açıldıktan kaynaklanan ve kullanılabilir [github'da](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: İşlemler

<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> Yöntemi artık MSDTC dışındaki bir Dağıtılmış İşlem Yöneticisi işlem yükseltmek için kullanabilir. Yeni bir GUID işlem promoter tanımlayıcısını belirterek bunu <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yükleme. Bu işlem başarılı olursa, işlem yeteneklerine yerleştirilmiş sınırlamaları vardır. MSDTC dışı işlem promoter kayıtlı sonra aşağıdaki yöntemlerden throw bir <xref:System.Transactions.TransactionPromotionException> çünkü bu yöntemler MSDTC yükseltmesine gerektirir:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

MSDTC dışı işlem promoter kayıtlı sonra gelecek kalıcı kayıtlar için tanımladığı protokolleri kullanarak kullanılmalıdır. <xref:System.Guid> Hareket promoter kullanılarak elde edilebilir <xref:System.Transactions.Transaction.PromoterType%2A> özelliği. Ne zaman işlem yükseltir, işlem promoter sağlayan bir <xref:System.Byte> yükseltilen belirteci temsil eden bir dizi. Bir uygulama olan yükseltilen MSDTC dışı işlem için yükseltilmiş belirteci edinebilirsiniz <xref:System.Transactions.Transaction.GetPromotedToken%2A> yöntemi.

Yeni kullanıcılar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yükleme, yükseltme işleminin başarıyla tamamlanması için sırayla bir belirli çağrı sırası izlemelidir. Bu kurallar yöntemin belgelerinde belgelenmiştir.

<a name="Profile461" />

### <a name="profiling"></a>Profil Oluşturma

Yönetilmeyen profil oluşturma API'si şu şekilde geliştirilmiştir:

- Pdb içinde erişmek için daha iyi destek [Icorprofilerınfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimi.

   ASP.NET Core, derlenmiş bellek içi Roslyn tarafından derlemeler çok daha yaygın gelmektedir. Profil oluşturma araçları yapma, geliştiriciler için daha önce disk üzerinde seri hale pdb artık mevcut olabileceğini gösterir. Profiler Araçlar genellikle pdb kod geri kod kapsamı veya satır satır Performans Analizi gibi görevler için kaynak satırları eşlemek için kullanın. [Icorprofilerınfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimi artık iki yeni yöntem içerir [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) ve [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) , yeni API'leri kullanarak bu profil oluşturucu Araçlar, bellek içi PDB verilere erişimi sağlamak için bir profil oluşturucu bir bayt dizisi olarak bir bellek içi PDB içeriğini edinebilir ve sonra işleyin veya diske seri hale getirme.

- ICorProfiler arabirimi ile daha iyi izleme.

   Kullanmakta olduğunuz profil oluşturucular `ICorProfiler` API'leri ReJit işlevlerini dinamik araçları artık bazı meta verileri değiştirin. Daha önce bu tür Araçlar IL herhangi bir zamanda izleme, ancak meta verileri yalnızca Modül yükleme zamanında değiştirilmiş. IL meta verileri başvurduğundan bu yapılabilir izleme türlerini sınırlı. Biz bu sınırları bazıları ekleyerek yükseltilmiş [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) modülü, özellikle yeni ekleyerek yüklendikten sonra bir alt kümesi meta verileri düzenlemeleri desteklemek için gereken yöntemini `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, ve `UserString` kaydeder. Bu değişiklik, daha geniş bir şirket halindeyken izleme mümkün kılar.

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a>Yerel Görüntü Oluşturucu (NGEN) pdb

Çapraz makine olay izleme profil bir makinede bir programı yapmasını sağlar ve B. makine kullanarak önceki sürümlerinde kullanıcı .NET Framework'ün kaynak satırı eşleme ile profil oluşturma verilerinin göz tüm yerel görüntüleri ve modülleri profili oluşturulmuş kopyalayın Makine analiz makineye kaynak yerel eşleme oluşturmak için IL PDB içerir. Bu işlem, dosyaları telefon uygulamaları için görece küçük gibi olduğunda iyi çalışabilir ancak dosyalar Masaüstü sistemlerinde çok büyük olabilir ve kopyalamak için önemli zaman gerektirir.

Ngen Pdb'lerin ile NGen IL PDB bağımlılığı olmadan IL yerel eşleme içeren bir PDB oluşturabilirsiniz. Çapraz makine olay izleme senaryomuzdaki ise gereken tek şey yerel görüntü makine B makine A tarafından oluşturulan PDB kopyalamak ve kullanmak için [hata ayıklama arabirimi erişim API'leri](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) IL PDB'ın kaynak IL eşleme ve yerel okuma PDB'ın IL yerel eşleme resmi. Her iki eşlemeleri birleştirme kaynağı yerel eşleme sağlar. PDB yerel görüntü tüm modüller ve yerel görüntüler çok daha küçük olduğundan, makine A'dan B'ye makine kopyalama işlemi daha hızlıdır.

<a name="v46" />

## <a name="whats-new-in-net-2015"></a>.NET 2015'teki yenilikler

.NET 2015 tanıtır [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve .NET Core. Bazı yeni özellikler hem de uygulama ve diğer özelliklere özgü [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] veya .NET Core.

- **ASP.NET Core**

     .NET 2015, ASP.NET Core, modern bulut tabanlı uygulamaları derlemeye yönelik yalın bir .NET uygulaması içerir. ASP.NET Core modüler olduğundan, uygulamanızda yalnızca gerekli olan özellikleri içerebilir. IIS'de barındırılan veya özel bir işlemde kendi kendine barındırılan ve uygulamaları .NET Framework'ün farklı sürümleri ile aynı sunucu üzerinde çalıştırabilirsiniz. Bu, bulut dağıtımı için tasarlanan yeni bir ortam yapılandırma sistemi içerir.

     MVC, Web API ve Web sayfaları, MVC 6 olarak adlandırılan tek bir üründe yararlanma birleşik. ASP.NET Core araçları Visual Studio 2015 veya sonraki sürümlerde aracılığıyla uygulamaları oluşturun. Mevcut uygulamalarınızı yeni .NET Framework üzerinde çalışır; bir uygulama oluşturmak için MVC 6 veya SignalR 3 kullanan ancak Visual Studio 2015 veya daha sonra proje sistemi kullanmanız gerekir.

     Bilgi için [ASP.NET Core](/aspnet/core/).

- **ASP.NET güncelleştirmeleri**

    - **Görev tabanlı bir API için zaman uyumsuz yanıt düzenleniyor**

         ASP.NET artık zaman uyumsuz yanıt boşaltma için basit bir görev tabanlı API sağlar <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, dilinizin kullanarak zaman uyumsuz olarak kopyalanması yanıtlar sağlayan `async/await` destekler.

    - **Model bağlama, görev döndürme yöntemlerini destekler**

         İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ASP.NET Web formları sayfaları ve kullanıcı denetimleri CRUD tabanlı veri işlemlerinde genişletilebilir, kod odaklı bir yaklaşım etkin Model bağlama özelliği eklendi. Model bağlama sistemi artık destekliyor <xref:System.Threading.Tasks.Task>-model bağlama yöntemleri döndürüyor. Bu özellik, Web Forms geliştiricilerin ORMs, Entity Framework dahil olmak üzere daha yeni sürümlerini kullanırken, veri bağlama sistem kolaylıkla zaman uyumsuz ölçeklenebilirlik avantajlarından yararlanın sağlar.

         Zaman uyumsuz model bağlama tarafından denetlenir `aspnet:EnableAsyncModelBinding` yapılandırma ayarı.

        ```xml
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         Uygulamalarda hedef [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], varsayılan `true`. Üzerinde çalışan uygulamaları [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] .NET Framework'ün önceki bir sürümünü hedefleyen, `false` varsayılan olarak. Yapılandırma ayarı ayarlayarak etkinleştirilebilir `true`.

    - **HTTP/2 desteği (Windows 10)**

         [HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) sağlayan çok daha iyi bağlantı kullanımı (daha az arasındaki gidiş dönüş istemci ve sunucu), HTTP protokolü yeni bir sürümü, daha düşük gecikme süresi web sayfası için kullanıcılar yüklenirken výsledek.  Tek bir deneyiminin bir parçası istenen birden çok yapıtı için protokol iyileştirme yaptığından web sayfaları (aksine, Hizmetler) HTTP/2, en iyi yararlanabilir. ASP .NET Framework 4.6 HTTP/2 desteği eklendi. Birden çok katmanına ağ işlevlerini olduğundan, Windows, IIS ve ASP.NET HTTP/2 etkinleştirmek için yeni özellikler daha gerekiyordu. HTTP/2 ASP.NET ile kullanmak için Windows 10 çalıştırıyor olmalısınız.

         HTTP/2 da desteklenir ve Windows 10 Evrensel Windows Platformu (UWP) kullanan uygulamalar varsayılan değer olarak <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.

         Kullanmak için bir yol sağlamak için [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) özelliği, ASP.NET uygulamalarında iki aşırı yükleme ile yeni bir yöntem <xref:System.Web.HttpResponse.PushPromise%28System.String%29> ve <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, eklenen <xref:System.Web.HttpResponse> sınıfı.

        > [!NOTE]
        > ASP.NET Core, HTTP/2 desteklese de, anında İLETME PROMISE özelliği henüz henüz eklenmemiş desteği.

         İş tarayıcı ve web sunucusu (IIS Windows üzerinde) yapın. Ağır kaldırarak tüm kullanıcılarınız için yapmanız gerekmez.

         Çoğu [bilinen tarayıcılar HTTP/2 desteği](https://www.wikipedia.org/wiki/HTTP/2), büyük olasılıkla sunucunuz destekliyorsa, kullanıcılarınızın, HTTP/2 desteğine yararlı olacaktır.

    - **Belirteç bağlama protokolü için desteği**

         Microsoft ve Google işbirliği adlı kimlik doğrulaması için yeni bir yaklaşım [belirteç bağlama Protokolü](https://github.com/TokenBinding/Internet-Drafts). Şirket içi kimlik doğrulama belirteçlerini (tarayıcı önbelleğinizi) çalınması ve parolanızı veya ayrıcalıklı başka bir bilgi gerek kalmadan Suçları erişim aksi güvenli kaynaklara (örneğin, banka hesabı) tarafından kullanılan olmasıdır. Bu sorunu çözmek için yeni Protokolü amaçlar.

         Belirteç bağlama protokolü Windows 10'da bir tarayıcı özelliği olarak uygulanacaktır. Böylece kimlik doğrulama belirteçlerinizi yasal doğrulanmıştır ASP.NET uygulamaları protokolünde katılacak. İstemci ve sunucu uygulamaları protokolü tarafından belirtilen uçtan uca koruma kurun.

    - **Rastgele dize karma algoritmaları**

         .NET framework 4.5 sunulan bir [rastgele dize karma algoritması](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Ancak, ASP.NET tarafından nedeniyle bazı ASP.NET desteklenmiyordu özellikleri bağımlı bir kararlı karma kodu. İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], rastgele dize karma algoritmaları artık desteklenmektedir. Bu özelliği etkinleştirmek için `aspnet:UseRandomizedStringHashAlgorithm` yapılandırma ayarı.

        ```xml
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO .NET artık SQL Server 2016 Community Technology Preview 2 (CTP2) bulunan Always Encrypted özelliğini destekler. Always Encrypted ile SQL Server, şifrelenmiş veriler üzerinde işlemler gerçekleştirebilir ve tüm şifreleme anahtarı en iyi uygulama içindeki müşterinin güvenilir bir ortamda hem de sunucuda yer alıyor. Her zaman şifreli Dba'lar düz metin verilerine erişimi olmaması için Müşteri verilerinin güvenliğini sağlar. Şifreleme ve şifre çözme veri olur şeffaf bir şekilde sürücü düzeyinde uygulamalarınız için yapılması gereken değişiklikleri en aza indirir. Ayrıntılar için bkz [(veritabanı altyapısı)'Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-database-engine) ve [(istemci geliştirme)'Always Encrypted](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **yönetilen kod için 64 bit JIT Derleyici**

     64 bit JIT Derleyici (başlangıçta eskiden Ryujıt) yeni bir sürümü .NET framework 4.6 özellikleri. Yeni 64 bit derleyici eski 64 bit JIT Derleyici üzerinde önemli performans geliştirmeleri sunar. Yeni 64 bit Derleyici, .NET Framework 4.6 üzerinde çalışan 64-bit işlemler için etkinleştirilir. Uygulamanızı bir 64 bit işlem olarak 64-bit derlenirse veya AnyCPU çalışır ve bir 64-bit işletim sisteminde çalışır. Yeni derleyici geçişi mümkün olduğu kadar şeffaf hale getirmek için dikkatli alınmış olsa da davranışında değişiklik yapılamaz. Doğrudan yeni JIT derleyicisi kullanılırken karşılaşılan sorunları hakkında görüşlerinizi almak isteriz. Lütfen bize başvurun [Microsoft Connect](https://connect.microsoft.com/) yeni 64 bit JIT Derleyici için ilgili bir sorunla karşılaşırsanız.

     Yeni 64 bit JIT Derleyici ayrıca SIMD etkin türleri ile birlikte, donanım SIMD hızlandırma özellikleri içerir <xref:System.Numerics> ad alanı iyi performans artışı sağlayabilir.

- **Derleme yükleyici geliştirmeleri**

     Bir ilgili NGEN resmi yüklendikten sonra derleme yükleyici artık daha verimli bir şekilde IL derlemeleri tarafından bellek kullanır. Bu değişiklik (örneğin, Visual Studio) büyük 32-bit uygulamalar için özellikle yararlıdır ve ayrıca fiziksel bellek alanından tasarruf sanal belleği azaltır.

- **Temle sınıf kitaplık değişiklikleri**

     Çok sayıda yeni API etrafında eklenmiş [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] senaryoları etkinleştirmek için. Bunlar arasında aşağıdaki değişikler ve eklemeler şunlardır:

    - **IReadOnlyCollection\<T > uygulamaları**

         Ek koleksiyonlar uygulamak <xref:System.Collections.Generic.IReadOnlyCollection%601> gibi <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601>.

    - **CultureInfo.CurrentCulture ve CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri artık okuma-yazma yerine salt okunur. Yeni bir atarsanız <xref:System.Globalization.CultureInfo> nesne bu özellikler, geçerli iş parçacığı kültürü tarafından tanımlanan `Thread.CurrentThread.CurrentCulture` özelliği ve geçerli kullanıcı Arabirimi iş parçacığı kültürü tarafından tanımlanan `Thread.CurrentThread.CurrentUICulture` özelliklerini de değiştirebilirsiniz.

    - **Çöp toplama (GC) geliştirmeleri**

         <xref:System.GC> Sınıfı artık içerir <xref:System.GC.TryStartNoGCRegion%2A> ve <xref:System.GC.EndNoGCRegion%2A> çöp toplama sırasında kritik yol yürütülmesini engellemek olanak tanıyan yöntemler.

         Yeni aşırı yöntemin <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi sayesinde denetimine hem küçük nesne yığını ve büyük nesne yığınını gözden geçirilmiştir ve sıkıştırılmış veya yalnızca gözden geçirilmiştir.

    - **SIMD etkin türleri**

         <xref:System.Numerics> Ad alanı artık birkaç kapsar SIMD etkin türleri gibi <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, ve <xref:System.Numerics.Vector4>.

         Yeni 64 bit JIT Derleyici ayrıca donanım SIMD hızlandırma özelliklerinden içerdiğinden, özellikle önemli performans geliştirmeleri SIMD etkin türleri kullanarak yeni bir 64 bit JIT Derleyici ile oluşan vardır.

    - **Şifreleme güncelleştirmeleri**

         <xref:System.Security.Cryptography?displayProperty=nameWithType> API güncelleştiriliyor desteklemek için [Windows CNG şifreleme API'leri](/windows/desktop/SecCNG/cng-reference). .NET Framework'ün önceki sürümlerini yararlandı tamamen açık bir [önceki sürümünü Windows şifreleme API'leri](/windows/desktop/SecCrypto/cryptography-portal) temeli olarak <xref:System.Security.Cryptography?displayProperty=nameWithType> uygulaması. Bu desteklediğinden CNG API desteklemek için istekleri bizde [modern şifreleme algoritmalarını](/windows/desktop/SecCNG/cng-features#suite-b-support), hangi belirli türdeki uygulamalar için önemli.

         .NET framework 4.6 Windows CNG şifreleme API'lerini destekleyen aşağıdaki yeni iyileştirmeleri içerir:

        - Bir dizi X509 için genişletme yöntemleri sertifikalarını `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` ve `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, CAPI tabanlı uygulama mümkün olduğunda yerine CNG tabanlı bir uygulama döndürür. (Bazı akıllı kartlar, vs. hala CAPI gerektirir ve geri dönüş API'leri işlemek).

        - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> RSA algoritması bir CNG uygulamasını sağlar sınıfını.

        - RSA API geliştirmeleri ve böylece ortak Eylemler atama artık gerektirmez. Örneğin, verileri kullanarak şifreleme bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nesnesi, .NET Framework'ün önceki sürümlerinde aşağıdaki gibi kod gerektirir.

             [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             Cast önlemek için .NET Framework 4. 6 ' yeni şifreleme API'leri kullanan kod şu şekilde yeniden yazılabilir.

             [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **Tarihler ve saatler için veya Unix zamanından dönüştürmek için destek**

         Aşağıdaki yeni yöntemler eklenmiştir <xref:System.DateTimeOffset> yapısı tarih ve saat değerleri için veya Unix zamanından dönüştürmeyi desteklemek için:

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - **Uyumluluk anahtarları**

         Yeni <xref:System.AppContext> sınıfı kitaplığı yazıcılarının kullanıcıları için yeni işlevler Tekdüzen çevirme mekanizmaya sağlayan yeni bir uyumluluk özelliği ekler. Bu, bir geri çevirme isteği iletişim kurmak için bileşenler arasındaki zamanı gevşek bağlanmış bir sözleşme oluşturur. Var olan işlevselliği için bir değişiklik yapıldığında bu genellikle önemli bir özelliktir. Buna karşılık, zaten var. bir örtük katılımı için yeni işlevler.

         İle <xref:System.AppContext>kitaplıkları tanımlamak ve sunmaya uyumluluk anahtarları, onlara bağımlı kod çalışırken, bu anahtarlar kitaplık davranışını etkilemek için ayarlayabilirsiniz. Varsayılan olarak, kitaplıkları, yeni işlevsellik sağlar ve bunlar yalnızca alter (diğer bir deyişle, bunlar önceki işlevselliğini sağlar) anahtarı ayarlanırsa.

         Bir anahtar değeri, bir uygulama (veya bir kitaplık) bildirebilirsiniz (her zaman bir <xref:System.Boolean> değer), bağımlı bir kitaplığı tanımlar. Her zaman örtük olarak anahtarıdır `false`. Anahtar ayarını `true` etkinleştirir. Anahtar açıkça ayarını `false` yeni davranış sağlar.

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

        ```vb
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
        ```

         Bir tüketici anahtarı değeri belirtmiş ve uygun şekilde hareket üzerinde sonra kitaplık denetlemeniz gerekir.

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

         Bir kitaplığı tarafından kullanıma sunulan resmi bir sözleşme olduğundan anahtarlar için tutarlı bir biçim kullanmak yararlıdır. İki belirgin biçimler şunlardır:

        - *Anahtar*. *ad alanı*. *AnahtarAdı*

        - *Anahtar*. *Kitaplık*. *AnahtarAdı*

    - **Görev tabanlı zaman uyumsuz desen (TAP) değişiklikleri**

         Hedefleyen uygulamalar için [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneleri, kültür ve çağıran iş parçacığı UI kültürünü devralır. .NET Framework'ün önceki sürümlerini hedefleyen ya da belirli bir .NET Framework sürümünü hedef değil uygulamalarının davranışını etkilenmez. Daha fazla bilgi için bkz: "Kültür ve görev tabanlı zaman uyumsuz işlemler" bölümündeki <xref:System.Globalization.CultureInfo> sınıf konusuna.

         <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Sınıfı sağlar, olduğu gibi belirli bir zaman uyumsuz denetim akışı için yerel ortam verileri temsil etmek bir `async` yöntemi. İş parçacıkları arasında verileri kalıcı hale getirmek için kullanılabilir. Ayrıca, ortam veriler olduğundan ya da değiştiğinde bildirilir bir geri çağırma yöntemi tanımlayabilirsiniz <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> açıkça özelliği değiştirildi, veya iş parçacığı bir bağlam geçişi ile karşılaştı.

         Üç kolay yöntem <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, tamamlanan görevler, belirli bir duruma döndürmek için görev tabanlı zaman uyumsuz desen (TAP) eklenmiştir.

         <xref:System.IO.Pipes.NamedPipeClientStream> Sınıfı şimdi kendi yeni zaman uyumsuz iletişim destekler <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. yöntem.

    - **EventSource olay günlüğüne yazma artık desteklemektedir.**

         Artık <xref:System.Diagnostics.Tracing.EventSource> yönetim veya işlem günlüğüne sınıfı iletileri olay günlüğüne, ayrıca makinede oluşturulmuş var olan tüm ETW oturumlarına. Geçmişte, bu işlev için gt;Microsoft.Diagnostics.tracing.EventSource NuGet paketini kullanmanız gerekiyordu. Bu işlevsellik, .NET Framework 4.6'nda yerleşik olarak sunulmuştur.

         NuGet paketi ve .NET Framework 4.6 aşağıdaki özelliklerle güncelleştirilmiştir:

        - **Dinamik olayları**

             "Halindeyken" olay yöntemleri oluşturmadan tanımlanan olayları sağlar.

        - **Zengin yükler**

             İlkel türler, yükü olarak geçirilecek yanı sıra özel öznitelik sınıfları ve diziler sağlar

        - **Etkinlik izleme**

             Başlatma ve durdurma olayları aralarında şu anda etkin olan tüm etkinlikleri temsil eden Kimliğine sahip etiket olayları neden olur.

         Bu destek özelliklerini, aşırı yüklenmiş <xref:System.Diagnostics.Tracing.EventSource.Write%2A> yöntemi eklendi <xref:System.Diagnostics.Tracing.EventSource> sınıfı.

- **Windows Presentation Foundation (WPF)**

    - **HDPI geliştirmeleri**

         HDPI Destek ' WPF'de içinde daha iyi, artık [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Kırpma kenarlıklı denetimlerinde örneklerini azaltmak için yuvarlama Düzen değişiklikler yapıldı. Varsayılan olarak, bu özellik yalnızca etkin, <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET 4.6 için ayarlanır.  Framework'ün önceki sürümlerini hedefleyen ancak üzerinde çalışan uygulamalar [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] içinde yeni davranışı aşağıdaki satırı ekleyerek seçebilirsiniz [ \<çalışma zamanı >](../configure-apps/file-schema/runtime/runtime-element.md) app.config dosyasının:

        ```xml
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         Farklı DPI ayarlarla (çoklu DPI Kurulumu) birden çok monitör payından WPF windows artık blacked genişletme bölgeler tamamen işlenir. Aşağıdaki satırı ekleyerek bu davranışı iptal seçebilirsiniz `<appSettings>` app.config dosyasının yeni bu davranışı devre dışı bırakmak için:

        ```xml
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         Otomatik olarak DPI ayarını temel alarak doğru imleç yüklenirken eklendi desteği <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

    - **Dokunma daha iyidir**

         Müşteri rapor [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) öngörülemeyen davranışlara ele içinde üretir touch [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Windows Store uygulamaları ve WPF uygulamaları için iki kez dokunun eşiği artık Windows 8.1 ve üzeri aynıdır.

    - **Saydam bir alt pencere desteği**

         WPF içinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] saydam alt pencereler Windows 8.1 ve üzeri destekler. Bu, üst düzey windows olmayan ve saydam bir alt öğe pencerelerini oluşturmanıza olanak sağlar. Ayarlayarak bu özelliği etkinleştirebilirsiniz <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> özelliğini `true`.

- **Windows Communication Foundation (WCF)**

    - **SSL desteği**

         WCF artık SSL TLS 1.1 sürümü ve ek olarak SSL 3.0 ve TLS 1.0, TLS 1.2 NetTcp aktarım güvenliği ve istemci kimlik doğrulaması ile kullanırken destekler. Artık, hangi protokolün kullanılacağını veya eski daha az güvenli protokolleri devre dışı bırakmak için seçilecek mümkündür. Bu ayarı tarafından yapılabilir <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> özelliği veya aşağıdaki yapılandırma dosyasına ekleyerek.

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

         WCF artık kullanıcılar farklı temel alınan HTTP bağlantıları kullanarak belirli iletileri gönderildiğinden emin olmak sağlar. Bunu yapmak için iki yol vardır:

        - **Bir bağlantı grup adı ön eki kullanma**

             Kullanıcılar, WCF bağlantı grubu adı için önek olarak kullanacağınız bir dize olarak belirtebilirsiniz. Farklı temel alınan HTTP bağlantıları kullanarak farklı öneklerle iki ileti gönderilir. İletinin bir anahtar/değer çifti ekleyerek ön ek ayarlanır <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> özelliği. "HttpTransportConnectionGroupNamePrefix"; anahtardır değer, istenen önekidir.

        - **Farklı bir kanal fabrikaları kullanma**

             Kullanıcılar, farklı bir kanal fabrikaları tarafından oluşturulan kanalı kullanılarak gönderilen iletilerin farklı temel alınan HTTP bağlantılarını kullanmanızı sağlayan bir özellik de etkinleştirebilirsiniz. Bu özelliği etkinleştirmek için kullanıcılar aşağıdaki ayarlamalısınız `appSetting` için `true`:

            ```xml
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Windows Workflow Foundation (WWF)**

     Artık, bekleyen bir "Protokolü olmayan" yer işareti istek zaman aşımına uğramadan olduğunda bir iş akışı hizmeti için bir sipariş çıkış operation isteğini tutacak saniye sayısını belirtebilirsiniz. "Protokol olmayan" işareti, bekleyen alma etkinliklerle ilgili olmayan bir yer işaretidir. Bazı etkinlikler Protokolü olmayan yer işaretleri, uygulama içinde oluşturarak Protokolü olmayan yer işareti bulunduğunu belirgin olmayabilir. Bunlar, durumu ve çekme içerir. Bu nedenle, uygulanan değerleriyle bir Durum makinesi iş akışı hizmeti veya Pick etkinliği içeren, büyük olasılıkla yapacaklarınız Protokolü olmayan yer işaretleri gerekir. Aşağıdaki gibi bir satır ekleyerek aralığı belirtin `appSettings` app.config dosyanıza bölümünü:

    ```xml
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     Varsayılan değer 60 saniyedir. Varsa `value` ayarlanmış 0, sırası istekler hemen metinle şuna benzer bir hata ile reddedilir:

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
    ```

     Bu sıra dışı işlemi ileti aldığında, aldığınız iletinin ve protokolü olmayan yer işareti yok vardır.

     Varsa değerini `FilterResumeTimeoutInSeconds` sıfır olmayan bir öğedir, Protokolü olmayan yer işaretleri, vardır ve zaman aşımı aralığı sona, işlemi zaman aşımı iletisiyle başarısız olur.

- **İşlemler**

     Artık türetilmiş bir özel duruma neden işlem için Dağıtılmış işlem tanımlayıcısı içerebilir <xref:System.Transactions.TransactionException> oluşturulması için. Aşağıdaki anahtarı ekleyerek bunu `appSettings` app.config dosyanıza bölümünü:

    ```xml
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
    ```

     Varsayılan değer `false` şeklindedir.

- **Ağ**

    - **Yuva yeniden kullanma**

         Windows 10 giden TCP bağlantıları için yerel bağlantı noktaları yeniden kullanarak makine kaynakları daha iyi kullanılmasını sağlayan yeni bir ağ yüksek ölçeklenebilirlik algoritma içerir. .NET framework 4.6, yeni algoritma, yeni davranış yararlanmak .NET uygulamaları etkinleştirme destekler. Önceki Windows sürümlerinde, bir hizmetin ölçeklenebilirlik, yük altında bağlantı noktası tükenmesi neden olarak kısıtlayacaktır bir yapay eş zamanlı bağlantı sınırı (genellikle 16,384, dinamik bağlantı noktası aralığı varsayılan boyutu), vardı.

         İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], eş zamanlı bağlantı 64 K sınırı etkili bir şekilde kaldıran bağlantı noktası yeniden etkinleştirmek için iki yeni API'ler eklenmiştir:

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> Numaralandırma değeri.

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Özelliği.

         Varsayılan olarak, <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliği `false` sürece `HWRPortReuseOnSocketBind` değerini `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` kayıt defteri anahtarını 0x1 olarak ayarlayın. HTTP bağlantılarında yerel bağlantı noktası yeniden etkinleştirmek için <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliğini `true`. Bu, tüm giden TCP yuva bağlantılarından neden <xref:System.Net.Http.HttpClient> ve <xref:System.Net.HttpWebRequest> yeni bir Windows 10 yuva seçeneği kullanmak için [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), yerel bağlantı noktası yeniden kullanımı sağlayan.

         Bir yuva-yalnızca uygulama yazma geliştiriciler belirtebilirsiniz <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> seçeneği gibi bir yöntemi çağırırken <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> giden yuva yerel bağlantı noktaları bağlama sırasında yeniden. böylece.

    - **Uluslararası etki alanı adları ve zayıf kod desteği**

         Yeni bir özellik <xref:System.Uri.IdnHost%2A>, eklenen <xref:System.Uri> uluslararası etki alanı adları ve zayıf kod daha iyi desteklemek için sınıf.

- **Windows Forms denetimlerinde yeniden boyutlandırma.**

     Bu özellik, Genişletilmiş [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] içerecek şekilde <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.ToolStripSplitButton> türleri ve tarafından belirtilen dikdörtgen <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> çizerken kullanılan özellik bir <xref:System.Drawing.Design.UITypeEditor> .

     Bu bir katılım özelliğidir. Bunu etkinleştirmek için ayarlanmış `EnableWindowsFormsHighDpiAutoResizing` öğesine `true` uygulama yapılandırma (app.config) dosyasında:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Kod sayfası kodlamaları için destek**

     .NET core, öncelikle Unicode kodlamaları destekler ve varsayılan olarak, kod sayfası kodlamaları için sınırlı destek sağlar. İle kod sayfası kodlamalarını kaydederek .NET Framework'de kullanılabilen ancak .NET core'da desteklenmeyen kod sayfası kodlamaları için destek ekleyebilirsiniz <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> yöntemi. Daha fazla bilgi için bkz. <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

     .NET Core hedefleyen ve yazıldığı Windows uygulamalarını Windows 10 için C# veya Visual Basic, uygulamaları IL yerine yerel koda derleyen yeni bir teknoloji avantajlarından faydalanabilirsiniz. Bunlar, uygulamaları daha hızlı başlangıç ve yürütme süreleri tarafından temsil edilen üretir. Daha fazla bilgi için [.NET Native ile uygulamalar derlemek](../net-native/index.md). Anlamına gelir, kodunuz için .NET JIT derlemesi hem NGEN benzerlikleri ve hangi, inceleyen yerel genel bakış için bkz. [.NET Native ve derleme](../net-native/net-native-and-compilation.md).

     Bunları Visual Studio 2015 veya sonraki derleme yaptığınızda uygulamalarınızın yerel kod için varsayılan olarak derlenir. Daha fazla bilgi için [.NET Native ile çalışmaya başlama](../net-native/getting-started-with-net-native.md).

     Hata ayıklama .NET Native uygulamaları desteklemek için bir dizi yeni arabirimleri ve sabit listeleri için yönetilmeyen hata ayıklama API'si eklenmiştir. Daha fazla bilgi için [hata ayıklama (yönetilmeyen API Başvurusu)](../unmanaged-api/debugging/index.md) konu.

- **Açık kaynak .NET Framework paketleri**

     Sabit koleksiyonlar gibi .NET core paketleri [SIMD API'leri](https://go.microsoft.com/fwlink/?LinkID=518639), ve API'leri gibi ağ bulunan <xref:System.Net.Http> ad alanı şu anda açık kaynak paketleri olarak kullanılabilir durumda [GitHub](https://github.com/). Kod erişmek için bkz: [github'da Corefx'te](https://github.com/dotnet/corefx). Daha fazla bilgi ve bu paketlere katkıda bulunmak için bkz: [.NET Core ve açık kaynaklı](../get-started/net-core-and-open-source.md), [GitHub .NET giriş sayfasında](https://github.com/dotnet/home).

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a>.NET Framework 4.5.2 yenilikler

- **ASP.NET uygulamaları için yeni API'ler sağlar.** Yeni <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> yöntemleri inceleyin ve yanıtı istemci uygulamasına Temizlenen olarak yanıt üst bilgileri ve durum kodunu değiştirmenizi sağlar. Yerine bu yöntemleri kullanmayı <xref:System.Web.HttpApplication.PreSendRequestHeaders> ve <xref:System.Web.HttpApplication.PreSendRequestContent> olayları; daha etkili ve güvenilir.

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Küçük arka plan iş öğeleri zamanlama yöntemi sağlar. ASP.NET, bu öğeler izler ve tüm arka plan iş öğelerini tamamlayıncaya kadar aniden çalışan işlemi sonlandırılıyor dan IIS engeller. Bu yöntem, bir ASP.NET yönetilen uygulama etki alanı dışında çağrılamaz.

     Yeni <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> özellikleri yanıt üstbilgilerini yazılmış olup olmadığını gösteren Boole değerleri döndürür. Bu özellikler emin olmak için API'leri gibi çağıran kullanabilirsiniz <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (üstbilgileri yazılmış, özel durumlar) başarılı olur.

- **Windows Forms denetimlerinde yeniden boyutlandırma.** Bu özelliği genişletildi. Sistem DPI ayarı artık aşağıdaki ek denetimleri (örneğin, birleşik giriş kutuları, açılan liste okunu) bileşenleri yeniden boyutlandırmak için de kullanabilirsiniz:

    - <xref:System.Windows.Forms.ComboBox>
    - <xref:System.Windows.Forms.ToolStripComboBox>
    - <xref:System.Windows.Forms.ToolStripMenuItem>
    - <xref:System.Windows.Forms.Cursor>
    - <xref:System.Windows.Forms.DataGridView>
    - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     Bu bir katılım özelliğidir. Bunu etkinleştirmek için ayarlanmış `EnableWindowsFormsHighDpiAutoResizing` öğesine `true` uygulama yapılandırma (app.config) dosyasında:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Yeni iş akışı özelliği.** Kullanan bir kaynak yöneticisi <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> yöntemi (ve bu nedenle uygulama <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi) yeni kullanabilirsiniz <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> yöntemi aşağıdaki istemek için:

    - Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem harekete tanıtın.

    - Değiştirin <xref:System.Transactions.IPromotableSinglePhaseNotification> ile bir <xref:System.Transactions.ISinglePhaseNotification>, tek aşaması işlemeler destekleyen kalıcı bir liste olduğu.

     Bu aynı uygulama etki alanında yapılabilir ve yükseltmeyi gerçekleştirmek için MSDTC ile etkileşim kurmak için herhangi bir ekstra yönetilmeyen kod gerektirmez. Yalnızca bir bekleyen çağrısından olduğunda yeni yöntem çağrılabilir <xref:System.Transactions?displayProperty=nameWithType> için <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` promotable liste tarafından uygulanan yöntem.

- **Profil oluşturma geliştirmeleri.** Aşağıdaki yeni yönetilmeyen profil oluşturma API'leri daha sağlam profil oluşturma sağlar:

    - [COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
    - [COR_PRF_HIGH_MONITOR Sabit Listesi](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
    - [GetAssemblyReferences Yöntemi](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
    - [GetEventMask2 Yöntemi](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
    - [SetEventMask2 Yöntemi](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
    - [AddAssemblyReference Yöntemi](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     Önceki `ICorProfiler` uygulamalarında desteklenen bağımlı derlemelerin yavaş yükleniyor. Yeni profil oluşturma API'ları, uygulamayı tamamen yeniden başlatıldıktan sonra hemen yüklenen yerine yüklenebilir olması için Profil Oluşturucu tarafından eklenen bağımlı derlemeleri gerektirir. Bu değişiklik varolan kullanıcıları etkilemez `ICorProfiler` API'leri.

- **Hata ayıklama geliştirmeleri.** Aşağıdaki yeni yönetilmeyen hata ayıklama API'leri bir profil oluşturucu ile daha iyi tümleştirme sağlar. Erişim meta verileri ve profil oluşturucu hem de yerel değişkenleri ve kod tarafından eklenen derleyici ReJIT istekleri tarafından üretilen artık, hata ayıklama dökümü.

    - [SetWriteableMetadataUpdateMode Yöntemi](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
    - [EnumerateLocalVariablesEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
    - [GetLocalVariableEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
    - [GetCodeEx Yöntemi](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
    - [GetActiveReJitRequestILCode Yöntemi](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
    - [GetInstrumentedILMap Yöntemi](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Değişiklik izleme olayı.** .NET framework 4.5.2 için daha geniş bir yüzey alanını işlem dışı, olay izleme için Windows ETW tabanlı Etkinlik izleme sağlar. Bu, tek tek isteklerin ve iş parçacıkları arası etkinlikleri maliyetlerini doğru şekilde izleyen basit Araçlar sağlamak güç yönetimi (APM) satıcıları sağlar.  Yalnızca ETW denetleyicileri bunları etkinleştirdiğinizde, bu olaylar oluşturulur; Bu nedenle, önceden yazılmış ETW kodu veya devre dışı ETW ile çalışan kod değişiklikleri etkilemez.

- **İşlem yükseltme ve kalıcı bir liste dönüştürme**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> Yeni bir API, .NET Framework 4.5.2 ve 4.6 eklenir:

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

    ```vb
    <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
    public Function PromoteAndEnlistDurable(GresourceManagerIdentifier As Guid,
                                            promotableNotification As IPromotableSinglePhaseNotification,
                                            enlistmentNotification As ISinglePhaseNotification,
                                            enlistmentOptions As EnlistmentOptions) As Enlistment
    ```

     Yöntemi tarafından önceden oluşturulmuş bir liste tarafından kullanılabilir <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> yanıt olarak <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> yöntemi. Bunu ister `System.Transactions` işlem için bir MSDTC işlem yükseltmek ve "kalıcı bir liste promotable liste dönüştürmek için". Bu yöntem başarıyla tamamlandıktan sonra <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi artık başvuru tarafından `System.Transactions`, ve gelecekteki tüm bildirimleri sağlanan ulaşır <xref:System.Transactions.ISinglePhaseNotification> arabirimi. Söz konusu liste, işlem günlüğü ve kurtarma destekleyen bir kalıcı liste davranmalıdır. Başvurmak <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> Ayrıntılar için. Ayrıca, liste desteklemelidir <xref:System.Transactions.ISinglePhaseNotification>.  Bu yöntem için *yalnızca* işlenirken çağrılabilir bir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> çağırın. Bu durumda değilse bir <xref:System.Transactions.TransactionException> özel durumu oluşturulur.

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a>.NET Framework 4.5.1'teki yenilikler

**Nisan 2014 güncelleştirmeleri**:

- [Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) güncelleştirmeleri bu senaryoları desteklemek için taşınabilir sınıf kitaplığı şablonları içerir:

    - Windows 8.1, Windows Phone 8.1 ve Windows Phone Silverlight 8. 1'i hedefleyen taşınabilir kitaplıklarda Windows Runtime API'ları kullanabilirsiniz.

    - Windows 8.1 veya Windows Phone 8.1 hedeflediğinizde taşınabilir kitaplıklarda XAML (Windows.UI.XAML türleri) içerebilir. Aşağıdaki XAML şablonlar desteklenir:  Boş sayfa, kaynak sözlüğü, şablonlu denetim ve kullanıcı denetimi.

    - Windows 8.1 ve Windows Phone 8.1 hedefleyen Store uygulamaları kullanmak için taşınabilir bir Windows çalışma zamanı bileşeni (.winmd dosyası) oluşturabilirsiniz.

    - Taşınabilir sınıf kitaplığı gibi bir Windows Store veya Windows Phone Store sınıf kitaplığı hedefleyebilirsiniz.

     Bu değişiklikler hakkında daha fazla bilgi için bkz. [taşınabilir sınıf kitaplığı](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Artık .NET Framework içerik belgeleri içerir [!INCLUDE[net_native](../../../includes/net-native-md.md)], oluşturmak ve Windows uygulamalarını dağıtmak için bir ön derleme teknolojisi olduğu. [!INCLUDE[net_native](../../../includes/net-native-md.md)] uygulamalarınızı doğrudan yerel kod yerine Ara dil (IL) daha iyi performans için derler. Ayrıntılar için bkz [.NET Native ile uygulamalar derlemek](../net-native/index.md).

- [.NET Framework başvuru kaynağı](https://referencesource.microsoft.com/) yeni gözatma deneyimi ve geliştirilmiş işlevselliği sağlar. Artık .NET Framework kaynak kodu çevrimiçi olarak göz atabilirsiniz [başvuru indirme](https://referencesource.microsoft.com/download.html) çevrimdışı izleme ve hata ayıklama sırasında (düzeltme eklerini ve güncelleştirmeleri gibi) kaynakları adımlayın. Daha fazla bilgi için blog girişine bakın [.NET başvuru kaynağı için yeni bir görünüm](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).

Yeni özellikler ve temel sınıfları .NET Framework 4.5.1'deki geliştirmeler şunları içerir:

- Derlemeler için otomatik bağlama yeniden yönlendirme. Visual Studio 2013 ile başlayarak, derleme yaptığınızda hedefleyen bir uygulama [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], bağlama yönlendirmeleri eklenebilir uygulama yapılandırma dosyasına uygulamanız veya bileşenleri aynı derlemenin birden çok sürümüne başvuruyorsa. Bu özellik .NET Framework'ün eski sürümlerini hedefleyen projeler için de etkinleştirebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Enable ve Disable otomatik bağlama yeniden yönlendirme](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Geliştiricilerin sunucu ve bulut uygulamalarının performansını artırmak amacıyla tanılama bilgilerini toplama yeteneği. Daha fazla bilgi için <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> ve <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> yöntemleri <xref:System.Diagnostics.Tracing.EventSource> sınıfı.

- Açıkça büyük nesne yığını (LOH) çöğ toplama sırasında biriktirme yeteneği. Daha fazla bilgi için <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliği.

- .NET Framework sonra ASP.NET uygulama askıya alma, çok çekirdekli JIT geliştirmeleri ve daha hızlı uygulama başlatma gibi ek performans artışları güncelleştirin. Ayrıntılar için bkz [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) ve [ASP.NET uygulama askıya alma](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog gönderisi.

Windows Forms için geliştirmeler şunlardır:

- Windows Forms denetimlerinde yeniden boyutlandırma. Sistem DPI ayarı, uygulamanız için uygulama yapılandırma dosyasına (app.config) girişte oturum çıkarak denetimler (örneğin, bir özellik kılavuzunda görüntülenen simgeler) bileşenleri yeniden boyutlandırmak için kullanabilirsiniz. Bu özellik şu anda aşağıdaki Windows Forms denetimlerinde desteklenir:

    - <xref:System.Windows.Forms.PropertyGrid>
    - <xref:System.Windows.Forms.TreeView>
    - Bazı yönlerini <xref:System.Windows.Forms.DataGridView> (bkz [4.5.2'deki yeni özellikler](#v452) desteklenen ek denetimler için)

     Bu özelliği etkinleştirmek için yeni bir ekleme \<appSettings > ayarlama ve yapılandırma dosyası (app.config) öğesine `EnableWindowsFormsHighDpiAutoResizing` öğesine `true`:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

.NET Framework uygulamalarınızı Visual Studio 2013'te hata ayıklama sırasında geliştirmeler şunlardır:

- Visual Studio hata ayıklayıcıda dönüş değerleri. Visual Studio 2013'te yönetilen bir uygulamada hata ayıklaması yaparken otomatik değişkenler penceresi dönüş türleri ve yöntemleri için değerleri görüntüler. Bu bilgiler Masaüstü, Windows Store ve Windows Phone uygulamaları için kullanılabilir. Daha fazla bilgi için [yöntem çağrılarının dönüş değerlerini İnceleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).

- Düzenle ve devam etmek için 64-bit uygulamalar. Visual Studio 2013, 64 bit yönetilen uygulamaları, masaüstü, Windows Store ve Windows Phone için Düzenle ve devam et özelliğini destekler. Varolan kısıtlamalar hem 32-bit hem de 64-bit uygulamalar için yürürlükte kalır. (son bölümüne bakın [desteklenen kod değişiklikleri (C#)](/visualstudio/debugger/supported-code-changes-csharp) makale).

- Zaman uyumsuz yönteme duyarlı hata ayıklama. Visual Studio 2013'te zaman uyumsuz uygulamalarında hata ayıklama daha kolay hale getirmek için çağrı yığınını Zamanuyumsuz programlamayı desteklemek için derleyiciler tarafından sağlanan altyapı kodunu gizler ve daha fazla mantıksal program yürütme izleyebilmeniz mantıksal üst çerçeve içinde ayrıca zincir NET bir şekilde. Görevler penceresi Paralel Görevler penceresinin yerine geçer ve belirli bir kesme noktasıyla ilgili görevleri görüntüler ve ayrıca şu anda uygulamada zamanlanmış veya etkin olan diğer görevleri de görüntüler. "Zaman uyumsuz yönteme duyarlı hata ayıklama" bölümünde bu özellikle ilgili bilgi edinebilirsiniz [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

- Windows çalışma zamanı bileşenleri için daha iyi özel durum desteği. İçinde [!INCLUDE[win81](../../../includes/win81-md.md)], Windows Store uygulamalarından doğan özel durumlar, dil sınırları dahil özel duruma neden olan hata hakkında bilgi koruma. "Windows Store uygulaması geliştirme" bölümünde bu özellikle ilgili bilgi edinebilirsiniz [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).

Kullanabileceğiniz Visual Studio 2013 ile başlayarak, [yönetilen profil Kılavuzlu optimizasyon Aracı (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) iyileştirmek için [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Masaüstü uygulamaların yanı sıra uygulamaları.

ASP.NET 4.5.1'deki yeni özellikler için bkz: [için ASP.NET and Web Tools Visual Studio 2013 sürüm notları](/aspnet/visual-studio/overview/2013/release-notes).

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a>.NET Framework 4. 5 ' yenilikler nelerdir?

### <a name="base-classes"></a>Temel sınıflar

- Reduce sistemi olanağı algılayarak ve dağıtım sırasında .NET Framework 4 uygulamaları kapatarak yeniden başlatır. Bkz: [sistem yeniden başlatmalarını azaltma .NET Framework 4.5 yüklemeleri sırasında](../deployment/reducing-system-restarts.md).

- 64-bit platformlarda 2 gigabayt'tan (GB) büyük diziler için destek. Bu özellik, uygulama yapılandırma dosyasında etkinleştirilebilir. Bkz: [ \<gcAllowVeryLargeObjects > öğesi](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), nesne boyutu ve dizi boyutu üzerindeki diğer kısıtlamaları da listelenir.

- Arka plan çöp toplama sunucuları için daha iyi performans. Sunucu çöp toplama kullandığınızda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], arka plan çöp toplama otomatik olarak etkinleştirilir. Arka plan sunucusu çöp toplama bölümüne bakın [çöp toplamanın Temelleri](../../standard/garbage-collection/fundamentals.md) konu.

- Uygulama performansını artırmak için çok çekirdekli işlemcilerde isteğe bağlı olarak kullanılabilir arka plan just-in-time (JIT) derleme. Bkz. <xref:System.Runtime.ProfileOptimization>.

- Normal ifade motorunun ne kadar sınırlama yeteneği, normal ifade zaman aşımına uğramadan önce çözümlemeyi dener. Bkz: <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> özelliği.

- Uygulama etki alanı için varsayılan kültürü tanımlama yeteneği. Bkz: <xref:System.Globalization.CultureInfo> sınıfı.

- Unicode (UTF-16) kodlaması için konsol desteği. Bkz: <xref:System.Console> sınıfı.

- Kültürel dize sıralama ve karşılaştırma verilerinin sürümü oluşturma desteği. Bkz: <xref:System.Globalization.SortVersion> sınıfı.

- Kaynaklar alınırken daha iyi performans. Bkz: [paketleme ve dağıtma kaynakları](../resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Sıkıştırılmış bir dosya boyutunu azaltmak için zip sıkıştırma işlevinde geliştirmeler. Bkz: <xref:System.IO.Compression?displayProperty=nameWithType> ad alanı.

- Aracılığıyla varsayılan yansıtma davranışını geçersiz kılmak için Yansıtmalı bir bağlamı özelleştirme yeteneği <xref:System.Reflection.Context.CustomReflectionContext> sınıfı.

- Uluslararası yapılan etki adlarını in Applications (IDNA) 2008 sürümü için destek standart olduğunda <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> sınıfı ınternationalized [!INCLUDE[win8](../../../includes/win8-md.md)].

- .NET Framework üzerinde kullanıldığında Unicode 6.0 uygulayan işletim sistemine, dize karşılaştırma temsilcisi [!INCLUDE[win8](../../../includes/win8-md.md)]. Başka platformlarda çalışırken, .NET Framework, Unicode uygulayan kendi dize karşılaştırma verilerini içerir. 5.x. Bkz: <xref:System.String> sınıfı ve Açıklamalar bölümüne <xref:System.Globalization.SortVersion> sınıfı.

- Dizeler için karma kodları hesaplama yeteneği bir her uygulama etki alanı. Bkz: [ \<UseRandomizedStringHashAlgorithm > öğesi](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Tür yansıtma desteği arasında bölünür <xref:System.Type> ve <xref:System.Reflection.TypeInfo> sınıfları. Bkz: [Windows Store uygulamaları için .NET Framework'te yansıma](../reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Yönetilen Genişletilebilirlik Çerçevesi (MEF) aşağıdaki yeni özellikleri sağlar:

- Genel türler için destek.

- Nitelikler yerine adlandırma kurallarına göre bölümleri oluşturmanıza olanak tanıyan kural tabanlı programlama modeli.

- Birden çok kapsam.

- Bir alt kümesini oluşturduğunuzda kullandığınız MEF [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Bu alt küme olarak kullanılabilir bir [indirilebilir paket](https://go.microsoft.com/fwlink/?LinkId=256238) NuGet Gallery sayfasından. Paketi yüklemek için projenizi Visual Studio'da açın, **NuGet paketlerini Yönet** gelen **proje** menü ve çevrimiçi olarak arayın `Microsoft.Composition` paket.

Daha fazla bilgi için [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](../mef/index.md).

### <a name="asynchronous-file-operations"></a>Zaman uyumsuz dosya işlemleri

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], C# ve Visual Basic diller için yeni zaman uyumsuz özellikler eklenmiştir. Bu özellikler, zaman uyumsuz işlemleri gerçekleştirmek için görev tabanlı bir model ekler. Bu yeni modeli kullanmak için g/ç sınıflarında zaman uyumsuz yöntemleri kullanın. Bkz: [zaman uyumsuz dosya g/ç](../../standard/io/asynchronous-file-i-o.md).

<a name="tools" />

### <a name="tools"></a>Araçlar

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kaynak dosya oluşturucu (Resgen.exe) kullanmak üzere bir .resw dosyası oluşturmanıza imkan tanır [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları bir .resources dosyasından bir .NET Framework derlemesine katıştırılmış. Daha fazla bilgi için [Resgen.exe (kaynak dosya oluşturucu)](../tools/resgen-exe-resource-file-generator.md).

Yönetilen profil temelli iyileştirme (Mpgo.exe), yerel görüntü derlemelerini en iyi duruma getirme tarafından uygulama başlangıç zamanı, bellek kullanımı (çalışma kümesi boyutu) ve aktarım hızı geliştirmenizi sağlar. Komut satırı aracı yerel görüntü uygulama derlemeleri için profil verileri oluşturur. Bkz: [Mpgo.exe (yönetilen profil temelli iyileştirme aracı)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Visual Studio 2013 ile başlayarak, en iyi duruma getirmek için Mpgo.exe'yi kullanabilirsiniz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Masaüstü uygulamaların yanı sıra uygulamaları.

<a name="parallel" />

### <a name="parallel-computing"></a>Paralel hesaplama

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Çeşitli yeni özellikler ve geliştirmeler, paralel bilgi işlem sağlar. Bunlar, Gelişmiş performans, artırılmış denetim, zaman uyumsuz programlama için gelişmiş destek, yeni bir veri akışı kitaplığı ve paralel hata ayıklama ve performans analizi için geliştirilmiş destek içerir. Girdisine bakın [.NET 4.5 paralellikteki yenilikler](https://go.microsoft.com/fwlink/?LinkId=235061) .NET Web günlüğü ile paralel programlama içindeki.

<a name="web" />

### <a name="web"></a>Web

ASP.NET 4.5 ve 4.5.1 Web formları, WebSocket desteği, zaman uyumsuz işleyiciler, performans iyileştirmeleri ve diğer birçok özelliği için bağlama modeli ekler. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [ASP.NET 4.5 ve Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))

- [Visual Studio 2013 için ASP.NET and Web Tools Sürüm Notları](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking-a-namenetworking-"></a>Ağ iletişimi <a name="networking" />

[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] HTTP uygulamaları için yeni bir programlama arabirimi sağlar. Daha fazla bilgi için bkz. yeni <xref:System.Net.Http?displayProperty=nameWithType> ve <xref:System.Net.Http.Headers?displayProperty=nameWithType> ad alanları.

Destek kabul eden ve mevcut kullanılarak bir WebSocket bağlantısı ile etkileşim için yeni bir programlama arabirimi için dahil edilen ayrıca <xref:System.Net.HttpListener> ve ilgili sınıflar. Daha fazla bilgi için bkz. yeni <xref:System.Net.WebSockets> ad alanı ve <xref:System.Net.HttpListener> sınıfı.

Ayrıca, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aşağıdaki ağ geliştirmeleri içerir:

- RFC uyumlu URI desteği. Daha fazla bilgi için <xref:System.Uri> ve ilgili sınıflar.

- Uluslararası yapılan etki alanı adı (IDN) ayrıştırma desteği. Daha fazla bilgi için <xref:System.Uri> ve ilgili sınıflar.

- E-posta adresi uluslararası duruma getirme (EAI) desteği. Daha fazla bilgi için <xref:System.Net.Mail> ad alanı.

- Gelişmiş IPv6 desteği. Daha fazla bilgi için <xref:System.Net.NetworkInformation> ad alanı.

- Çift modlu yuva desteği. Daha fazla bilgi için <xref:System.Net.Sockets.Socket> ve <xref:System.Net.Sockets.TcpListener> sınıfları.

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Presentation Foundation (WPF), değişiklikler ve aşağıdaki alanlarda geliştirmeler içerir:

- Yeni <xref:System.Windows.Controls.Ribbon.Ribbon> hızlı erişim araç çubuğu, uygulama menüsü ve sekmeler barındıran Şerit kullanıcı arabirimini uygulamanızı sağlayan bir denetimi.

- Yeni <xref:System.ComponentModel.INotifyDataErrorInfo> zaman uyumlu ve zaman uyumsuz veri doğrulamasını destekleyen arabirimi.

- Yeni özellikleri <xref:System.Windows.Controls.VirtualizingPanel> ve <xref:System.Windows.Threading.Dispatcher> sınıfları.

- Büyük görüntülerken, Gelişmiş performans, gruplandırılmış veri ve UI olmayan iş parçacıklarında koleksiyonlara erişerek ayarlar.

- Statik özelliklere veri bağlama, özel veri bağlama uygulayan türleri <xref:System.Reflection.ICustomTypeProvider> arabirimi ve bir bağlama ifadesinden veri bağlama bilgisi alımı.

- (Canlı şekillendirme) değerleri değiştikçe verileri yeniden konumlandırma.

- Öğe kapsayıcı için veri bağlamının bağlantısının kesilip kesilmediğini kontrol yeteneği.

- Özellik değişiklikleri ve veri kaynağı güncelleştirmeleri arasında geçmesi gereken süreyi ayarlama yeteneği.

- Zayıf olay desenlerini uygulamak için geliştirilmiş destek. Ayrıca, olayları artık biçimlendirme uzantılarını kabul edebilir.

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], yazma ve Windows Communication Foundation (WCF) uygulamalarını basitleştirmek için aşağıdaki özellikler eklenmiştir:

- Üretilen yapılandırma dosyalarını basitleştirme.

- Sözleşme ilk geliştirmesi için destek.

- Daha kolay ASP.NET uyumlu mod yapılandırma yeteneği.

- Değişiklikleri varsayılan özellik değerleri, bunları ayarlamak zorunda kalacaksınız olasılığını azaltmak için taşıma.

- Güncelleştirmeleri <xref:System.Xml.XmlDictionaryReaderQuotas> XML sözlük okuyucularına yönelik kotaları el gerekecektir olasılığını azaltmak için sınıf.

- Uygulamanızı çalıştırmadan önce yapılandırma hatalarını algılayabilmeniz için yapı işleminin parçası olarak WCF yapılandırma dosyalarının Visual Studio tarafından doğrulanması.

- Yeni zaman uyumsuz akış desteği.

- Internet Information Services (IIS) ile HTTPS üzerinden bir uç noktanın kullanıma daha kolay hale getirmek için yeni HTTPS protokolü eşlemesi.

- Ekleyerek tek bir WSDL belgesinde meta veriler oluşturma yeteneği `?singleWSDL` hizmet URL'si.

- Websockets, 80 ve 443 numaralı TCP aktarımına benzer performans özellikleri olan bağlantı noktaları üzerinde doğru çift yönlü iletişimi etkinleştirmek için destek.

- Kodda hizmetlerin yapılandırılması için destek.

- XML Düzenleyicisi araç ipuçları.

- <xref:System.ServiceModel.ChannelFactory> önbelleğe alma desteği.

- İkili Kodlayıcı sıkıştırma desteği.

- "Başlat ve unut" kullanan hizmetler yazmasına geliştiricilerin sağlayan bir UDP taşıma desteği Mesajlaşma. Bir istemci bir hizmete ileti gönderir ve hizmetten yanıt bekliyor.

- HTTP taşıma ve Taşım güvenliği kullanıldığında tek bir WCF uç noktada birden çok kimlik doğrulama modları destekleme yeteneği.

- Kullanan WCF hizmetleri için destek Uluslararası yapılan etki adlarını (IDN'ler).

Daha fazla bilgi için [Windows Communication Foundation'da yenilikler](https://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)

İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Workflow Foundation (WF) için birkaç yeni özellik eklenmiştir dahil olmak üzere:

- Durum ilk kez .NET Framework 4.0.1'in parçası olarak sunulan makine iş akışları ([.NET Framework 4 Platform Update 1](https://go.microsoft.com/fwlink/?LinkID=215092)). Bu güncelleştirme birkaç yeni sınıfı ve geliştiricilerin durum makine iş akışları oluşturmak etkinlikler dahil. Bu sınıflar ve etkinlikler için güncelleştirilmiştir [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] eklemek için:

    - Durumlar üzerinde kesme noktaları ayarlama yeteneği.

    - İş akışı tasarımcısında geçişleri yapıştırın yeteneği.

    - Paylaşılan tetikleyici geçişi oluşumu için tasarımcı desteği.

    - Etkinlikler dahil olmak üzere durum makine iş akışları oluşturmak için: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, ve <xref:System.Activities.Statements.Transition>.

- Aşağıdaki gibi gelişmiş iş akışı Tasarımcısı özellikleri:

    - Geliştirilmiş Visual Studio iş akışı arama özellikleri dahil olmak üzere **Hızlı Bul** ve **dosyalarda Bul**.

    - Bir kapsayıcı etkinliğe ikinci bir alt etkinlik eklendiğinde otomatik olarak bir sıralama etkinliği oluşturma ve her iki etkinliğini de sıralama etkinliğine dahil yeteneği.

    - Kaydırma çubukları kullanılmadan değiştirilmesine bir iş akışının görünür bölümünün sağlayan kaydırma desteği.

    - Yeni bir **belge anahattı** görünümü, ağaç stili ana görünümünde iş akışının bileşenlerini gösterir ve sağlar bir bileşeni seçmenize **belge anahattı** görünümü.

    - Ek açıklamalar ekleme yeteneği.

    - Tanımlama ve iş akışı Tasarımcısı kullanarak etkinlik temsilcileri kullanma olanağı.

    - Otomatik bağlanma ve etkinlikleri ve geçişler, durum makine ve akış çizelgesi iş akışları için Otomatik Ekle.

- Görünüm durumu bilgilerini kolayca bulun ve görünüm durumu bilgilerini düzenlemek için XAML dosyasında tek bir öğede bir iş akışı için depolama alanı.

- Çocuk etkinliklerinin kalıcı önlemek için bir NoPersistScope kapsayıcı etkinliği.

- C# ifadeleri için destek:

    - Visual Basic kullanan iş akışı projeleri Visual Basic deyimleri kullanacak ve C# iş akışı projeleri C# ifadeleri kullanacaktır.

    - Visual Studio 2010'da oluşturulmuş olan ve Visual Basic deyimleri içeren C# iş akışı projeleri C# ifadelerini kullanan C# iş akışı projeleri ile uyumlu değildir.

- Sürüm oluşturma ile ilgili geliştirmeler:

    - Yeni <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneği iş akışı tanımı arasında bir eşleme sağlar sınıfını.

    - Dahil olmak üzere aynı konakta birden çok iş akışı sürümünün yan yana yürütülmesi <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

    - Dinamik Güncelleştirme'de kalıcı iş akışı örneğinin tanımını değiştirebilme.

- Sözleşme ilk iş akışı hizmet geliştirme otomatik olarak mevcut bir hizmet sözleşmesi ile eşleşmesi için etkinlikleri oluşturmak için destek sağlar.

 Daha fazla bilgi için [Windows Workflow Foundation'daki yenilikler](https://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored" />

### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]

[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamaları belirli biçim faktörleri için tasarlanmıştır ve Windows işletim sisteminin gücünden yararlanın. Bir alt kümesini [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya 4.5.1 için yapı kullanılabilir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] C# veya Visual Basic kullanarak Windows için uygulamalar. Bu alt küme olarak adlandırılan [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] ele alınır bir [genel bakış](https://go.microsoft.com/fwlink/?LinkId=228491) Windows geliştirme Merkezi'nde.

### <a name="portable-class-libraries-a-nameportable-"></a>Taşınabilir sınıf kitaplıkları <a name="portable" />

Taşınabilir sınıf kitaplığı projesi Visual Studio 2012 (ve sonraki sürümler), yazma ve Yönetilen derlemeler çalışan birden çok .NET Framework platformunda çalışan yapı sağlar. Taşınabilir sınıf kitaplığı projesi kullanarak platformlarını seçin (Windows Phone gibi ve [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) hedef. Kullanılabilir türler ve üyeler, projenizdeki bu platformlardaki ortak türler ve üyeler otomatik olarak kısıtlanır. Daha fazla bilgi için [taşınabilir sınıf kitaplığı](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework ve Bant Dışı Yayınlar](../get-started/the-net-framework-and-out-of-band-releases.md)
- [Erişilebilirlik .NET Framework'teki yenilikler](whats-new-in-accessibility.md)
- [Visual Studio 2017'deki yenilikler](/visualstudio/ide/whats-new-in-visual-studio)
- [ASP.NET](/aspnet)
- [Visual C++ yenilikleri](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
