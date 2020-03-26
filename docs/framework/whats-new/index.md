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
ms.openlocfilehash: d5657f4081577b2a27bc3c2f6880784015c56060
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249701"
---
# <a name="whats-new-in-net-framework"></a><span data-ttu-id="8b6b2-102">.NET Framework'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-102">What's new in .NET Framework</span></span>

<span data-ttu-id="8b6b2-103">Bu makalede, .NET Framework'ün aşağıdaki sürümlerindeki önemli yeni özellikler ve geliştirmeler özetlenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-103">This article summarizes key new features and improvements in the following versions of the .NET Framework:</span></span>

- [<span data-ttu-id="8b6b2-104">.NET Çerçeve 4.8</span><span class="sxs-lookup"><span data-stu-id="8b6b2-104">.NET Framework 4.8</span></span>](#v48)
- [<span data-ttu-id="8b6b2-105">.NET Çerçeve 4.7.2</span><span class="sxs-lookup"><span data-stu-id="8b6b2-105">.NET Framework 4.7.2</span></span>](#v472)
- [<span data-ttu-id="8b6b2-106">.NET Çerçeve 4.7.1</span><span class="sxs-lookup"><span data-stu-id="8b6b2-106">.NET Framework 4.7.1</span></span>](#v471)
- [<span data-ttu-id="8b6b2-107">.NET Çerçeve 4.7</span><span class="sxs-lookup"><span data-stu-id="8b6b2-107">.NET Framework 4.7</span></span>](#v47)
- [<span data-ttu-id="8b6b2-108">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="8b6b2-108">.NET Framework 4.6.2</span></span>](#v462)
- [<span data-ttu-id="8b6b2-109">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="8b6b2-109">.NET Framework 4.6.1</span></span>](#v461)
- [<span data-ttu-id="8b6b2-110">.NET 2015 ve .NET Çerçeve 4.6</span><span class="sxs-lookup"><span data-stu-id="8b6b2-110">.NET 2015 and .NET Framework 4.6</span></span>](#v46)
- [<span data-ttu-id="8b6b2-111">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="8b6b2-111">.NET Framework 4.5.2</span></span>](#v452)
- [<span data-ttu-id="8b6b2-112">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="8b6b2-112">.NET Framework 4.5.1</span></span>](#v451)
- [<span data-ttu-id="8b6b2-113">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8b6b2-113">.NET Framework 4.5</span></span>](#v45)

<span data-ttu-id="8b6b2-114">Bu makalede, her yeni özellik hakkında kapsamlı bilgi sağlamaz ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-114">This article does not provide comprehensive information about each new feature and is subject to change.</span></span> <span data-ttu-id="8b6b2-115">.NET Framework hakkında genel bilgi için [bkz.](../get-started/index.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-115">For general information about the .NET Framework, see [Getting Started](../get-started/index.md).</span></span> <span data-ttu-id="8b6b2-116">Desteklenen platformlar için [Sistem Gereksinimleri'ne](../get-started/system-requirements.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-116">For supported platforms, see [System Requirements](../get-started/system-requirements.md).</span></span> <span data-ttu-id="8b6b2-117">İndirme bağlantıları ve yükleme yönergeleri için [Kurulum Kılavuzu'na](../install/guide-for-developers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-117">For download links and installation instructions, see [Installation Guide](../install/guide-for-developers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8b6b2-118">.NET Framework ekibi ayrıca platform desteğini genişletmek ve değişmez koleksiyonlar ve SIMD özellikli vektör türleri gibi yeni işlevleri tanıtmak için NuGet ile bant dışı özellikler de yayımlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-118">The .NET Framework team also releases features out of band with NuGet to expand platform support and to introduce new functionality, such as immutable collections and SIMD-enabled vector types.</span></span> <span data-ttu-id="8b6b2-119">Daha fazla bilgi için [ek sınıf kitaplıkları ve API'ler ve](../additional-apis/index.md) [.NET Framework ve Out-of-Band Sürümleri'ne](../get-started/the-net-framework-and-out-of-band-releases.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-119">For more information, see [Additional Class Libraries and APIs](../additional-apis/index.md) and [The .NET Framework and Out-of-Band Releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span></span>
> <span data-ttu-id="8b6b2-120">.NET Framework için [NuGet paketlerinin tam listesine](https://www.nuget.org/profiles/dotnetframework) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-120">See a [complete list of NuGet packages](https://www.nuget.org/profiles/dotnetframework) for the .NET Framework.</span></span>

<a name="v48" />

## <a name="introducing-net-framework-48"></a><span data-ttu-id="8b6b2-121">.NET Framework 4.8 Tanıtımı</span><span class="sxs-lookup"><span data-stu-id="8b6b2-121">Introducing .NET Framework 4.8</span></span>

<span data-ttu-id="8b6b2-122">.NET Framework 4.8, .NET Framework 4.x'in önceki sürümlerine, çok kararlı bir ürün olarak kalırken birçok yeni düzeltme ve birkaç yeni özellik ekleyerek temel oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-122">.NET Framework 4.8 builds on previous versions of the .NET Framework 4.x by adding many new fixes and several new features while remaining a very stable product.</span></span>

### <a name="downloading-and-installing-net-framework-48"></a><span data-ttu-id="8b6b2-123">.NET Framework 4.8'i indirme ve yükleme</span><span class="sxs-lookup"><span data-stu-id="8b6b2-123">Downloading and installing .NET Framework 4.8</span></span>

<span data-ttu-id="8b6b2-124">.NET Framework 4.8'i aşağıdaki konumlardan indirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-124">You can download .NET Framework 4.8  from the following locations:</span></span>

- [<span data-ttu-id="8b6b2-125">.NET Framework 4.8 Web Yükleyici</span><span class="sxs-lookup"><span data-stu-id="8b6b2-125">.NET Framework 4.8 Web Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [<span data-ttu-id="8b6b2-126">NET Framework 4.8 Çevrimdışı Yükleyici</span><span class="sxs-lookup"><span data-stu-id="8b6b2-126">NET Framework 4.8 Offline Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="8b6b2-127">.NET Framework 4.8, Windows 10, Windows 8.1, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayan ilgili sunucu platformlarına yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-127">.NET Framework 4.8 can be installed on Windows 10, Windows 8.1, Windows 7 SP1, and the corresponding server platforms starting with Windows Server 2008 R2 SP1.</span></span> <span data-ttu-id="8b6b2-128">.NET Framework 4.8'i web yükleyicisini veya çevrimdışı yükleyiciyi kullanarak yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-128">You can install .NET Framework 4.8 by using either the web installer or the offline installer.</span></span> <span data-ttu-id="8b6b2-129">Çoğu kullanıcı için önerilen yol web yükleyicisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-129">The recommended way for most users is to use the web installer.</span></span>

<span data-ttu-id="8b6b2-130">.NET Framework 4.8'i Visual Studio 2012'de veya daha sonra [.NET Framework 4.8 Geliştirici Paketini](https://go.microsoft.com/fwlink/?LinkId=2085167)yükleyerek hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-130">You can target .NET Framework 4.8 in Visual Studio 2012 or later by installing the [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span></span>

### <a name="whats-new-in-net-framework-48"></a><span data-ttu-id="8b6b2-131">.NET Framework 4.8'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-131">What's new in .NET Framework 4.8</span></span>

<span data-ttu-id="8b6b2-132">.NET Framework 4.8 aşağıdaki alanlarda yeni özellikler sunar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-132">.NET Framework 4.8 introduces new features in the following areas:</span></span>

- [<span data-ttu-id="8b6b2-133">Taban sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-133">Base classes</span></span>](#core48)
- [<span data-ttu-id="8b6b2-134">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-134">Windows Communication Foundation (WCF)</span></span>](#wcf48)
- [<span data-ttu-id="8b6b2-135">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-135">Windows Presentation Foundation (WPF)</span></span>](#wpf48)
- [<span data-ttu-id="8b6b2-136">Ortak dil çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8b6b2-136">Common language runtime</span></span>](#clr48)

<span data-ttu-id="8b6b2-137">Bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sunmasına olanak tanıyan gelişmiş erişilebilirlik, .NET Framework 4.8'in ana odak noktası olmaya devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-137">Improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology, continues to be a major focus of .NET Framework 4.8.</span></span> <span data-ttu-id="8b6b2-138">.NET Framework 4.8'deki erişilebilirlik geliştirmeleri hakkında bilgi için [.NET Framework'deki erişilebilirlikte yeniliklere](whats-new-in-accessibility.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-138">For information on accessibility improvements in .NET Framework 4.8, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core48" />

#### <a name="base-classes"></a><span data-ttu-id="8b6b2-139">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-139">Base classes</span></span>

<span data-ttu-id="8b6b2-140">**Şifreleme üzerinde azaltılmış FIPS etkisi.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-140">**Reduced FIPS impact on Cryptography**.</span></span> <span data-ttu-id="8b6b2-141">.NET Framework'ün önceki sürümlerinde, sistem şifreleme <xref:System.Security.Cryptography.SHA256Managed> kitaplıklarının "FIPS modunda" yapılandırıldığı zaman <xref:System.Security.Cryptography.CryptographicException> atma gibi yönetilen şifreleme sağlayıcısı sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-141">In previous versions of the .NET Framework, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in “FIPS mode”.</span></span> <span data-ttu-id="8b6b2-142">Bu özel durumlar, sistem şifreleme kitaplıklarının aksine, şifreleme sağlayıcı sınıflarının yönetilen sürümleri FIPS (Federal Bilgi İşlem Standartları) 140-2 sertifikasına sahip olmadığından atılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-142">These exceptions are thrown because the managed versions of the cryptographic provider classes, unlike the system cryptographic libraries, have not undergone FIPS (Federal Information Processing Standards) 140-2 certification.</span></span> <span data-ttu-id="8b6b2-143">Çok az geliştiricinin GELIŞTIRME makineleri FIPS modunda olduğundan, özel durumlar genellikle üretim sistemlerine atılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-143">Because few developers have their development machines in FIPS mode, the exceptions are commonly thrown in production systems.</span></span>

<span data-ttu-id="8b6b2-144">.NET Framework 4.8'i hedefleyen uygulamalarda varsayılan olarak, aşağıdaki yönetilen <xref:System.Security.Cryptography.CryptographicException> şifreleme sınıfları artık bu durumda bir şey atmamaktadır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-144">By default in applications that target .NET Framework 4.8, the following managed cryptography classes no longer throw a <xref:System.Security.Cryptography.CryptographicException> in this case:</span></span>

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

<span data-ttu-id="8b6b2-145">Bunun yerine, bu sınıflar şifreleme işlemlerini bir sistem şifreleme kitaplığına yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-145">Instead, these classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="8b6b2-146">Bu değişiklik, geliştirici ortamları ile üretim ortamları arasındaki olası kafa karıştırıcı farkı etkili bir şekilde ortadan kaldırır ve yerel bileşenlerin ve yönetilen bileşenlerin aynı şifreleme ilkesi altında çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-146">This change effectively removes a potentially confusing difference between developer environments and production environments and makes native components and managed components operate under the same cryptographic policy.</span></span> <span data-ttu-id="8b6b2-147">Bu özel durumlara bağlı uygulamalar, AppContext anahtarını `Switch.System.Security.Cryptography.UseLegacyFipsThrow` `true`'da ayarlayarak önceki davranışı geri yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-147">Applications that depend on these exceptions can restore the previous behavior by setting the AppContext switch `Switch.System.Security.Cryptography.UseLegacyFipsThrow` to `true`.</span></span> <span data-ttu-id="8b6b2-148">Daha fazla bilgi için bkz: [Yönetilen şifreleme sınıfları FIPS modunda ŞifrelemeÖzel Durum'u atmayın.](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-148">For more information, see [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span></span>

<span data-ttu-id="8b6b2-149">**ZLib'in güncelleştirilmiş sürümünün kullanımı**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-149">**Use of updated version of ZLib**</span></span>

<span data-ttu-id="8b6b2-150">.NET Framework 4.5 ile başlayarak, clrcompression.dll derlemesi, söndürme algoritması için bir uygulama sağlamak için veri sıkıştırma için yerel bir dış kitaplık olan [ZLib'i](https://www.zlib.net)kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-150">Starting with .NET Framework 4.5, the clrcompression.dll assembly uses [ZLib](https://www.zlib.net), a native external library for data compression, in order to provide an implementation for the deflate algorithm.</span></span> <span data-ttu-id="8b6b2-151">.NET Framework 4.8, clrcompression.dll, birkaç önemli iyileştirme ve düzeltme içeren ZLib Sürüm 1.2.11'i kullanacak şekilde güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-151">The .NET Framework 4.8, clrcompression.dll is updated to use ZLib Version 1.2.11, which includes several key improvements and fixes.</span></span>

<a name="wcf48" />

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="8b6b2-152">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-152">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="8b6b2-153">**Hizmet EkiHizmetSağlık Davranışı**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-153">**Introduction of ServiceHealthBehavior**</span></span>

<span data-ttu-id="8b6b2-154">Sistem durumu uç noktaları, hizmetleri sağlık durumuna göre yönetmek için düzenleme araçları tarafından yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-154">Health endpoints are widely used by orchestration tools to manage services based on their health status.</span></span> <span data-ttu-id="8b6b2-155">Sistem durumu denetimleri, bir hizmetin kullanılabilirliği ve performansı hakkında bildirimleri izlemek ve sağlamak için izleme araçları tarafından da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-155">Health checks can also be used by monitoring tools to track and provide notifications about the availability and performance of a service.</span></span>

<span data-ttu-id="8b6b2-156">**ServiceHealthBehavior** genişleten <xref:System.ServiceModel.Description.IServiceBehavior>bir WCF hizmet davranışıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-156">**ServiceHealthBehavior** is a WCF service behavior that extends <xref:System.ServiceModel.Description.IServiceBehavior>.</span></span>  <span data-ttu-id="8b6b2-157">Koleksiyona <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> eklendiğinde, bir hizmet davranışı aşağıdakileri yapar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-157">When added to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> collection, a service behavior does the following:</span></span>

- <span data-ttu-id="8b6b2-158">HIZMET durumu durumunu HTTP yanıt kodlarıyla döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-158">Returns service health status with HTTP response codes.</span></span> <span data-ttu-id="8b6b2-159">Bir http/GET sistem durumu sondası isteği için http durum kodunu sorgu dizesinde belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-159">You can specify in a query string the HTTP status code for a HTTP/GET health probe request.</span></span>

- <span data-ttu-id="8b6b2-160">Hizmet durumu yla ilgili bilgileri yayımlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-160">Publishes information about service health.</span></span> <span data-ttu-id="8b6b2-161">Hizmet durumu, gaz sayımı ve kapasite gibi hizmete özgü ayrıntılar sorgu dizesi ile `?health` bir HTTP/GET isteği kullanılarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-161">Service-specific details, including service state, throttle counts, and capacity can be displayed by using an HTTP/GET request with the `?health` query string.</span></span> <span data-ttu-id="8b6b2-162">Bir yanlış davranan WCF hizmetini gidermede bu tür bilgilere erişim kolaylığı önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-162">Ease of access to such information is important when troubleshooting a misbehaving WCF service.</span></span>

<span data-ttu-id="8b6b2-163">Sistem durumu bitiş noktasını ortaya çıkarmanın ve WCF hizmet sistem durumu bilgilerini yayımlamanın iki yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-163">There are two ways to expose the health endpoint and publish WCF service health information:</span></span>

- <span data-ttu-id="8b6b2-164">Kod aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-164">Through code.</span></span> <span data-ttu-id="8b6b2-165">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-165">For example:</span></span>

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

- <span data-ttu-id="8b6b2-166">Yapılandırma dosyası kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-166">By using a configuration file.</span></span> <span data-ttu-id="8b6b2-167">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-167">For example:</span></span>

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

<span data-ttu-id="8b6b2-168">`OnServiceFailure`Bir hizmetin sistem durumu, , , , `OnDispatcherFailure` `OnListenerFailure` `OnThrottlePercentExceeded`gibi sorgu parametreleri kullanılarak sorgulanabilir ve her sorgu parametresi için bir HTTP yanıt kodu belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-168">A service's health status can be queried by using query parameters such as `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), and an HTTP response code can be specified for each query parameter.</span></span> <span data-ttu-id="8b6b2-169">Bir sorgu parametresi için HTTP yanıt kodu atlanırsa, varsayılan olarak 503 HTTP yanıt kodu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-169">If the HTTP response code is omitted for a query parameter, a 503 HTTP response code is used by default.</span></span> <span data-ttu-id="8b6b2-170">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-170">For example:</span></span>

- <span data-ttu-id="8b6b2-171">OnServiceFailure:`https://contoso:81/Service1?health&OnServiceFailure=450`</span><span class="sxs-lookup"><span data-stu-id="8b6b2-171">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span></span>

  <span data-ttu-id="8b6b2-172">[ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) daha <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>büyük olduğunda 450 HTTP yanıt durum kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-172">A 450 HTTP response status code is returned when [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>
<span data-ttu-id="8b6b2-173">Sorgu parametreleri ve örnekler:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-173">Query parameters and examples:</span></span>

- <span data-ttu-id="8b6b2-174">OnDispatcherFailure:`https://contoso:81/Service1?health&OnDispatcherFailure=455`</span><span class="sxs-lookup"><span data-stu-id="8b6b2-174">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span></span>

  <span data-ttu-id="8b6b2-175">Kanal gönderenlerden herhangi birinin durumu 'ndan <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>büyük olduğunda 455 HTTP yanıt durum kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-175">A 455 HTTP response status code is returned when the state of any of the channel dispatchers is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8b6b2-176">OnListenerFailure:`https://contoso:81/Service1?health&OnListenerFailure=465`</span><span class="sxs-lookup"><span data-stu-id="8b6b2-176">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span></span>

  <span data-ttu-id="8b6b2-177">Kanal dinleyicilerinden herhangi birinin durumu daha büyük olduğunda 465 HTTP <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>yanıt durum kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-177">A 465 HTTP response status code is returned when the state of any of the channel listeners is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8b6b2-178">OnThrottlePercentExceeded:`https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span><span class="sxs-lookup"><span data-stu-id="8b6b2-178">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span></span>

  <span data-ttu-id="8b6b2-179">Yanıtı tetikleyen {1 – 100} yüzdesini ve HTTP yanıt kodunu {200 – 599} belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-179">Specifies the percentage {1 – 100} that triggers the response and its HTTP response code {200 – 599}.</span></span> <span data-ttu-id="8b6b2-180">Bu örnekte:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-180">In this example:</span></span>

  - <span data-ttu-id="8b6b2-181">Yüzde 95'ten büyükse, 500 HTTP yanıt kodu döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-181">If the percentage is greater than 95, a 500 HTTP response code is returned.</span></span>

  - <span data-ttu-id="8b6b2-182">Yüzde veya 70 ile 95 arasındaysa, 350 döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-182">If the percentage or between 70 and 95, 350 is returned.</span></span>

  - <span data-ttu-id="8b6b2-183">Aksi takdirde, 200 döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-183">Otherwise, 200 is returned.</span></span>

<span data-ttu-id="8b6b2-184">Hizmet durumu durumu, XML gibi `https://contoso:81/Service1?health` bir sorgu dizesi belirterek HTML'de `https://contoso:81/Service1?health&Xml`görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-184">The service health status can be displayed either in HTML by specifying a query string like `https://contoso:81/Service1?health` or in XML by specifying a query string like `https://contoso:81/Service1?health&Xml`.</span></span> <span data-ttu-id="8b6b2-185">Gibi `https://contoso:81/Service1?health&NoContent` bir sorgu dizesi boş bir HTML sayfasını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-185">A query string like `https://contoso:81/Service1?health&NoContent` returns an empty HTML page.</span></span>

<a name="wpf48" />

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8b6b2-186">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-186">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8b6b2-187">**Yüksek DPI geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-187">**High DPI enhancements**</span></span>

<span data-ttu-id="8b6b2-188">.NET Framework 4.8'de WPF, Per-Monitor V2 DPI Bilinirliği ve Karma ModLU DPI ölçeklendirmesi için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-188">In .NET Framework 4.8, WPF adds support for Per-Monitor V2 DPI Awareness and Mixed-Mode DPI scaling.</span></span> <span data-ttu-id="8b6b2-189">Yüksek DPI geliştirme hakkında ek bilgi için [Windows'da Yüksek DPI Masaüstü Uygulama Geliştirme'ye](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-189">See [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) for additional information about high DPI development.</span></span>

<span data-ttu-id="8b6b2-190">.NET Framework 4.8, Karma Mod DPI ölçeklemeişlemini destekleyen platformlarda Yüksek DPI WPF uygulamalarında barındırılan HWND'ler ve Windows Formlar ara çalışması için desteği artırır (Windows 10 Nisan 2018 Güncelleştirmesi'nden başlayarak).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-190">.NET Framework 4.8 improves support for hosted HWNDs and Windows Forms interoperation in High-DPI WPF applications on platforms that support Mixed-Mode DPI scaling (starting with Windows 10 April 2018 Update).</span></span> <span data-ttu-id="8b6b2-191">Barındırılan HWND'ler veya Windows Formları denetimleri [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) ve [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext)çağırarak Karışık Mod DPI ölçekli pencereler olarak oluşturulduğunda, bir Per-Monitor V2 WPF uygulamasında barındırılabilir ve uygun şekilde boyutlandırılır ve ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-191">When hosted HWNDs or Windows Forms controls are created as Mixed-Mode DPI-scaled windows by calling [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) and [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), they can be hosted in a Per-Monitor V2 WPF application and are sized and scaled appropriately.</span></span> <span data-ttu-id="8b6b2-192">Bu tür barındırılan içerik yerel DPI'da işlenmez; bunun yerine, işletim sistemi barındırılan içeriği uygun boyuta ölçeklendiriyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-192">Such hosted content is not rendered at the native DPI; instead, the operating system scales the hosted content to the appropriate size.</span></span> <span data-ttu-id="8b6b2-193">Per-Monitor v2 DPI bilinirlik modu desteği, WPF denetimlerinin yüksek DPI uygulamasında yerel bir pencerede barındırılmasına (örneğin, ebeveynli) izin verir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-193">The support for Per-Monitor v2 DPI awareness mode also allows WPF controls to be hosted (i.e., parented) in a native window in a high-DPI application.</span></span>

<span data-ttu-id="8b6b2-194">Karışık Mod yüksek DPI ölçekleme desteği etkinleştirmek için, aşağıdaki [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarları uygulama yapılandırma dosyası ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-194">To enable support for Mixed-Mode High DPI scaling, you can set the following [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches the application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48" />

#### <a name="common-language-runtime"></a><span data-ttu-id="8b6b2-195">Ortak dil çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="8b6b2-195">Common language runtime</span></span>

<span data-ttu-id="8b6b2-196">.NET Framework 4.8'deki çalışma süresi aşağıdaki değişiklikleri ve iyileştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-196">The runtime in .NET Framework 4.8 includes the following changes and improvements:</span></span>

<span data-ttu-id="8b6b2-197">**JIT derleyicisi için iyileştirmeler**.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-197">**Improvements to the JIT compiler**.</span></span> <span data-ttu-id="8b6b2-198">.NET Framework 4.8'deki Just-in-time (JIT) derleyicisi ,NET Core 2.1'deki JIT derleyicisini temel adatır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-198">The Just-in-time (JIT) compiler in .NET Framework 4.8 is based on the JIT compiler in .NET Core 2.1.</span></span> <span data-ttu-id="8b6b2-199">.NET Core 2.1 JIT derleyicisine yapılan optimizasyonların ve tüm hata düzeltmelerinin çoğu .NET Framework 4.8 JIT derleyicisine dahildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-199">Many of the optimizations and all of the bug fixes made to the .NET Core 2.1 JIT compiler are included in the .NET Framework 4.8 JIT compiler.</span></span>

<span data-ttu-id="8b6b2-200">**NGEN iyileştirmeler**.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-200">**NGEN improvements**.</span></span> <span data-ttu-id="8b6b2-201">Çalışma süresi, NGEN görüntülerinden eşlenen verilerin bellekte yerleşik olmaması için [Yerel Görüntü Üreteci](../tools/ngen-exe-native-image-generator.md) (NGEN) görüntüleri için bellek yönetimini geliştirmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-201">The runtime has improved its memory management for [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) images so that data mapped from NGEN images are not memory-resident.</span></span> <span data-ttu-id="8b6b2-202">Bu, yürütülecek belleği değiştirerek rasgele kod yürütmeye çalışan saldırıların kullanabileceği yüzey alanını azaltır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-202">This reduces the surface area available to attacks that attempt to execute arbitrary code by modifying memory that will be executed.</span></span>

<span data-ttu-id="8b6b2-203">**Tüm derlemeler için antimalware tarama**.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-203">**Antimalware scanning for all assemblies**.</span></span> <span data-ttu-id="8b6b2-204">.NET Framework'ün önceki sürümlerinde, çalışma zamanı, Windows Defender veya üçüncü taraf kötü amaçlı yazılımdan koruma yazılımını kullanarak diskten yüklenen tüm derlemeleri tarar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-204">In previous versions of the .NET Framework, the runtime scans all assemblies loaded from disk using either Windows Defender or third-party antimalware software.</span></span> <span data-ttu-id="8b6b2-205">Ancak, <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> yöntem gibi diğer kaynaklardan yüklenen derlemeler taranır ve algılanmayan kötü amaçlı yazılımlar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-205">However, assemblies loaded from other sources, such as by the <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> method, are not scanned and can potentially contain undetected malware.</span></span> <span data-ttu-id="8b6b2-206">Windows 10'da çalışan .NET Framework 4.8 ile başlayan çalışma zamanı, kötü amaçlı yazılımdan koruma çözümleriyle kötü [amaçlı yazılımdan koruma arabirimini (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal)uygulayan bir taramaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-206">Starting with .NET Framework 4.8 running on Windows 10, the runtime triggers a scan by antimalware solutions that implement the [Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span></span>

<a name="v472" />

## <a name="whats-new-in-net-framework-472"></a><span data-ttu-id="8b6b2-207">.NET Framework 4.7.2'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-207">What's new in .NET Framework 4.7.2</span></span>

<span data-ttu-id="8b6b2-208">.NET Framework 4.7.2 aşağıdaki alanlarda yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-208">.NET Framework 4.7.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="8b6b2-209">Taban sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-209">Base classes</span></span>](#core-472)
- [<span data-ttu-id="8b6b2-210">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-210">ASP.NET</span></span>](#asp-net472)
- [<span data-ttu-id="8b6b2-211">Ağ Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-211">Networking</span></span>](#net472)
- [<span data-ttu-id="8b6b2-212">SQL</span><span class="sxs-lookup"><span data-stu-id="8b6b2-212">SQL</span></span>](#sql472)
- [<span data-ttu-id="8b6b2-213">WPF</span><span class="sxs-lookup"><span data-stu-id="8b6b2-213">WPF</span></span>](#wpf472)
- [<span data-ttu-id="8b6b2-214">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="8b6b2-214">ClickOnce</span></span>](#clickonce)

<span data-ttu-id="8b6b2-215">.NET Framework 4.7.2'de devam eden bir odak noktası, bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sunmasına olanak tanıyan gelişmiş erişilebilirliktir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-215">A continuing focus in .NET Framework 4.7.2 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="8b6b2-216">.NET Framework 4.7.2'deki erişilebilirlik geliştirmeleri hakkında bilgi için [.NET Framework'de erişilebilirlikte yenilikler](whats-new-in-accessibility.md)egörebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-216">For information on accessibility improvements in .NET Framework 4.7.2, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core-472" />

#### <a name="base-classes"></a><span data-ttu-id="8b6b2-217">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-217">Base classes</span></span>

<span data-ttu-id="8b6b2-218">.NET Framework 4.7.2 çok sayıda şifreleme geliştirmesi, ZIP arşivleri için daha iyi dekompresyon desteği ve ek toplama API'leri sunar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-218">.NET Framework 4.7.2 features a large number of cryptographic enhancements, better decompression support for ZIP archives, and additional collection APIs.</span></span>

<span data-ttu-id="8b6b2-219">**RsA yeni aşırı yükleri. Oluştur ve DSA. Oluşturmak**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-219">**New overloads of RSA.Create and DSA.Create**</span></span>

<span data-ttu-id="8b6b2-220">Ve <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> yöntemler, yeni <xref:System.Security.Cryptography.DSA> veya <xref:System.Security.Cryptography.RSA> anahtarı anında alırken anahtar parametreleri sağlamanıza izin sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-220">The <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> methods let you supply key parameters when instantiating a new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> key.</span></span> <span data-ttu-id="8b6b2-221">Aşağıdaki gibi kodu değiştirmenize izin verirler:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-221">They allow you to replace code like the following:</span></span>

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

<span data-ttu-id="8b6b2-222">bu gibi kod ile:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-222">with code like this:</span></span>

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

<span data-ttu-id="8b6b2-223">Ve <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> yöntemler, belirli <xref:System.Security.Cryptography.DSA> bir <xref:System.Security.Cryptography.RSA> anahtar boyutuna sahip yeni veya anahtarlar oluşturmanıza izin sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-223">The <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> methods let you generate new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> keys with a specific key size.</span></span> <span data-ttu-id="8b6b2-224">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-224">For example:</span></span>

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

<span data-ttu-id="8b6b2-225">**Rfc2898DeriveBayt yapıcılar karma algoritma adı kabul**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-225">**Rfc2898DeriveBytes constructors accept a hash algorithm name**</span></span>

<span data-ttu-id="8b6b2-226">Sınıfın, <xref:System.Security.Cryptography.Rfc2898DeriveBytes> anahtarları türeterken kullanmak <xref:System.Security.Cryptography.HashAlgorithmName> üzere Kullanılacak HMAC algoritmasını tanımlayan bir parametreye sahip üç yeni oluşturucusu vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-226">The <xref:System.Security.Cryptography.Rfc2898DeriveBytes> class has three new constructors with a <xref:System.Security.Cryptography.HashAlgorithmName> parameter that identifies the HMAC algorithm to use when deriving keys.</span></span> <span data-ttu-id="8b6b2-227">Bunun yerine SHA-1 kullanarak, geliştiriciler sha-256 gibi sha-2 tabanlı HMAC kullanmanız gerekir, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-227">Instead of using SHA-1, developers should use a SHA-2-based HMAC like SHA-256, as shown in the following example:</span></span>

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

<span data-ttu-id="8b6b2-228">**Geçici anahtarlar için destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-228">**Support for ephemeral keys**</span></span>

<span data-ttu-id="8b6b2-229">PFX alma işlemi, sabit sürücüyü atlayarak özel anahtarları doğrudan bellekten yükleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-229">PFX import can optionally load private keys directly from memory, bypassing the hard drive.</span></span><span data-ttu-id="8b6b2-230">Yeni <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> bayrak bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> oluşturucuda veya <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> yöntemin aşırı yüklerinden birinde belirtildiğinde, özel anahtarlar geçici anahtarlar olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-230"> When the new <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flag is specified in an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor or one of the overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> method, the private keys will be loaded as ephemeral keys.</span></span> <span data-ttu-id="8b6b2-231">Bu, anahtarların diskte görünmesini önler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-231">This prevents the keys from being visible on the disk.</span></span> <span data-ttu-id="8b6b2-232">Ancak:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-232">However:</span></span>

- <span data-ttu-id="8b6b2-233">Anahtarlar diske kalıcı olmadığından, bu bayrakla yüklenen sertifikalar X509Store'a eklemek için iyi adaylar değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-233">Since the keys are not persisted to disk, certificates loaded with this flag are not good candidates to add to an X509Store.</span></span>

- <span data-ttu-id="8b6b2-234">Bu şekilde yüklenen anahtarlar hemen hemen her zaman Windows CNG üzerinden yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-234">Keys loaded in this manner are almost always loaded via Windows CNG.</span></span> <span data-ttu-id="8b6b2-235">Bu nedenle, arayanlar ın sertifika gibi uzantı yöntemlerini arayarak özel anahtara erişmesi [gerekir. GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-235">Therefore, callers must access the private key by calling extension methods, such as [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span></span> <span data-ttu-id="8b6b2-236">Özellik <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-236">The <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not function.</span></span>

- <span data-ttu-id="8b6b2-237">Eski <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> özellik sertifikalarla çalışmadığından, geliştiriciler geçici anahtarlara geçmeden önce zorlu sınamalar gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-237">Since the legacy <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not work with certificates, developers should perform rigorous testing before switching to ephemeral keys.</span></span>

<span data-ttu-id="8b6b2-238">**PKCS#10 sertifika imzalama isteklerinin ve X.509 ortak anahtar sertifikalarının programlı oluşturulması**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-238">**Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates**</span></span>

<span data-ttu-id="8b6b2-239">.NET Framework 4.7.2 ile başlayarak, iş yükleri sertifika isteği oluşturmanın varolan takım oluşturmaya olanak tanıyan sertifika imzalama istekleri (CSR) oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-239">Starting with .NET Framework 4.7.2, workloads can generate certificate signing requests (CSRs), which allows certificate request generation to be staged into existing tooling.</span></span> <span data-ttu-id="8b6b2-240">Bu, test senaryolarında sık sık yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-240">This is frequently useful in test scenarios.</span></span>

<span data-ttu-id="8b6b2-241">Daha fazla bilgi ve kod örnekleri için [,.NET blogunda](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"PKCS#10 sertifika imzalama isteklerinin ve X.509 ortak anahtar sertifikalarının programlı oluşturulması" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-241">For more information and code examples, see "Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="8b6b2-242">**Yeni SignerInfo üyeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-242">**New SignerInfo members**</span></span>

<span data-ttu-id="8b6b2-243">.NET Framework 4.7.2 ile <xref:System.Security.Cryptography.Pkcs.SignerInfo> başlayarak, sınıf imza hakkında daha fazla bilgi ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-243">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.Pkcs.SignerInfo> class exposes more information about the signature.</span></span> <span data-ttu-id="8b6b2-244">İmzalayıcı tarafından kullanılan <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> imza algoritmasını belirlemek için özelliğin değerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-244">You can retrieve the value of the <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> property to determine the signature algorithm used by the signer.</span></span> <span data-ttu-id="8b6b2-245"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType>bu imzalayan için şifreleme imzasının bir kopyasını almak için çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-245"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> can be called to get a copy of the cryptographic signature for this signer.</span></span>

<span data-ttu-id="8b6b2-246">**CryptoStream imha edildikten sonra sarılmış bir akışı açık bırakma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-246">**Leaving a wrapped stream open after CryptoStream is disposed**</span></span>

<span data-ttu-id="8b6b2-247">.NET Framework 4.7.2 ile <xref:System.Security.Cryptography.CryptoStream> başlayarak, sınıf sarılmış <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> akışı kapatmamaya izin veren ek bir oluşturucuya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-247">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.CryptoStream> class has an additional constructor that allows <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> to not close the wrapped stream.</span></span><span data-ttu-id="8b6b2-248">Paketlenmiş akışı <xref:System.Security.Cryptography.CryptoStream> örnek bertaraf edildikten sonra açık bırakmak <xref:System.Security.Cryptography.CryptoStream> için, yeni oluşturucuyu aşağıdaki gibi arayın:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-248"> To leave the wrapped stream open after the <xref:System.Security.Cryptography.CryptoStream> instance is disposed, call the new <xref:System.Security.Cryptography.CryptoStream> constructor as follows:</span></span>

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

<span data-ttu-id="8b6b2-249">**DeflateStream'de dekompresyon değişiklikleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-249">**Decompression changes in DeflateStream**</span></span>

<span data-ttu-id="8b6b2-250">.NET Framework 4.7.2 ile başlayarak, <xref:System.IO.Compression.DeflateStream> sınıfta dekompresyon işlemlerinin uygulanması varsayılan olarak yerel Windows API'lerini kullanacak şekilde değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-250">Starting with .NET Framework 4.7.2, the implementation of decompression operations in the <xref:System.IO.Compression.DeflateStream> class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="8b6b2-251">Genellikle, bu önemli bir performans artışı ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-251">Typically, this results in a substantial performance improvement.</span></span>

<span data-ttu-id="8b6b2-252">.NET Framework 4.7.2'yi hedefleyen uygulamalar için varsayılan olarak Windows API'leri kullanılarak dekompresyon desteği sağlanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-252">Support for decompression by using Windows APIs is enabled by default for applications that target .NET Framework 4.7.2.</span></span> <span data-ttu-id="8b6b2-253">.NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.7.2 altında çalışan uygulamalar, uygulama yapılandırma dosyasına aşağıdaki [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) ekleyerek bu davranışı seçebilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-253">Applications that target earlier versions of .NET Framework but are running under .NET Framework 4.7.2 can opt into this behavior by adding the following [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

<span data-ttu-id="8b6b2-254">**Ek toplama API'leri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-254">**Additional collection APIs**</span></span>

<span data-ttu-id="8b6b2-255">.NET Framework 4.7.2, bu <xref:System.Collections.Generic.SortedSet%601> tür ve <xref:System.Collections.Generic.HashSet%601> türlere bir dizi yeni API ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-255">.NET Framework 4.7.2 adds a number of new APIs to the <xref:System.Collections.Generic.SortedSet%601> and <xref:System.Collections.Generic.HashSet%601> types.</span></span> <span data-ttu-id="8b6b2-256">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-256">These include:</span></span>

- <span data-ttu-id="8b6b2-257">`TryGetValue`diğer toplama türlerinde kullanılan try deseni bu iki türe genişleten yöntemler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-257">`TryGetValue` methods, which extend the try pattern used in other collection types to these two types.</span></span> <span data-ttu-id="8b6b2-258">Yöntemler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-258">The methods are:</span></span>

  - [<span data-ttu-id="8b6b2-259">kamu bool HashSet\<T>. TryGetValue(T equalValue, çıkış T actualValue)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-259">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [<span data-ttu-id="8b6b2-260">kamu bool SortedSet\<T>. TryGetValue(T equalValue, çıkış T actualValue)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-260">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- <span data-ttu-id="8b6b2-261">`Enumerable.To*`bir koleksiyonu bir: <xref:System.Collections.Generic.HashSet%601></span><span class="sxs-lookup"><span data-stu-id="8b6b2-261">`Enumerable.To*` extension methods, which convert a collection to a <xref:System.Collections.Generic.HashSet%601>:</span></span>

  - [<span data-ttu-id="8b6b2-262">kamu statik HashSet\<TSource>\<ToHashSet TSource>\<(Bu Ayrılmaz TSource> kaynak)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-262">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [<span data-ttu-id="8b6b2-263">kamu\<statik HashSet TSource>\<ToHashSet TSource>\<(Bu Ayrılmaz TSource>\<kaynak, IEqualityComparer TSource> comparer)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-263">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)

- <span data-ttu-id="8b6b2-264">Koleksiyonun kapasitesini ayarlamanıza izin veren yeni <xref:System.Collections.Generic.HashSet%601> yapıcılar, önceden boyutu bildiğinizde <xref:System.Collections.Generic.HashSet%601> performans avantajı sağlar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-264">New <xref:System.Collections.Generic.HashSet%601> constructors that let you set the collection's capacity, which yields a performance benefit when you know the size of the <xref:System.Collections.Generic.HashSet%601> in advance:</span></span>

  - <span data-ttu-id="8b6b2-265">[kamu HashSet(int kapasitesi)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8b6b2-265">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span></span>
  - <span data-ttu-id="8b6b2-266">[kamu HashSet(int kapasitesi, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span><span class="sxs-lookup"><span data-stu-id="8b6b2-266">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span></span>

<span data-ttu-id="8b6b2-267">Sınıf, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sözlükten bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> değer <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> almak veya bulunamazsa eklemek ve sözlükte bir değer eklemek veya zaten varsa güncelleştirmek için yeni aşırı yüklemeler ve yöntemler içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-267">The <xref:System.Collections.Concurrent.ConcurrentDictionary%602> class includes new overloads of the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to retrieve a value from the dictionary or to add it if it is not found, and to add a value to the dictionary or to update it if it already exists.</span></span>

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472" />

#### <a name="aspnet"></a><span data-ttu-id="8b6b2-268">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-268">ASP.NET</span></span>

<span data-ttu-id="8b6b2-269">**Web Formlarında bağımlılık enjeksiyonu desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-269">**Support for dependency injection in Web Forms**</span></span>

<span data-ttu-id="8b6b2-270">[Bağımlılık enjeksiyonu (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) nesneleri ve bunların bağımlılıklarını birbirinden ayırarak, yalnızca bağımlılık değiştiği için nesnenin kodunun değiştirilmesine gerek kalmamasını engeller.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-270">[Dependency injection (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) decouples objects and their dependencies so that an object's code no longer needs to be changed just because a dependency has changed.</span></span> <span data-ttu-id="8b6b2-271">.NET Framework 4.7.2'yi hedefleyen ASP.NET uygulamalar geliştirirken şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-271">When developing ASP.NET applications that target .NET Framework 4.7.2, you can:</span></span>

- <span data-ttu-id="8b6b2-272">İşleyici [ve modüllerde,](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)) [Sayfa örneklerinde](xref:System.Web.UI.Page)ve ASP.NET web uygulama projelerinin [kullanıcı denetimlerinde](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ayarlayıcı tabanlı, arayüz tabanlı ve yapıcı tabanlı enjeksiyon kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-272">Use setter-based, interface-based, and constructor-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web application projects.</span></span>

- <span data-ttu-id="8b6b2-273">[Işleyicive modüllerde,](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)) [Sayfa örneklerinde](xref:System.Web.UI.Page)ve ASP.NET web sitesi projelerinin [kullanıcı denetimlerinde](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) ayarlayıcı tabanlı ve arayüz tabanlı enjeksiyon kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-273">Use setter-based and interface-based injection in [handlers and modules](https://docs.microsoft.com/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](https://docs.microsoft.com/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web site projects.</span></span>

- <span data-ttu-id="8b6b2-274">Farklı bağımlılık enjeksiyon çerçevelerini takın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-274">Plug in different dependency injection frameworks.</span></span>

<span data-ttu-id="8b6b2-275">**Aynı site çerezleri için destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-275">**Support for same-site cookies**</span></span>

<span data-ttu-id="8b6b2-276">[SameSite,](https://tools.ietf.org/html/draft-west-first-party-cookies-07) bir tarayıcının site ler arası istekle birlikte çerez göndermesini engeller.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-276">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) prevents a browser from sending a cookie along with a cross-site request.</span></span> <span data-ttu-id="8b6b2-277">.NET Framework 4.7.2 <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> değeri numaralandırma <xref:System.Web.SameSiteMode?displayProperty=nameWithType> üyesi olan bir özellik ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-277">.NET Framework 4.7.2 adds a <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> property whose value is a <xref:System.Web.SameSiteMode?displayProperty=nameWithType> enumeration member.</span></span> <span data-ttu-id="8b6b2-278">Değeri <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> veya <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET ayarlı çerez üstbilgiözözek. `SameSite`</span><span class="sxs-lookup"><span data-stu-id="8b6b2-278">If its value is <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> or <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET adds the `SameSite` attribute to the set-cookie header.</span></span> <span data-ttu-id="8b6b2-279">SameSite desteği nesneler, tanımlama bilgileri <xref:System.Web.HttpCookie> ve <xref:System.Web.Security.FormsAuthentication> <xref:System.Web.SessionState> nesneler için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-279">SameSite support applies to <xref:System.Web.HttpCookie> objects, as well as to <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies.</span></span>

<span data-ttu-id="8b6b2-280">SameSite'yi bir <xref:System.Web.HttpCookie> nesne için aşağıdaki gibi ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-280">You can set SameSite for an <xref:System.Web.HttpCookie> object as follows:</span></span>

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

<span data-ttu-id="8b6b2-281">Ayrıca web.config dosyasını değiştirerek uygulama düzeyinde SameSite çerezleri yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-281">You can also configure SameSite cookies at the application level by modifying the web.config file:</span></span>

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

<span data-ttu-id="8b6b2-282">Web config dosyasını değiştirerek SameSite for <xref:System.Web.Security.FormsAuthentication> ve <xref:System.Web.SessionState> cookies ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-282">You can add SameSite for <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies by modifying the web config file:</span></span>

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472" />

#### <a name="networking"></a><span data-ttu-id="8b6b2-283">Ağ Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-283">Networking</span></span>

<span data-ttu-id="8b6b2-284">**HttpClientHandler özelliklerinin uygulanması**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-284">**Implementation of HttpClientHandler properties**</span></span>

<span data-ttu-id="8b6b2-285">.NET Framework 4.7.1 <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> sınıfa sekiz özellik ekledi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-285">.NET Framework 4.7.1 added eight properties to the <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8b6b2-286">Ancak, iki <xref:System.PlatformNotSupportedException>attı .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-286">However, two threw a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="8b6b2-287">.NET Framework 4.7.2 şimdi bu özellikler için bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-287">.NET Framework 4.7.2 now provides an implementation for these properties.</span></span> <span data-ttu-id="8b6b2-288">Özellikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-288">The properties are:</span></span>

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472" />

#### <a name="sqlclient"></a><span data-ttu-id="8b6b2-289">SQLClient</span><span class="sxs-lookup"><span data-stu-id="8b6b2-289">SQLClient</span></span>

<span data-ttu-id="8b6b2-290">**Azure Active Directory Evrensel Kimlik Doğrulaması ve Çok Faktörlü Kimlik Doğrulaması desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-290">**Support for Azure Active Directory Universal Authentication and Multi-Factor authentication**</span></span>

<span data-ttu-id="8b6b2-291">Artan uyumluluk ve güvenlik talepleri, birçok müşterinin çok faktörlü kimlik doğrulaması (MFA) kullanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-291">Growing compliance and security demands require that many customers use multi-factor authentication (MFA).</span></span> <span data-ttu-id="8b6b2-292">Buna ek olarak, geçerli en iyi uygulamalar doğrudan bağlantı dizeleri kullanıcı parolaları da dahil olmak üzere cesaretini.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-292">In addition, current best practices discourage including user passwords directly in connection strings.</span></span> <span data-ttu-id="8b6b2-293">Bu değişiklikleri desteklemek için .NET Framework 4.7.2, MFA ve [Azure AD Kimlik Doğrulaması'nı](/azure/sql-database/sql-database-aad-authentication-configure)desteklemek için varolan "Kimlik Doğrulama" anahtar sözcüğü için yeni bir değer olan "Active Directory Interactive" ekleyerek [SQLClient bağlantı dizelerini](xref:System.Data.SqlClient.SqlConnection.ConnectionString) genişletir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-293">To support these changes, .NET Framework 4.7.2 extends [SQLClient connection strings](xref:System.Data.SqlClient.SqlConnection.ConnectionString) by adding a new value, "Active Directory Interactive", for the existing "Authentication" keyword to support MFA and [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure).</span></span> <span data-ttu-id="8b6b2-294">Yeni etkileşimli yöntem, yerel ve federe Azure AD kullanıcılarının yanı sıra Azure AD konuk kullanıcılarını da destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-294">The new interactive method supports native and federated Azure AD users as well as Azure AD guest users.</span></span> <span data-ttu-id="8b6b2-295">Bu yöntem kullanıldığında, Azure AD tarafından dayatılan MFA kimlik doğrulaması SQL veritabanları için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-295">When this method is used, the MFA authentication imposed by Azure AD is supported for SQL databases.</span></span> <span data-ttu-id="8b6b2-296">Buna ek olarak, kimlik doğrulama işlemi güvenlik en iyi uygulamalarına uymak için bir kullanıcı parolası ister.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-296">In addition, the authentication process requests a user password to adhere to security best practices.</span></span>

<span data-ttu-id="8b6b2-297">.NET Framework'ün önceki sürümlerinde, SQL bağlantısı <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> yalnızca seçenekleri ve seçenekleri desteklenebildi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-297">In previous versions of the .NET Framework, SQL connectivity supported only the <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> and <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="8b6b2-298">Bunların her ikisi de MFA'yı desteklemeyen etkileşimli olmayan [ADAL protokolünün](/azure/active-directory/develop/active-directory-authentication-libraries)bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-298">Both of these are part of the non-interactive [ADAL protocol](/azure/active-directory/develop/active-directory-authentication-libraries), which does not support MFA.</span></span> <span data-ttu-id="8b6b2-299">Yeni <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> seçenekle, SQL bağlantısı MFA'nın yanı sıra kullanıcıların bağlantı dizesinde parolaları kalıcı hale getirilmeden etkileşimli olarak kullanıcı parolalarını girmelerine olanak tanıyan mevcut kimlik doğrulama yöntemlerini (parola ve tümleşik kimlik doğrulama) destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-299">With the new <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> option, SQL connectivity supports MFA as well as existing authentication methods (password and integrated authentication), which allows users to enter user passwords interactively without persisting passwords in the connection string.</span></span>

<span data-ttu-id="8b6b2-300">Daha fazla bilgi ve örnek için [,.NET blogundaki](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)"SQL -- Azure AD Evrensel ve Çok Faktörlü Kimlik Doğrulama Desteği" başlıklı bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-300">For more information and an example, see "SQL -- Azure AD Universal and Multi-factor Authentication Support" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="8b6b2-301">**Her Zaman Şifrelenmiş sürüm 2 desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-301">**Support for Always Encrypted version 2**</span></span>

<span data-ttu-id="8b6b2-302">NET Framework 4.7.2, her zaman şifrelenmiş enklav tabanlı destekler ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-302">NET Framework 4.7.2 adds supports for enclave-based Always Encrypted.</span></span> <span data-ttu-id="8b6b2-303">Always Encrypted'ın özgün sürümü, şifreleme anahtarlarının istemciden asla ayrılmadığı istemci tarafı şifreleme teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-303">The original version of Always Encrypted is a client-side encryption technology in which encryption keys never leave the client.</span></span> <span data-ttu-id="8b6b2-304">Enklav tabanlı Her Zaman Şifrelenmiş'te istemci, şifreleme anahtarlarını isteğe bağlı olarak, SQL Server'ın bir parçası olarak kabul edilebilen ancak SQL Server kodunun kurcalayamayacağı güvenli bir işlem varlığı olan güvenli bir enklava gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-304">In enclave-based Always Encrypted, the client can optionally send the encryption keys to a secure enclave, which is a secure computational entity that can be considered part of SQL Server but that SQL Server code cannot tamper with.</span></span> <span data-ttu-id="8b6b2-305">Her Zaman Şifrelenmiş yerleşim bölgesini desteklemek için,.NET Framework 4.7.2 <xref:System.Data.SqlClient> ad alanına aşağıdaki türleri ve üyeleri ekler:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-305">To support enclave-based Always Encrypted, .NET Framework 4.7.2 adds the following types and members to the <xref:System.Data.SqlClient> namespace:</span></span>

- <span data-ttu-id="8b6b2-306"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, enklav tabanlı Her Zaman Şifreli uri belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-306"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, which specifies the Uri for enclave-based Always Encrypted.</span></span>

- <span data-ttu-id="8b6b2-307"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, tüm enklav sağlayıcılarıtüretildiği soyut bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-307"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, which is an abstract class from which all enclave providers are derived.</span></span>

- <span data-ttu-id="8b6b2-308"><xref:System.Data.SqlClient.SqlEnclaveSession>, hangi belirli bir enklav oturumu için devlet kapsüller.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-308"><xref:System.Data.SqlClient.SqlEnclaveSession>, which encapsulates the state for a given enclave session.</span></span>

- <span data-ttu-id="8b6b2-309"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, belirli bir Attestation Protokolü yürütmek için gerekli bilgileri almak için SQL Server tarafından kullanılan attestation parametrelerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-309"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, which provides the attestation parameters used by SQL Server to get information required to execute a particular Attestation Protocol.</span></span>

<span data-ttu-id="8b6b2-310">Uygulama yapılandırma dosyası daha sonra enklav <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> sağlayıcısı için işlevselliği sağlayan soyut sınıfın somut bir uygulama belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-310">The application configuration file then specifies a concrete implementation of the abstract <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> class that provides the functionality for the enclave provider.</span></span> <span data-ttu-id="8b6b2-311">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-311">For example:</span></span>

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

<span data-ttu-id="8b6b2-312">Her Zaman Şifrelenmiş enklav tabanlı temel akışı:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-312">The basic flow of enclave-based Always Encrypted is:</span></span>

1. <span data-ttu-id="8b6b2-313">Kullanıcı, enklav tabanlı Her Zaman Şifrelenmiş'i destekleyen SQL Server'a AlwaysEncrypted bağlantısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-313">The user creates an AlwaysEncrypted connection to SQL Server that supported enclave-based Always Encrypted.</span></span> <span data-ttu-id="8b6b2-314">Sürücü, doğru yerleşim bölgesine bağlandığından emin olmak için attestation hizmetiyle bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-314">The driver contacts the attestation service to ensure that it is connecting to right enclave.</span></span>

1. <span data-ttu-id="8b6b2-315">Enklav kanıtlandıktan sonra, sürücü SQL Server'da barındırılan güvenli enklavile güvenli bir kanal kurar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-315">Once the enclave has been attested, the driver establishes a secure channel with the secure enclave hosted on SQL Server.</span></span>

1. <span data-ttu-id="8b6b2-316">Sürücü, istemci tarafından yetkilendirilen şifreleme anahtarlarını SQL bağlantısı süresince güvenli enklavla paylaşır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-316">The driver shares encryption keys authorized by the client with the secure enclave for the duration of the SQL connection.</span></span>

<a name="wpf472" />

#### <a name="windows-presentation-foundation"></a><span data-ttu-id="8b6b2-317">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="8b6b2-317">Windows Presentation Foundation</span></span>

<span data-ttu-id="8b6b2-318">**Kaynağa Göre KaynakDictionaries bulma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-318">**Finding ResourceDictionaries by Source**</span></span>

<span data-ttu-id="8b6b2-319">.NET Framework 4.7.2 ile başlayarak, <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> bir tanı asistanı belirli bir kaynak Uri oluşturulan yerini bulabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-319">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> that have been created from a given source Uri.</span></span><span data-ttu-id="8b6b2-320">(Bu özellik üretim uygulamaları tarafından değil, tanı asistanları tarafından kullanılmak üzeredir.) Visual Studio'nun "Edit-and-Continue" tesisi gibi bir tanı asistanı, kullanıcının, değişikliklerin çalışan uygulamaya uygulanması amacıyla bir Kaynak Sözlüğü'nü yönetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-320"> (This feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility lets its user edit a ResourceDictionary with the intent that the changes be applied to the running application.</span></span> <span data-ttu-id="8b6b2-321">Bunu başarmanın bir adımı, çalışan uygulamanın düzenlenen sözlükten oluşturduğu tüm KaynakDictions'ları bulmaktır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-321">One step in achieving this is finding all the ResourceDictionaries that the running application has created from the dictionary that’s being edited.</span></span> <span data-ttu-id="8b6b2-322">Örneğin, bir uygulama, içeriği belirli bir kaynak URI'den kopyalanan bir Kaynak Sözlüğü'nü bildirebilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-322">For example, an application can declare a ResourceDictionary whose content is copied from a given source URI:</span></span>

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

<span data-ttu-id="8b6b2-323">*MyRD.xaml'da* orijinal biçimlendirmeyi ayarlayan bir tanı asistanı, sözlüğü bulmak için yeni özelliği kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-323">A diagnostic assistant that edits the original markup in *MyRD.xaml* can use the new feature to locate the dictionary.</span></span><span data-ttu-id="8b6b2-324">Özellik yeni bir statik yöntem ile <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-324"> The feature is implemented by a new static method, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8b6b2-325">Tanıasistanı, aşağıdaki kodda gösterildiği gibi, özgün biçimlendirmeyi tanımlayan mutlak bir Uri kullanarak yeni yöntemi çağırır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-325">The diagnostic assistant calls the new method using an absolute Uri that identifies the original markup, as illustrated by the following code:</span></span>

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

<span data-ttu-id="8b6b2-326">Yöntem etkinleştirilmedikçe ve <xref:System.Windows.Diagnostics.VisualDiagnostics> [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ortam değişkeni ayarlı olmadıkça boş bir sayısal akçe döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-326">The method returns an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="8b6b2-327">**Kaynak BulmaSözlük sahipleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-327">**Finding ResourceDictionary owners**</span></span>

<span data-ttu-id="8b6b2-328">.NET Framework 4.7.2 ile başlayarak, bir tanı <xref:Windows.UI.Xaml.ResourceDictionary>asistanı belirli bir .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-328">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the owners of a given <xref:Windows.UI.Xaml.ResourceDictionary>.</span></span><span data-ttu-id="8b6b2-329">(Bu özellik üretim uygulamaları tarafından değil, tanı asistanları tarafından kullanılmak üzeredir.) Bir <xref:Windows.UI.Xaml.ResourceDictionary>değişiklik yapıldığında , WPF değişiklikten etkilenebilecek tüm [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvurularını otomatik olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-329"> (The feature is for use by diagnostic assistants and not by production applications.) Whenever a change is made to a <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatically finds all [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references that might be affected by the change.</span></span>

<span data-ttu-id="8b6b2-330">Visual Studio'nun "Edit-and-Continue" tesisi gibi bir tanı [asistanı, Statik Kaynak](../wpf/advanced/staticresource-markup-extension.md) başvurularını işlemek için bunu genişletmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-330">A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to extend this to handle [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="8b6b2-331">Bu işlemin ilk adımı sözlük sahiplerini bulmaktır; diğer bir deyişle, özelliği sözlüğe atıfta bulunan `Resources` tüm nesneleri bulmak için <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> (doğrudan veya dolaylı olarak özellik üzerinden).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-331">The first step in this process is to find the owners of the dictionary; that is, to find all the objects whose `Resources` property refers to the dictionary (either directly, or indirectly via the <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="8b6b2-332"><xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> Sınıfa uygulanan üç yeni statik yöntem, bir özelliği olan `Resources` temel türlerin her biri için bir, bu adımı destekler:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-332">Three new static methods implemented on the <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> class, one for each of the base types that has a `Resources` property, support this step:</span></span>

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

<span data-ttu-id="8b6b2-333">Bu yöntemler etkinleştirilmedikçe ve <xref:System.Windows.Diagnostics.VisualDiagnostics> ortam değişkeni [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ayarlınca boş bir sayısal adedi döndürün.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-333">These methods return an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="8b6b2-334">**StaticResource başvurularını bulma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-334">**Finding StaticResource references**</span></span>

<span data-ttu-id="8b6b2-335">Bir tanılama yardımcısı artık [statik](../wpf/advanced/staticresource-markup-extension.md) kaynak başvurusu çözüldüğünde bir bildirim alabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-335">A diagnostic assistant can now receive a notification whenever a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference is resolved.</span></span><span data-ttu-id="8b6b2-336">(Özellik, üretim uygulamaları tarafından değil, tanı asistanları tarafından kullanılmak üzeredir.) Visual Studio'nun "Edit-and-Continue" tesisi gibi bir <xref:Windows.UI.Xaml.ResourceDictionary> tanı asistanı, bir kaynağın değeri değiştiğinde tüm kullanımlarını güncelleştirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-336"> (The feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio’s “Edit-and-Continue” facility may want to update all uses of a resource when its value in a <xref:Windows.UI.Xaml.ResourceDictionary> changes.</span></span> <span data-ttu-id="8b6b2-337">WPF bunu [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) başvuruları için otomatik olarak yapar, ancak [bunu statik](../wpf/advanced/staticresource-markup-extension.md) kaynak başvuruları için kasıtlı olarak yapmaz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-337">WPF does this automatically for [DynamicResource](../wpf/advanced/dynamicresource-markup-extension.md) references, but it intentionally does not do so for [StaticResource](../wpf/advanced/staticresource-markup-extension.md) references.</span></span> <span data-ttu-id="8b6b2-338">.NET Framework 4.7.2 ile başlayarak, tanılama asistanı statik kaynağın bu kullanımlarını bulmak için bu bildirimleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-338">Starting with .NET Framework 4.7.2, the diagnostic assistant can use these notifications to locate those uses of the static resource.</span></span>

<span data-ttu-id="8b6b2-339">Bildirim yeni <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> olay tarafından uygulanır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-339">The notification is implemented by the new <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> event:</span></span>

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

<span data-ttu-id="8b6b2-340">Bu olay, çalışma zamanı statik [kaynak](../wpf/advanced/staticresource-markup-extension.md) başvurusu çözdüğünde yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-340">This event is raised whenever the runtime resolves a [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference.</span></span><span data-ttu-id="8b6b2-341">Bağımsız <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> değişkenler çözünürlüğü açıklar ve Statik [Kaynak](../wpf/advanced/staticresource-markup-extension.md) başvuruyu <xref:Windows.UI.Xaml.ResourceDictionary> ve çözünürlük için kullanılan ve anahtar da barındıran nesneyi ve özelliği gösterir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-341"> The <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> arguments describe the resolution, and indicate the object and property that host the [StaticResource](../wpf/advanced/staticresource-markup-extension.md) reference and the <xref:Windows.UI.Xaml.ResourceDictionary> and key used for the resolution:</span></span>

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

<span data-ttu-id="8b6b2-342">Olay etkinleştirilmedikçe ve `add` ortam <xref:System.Windows.Diagnostics.VisualDiagnostics> değişkeni [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A)  ayarlanmadıkça olay yükseltilmez (ve erişime giren yoksayılır).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-342">The event is not raised (and its `add` accessor is ignored) unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

#### <a name="clickonce"></a><span data-ttu-id="8b6b2-343">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="8b6b2-343">ClickOnce</span></span>

<span data-ttu-id="8b6b2-344">Windows Forms, Windows Presentation Foundation (WPF) ve Office için Visual Studio Tools (VSTO) için HDPI'ye duyarlı uygulamalar ClickOnce kullanılarak dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-344">HDPI-aware applications for Windows Forms, Windows Presentation Foundation (WPF), and Visual Studio Tools for Office (VSTO) can all be deployed by using ClickOnce.</span></span> <span data-ttu-id="8b6b2-345">Uygulama bildiriminde aşağıdaki giriş bulunursa, dağıtım .NET Framework 4.7.2 altında başarılı olur:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-345">If the following entry is found in the application manifest, deployment will succeed under .NET Framework 4.7.2:</span></span>

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

<span data-ttu-id="8b6b2-346">Windows Forms uygulaması için, uygulama bildirimi yerine uygulama yapılandırma dosyasında DPI bilinirliği ayarlamanın önceki geçici çözümünün ClickOnce dağıtımının başarılı olması için artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-346">For Windows Forms application, the previous workaround of setting DPI awareness in the application configuration file rather than the application manifest is no longer necessary for ClickOnce deployment to succeed.</span></span>

<a name="v471" />

## <a name="whats-new-in-net-framework-471"></a><span data-ttu-id="8b6b2-347">.NET Framework 4.7.1'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-347">What's new in .NET Framework 4.7.1</span></span>

<span data-ttu-id="8b6b2-348">.NET Framework 4.7.1 aşağıdaki alanlarda yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-348">.NET Framework 4.7.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="8b6b2-349">Taban sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-349">Base classes</span></span>](#core471)
- [<span data-ttu-id="8b6b2-350">Ortak dil çalışma zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-350">Common language runtime (CLR)</span></span>](#clr)
- [<span data-ttu-id="8b6b2-351">Ağ Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-351">Networking</span></span>](#net471)
- [<span data-ttu-id="8b6b2-352">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-352">ASP.NET</span></span>](#asp-net471)

<span data-ttu-id="8b6b2-353">Buna ek olarak, .NET Framework 4.7.1'deki önemli bir odak noktası, bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sağlamasına olanak tanıyan gelişmiş erişilebilirliktir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-353">In addition, a major focus in .NET Framework 4.7.1 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="8b6b2-354">.NET Framework 4.7.1'deki erişilebilirlik geliştirmeleri hakkında bilgi için [.NET Framework'de erişilebilirlikte yenilikler](whats-new-in-accessibility.md)egörebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-354">For information on accessibility improvements in .NET Framework 4.7.1, see [What's new in accessibility in the .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core471" />

#### <a name="base-classes"></a><span data-ttu-id="8b6b2-355">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-355">Base classes</span></span>

<span data-ttu-id="8b6b2-356">**.NET Standard 2.0 desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-356">**Support for .NET Standard 2.0**</span></span>

<span data-ttu-id="8b6b2-357">[.NET Standard,](../../standard/net-standard.md) standardın bu sürümünü destekleyen her .NET uygulamasında bulunması gereken bir API kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-357">[.NET Standard](../../standard/net-standard.md) defines a set of APIs that must be available on each .NET implementation that supports that version of the standard.</span></span> <span data-ttu-id="8b6b2-358">.NET Framework 4.7.1 .NET Standard 2.0'ı tam olarak destekler ve .NET Standart 2.0'da tanımlanan ve .NET Framework 4.6.1, 4.6.2 ve 4.7'den eksik olan [yaklaşık 200 API](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-358">.NET Framework 4.7.1 fully supports .NET Standard 2.0 and adds [about 200 APIs](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) that are defined in .NET Standard 2.0 and are missing from .NET Framework 4.6.1, 4.6.2, and 4.7.</span></span> <span data-ttu-id="8b6b2-359">(.NET Framework'ün bu sürümlerinin .NET Standard 2.0'ı yalnızca hedef sistemde ek .NET Standart destek dosyaları da dağıtılırsa desteklediğini unutmayın.) Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "BCL - .NET Standart 2.0 Desteği" başlıklı yazıya bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-359">(Note that these versions of the .NET Framework support .NET Standard 2.0 only if additional .NET Standard support files are also deployed on the target system.) For more information, see "BCL - .NET Standard 2.0 Support" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="8b6b2-360">**Yapılandırma oluşturucuları için destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-360">**Support for configuration builders**</span></span>

<span data-ttu-id="8b6b2-361">Yapılandırma oluşturucuları, geliştiricilerin çalışma zamanında uygulamalar için dinamik olarak yapılandırma ayarları enjekte etmesine ve oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-361">Configuration builders allow developers to inject and build configuration settings for applications dynamically at run time.</span></span> <span data-ttu-id="8b6b2-362">Özel yapılandırma oluşturucuları, yapılandırma bölümündeki varolan verileri değiştirmek veya tamamen sıfırdan bir yapılandırma bölümü oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-362">Custom configuration builders can be used to modify existing data in a configuration section or to build a configuration section entirely from scratch.</span></span> <span data-ttu-id="8b6b2-363">Yapılandırma oluşturucuları olmadan,.config dosyaları statiktir ve ayarları uygulama başlatılmadan bir süre önce tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-363">Without configuration builders, .config files are static, and their settings are defined some time before an application is launched.</span></span>

<span data-ttu-id="8b6b2-364">Özel bir yapılandırma oluşturucu oluşturmak için, soyut <xref:System.Configuration.ConfigurationBuilder> sınıftan oluşturucu türetmek ve onun <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> ve <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>geçersiz kılmak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-364">To create a custom configuration builder, you derive your builder from the abstract <xref:System.Configuration.ConfigurationBuilder> class and override its <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> and <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8b6b2-365">Ayrıca .config dosyanızda oluşturucularınızı tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-365">You also define your builders in your .config file.</span></span> <span data-ttu-id="8b6b2-366">Daha fazla bilgi için [.NET Framework 4.7.1 ASP.NET ve Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisindeki "Yapılandırma Oluşturucuları" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-366">For more information, see the "Configuration Builders" section in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="8b6b2-367">**Çalışma zamanı özellik algılama**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-367">**Run-time feature detection**</span></span>

<span data-ttu-id="8b6b2-368">Sınıf, <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> önceden tanımlanmış bir özelliğin derleme zamanında veya çalışma zamanında belirli bir .NET uygulamasında desteklenip desteklenmediğini belirlemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-368">The <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> class provides a mechanism for determine whether a predefined feature is supported on a given .NET implementation at compile time or run time.</span></span> <span data-ttu-id="8b6b2-369">Derleme zamanında, bir derleyici özelliğin desteklenip desteklenmediğini belirlemek için belirli bir alanın var olup olmadığını denetleyebilir; eğer öyleyse, bu özellik yararlanır kod yatabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-369">At compile time, a compiler can check whether a specified field exists to determine whether the feature is supported; if so, it can emit code that takes advantage of that feature.</span></span> <span data-ttu-id="8b6b2-370">Çalışma zamanında, bir uygulama <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> çalışma zamanında kod yaymadan önce yöntemi çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-370">At run time, an application can call the <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> method before emitting code at runtime.</span></span> <span data-ttu-id="8b6b2-371">Daha fazla bilgi için çalışma [zamanı tarafından desteklenen özellikleri açıklamak için yardımcı ekle yöntemine](https://github.com/dotnet/corefx/issues/17116)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-371">For more information, see [Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116).</span></span>

<span data-ttu-id="8b6b2-372">**Değer tuple türleri serileştirilebilir**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-372">**Value tuple types are serializable**</span></span>

<span data-ttu-id="8b6b2-373">.NET Framework 4.7.1 <xref:System.ValueTuple?displayProperty=nameWithType> ile başlayarak ve ilişkili genel türleri [serileştirilebilir](xref:System.SerializableAttribute)olarak işaretlenir, bu da ikili serileştirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-373">Starting with .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> and its associated generic types are marked as [Serializable](xref:System.SerializableAttribute), which allows binary serialization.</span></span> <span data-ttu-id="8b6b2-374">Bu, tuple türlerini daha <xref:System.Tuple%603> kolay <xref:System.Tuple%604>değer vermek gibi ve , geçiş yapan Tuple türlerini kolaylaştırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-374">This should make migrating Tuple types, such as <xref:System.Tuple%603> and <xref:System.Tuple%604>, to value tuple types easier.</span></span> <span data-ttu-id="8b6b2-375">Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "Derleyici -- ValueTuple Serializable"a bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-375">For more information, see "Compiler -- ValueTuple is Serializable" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="8b6b2-376">**Salt okunur başvurular için destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-376">**Support for read-only references**</span></span>

<span data-ttu-id="8b6b2-377">.NET Framework 4.7.1 <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-377">.NET Framework 4.7.1 adds the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8b6b2-378">Bu öznitelik, yalnızca okunan ref return türleri veya parametreleri olan üyeleri işaretlemek için dil derleyicileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-378">This attribute is used by language compilers to mark members that have read-only ref return types or parameters.</span></span> <span data-ttu-id="8b6b2-379">Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisinde "Derleyici -- ReadOnlyReferences desteği" başlıklı yazıya bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-379">For more information, see "Compiler -- Support for ReadOnlyReferences" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span> <span data-ttu-id="8b6b2-380">Ref iade değerleri hakkında bilgi için ref [iade değerleri ve ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) ve Ref dönüş değerleri [(Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-380">For information on ref return values, see [Ref return values and ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) and [Ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span></span>

<a name="clr" />

#### <a name="common-language-runtime-clr"></a><span data-ttu-id="8b6b2-381">Ortak dil çalışma zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-381">Common language runtime (CLR)</span></span>

<span data-ttu-id="8b6b2-382">**Çöp toplama performans iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-382">**Garbage collection performance improvements**</span></span>

<span data-ttu-id="8b6b2-383">.NET Framework 4.7.1'deki çöp toplama (GC) değişiklikleri, özellikle büyük nesne yığını (LOH) ayırmaları için genel performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-383">Changes to garbage collection (GC) in .NET Framework 4.7.1 improve overall performance, especially for large object heap (LOH) allocations.</span></span> <span data-ttu-id="8b6b2-384">.NET Framework 4.7.1'de, küçük nesne yığını (SOH) ve LOH ayırmaları için ayrı kilitler kullanılır ve bu da arka plan GC'nin SOH'u süpürmesinde LOH ayırmalarının gerçekleşmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-384">In .NET Framework 4.7.1, separate locks are used for small object heap (SOH) and LOH allocations, which allows LOH allocations to occur when background GC is sweeping the SOH.</span></span> <span data-ttu-id="8b6b2-385">Sonuç olarak, çok sayıda LOH ayırması yapan uygulamalarda ayırma kilidi çekişmesinde bir azalma ve geliştirilmiş performans görünmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-385">As a result, applications that make a large number of LOH allocations should see a reduction in allocation lock contention and improved performance.</span></span> <span data-ttu-id="8b6b2-386">Daha fazla bilgi için [.NET Framework 4.7.1 Runtime ve Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog gönderisindeki "Çalışma Zamanı -- GC Performans Geliştirmeleri" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-386">For more information, see the "Runtime -- GC Performance Improvements" section in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<a name="net471"/>

#### <a name="networking"></a><span data-ttu-id="8b6b2-387">Ağ Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-387">Networking</span></span>

<span data-ttu-id="8b6b2-388">**Message.HashAlgorithm için SHA-2 desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-388">**SHA-2 support for Message.HashAlgorithm**</span></span>

<span data-ttu-id="8b6b2-389">.NET Framework 4.7 ve önceki <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> sürümlerde, <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> özellik <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> yalnızca ve yalnızca değerleri desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-389">In .NET Framework 4.7 and earlier versions, the <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> property supported values of <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> and <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> only.</span></span> <span data-ttu-id="8b6b2-390">.NET Framework 4.7.1 <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType> <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>ile başlayarak ve aynı zamanda <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-390">Starting with .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, and <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> are also supported.</span></span> <span data-ttu-id="8b6b2-391">Bu değerin <xref:System.Messaging.Message> gerçekten kullanılıp kullanılmadığı MSMQ'ya bağlıdır, çünkü örneğin kendisi karma yapmaz, ancak değerleri yalnızca MSMQ'ya aktarAbilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-391">Whether this value is actually used depends on MSMQ, since the <xref:System.Messaging.Message> instance itself does no hashing but simply passes on values to MSMQ.</span></span> <span data-ttu-id="8b6b2-392">Daha fazla bilgi için [,.NET Framework 4.7.1 ASP.NET ve Configuration özellikleri](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisindeki "Message.HashAlgorithm için SHA-2 desteği" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-392">For more information, see the "SHA-2 support for Message.HashAlgorithm" section in the [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<a name="asp-net471" />

#### <a name="aspnet"></a><span data-ttu-id="8b6b2-393">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-393">ASP.NET</span></span>

<span data-ttu-id="8b6b2-394">**ASP.NET uygulamalarında yürütme adımları**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-394">**Execution steps in ASP.NET applications**</span></span>

<span data-ttu-id="8b6b2-395">ASP.NET, 23 olay içeren önceden tanımlanmış bir ardışık ardışık işlemde istekleri işler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-395">ASP.NET processes requests in a predefined pipeline that includes 23 events.</span></span> <span data-ttu-id="8b6b2-396">ASP.NET, her olay işleyicisi bir yürütme adımı olarak yürütür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-396">ASP.NET executes each event handler as an execution step.</span></span> <span data-ttu-id="8b6b2-397">.NET Framework 4.7'ye kadar olan ASP.NET sürümlerinde, ASP.NET, yerel ve yönetilen iş parçacıkları arasında geçiş nedeniyle yürütme bağlamını akıtamaz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-397">In versions of ASP.NET up to .NET Framework 4.7, ASP.NET can't flow the execution context due to switching between native and managed threads.</span></span> <span data-ttu-id="8b6b2-398">Bunun yerine, ASP.NET seçici <xref:System.Web.HttpContext>olarak yalnızca .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-398">Instead, ASP.NET selectively flows only the <xref:System.Web.HttpContext>.</span></span> <span data-ttu-id="8b6b2-399">.NET Framework 4.7.1 <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> ile başlayan yöntem, modüllerin ortam verilerini geri yüklemesine de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-399">Starting with .NET Framework 4.7.1, the <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> method also allows modules to restore ambient data.</span></span> <span data-ttu-id="8b6b2-400">Bu özellik, örneğin uygulamanın yürütme akışını önemseyen izleme, profil oluşturma, tanılama veya işlemlerle ilgili kitaplıkları hedeflemeye yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-400">This feature is targeted at libraries concerned with tracing, profiling, diagnostics, or transactions, for example, that care about the execution flow of the application.</span></span> <span data-ttu-id="8b6b2-401">Daha fazla bilgi için [.NET Framework 4.7.1 ASP.NET ve Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinde yer alan "ASP.NET Yürütme Adımı Özelliği"ne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-401">For more information, see the "ASP.NET Execution Step Feature" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="8b6b2-402">**ASP.NET HttpCookie ayrışma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-402">**ASP.NET HttpCookie parsing**</span></span>

<span data-ttu-id="8b6b2-403">.NET Framework 4.7.1, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>bir dizeden bir <xref:System.Web.HttpCookie> nesne oluşturmak ve son kullanma tarihi ve yol gibi çerez değerlerini doğru bir şekilde atamak için standartlaştırılmış bir yol sağlayan yeni bir yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-403">.NET Framework 4.7.1 includes a new method, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, that provides a standardized way to create an <xref:System.Web.HttpCookie> object from a string and accurately assign cookie values such as expiration date and path.</span></span> <span data-ttu-id="8b6b2-404">Daha fazla bilgi için [.NET Framework 4.7.1 ASP.NET ve Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog gönderisinde "ASP.NET HttpCookie ayrıştırma" başlıklı yazıya bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-404">For more information, see "ASP.NET HttpCookie parsing" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="8b6b2-405">**ASP.NET formlar kimlik doğrulama kimlik bilgileri için SHA-2 karma seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-405">**SHA-2 hash options for ASP.NET forms authentication credentials**</span></span>

<span data-ttu-id="8b6b2-406">.NET Framework 4.7 ve önceki sürümlerde, ASP.NET geliştiricilerin MD5 veya SHA1 kullanarak yapılandırma dosyalarında hashed parolalarla kullanıcı kimlik bilgilerini depolamasına izin verdi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-406">In .NET Framework 4.7 and earlier versions, ASP.NET allowed developers to store user credentials with hashed passwords in configuration files using either MD5 or SHA1.</span></span> <span data-ttu-id="8b6b2-407">.NET Framework 4.7.1 ile başlayan ASP.NET, SHA256, SHA384 ve SHA512 gibi yeni güvenli SHA-2 karma seçeneklerini de destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-407">Starting with .NET Framework 4.7.1, ASP.NET also supports new secure SHA-2 hash options such as SHA256, SHA384, and SHA512.</span></span> <span data-ttu-id="8b6b2-408">SHA1 varsayılan olarak kalır ve varsayılan olmayan karma algoritması web yapılandırma dosyasında tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-408">SHA1 remains the default, and a non-default hash algorithm can be defined in the web configuration file.</span></span> <span data-ttu-id="8b6b2-409">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-409">For example:</span></span>

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

## <a name="whats-new-in-net-framework-47"></a><span data-ttu-id="8b6b2-410">.NET Framework 4.7'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-410">What's new in .NET Framework 4.7</span></span>

<span data-ttu-id="8b6b2-411">.NET Framework 4.7 aşağıdaki alanlarda yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-411">.NET Framework 4.7 includes new features in the following areas:</span></span>

- [<span data-ttu-id="8b6b2-412">Taban sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-412">Base classes</span></span>](#Core47)
- [<span data-ttu-id="8b6b2-413">Ağ Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-413">Networking</span></span>](#net47)
- [<span data-ttu-id="8b6b2-414">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-414">ASP.NET</span></span>](#ASP-NET47)
- [<span data-ttu-id="8b6b2-415">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-415">Windows Communication Foundation (WCF)</span></span>](#wcf47)
- [<span data-ttu-id="8b6b2-416">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b6b2-416">Windows Forms</span></span>](#wf47)
- [<span data-ttu-id="8b6b2-417">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-417">Windows Presentation Foundation (WPF)</span></span>](#WPF47)

<span data-ttu-id="8b6b2-418">.NET Framework 4.7'ye eklenen yeni API'lerin listesi için GitHub'daki [.NET Framework 4.7 API Değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-418">For a list of new APIs added to .NET Framework 4.7, see [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span></span> <span data-ttu-id="8b6b2-419">.NET Framework 4.7'deki özellik geliştirmeleri ve hata düzeltmeleri listesi için [bkz.](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-419">For a list of feature improvements and bug fixes in .NET Framework 4.7, see [.NET Framework 4.7 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) on GitHub.</span></span> <span data-ttu-id="8b6b2-420">Daha fazla bilgi için [bkz.](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-420">For more information, see [Announcing the .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) in the .NET blog.</span></span>

<a name="Core47" />

#### <a name="base-classes"></a><span data-ttu-id="8b6b2-421">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-421">Base classes</span></span>

<span data-ttu-id="8b6b2-422">.NET Framework 4.7 aşağıdakiler <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ile serileştirmeyi geliştirir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-422">.NET Framework 4.7 improves serialization by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>

<span data-ttu-id="8b6b2-423">**Eliptik Eğri Şifrelemesi (ECC) ile geliştirilmiş işlevsellik**\*</span><span class="sxs-lookup"><span data-stu-id="8b6b2-423">**Enhanced functionality with Elliptic Curve Cryptography (ECC)**\*</span></span>

<span data-ttu-id="8b6b2-424">.NET Framework 4.7'de, `ImportParameters(ECParameters)` bir <xref:System.Security.Cryptography.ECDsa> <xref:System.Security.Cryptography.ECDiffieHellman> nesnenin zaten kurulmuş bir anahtarı temsil etmesine izin vermek için ve sınıflara yöntemler eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-424">In .NET Framework 4.7, `ImportParameters(ECParameters)` methods were added to the <xref:System.Security.Cryptography.ECDsa> and <xref:System.Security.Cryptography.ECDiffieHellman> classes to allow for an object to represent an already-established key.</span></span> <span data-ttu-id="8b6b2-425">Açık `ExportParameters(Boolean)` eğri parametreleri kullanılarak anahtarı dışa aktarmak için bir yöntem de eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-425">An `ExportParameters(Boolean)` method was also added for exporting the key using explicit curve parameters.</span></span>

<span data-ttu-id="8b6b2-426">.NET Framework 4.7 ayrıca ek eğriler (Brainpool eğrisi paketi dahil) için destek ekler ve yeni <xref:System.Security.Cryptography.ECDsa.Create%2A> ve <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> fabrika yöntemleri yle oluşturma kolaylığı için önceden tanımlanmış tanımlar ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-426">.NET Framework 4.7 also adds support for additional curves (including the Brainpool curve suite), and has added predefined definitions for ease-of-creation through the new <xref:System.Security.Cryptography.ECDsa.Create%2A> and <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> factory methods.</span></span>

<span data-ttu-id="8b6b2-427">[GitHub'da .NET Framework 4.7 şifreleme geliştirmelerine bir örnek](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-427">You can see an [example of .NET Framework 4.7 cryptography improvements](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) on GitHub.</span></span>

<span data-ttu-id="8b6b2-428">**DataContractJsonSerializer tarafından kontrol karakterleri için daha iyi destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-428">**Better support for control characters by the DataContractJsonSerializer**</span></span>

<span data-ttu-id="8b6b2-429">.NET Framework 4.7'de, kontrol karakterlerini <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ECMAScript 6 standardına uygun olarak serihale sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-429">In .NET Framework 4.7, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serializes control characters in conformity with the ECMAScript 6 standard.</span></span> <span data-ttu-id="8b6b2-430">Bu davranış, .NET Framework 4.7'yi hedefleyen uygulamalar için varsayılan olarak etkinleştirilir ve .NET Framework 4.7 altında çalışan ancak .NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için bir tercih özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-430">This behavior is enabled by default for applications that target .NET Framework 4.7, and is an opt-in feature for applications that are running under .NET Framework 4.7 but target a previous version of the .NET Framework.</span></span> <span data-ttu-id="8b6b2-431">Daha fazla bilgi için bkz: [.NET Framework 4.7'deki Değişiklikleri Yeniden Hedefleme.](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-431">For more information, see [Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span></span>

<a name="net47" />

#### <a name="networking"></a><span data-ttu-id="8b6b2-432">Ağ Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-432">Networking</span></span>

<span data-ttu-id="8b6b2-433">.NET Framework 4.7 ağla ilgili aşağıdaki özelliği ekler:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-433">.NET Framework 4.7 adds the following network-related feature:</span></span>

<span data-ttu-id="8b6b2-434">**TLS protokolleri için varsayılan işletim sistemi desteği**\*</span><span class="sxs-lookup"><span data-stu-id="8b6b2-434">**Default operating system support for TLS protocols**\*</span></span>

<span data-ttu-id="8b6b2-435">HTTP, FTP ve SMTP gibi bileşenler tarafından <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve yukarı yığında kullanılan TLS yığını, geliştiricilerin işletim sistemi tarafından desteklenen varsayılan TLS protokollerini kullanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-435">The TLS stack, which is used by <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and up-stack components such as HTTP, FTP, and SMTP, allows developers to use the default TLS protocols supported by the operating system.</span></span> <span data-ttu-id="8b6b2-436">Geliştiriciler artık bir TLS sürümü sabit kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-436">Developers need no longer hard-code a TLS version.</span></span>

<a name="ASP-NET47" />

#### <a name="aspnet"></a><span data-ttu-id="8b6b2-437">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-437">ASP.NET</span></span>

<span data-ttu-id="8b6b2-438">.NET Framework 4.7'de ASP.NET aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-438">In .NET Framework 4.7, ASP.NET includes the following new features:</span></span>

<span data-ttu-id="8b6b2-439">**Nesne Önbellek Genişletilebilirlik**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-439">**Object Cache Extensibility**</span></span>

<span data-ttu-id="8b6b2-440">ASP.NET,.NET Framework 4.7 ile başlayarak, geliştiricilerin bellek içi nesne önbelleğe alma ve bellek izleme için varsayılan ASP.NET uygulamalarını değiştirmelerine olanak tanıyan yeni bir API kümesi ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-440">Starting with .NET Framework 4.7, ASP.NET adds a new set of APIs that allow developers to replace the default ASP.NET implementations for in-memory object caching and memory monitoring.</span></span> <span data-ttu-id="8b6b2-441">ASP.NET uygulaması yeterli değilse, geliştiriciler artık aşağıdaki üç bileşenden herhangi birini değiştirebilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-441">Developers can now replace any of the following three components if the ASP.NET implementation is not adequate:</span></span>

- <span data-ttu-id="8b6b2-442">**Nesne Önbellek Deposu**.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-442">**Object Cache Store**.</span></span> <span data-ttu-id="8b6b2-443">Geliştiriciler, yeni önbellek sağlayıcıları yapılandırma bölümünü kullanarak, yeni **ICacheStoreProvider** arabirimini kullanarak ASP.NET bir uygulama için nesne önbelleğinin yeni uygulamalarını takabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-443">By using the new cache providers configuration section, developers can plug in new implementations of an object cache for an ASP.NET application by using the new **ICacheStoreProvider** interface.</span></span>

- <span data-ttu-id="8b6b2-444">**Bellek izleme**.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-444">**Memory monitoring**.</span></span> <span data-ttu-id="8b6b2-445">ASP.NET'daki varsayılan bellek monitörü, işlem için yapılandırılan özel bayt sınırına yakın çalıştıklarında veya makinenin kullanılabilir toplam fiziksel RAM'i düşük olduğunda uygulamaları haber eder.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-445">The default memory monitor in ASP.NET notifies applications when they are running close to the configured private bytes limit for the process, or when the machine is low on total available physical RAM.</span></span> <span data-ttu-id="8b6b2-446">Bu sınırlar yaklaştığında, bildirimler ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-446">When these limits are near, notifications are fired.</span></span> <span data-ttu-id="8b6b2-447">Bazı uygulamalariçin bildirimler, yararlı reaksiyonlara izin vermek için yapılandırılan sınırlara çok yakın ateşlenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-447">For some applications, notifications are fired too close to the configured limits to allow for useful reactions.</span></span> <span data-ttu-id="8b6b2-448">Geliştiriciler artık <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> özelliği kullanarak varsayılan değiştirmek için kendi bellek monitörleri yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-448">Developers can now write their own memory monitors to replace the default by using the <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="8b6b2-449">**Bellek Limit Reaksiyonları**.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-449">**Memory Limit Reactions**.</span></span> <span data-ttu-id="8b6b2-450">Varsayılan olarak, ASP.NET nesne önbelleğini kırpmaya <xref:System.GC.Collect%2A?displayProperty=nameWithType> çalışır ve özel bayt işlem sınırı yaklaştığında düzenli olarak arama yapılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-450">By default, ASP.NET attempts to trim the object cache and periodically call <xref:System.GC.Collect%2A?displayProperty=nameWithType> when the private byte process limit is near.</span></span> <span data-ttu-id="8b6b2-451">Bazı uygulamalariçin, yapılan aramaların <xref:System.GC.Collect%2A?displayProperty=nameWithType> sıklığı veya kırpılan önbellek miktarı verimsizdir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-451">For some applications, the frequency of calls to <xref:System.GC.Collect%2A?displayProperty=nameWithType> or the amount of cache that is trimmed are inefficient.</span></span> <span data-ttu-id="8b6b2-452">Geliştiriciler artık Uygulamanın bellek monitörüne **IObserver** uygulamalarını abone ederek varsayılan davranışı değiştirebilir veya tamamlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-452">Developers can now replace or supplement the default behavior by subscribing **IObserver** implementations to the application's memory monitor.</span></span>

<a name="wcf47" />

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="8b6b2-453">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-453">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="8b6b2-454">Windows Communication Foundation (WCF) aşağıdaki özellikleri ve değişiklikleri ekler:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-454">Windows Communication Foundation (WCF) adds the following features and changes:</span></span>

<span data-ttu-id="8b6b2-455">**Varsayılan ileti güvenlik ayarlarını TLS 1.1 veya TLS 1.2 olarak yapılandırabilme**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-455">**Ability to configure the default message security settings to TLS 1.1 or TLS 1.2**</span></span>

<span data-ttu-id="8b6b2-456">.NET Framework 4.7 ile başlayan WCF, varsayılan ileti güvenlik protokolü olarak SSL 3.0 ve TSL 1.0'a ek olarak TSL 1.1 veya TLS 1.2 yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-456">Starting with .NET Framework 4.7, WCF allows you to configure TSL 1.1 or TLS 1.2 in addition to SSL 3.0 and TSL 1.0 as the default message security protocol.</span></span> <span data-ttu-id="8b6b2-457">Bu bir opt-in ayarıdır; etkinleştirmek için, uygulama yapılandırma dosyanıza aşağıdaki girişi eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-457">This is an opt-in setting; to enable it, you must add the following entry to your application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

<span data-ttu-id="8b6b2-458">**WCF uygulamalarının ve WCF serileştirmesinin geliştirilmiş güvenilirliği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-458">**Improved reliability of WCF applications and WCF serialization**</span></span>

<span data-ttu-id="8b6b2-459">WCF, yarış koşullarını ortadan kaldıran ve performansı ve serileştirme seçeneklerinin güvenilirliğini artıran bir dizi kod değişikliği içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-459">WCF includes a number of code changes that eliminate race conditions, thereby improving performance and the reliability of serialization options.</span></span> <span data-ttu-id="8b6b2-460">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-460">These include:</span></span>

- <span data-ttu-id="8b6b2-461">**SocketConnection.BeginRead** ve **SocketConnection.Read**aramalarında asynchronous ve senkron kodu karıştırmak için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-461">Better support for mixing asynchronous and synchronous code in calls to **SocketConnection.BeginRead** and **SocketConnection.Read**.</span></span>
- <span data-ttu-id="8b6b2-462">**SharedConnectionListener** ve **DuplexChannelBinder**ile bağlantıyı iptal ederken geliştirilmiş güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-462">Improved reliability when aborting a connection with **SharedConnectionListener** and **DuplexChannelBinder**.</span></span>
- <span data-ttu-id="8b6b2-463">Yöntemi ararken serileştirme işlemlerinin <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> güvenilirliği artırıldı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-463">Improved reliability of serialization operations when calling the <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="8b6b2-464">**ChannelSynchronizer.RemoveWaiter** yöntemini arayarak bir garsonu kaldırırken daha iyi güvenilirlik.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-464">Improved reliability when removing a waiter by calling the **ChannelSynchronizer.RemoveWaiter** method.</span></span>

<a name="wf47" />

#### <a name="windows-forms"></a><span data-ttu-id="8b6b2-465">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b6b2-465">Windows Forms</span></span>

<span data-ttu-id="8b6b2-466">.NET Framework 4.7'de, Windows Forms yüksek DPI monitörleri için desteği artırır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-466">In .NET Framework 4.7, Windows Forms improves support for high DPI monitors.</span></span>

<span data-ttu-id="8b6b2-467">**Yüksek DPI desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-467">**High DPI support**</span></span>

<span data-ttu-id="8b6b2-468">.NET Framework 4.7'yi hedefleyen uygulamalardan başlayarak,.NET Framework, Windows Forms uygulamaları için yüksek DPI ve dinamik DPI desteği ne sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-468">Starting with applications that target .NET Framework 4.7, the .NET Framework features high DPI and dynamic DPI support for Windows Forms applications.</span></span> <span data-ttu-id="8b6b2-469">Yüksek DPI desteği, yüksek DPI monitörlerde formların ve denetimlerin düzenini ve görünümünü geliştirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-469">High DPI support improves the layout and appearance of forms and controls on high DPI monitors.</span></span> <span data-ttu-id="8b6b2-470">Dinamik DPI, kullanıcı çalışan bir uygulamanın DPI veya ekran ölçek faktörünün değiştirdiğinde formların ve denetimlerin düzenini ve görünümünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-470">Dynamic DPI changes the layout and appearance of forms and controls when the user changes the DPI or display scale factor of a running application.</span></span>

<span data-ttu-id="8b6b2-471">Yüksek DPI desteği, uygulama yapılandırma dosyanızdaki [ \<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) bölümünü tanımlayarak yapılandırdığınız bir tercih özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-471">High DPI support is an opt-in feature that you configure by defining a [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) section in your application configuration file.</span></span> <span data-ttu-id="8b6b2-472">Windows Forms uygulamanıza yüksek DPI desteği ve dinamik DPI desteği ekleme hakkında daha fazla bilgi için [Windows Formlarında Yüksek DPI Desteği'ne](../winforms/high-dpi-support-in-windows-forms.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-472">For more information on adding high DPI support and dynamic DPI support to your Windows Forms application, see [High DPI Support in Windows Forms](../winforms/high-dpi-support-in-windows-forms.md).</span></span>

<a name="WPF47" />

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8b6b2-473">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-473">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8b6b2-474">.NET Framework 4.7'de WPF aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-474">In .NET Framework 4.7, WPF includes the following enhancements:</span></span>

<span data-ttu-id="8b6b2-475">**Windows WM_POINTER iletilerine dayalı dokunma/kalem yığını desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-475">**Support for a touch/stylus stack based on Windows WM_POINTER messages**</span></span>

<span data-ttu-id="8b6b2-476">Artık Windows Mürekkep Hizmetleri Platformu (WISP) yerine [WM_POINTER iletilerine](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) dayalı bir dokunma/kalem yığını kullanma seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-476">You now have the option of using a touch/stylus stack based on [WM_POINTER messages](https://docs.microsoft.com/previous-versions/windows/desktop/InputMsg/messages) instead of the Windows Ink Services Platform (WISP).</span></span> <span data-ttu-id="8b6b2-477">Bu, .NET Framework'de yer alan bir tercih özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-477">This is an opt-in feature in the .NET Framework.</span></span> <span data-ttu-id="8b6b2-478">Daha fazla bilgi için bkz: [.NET Framework 4.7'deki Değişiklikleri Yeniden Hedefleme.](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-478">For more information, see [Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span></span>

<span data-ttu-id="8b6b2-479">**WPF yazdırma API'leri için yeni uygulama**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-479">**New implementation for WPF printing APIs**</span></span>

<span data-ttu-id="8b6b2-480">WPF'nin sınıftaki <xref:System.Printing.PrintQueue?displayProperty=nameWithType> yazdırma API'leri, amortismana kalanmış [XPS Print API](/windows/desktop/printdocs/xps-printing)yerine Windows [Print Document Package API'yi](/windows/desktop/printdocs/tailored-app-printing-api) çağırır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-480">WPF's printing APIs in the <xref:System.Printing.PrintQueue?displayProperty=nameWithType> class call the Windows [Print Document Package API](/windows/desktop/printdocs/tailored-app-printing-api) instead of the deprecated [XPS Print API](/windows/desktop/printdocs/xps-printing).</span></span> <span data-ttu-id="8b6b2-481">Bu değişikliğin uygulama uyumluluğu üzerindeki etkisi [için](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-481">For the impact of this change on application compatibility, see [Retargeting Changes in the .NET Framework 4.7](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).</span></span>

<a name="v462" />

## <a name="whats-new-in-net-framework-462"></a><span data-ttu-id="8b6b2-482">.NET Framework 4.6.2'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-482">What's new in .NET Framework 4.6.2</span></span>

<span data-ttu-id="8b6b2-483">.NET Framework 4.6.2 aşağıdaki alanlarda yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-483">The .NET Framework 4.6.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="8b6b2-484">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-484">ASP.NET</span></span>](#ASPNET462)

- [<span data-ttu-id="8b6b2-485">Karakter kategorileri</span><span class="sxs-lookup"><span data-stu-id="8b6b2-485">Character categories</span></span>](#Strings)

- [<span data-ttu-id="8b6b2-486">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="8b6b2-486">Cryptography</span></span>](#Crypto462)

- [<span data-ttu-id="8b6b2-487">Sqlclient</span><span class="sxs-lookup"><span data-stu-id="8b6b2-487">SqlClient</span></span>](#SQLClient)

- [<span data-ttu-id="8b6b2-488">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8b6b2-488">Windows Communication Foundation</span></span>](#WCF)

- [<span data-ttu-id="8b6b2-489">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-489">Windows Presentation Foundation (WPF)</span></span>](#WPF462)

- [<span data-ttu-id="8b6b2-490">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-490">Windows Workflow Foundation (WF)</span></span>](#WF462)

- [<span data-ttu-id="8b6b2-491">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="8b6b2-491">ClickOnce</span></span>](#clickonce-1)

- [<span data-ttu-id="8b6b2-492">Windows Formlarını ve WPF uygulamalarını UWP uygulamalarına dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8b6b2-492">Converting Windows Forms and WPF apps to UWP apps</span></span>](#UWPConvert)

- [<span data-ttu-id="8b6b2-493">Hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="8b6b2-493">Debugging improvements</span></span>](#Debug462)

<span data-ttu-id="8b6b2-494">.NET Framework 4.6.2'ye eklenen yeni API'lerin listesi için GitHub'daki [.NET Framework 4.6.2 API Değişiklikleri'ne](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-494">For a list of new APIs added to .NET Framework 4.6.2, see [.NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) on GitHub.</span></span> <span data-ttu-id="8b6b2-495">.NET Framework 4.6.2'deki özellik geliştirmeleri ve hata düzeltmeleri listesi için [bkz.](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-495">For a list of feature improvements and bug fixes in .NET Framework 4.6.2, see [.NET Framework 4.6.2 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) on GitHub.</span></span> <span data-ttu-id="8b6b2-496">Daha fazla bilgi için .NET blogunda [.NET Framework 4.6.2'yi duyurmak](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) için bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-496">For more information, see [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) in the .NET blog.</span></span>

<a name="ASPNET462" />

### <a name="aspnet"></a><span data-ttu-id="8b6b2-497">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-497">ASP.NET</span></span>

<span data-ttu-id="8b6b2-498">.NET Framework 4.6.2'de ASP.NET aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-498">In the .NET Framework 4.6.2, ASP.NET includes the following enhancements:</span></span>

<span data-ttu-id="8b6b2-499">**Veri ek açıklama doğrulayıcılarında yerelleştirilmiş hata iletileri için geliştirilmiş destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-499">**Improved support for localized error messages in data annotation validators**</span></span>

<span data-ttu-id="8b6b2-500">Veri ek açıklama doğrulayıcıları, bir sınıf özelliğine bir veya daha fazla öznitelik ekleyerek doğrulama gerçekleştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-500">Data annotation validators enable you to perform validation by adding one or more attributes to a class property.</span></span> <span data-ttu-id="8b6b2-501">Öznitelik <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> öğesi doğrulama başarısız olursa hata iletisinin metnini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-501">The attribute's <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element defines the text of the error message if validation fails.</span></span> <span data-ttu-id="8b6b2-502">.NET Framework 4.6.2 ile başlayarak, ASP.NET hata iletilerini yerelleştirmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-502">Starting with the .NET Framework 4.6.2, ASP.NET makes it easy to localize error messages.</span></span> <span data-ttu-id="8b6b2-503">Hata iletileri:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-503">Error messages will be localized if:</span></span>

1. <span data-ttu-id="8b6b2-504">Doğrulama <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> özniteliği sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-504">The <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> is provided in the validation attribute.</span></span>

2. <span data-ttu-id="8b6b2-505">Kaynak dosyası App_LocalResources klasöründe depolanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-505">The resource file is stored in the App_LocalResources folder.</span></span>

3. <span data-ttu-id="8b6b2-506">Yerelleştirilmiş kaynaklar dosyasının `DataAnnotation.Localization.{` *adı,*`}.resx` *ad* biçimi *languageCode*`-`*ülke /regionCode* veya *languageCode*bir kültür adı dır form adı vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-506">The name of the localized resources file has the form `DataAnnotation.Localization.{`*name*`}.resx`, where *name* is a culture name in the format *languageCode*`-`*country/regionCode* or *languageCode*.</span></span>

4. <span data-ttu-id="8b6b2-507">Kaynağın anahtar adı öznitelik atanan <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> dize ve değeri yerelleştirilmiş hata iletisi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-507">The key name of the resource is the string assigned to the <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> attribute,  and its value is the localized error message.</span></span>

<span data-ttu-id="8b6b2-508">Örneğin, aşağıdaki veri ek açıklama özniteliği geçersiz bir derecelendirme için varsayılan kültürün hata iletisini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-508">For example, the following data annotation attribute defines the default culture's error message for an invalid rating.</span></span>

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

<span data-ttu-id="8b6b2-509">Daha sonra, anahtarı hata iletisi dizesi olan ve değeri yerelleştirilmiş hata iletisi olan DataAnnotation.Localization.fr.resx(</span><span class="sxs-lookup"><span data-stu-id="8b6b2-509">You can then create a resource file, DataAnnotation.Localization.fr.resx, whose key is the error message string and whose value is the localized error message.</span></span> <span data-ttu-id="8b6b2-510">Dosya `App.LocalResources` klasörde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-510">The file must be found in the `App.LocalResources` folder.</span></span> <span data-ttu-id="8b6b2-511">Örneğin, yerelleştirilmiş bir Fransızca (fr) dil hata iletisinde anahtar ve değeri aşağıdakigibidir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-511">For example, the following is the key and its value in a localized French (fr) language error message:</span></span>

| <span data-ttu-id="8b6b2-512">Adı</span><span class="sxs-lookup"><span data-stu-id="8b6b2-512">Name</span></span>                                 | <span data-ttu-id="8b6b2-513">Değer</span><span class="sxs-lookup"><span data-stu-id="8b6b2-513">Value</span></span>                                     |
| ------------------------------------ | ----------------------------------------- |
| <span data-ttu-id="8b6b2-514">Derecelendirme 1 ile 10 arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-514">The rating must be between 1 and 10.</span></span> | <span data-ttu-id="8b6b2-515">La not doit être entre 1 et 10 oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-515">La note doit être comprise entre 1 et 10.</span></span> |

 <span data-ttu-id="8b6b2-516">Buna ek olarak, veri ek açıklama yerelleştirme genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-516">In addition, data annotation localization is extensible.</span></span> <span data-ttu-id="8b6b2-517">Geliştiriciler, yerelleştirme dizesini <xref:System.Web.Globalization.IStringLocalizerProvider> kaynak dosyasıdışında başka bir yerde depolamak için arabirimi uygulayarak kendi dize yerelleştirici sağlayıcısını takabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-517">Developers can plug in their own string localizer provider by implementing the <xref:System.Web.Globalization.IStringLocalizerProvider> interface to store localization string somewhere other than in a resource file.</span></span>

 <span data-ttu-id="8b6b2-518">**Oturum durumu mağaza sağlayıcılarıyla async desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-518">**Async support with session-state store providers**</span></span>

 <span data-ttu-id="8b6b2-519">ASP.NET artık görev döndürme yöntemlerinin oturum durumu mağaza sağlayıcılarında kullanılmasına izin vererek ASP.NET uygulamalarının async'in ölçeklenebilirlik avantajlarından yararlanmasına olanak sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-519">ASP.NET now allows task-returning methods to be used with session-state store providers, thereby allowing ASP.NET apps to get the scalability benefits of async.</span></span> <span data-ttu-id="8b6b2-520">Oturum durum deposu sağlayıcıları ile eşzamanlı işlemleri destekler ASP.NET, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>devralır <xref:System.Web.IHttpModule> ve geliştiriciler kendi oturum durumu modülü ve async oturum deposu sağlayıcıları uygulamak için izin veren yeni bir arabirim içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-520">To supports asynchronous operations with session state store providers, ASP.NET includes  a new interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, which inherits from <xref:System.Web.IHttpModule> and allows developers to implement their own session-state module and async session store providers.</span></span> <span data-ttu-id="8b6b2-521">Arabirim aşağıdaki gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-521">The interface is defined as follows:</span></span>

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

 <span data-ttu-id="8b6b2-522">Buna ek <xref:System.Web.SessionState.SessionStateUtility> olarak, sınıf iki <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>yeni yöntem içerir ve , bu eşzamanlı işlemleri desteklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-522">In addition, the <xref:System.Web.SessionState.SessionStateUtility> class includes two new methods, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> and <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, that can be used to support asynchronous operations.</span></span>

 <span data-ttu-id="8b6b2-523">**Çıktı önbellek sağlayıcıları için async desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-523">**Async support for output-cache providers**</span></span>

 <span data-ttu-id="8b6b2-524">.NET Framework 4.6.2 ile başlayarak, görev döndürme yöntemleri, async'in ölçeklenebilirlik avantajlarını sağlamak için çıktı önbellek sağlayıcılarıyla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-524">Starting with the .NET Framework 4.6.2, task-returning methods can be used with output-cache providers to provide the scalability benefits of async.</span></span>  <span data-ttu-id="8b6b2-525">Bu yöntemleri uygulayan sağlayıcılar, bir web sunucusunda iş parçacığı engellemeyi azaltır ve ASP.NET bir hizmetin ölçeklenebilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-525">Providers that implement these methods reduce thread-blocking on a web server and improve the scalability of an ASP.NET service.</span></span>

 <span data-ttu-id="8b6b2-526">Eşzamanlı çıktı önbellek sağlayıcılarını desteklemek için aşağıdaki API'ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-526">The following APIs have been added to support asynchronous output-cache providers:</span></span>

- <span data-ttu-id="8b6b2-527">Geliştiricilerin <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> bir eşzamanlı <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> çıktı önbelleği sağlayıcısı nı uygulamasına olanak tanıyan sınıf.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-527">The <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> class, which inherits from <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> and allows developers to implement an asynchronous output-cache provider.</span></span>

- <span data-ttu-id="8b6b2-528">Çıktı <xref:System.Web.Caching.OutputCacheUtility> önbelleğini yapılandırmak için yardımcı yöntemler sağlayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-528">The <xref:System.Web.Caching.OutputCacheUtility> class, which provides helper methods for configuring the output cache.</span></span>

- <span data-ttu-id="8b6b2-529"><xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> Sınıfta 18 yeni yöntem.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-529">18 new methods in the <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8b6b2-530">Bunlar <xref:System.Web.HttpCachePolicy.GetCacheability%2A>arasında <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A> <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A> <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A> <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A> <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A> <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>, , , , , , ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-530">These include <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, and <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.</span></span>

- <span data-ttu-id="8b6b2-531"><xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> Sınıfta 2 yeni yöntem: <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A> <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-531">2 new methods in the <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> class:  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> and <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span></span>

- <span data-ttu-id="8b6b2-532"><xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> Sınıfta 2 yeni yöntem: <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A> <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-532">2 new methods in the <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> and <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span></span>

- <span data-ttu-id="8b6b2-533"><xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> Sınıfta 2 yeni yöntem: <xref:System.Web.HttpCacheVaryByParams.SetParams%2A> <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-533">2 new methods in the <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> and <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span></span>

- <span data-ttu-id="8b6b2-534"><xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> Sınıfta, <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> yöntem.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-534">In the <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> class, the <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> method.</span></span>

- <span data-ttu-id="8b6b2-535">' <xref:System.Web.Caching.CacheDependency> <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> de, yöntem.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-535">In the <xref:System.Web.Caching.CacheDependency>, the <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> method.</span></span>

<a name="Strings" />

### <a name="character-categories"></a><span data-ttu-id="8b6b2-536">Karakter kategorileri</span><span class="sxs-lookup"><span data-stu-id="8b6b2-536">Character categories</span></span>

<span data-ttu-id="8b6b2-537">.NET Framework 4.6.2'deki karakterler [Unicode Standardı, Sürüm 8.0.0'a](https://www.unicode.org/versions/Unicode8.0.0/)göre sınıflandırılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-537">Characters in the .NET Framework 4.6.2 are classified based on the [Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="8b6b2-538">.NET Framework 4.6 ve .NET Framework 4.6.1'de karakterler Unicode 6.3 karakter kategorilerine göre sınıflandırıldı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-538">In .NET Framework 4.6 and .NET Framework 4.6.1, characters were classified based on Unicode 6.3 character categories.</span></span>

<span data-ttu-id="8b6b2-539">Unicode 8.0 desteği, karakterlerin <xref:System.Globalization.CharUnicodeInfo> sınıfa göre sınıflandırılması ve ona dayanan tür ve yöntemlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-539">Support for Unicode 8.0 is limited to the classification of characters by the <xref:System.Globalization.CharUnicodeInfo> class and to types and methods that rely on it.</span></span> <span data-ttu-id="8b6b2-540">Bunlar <xref:System.Globalization.StringInfo> sınıf, aşırı yüklenen <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> yöntem ve .NET Framework düzenli ifade altyapısı tarafından tanınan [karakter sınıflarını](../../standard/base-types/character-classes-in-regular-expressions.md) içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-540">These include the <xref:System.Globalization.StringInfo> class, the overloaded <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> method, and the [character classes](../../standard/base-types/character-classes-in-regular-expressions.md) recognized by the .NET Framework regular expression engine.</span></span>  <span data-ttu-id="8b6b2-541">Karakter ve dize karşılaştırması ve sıralama bu değişiklikten etkilenmez ve altta yatan işletim sistemine veya Windows 7 sistemlerinde .NET Framework tarafından sağlanan karakter verilerine güvenmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-541">Character and string comparison and sorting is unaffected by this change and continues to rely on the underlying operating system or, on Windows 7 systems, on character data provided by the .NET Framework.</span></span>

<span data-ttu-id="8b6b2-542">Unicode 6.0'dan Unicode 7.0'a kadar karakter kategorilerinde yapılan değişiklikler için Unicode Konsorsiyumu web [sitesindeun Unicode Standardı, Sürüm 7.0.0'a](https://www.unicode.org/versions/Unicode7.0.0/) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-542">For changes in character categories from Unicode 6.0 to Unicode 7.0, see [The Unicode Standard, Version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) at The Unicode Consortium website.</span></span> <span data-ttu-id="8b6b2-543">Unicode 7.0'dan Unicode 8.0'a değişiklikler için Unicode Konsorsiyumu web [sitesindeki Unicode Standard, Sürüm 8.0.0'a](https://www.unicode.org/versions/Unicode8.0.0/) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-543">For changes from Unicode 7.0 to Unicode 8.0, see [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) at The Unicode Consortium website.</span></span>

<a name="Crypto462" />

### <a name="cryptography"></a><span data-ttu-id="8b6b2-544">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="8b6b2-544">Cryptography</span></span>

<span data-ttu-id="8b6b2-545">**FIPS 186-3 DSA içeren X509 sertifikaları için destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-545">**Support for X509 certificates containing FIPS 186-3 DSA**</span></span>

<span data-ttu-id="8b6b2-546">.NET Framework 4.6.2, anahtarları FIPS 186-2 1024 bit sınırını aşan DSA (Dijital İmza Algoritması) X509 sertifikaları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-546">The .NET Framework 4.6.2 adds support for DSA (Digital Signature Algorithm) X509 certificates whose keys exceed the FIPS 186-2 1024-bit limit.</span></span>

<span data-ttu-id="8b6b2-547">.NET Framework 4.6.2, FIPS 186-3'ün daha büyük anahtar boyutlarını desteklemenin yanı sıra SHA-2 karma algoritmaailesi (SHA256, SHA384 ve SHA512) ile hesaplama imzalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-547">In addition to supporting the larger key sizes of FIPS 186-3, the .NET Framework 4.6.2 allows computing signatures with the SHA-2 family of hash algorithms (SHA256, SHA384, and SHA512).</span></span> <span data-ttu-id="8b6b2-548">FIPS 186-3 desteği yeni <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> sınıf tarafından sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-548">FIPS 186-3 support is provided by the new <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="8b6b2-549">.NET Framework 4.6'daki <xref:System.Security.Cryptography.RSA> sınıf ve .NET <xref:System.Security.Cryptography.ECDsa> Framework 4.6.1'deki sınıfa yapılan son değişikliklere uygun olarak, .NET Framework 4.6.2'deki <xref:System.Security.Cryptography.DSA> soyut taban sınıfı, arayanların bu işlevselliği döküm yapmadan kullanmalarına olanak tanıyan ek yöntemlere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-549">In keeping with recent changes to the <xref:System.Security.Cryptography.RSA> class in .NET Framework 4.6 and the <xref:System.Security.Cryptography.ECDsa> class in .NET Framework 4.6.1, the <xref:System.Security.Cryptography.DSA> abstract base class in .NET Framework 4.6.2 has additional methods to allow callers to use this functionality without casting.</span></span> <span data-ttu-id="8b6b2-550">Aşağıdaki örnekte <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> görüldüğü gibi, verileri imzalamak için uzantı yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-550">You can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> extension method to sign data, as the following example shows.</span></span>

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

<span data-ttu-id="8b6b2-551">İmzalı verileri <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> doğrulamak için uzantı yöntemini aşağıdaki örnekte gösterdiği gibi arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-551">And you can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> extension method to verify signed data, as the following example shows.</span></span>

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

<span data-ttu-id="8b6b2-552">**ECDiffieHellman anahtar türetme rutinlerine girişler için artırılmış netlik**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-552">**Increased clarity for inputs to ECDiffieHellman key derivation routines**</span></span>

<span data-ttu-id="8b6b2-553">.NET Framework 3.5, üç farklı Anahtar Türetme Fonksiyonu (KDF) yordamı yla Eliptik Eğri Diffie-Hellman Anahtar Anlaşması'na destek ekledi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-553">.NET Framework 3.5 added support for Elliptic Curve Diffie-Hellman Key Agreement with three different Key Derivation Function (KDF) routines.</span></span> <span data-ttu-id="8b6b2-554">Yordamlara girişler ve yordamların kendileri, <xref:System.Security.Cryptography.ECDiffieHellmanCng> nesneüzerindeki özellikler aracılığıyla yapılandırıldı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-554">The inputs to the routines, and the routines themselves, were configured via properties on the <xref:System.Security.Cryptography.ECDiffieHellmanCng> object.</span></span> <span data-ttu-id="8b6b2-555">Ama her rutin her giriş özelliği okumak bu yana, geliştirici geçmiş karışıklık için yeterli oda vardı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-555">But since not every routine read every input property, there was ample room for confusion on the past of the developer.</span></span>

<span data-ttu-id="8b6b2-556">.NET Framework 4.6.2'de bu sorunu gidermek için, bu <xref:System.Security.Cryptography.ECDiffieHellman> KDF yordamlarını ve girişlerini daha net bir şekilde temsil etmek için taban sınıfa aşağıdaki üç yöntem eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-556">To address this in the .NET Framework 4.6.2, the following three methods have been added to the  <xref:System.Security.Cryptography.ECDiffieHellman> base class to more clearly represent these KDF routines and their inputs:</span></span>

|<span data-ttu-id="8b6b2-557">ECDiffieHellman yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-557">ECDiffieHellman method</span></span>|<span data-ttu-id="8b6b2-558">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8b6b2-558">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="8b6b2-559">Formülü kullanarak anahtar malzeme türler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-559">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="8b6b2-560">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-560">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="8b6b2-561">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-561">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="8b6b2-562">*x,* EC Diffie-Hellman algoritmasının hesaplanmış sonucudur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-562">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="8b6b2-563">Formülü kullanarak anahtar malzeme türler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-563">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="8b6b2-564">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-564">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="8b6b2-565">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-565">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="8b6b2-566">*x,* EC Diffie-Hellman algoritmasının hesaplanmış sonucudur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-566">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="8b6b2-567">TLS sözde rasgele fonksiyon (PRF) türetme algoritması kullanarak anahtar malzeme türetir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-567">Derives key material using the TLS pseudo-random function (PRF) derivation algorithm.</span></span>|

<span data-ttu-id="8b6b2-568">**Kalıcı anahtar simetrik şifreleme desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-568">**Support for persisted-key symmetric encryption**</span></span>

<span data-ttu-id="8b6b2-569">Windows şifreleme kitaplığı (CNG), kalıcı simetrik tuşları depolamak ve donanımda depolanan simetrik anahtarları kullanmak için destek ekledi ve .NET Framework 4.6.2 geliştiricilerin bu özelliği kullanmasını mümkün kıldı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-569">The Windows cryptography library (CNG) added support for storing persisted symmetric keys and using hardware-stored symmetric keys, and the .NET Framework 4.6.2 made it possible for developers to make use of this feature.</span></span>  <span data-ttu-id="8b6b2-570">Anahtar adlar ve anahtar sağlayıcılar kavramı uygulamaya özgü olduğundan, bu özelliği kullanmak, tercih edilen fabrika yaklaşımı (arama `Aes.Create`gibi) yerine somut uygulama türlerinin oluşturucusu kullanılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-570">Since the notion of key names and key providers is implementation-specific, using this feature requires utilizing the constructor of the concrete implementation types instead of the preferred factory approach (such as calling `Aes.Create`).</span></span>

<span data-ttu-id="8b6b2-571">AES ( ) ve 3DES (<xref:System.Security.Cryptography.AesCng><xref:System.Security.Cryptography.TripleDESCng>) algoritmaları için kalıcı anahtar simetrik şifreleme desteği vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-571">Persisted-key symmetric encryption support exists for the AES (<xref:System.Security.Cryptography.AesCng>) and 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorithms.</span></span> <span data-ttu-id="8b6b2-572">Örnek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-572">For example:</span></span>

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

<span data-ttu-id="8b6b2-573">**SHA-2 karma için SignedXml desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-573">**SignedXml support for SHA-2 hashing**</span></span>

<span data-ttu-id="8b6b2-574">.NET Framework 4.6.2, RSA-SHA256, RSA-SHA384 ve RSA-SHA512 PKCS#1 imza yöntemleri ve SHA256, SHA384 ve SHA512 referans özet algoritmaları için <xref:System.Security.Cryptography.Xml.SignedXml> sınıfa destek ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-574">The .NET Framework 4.6.2 adds support to  the <xref:System.Security.Cryptography.Xml.SignedXml> class for RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1 signature methods, and SHA256, SHA384, and SHA512 reference digest algorithms.</span></span>

<span data-ttu-id="8b6b2-575">URI sabitlerinin tümü şu <xref:System.Security.Cryptography.Xml.SignedXml>şekilde açıktadır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-575">The URI constants are all exposed on <xref:System.Security.Cryptography.Xml.SignedXml>:</span></span>

|<span data-ttu-id="8b6b2-576">SignedXml alanı</span><span class="sxs-lookup"><span data-stu-id="8b6b2-576">SignedXml field</span></span>|<span data-ttu-id="8b6b2-577">Sabit</span><span class="sxs-lookup"><span data-stu-id="8b6b2-577">Constant</span></span>|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|<span data-ttu-id="8b6b2-578">"http://www.w3.org/2001/04/xmlenc#sha256"</span><span class="sxs-lookup"><span data-stu-id="8b6b2-578">"http://www.w3.org/2001/04/xmlenc#sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|<span data-ttu-id="8b6b2-579">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span><span class="sxs-lookup"><span data-stu-id="8b6b2-579">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|<span data-ttu-id="8b6b2-580">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span><span class="sxs-lookup"><span data-stu-id="8b6b2-580">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|<span data-ttu-id="8b6b2-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span><span class="sxs-lookup"><span data-stu-id="8b6b2-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|<span data-ttu-id="8b6b2-582">"http://www.w3.org/2001/04/xmlenc#sha512"</span><span class="sxs-lookup"><span data-stu-id="8b6b2-582">"http://www.w3.org/2001/04/xmlenc#sha512"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|<span data-ttu-id="8b6b2-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span><span class="sxs-lookup"><span data-stu-id="8b6b2-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span></span>|

 <span data-ttu-id="8b6b2-584">Bu algoritmalar için <xref:System.Security.Cryptography.SignatureDescription> destek eklemek <xref:System.Security.Cryptography.CryptoConfig> için özel bir işleyici kaydetmiş olan tüm programlar geçmişte olduğu gibi çalışmaya devam <xref:System.Security.Cryptography.CryptoConfig> edecektir, ancak artık platform varsayılanları olduğundan, kayıt artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-584">Any programs that have registered a custom <xref:System.Security.Cryptography.SignatureDescription> handler into <xref:System.Security.Cryptography.CryptoConfig> to add support for these algorithms will continue to function as they did in the past, but since there are now platform defaults, the <xref:System.Security.Cryptography.CryptoConfig> registration is no longer necessary.</span></span>

<a name="SQLClient" />

### <a name="sqlclient"></a><span data-ttu-id="8b6b2-585">Sqlclient</span><span class="sxs-lookup"><span data-stu-id="8b6b2-585">SqlClient</span></span>

<span data-ttu-id="8b6b2-586">.NET Framework Data Provider<xref:System.Data.SqlClient?displayProperty=nameWithType>for SQL Server ( ) .NET Framework 4.6.2'de aşağıdaki yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-586">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) includes the following new features in the .NET Framework 4.6.2:</span></span>

<span data-ttu-id="8b6b2-587">**Azure SQL veritabanları ile bağlantı havuzu ve zaman ekmeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-587">**Connection pooling and timeouts with Azure SQL databases**</span></span>

<span data-ttu-id="8b6b2-588">Bağlantı havuzu etkinleştirildiğinde ve bir zaman ekme veya başka bir oturum açma hatası oluştuğunda, önbelleğe alınan özel durum önbelleğe alınır ve önbelleğe alınan özel durum sonraki 5 saniye ile 1 dakika arasında sonraki herhangi bir bağlantı denemesine atılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-588">When connection pooling is enabled and a timeout or other login error occurs, an exception is cached, and the cached exception is thrown on any subsequent connection attempt for the next 5 seconds to 1 minute.</span></span> <span data-ttu-id="8b6b2-589">Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md)adresine bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-589">For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span>

<span data-ttu-id="8b6b2-590">Bağlantı denemeleri genellikle hızlı bir şekilde kurtarılan geçici hatalarla başarısız olabileceğinden, bu davranış Azure SQL Veritabanlarına bağlanırken istenmez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-590">This behavior is not desirable when connecting to Azure SQL Databases, since connection attempts can fail with transient errors that are typically recovered quickly.</span></span> <span data-ttu-id="8b6b2-591">Bağlantı yeniden deneme deneyimini daha iyi en iyi duruma getirmek için, Azure SQL Veritabanlarına bağlantılar başarısız olduğunda bağlantı havuzu engelleme dönemi davranışı kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-591">To better optimize the connection retry experience, the connection pool blocking period behavior is removed when connections to Azure SQL Databases fail.</span></span>

<span data-ttu-id="8b6b2-592">Yeni `PoolBlockingPeriod` anahtar kelimenin eklenmesi, uygulamanız için en uygun engelleme dönemini seçmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-592">The addition of the new `PoolBlockingPeriod` keyword lets you select the blocking period best suited for your app.</span></span> <span data-ttu-id="8b6b2-593">Değerlere şunlar dahildir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-593">Values include:</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

<span data-ttu-id="8b6b2-594">Azure SQL Veritabanı'na bağlanan bir uygulamanın bağlantı havuzu engelleme süresi devre dışı bırakılır ve başka bir SQL Server örneğine bağlanan bir uygulamanın bağlantı havuzu engelleme süresi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-594">The connection pool blocking period for an application that connects to an Azure SQL Database is disabled, and the connection pool blocking period for an application that connects to any other SQL Server instance is enabled.</span></span> <span data-ttu-id="8b6b2-595">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-595">This is the default value.</span></span> <span data-ttu-id="8b6b2-596">Sunucu bitiş noktası adı aşağıdakilerden biriyle biterse, Azure SQL Veritabanları olarak kabul edilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-596">If the Server endpoint name ends with any of the following, they are considered Azure SQL Databases:</span></span>

- <span data-ttu-id="8b6b2-597">.database.windows.net</span><span class="sxs-lookup"><span data-stu-id="8b6b2-597">.database.windows.net</span></span>

- <span data-ttu-id="8b6b2-598">.database.chinacloudapi.cn</span><span class="sxs-lookup"><span data-stu-id="8b6b2-598">.database.chinacloudapi.cn</span></span>

- <span data-ttu-id="8b6b2-599">.database.usgovcloudapi.net</span><span class="sxs-lookup"><span data-stu-id="8b6b2-599">.database.usgovcloudapi.net</span></span>

- <span data-ttu-id="8b6b2-600">.database.cloudapi.de</span><span class="sxs-lookup"><span data-stu-id="8b6b2-600">.database.cloudapi.de</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

<span data-ttu-id="8b6b2-601">Bağlantı havuzu engelleme süresi her zaman etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-601">The connection pool blocking period is always enabled.</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

<span data-ttu-id="8b6b2-602">Bağlantı havuzu engelleme süresi her zaman devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-602">The connection pool blocking period is always disabled.</span></span>

<span data-ttu-id="8b6b2-603">**Her Zaman Şifrelenenler için Geliştirmeler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-603">**Enhancements for Always Encrypted**</span></span>

<span data-ttu-id="8b6b2-604">SQLClient Her Zaman Şifrelenmiş için iki geliştirme sunar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-604">SQLClient introduces two enhancements for Always Encrypted:</span></span>

- <span data-ttu-id="8b6b2-605">Parametreli sorguların şifrelenmiş veritabanı sütunlarına karşı performansını artırmak için, sorgu parametreleri için şifreleme meta verileri artık önbelleğe alındı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-605">To improve performance of parameterized queries against encrypted database columns, encryption metadata for query parameters is now cached.</span></span> <span data-ttu-id="8b6b2-606"><xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> Özellik ayarlandığı `true` (varsayılan değer olan) ile, aynı sorgu birden çok kez çağrılırsa, istemci sunucudan yalnızca bir kez parametre meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-606">With the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> property set to `true` (which is the default value), if the same query is called multiple times, the client retrieves parameter metadata from the server only once.</span></span>

- <span data-ttu-id="8b6b2-607">Anahtar önbelleğindeki sütun şifreleme anahtarı girişleri, <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> özelliği kullanılarak ayarlanan, yapılandırılabilir bir zaman aralığından sonra şimdi tahliye edilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-607">Column encryption key entries in the key cache are now evicted after a configurable time interval, set using the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> property.</span></span>

<a name="WCF" />

### <a name="windows-communication-foundation"></a><span data-ttu-id="8b6b2-608">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8b6b2-608">Windows Communication Foundation</span></span>

<span data-ttu-id="8b6b2-609">.NET Framework 4.6.2'de Windows Communication Foundation aşağıdaki alanlarda geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-609">In the .NET Framework 4.6.2, Windows Communication Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="8b6b2-610">**CNG kullanılarak depolanan sertifikalar için WCF taşıma güvenliği desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-610">**WCF transport security support for certificates stored using CNG**</span></span>

<span data-ttu-id="8b6b2-611">WCF aktarım güvenliği, Windows şifreleme kitaplığı (CNG) kullanılarak depolanan sertifikaları destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-611">WCF transport security supports certificates stored using the Windows cryptography library (CNG).</span></span> <span data-ttu-id="8b6b2-612">.NET Framework 4.6.2'de bu destek, 32 bitten fazla olmayan bir üse sahip ortak anahtara sahip sertifikaları kullanmakla sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-612">In the .NET Framework 4.6.2, this support is limited to using certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="8b6b2-613">Bir uygulama .NET Framework 4.6.2'yi hedefaldığında, bu özellik varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-613">When an application targets the .NET Framework 4.6.2, this feature is on by default.</span></span>

<span data-ttu-id="8b6b2-614">.NET Framework 4.6.1 ve daha öncesini hedefleyen ancak .NET Framework 4.6.2 üzerinde çalışan uygulamalariçin bu özellik, app.config veya web.config dosyasının [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satır eklenerek etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-614">For applications that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2, this feature can be enabled by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config or web.config file.</span></span>

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

<span data-ttu-id="8b6b2-615">Bu, aşağıdaki gibi kodla programlı olarak da yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-615">This can also be done programmatically with code like the following:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="8b6b2-616">**DataContractJsonSerializer sınıfı tarafından birden fazla gün ışığından yararlanma saati ayarlama kuralları için daha iyi destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-616">**Better support for multiple daylight saving time adjustment rules by the DataContractJsonSerializer class**</span></span>

<span data-ttu-id="8b6b2-617">Müşteriler, sınıfın tek bir saat <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> dilimi için birden çok ayarlama kuralını destekleyip desteklemediğini belirlemek için bir uygulama yapılandırma ayarını kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-617">Customers can use an application configuration setting to determine whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class supports multiple adjustment rules for a single time zone.</span></span> <span data-ttu-id="8b6b2-618">Bu bir tercih özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-618">This is an opt-in feature.</span></span> <span data-ttu-id="8b6b2-619">Etkinleştirmek için app.config dosyanıza aşağıdaki ayarı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-619">To enable it, add the following setting to your app.config file:</span></span>

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

<span data-ttu-id="8b6b2-620">Bu özellik etkinleştirildiğinde, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir <xref:System.TimeZoneInfo> nesne tarih <xref:System.TimeZone> ve saat verilerini deserialize etmek için türü yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-620">When this feature is enabled, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object uses the <xref:System.TimeZoneInfo> type instead of the <xref:System.TimeZone> type to deserialize date and time data.</span></span> <span data-ttu-id="8b6b2-621"><xref:System.TimeZoneInfo>geçmiş saat dilimi verileriyle çalışmayı mümkün kılan birden çok ayarlama kuralını destekler;   <xref:System.TimeZone> değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-621"><xref:System.TimeZoneInfo> supports multiple adjustment rules, which makes it possible to work with historic time zone data;   <xref:System.TimeZone> does not.</span></span>

<span data-ttu-id="8b6b2-622"><xref:System.TimeZoneInfo> Yapı ve saat dilimi ayarlamaları hakkında daha fazla bilgi için Saat [Dilimine Genel Bakış'a](../../standard/datetime/time-zone-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-622">For more information on the <xref:System.TimeZoneInfo> structure and time zone adjustments, see [Time Zone Overview](../../standard/datetime/time-zone-overview.md).</span></span>

<span data-ttu-id="8b6b2-623">**NetNamedPipeBinding en iyi maç**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-623">**NetNamedPipeBinding best match**</span></span>

<span data-ttu-id="8b6b2-624">WCF, istedikleri uygulamayla en iyi eşleşen URI dinleme hizmetine her zaman bağlanmalarını sağlamak için istemci uygulamalarında ayarlanabilen yeni bir uygulama ayarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-624">WCF has a new app setting that can be set on client applications to ensure they always connect to the service listening on the URI that best matches the one that they request.</span></span> <span data-ttu-id="8b6b2-625">Bu uygulama ayarı `false` (varsayılan) olarak ayarlandığı <xref:System.ServiceModel.NetNamedPipeBinding> için, kullanan istemcilerin istenen URI'nin bir alt parçası olan URI'yi dinleyen bir hizmete bağlanmaya çalışması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-625">With this app setting set to `false` (the default), it is possible for clients using <xref:System.ServiceModel.NetNamedPipeBinding> to attempt to connect to a service listening on a URI that is a substring of the requested URI.</span></span>

<span data-ttu-id="8b6b2-626">Örneğin, bir istemci dinleme bir hizmete `net.pipe://localhost/Service1`bağlanmaya çalışır, ancak yönetici ayrıcalığı ile `net.pipe://localhost`çalışan bu makinede farklı bir hizmet dinliyor .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-626">For example, a client tries to connect to a service listening at `net.pipe://localhost/Service1`, but a different service on that machine running with administrator privilege is listening at `net.pipe://localhost`.</span></span> <span data-ttu-id="8b6b2-627">Bu uygulama ayarı `false`ayarlandığı için, istemci yanlış hizmete bağlanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-627">With this app setting set to `false`, the client would attempt to connect to the wrong service.</span></span> <span data-ttu-id="8b6b2-628">Uygulama ayarını ayarladıktan `true`sonra, istemci her zaman en iyi eşleşen hizmete bağlanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-628">After setting the app setting to `true`, the client will always connect to the best matching service.</span></span>

> [!NOTE]
> <span data-ttu-id="8b6b2-629">Tam <xref:System.ServiceModel.NetNamedPipeBinding> bitiş noktası adresi yerine hizmetin temel adresine (varsa) dayalı hizmetleri kullanan istemciler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-629">Clients using <xref:System.ServiceModel.NetNamedPipeBinding> find services based on the service's base address (if it exists) rather than the full endpoint address.</span></span> <span data-ttu-id="8b6b2-630">Bu ayarın her zaman çalıştığından emin olmak için hizmetin benzersiz bir temel adres kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-630">To ensure this setting always works the service should use a unique base address.</span></span>

<span data-ttu-id="8b6b2-631">Bu değişikliği etkinleştirmek için, istemci uygulamanızın App.config veya Web.config dosyasına aşağıdaki uygulama ayarını ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-631">To enable this change, add the following app setting to your client application's App.config or Web.config file:</span></span>

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="8b6b2-632">**SSL 3.0 varsayılan bir protokol değildir**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-632">**SSL 3.0 is not a default protocol**</span></span>

<span data-ttu-id="8b6b2-633">Aktarım güvenliği ve kimlik bilgisi sertifikası türüyle NetTcp kullanılırken, SSL 3.0 artık güvenli bir bağlantı için kullanılan varsayılan bir protokol değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-633">When using NetTcp with transport security and a credential type of certificate, SSL 3.0 is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="8b6b2-634">TlS 1.0 NetTcp için protokol listesine dahil olduğundan, çoğu durumda, varolan uygulamalar üzerinde hiçbir etkisi olmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-634">In most cases, there should be no impact to existing apps, because TLS 1.0 is included in the protocol list for NetTcp.</span></span> <span data-ttu-id="8b6b2-635">Mevcut tüm istemciler en az TLS 1.0 kullanarak bir bağlantı üzerinde anlaşma yapabilmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-635">All existing clients should be able to negotiate a connection using at least TLS 1.0.</span></span> <span data-ttu-id="8b6b2-636">Ssl3 gerekiyorsa, anlaşmalı protokoller listesine eklemek için aşağıdaki yapılandırma mekanizmalarından birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-636">If Ssl3 is required, use one of the following configuration mechanisms to add it to the list of negotiated protocols.</span></span>

- <span data-ttu-id="8b6b2-637">Özellik <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b6b2-637">The <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="8b6b2-638">Özellik <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b6b2-638">The <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="8b6b2-639">[ \<](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) [ \<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) bölümünün taşıma>bölümü</span><span class="sxs-lookup"><span data-stu-id="8b6b2-639">The [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) section</span></span>

- <span data-ttu-id="8b6b2-640">[ \<ÖzelBağlayıcı](../configure-apps/file-schema/wcf/custombinding.md) [ \<](../configure-apps/file-schema/wcf/sslstreamsecurity.md)>bölümünün sslStreamSecurity>bölümü</span><span class="sxs-lookup"><span data-stu-id="8b6b2-640">The [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) section</span></span>

<a name="WPF462" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8b6b2-641">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-641">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8b6b2-642">.NET Framework 4.6.2'de, Windows Sunu Vakfı aşağıdaki alanlarda geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-642">In the .NET Framework 4.6.2, Windows Presentation Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="8b6b2-643">**Grup sıralama**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-643">**Group sorting**</span></span>

<span data-ttu-id="8b6b2-644">Verileri gruplandırmak <xref:System.Windows.Data.CollectionView> için bir nesne kullanan bir uygulama artık grupları nasıl sıralayacak açık bir şekilde bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-644">An application that uses a <xref:System.Windows.Data.CollectionView> object to group data can now explicitly declare how to  sort the groups.</span></span> <span data-ttu-id="8b6b2-645">Açık sıralama, bir uygulama dinamik olarak gruplar eklendiğinde veya kaldırdığında veya gruplandırmada yer alan madde özelliklerinin değerini değiştirdiğinde ortaya çıkan sezgisel olmayan sıralama sorununu gidermektedir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-645">Explicit sorting addresses the problem of non-intuitive ordering that occurs when an app dynamically adds or removes groups, or when it changes the value of item properties involved in grouping.</span></span> <span data-ttu-id="8b6b2-646">Ayrıca, gruplandırma özelliklerinin karşılaştırmalarını tam koleksiyon türünden grupların türüne taşıyarak grup oluşturma işleminin performansını artırabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-646">It can also improve the performance of the group creation process by moving comparisons of the grouping properties from the sort of the full collection to the sort of the groups.</span></span>

<span data-ttu-id="8b6b2-647">Grup sıralamasını desteklemek için, yeni <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> ve <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> özellikler nesne tarafından üretilen <xref:System.ComponentModel.GroupDescription> grupların koleksiyonunu nasıl sıralayacaklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-647">To support group sorting, the new <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> and <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> properties describe how to sort the collection of groups produced by the <xref:System.ComponentModel.GroupDescription> object.</span></span> <span data-ttu-id="8b6b2-648">Bu, aynı adlandırılmış <xref:System.Windows.Data.ListCollectionView> özelliklerin veri öğelerini nasıl sıralayacaklarını açıklama şekline benzer.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-648">This is analogous to the way the identically named <xref:System.Windows.Data.ListCollectionView> properties describe how to sort the data items.</span></span>

<span data-ttu-id="8b6b2-649"><xref:System.Windows.Data.PropertyGroupDescription> Sınıfın iki yeni statik <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> özellikleri <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>ve , en sık karşılaşılan durumlar için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-649">Two new static properties of the <xref:System.Windows.Data.PropertyGroupDescription> class,  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> and <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, can be used for the most common cases.</span></span>

<span data-ttu-id="8b6b2-650">Örneğin, aşağıdaki XAML verileri yaşa göre gruplandırmak, artan sırada yaş gruplarını sıralamak ve her yaş grubundaki öğeleri soyadına göre gruplandırmak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-650">For example, the following XAML groups data by age, sort the age groups in ascending order, and group the items within each age group by last name.</span></span>

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

<span data-ttu-id="8b6b2-651">**Dokunmatik klavye desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-651">**Touch keyboard support**</span></span>

<span data-ttu-id="8b6b2-652">Dokunmatik klavye desteği, metin girişi alabilen bir denetim tarafından dokunmatik giriş yapıldığında Windows 10'daki dokunmatik Klavyeyi otomatik olarak çağırArak ve reddederek WPF uygulamalarında odak izleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-652">Touch keyboard support enables focus tracking in WPF applications by automatically invoking and dismissing the touch Keyboard in Windows 10 when the touch input is received by a control that can take textual input.</span></span>

<span data-ttu-id="8b6b2-653">.NET Framework'ün önceki sürümlerinde, WPF uygulamaları WPF kalem/dokunma hareketi desteğini devre dışı bırakmadan odak izlemeyi seçemez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-653">In previous versions of .NET Framework, WPF applications can't opt into the focus tracking without disabling WPF pen/touch gesture support.</span></span> <span data-ttu-id="8b6b2-654">Sonuç olarak, WPF uygulamaları tam WPF dokunmatik desteği arasında seçim yapmalı veya Windows fare promosyonuna güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-654">As a result, WPF applications must choose between full WPF touch support or rely on Windows mouse promotion.</span></span>

<span data-ttu-id="8b6b2-655">**Monitör başına DPI**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-655">**Per-monitor DPI**</span></span>

<span data-ttu-id="8b6b2-656">WPF uygulamaları için yüksek DPI ve hibrit DPI ortamlarının yakın zamanda yayılmasını desteklemek için,.NET Framework 4.6.2'deki WPF, monitör başına farkındalık sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-656">To support the recent proliferation of high-DPI and hybrid-DPI environments for WPF apps, WPF in the .NET Framework 4.6.2 enables per-monitor awareness.</span></span> <span data-ttu-id="8b6b2-657">WPF uygulamanızın monitör başına DPI farkında olmasını nasıl sağlayacağınız hakkında daha fazla bilgi için GitHub'daki [örneklere ve geliştirici kılavuzuna](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-657">See the [samples and developer guide](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) on GitHub for more information about how to enable your WPF app to become per-monitor DPI aware.</span></span>

<span data-ttu-id="8b6b2-658">.NET Framework'ün önceki sürümlerinde, WPF uygulamaları sistem-DPI farkındadır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-658">In previous versions of the .NET Framework, WPF apps are system-DPI aware.</span></span> <span data-ttu-id="8b6b2-659">Başka bir deyişle, uygulamanın Kullanıcı UI'si, uygulamanın işlendiği monitörün DPI'sına bağlı olarak, uygun şekilde OS tarafından ölçeklendirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-659">In other words, the application's UI is scaled by the OS as appropriate, depending on the DPI of the monitor on which the app is rendered.</span></span>

<span data-ttu-id="8b6b2-660">.NET Framework 4.6.2 altında çalışan uygulamalar için, uygulama yapılandırma dosyanızın [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki gibi bir yapılandırma bildirimi ekleyerek WPF uygulamalarındaki DPI değişikliklerini izlemek başına devre dışı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-660">For apps running under the .NET Framework 4.6.2, you can disable per-monitor DPI changes in WPF apps by adding a configuration statement to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file, as follows:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462" />

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="8b6b2-661">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-661">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="8b6b2-662">.NET Framework 4.6.2'de, Windows İş Akışı Temeli aşağıdaki alanda geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-662">In the .NET Framework 4.6.2, Windows Workflow Foundation has been enhanced in the following area:</span></span>

<span data-ttu-id="8b6b2-663">**Yeniden Barındırılan WF Tasarımcısı'nda C# ifadeleri ve IntelliSense desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-663">**Support for C# expressions and IntelliSense in the Rehosted WF Designer**</span></span>

<span data-ttu-id="8b6b2-664">.NET Framework 4.5 ile başlayan WF, Hem Visual Studio Designer'da hem de kod iş akışlarında C# ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-664">Starting with .NET Framework 4.5, WF supports C# expressions in both the Visual Studio Designer and in code workflows.</span></span> <span data-ttu-id="8b6b2-665">Yeniden Barındırılan İş Akışı Tasarımcısı, İş Akışı Tasarımcısı'nın Visual Studio dışındaki bir uygulamada (örneğin, WPF'de) olmasını sağlayan WF'nin önemli bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-665">The Rehosted Workflow Designer is a key feature of WF that allows for the Workflow Designer to be in an application outside Visual Studio (for example, in WPF).</span></span>  <span data-ttu-id="8b6b2-666">Windows İş Akışı Temeli, Yeniden Barındırılan İş Akışı Tasarımcısı'nda C# ifadelerini ve IntelliSense'i destekleme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-666">Windows Workflow Foundation provides the ability to support C# expressions and IntelliSense in the Rehosted Workflow Designer.</span></span> <span data-ttu-id="8b6b2-667">Daha fazla bilgi için [Windows İş Akışı Vakfı bloguna](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-667">For more information, see the [Windows Workflow Foundation blog](https://docs.microsoft.com/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span></span>

<span data-ttu-id="8b6b2-668">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`4.6.2'den önceki .NET Framework sürümlerinde, Bir müşteri Visual Studio'dan bir iş akışı projesi yeniden inşa ettiğinde WF Designer IntelliSense bozulur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-668">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` In versions of the .NET Framework prior to 4.6.2, WF Designer IntelliSense is broken when a customer rebuilds a workflow project from Visual Studio.</span></span> <span data-ttu-id="8b6b2-669">Proje yapısı başarılı olsa da, tasarımcıda iş akışı türleri bulunmaz ve eksik iş akışı türleri için IntelliSense'den gelen uyarılar **Hata Listesi** penceresinde görünür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-669">While the project build is successful, the workflow types are not found on the designer, and warnings from IntelliSense for the missing workflow types appear in the **Error List** window.</span></span> <span data-ttu-id="8b6b2-670">.NET Framework 4.6.2 bu sorunu gideriyor ve IntelliSense'i kullanılabilir hale getiriyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-670">.NET Framework 4.6.2 addresses this issue and makes IntelliSense available.</span></span>

<span data-ttu-id="8b6b2-671">**İş Akışı İzleme ile İş Akışı V1 uygulamaları artık FIPS modu altında çalıştırıl**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-671">**Workflow V1 applications with Workflow Tracking on now run under FIPS-mode**</span></span>

<span data-ttu-id="8b6b2-672">FIPS Uyumluluk Modu etkin leştirilmiş makineler artık iş akışı Sürüm 1 tarzı bir uygulamayı İş Akışı izleme üzerinde başarıyla çalıştırabiliyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-672">Machines with FIPS Compliance Mode enabled can now successfully run a workflow Version 1-style application with Workflow tracking on.</span></span> <span data-ttu-id="8b6b2-673">Bu senaryoyu etkinleştirmek için app.config dosyanızda aşağıdaki değişikliği yapmalısınız:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-673">To enable this scenario, you must make the following change to your app.config file:</span></span>

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

<span data-ttu-id="8b6b2-674">Bu senaryo etkinleştirilmezse, uygulamayı çalıştıran ileti ile bir özel durum oluşturmaya devam ediyor, "Bu uygulama Windows Platformu FIPS doğrulanmış şifreleme algoritmaları parçası değildir."</span><span class="sxs-lookup"><span data-stu-id="8b6b2-674">If this scenario is not enabled, running the application continues to generate an exception with the message, "This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms."</span></span>

<span data-ttu-id="8b6b2-675">**Visual Studio İş Akışı Tasarımcısı ile Dinamik Güncelleme kullanırken İş Akışı Geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-675">**Workflow Improvements when using Dynamic Update with Visual Studio Workflow Designer**</span></span>

<span data-ttu-id="8b6b2-676">İş Akışı Tasarımcısı, FlowChart Etkinlik Tasarımcısı ve diğer İş Akışı Etkinlik Tasarımcıları artık <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi aradıktan sonra kaydedilen iş akışlarını başarıyla yükler ve görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-676">The Workflow Designer, FlowChart Activity Designer, and other Workflow Activity Designers now successfully load and display workflows that have been saved after calling  the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b6b2-677">.NET Framework 4.6.2'den önceki .NET Framework sürümlerinde, arama <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> dan sonra kaydedilen bir iş akışı için Visual Studio'da bir XAML dosyasının yüklenmesi aşağıdaki sorunlara neden olabilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-677">In versions of the .NET Framework before .NET Framework 4.6.2, loading a XAML file in Visual Studio for a workflow that has been saved after calling <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> can result in the following issues:</span></span>

- <span data-ttu-id="8b6b2-678">İş Akışı Tasarımcısı XAML dosyasını doğru yükleyemez <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> (satırın sonundayken).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-678">The Workflow Designer can't load the XAML file correctly (when the <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> is at the end of the line).</span></span>

- <span data-ttu-id="8b6b2-679">Akış Şeması Etkinlik Tasarımcısı veya diğer İş Akışı Etkinlik Tasarımcıları, ekli özellik değerlerinin aksine tüm nesneleri varsayılan konumlarında görüntüleyebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-679">Flowchart Activity Designer or other Workflow Activity Designers may display all objects in their default locations as opposed to attached property values.</span></span>

<a name="clickonce-1" />

### <a name="clickonce"></a><span data-ttu-id="8b6b2-680">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="8b6b2-680">ClickOnce</span></span>

<span data-ttu-id="8b6b2-681">ClickOnce, zaten desteklediği 1.0 protokolüne ek olarak TLS 1.1 ve TLS 1.2'yi destekleyecek şekilde güncellendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-681">ClickOnce has been updated to support TLS 1.1 and TLS 1.2 in addition to the 1.0 protocol, which it already supports.</span></span> <span data-ttu-id="8b6b2-682">ClickOnce hangi protokolün gerekli olduğunu otomatik olarak algılar; TLS 1.1 ve 1.2 desteğini etkinleştirmek için ClickOnce uygulamasında ek adım gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-682">ClickOnce automatically detects which protocol is required; no extra steps within the ClickOnce application are required to enable TLS 1.1 and 1.2 support.</span></span>

<a name="UWPConvert" />

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a><span data-ttu-id="8b6b2-683">Windows Formlarını ve WPF uygulamalarını UWP uygulamalarına dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8b6b2-683">Converting Windows Forms and WPF apps to  UWP apps</span></span>

<span data-ttu-id="8b6b2-684">Windows artık WPF ve Windows Forms uygulamaları da dahil olmak üzere mevcut Windows masaüstü uygulamalarını Evrensel Windows Platformu'na (UWP) getirme özellikleri sunuyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-684">Windows now offers capabilities to bring existing Windows desktop apps, including WPF and Windows Forms apps, to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="8b6b2-685">Bu teknoloji, mevcut kod tabanınızı kademeli olarak UWP'ye geçirmenizi sağlayarak uygulamanızı tüm Windows 10 aygıtlarına getirerek bir köprü görevi görür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-685">This technology acts as a bridge by enabling you to gradually migrate your existing code base to UWP, thereby bringing your app to all Windows 10 devices.</span></span>

<span data-ttu-id="8b6b2-686">Dönüştürülmüş masaüstü uygulamaları, UWP uygulamalarının uygulama kimliğine benzer bir uygulama kimliği kazanır ve bu da UWP API'lerinin Canlı Kutucuklar ve bildirimler gibi özellikleri etkinleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-686">Converted desktop apps gain an app identity similar to the app identity of UWP apps, which makes UWP APIs accessible to enable features such as Live Tiles and notifications.</span></span> <span data-ttu-id="8b6b2-687">Uygulama eskisi gibi olmaya devam ediyor ve tam bir güven uygulaması olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-687">The app continues to behave as before and runs as a full trust app.</span></span> <span data-ttu-id="8b6b2-688">Uygulama dönüştürüldükten sonra, uyarlanabilir bir kullanıcı arabirimi eklemek için varolan tam güven işlemine bir uygulama kapsayıcı işlemi eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-688">Once the app is converted, an app container process can be added to the existing full trust process to add an adaptive user interface.</span></span> <span data-ttu-id="8b6b2-689">Tüm işlevler uygulama kapsayıcı işlemine taşındığında, tam güven işlemi kaldırılabilir ve yeni UWP uygulaması tüm Windows 10 aygıtları tarafından kullanılabilir hale getirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-689">When all functionality is moved to the app container process, the full trust process can be removed and the new UWP app can be made available to all Windows 10 devices.</span></span>

<a name="Debug462" />

### <a name="debugging-improvements"></a><span data-ttu-id="8b6b2-690">Hata ayıklama iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="8b6b2-690">Debugging improvements</span></span>

<span data-ttu-id="8b6b2-691">*Yönetilmeyen hata ayıklama API* kaynak kodu tek bir satırda hangi değişkenbelirlemek mümkün <xref:System.NullReferenceException> böylece bir atıldığında ek analiz gerçekleştirmek için .NET `null`Framework 4.6.2 geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-691">The *unmanaged debugging API* has been enhanced in the .NET Framework 4.6.2 to perform additional analysis when a <xref:System.NullReferenceException> is thrown so that it is possible to determine which variable in a single line of source code is `null`.</span></span>   <span data-ttu-id="8b6b2-692">Bu senaryoyu desteklemek için, yönetilmeyen hata ayıklama API'sine aşağıdaki API'ler eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-692">To support this scenario, the following APIs have been added to the unmanaged debugging API.</span></span>

- <span data-ttu-id="8b6b2-693">[ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), ve [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) arayüzleri, yönetilen değişkenlerin yerli evleri ortaya çıkarmak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-693">The [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), and [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, which expose the native homes of managed variables.</span></span> <span data-ttu-id="8b6b2-694">Bu, hata ayıklayıcıların bir <xref:System.NullReferenceException> olay olduğunda bazı kod akış çözümlemesi yapmalarını ve yerel konuma karşılık `null`gelen yönetilen değişkeni belirlemek için geriye doğru çalışmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-694">This enables debuggers to do some code flow analysis when a  <xref:System.NullReferenceException> occurs and to work backwards to determine the managed variable that corresponds to the native location that was `null`.</span></span>

- <span data-ttu-id="8b6b2-695">[ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi, hata ayıklayıcının ICorDebugType örneği olmadan [bir COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) elde etmesini sağlayan iCorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md)için bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-695">The [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method provides a mapping for ICorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), which allows the debugger to obtain a [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) without an instance of the ICorDebugType.</span></span> <span data-ttu-id="8b6b2-696">[COR_TYPEID'daki](../unmanaged-api/debugging/cor-typeid-structure.md) varolan API'ler daha sonra türün sınıf düzenini belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-696">Existing APIs on [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) can then be used to determine the class layout of the type.</span></span>

<a name="v461" />

## <a name="whats-new-in-net-framework-461"></a><span data-ttu-id="8b6b2-697">.NET Framework 4.6.1'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-697">What's new in .NET Framework 4.6.1</span></span>

<span data-ttu-id="8b6b2-698">.NET Framework 4.6.1 aşağıdaki alanlarda yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-698">The .NET Framework 4.6.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="8b6b2-699">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="8b6b2-699">Cryptography</span></span>](#Crypto)

- [<span data-ttu-id="8b6b2-700">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-700">ADO.NET</span></span>](#ADO.NET461)

- [<span data-ttu-id="8b6b2-701">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-701">Windows Presentation Foundation (WPF)</span></span>](#WPF461)

- [<span data-ttu-id="8b6b2-702">Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="8b6b2-702">Windows Workflow Foundation</span></span>](#WWF461)

- [<span data-ttu-id="8b6b2-703">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-703">Profiling</span></span>](#Profile461)

- [<span data-ttu-id="8b6b2-704">Ngen</span><span class="sxs-lookup"><span data-stu-id="8b6b2-704">NGen</span></span>](#NGEN461)

<span data-ttu-id="8b6b2-705">.NET Framework 4.6.1 hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-705">For more information on the .NET Framework 4.6.1, see the following topics:</span></span>

- [<span data-ttu-id="8b6b2-706">.NET Framework 4.6.1 değişiklik listesi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-706">.NET Framework 4.6.1 list of changes</span></span>](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [<span data-ttu-id="8b6b2-707">4.6.1'de Uygulama Uyumluluğu</span><span class="sxs-lookup"><span data-stu-id="8b6b2-707">Application Compatibility in 4.6.1</span></span>](../migration-guide/application-compatibility.md)

- <span data-ttu-id="8b6b2-708">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (GitHub'da)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-708">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (on GitHub)</span></span>

<a name="Crypto" />

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a><span data-ttu-id="8b6b2-709">Şifreleme: ECDSA içeren X509 sertifikaları için destek</span><span class="sxs-lookup"><span data-stu-id="8b6b2-709">Cryptography: Support for X509 certificates containing ECDSA</span></span>

<span data-ttu-id="8b6b2-710">.NET Framework 4.6 X509 sertifikaları için RSACng desteği eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-710">.NET Framework 4.6 added RSACng support for X509 certificates.</span></span> <span data-ttu-id="8b6b2-711">.NET Framework 4.6.1, ECDSA (Eliptik Eğri Dijital İmza Algoritması) X509 sertifikaları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-711">The .NET Framework 4.6.1 adds support for ECDSA (Elliptic Curve Digital Signature Algorithm) X509 certificates.</span></span>

<span data-ttu-id="8b6b2-712">ECDSA daha iyi performans sunar ve RSA'dan daha güvenli bir şifreleme algoritmasıdır ve Taşıma Katmanı Güvenliği (TLS) performansı ve ölçeklenebilirliğinin bir sorun olduğu mükemmel bir seçim sunar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-712">ECDSA offers better performance and is a more secure cryptography algorithm than RSA, providing an excellent choice where Transport Layer Security (TLS) performance and scalability is a concern.</span></span> <span data-ttu-id="8b6b2-713">.NET Framework uygulaması çağrıları varolan Windows işlevlerine sarar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-713">The .NET Framework implementation wraps calls into existing Windows functionality.</span></span>

<span data-ttu-id="8b6b2-714">Aşağıdaki örnek kod, .NET Framework 4.6.1'de yer alan ECDSA X509 sertifikaları için yeni desteği kullanarak bir bayt akışı için imza oluşturmanın ne kadar kolay olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-714">The following example code shows how easy it is to generate a signature for a byte stream by using the new  support for ECDSA  X509 certificates included in the .NET Framework 4.6.1.</span></span>

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

<span data-ttu-id="8b6b2-715">Bu, .NET Framework 4.6'da imza oluşturmak için gereken kodla belirgin bir kontrast sunar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-715">This offers a marked contrast to the code needed to generate a signature in .NET Framework 4.6.</span></span>

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461" />

### <a name="adonet"></a><span data-ttu-id="8b6b2-716">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-716">ADO.NET</span></span>

<span data-ttu-id="8b6b2-717">ADO.NET aşağıdakiler eklendi:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-717">The following have been added to ADO.NET:</span></span>

<span data-ttu-id="8b6b2-718">**Donanım korumalı anahtarlar için her zaman Şifrelenmiş destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-718">**Always Encrypted support for hardware protected keys**</span></span>

<span data-ttu-id="8b6b2-719">ADO.NET artık Her Zaman Şifrelenmiş sütun ana anahtarlarını Donanım Güvenlik Modüllerinde (HSM) doğal olarak depolamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-719">ADO.NET now supports storing Always Encrypted column master keys natively in Hardware Security Modules (HSMs).</span></span> <span data-ttu-id="8b6b2-720">Bu destekle, müşteriler özel sütun ana anahtar deposu sağlayıcıları yazmak ve bunları uygulamalara kaydettirmek zorunda kalmadan HSM'lerde depolanan asimetrik anahtarlardan yararlanabilirler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-720">With this support, customers can leverage asymmetric keys stored in HSMs without having to write custom column master key store providers and registering them in applications.</span></span>

<span data-ttu-id="8b6b2-721">Müşterilerin HSM'de depolanan sütun ana anahtarlarıyla korunan Her Zaman Şifrelenmiş verilere erişmek için hsm satıcı tarafından sağlanan CSP sağlayıcısını veya CNG anahtar mağaza sağlayıcılarını uygulama sunucularına veya istemci bilgisayarlara yüklemeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-721">Customers need to install the HSM vendor-provided CSP provider or CNG key store providers on the app servers or client computers in order to access Always Encrypted data protected with column master keys stored in a HSM.</span></span>

<span data-ttu-id="8b6b2-722">**AlwaysOn için geliştirilmiş <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> bağlantı davranışı**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-722">**Improved <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> connection behavior for AlwaysOn**</span></span>

<span data-ttu-id="8b6b2-723">SqlClient artık bir AlwaysOn Kullanılabilirlik Grubu'na (AG) otomatik olarak daha hızlı bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-723">SqlClient now automatically provides faster connections to an AlwaysOn Availability Group (AG).</span></span> <span data-ttu-id="8b6b2-724">Uygulamanızın farklı bir alt ağdaki bir AlwaysOn kullanılabilirlik grubuna (AG) bağlanıp bağlanmadığını saydam olarak algılar ve geçerli etkin sunucuyu hızla keşfeder ve sunucuya bağlantı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-724">It transparently detects whether your application is connecting to an AlwaysOn availability group (AG) on a different subnet and quickly discovers the current active server and provides a connection to the server.</span></span> <span data-ttu-id="8b6b2-725">Bu sürümden önce, bir uygulamanın bir `"MultisubnetFailover=true"` AlwaysOn Kullanılabilirlik Grubuna bağlandığını belirtmek için bağlantı dizesini eklemesi gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-725">Prior to this release, an application had to set the connection string to include `"MultisubnetFailover=true"` to indicate that it was connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="8b6b2-726">Bağlantı anahtar sözcükünü `true`ayarlamadan, bir uygulama Bir AlwaysOn Kullanılabilirlik Grubuna bağlanırken bir zaman ayarı yaşayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-726">Without setting the connection keyword to `true`, an application might experience a timeout while connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="8b6b2-727">Bu sürümle, bir uygulamanın `true` <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> artık ayarlanmaması *gerekmez.*</span><span class="sxs-lookup"><span data-stu-id="8b6b2-727">With this release, an application does *not* need to set <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> to `true` anymore.</span></span> <span data-ttu-id="8b6b2-728">Her Zaman Kullanılabilirlik Grupları için SqlClient desteği hakkında daha fazla bilgi için, [Yüksek Kullanılabilirlik için SqlClient Desteği, Olağanüstü Durum Kurtarma'ya](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-728">For more information about SqlClient support for Always On Availability Groups, see [SqlClient Support for High Availability, Disaster Recovery](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span></span>

<a name="WPF461" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8b6b2-729">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-729">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8b6b2-730">Windows Sunu Temeli bir dizi geliştirme ve değişiklik içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-730">Windows Presentation Foundation includes a number of improvements and changes.</span></span>

<span data-ttu-id="8b6b2-731">**Geliştirilmiş performans**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-731">**Improved performance**</span></span>

<span data-ttu-id="8b6b2-732">Dokunma olaylarının ateşlemedeki gecikmesi .NET Framework 4.6.1'de giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-732">The delay in firing touch events has been fixed in the .NET Framework 4.6.1.</span></span> <span data-ttu-id="8b6b2-733">Buna ek olarak, <xref:System.Windows.Controls.RichTextBox> bir denetim de yazma artık hızlı giriş sırasında render iş parçacığı bağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-733">In addition, typing in a <xref:System.Windows.Controls.RichTextBox> control no longer ties up the render thread during fast input.</span></span>

<span data-ttu-id="8b6b2-734">**Yazım denetimi geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-734">**Spell checking improvements**</span></span>

<span data-ttu-id="8b6b2-735">WPF'deki yazım denetleyicisi, yazım denetimi ek dilleri için işletim sistemi desteğinden yararlanmak için Windows 8.1 ve sonraki sürümlerde güncelleştirildi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-735">The spell checker in WPF has been updated on Windows 8.1 and later versions to leverage operating system support for spell-checking additional languages.</span></span>  <span data-ttu-id="8b6b2-736">Windows 8.1'den önce Windows sürümlerinde işlevsellik değişikliği yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-736">There is no change in functionality on Windows versions prior to Windows 8.1.</span></span>

<span data-ttu-id="8b6b2-737">.NET Framework'ün önceki sürümlerinde olduğu <xref:System.Windows.Controls.TextBox> gibi, <xref:System.Windows.Controls.RichTextBox> bir denetim ora bloğunun dili aşağıdaki sırayla bilgi arayarak algılanır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-737">As in previous versions of the .NET Framework, the language for a <xref:System.Windows.Controls.TextBox> control ora <xref:System.Windows.Controls.RichTextBox> block is detected by looking for information in the following order:</span></span>

- <span data-ttu-id="8b6b2-738">`xml:lang`, varsa.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-738">`xml:lang`, if it is present.</span></span>

- <span data-ttu-id="8b6b2-739">Geçerli giriş dili.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-739">Current input language.</span></span>

- <span data-ttu-id="8b6b2-740">Geçerli iş parçacığı kültürü.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-740">Current thread culture.</span></span>

<span data-ttu-id="8b6b2-741">WPF'de dil desteği hakkında daha fazla bilgi için [.NET Framework 4.6.1 özelliklerindeki WPF blog](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)gönderisine bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-741">For more information on language support in WPF, see the [WPF blog post on .NET Framework 4.6.1 features](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).</span></span>

<span data-ttu-id="8b6b2-742">**Kullanıcı başına özel sözlükler için ek destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-742">**Additional support for per-user custom dictionaries**</span></span>

<span data-ttu-id="8b6b2-743">.NET Framework 4.6.1'de WPF, genel olarak kayıtlı özel sözlükleri tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-743">In .NET Framework 4.6.1, WPF recognizes custom dictionaries that are registered globally.</span></span> <span data-ttu-id="8b6b2-744">Bu özellik, bunları denetim başına kaydetme özelliğine ek olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-744">This capability is available in addition to the ability to register them per-control.</span></span>

<span data-ttu-id="8b6b2-745">WPF'nin önceki sürümlerinde, özel sözlükler Dışlanmış Sözcükler i ve Otomatik Düzeltme listelerini tanımadı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-745">In previous versions of WPF, custom dictionaries did not recognize Excluded Words and AutoCorrect lists.</span></span> <span data-ttu-id="8b6b2-746">Bunlar, `%AppData%\Microsoft\Spelling\<language tag>` dizin altına yerleştirilebilen dosyaların kullanımı yoluyla Windows 8.1 ve Windows 10'da desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-746">They are supported on Windows 8.1 and Windows 10 through the use of files that can be placed under the `%AppData%\Microsoft\Spelling\<language tag>` directory.</span></span>  <span data-ttu-id="8b6b2-747">Aşağıdaki kurallar bu dosyalar için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-747">The following rules apply to these files:</span></span>

- <span data-ttu-id="8b6b2-748">Dosyalarda .dic (eklenen sözcükler için), .exc (dışlanmış sözcükler için) veya .acl (Otomatik Düzeltme için) uzantıları olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-748">The files should have extensions of .dic (for added words), .exc (for excluded words), or .acl (for AutoCorrect).</span></span>

- <span data-ttu-id="8b6b2-749">Dosyalar Byte Order Mark (BOM) ile başlayan UTF-16 LE düz metin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-749">The files should be UTF-16 LE plaintext that starts with the Byte Order Mark (BOM).</span></span>

- <span data-ttu-id="8b6b2-750">Her satır bir sözcükten (eklenen ve dışlanan sözcük listelerinde) veya sözcükleri dikey çubukla ("&#124;") (Otomatik Düzeltme sözcük listesinde) ayrılmış otomatik düzeltme çiftinden oluşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-750">Each line should consist of a word (in the added and excluded word lists), or an autocorrect pair with the words separated by a vertical bar ("&#124;") (in the AutoCorrect word list).</span></span>

- <span data-ttu-id="8b6b2-751">Bu dosyalar salt okunur olarak kabul edilir ve sistem tarafından değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-751">These files are considered read-only and are not modified by the system.</span></span>

> [!NOTE]
> <span data-ttu-id="8b6b2-752">Bu yeni dosya biçimleri doğrudan WPF yazım denetimi API'leri tarafından desteklenmez ve uygulamalarda WPF'ye verilen özel sözlükler .lex dosyalarını kullanmaya devam etmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-752">These new file-formats are not directly supported by the WPF spell checking APIs, and the custom dictionaries supplied to WPF in applications should continue to use .lex files.</span></span>

<span data-ttu-id="8b6b2-753">**Örnekler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-753">**Samples**</span></span>

<span data-ttu-id="8b6b2-754">[Microsoft/WPF-Örnekleri](https://github.com/Microsoft/WPF-Samples) GitHub deposunda birkaç WPF örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-754">There are a number of WPF samples on the [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub repository.</span></span> <span data-ttu-id="8b6b2-755">Bize bir çekme isteği göndererek veya bir [GitHub sorunu](https://github.com/Microsoft/WPF-Samples/issues)açarak örneklerimizi geliştirmemize yardımcı olun.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-755">Help us improve our samples by sending us a pull-request or opening a [GitHub issue](https://github.com/Microsoft/WPF-Samples/issues).</span></span>

<span data-ttu-id="8b6b2-756">**DirectX uzantıları**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-756">**DirectX extensions**</span></span>

<span data-ttu-id="8b6b2-757">WPF, DX10 ve Dx11 içeriğiyle birlikte çalışmanızı kolaylaştıran yeni uygulamalar <xref:System.Windows.Interop.D3DImage> sağlayan bir [NuGet paketi](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-757">WPF includes a [NuGet package](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) that provides new implementations of <xref:System.Windows.Interop.D3DImage> that make it easy for you to interoperate with DX10 and Dx11 content.</span></span> <span data-ttu-id="8b6b2-758">Bu paketin kodu açık kaynaklı olmuştur ve [GitHub'da](https://github.com/Microsoft/WPFDXInterop)kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-758">The code for this package has been open sourced and is available [on GitHub](https://github.com/Microsoft/WPFDXInterop).</span></span>

<a name="WWF461" />

### <a name="windows-workflow-foundation-transactions"></a><span data-ttu-id="8b6b2-759">Windows İş Akışı Temeli: İşlemler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-759">Windows Workflow Foundation: Transactions</span></span>

<span data-ttu-id="8b6b2-760">Yöntem <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> artık hareketi tanıtmak için MSDTC dışında dağıtılmış bir işlem yöneticisi kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-760">The <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> method can now use a distributed transaction manager other than MSDTC to promote the transaction.</span></span> <span data-ttu-id="8b6b2-761">Bunu, yeni <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yüke guid işlem organizatörü tanımlayıcısı belirterek yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-761">You do this by specifying a GUID transaction promoter identifier to the  new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload .</span></span> <span data-ttu-id="8b6b2-762">Bu işlem başarılı olursa, işlemin yeteneklerine sınırlamalar yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-762">If this operation is successful, there are limitations placed on the capabilities of the transaction.</span></span> <span data-ttu-id="8b6b2-763">MSDTC olmayan bir işlem organizatörü kaydolduktan sonra, bu <xref:System.Transactions.TransactionPromotionException> yöntemler MSDTC'ye terfi etmeyi gerektirdiğinden aşağıdaki yöntemler bir yöntem atar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-763">Once a non-MSDTC transaction promoter is enlisted, the following methods throw a <xref:System.Transactions.TransactionPromotionException> because these methods require promotion to MSDTC:</span></span>

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

<span data-ttu-id="8b6b2-764">MSDTC olmayan bir işlem organizatörü kaydolduktan sonra, tanımladığı protokoller kullanılarak gelecekteki dayanıklı listments için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-764">Once a non-MSDTC transaction promoter is enlisted, it must be used for future durable enlistments by using protocols that it defines.</span></span> <span data-ttu-id="8b6b2-765">İşlem <xref:System.Guid> organizatörü <xref:System.Transactions.Transaction.PromoterType%2A> özelliği kullanılarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-765">The <xref:System.Guid> of the transaction promoter can be obtained by using the <xref:System.Transactions.Transaction.PromoterType%2A> property.</span></span> <span data-ttu-id="8b6b2-766">Hareket teşvik edildiğinde, hareket organizatörü tanıtılan belirteci temsil eden bir <xref:System.Byte> dizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-766">When the transaction promotes, the transaction promoter provides a <xref:System.Byte> array that represents the promoted token.</span></span> <span data-ttu-id="8b6b2-767">Bir uygulama <xref:System.Transactions.Transaction.GetPromotedToken%2A> yöntemi ile MSDTC olmayan bir hareket için terfi jeton elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-767">An application can obtain the promoted token for a non-MSDTC promoted transaction with the <xref:System.Transactions.Transaction.GetPromotedToken%2A> method.</span></span>

<span data-ttu-id="8b6b2-768">Promosyon işleminin <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> başarıyla tamamlanması için yeni aşırı yüklemenin kullanıcılarının belirli bir çağrı sırasını izlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-768">Users of the new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload must follow a specific call sequence in order for the promotion operation to complete successfully.</span></span> <span data-ttu-id="8b6b2-769">Bu kurallar yöntemin belgelerinde belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-769">These rules are documented in the method's documentation.</span></span>

<a name="Profile461" />

### <a name="profiling"></a><span data-ttu-id="8b6b2-770">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b2-770">Profiling</span></span>

<span data-ttu-id="8b6b2-771">Yönetilmeyen profil oluşturma API'si aşağıdaki gibi geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-771">The unmanaged profiling API has been enhanced as follows:</span></span>

- <span data-ttu-id="8b6b2-772">[ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabiriminde PDB'lere erişmek için daha iyi destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-772">Better support for accessing PDBs in the [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface.</span></span>

  <span data-ttu-id="8b6b2-773">ASP.NET Core'da, derlemelerin Roslyn tarafından hafızalarda derlenmeleri çok daha yaygın hale gelmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-773">In ASP.NET Core, it is becoming much more common for assemblies to be compiled in-memory by Roslyn.</span></span> <span data-ttu-id="8b6b2-774">Profil oluşturma araçları yapan geliştiriciler için bu, geçmişte diskte seri hale getirilen PDB'lerin artık bulunamayacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-774">For developers making profiling tools, this means that PDBs that historically were serialized on disk may no longer be present.</span></span> <span data-ttu-id="8b6b2-775">Profiler araçları genellikle kod kapsamı veya satır satır performans analizi gibi görevler için kodu kaynak satırlarına yeniden eşlemek için PDB'leri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-775">Profiler tools often use PDBs to map code back to source lines for tasks such as code coverage or line-by-line performance analysis.</span></span> <span data-ttu-id="8b6b2-776">[ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) arayüzü şimdi iki yeni yöntem içerir, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) ve [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), bellek PDB verilere erişim ile bu profilci araçları sağlamak için, yeni API'ler kullanarak, bir profilci bir bayt dizisi olarak bellek tep pdb içeriğini elde edebilirsiniz ve sonra işleyebilir veya disk için seri.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-776">The [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface now includes two new methods, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) and [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), to provide these profiler tools with access to the in-memory PDB data, By using the new APIs, a profiler can obtain the contents of an in-memory PDB as a byte array and then process it or serialize it to disk.</span></span>

- <span data-ttu-id="8b6b2-777">ICorProfiler arabirimi ile daha iyi enstrümantasyon.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-777">Better instrumentation with the ICorProfiler interface.</span></span>

  <span data-ttu-id="8b6b2-778">Dinamik enstrümantasyon `ICorProfiler` için API'ler ReJit işlevini kullanan profilciler artık bazı meta verileri değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-778">Profilers that are using the `ICorProfiler` APIs ReJit functionality for dynamic instrumentation can now modify some metadata.</span></span> <span data-ttu-id="8b6b2-779">Daha önce bu tür araçlar herhangi bir zamanda IL enstrüman olabilir, ancak meta veriler yalnızca modül yükleme zamanında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-779">Previously such tools could instrument IL at any time, but metadata could only be modified at module load time.</span></span> <span data-ttu-id="8b6b2-780">IL meta verilere atıfta bulunduğundan, bu yapılabilecek enstrümantasyon türlerini sınırlandırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-780">Because IL refers to metadata, this limited the kinds of instrumentation that could be done.</span></span> <span data-ttu-id="8b6b2-781">Biz ICorProfilerInfo7 ekleyerek bu sınırların bazılarını [kaldırdık::UygulamaMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) yöntemi modül yükleri sonra meta veri düzenlemebir alt `AssemblyRef`kümesi `TypeRef` `TypeSpec`desteklemek `MemberRef` `MemberSpec`için, `UserString` özellikle ekleyerek , , , , , ve kayıtlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-781">We have lifted some of those limits by adding the [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) method to support a subset of metadata edits after the module loads, in particular by adding new `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, and `UserString` records.</span></span> <span data-ttu-id="8b6b2-782">Bu değişiklik, çok daha geniş bir anında enstrümantasyon yelpazesini mümkün kılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-782">This change makes a much broader range of on-the-fly instrumentation possible.</span></span>

<a name="NGEN461" />

### <a name="native-image-generator-ngen-pdbs"></a><span data-ttu-id="8b6b2-783">Yerli Görüntü Jeneratörü (NGEN) PDB'leri</span><span class="sxs-lookup"><span data-stu-id="8b6b2-783">Native Image Generator (NGEN) PDBs</span></span>

<span data-ttu-id="8b6b2-784">Makineler arası olay izleme, müşterilerin Machine A'daki bir programın profilini çıkarmalarına ve Makine B'deki kaynak çizgi eşlemesiyle profil oluşturma verilerine bakmalarını sağlar. kaynaktan yerel eşleme oluşturmak için IL PDB içeren analiz makinesine makine.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-784">Cross-machine event tracing allows customers to profile a program on Machine A and look at the profiling data with source line mapping on Machine B. Using previous versions of the .NET Framework, the user would copy all the modules and native images from the profiled machine to the analysis machine that contains the IL PDB to create the source-to-native mapping.</span></span> <span data-ttu-id="8b6b2-785">Dosyalar telefon uygulamaları gibi nispeten küçük olduğunda bu işlem iyi çalışabilir, ancak dosyalar masaüstü sistemlerinde çok büyük olabilir ve kopyalamak için önemli bir zaman gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-785">While this process may work well when the files are relatively small, such as for phone applications, the files can be very large on desktop systems and require significant time to copy.</span></span>

<span data-ttu-id="8b6b2-786">Ngen PDB'leri ile NGen, IL PDB'ye bağımlı olmadan IL-to-native eşlemi içeren bir PDB oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-786">With Ngen PDBs, NGen can create a PDB that contains the IL-to-native mapping without a dependency on the IL PDB.</span></span> <span data-ttu-id="8b6b2-787">Makineler arası olay izleme senaryomuzda, tek gereken Makine A'dan Makine B'ye oluşturulan yerel görüntü PDB'yi kopyalamak ve IL PDB'nin kaynaktan IL'e eşleğesini ve pdb'nin IL-yerel eşlemasını okumak için [Hata Ayık Arabirim Erişim API'lerini](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-787">In our cross-machine event tracing scenario, all that is needed is to copy the native image PDB that is generated by Machine A to Machine B and to use [Debug Interface Access APIs](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) to read the IL PDB's source-to-IL mapping and the native image PDB's IL-to-native mapping.</span></span> <span data-ttu-id="8b6b2-788">Her iki eşlemenin birleştirilmesi kaynaktan yereleşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-788">Combining both mappings provides a source-to-native mapping.</span></span> <span data-ttu-id="8b6b2-789">Yerel görüntü PDB tüm modüllerden ve yerel görüntülerden çok daha küçük olduğundan, Makine A'dan Makine B'ye kopyalama işlemi çok daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-789">Since the native image PDB is much smaller than all the modules and native images, the process of copying from Machine A to Machine B is much faster.</span></span>

<a name="v46" />

## <a name="whats-new-in-net-2015"></a><span data-ttu-id="8b6b2-790">.NET 2015'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-790">What's new in .NET 2015</span></span>

<span data-ttu-id="8b6b2-791">.NET 2015 .NET Framework 4.6 ve .NET Core'u tanıttı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-791">.NET 2015 introduces the .NET Framework 4.6 and .NET Core.</span></span> <span data-ttu-id="8b6b2-792">Bazı yeni özellikler her ikisi için de geçerlidir ve diğer özellikler .NET Framework 4.6 veya .NET Core'a özgüdir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-792">Some new features apply to both, and other features are specific to .NET Framework 4.6 or .NET Core.</span></span>

- <span data-ttu-id="8b6b2-793">**ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-793">**ASP.NET Core**</span></span>

  <span data-ttu-id="8b6b2-794">.NET 2015, modern bulut tabanlı uygulamalar oluşturmak için yalın bir .NET uygulaması olan ASP.NET Core'u içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-794">.NET 2015 includes ASP.NET Core, which is a lean .NET implementation for building modern cloud-based apps.</span></span> <span data-ttu-id="8b6b2-795">ASP.NET Core modülerdir, böylece yalnızca uygulamanızda gereken özellikleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-795">ASP.NET Core is modular so you can include only those features that are needed in your application.</span></span> <span data-ttu-id="8b6b2-796">IIS'de barındırılabilir veya özel bir işlemle kendi kendine barındırılabilir ve .NET Framework'ün farklı sürümlerine sahip uygulamaları aynı sunucuda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-796">It can be hosted on IIS or self-hosted in a custom process, and you can run apps with different versions of the .NET Framework on the same server.</span></span> <span data-ttu-id="8b6b2-797">Bulut dağıtımı için tasarlanmış yeni bir ortam yapılandırma sistemi içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-797">It includes a new environment configuration system that is designed for cloud deployment.</span></span>

  <span data-ttu-id="8b6b2-798">MVC, Web API ve Web Sayfaları, MVC 6 adı verilen tek bir çerçevede birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-798">MVC, Web API, and Web Pages are unified into a single framework called MVC 6.</span></span> <span data-ttu-id="8b6b2-799">Visual Studio 2015 veya sonraki araçlar aracılığıyla ASP.NET Core uygulamaları oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-799">You build ASP.NET Core apps through tools in Visual Studio 2015 or later.</span></span> <span data-ttu-id="8b6b2-800">Mevcut uygulamalarınız yeni .NET Framework üzerinde çalışacaktır; ancak MVC 6 veya SignalR 3 kullanan bir uygulama oluşturmak için Visual Studio 2015 veya sonraki yıllarda proje sistemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-800">Your existing applications will work on the new .NET Framework; however to build an app that uses MVC 6 or SignalR 3, you must use the project system in Visual Studio 2015 or later.</span></span>

  <span data-ttu-id="8b6b2-801">Bilgi için [ASP.NET Core'a](/aspnet/core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-801">For information, see [ASP.NET Core](/aspnet/core/).</span></span>

- <span data-ttu-id="8b6b2-802">**ASP.NET Güncellemeler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-802">**ASP.NET Updates**</span></span>

  - <span data-ttu-id="8b6b2-803">**Asynchronous Yanıt Yıkama için Görev Tabanlı API**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-803">**Task-based API for Asynchronous Response Flushing**</span></span>

    <span data-ttu-id="8b6b2-804">ASP.NET şimdi asynchronous yanıt yıkama için basit bir <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>görev tabanlı API sağlar, bu yanıtları eşit sizde dil `async/await` desteği kullanarak floş sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-804">ASP.NET now provides a simple task-based API for asynchronous response flushing, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, that allows responses to be flushed asynchronously by using your language's `async/await` support.</span></span>

  - <span data-ttu-id="8b6b2-805">**Model bağlama görev döndürme yöntemlerini destekler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-805">**Model binding supports task-returning methods**</span></span>

    <span data-ttu-id="8b6b2-806">.NET Framework 4.5'te ASP.NET, Web Formları sayfalarında ve kullanıcı denetimlerinde CRUD tabanlı veri işlemlerine genişletilebilir, kod odaklı bir yaklaşım sağlayan Model Bağlama özelliğini ekledi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-806">In the .NET Framework 4.5, ASP.NET added the Model Binding feature that enabled an extensible, code-focused approach to CRUD-based data operations in Web Forms pages and user controls.</span></span> <span data-ttu-id="8b6b2-807">Model Bağlama sistemi <xref:System.Threading.Tasks.Task>artık model bağlama yöntemlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-807">The Model Binding system now supports <xref:System.Threading.Tasks.Task>-returning model binding methods.</span></span> <span data-ttu-id="8b6b2-808">Bu özellik, Web Forms geliştiricilerinin Varlık Çerçevesi de dahil olmak üzere ORM'lerin yeni sürümlerini kullanırken veri bağlama sisteminin kolaylığıyla async'in ölçeklenebilirlik avantajlarını elde etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-808">This feature allows Web Forms developers to get the scalability benefits of async with the ease of the data-binding system when using newer versions of ORMs, including the Entity Framework.</span></span>

    <span data-ttu-id="8b6b2-809">Async modeli bağlama `aspnet:EnableAsyncModelBinding` yapılandırma ayarı tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-809">Async model binding is controlled by the `aspnet:EnableAsyncModelBinding` configuration setting.</span></span>

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    <span data-ttu-id="8b6b2-810">Uygulamalarda hedef .NET Framework 4.6, varsayılan `true`olarak .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-810">On apps the target the .NET Framework 4.6, it defaults to `true`.</span></span> <span data-ttu-id="8b6b2-811">.NET Framework 4.6 üzerinde çalışan ve .NET Framework'ün önceki `false` bir sürümünü hedefleyen uygulamalarda varsayılan olarak bu durum dur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-811">On apps running on the .NET Framework 4.6 that target an earlier version of the .NET Framework, it is `false` by default.</span></span> <span data-ttu-id="8b6b2-812">Yapılandırma ayarını `true`.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-812">It can be enabled by setting the configuration setting to `true`.</span></span>

  - <span data-ttu-id="8b6b2-813">**HTTP/2 Desteği (Windows 10)**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-813">**HTTP/2 Support (Windows 10)**</span></span>

    <span data-ttu-id="8b6b2-814">[HTTP/2,](https://www.wikipedia.org/wiki/HTTP/2) çok daha iyi bağlantı kullanımı (istemci ve sunucu arasında daha az gidiş-dönüş) sağlayan ve kullanıcılar için daha düşük gecikmeli web sayfası yüklemesi sağlayan HTTP protokolünün yeni bir sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-814">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) is a new version of the HTTP protocol that provides much better connection utilization (fewer round-trips between client and server), resulting in lower latency web page loading for users.</span></span>  <span data-ttu-id="8b6b2-815">Web sayfaları (hizmetlerin aksine) http/2'den en çok yararlanan, protokol tek bir deneyimin bir parçası olarak istenen birden çok eser için optimize edildiğinden.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-815">Web pages (as opposed to services) benefit the most from HTTP/2, since the protocol optimizes for multiple artifacts being requested as part of a single experience.</span></span> <span data-ttu-id="8b6b2-816">.NET Framework 4.6'daki ASP.NET http/2 desteği eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-816">HTTP/2 support has been added to ASP.NET in .NET Framework 4.6.</span></span> <span data-ttu-id="8b6b2-817">Ağ işlevi birden çok katmanda olduğundan, HTTP/2'yi etkinleştirmek için Windows' da, IIS' de ve ASP.NET'da yeni özellikler gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-817">Because networking functionality exists at multiple layers, new features were required in Windows, in IIS, and in ASP.NET to enable HTTP/2.</span></span> <span data-ttu-id="8b6b2-818">ASP.NET ile HTTP/2'yi kullanmak için Windows 10'da çalışıyor olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-818">You must be running on Windows 10 to use HTTP/2 with ASP.NET.</span></span>

    <span data-ttu-id="8b6b2-819">HTTP/2, <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API'yi kullanan Windows 10 Evrensel Windows Platformu (UWP) uygulamaları için de desteklenir ve varsayılan olarak açık ta.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-819">HTTP/2 is also supported and on by default for Windows 10 Universal Windows Platform (UWP) apps that use the <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.</span></span>

    <span data-ttu-id="8b6b2-820">ASP.NET uygulamalarda [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) özelliğini kullanmanın bir yolunu sağlamak için, iki <xref:System.Web.HttpResponse.PushPromise%28System.String%29> aşırı <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>yükleme içeren yeni <xref:System.Web.HttpResponse> bir yöntem sınıfa eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-820">In order to provide a way to use the [PUSH_PROMISE](https://http2.github.io/http2-spec/#PUSH_PROMISE) feature in ASP.NET applications, a new method with two overloads, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> and <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, has been added to the <xref:System.Web.HttpResponse> class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8b6b2-821">ASP.NET Core HTTP/2'yi desteklerken, PUSH PROMISE özelliği için destek henüz eklenmedi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-821">While ASP.NET Core supports HTTP/2, support for the PUSH PROMISE feature has not yet been added.</span></span>

    <span data-ttu-id="8b6b2-822">Tarayıcı ve web sunucusu (Windows'da IIS) tüm işi yapmak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-822">The browser and the web server (IIS on Windows) do all the work.</span></span> <span data-ttu-id="8b6b2-823">Kullanıcılarınız için herhangi bir ağır kaldırma yapmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-823">You don't have to do any heavy-lifting for your users.</span></span>

    <span data-ttu-id="8b6b2-824">Büyük tarayıcıların çoğu [HTTP/2'yi destekler,](https://www.wikipedia.org/wiki/HTTP/2)bu nedenle sunucunuz destekliyorsa kullanıcılarınızın HTTP/2 desteğinden yararlanmaolasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-824">Most of the [major browsers support HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), so it's likely that your users will benefit from HTTP/2 support if your server supports it.</span></span>

  - <span data-ttu-id="8b6b2-825">**Belirteç Bağlama Protokolü Desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-825">**Support for the Token Binding Protocol**</span></span>

    <span data-ttu-id="8b6b2-826">Microsoft ve Google, [Token Bağlama Protokolü](https://github.com/TokenBinding/Internet-Drafts)adı verilen kimlik doğrulamasına yönelik yeni bir yaklaşım üzerinde işbirliği içindedir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-826">Microsoft and Google have been collaborating on a new approach to authentication, called the [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span></span> <span data-ttu-id="8b6b2-827">Öncül kimlik doğrulama belirteçleri (tarayıcı önbelleğinde) çalınabilir ve şifrenizi veya başka herhangi bir ayrıcalıklı bilgi gerektirmeden başka güvenli kaynaklara (örneğin, banka hesabınız) erişmek için suçlular tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-827">The premise is that authentication tokens (in your browser cache) can be stolen and used by criminals to access otherwise secure resources (for example, your bank account) without requiring your password or any other privileged knowledge.</span></span> <span data-ttu-id="8b6b2-828">Yeni protokol, bu sorunu azaltmayı amaçlıyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-828">The new protocol aims to mitigate this problem.</span></span>

    <span data-ttu-id="8b6b2-829">Belirteç Bağlama Protokolü, Windows 10'da tarayıcı özelliği olarak uygulanacaktır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-829">The Token Binding Protocol will be implemented in Windows 10 as a browser feature.</span></span> <span data-ttu-id="8b6b2-830">ASP.NET uygulamalar protokole katılır, böylece kimlik doğrulama belirteçleri yasal olarak doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-830">ASP.NET apps will participate in the protocol, so that authentication tokens are validated to be legitimate.</span></span> <span data-ttu-id="8b6b2-831">İstemci ve sunucu uygulamaları protokolü tarafından belirtilen uçlardan uca korumayı kurar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-831">The client and the server implementations establish the end-to-end protection specified by the protocol.</span></span>

  - <span data-ttu-id="8b6b2-832">**Randomize dize karma algoritmaları**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-832">**Randomized string hash algorithms**</span></span>

    <span data-ttu-id="8b6b2-833">.NET Framework 4.5 [randomize dize karma algoritması](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)tanıttı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-833">.NET Framework 4.5 introduced a [randomized string hash algorithm](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span> <span data-ttu-id="8b6b2-834">Ancak, bazı ASP.NET özellikleri kararlı bir karma koduna bağlı olduğu için ASP.NET tarafından desteklenmedi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-834">However, it was not supported by ASP.NET because of some ASP.NET features depended on a stable hash code.</span></span> <span data-ttu-id="8b6b2-835">.NET Framework 4.6'da randomize dize karma algoritmaları artık desteklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-835">In .NET Framework 4.6, randomized string hash algorithms are now supported.</span></span> <span data-ttu-id="8b6b2-836">Bu özelliği etkinleştirmek `aspnet:UseRandomizedStringHashAlgorithm` için config ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-836">To enable this feature, use the `aspnet:UseRandomizedStringHashAlgorithm` config setting.</span></span>

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- <span data-ttu-id="8b6b2-837">**ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-837">**ADO.NET**</span></span>

  <span data-ttu-id="8b6b2-838">ADO .NET artık SQL Server 2016 Topluluk Teknolojisi Önizleme 2'de (CTP2) bulunan Her Zaman Şifrelenmiş özelliğini destekliyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-838">ADO .NET now supports the Always Encrypted feature available in SQL Server 2016 Community Technology Preview 2 (CTP2).</span></span> <span data-ttu-id="8b6b2-839">Her Zaman Şifrelenmiş ile, SQL Server şifreli veriler üzerinde işlem yapabilir ve en iyisi şifreleme anahtarı sunucuda değil, müşterinin güvendiği ortamda uygulamayla birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-839">With Always Encrypted, SQL Server can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer’s trusted environment and not on the server.</span></span> <span data-ttu-id="8b6b2-840">Her zaman Şifrelenmiş müşteri verilerini güvenli hale getirmekte, böylece DBA'ların düz metin verilerine erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-840">Always Encrypted secures customer data so DBAs do not have access to plain text data.</span></span> <span data-ttu-id="8b6b2-841">Verilerin şifrelemesi ve şifre çözmesi, sürücü düzeyinde saydam bir şekilde gerçekleşir ve varolan uygulamalarda yapılması gereken değişiklikleri en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-841">Encryption and decryption of data happens transparently at the driver level, minimizing changes that have to be made to existing applications.</span></span> <span data-ttu-id="8b6b2-842">Ayrıntılar için her [zaman şifrelenmiş (Veritabanı Altyapısı)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) ve [Her Zaman Şifrelenmiş (istemci geliştirme)](/sql/relational-databases/security/encryption/always-encrypted-client-development)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-842">For details, see [Always Encrypted (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) and [Always Encrypted (client development)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span></span>

- <span data-ttu-id="8b6b2-843">**Yönetilen kod için 64 bit JIT Derleyicisi**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-843">**64-bit JIT Compiler for managed code**</span></span>

  <span data-ttu-id="8b6b2-844">.NET Framework 4.6, 64 bit JIT derleyicisinin (orijinal olarak RyuJIT kod adı verilen) yeni bir sürümünü sunar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-844">.NET Framework 4.6 features a new version of the 64-bit JIT compiler (originally code-named RyuJIT).</span></span> <span data-ttu-id="8b6b2-845">Yeni 64 bit derleyici, eski 64 bit JIT derleyicisi üzerinde önemli performans iyileştirmeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-845">The new 64-bit compiler provides significant performance improvements over the older 64-bit JIT compiler.</span></span> <span data-ttu-id="8b6b2-846">Yeni 64 bit derleyici,.NET Framework 4.6'nın üzerinde çalışan 64 bit işlemler için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-846">The new 64-bit compiler is enabled for 64-bit processes running on top of .NET Framework 4.6.</span></span> <span data-ttu-id="8b6b2-847">Uygulamanız 64 bit veya AnyCPU olarak derlenmişse ve 64 bit işletim sistemiyle çalışıyorsa 64 bit işlemle çalışır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-847">Your app will run in a 64-bit process if it is compiled as 64-bit or AnyCPU and is running on a 64-bit operating system.</span></span> <span data-ttu-id="8b6b2-848">Yeni derleyiciye geçişi mümkün olduğunca saydam hale getirmek için özen gösterilmiştir, ancak davranış değişiklikleri mümkündür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-848">While care has been taken to make the transition to the new compiler as transparent as possible, changes in behavior are possible.</span></span>

  <span data-ttu-id="8b6b2-849">Yeni 64 bit JIT derleyicisi, <xref:System.Numerics> iyi performans iyileştirmeleri sağlayabilen ad alanında SIMD özellikli tiplerle birleştiğinde donanım SIMD hızlandırma özellikleri de içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-849">The new 64-bit JIT compiler also includes hardware SIMD acceleration features when coupled with SIMD-enabled types in the <xref:System.Numerics> namespace, which can yield good performance improvements.</span></span>

- <span data-ttu-id="8b6b2-850">**Montaj yükleyici iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-850">**Assembly loader improvements**</span></span>

  <span data-ttu-id="8b6b2-851">Montaj yükleyicisi, ilgili NGEN görüntüsü yüklendikten sonra IL derlemelerini boşaltarak belleği daha verimli kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-851">The assembly loader now uses memory more efficiently by unloading IL assemblies after a corresponding NGEN image is loaded.</span></span> <span data-ttu-id="8b6b2-852">Bu değişiklik, özellikle büyük 32 bit uygulamalar (Visual Studio gibi) için yararlı olan sanal belleği azaltır ve aynı zamanda fiziksel bellek tasarrufu sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-852">This change decreases virtual memory, which is particularly beneficial for large 32-bit apps (such as Visual Studio), and also saves physical memory.</span></span>

- <span data-ttu-id="8b6b2-853">**Taban sınıf kitaplığı değişiklikleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-853">**Base class library changes**</span></span>

  <span data-ttu-id="8b6b2-854">Önemli senaryoları etkinleştirmek için .NET Framework 4.6'ya birçok yeni API eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-854">Many new APIs have been added around to .NET Framework 4.6 to enable key scenarios.</span></span> <span data-ttu-id="8b6b2-855">Bunlar aşağıdaki değişiklikleri ve eklemeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-855">These include the following changes and additions:</span></span>

  - <span data-ttu-id="8b6b2-856">**IReadOnlyCollection\<T> uygulamaları**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-856">**IReadOnlyCollection\<T> implementations**</span></span>

    <span data-ttu-id="8b6b2-857">Ek koleksiyonlar <xref:System.Collections.Generic.IReadOnlyCollection%601> gibi <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Generic.Stack%601>uygulamak ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-857">Additional collections implement <xref:System.Collections.Generic.IReadOnlyCollection%601> such as <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601>.</span></span>

  - <span data-ttu-id="8b6b2-858">**CultureInfo.CurrentKültür ve KültürInfo.CurrentUICulture**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-858">**CultureInfo.CurrentCulture and CultureInfo.CurrentUICulture**</span></span>

    <span data-ttu-id="8b6b2-859"><xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri artık salt okunur değil, okuma-yazma vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-859">The <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties are now read-write rather than read-only.</span></span> <span data-ttu-id="8b6b2-860">Bu özelliklere yeni <xref:System.Globalization.CultureInfo> bir nesne atarsanız, `Thread.CurrentThread.CurrentCulture` özellik tarafından tanımlanan geçerli iş parçacığı kültürü ve `Thread.CurrentThread.CurrentUICulture` özellikler tarafından tanımlanan geçerli UI iş parçacığı kültürü de değişir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-860">If you assign a new <xref:System.Globalization.CultureInfo> object to these properties, the current thread culture defined by the `Thread.CurrentThread.CurrentCulture` property and the current UI thread culture defined by the `Thread.CurrentThread.CurrentUICulture` properties also change.</span></span>

  - <span data-ttu-id="8b6b2-861">**Çöp toplama geliştirmeleri (GC)**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-861">**Enhancements to garbage collection (GC)**</span></span>

    <span data-ttu-id="8b6b2-862">Sınıf <xref:System.GC> şimdi <xref:System.GC.TryStartNoGCRegion%2A> içerir <xref:System.GC.EndNoGCRegion%2A> ve kritik bir yol yürütülmesi sırasında çöp toplama izin vermeizni yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-862">The <xref:System.GC> class now includes <xref:System.GC.TryStartNoGCRegion%2A> and <xref:System.GC.EndNoGCRegion%2A> methods that allow you to disallow garbage collection during the execution of a critical path.</span></span>

    <span data-ttu-id="8b6b2-863"><xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> Yöntemin yeni bir aşırı hem küçük nesne yığını ve büyük nesne yığını süpürüldü ve sıkıştırılmış veya yalnızca süpürüldü olup olmadığını kontrol etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-863">A new overload of the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> method allows you to control whether both the small object heap and the large object heap are swept and compacted or swept only.</span></span>

  - <span data-ttu-id="8b6b2-864">**SIMD özellikli türleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-864">**SIMD-enabled types**</span></span>

    <span data-ttu-id="8b6b2-865">Ad <xref:System.Numerics> alanı artık SIMD özellikli bir dizi tür <xref:System.Numerics.Matrix3x2>içerir, <xref:System.Numerics.Quaternion> <xref:System.Numerics.Vector2>gibi <xref:System.Numerics.Vector3>, <xref:System.Numerics.Vector4>, <xref:System.Numerics.Matrix4x4> <xref:System.Numerics.Plane>, , , , ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-865">The <xref:System.Numerics> namespace now includes a number of SIMD-enabled types, such as <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4>.</span></span>

    <span data-ttu-id="8b6b2-866">Yeni 64 bit JIT derleyicisi donanım SIMD hızlandırma özellikleri de içerdiğinden, yeni 64 bit JIT derleyicisi ile SIMD özellikli türleri kullanırken özellikle önemli performans iyileştirmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-866">Because the new 64-bit JIT compiler also includes hardware SIMD acceleration features, there are especially significant performance improvements when using the SIMD-enabled types with the new 64-bit JIT compiler.</span></span>

  - <span data-ttu-id="8b6b2-867">**Şifreleme güncellemeleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-867">**Cryptography updates**</span></span>

    <span data-ttu-id="8b6b2-868">[API, Windows CNG şifreleme API'lerini](/windows/desktop/SecCNG/cng-reference)destekleyecek şekilde güncelleştiriliyor. <xref:System.Security.Cryptography?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b6b2-868">The <xref:System.Security.Cryptography?displayProperty=nameWithType> API is being updated to support the [Windows CNG cryptography APIs](/windows/desktop/SecCNG/cng-reference).</span></span> <span data-ttu-id="8b6b2-869">.NET Framework'ün önceki sürümleri, uygulamanın temeli olarak [tamamen Windows Şifreleme API'lerinin önceki](/windows/desktop/SecCrypto/cryptography-portal) bir sürümüne <xref:System.Security.Cryptography?displayProperty=nameWithType> dayanıyordu.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-869">Previous versions of the .NET Framework have relied entirely on an [earlier version of the Windows Cryptography APIs](/windows/desktop/SecCrypto/cryptography-portal) as the basis for the <xref:System.Security.Cryptography?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="8b6b2-870">Belirli uygulama kategorileri için önemli olan modern [şifreleme algoritmalarını](/windows/desktop/SecCNG/cng-features#suite-b-support)desteklediği için CNG API'yi desteklemek için talepler aldık.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-870">We have had requests to support the CNG API, since it supports [modern cryptography algorithms](/windows/desktop/SecCNG/cng-features#suite-b-support), which are important for certain categories of apps.</span></span>

    <span data-ttu-id="8b6b2-871">.NET Framework 4.6, Windows CNG şifreleme API'lerini desteklemek için aşağıdaki yeni geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-871">.NET Framework 4.6 includes the following new enhancements to support the Windows CNG cryptography APIs:</span></span>

    - <span data-ttu-id="8b6b2-872">X509 Sertifikaları için bir dizi `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` uzatma `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`yöntemi ve mümkün olduğunda CAPI tabanlı bir uygulama yerine CNG tabanlı bir uygulama döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-872">A set of extension methods for X509 Certificates, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` and `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, that return a CNG-based implementation rather than a CAPI-based implementation when possible.</span></span> <span data-ttu-id="8b6b2-873">(Bazı akıllı kartlar, vb, hala CAPI gerektirir ve API'ler geri dönüş işlemek).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-873">(Some smartcards, etc., still require CAPI, and the APIs handle the fallback).</span></span>

    - <span data-ttu-id="8b6b2-874">RSA algoritmasının CNG uygulamasını sağlayan <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> sınıf.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-874">The <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> class, which provides a CNG implementation of the RSA algorithm.</span></span>

    - <span data-ttu-id="8b6b2-875">Yaygın eylemlerin artık döküm gerektirmemesi için RSA API'deki geliştirmeler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-875">Enhancements to the RSA API so that common actions no longer require casting.</span></span> <span data-ttu-id="8b6b2-876">Örneğin, bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nesneyi kullanarak verileri şifrelemek, .NET Framework'ün önceki sürümlerinde aşağıdaki gibi kod gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-876">For example, encrypting data using an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> object requires code like the following in previous versions of the .NET Framework.</span></span>

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      <span data-ttu-id="8b6b2-877">.NET Framework 4.6'da yeni şifreleme API'lerini kullanan kod, dökümü önlemek için aşağıdaki gibi yeniden yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-877">Code that uses the new cryptography APIs in .NET Framework 4.6 can be rewritten as follows to avoid the cast.</span></span>

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - <span data-ttu-id="8b6b2-878">**Tarihleri ve saatleri Unix zamanına veya unix saatine dönüştürme desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-878">**Support for converting dates and times to or from Unix time**</span></span>

    <span data-ttu-id="8b6b2-879">Tarih ve saat değerlerinin <xref:System.DateTimeOffset> Unix zamanına veya Unix zamanına dönüştürülmesini desteklemek için yapıya aşağıdaki yeni yöntemler eklendi:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-879">The following new methods have been added to the <xref:System.DateTimeOffset> structure to support converting date and time values to or from Unix time:</span></span>

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - <span data-ttu-id="8b6b2-880">**Uyumluluk anahtarları**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-880">**Compatibility switches**</span></span>

    <span data-ttu-id="8b6b2-881">Sınıf, <xref:System.AppContext> kitaplık yazarlarının kullanıcıları için yeni işlevler için tek tip bir devre dışı bırakma mekanizması sağlamalarını sağlayan yeni bir uyumluluk özelliği ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-881">The <xref:System.AppContext> class adds a new compatibility feature that enables library writers to provide a uniform opt-out mechanism for new functionality for their users.</span></span> <span data-ttu-id="8b6b2-882">Bir opt-out isteğini iletmek için bileşenler arasında gevşek bir leştirilmiş bir sözleşme kurar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-882">It establishes a loosely coupled contract between components in order to communicate an opt-out request.</span></span> <span data-ttu-id="8b6b2-883">Varolan işlevde değişiklik yapıldığında bu özellik genellikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-883">This capability is typically important when a change is made to existing functionality.</span></span> <span data-ttu-id="8b6b2-884">Tersine, yeni işlevler için zaten örtülü bir opt-in vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-884">Conversely, there is already an implicit opt-in for new functionality.</span></span>

    <span data-ttu-id="8b6b2-885">Ile, <xref:System.AppContext>kitaplıklar tanımlamak ve uyumluluk anahtarları ortaya çıkarır, onlara bağlı kod kitaplık davranışını etkileyecek şekilde bu anahtarları ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-885">With <xref:System.AppContext>, libraries define and expose compatibility switches, while code that depends on them can set those switches to affect the library behavior.</span></span> <span data-ttu-id="8b6b2-886">Varsayılan olarak, kitaplıklar yeni işlevselliği sağlar ve yalnızca anahtar ayarlanırsa onu değiştirirler (diğer bir şekilde önceki işlevselliği sağlarlar).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-886">By default, libraries provide the new functionality, and they only alter it (that is, they provide the previous functionality) if the switch is set.</span></span>

    <span data-ttu-id="8b6b2-887">Bir uygulama (veya kitaplık), bağımlı kitaplığın tanımladığı bir <xref:System.Boolean> anahtarın (her zaman bir değer olan) değerini bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-887">An application (or a library) can declare the value of a switch (which is always a <xref:System.Boolean> value) that a dependent library defines.</span></span> <span data-ttu-id="8b6b2-888">Anahtar her zaman `false`örtülüdür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-888">The switch is always implicitly `false`.</span></span> <span data-ttu-id="8b6b2-889">Anahtarı etkinleştirmek `true` için ayarlama.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-889">Setting the switch to `true` enables it.</span></span> <span data-ttu-id="8b6b2-890">Anahtarı açıkça yeni `false` davranış sağlamak için ayarlamak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-890">Explicitly setting the switch to `false` provides the new behavior.</span></span>

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    <span data-ttu-id="8b6b2-891">Kitaplık, bir tüketicinin anahtarın değerini beyan edip olmadığını kontrol etmeli ve ardından uygun şekilde hareket etmelidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-891">The library must check if a consumer has declared the value of the switch and then appropriately act on it.</span></span>

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

    <span data-ttu-id="8b6b2-892">Bir kitaplık tarafından ortaya çıkarılan resmi bir sözleşme olduğundan, anahtarlar için tutarlı bir biçim kullanmak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-892">It's beneficial to use a consistent format for switches, since they are a formal contract exposed by a library.</span></span> <span data-ttu-id="8b6b2-893">Aşağıdaki iki açık biçimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-893">The following are two obvious formats.</span></span>

    - <span data-ttu-id="8b6b2-894">*Değiştir*. *ad alanı*. *anahtar adı*</span><span class="sxs-lookup"><span data-stu-id="8b6b2-894">*Switch*.*namespace*.*switchname*</span></span>

    - <span data-ttu-id="8b6b2-895">*Değiştir*. *kütüphane*. *anahtar adı*</span><span class="sxs-lookup"><span data-stu-id="8b6b2-895">*Switch*.*library*.*switchname*</span></span>

  - <span data-ttu-id="8b6b2-896">**Görev tabanlı eşsenkronize desendeki değişiklikler (TAP)**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-896">**Changes to the task-based asynchronous pattern (TAP)**</span></span>

    <span data-ttu-id="8b6b2-897">.NET Framework 4.6'yı hedefleyen <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> uygulamalar için ve nesneler çağrı iş parçacığının kültür ve ui kültürünü devralır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-897">For apps that target the .NET Framework 4.6, <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects inherit the culture and UI culture of the calling thread.</span></span> <span data-ttu-id="8b6b2-898">.NET Framework'ün önceki sürümlerini hedefleyen veya .NET Framework'ün belirli bir sürümünü hedeflemeyen uygulamaların davranışı etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-898">The behavior of apps that target previous versions of the .NET Framework, or that do not target a specific version of the .NET Framework, is unaffected.</span></span> <span data-ttu-id="8b6b2-899">Daha fazla bilgi için sınıf konusunun "Kültür ve görev tabanlı <xref:System.Globalization.CultureInfo> eşzamanlı işlemler" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-899">For more information, see the "Culture and task-based asynchronous operations" section of the <xref:System.Globalization.CultureInfo> class topic.</span></span>

    <span data-ttu-id="8b6b2-900">Sınıf, <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> `async` yöntem gibi belirli bir eşzamanlı denetim akışına yerel ortam verilerini temsil etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-900">The <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> class allows you to represent ambient data that is local to a given asynchronous control flow, such as an `async` method.</span></span> <span data-ttu-id="8b6b2-901">Verileri iş parçacıkları arasında kalıcı hale getirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-901">It can be used to persist data across threads.</span></span> <span data-ttu-id="8b6b2-902">Ayrıca, <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> ortam verileri ne zaman değiştirilse, özellik açıkça değiştirildi, ya da iş parçacığı bir bağlam geçişiyle karşılaştığından bildirilen bir geri arama yöntemi de tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-902">You can also define a callback method that is notified whenever the ambient data changes either because the <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> property was explicitly changed, or because the thread encountered a context transition.</span></span>

    <span data-ttu-id="8b6b2-903">Tamamlanan görevleri <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>belirli <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>bir <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>durumda döndürmek için görev tabanlı eşsenkronize desene (TAP) üç kolaylık yöntemi eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-903">Three convenience methods, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, have been added to the task-based asynchronous pattern (TAP) to return completed tasks in a particular state.</span></span>

    <span data-ttu-id="8b6b2-904">Sınıf <xref:System.IO.Pipes.NamedPipeClientStream> şimdi yeni <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>ile asynchronous iletişim destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-904">The <xref:System.IO.Pipes.NamedPipeClientStream> class now supports asynchronous communication with its new <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span></span> <span data-ttu-id="8b6b2-905">Yöntem.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-905">method.</span></span>

  - <span data-ttu-id="8b6b2-906">**EventSource artık Olay günlüğüne yazmayı destekler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-906">**EventSource now supports writing to the Event log**</span></span>

    <span data-ttu-id="8b6b2-907">Artık <xref:System.Diagnostics.Tracing.EventSource> sınıfı, makinede oluşturulan mevcut ETW oturumlarına ek olarak, olay günlüğüne yönetim veya operasyonel iletileri günlüğe kaydetmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-907">You now can use the <xref:System.Diagnostics.Tracing.EventSource> class to log administrative or operational messages to the event log, in addition to any existing ETW sessions created on the machine.</span></span> <span data-ttu-id="8b6b2-908">Geçmişte, bu işlevsellik için Microsoft.Diagnostics.Tracing.EventSource NuGet paketini kullanmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-908">In the past, you had to use the Microsoft.Diagnostics.Tracing.EventSource NuGet package for this functionality.</span></span> <span data-ttu-id="8b6b2-909">Bu işlevsellik artık yerleşik .NET Framework 4.6'dır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-909">This functionality is now built-into .NET Framework 4.6.</span></span>

    <span data-ttu-id="8b6b2-910">Hem NuGet paketi hem de .NET Framework 4.6 aşağıdaki özelliklerle güncellenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-910">Both the NuGet package and .NET Framework 4.6 have been updated with the following features:</span></span>

    - <span data-ttu-id="8b6b2-911">**Dinamik olaylar**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-911">**Dynamic events**</span></span>

      <span data-ttu-id="8b6b2-912">Olay yöntemleri oluşturmadan "anında" tanımlanan olaylara izin verir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-912">Allows events defined "on the fly" without creating event methods.</span></span>

    - <span data-ttu-id="8b6b2-913">**Zengin yükler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-913">**Rich payloads**</span></span>

      <span data-ttu-id="8b6b2-914">Özel olarak atfedilen sınıfların ve dizilerin yanı sıra ilkel türlerin yük olarak geçirilmesine izin verir</span><span class="sxs-lookup"><span data-stu-id="8b6b2-914">Allows specially attributed classes and arrays as well as primitive types to be passed as a payload</span></span>

    - <span data-ttu-id="8b6b2-915">**Etkinlik izleme**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-915">**Activity tracking**</span></span>

      <span data-ttu-id="8b6b2-916">Tüm şu anda etkin olan etkinlikleri temsil eden bir kimlikle aralarındaki olayları etiketlemek için Başlat ve Durdur olaylarının başlatılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-916">Causes Start and Stop events to tag events between them with an ID that represents all currently active activities.</span></span>

    <span data-ttu-id="8b6b2-917">Bu özellikleri desteklemek için, <xref:System.Diagnostics.Tracing.EventSource.Write%2A> aşırı yüklenen yöntem <xref:System.Diagnostics.Tracing.EventSource> sınıfa eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-917">To support these features, the overloaded <xref:System.Diagnostics.Tracing.EventSource.Write%2A> method has been added to the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="8b6b2-918">**Windows Presentation Foundation (WPF)**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-918">**Windows Presentation Foundation (WPF)**</span></span>

  - <span data-ttu-id="8b6b2-919">**HDPI iyileştirmeler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-919">**HDPI improvements**</span></span>

    <span data-ttu-id="8b6b2-920">WPF'de HDPI desteği artık .NET Framework 4.6'da daha iyi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-920">HDPI support in WPF is now better in the .NET Framework 4.6.</span></span> <span data-ttu-id="8b6b2-921">Kenarlıklı denetimlerde kırpma örneklerini azaltmak için düzen yuvarlamada değişiklikler yapıldı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-921">Changes have been made to layout rounding to reduce instances of clipping in controls with borders.</span></span> <span data-ttu-id="8b6b2-922">Varsayılan olarak, bu özellik yalnızca <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET 4.6 olarak ayarlanmışsa etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-922">By default, this feature is enabled only if your <xref:System.Runtime.Versioning.TargetFrameworkAttribute> is set to .NET 4.6.</span></span>  <span data-ttu-id="8b6b2-923">Çerçevenin önceki sürümlerini hedefleyen ancak .NET Framework 4.6 üzerinde çalışan uygulamalar, app.config dosyasının [ \<çalışma süresi>](../configure-apps/file-schema/runtime/runtime-element.md) bölümüne aşağıdaki satırı ekleyerek yeni davranışı seçebilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-923">Applications that target earlier versions of the framework but are running on the .NET Framework 4.6 can opt in to the new behavior by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config file:</span></span>

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    <span data-ttu-id="8b6b2-924">Farklı DPI ayarlarına (Multi-DPI kurulumu) sahip birden fazla monitörü saran WPF pencereleri artık tamamen karartılmış bölgeler olmadan işleniyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-924">WPF windows straddling multiple monitors with different DPI settings (Multi-DPI setup) are now completely rendered without blacked-out regions.</span></span> <span data-ttu-id="8b6b2-925">Bu yeni davranışı devre dışı bırakmak için `<appSettings>` app.config dosyasının bölümüne aşağıdaki satırı ekleyerek bu davranışı devre dışı bırakmak:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-925">You can opt out of this behavior by adding the following line to the `<appSettings>` section of the app.config file to disable this new behavior:</span></span>

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <span data-ttu-id="8b6b2-926">DPI ayarına göre sağ imlecin otomatik olarak <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>yüklenmesi için destek eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-926">Support for automatically loading the right cursor based on DPI setting has been added to  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="8b6b2-927">**Dokunma kiyidir daha iyidir**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-927">**Touch is better**</span></span>

    <span data-ttu-id="8b6b2-928">[Connect'in](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) ,.NET Framework 4.6'da öngörülemeyen davranışlar ürettiğine ilişkin müşteri raporları ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-928">Customer reports on [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) that touch produces unpredictable behavior have been addressed in the .NET Framework 4.6.</span></span> <span data-ttu-id="8b6b2-929">Windows Mağazası uygulamaları ve WPF uygulamaları için çift dokunma eşiği artık Windows 8.1 ve üzeri için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-929">The double tap threshold for Windows Store applications and WPF applications is now the same in Windows 8.1 and above.</span></span>

  - <span data-ttu-id="8b6b2-930">**Saydam alt pencere desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-930">**Transparent child window support**</span></span>

    <span data-ttu-id="8b6b2-931">.NET Framework 4.6'daki WPF, Windows 8.1 ve üzeri saydam alt pencereleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-931">WPF in the .NET Framework 4.6 supports transparent child windows in Windows 8.1 and above.</span></span> <span data-ttu-id="8b6b2-932">Bu, üst düzey pencerelerinizde dikdörtgen olmayan ve saydam alt pencereler oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-932">This allows you to create non-rectangular and transparent child windows in your top-level windows.</span></span> <span data-ttu-id="8b6b2-933">Özelliği `true`' ne ayarlayarak <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> bu özelliği etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-933">You can enable this feature by setting the <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> property to `true`.</span></span>

- <span data-ttu-id="8b6b2-934">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-934">**Windows Communication Foundation (WCF)**</span></span>

  - <span data-ttu-id="8b6b2-935">**SSL desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-935">**SSL support**</span></span>

    <span data-ttu-id="8b6b2-936">WCF, artık Aktarım güvenliği ve müşteri kimlik doğrulaması ile NetTcp kullanırken SSL 3.0 ve TLS 1.0'a ek olarak SSL 1.1 ve TLS 1.2 sürümünü desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-936">WCF now supports SSL version TLS 1.1 and TLS 1.2, in addition to SSL 3.0 and TLS 1.0, when using NetTcp with transport security and client authentication.</span></span> <span data-ttu-id="8b6b2-937">Artık hangi protokolün kullanılacağını seçmek veya eski daha az güvenli protokolleri devre dışı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-937">It is now possible to select which protocol to use, or to disable old lesser secure protocols.</span></span> <span data-ttu-id="8b6b2-938">Bu özellik ayarı <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> veya bir yapılandırma dosyasına aşağıdaki ekleyerek yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-938">This can be done either by setting the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> property or by adding the following to a configuration file.</span></span>

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

  - <span data-ttu-id="8b6b2-939">**Farklı HTTP bağlantılarını kullanarak ileti gönderme**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-939">**Sending messages using different HTTP connections**</span></span>

    <span data-ttu-id="8b6b2-940">WCF artık kullanıcıların bazı iletilerin temeldeki farklı HTTP bağlantıları kullanılarak gönderilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-940">WCF now allows users to ensure certain messages are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="8b6b2-941">Bunu yapmak için iki yol vardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-941">There are two ways to do this:</span></span>

    - <span data-ttu-id="8b6b2-942">**Bağlantı grubu adı öneki kullanma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-942">**Using a connection group name prefix**</span></span>

      <span data-ttu-id="8b6b2-943">Kullanıcılar, WCF'nin bağlantı grubu adı için önek olarak kullanacağı bir dize belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-943">Users can specify a string that WCF will use as a prefix for the connection group name.</span></span> <span data-ttu-id="8b6b2-944">Farklı öneklere sahip iki ileti, temeldeki farklı HTTP bağlantıları kullanılarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-944">Two messages with different prefixes are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="8b6b2-945">İletinin <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> özelliğine bir anahtar/değer çifti ekleyerek önek ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-945">You set the prefix by adding a key/value pair to the message's <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8b6b2-946">Anahtar "HttpTransportConnectionGroupNamePrefix"; değeri istenilen önektir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-946">The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.</span></span>

    - <span data-ttu-id="8b6b2-947">**Farklı kanal fabrikalarını kullanma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-947">**Using different channel factories**</span></span>

      <span data-ttu-id="8b6b2-948">Kullanıcılar ayrıca, farklı kanal fabrikaları tarafından oluşturulan kanallar kullanılarak gönderilen iletilerin farklı temel HTTP bağlantılarını kullanmasını sağlayan bir özelliği de etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-948">Users can also enable a feature that ensures that messages sent using channels created by different channel factories will use different underlying HTTP connections.</span></span> <span data-ttu-id="8b6b2-949">Bu özelliği etkinleştirmek için, `appSetting` `true`kullanıcıların aşağıdakileri ayarlamaları gerekir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-949">To enable this feature, users must set the following `appSetting` to `true`:</span></span>

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- <span data-ttu-id="8b6b2-950">**Windows İş Akışı Vakfı (WWF)**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-950">**Windows Workflow Foundation (WWF)**</span></span>

  <span data-ttu-id="8b6b2-951">Artık, isteği zamanlamadan önce olağanüstü bir "protokol dışı" yer imi olduğunda, bir iş akışı hizmetinin sıra dışı bir işlem isteğine tutunacağı saniye sayısını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-951">You can now specify the number of seconds a workflow service will hold on to an out-of-order operation request when there is an outstanding "non-protocol" bookmark before timing out the request.</span></span> <span data-ttu-id="8b6b2-952">"Protokol dışı" yer imi, olağanüstü Alma etkinlikleriile ilgili olmayan bir yer imidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-952">A "non-protocol" bookmark is a bookmark that is not related to outstanding Receive activities.</span></span> <span data-ttu-id="8b6b2-953">Bazı etkinlikler, uygulamaları içinde protokol dışı yer imleri oluşturur, bu nedenle protokol dışı bir yer imi olduğu açık olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-953">Some activities create non-protocol bookmarks within their implementation, so it may not be obvious that a non-protocol bookmark exists.</span></span> <span data-ttu-id="8b6b2-954">Bunlar arasında Durum ve Seç yer alır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-954">These include State and Pick.</span></span> <span data-ttu-id="8b6b2-955">Bu nedenle, bir durum makinesiyle uygulanan veya bir Çekme etkinliği içeren bir iş akışı hizmetiniz varsa, büyük olasılıkla protokol dışı yer imleri olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-955">So if you have a workflow service implemented with a state machine or containing a Pick activity, you will most likely have non-protocol bookmarks.</span></span> <span data-ttu-id="8b6b2-956">App.config dosyanızın `appSettings` bölümüne aşağıdaki gibi bir satır ekleyerek aralığı belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-956">You specify the interval by adding a line like the following to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  <span data-ttu-id="8b6b2-957">Varsayılan değer 60 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-957">The default value is 60 seconds.</span></span> <span data-ttu-id="8b6b2-958">0 `value` olarak ayarlanırsa, sıra dışı istekler hemen aşağıdaki gibi görünen metinile bir hata ile reddedilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-958">If `value` is set to 0, out-of-order requests are immediately rejected with a fault with text that looks like this:</span></span>

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  <span data-ttu-id="8b6b2-959">Bu, sıra dışı bir işlem iletisi alınırsa ve protokol dışı yer imleri yoksa aldığınız iletiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-959">This is the same message that you receive if an out-of-order operation message is received and there are no non-protocol bookmarks.</span></span>

  <span data-ttu-id="8b6b2-960">`FilterResumeTimeoutInSeconds` Öğenin değeri sıfır değilse, protokol dışı yer imleri vardır ve zaman aşımı aralığı sona ererse, işlem bir zaman aşımı iletisiyle başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-960">If the value of the `FilterResumeTimeoutInSeconds` element is non-zero, there are non-protocol bookmarks, and the timeout interval expires, the operation fails with a timeout message.</span></span>

- <span data-ttu-id="8b6b2-961">**İşlemler**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-961">**Transactions**</span></span>

  <span data-ttu-id="8b6b2-962">Artık, atılması <xref:System.Transactions.TransactionException> için türetilen bir özel durum neden olan hareket için dağıtılmış hareket tanımlayıcısı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-962">You can now include the distributed transaction identifier for the transaction that has caused an exception derived from <xref:System.Transactions.TransactionException> to be thrown.</span></span> <span data-ttu-id="8b6b2-963">Bunu app.config dosyanızın `appSettings` bölümüne aşağıdaki anahtarı ekleyerek yaparsınız:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-963">You do this by adding the following key to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  <span data-ttu-id="8b6b2-964">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-964">The default value is `false`.</span></span>

- <span data-ttu-id="8b6b2-965">**Ağ Oluşturma**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-965">**Networking**</span></span>

  - <span data-ttu-id="8b6b2-966">**Soket yeniden kullanımı**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-966">**Socket reuse**</span></span>

    <span data-ttu-id="8b6b2-967">Windows 10, giden TCP bağlantıları için yerel bağlantı noktalarını yeniden kullanarak makine kaynaklarını daha iyi kullanan yeni bir yüksek ölçeklenebilirlik ağ algoritması içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-967">Windows 10 includes a new high-scalability networking algorithm that makes better use of machine resources by reusing local ports for outbound TCP connections.</span></span> <span data-ttu-id="8b6b2-968">.NET Framework 4.6 yeni algoritmayı destekleyerek .NET uygulamalarının yeni davranıştan yararlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-968">.NET Framework 4.6 supports the new algorithm, enabling .NET apps to take advantage of the new behavior.</span></span> <span data-ttu-id="8b6b2-969">Windows'un önceki sürümlerinde, yük altındayken bağlantı noktası tükenmesine neden olarak bir hizmetin ölçeklenebilirliğini sınırlandırabilecek yapay bir eşzamanlı bağlantı sınırı (genellikle dinamik bağlantı noktası aralığının varsayılan boyutu olan 16.384) vardı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-969">In previous versions of Windows, there was an artificial concurrent connection limit (typically 16,384, the default size of the dynamic port range), which could limit the scalability of a service by causing port exhaustion when under load.</span></span>

    <span data-ttu-id="8b6b2-970">.NET Framework 4.6'da, eşzamanlı bağlantılardaki 64 KB sınırını etkili bir şekilde kaldıran bağlantı noktasının yeniden kullanılmasını sağlamak için iki API eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-970">In .NET Framework 4.6, two APIs have been added to enable port reuse, which effectively removes the 64 KB limit on concurrent connections:</span></span>

    - <span data-ttu-id="8b6b2-971">Numaralandırma <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> değeri.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-971">The <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> enumeration value.</span></span>

    - <span data-ttu-id="8b6b2-972">Mülk. <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="8b6b2-972">The <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="8b6b2-973">Varsayılan olarak, <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` kayıt `false` defteri `HWRPortReuseOnSocketBind` anahtarının değeri 0x1 olarak ayarlı değilse, özellik.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-973">By default, the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property is `false` unless the `HWRPortReuseOnSocketBind` value of the `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` registry key is set to 0x1.</span></span> <span data-ttu-id="8b6b2-974">HTTP bağlantılarında yerel bağlantı noktasının yeniden <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> kullanılmasını `true`etkinleştirmek için özelliği ' ye göre ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-974">To enable local port reuse on HTTP connections, set the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="8b6b2-975">Bu, yerel bağlantı noktasının yeniden <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest> kullanılmasını sağlayan, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options)yeni bir Windows 10 soketi seçeneğinden gelen ve kullanan tüm Giden TCP soket bağlantılarına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-975">This causes all outgoing TCP socket connections from <xref:System.Net.Http.HttpClient> and <xref:System.Net.HttpWebRequest> to use a new Windows 10 socket option, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), that enables local port reuse.</span></span>

    <span data-ttu-id="8b6b2-976">Yalnızca soketlere ait bir <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> uygulama yazan geliştiriciler, <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> giden soketlerin bağlama sırasında yerel bağlantı noktalarını yeniden kullanması için bir yöntem ararken seçeneği belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-976">Developers writing a sockets-only application can specify the <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> option when calling a method such as <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> so that outbound sockets reuse local ports during binding.</span></span>

  - <span data-ttu-id="8b6b2-977">**Uluslararası alan adları ve PunyCode desteği**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-977">**Support for international domain names and PunyCode**</span></span>

    <span data-ttu-id="8b6b2-978">Uluslararası alan <xref:System.Uri.IdnHost%2A>adlarını ve PunyCode'u daha iyi desteklemek için <xref:System.Uri> sınıfa yeni bir özellik eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-978">A new property, <xref:System.Uri.IdnHost%2A>, has been added to the <xref:System.Uri> class to better support international domain names and PunyCode.</span></span>

- <span data-ttu-id="8b6b2-979">**Windows Forms denetimlerinde yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-979">**Resizing in Windows Forms controls.**</span></span>

  <span data-ttu-id="8b6b2-980">Bu özellik .NET Framework 4.6'da <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> <xref:System.Windows.Forms.ToolStripSplitButton> ve türleri ve <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> bir <xref:System.Drawing.Design.UITypeEditor>.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-980">This feature has been expanded in .NET Framework 4.6 to include the <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.ToolStripSplitButton> types and the rectangle specified by the <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> property used when drawing a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

  <span data-ttu-id="8b6b2-981">Bu bir tercih özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-981">This is an opt-in feature.</span></span> <span data-ttu-id="8b6b2-982">Etkinleştirmek için, `EnableWindowsFormsHighDpiAutoResizing` öğeyi `true` uygulama yapılandırmasında (app.config) dosyaya ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-982">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="8b6b2-983">**Kod sayfası kodlamaları için destek**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-983">**Support for code page encodings**</span></span>

  <span data-ttu-id="8b6b2-984">.NET Core öncelikle Unicode kodlamalarını destekler ve varsayılan olarak kod sayfası kodlamaları için sınırlı destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-984">.NET Core primarily supports the Unicode encodings and by default provides limited support for code page encodings.</span></span> <span data-ttu-id="8b6b2-985">.NET Framework'de bulunan ancak .NET Core'da desteklenmeyen kod sayfası kodlamaları için destek <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> ekleyebilir, kod sayfası kodlamalarını yöntemle kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-985">You can add support for code page encodings available in .NET Framework but unsupported in .NET Core by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b6b2-986">Daha fazla bilgi için bkz. <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-986">For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8b6b2-987">**.NET Yerel**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-987">**.NET Native**</span></span>

  <span data-ttu-id="8b6b2-988">.NET Core'u hedefleyen ve C# veya Visual Basic ile yazılan Windows 10 için Windows uygulamaları, uygulamaları IL yerine yerel koda derleyen yeni bir teknolojiden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-988">Windows apps for Windows 10 that target .NET Core and are written in C# or Visual Basic can take advantage of a new technology that compiles apps to native code rather than IL.</span></span> <span data-ttu-id="8b6b2-989">Daha hızlı başlatma ve yürütme süreleri ile karakterize uygulamalar üretirler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-989">They produce apps characterized by faster startup and execution times.</span></span> <span data-ttu-id="8b6b2-990">Daha fazla bilgi için [bkz.](../net-native/index.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-990">For more information, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span> <span data-ttu-id="8b6b2-991">Hem JIT derlemesi hem de NGEN'den nasıl farklı olduğunu ve bunun kodunuz için ne anlama geldiğini inceleyen [.NET Native'e](../net-native/net-native-and-compilation.md)genel bir bakış için bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-991">For an overview of .NET Native that examines how it differs from both JIT compilation and NGEN and what that means for your code, see [.NET Native and Compilation](../net-native/net-native-and-compilation.md).</span></span>

  <span data-ttu-id="8b6b2-992">Uygulamalarınız Visual Studio 2015 veya sonraki yollarla derlediğinizde varsayılan olarak yerel koda göre derlenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-992">Your apps are compiled to native code by default when you compile them with Visual Studio 2015 or later.</span></span> <span data-ttu-id="8b6b2-993">Daha fazla bilgi için [.NET Native ile Başlarken'e](../net-native/getting-started-with-net-native.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-993">For more information, see [Getting Started with .NET Native](../net-native/getting-started-with-net-native.md).</span></span>

  <span data-ttu-id="8b6b2-994">.NET Yerel uygulamaları hata ayıklamayı desteklemek için, yönetilmeyen hata ayıklama API'sine bir dizi yeni arabirim ve numaralandırma eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-994">To support debugging .NET Native apps, a number of new interfaces and enumerations have been added to the unmanaged debugging API.</span></span> <span data-ttu-id="8b6b2-995">Daha fazla bilgi için [Hata Ayıklama (Yönetilmeyen API Başvurusu)](../unmanaged-api/debugging/index.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-995">For more information, see the [Debugging (Unmanaged API Reference)](../unmanaged-api/debugging/index.md) topic.</span></span>

- <span data-ttu-id="8b6b2-996">**Açık kaynak .NET Framework paketleri**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-996">**Open-source .NET Framework packages**</span></span>

  <span data-ttu-id="8b6b2-997">.NET Core paketleri gibi değişmez koleksiyonlar, [SIMD API'ler](https://www.nuget.org/packages/Microsoft.Bcl.Simd)ve <xref:System.Net.Http> ağ API'leri gibi ad alanında bulunanlar artık [GitHub'da](https://github.com/)açık kaynak paketleri olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-997">.NET Core packages such as the immutable collections, [SIMD APIs](https://www.nuget.org/packages/Microsoft.Bcl.Simd), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open-source packages on [GitHub](https://github.com/).</span></span> <span data-ttu-id="8b6b2-998">Koda erişmek için [GitHub'daki .NET'e](https://github.com/dotnet/runtime)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-998">To access the code, see [.NET on GitHub](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="8b6b2-999">Daha fazla bilgi ve bu paketlere nasıl katkıda bulunabilirsiniz, [github'daki](https://github.com/dotnet/home) [.NET Core ve Open-Source](../get-started/net-core-and-open-source.md), .NET Giriş Sayfası'na bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-999">For more information and how to contribute to these packages, see [.NET Core and Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](https://github.com/dotnet/home).</span></span>

<a name="v452" />

## <a name="whats-new-in-net-framework-452"></a><span data-ttu-id="8b6b2-1000">.NET Framework 4.5.2'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1000">What's new in .NET Framework 4.5.2</span></span>

- <span data-ttu-id="8b6b2-1001">**ASP.NET uygulamalar için yeni API'ler.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1001">**New APIs for ASP.NET apps.**</span></span> <span data-ttu-id="8b6b2-1002">Yeni <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> yöntemler, yanıt istemci uygulamasına atılırken yanıt üstbilgilerini ve durum kodunu incelemenize ve değiştirmenize izin sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1002">The new <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> methods let you inspect and modify response headers and status code as the response is being flushed to the client app.</span></span> <span data-ttu-id="8b6b2-1003">Olaylar <xref:System.Web.HttpApplication.PreSendRequestHeaders> ve <xref:System.Web.HttpApplication.PreSendRequestContent> olaylar yerine bu yöntemleri kullanmayı düşünün; daha verimli ve güvenilirdirler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1003">Consider using these methods instead of the <xref:System.Web.HttpApplication.PreSendRequestHeaders> and <xref:System.Web.HttpApplication.PreSendRequestContent> events; they are more efficient and reliable.</span></span>

  <span data-ttu-id="8b6b2-1004">Yöntem, <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> küçük arka plan çalışma öğeleri zamanlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1004">The <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> method lets you schedule small background work items.</span></span> <span data-ttu-id="8b6b2-1005">ASP.NET bu öğeleri izler ve IIS'nin tüm arka plan çalışma öğeleri tamamlanana kadar alt işlemi aniden sona erdirmesini engeller.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1005">ASP.NET tracks these items and prevents IIS from abruptly terminating the worker process until all background work items have completed.</span></span> <span data-ttu-id="8b6b2-1006">Bu yöntem, ASP.NET yönetilen bir uygulama etki alanının dışında çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1006">This method can't be called outside an ASP.NET managed app domain.</span></span>

  <span data-ttu-id="8b6b2-1007">Yeni <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> özellikler, yanıt üstbilgisinin yazılıp yazılmadığını gösteren Boolean değerlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1007">The new <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> properties return Boolean values that indicate whether the response headers have been written.</span></span> <span data-ttu-id="8b6b2-1008">Bu özellikleri, (üstbilgi yazılmışsa özel <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> durumlar atan) gibi API'lere yapılan çağrıların başarılı olacağından emin olmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1008">You can use these properties to make sure that calls to APIs such as <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (which throw exceptions if the headers have been written) will succeed.</span></span>

- <span data-ttu-id="8b6b2-1009">**Windows Forms denetimlerinde yeniden boyutlandırma.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1009">**Resizing in Windows Forms controls.**</span></span> <span data-ttu-id="8b6b2-1010">Bu özellik genişletildi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1010">This feature has been expanded.</span></span> <span data-ttu-id="8b6b2-1011">Şimdi sistem DPI ayarını, aşağıdaki ek denetimlerin bileşenlerini yeniden boyutlandırmak için kullanabilirsiniz (örneğin, açılan kutulardaki açılır ok):</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1011">You can now use the system DPI setting to resize components of the following additional controls (for example, the drop-down arrow in combo boxes):</span></span>

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  <span data-ttu-id="8b6b2-1012">Bu bir tercih özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1012">This is an opt-in feature.</span></span> <span data-ttu-id="8b6b2-1013">Etkinleştirmek için, `EnableWindowsFormsHighDpiAutoResizing` öğeyi `true` uygulama yapılandırmasında (app.config) dosyaya ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1013">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="8b6b2-1014">**Yeni iş akışı özelliği.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1014">**New workflow feature.**</span></span> <span data-ttu-id="8b6b2-1015"><xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> Yöntemi kullanan (ve bu nedenle <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi uygulayan) bir kaynak yöneticisi aşağıdakileri istemek için yeni <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> yöntemi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1015">A resource manager that's using the <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> method (and therefore implementing the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) can use the new <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> method to request the following:</span></span>

  - <span data-ttu-id="8b6b2-1016">Hareketi bir Microsoft Dağıtılmış Hareket Koordinatörü (MSDTC) hareketine tanıtın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1016">Promote the transaction to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction.</span></span>

  - <span data-ttu-id="8b6b2-1017">Tek <xref:System.Transactions.IPromotableSinglePhaseNotification> faz <xref:System.Transactions.ISinglePhaseNotification>taahhüt destekleyen dayanıklı bir listment ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1017">Replace <xref:System.Transactions.IPromotableSinglePhaseNotification> with an <xref:System.Transactions.ISinglePhaseNotification>, which is a durable enlistment that supports single phase commits.</span></span>

  <span data-ttu-id="8b6b2-1018">Bu, aynı uygulama etki alanı içinde yapılabilir ve promosyongerçekleştirmek için MSDTC ile etkileşim için herhangi bir ekstra yönetilmeyen kod gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1018">This can be done within the same app domain, and doesn't require any extra unmanaged code to interact with MSDTC to perform the promotion.</span></span> <span data-ttu-id="8b6b2-1019">Yeni yöntem, yalnızca teşvik edilebilir listment tarafından <xref:System.Transactions?displayProperty=nameWithType> uygulanan <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` yönteme olağanüstü bir çağrı olduğunda çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1019">The new method can be called only when there's an outstanding call from <xref:System.Transactions?displayProperty=nameWithType> to the <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` method that's implemented by the promotable enlistment.</span></span>

- <span data-ttu-id="8b6b2-1020">**Profil geliştirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1020">**Profiling improvements.**</span></span> <span data-ttu-id="8b6b2-1021">Aşağıdaki yeni yönetilmeyen profil oluşturma API'leri daha sağlam profil oluşturma sağlar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1021">The following new unmanaged profiling APIs provide more robust profiling:</span></span>

  - [<span data-ttu-id="8b6b2-1022">COR_PRF_ASSEMBLY_REFERENCE_INFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1022">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [<span data-ttu-id="8b6b2-1023">COR_PRF_HIGH_MONITOR Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1023">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [<span data-ttu-id="8b6b2-1024">GetAssemblyReferences Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1024">GetAssemblyReferences Method</span></span>](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [<span data-ttu-id="8b6b2-1025">GetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1025">GetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [<span data-ttu-id="8b6b2-1026">SetEventMask2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1026">SetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [<span data-ttu-id="8b6b2-1027">AddAssemblyReference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1027">AddAssemblyReference Method</span></span>](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  <span data-ttu-id="8b6b2-1028">Önceki `ICorProfiler` uygulamalar bağımlı derlemelerin tembel yüklenmesi desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1028">Previous `ICorProfiler` implementations supported lazy loading of dependent assemblies.</span></span> <span data-ttu-id="8b6b2-1029">Yeni profil oluşturma API'leri, profil oluşturucu tarafından enjekte edilen bağımlı derlemelerin uygulama tamamen başlatıldıktan sonra yüklenmek yerine hemen yüklenebilmelerini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1029">The new profiling APIs require dependent assemblies that are injected by the profiler to be loadable immediately, instead of being loaded after the app is fully initialized.</span></span> <span data-ttu-id="8b6b2-1030">Bu değişiklik, varolan `ICorProfiler` API kullanıcılarını etkilemez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1030">This change doesn't affect users of the existing `ICorProfiler` APIs.</span></span>

- <span data-ttu-id="8b6b2-1031">**Hata ayıklama iyileştirmeleri.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1031">**Debugging improvements.**</span></span> <span data-ttu-id="8b6b2-1032">Aşağıdaki yeni yönetilmeyen hata ayıklama API'leri bir profil oluşturucuyla daha iyi tümleştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1032">The following new unmanaged debugging APIs provide better integration with a profiler.</span></span> <span data-ttu-id="8b6b2-1033">Artık profil oluşturucu tarafından eklenen meta verilere ve hata ayıklama yaparken derleyici ReJIT istekleri tarafından üretilen yerel değişkenlere ve koda erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1033">You can now access metadata inserted by the profiler as well as local variables and code produced by compiler ReJIT requests when dump debugging.</span></span>

  - [<span data-ttu-id="8b6b2-1034">SetWriteableMetadataUpdateMode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1034">SetWriteableMetadataUpdateMode Method</span></span>](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [<span data-ttu-id="8b6b2-1035">EnumerateLocalVariablesEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1035">EnumerateLocalVariablesEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [<span data-ttu-id="8b6b2-1036">GetLocalVariableEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1036">GetLocalVariableEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [<span data-ttu-id="8b6b2-1037">GetCodeEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1037">GetCodeEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [<span data-ttu-id="8b6b2-1038">GetActiveReJitRequestILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1038">GetActiveReJitRequestILCode Method</span></span>](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [<span data-ttu-id="8b6b2-1039">GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1039">GetInstrumentedILMap Method</span></span>](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- <span data-ttu-id="8b6b2-1040">**Olay izleme değişiklikleri.**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1040">**Event tracing changes.**</span></span> <span data-ttu-id="8b6b2-1041">.NET Framework 4.5.2, daha büyük bir yüzey alanı için Windows için Olay İzleme (ETW) tabanlı etkinlik izleme işleminin dışında olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1041">.NET Framework 4.5.2 enables out-of-process, Event Tracing for Windows (ETW)-based activity tracing for a larger surface area.</span></span> <span data-ttu-id="8b6b2-1042">Bu, Gelişmiş Güç Yönetimi (APM) satıcılarının, iş parçacığı arasında tek tek istek ve etkinliklerin maliyetlerini doğru bir şekilde izleyen hafif araçlar sağlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1042">This enables Advanced Power Management (APM) vendors to provide lightweight tools that accurately track the costs of individual requests and activities that cross threads.</span></span>  <span data-ttu-id="8b6b2-1043">Bu olaylar yalnızca ETW denetleyicileri etkinleştirildiğinde yükseltilir; bu nedenle, değişiklikler daha önce yazılmış ETW kodunu veya ETW devre dışı ile çalışan kodu etkilemez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1043">These events are raised only when ETW controllers enable them; therefore, the changes don't affect previously written ETW code or code that runs with ETW disabled.</span></span>

- <span data-ttu-id="8b6b2-1044">**Bir işlemin tanıtımı ve dayanıklı bir listeye dönüştürülmesi**</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1044">**Promoting a transaction and converting it to a durable enlistment**</span></span>

  <span data-ttu-id="8b6b2-1045"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>.NET Framework 4.5.2 ve 4.6'ya eklenen yeni bir API'dir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1045"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> is a new API added to .NET Framework 4.5.2 and 4.6:</span></span>

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

  <span data-ttu-id="8b6b2-1046">Yöntem, <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> yönteme yanıt olarak daha önce oluşturulan <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> bir listment tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1046">The method may be used by an enlistment that was previously created by <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> in response to the <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="8b6b2-1047">Bir `System.Transactions` MSDTC işlemine hareketi tanıtmak ve teşvik edilebilir listeyi dayanıklı bir listeye "dönüştürmek" ister.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1047">It asks `System.Transactions` to promote the transaction to an MSDTC transaction and to "convert" the promotable enlistment to a durable enlistment.</span></span> <span data-ttu-id="8b6b2-1048">Bu yöntem başarıyla tamamlandıktan <xref:System.Transactions.IPromotableSinglePhaseNotification> sonra, arabirim artık `System.Transactions`başvurulan olacak ve gelecekteki bildirimler <xref:System.Transactions.ISinglePhaseNotification> sağlanan arabirimde gelecektir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1048">After this method completes successfully, the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface will no longer be referenced by `System.Transactions`, and any future notifications will arrive on the provided <xref:System.Transactions.ISinglePhaseNotification> interface.</span></span> <span data-ttu-id="8b6b2-1049">Söz konusu askere alma, işlem günlüğü ve kurtarmayı destekleyen dayanıklı bir liste görevi almalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1049">The enlistment in question must act as a durable enlistment, supporting transaction logging and recovery.</span></span> <span data-ttu-id="8b6b2-1050">Ayrıntılar <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> için bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1050">Refer to <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> for details.</span></span> <span data-ttu-id="8b6b2-1051">Buna ek olarak, askere <xref:System.Transactions.ISinglePhaseNotification>destek olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1051">In addition, the enlistment must support <xref:System.Transactions.ISinglePhaseNotification>.</span></span>  <span data-ttu-id="8b6b2-1052">Bu yöntem *yalnızca* bir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> aramayı işlerken çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1052">This method can *only* be called while processing an <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="8b6b2-1053">Bu durumda değilse, bir <xref:System.Transactions.TransactionException> özel durum atılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1053">If that is not the case, a <xref:System.Transactions.TransactionException> exception is thrown.</span></span>

<a name="v451" />

## <a name="whats-new-in-net-framework-451"></a><span data-ttu-id="8b6b2-1054">.NET Framework 4.5.1'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1054">What's new in .NET Framework 4.5.1</span></span>

<span data-ttu-id="8b6b2-1055">**Nisan 2014 güncelleştirmeleri**:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1055">**April 2014 updates**:</span></span>

- <span data-ttu-id="8b6b2-1056">[Visual Studio 2013 Güncelleştirmesi,](https://go.microsoft.com/fwlink/p/?LinkId=393658) bu senaryoları desteklemek için Taşınabilir Sınıf Kitaplığı şablonlarında güncelleştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1056">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) includes updates to the Portable Class Library templates to support these scenarios:</span></span>

  - <span data-ttu-id="8b6b2-1057">Windows 8.1, Windows Phone 8.1 ve Windows Phone Silverlight 8.1'i hedefleyen taşınabilir kitaplıklarda Windows Runtime API'lerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1057">You can use Windows Runtime APIs in portable libraries that target Windows 8.1, Windows Phone 8.1, and Windows Phone Silverlight 8.1.</span></span>

  - <span data-ttu-id="8b6b2-1058">Windows 8.1 veya Windows Phone 8.1'i hedeflediğinizde taşınabilir kitaplıklarda XAML (Windows.UI.XAML türleri) ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1058">You can include XAML (Windows.UI.XAML types) in portable libraries when you target Windows 8.1 or Windows Phone 8.1.</span></span> <span data-ttu-id="8b6b2-1059">Aşağıdaki XAML şablonları desteklenir: Boş Sayfa, Kaynak Sözlüğü, Şablonlu Denetim ve Kullanıcı Denetimi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1059">The following XAML templates are supported:  Blank Page, Resource Dictionary, Templated Control, and User Control.</span></span>

  - <span data-ttu-id="8b6b2-1060">Windows 8.1 ve Windows Phone 8.1'i hedefleyen Mağaza uygulamalarında kullanılmak üzere taşınabilir bir Windows Runtime bileşeni (.winmd dosyası) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1060">You can create a portable Windows Runtime component (.winmd file) for use in Store apps that target Windows 8.1 and Windows Phone 8.1.</span></span>

  - <span data-ttu-id="8b6b2-1061">Taşınabilir Sınıf Kitaplığı gibi bir Windows Mağazası veya Windows Phone Mağazası sınıf kitaplığını yeniden hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1061">You can retarget a Windows Store or Windows Phone Store class library like a Portable Class Library.</span></span>

  <span data-ttu-id="8b6b2-1062">Bu değişiklikler hakkında daha fazla bilgi için [Bkz. Taşınabilir Sınıf Kitaplığı.](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1062">For more information about these changes, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

- <span data-ttu-id="8b6b2-1063">.NET Framework içerik kümesi artık Windows uygulamaları oluşturmak ve dağıtmak için bir ön derleme teknolojisi olan .NET Native için belgeler içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1063">The .NET Framework content set now includes documentation for .NET Native, which is a precompilation technology for building and deploying Windows apps.</span></span> <span data-ttu-id="8b6b2-1064">.NET Native, daha iyi performans için uygulamalarınızı ara dile (IL) değil, doğrudan yerel koda derler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1064">.NET Native compiles your apps directly to native code, rather than to intermediate language (IL), for better performance.</span></span> <span data-ttu-id="8b6b2-1065">Ayrıntılar için [.NET Native ile Uygulamaları Derleme'ye](../net-native/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1065">For details, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span>

- <span data-ttu-id="8b6b2-1066">[.NET Framework Reference Source](https://referencesource.microsoft.com/) yeni bir tarama deneyimi ve gelişmiş işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1066">The [.NET Framework Reference Source](https://referencesource.microsoft.com/) provides a new browsing experience and enhanced functionality.</span></span> <span data-ttu-id="8b6b2-1067">Artık .NET Framework kaynak koduna çevrimiçi olarak göz atabilir, çevrimdışı görüntüleme için [başvuruyu indirebilir](https://referencesource.microsoft.com/download.html) ve hata ayıklama sırasında kaynaklara (düzeltme ekinler ve güncelleştirmeler dahil) adım atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1067">You can now browse through the .NET Framework source code online, [download the reference](https://referencesource.microsoft.com/download.html) for offline viewing, and step through the sources (including patches and updates) during debugging.</span></span> <span data-ttu-id="8b6b2-1068">Daha fazla bilgi için blog girişine bakın [.NET Referans Kaynağı için yeni bir görünüm.](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1068">For more information, see the blog entry [A new look for .NET Reference Source](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span></span>

<span data-ttu-id="8b6b2-1069">.NET Framework 4.5.1'deki temel sınıflardaki yeni özellikler ve geliştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1069">New features and enhancements in the base classes in .NET Framework 4.5.1 include:</span></span>

- <span data-ttu-id="8b6b2-1070">Derlemeler için otomatik bağlama yeniden yönlendirme.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1070">Automatic binding redirection for assemblies.</span></span> <span data-ttu-id="8b6b2-1071">Visual Studio 2013'ten başlayarak,.NET Framework 4.5.1'i hedefleyen bir uygulamayı derlediğinizde, uygulamanız veya bileşenleri aynı derlemenin birden fazla sürümüne başvuruyorsa, uygulama yapılandırma dosyasına bağlama yönlendirmeleri eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1071">Starting with Visual Studio 2013, when you compile an app that targets the .NET Framework 4.5.1, binding redirects may be added to the app configuration file if your app or its components reference multiple versions of the same assembly.</span></span> <span data-ttu-id="8b6b2-1072">Bu özelliği,.NET Framework'ün eski sürümlerini hedefleyen projeler için de etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1072">You can also enable this feature for projects that target older versions of the .NET Framework.</span></span> <span data-ttu-id="8b6b2-1073">Daha fazla bilgi için [bkz: Otomatik Bağlama Yönlendirmesini Etkinleştirme ve Devre Dışı Kaldırma.](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1073">For more information, see [How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

- <span data-ttu-id="8b6b2-1074">Geliştiricilerin sunucu ve bulut uygulamalarının performansını artırmasına yardımcı olmak için tanılama bilgilerini toplama becerisi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1074">Ability to collect diagnostics information to help developers improve the performance of server and cloud applications.</span></span> <span data-ttu-id="8b6b2-1075">Daha fazla bilgi <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> için, sınıftaki yöntemlere ve <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> metotlara <xref:System.Diagnostics.Tracing.EventSource> bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1075">For more information, see the <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> and <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> methods in the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="8b6b2-1076">Çöp toplama sırasında büyük nesne yığınını (LOH) açıkça sıkıştırma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1076">Ability to explicitly compact the large object heap (LOH) during garbage collection.</span></span> <span data-ttu-id="8b6b2-1077">Daha fazla bilgi <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> için tesise bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1077">For more information, see the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="8b6b2-1078">ASP.NET uygulama süspansiyonu, çok çekirdekli JIT iyileştirmeleri ve .NET Framework güncellemeden sonra daha hızlı uygulama başlatma gibi ek performans iyileştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1078">Additional performance improvements such as ASP.NET app suspension, multi-core JIT improvements, and faster app startup after a .NET Framework update.</span></span> <span data-ttu-id="8b6b2-1079">Ayrıntılar için [.NET Framework 4.5.1 duyurusuna](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) bakın ve ASP.NET uygulaması blog gönderisini [askıya alın.](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1079">For details, see the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) and the [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog post.</span></span>

<span data-ttu-id="8b6b2-1080">Windows Formlarında iyileştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1080">Improvements to Windows Forms include:</span></span>

- <span data-ttu-id="8b6b2-1081">Windows Forms denetimlerinde yeniden boyutlandırma.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1081">Resizing in Windows Forms controls.</span></span> <span data-ttu-id="8b6b2-1082">Uygulama yapılandırma dosyasındaki (app.config) bir girişi uygulama yapılandırma dosyasında (app.config) seçerek denetimbileşenlerini (örneğin, özellik ızgarasında görünen simgeler) yeniden boyutlandırmak için sistem DPI ayarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1082">You can use the system DPI setting to resize components of controls (for example, the icons that appear in a property grid) by opting in with an entry in the application configuration file (app.config) for your app.</span></span> <span data-ttu-id="8b6b2-1083">Bu özellik şu anda aşağıdaki Windows Forms denetimlerinde desteklenir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1083">This feature is currently supported in the following Windows Forms controls:</span></span>

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <span data-ttu-id="8b6b2-1084">Bazı yönleri <xref:System.Windows.Forms.DataGridView> (desteklenen ek denetimler için [4.5.2'deki yeni özelliklere](#v452) bakın)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1084">Some aspects of the <xref:System.Windows.Forms.DataGridView> (see [new features in 4.5.2](#v452) for additional controls supported)</span></span>

  <span data-ttu-id="8b6b2-1085">Bu özelliği etkinleştirmek için \<yapılandırma dosyasına (app.config) yeni bir `EnableWindowsFormsHighDpiAutoResizing` uygulama `true`Ayarlar> öğesi ekleyin ve öğeyi şu şekilde ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1085">To enable this feature, add a new \<appSettings> element to the configuration file (app.config) and set the `EnableWindowsFormsHighDpiAutoResizing` element to `true`:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

<span data-ttu-id="8b6b2-1086">Visual Studio 2013'te .NET Framework uygulamalarınızı hata ayıklarken ki geliştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1086">Improvements when debugging your .NET Framework apps in Visual Studio 2013 include:</span></span>

- <span data-ttu-id="8b6b2-1087">Visual Studio hata ayıklamasında değerleri döndürün.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1087">Return values in the Visual Studio debugger.</span></span> <span data-ttu-id="8b6b2-1088">Visual Studio 2013'te yönetilen bir uygulamayı hata ayıklamayaptığınızda, Otomatik ler penceresi yöntemler için iade türlerini ve değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1088">When you debug a managed app in Visual Studio 2013, the Autos window displays return types and values for methods.</span></span> <span data-ttu-id="8b6b2-1089">Bu bilgiler masaüstü, Windows Mağazası ve Windows Phone uygulamaları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1089">This information is available for desktop, Windows Store, and Windows Phone apps.</span></span> <span data-ttu-id="8b6b2-1090">Daha fazla bilgi için bkz. [yöntem çağrılarının return değerlerini incele.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1090">For more information, see [Examine return values of method calls](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span></span>

- <span data-ttu-id="8b6b2-1091">64 bit uygulamalar için edit ve devam et.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1091">Edit and Continue for 64-bit apps.</span></span> <span data-ttu-id="8b6b2-1092">Visual Studio 2013, masaüstü, Windows Mağazası ve Windows Phone için 64 bit yönetilen uygulamalar için Edit ve Continue özelliğini destekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1092">Visual Studio 2013 supports the Edit and Continue feature for 64-bit managed apps for desktop, Windows Store, and Windows Phone.</span></span> <span data-ttu-id="8b6b2-1093">Varolan sınırlamalar hem 32 bit hem de 64 bit uygulamalar için geçerli liğini korur [(Desteklenen Kod Değişiklikleri (C#)](/visualstudio/debugger/supported-code-changes-csharp) makalesinin son bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1093">The existing limitations remain in effect for both 32-bit and 64-bit apps (see the last section of the [Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp) article).</span></span>

- <span data-ttu-id="8b6b2-1094">Async-aware hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1094">Async-aware debugging.</span></span> <span data-ttu-id="8b6b2-1095">Visual Studio 2013'te eşzamanlı uygulamaları hata ayıklamayı kolaylaştırmak için çağrı yığını, toplayıcılar tarafından sağlanan altyapı kodunu gizleyerek eşzamanlı programlamayı destekler ve mantıksal üst çerçevelerde zincirler oluşturarak mantıksal program yürütmesini daha fazla takip edebilirsiniz Açıkça.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1095">To make it easier to debug asynchronous apps in Visual Studio 2013, the call stack hides the infrastructure code provided by compilers to support asynchronous programming, and also chains in logical parent frames so you can follow logical program execution more clearly.</span></span> <span data-ttu-id="8b6b2-1096">Görevler penceresi Paralel Görevler penceresinin yerini alır ve belirli bir kesme noktasıyla ilgili görevleri görüntüler ve uygulamada şu anda etkin veya zamanlanmış diğer görevleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1096">A Tasks window replaces the Parallel Tasks window and displays tasks that relate to a particular breakpoint, and also displays any other tasks that are currently active or scheduled in the app.</span></span> <span data-ttu-id="8b6b2-1097">Bu özelliği [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"Async-aware hata ayıklama" bölümünde n için okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1097">You can read about this feature in the "Async-aware debugging" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

- <span data-ttu-id="8b6b2-1098">Windows Runtime bileşenleri için daha iyi özel durum desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1098">Better exception support for Windows Runtime components.</span></span> <span data-ttu-id="8b6b2-1099">Windows 8.1'de, Windows Mağazası uygulamalarından kaynaklanan özel durumlar, dil sınırları nın ötesinde bile özel durumlara neden olan hata yla ilgili bilgileri korur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1099">In Windows 8.1, exceptions that arise from Windows Store apps preserve information about the error that caused the exception, even across language boundaries.</span></span> <span data-ttu-id="8b6b2-1100">Bu özelliği [.NET Framework 4.5.1 duyurusunun](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)"Windows Mağazası uygulama geliştirme" bölümünden okuyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1100">You can read about this feature in the "Windows Store app development" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

<span data-ttu-id="8b6b2-1101">Visual Studio 2013'ten itibaren, Windows 8.x Store uygulamalarının yanı sıra masaüstü uygulamalarını optimize etmek için [Yönetilen Profil Destekli Optimizasyon Aracı'nı (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1101">Starting with Visual Studio 2013, you can use the [Managed Profile Guided Optimization Tool (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<span data-ttu-id="8b6b2-1102">ASP.NET 4.5.1'deki yeni özellikler [için Visual Studio 2013 Sürüm Notları için ASP.NET ve Web Araçları'na](/aspnet/visual-studio/overview/2013/release-notes)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1102">For new features in ASP.NET 4.5.1, see [ASP.NET and Web Tools for Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).</span></span>

<a name="v45" />

## <a name="whats-new-in-net-framework-45"></a><span data-ttu-id="8b6b2-1103">.NET Framework 4.5'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1103">What's new in .NET Framework 4.5</span></span>

### <a name="base-classes"></a><span data-ttu-id="8b6b2-1104">Temel sınıflar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1104">Base classes</span></span>

- <span data-ttu-id="8b6b2-1105">Dağıtım sırasında .NET Framework 4 uygulamalarını algılayıp kapatarak sistemin yeniden başlatılmasını azaltma becerisi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1105">Ability to reduce system restarts by detecting and closing .NET Framework 4 applications during deployment.</span></span> <span data-ttu-id="8b6b2-1106">Bkz. [.NET Framework 4.5 Kurulumları Sırasında Sistem Yeniden Başlatma](../deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1106">See [Reducing System Restarts During .NET Framework 4.5 Installations](../deployment/reducing-system-restarts.md).</span></span>

- <span data-ttu-id="8b6b2-1107">64 bit platformlarda 2 gigabayttan (GB) daha büyük diziler için destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1107">Support for arrays that are larger than 2 gigabytes (GB) on 64-bit platforms.</span></span> <span data-ttu-id="8b6b2-1108">Bu özellik uygulama yapılandırma dosyasında etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1108">This feature can be enabled in the application configuration file.</span></span> <span data-ttu-id="8b6b2-1109">Ayrıca nesne boyutu ve dizi boyutu diğer kısıtlamaları listeler [gcAllowVeryLargeObjects> öğesi ne bakın. \<](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1109">See the [\<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), which also lists other restrictions on object size and array size.</span></span>

- <span data-ttu-id="8b6b2-1110">Sunucular için arka plan çöp toplama yoluyla daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1110">Better performance through background garbage collection for servers.</span></span> <span data-ttu-id="8b6b2-1111">.NET Framework 4.5'te sunucu çöp toplama yı kullandığınızda, arka plan çöp toplama otomatik olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1111">When you use server garbage collection in the .NET Framework 4.5, background garbage collection is automatically enabled.</span></span> <span data-ttu-id="8b6b2-1112">Çöp Toplama konusunun [Temelleri](../../standard/garbage-collection/fundamentals.md) bölümüne bakınız.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1112">See the Background Server Garbage Collection section of the [Fundamentals of Garbage Collection](../../standard/garbage-collection/fundamentals.md) topic.</span></span>

- <span data-ttu-id="8b6b2-1113">Uygulama performansını artırmak için isteğe bağlı olarak çok çekirdekli işlemcilerde kullanılabilen tam zamanında (JIT) derleme.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1113">Background just-in-time (JIT) compilation, which is optionally available on multi-core processors to improve application performance.</span></span> <span data-ttu-id="8b6b2-1114">Bkz. <xref:System.Runtime.ProfileOptimization>.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1114">See <xref:System.Runtime.ProfileOptimization>.</span></span>

- <span data-ttu-id="8b6b2-1115">Normal ifade altyapısının ne kadar süreyle normal bir ifadeyi zaman ları aşmadan önce çözmeye çalışacağını sınırlama yeteneği. Araziyi <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> görün.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1115">Ability to limit how long the regular expression engine will attempt to resolve a regular expression before it times out. See the <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="8b6b2-1116">Bir uygulama etki alanı için varsayılan kültürü tanımlama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1116">Ability to define the default culture for an application domain.</span></span> <span data-ttu-id="8b6b2-1117">Sınıfa <xref:System.Globalization.CultureInfo> bak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1117">See the <xref:System.Globalization.CultureInfo> class.</span></span>

- <span data-ttu-id="8b6b2-1118">Unicode (UTF-16) kodlaması için konsol desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1118">Console support for Unicode (UTF-16) encoding.</span></span> <span data-ttu-id="8b6b2-1119">Sınıfa <xref:System.Console> bak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1119">See the <xref:System.Console> class.</span></span>

- <span data-ttu-id="8b6b2-1120">Kültürel dize sıralama ve karşılaştırma verilerinin sürümü için destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1120">Support for versioning of cultural string ordering and comparison data.</span></span> <span data-ttu-id="8b6b2-1121">Sınıfa <xref:System.Globalization.SortVersion> bak.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1121">See the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="8b6b2-1122">Kaynakları alırken daha iyi performans.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1122">Better performance when retrieving resources.</span></span> <span data-ttu-id="8b6b2-1123">Bkz. [Kaynakları Paketleme ve Dağıtma.](../resources/packaging-and-deploying-resources-in-desktop-apps.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1123">See [Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

- <span data-ttu-id="8b6b2-1124">Sıkıştırılmış bir dosyanın boyutunu azaltmak için zip sıkıştırma iyileştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1124">Zip compression improvements to reduce the size of a compressed file.</span></span> <span data-ttu-id="8b6b2-1125"><xref:System.IO.Compression?displayProperty=nameWithType> Ad alanına bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1125">See the <xref:System.IO.Compression?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="8b6b2-1126">Sınıf boyunca varsayılan yansıma davranışını geçersiz kılmak <xref:System.Reflection.Context.CustomReflectionContext> için yansıma bağlamını özelleştirme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1126">Ability to customize a reflection context to override default reflection behavior through the <xref:System.Reflection.Context.CustomReflectionContext> class.</span></span>

- <span data-ttu-id="8b6b2-1127">Sınıf Windows 8'de kullanıldığında Uygulamalarda UluslararasıLaştırılmış Alan Adları (IDNA) <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> standardının 2008 sürümü için destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1127">Support for the 2008 version of the Internationalized Domain Names in Applications (IDNA) standard when the <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> class is used  on Windows 8.</span></span>

- <span data-ttu-id="8b6b2-1128">.NET Framework Windows 8'de kullanıldığında Unicode 6.0'ı uygulayan işletim sistemiyle string karşılaştırması delegasyonu.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1128">Delegation of string comparison to the operating system, which implements Unicode 6.0, when the .NET Framework is used on Windows 8.</span></span> <span data-ttu-id="8b6b2-1129">Diğer platformlarda çalışırken,.NET Framework, Unicode 5.x'i uygulayan kendi dize karşılaştırma verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1129">When running on other platforms, the .NET Framework includes its own string comparison data, which implements Unicode 5.x.</span></span> <span data-ttu-id="8b6b2-1130"><xref:System.String> Sınıfın sınıf ve Açıklamalar bölümüne <xref:System.Globalization.SortVersion> bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1130">See the <xref:System.String> class and the Remarks section of the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="8b6b2-1131">Uygulama etki alanı bazında dizeleri için karma kodları hesaplama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1131">Ability to compute the hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="8b6b2-1132">[ \<Bkz. UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1132">See [\<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span>

- <span data-ttu-id="8b6b2-1133">Tür yansıma desteği <xref:System.Type> <xref:System.Reflection.TypeInfo> ve sınıflar arasında bölünmüş.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1133">Type reflection support split between <xref:System.Type> and <xref:System.Reflection.TypeInfo> classes.</span></span> <span data-ttu-id="8b6b2-1134">[Windows Mağazası Uygulamaları için .NET Çerçevesi'ndeki Yansıma'ya](../reflection-and-codedom/reflection-for-windows-store-apps.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1134">See [Reflection in the .NET Framework for Windows Store Apps](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span></span>

### <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="8b6b2-1135">Managed Extensibility Framework (MEF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1135">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="8b6b2-1136">.NET Framework 4.5'te Yönetilen Genişletilebilirlik Çerçevesi (MEF) aşağıdaki yeni özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1136">In the .NET Framework 4.5, the Managed Extensibility Framework (MEF) provides the following new features:</span></span>

- <span data-ttu-id="8b6b2-1137">Genel türleri için destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1137">Support for generic types.</span></span>

- <span data-ttu-id="8b6b2-1138">Öznitelikler yerine adlandırma geleneklerine dayalı parçalar oluşturmanıza olanak tanıyan kural kuralı tabanlı programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1138">Convention-based programming model that enables you to create parts based on naming conventions rather than attributes.</span></span>

- <span data-ttu-id="8b6b2-1139">Birden fazla kapsam.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1139">Multiple scopes.</span></span>

- <span data-ttu-id="8b6b2-1140">Windows 8.x Store uygulamaları oluştururken kullanabileceğiniz MEF alt kümesi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1140">A subset of MEF that you can use when you create Windows 8.x Store apps.</span></span> <span data-ttu-id="8b6b2-1141">Bu alt küme NuGet Galerisi'nden [indirilebilir](https://www.nuget.org/packages/Microsoft.Composition) paket olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1141">This subset is available as a [downloadable package](https://www.nuget.org/packages/Microsoft.Composition) from the NuGet Gallery.</span></span> <span data-ttu-id="8b6b2-1142">Paketi yüklemek için Projenizi Visual Studio'da açın, **Proje** menüsünden `Microsoft.Composition` **NuGet Paketlerini Yönet'i** seçin ve paketi çevrimiçi arayın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1142">To install the package, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the `Microsoft.Composition` package.</span></span>

<span data-ttu-id="8b6b2-1143">Daha fazla bilgi için Yönetilen [Genişletilebilirlik Çerçevesi 'ne (MEF)](../mef/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1143">For more information, see [Managed Extensibility Framework (MEF)](../mef/index.md).</span></span>

### <a name="asynchronous-file-operations"></a><span data-ttu-id="8b6b2-1144">Asynchronous dosya işlemleri</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1144">Asynchronous file operations</span></span>

<span data-ttu-id="8b6b2-1145">.NET Framework 4.5'te C# ve Visual Basic dillerine yeni eşzamanlı özellikler eklendi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1145">In the .NET Framework 4.5, new asynchronous features were added to the C# and Visual Basic languages.</span></span> <span data-ttu-id="8b6b2-1146">Bu özellikler, eşzamanlı işlemleri gerçekleştirmek için görev tabanlı bir model ekler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1146">These features add a task-based model for performing asynchronous operations.</span></span> <span data-ttu-id="8b6b2-1147">Bu yeni modeli kullanmak için G/Ç sınıflarında eşzamanlı yöntemleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1147">To use this new model, use the asynchronous methods in the I/O classes.</span></span> <span data-ttu-id="8b6b2-1148">Bkz. [Eşzamanlı Dosya I/O](../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1148">See [Asynchronous File I/O](../../standard/io/asynchronous-file-i-o.md).</span></span>

<a name="tools" />

### <a name="tools"></a><span data-ttu-id="8b6b2-1149">Araçlar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1149">Tools</span></span>

<span data-ttu-id="8b6b2-1150">.NET Framework 4.5'te, Kaynak Dosya Oluşturucusu (Resgen.exe), Windows 8.x Store uygulamalarında kullanılmak üzere bir .resw dosyası oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1150">In the .NET Framework 4.5, Resource File Generator (Resgen.exe) enables you to create a .resw file for use in Windows 8.x Store apps from a .resources file embedded in a .NET Framework assembly.</span></span> <span data-ttu-id="8b6b2-1151">Daha fazla bilgi için Bkz. [Resgen.exe (Kaynak Dosya Üreteci)](../tools/resgen-exe-resource-file-generator.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1151">For more information, see [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).</span></span>

<span data-ttu-id="8b6b2-1152">Yönetilen Profil Destekli Optimizasyon (Mpgo.exe), uygulama başlangıç süresini, bellek kullanımını (çalışma kümesi boyutunu) ve yerel görüntü derlemelerini optimize ederek iş oluşturmayı geliştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1152">Managed Profile Guided Optimization (Mpgo.exe) enables you to improve application startup time, memory utilization (working set size), and throughput by optimizing native image assemblies.</span></span> <span data-ttu-id="8b6b2-1153">Komut satırı aracı, yerel görüntü uygulama derlemeleri için profil verileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1153">The command-line tool generates profile data for native image application assemblies.</span></span> <span data-ttu-id="8b6b2-1154">Bkz. [Mpgo.exe (Yönetilen Profil Güdümlü Optimizasyon Aracı)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1154">See [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span></span> <span data-ttu-id="8b6b2-1155">Visual Studio 2013'ten itibaren, Windows 8.x Store uygulamalarının yanı sıra masaüstü uygulamalarını optimize etmek için Mpgo.exe'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1155">Starting with Visual Studio 2013, you can use Mpgo.exe to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<a name="parallel" />

### <a name="parallel-computing"></a><span data-ttu-id="8b6b2-1156">Paralel bilgi işlem</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1156">Parallel computing</span></span>

<span data-ttu-id="8b6b2-1157">.NET Framework 4.5, paralel bilgi işlem için çeşitli yeni özellikler ve geliştirmeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1157">The .NET Framework 4.5 provides several new features and improvements for parallel computing.</span></span> <span data-ttu-id="8b6b2-1158">Bunlar arasında geliştirilmiş performans, artırılmış denetim, eşzamanlı programlama için geliştirilmiş destek, yeni bir veri akışı kitaplığı ve paralel hata ayıklama ve performans çözümlemesi için geliştirilmiş destek yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1158">These include improved performance, increased control, improved support for asynchronous programming, a new dataflow library, and improved support for parallel debugging and performance analysis.</span></span> <span data-ttu-id="8b6b2-1159">.NET blogu ile [Paralel Programlama'da .NET 4.5'te Paralellik için Yenilikler](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) girişine bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1159">See the entry [What’s New for Parallelism in .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) in the Parallel Programming with .NET blog.</span></span>

<a name="web" />

### <a name="web"></a><span data-ttu-id="8b6b2-1160">Web</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1160">Web</span></span>

<span data-ttu-id="8b6b2-1161">ASP.NET 4.5 ve 4.5.1 Web Formları, WebSocket desteği, eşzamanlı işleyiciler, performans geliştirmeleri ve diğer birçok özellik için model bağlama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1161">ASP.NET 4.5 and 4.5.1 add model binding for Web Forms, WebSocket support, asynchronous handlers, performance enhancements, and many other features.</span></span> <span data-ttu-id="8b6b2-1162">Daha fazla bilgi için aşağıdaki kaynaklara bakın:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1162">For more information, see the following resources:</span></span>

- <span data-ttu-id="8b6b2-1163">[ASP.NET 4.5 ve Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1163">[ASP.NET 4.5 and Visual Studio 2012](https://docs.microsoft.com/previous-versions/aspnet/hh420390(v=vs.110))</span></span>

- [<span data-ttu-id="8b6b2-1164">Visual Studio 2013 için ASP.NET and Web Tools Sürüm Notları</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1164">ASP.NET and Web Tools for Visual Studio 2013 Release Notes</span></span>](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a><span data-ttu-id="8b6b2-1165">Ağ<a name="networking" /></span><span class="sxs-lookup"><span data-stu-id="8b6b2-1165">Networking <a name="networking" /></span></span>

<span data-ttu-id="8b6b2-1166">.NET Framework 4.5, HTTP uygulamaları için yeni bir programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1166">The .NET Framework 4.5 provides a new programming interface for HTTP applications.</span></span> <span data-ttu-id="8b6b2-1167">Daha fazla bilgi için <xref:System.Net.Http?displayProperty=nameWithType> <xref:System.Net.Http.Headers?displayProperty=nameWithType> yeni ve ad alanlarına bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1167">For more information, see the new <xref:System.Net.Http?displayProperty=nameWithType> and <xref:System.Net.Http.Headers?displayProperty=nameWithType> namespaces.</span></span>

<span data-ttu-id="8b6b2-1168">Mevcut ve ilgili sınıfları kullanarak <xref:System.Net.HttpListener> bir WebSocket bağlantısını kabul etmek ve onlarla etkileşimde bulunan yeni bir programlama arabirimi için destek de dahildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1168">Support is also included for a new programming interface for accepting and interacting with a WebSocket connection by using the existing <xref:System.Net.HttpListener> and related classes.</span></span> <span data-ttu-id="8b6b2-1169">Daha fazla bilgi için <xref:System.Net.WebSockets> yeni ad <xref:System.Net.HttpListener> alanına ve sınıfa bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1169">For more information, see the new <xref:System.Net.WebSockets> namespace and the <xref:System.Net.HttpListener> class.</span></span>

<span data-ttu-id="8b6b2-1170">Buna ek olarak, .NET Framework 4.5 aşağıdaki ağ geliştirmelerini içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1170">In addition, the .NET Framework 4.5 includes the following networking improvements:</span></span>

- <span data-ttu-id="8b6b2-1171">RFC uyumlu URI desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1171">RFC-compliant URI support.</span></span> <span data-ttu-id="8b6b2-1172">Daha fazla bilgi <xref:System.Uri> için bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1172">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="8b6b2-1173">Uluslararası Alan Adı (IDN) ayrıştırma desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1173">Support for Internationalized Domain Name (IDN) parsing.</span></span> <span data-ttu-id="8b6b2-1174">Daha fazla bilgi <xref:System.Uri> için bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1174">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="8b6b2-1175">E-posta Adresi Uluslararasılaştırma (EAI) desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1175">Support for Email Address Internationalization (EAI).</span></span> <span data-ttu-id="8b6b2-1176">Daha fazla bilgi <xref:System.Net.Mail> için ad alanına bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1176">For more information, see the <xref:System.Net.Mail> namespace.</span></span>

- <span data-ttu-id="8b6b2-1177">Geliştirilmiş IPv6 desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1177">Improved IPv6 support.</span></span> <span data-ttu-id="8b6b2-1178">Daha fazla bilgi <xref:System.Net.NetworkInformation> için ad alanına bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1178">For more information, see the <xref:System.Net.NetworkInformation> namespace.</span></span>

- <span data-ttu-id="8b6b2-1179">Çift modlu soket desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1179">Dual-mode socket support.</span></span> <span data-ttu-id="8b6b2-1180">Daha fazla bilgi <xref:System.Net.Sockets.Socket> için <xref:System.Net.Sockets.TcpListener> sınıflara ve sınıflara bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1180">For more information, see the <xref:System.Net.Sockets.Socket> and <xref:System.Net.Sockets.TcpListener> classes.</span></span>

<a name="client" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="8b6b2-1181">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1181">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="8b6b2-1182">.NET Framework 4.5'te, Windows Sunu Vakfı (WPF) aşağıdaki alanlarda değişiklikler ve iyileştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1182">In the .NET Framework 4.5, Windows Presentation Foundation (WPF) contains changes and improvements in the following areas:</span></span>

- <span data-ttu-id="8b6b2-1183">Hızlı <xref:System.Windows.Controls.Ribbon.Ribbon> Erişim Araç Çubuğu, Uygulama Menüsü ve sekmeler barındıran bir şerit kullanıcı arabirimi uygulamanızı sağlayan yeni denetim.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1183">The new <xref:System.Windows.Controls.Ribbon.Ribbon> control, which enables you to implement a ribbon user interface that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>

- <span data-ttu-id="8b6b2-1184">Senkron <xref:System.ComponentModel.INotifyDataErrorInfo> ve eşzamanlı veri doğrulamayı destekleyen yeni arabirim.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1184">The new <xref:System.ComponentModel.INotifyDataErrorInfo> interface, which supports synchronous and asynchronous data validation.</span></span>

- <span data-ttu-id="8b6b2-1185"><xref:System.Windows.Controls.VirtualizingPanel> Ve <xref:System.Windows.Threading.Dispatcher> sınıflar için yeni özellikler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1185">New features for the <xref:System.Windows.Controls.VirtualizingPanel> and <xref:System.Windows.Threading.Dispatcher> classes.</span></span>

- <span data-ttu-id="8b6b2-1186">Büyük gruplanmış veri kümelerini görüntülerken ve UI dışı iş parçacıklarındaki koleksiyonlara erişerek performansı artırıldı.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1186">Improved performance when displaying large sets of grouped data, and by accessing collections on non-UI threads.</span></span>

- <span data-ttu-id="8b6b2-1187">Statik özelliklere veri bağlama, <xref:System.Reflection.ICustomTypeProvider> arabirimi uygulayan özel türlere veri bağlama ve bağlayıcı bir ifadeden veri bağlama bilgisi alma.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1187">Data binding to static properties, data binding to custom types that implement the <xref:System.Reflection.ICustomTypeProvider> interface, and retrieval of data binding information from a binding expression.</span></span>

- <span data-ttu-id="8b6b2-1188">Değerler değiştikçe verilerin yeniden konumlandırılması (canlı şekillendirme).</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1188">Repositioning of data as the values change (live shaping).</span></span>

- <span data-ttu-id="8b6b2-1189">Madde kapsayıcısının veri bağlamınının kesilip kesilmediğini denetleme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1189">Ability to check whether the data context for an item container is disconnected.</span></span>

- <span data-ttu-id="8b6b2-1190">Özellik değişiklikleri ve veri kaynağı güncelleştirmeleri arasında zaman dilimini ayarlama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1190">Ability to set the amount of time that should elapse between property changes and data source updates.</span></span>

- <span data-ttu-id="8b6b2-1191">Zayıf olay kalıplarını uygulamak için geliştirilmiş destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1191">Improved support for implementing weak event patterns.</span></span> <span data-ttu-id="8b6b2-1192">Ayrıca, olaylar artık biçimlendirme uzantılarını kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1192">Also, events can now accept markup extensions.</span></span>

<a name="windows_communication_foundation" />

### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="8b6b2-1193">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1193">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="8b6b2-1194">.NET Framework 4.5'te, Windows Communication Foundation (WCF) uygulamalarının yazılması ve sürdürülmesini kolaylaştırmak için aşağıdaki özellikler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1194">In the .NET Framework 4.5, the following features have been added to make it simpler to write and maintain Windows Communication Foundation (WCF) applications:</span></span>

- <span data-ttu-id="8b6b2-1195">Oluşturulan yapılandırma dosyalarının basitleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1195">Simplification of generated configuration files.</span></span>

- <span data-ttu-id="8b6b2-1196">Sözleşmenin ilk geliştirilmesi için destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1196">Support for contract-first development.</span></span>

- <span data-ttu-id="8b6b2-1197">uyumluluk modunu daha kolay yapılandırma ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1197">Ability to configure ASP.NET compatibility mode more easily.</span></span>

- <span data-ttu-id="8b6b2-1198">Bunları ayarlamak zorunda kalma olasılığını azaltmak için varsayılan aktarım özelliği değerlerinde değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1198">Changes in default transport property values to reduce the likelihood that you will have to set them.</span></span>

- <span data-ttu-id="8b6b2-1199">XML <xref:System.Xml.XmlDictionaryReaderQuotas> sözlük okuyucuları için kotaları el ile yapılandırmanız gereken olasılığı azaltmak için sınıfa yapılan güncelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1199">Updates to the <xref:System.Xml.XmlDictionaryReaderQuotas> class to reduce the likelihood that you will have to manually configure quotas for XML dictionary readers.</span></span>

- <span data-ttu-id="8b6b2-1200">WCF yapılandırma dosyalarının Visual Studio tarafından yapı işleminin bir parçası olarak doğrulanması, böylece uygulamanızı çalıştırmadan önce yapılandırma hatalarını algılayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1200">Validation of WCF configuration files by Visual Studio as part of the build process, so you can detect configuration errors before you run your application.</span></span>

- <span data-ttu-id="8b6b2-1201">Yeni asynchronous akış desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1201">New asynchronous streaming support.</span></span>

- <span data-ttu-id="8b6b2-1202">Internet Information Services (IIS) ile HTTPS üzerinden bir bitiş noktasını ortaya çıkarmak için yeni HTTPS protokolü eşlemi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1202">New HTTPS protocol mapping to make it easier to expose an endpoint over HTTPS with Internet Information Services (IIS).</span></span>

- <span data-ttu-id="8b6b2-1203">Hizmet URL'sine ekleyerek `?singleWSDL` tek bir WSDL belgesinde meta veri oluşturma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1203">Ability to generate metadata in a single WSDL document by appending `?singleWSDL` to the service URL.</span></span>

- <span data-ttu-id="8b6b2-1204">Websockets, TCP taşımasına benzer performans özellikleriyle 80 ve 443 bağlantı noktaları üzerinden gerçek çift yönlü iletişimi etkinleştirmek için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1204">Websockets support to enable true bidirectional communication over ports 80 and 443 with performance characteristics similar to the TCP transport.</span></span>

- <span data-ttu-id="8b6b2-1205">Hizmetleri kodda yapılandırma desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1205">Support for configuring services in code.</span></span>

- <span data-ttu-id="8b6b2-1206">XML Düzenleyici araç ipuçları.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1206">XML Editor tooltips.</span></span>

- <span data-ttu-id="8b6b2-1207"><xref:System.ServiceModel.ChannelFactory>önbelleğe alma desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1207"><xref:System.ServiceModel.ChannelFactory> caching support.</span></span>

- <span data-ttu-id="8b6b2-1208">İkili kodlayıcı sıkıştırma desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1208">Binary encoder compression support.</span></span>

- <span data-ttu-id="8b6b2-1209">Geliştiricilerin "yangın ve unut" iletisi kullanan hizmetler yazmalarını sağlayan bir UDP aktarım desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1209">Support for a UDP transport that enables developers to write services that use "fire and forget" messaging.</span></span> <span data-ttu-id="8b6b2-1210">İstemci bir hizmete ileti gönderir ve hizmetten yanıt beklemez.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1210">A client sends a message to a service and expects no response from the service.</span></span>

- <span data-ttu-id="8b6b2-1211">HTTP aktarım ve aktarım güvenliğini kullanırken tek bir WCF bitiş noktasında birden çok kimlik doğrulama modunu destekleme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1211">Ability to support multiple authentication modes on a single WCF endpoint when using the HTTP transport and transport security.</span></span>

- <span data-ttu-id="8b6b2-1212">Uluslararası etki alanı adları (IDN' ler) kullanan WCF hizmetleri için destek.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1212">Support for WCF services that use internationalized domain names (IDNs).</span></span>

<span data-ttu-id="8b6b2-1213">Daha fazla bilgi için [Windows Communication Foundation'da Yenilikler](../wcf/whats-new.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1213">For more information, see [What's New in Windows Communication Foundation](../wcf/whats-new.md).</span></span>

<a name="windows_workflow_foundation" />

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="8b6b2-1214">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1214">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="8b6b2-1215">.NET Framework 4.5'te, Windows İş Akışı Temeli'ne (WF) aşağıdakiler dahil olmak üzere birçok yeni özellik eklendi:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1215">In the .NET Framework 4.5, several new features were added to Windows Workflow Foundation (WF), including:</span></span>

- <span data-ttu-id="8b6b2-1216">İlk olarak .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1)](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)kapsamında tanıtılan devlet makine iş akışları.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1216">State machine workflows, which were first introduced as part of .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span></span> <span data-ttu-id="8b6b2-1217">Bu güncelleştirme, geliştiricilerin durum makine iş akışları oluşturmasına olanak sağlayan birkaç yeni sınıf ve etkinlik içeriyordu.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1217">This update included several new classes and activities that enabled developers to create state machine workflows.</span></span> <span data-ttu-id="8b6b2-1218">Bu sınıflar ve etkinlikler .NET Framework 4.5 için aşağıdakileri içerecek şekilde güncelleştirildi:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1218">These classes and activities were updated for the .NET Framework 4.5 to include:</span></span>

  - <span data-ttu-id="8b6b2-1219">Devletlerüzerinde kesme noktaları ayarlama yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1219">The ability to set breakpoints on states.</span></span>

  - <span data-ttu-id="8b6b2-1220">İş akışı tasarımcısındaki geçişleri kopyalama ve yapıştırabilme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1220">The ability to copy and paste transitions in the workflow designer.</span></span>

  - <span data-ttu-id="8b6b2-1221">Paylaşılan tetikleyici geçiş oluşturma için tasarımcı desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1221">Designer support for shared trigger transition creation.</span></span>

  - <span data-ttu-id="8b6b2-1222">Devlet makine iş akışları oluşturmak için <xref:System.Activities.Statements.StateMachine> <xref:System.Activities.Statements.State>etkinlikler, <xref:System.Activities.Statements.Transition>dahil: , , ve .</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1222">Activities for creating state machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition>.</span></span>

- <span data-ttu-id="8b6b2-1223">Aşağıdakiler gibi geliştirilmiş İş Akışı Tasarımcısı özellikleri:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1223">Enhanced Workflow Designer features such as the following:</span></span>

  - <span data-ttu-id="8b6b2-1224">Visual Studio'da **Hızlı Bul** ve **Dosyalarda Bul**dahil olmak üzere gelişmiş iş akışı arama özellikleri.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1224">Enhanced workflow search capabilities in Visual Studio, including **Quick Find** and **Find in Files**.</span></span>

  - <span data-ttu-id="8b6b2-1225">Bir kapsayıcı etkinliğine ikinci bir alt etkinlik eklendiğinde otomatik olarak Sıra etkinliği oluşturma ve her iki etkinliği de Sıra lı etkinliklere dahil etme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1225">Ability to automatically create a Sequence activity when a second child activity is added to a container activity, and to include both activities in the Sequence activity.</span></span>

  - <span data-ttu-id="8b6b2-1226">Kaydırma çubukları kullanmadan iş akışının görünür bölümünün değiştirilmesini sağlayan kaydırma desteği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1226">Panning support, which enables the visible portion of a workflow to be changed without using the scroll bars.</span></span>

  - <span data-ttu-id="8b6b2-1227">Ağaç stili anahat görünümünde iş akışının bileşenlerini gösteren ve **Belge Anahat** görünümünde bir bileşen seçmenize olanak tanıyan yeni bir Belge **Anahat** görünümü.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1227">A new **Document Outline** view that shows the components of a workflow in a tree-style outline view and lets you select a component in the **Document Outline** view.</span></span>

  - <span data-ttu-id="8b6b2-1228">Etkinliklere ek açıklamalar ekleme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1228">Ability to add annotations to activities.</span></span>

  - <span data-ttu-id="8b6b2-1229">İş akışı tasarımcısını kullanarak etkinlik temsilcilerini tanımlama ve tüketme becerisi.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1229">Ability to define and consume activity delegates by using the workflow designer.</span></span>

  - <span data-ttu-id="8b6b2-1230">Durum makinesi ve akış şeması iş akışlarındaki etkinlikler ve geçişler için otomatik bağlanma ve otomatik ekleme.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1230">Auto-connect and auto-insert for activities and transitions in state machine and flowchart workflows.</span></span>

- <span data-ttu-id="8b6b2-1231">XAML dosyasındaki tek bir öğedeki iş akışı için görünüm durumu bilgilerinin depolanması, böylece görünüm durumu bilgilerini kolayca bulabilir ve edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1231">Storage of the view state information for a workflow in a single element in the XAML file, so you can easily locate and edit the view state information.</span></span>

- <span data-ttu-id="8b6b2-1232">Alt etkinliklerin devam etmesini önlemek için Bir NoPersistScope kapsayıcı etkinliği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1232">A NoPersistScope container activity to prevent child activities from persisting.</span></span>

- <span data-ttu-id="8b6b2-1233">C# ifadeleri için destek:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1233">Support for C# expressions:</span></span>

  - <span data-ttu-id="8b6b2-1234">Visual Basic kullanan iş akışı projeleri Visual Basic ifadelerini, C# iş akışı projeleri ise C# ifadelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1234">Workflow projects that use Visual Basic will use Visual Basic expressions, and C# workflow projects will use C# expressions.</span></span>

  - <span data-ttu-id="8b6b2-1235">Visual Studio 2010'da oluşturulan ve Visual Basic ifadelerine sahip C# iş akışı projeleri, C# ifadelerini kullanan C# iş akışı projeleri ile uyumludur.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1235">C# workflow projects that were created in Visual Studio 2010 and that have Visual Basic expressions are compatible with C# workflow projects that use C# expressions.</span></span>

- <span data-ttu-id="8b6b2-1236">Sürüm geliştirmeleri:</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1236">Versioning enhancements:</span></span>

  - <span data-ttu-id="8b6b2-1237">Kalıcı <xref:System.Activities.WorkflowIdentity> iş akışı örneği ile iş akışı tanımı arasında eşleme sağlayan yeni sınıf.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1237">The new  <xref:System.Activities.WorkflowIdentity> class, which provides a mapping between a persisted workflow instance and its workflow definition.</span></span>

  - <span data-ttu-id="8b6b2-1238">Aynı ana bilgisayarda birden çok iş akışı sürümü de <xref:System.ServiceModel.Activities.WorkflowServiceHost>dahil olmak üzere yan yana yürütme.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1238">Side-by-side execution of multiple workflow versions in the same host, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>

  - <span data-ttu-id="8b6b2-1239">Dinamik Güncelleştirme'de, kalıcı iş akışı örneğinin tanımını değiştirme yeteneği.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1239">In Dynamic Update, the ability to modify the definition of a persisted workflow instance.</span></span>

- <span data-ttu-id="8b6b2-1240">Varolan bir hizmet sözleşmesiyle eşleşecek otomatik olarak oluşturma etkinlikleri için destek sağlayan sözleşmeye bağlı ilk iş akışı hizmeti geliştirme.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1240">Contract-first workflow service development, which provides support for automatically generating activities to match an existing service contract.</span></span>

<span data-ttu-id="8b6b2-1241">Daha fazla bilgi için [Windows İş Akışı Temelinde Yeniliklere](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1241">For more information, see [What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span></span>

<a name="tailored" />

### <a name="net-for-windows-8x-store-apps"></a><span data-ttu-id="8b6b2-1242">Windows 8.x Mağazası uygulamaları için .NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1242">.NET for Windows 8.x Store apps</span></span>

<span data-ttu-id="8b6b2-1243">Windows 8.x Store uygulamaları belirli form faktörleri için tasarlanmıştır ve Windows işletim sisteminin gücünden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1243">Windows 8.x Store apps are designed for specific form factors and leverage the power of the Windows operating system.</span></span> <span data-ttu-id="8b6b2-1244">.NET Framework 4.5 veya 4.5.1 alt kümesi, C# veya Visual Basic kullanarak Windows 8.x Store uygulamalarını oluşturmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1244">A subset of the .NET Framework 4.5 or 4.5.1 is available for building Windows 8.x Store apps for Windows by using C# or Visual Basic.</span></span> <span data-ttu-id="8b6b2-1245">Bu alt küme, Windows 8.x Store uygulamaları için .NET olarak adlandırılır ve [genel bir bakışta](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140))tartışılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1245">This subset is called .NET for Windows 8.x Store apps and is discussed in an [overview](https://docs.microsoft.com/previous-versions/windows/apps/br230302(v=vs.140)).</span></span>

### <a name="portable-class-libraries"></a><span data-ttu-id="8b6b2-1246">Taşınabilir Sınıf Kütüphaneleri<a name="portable" /></span><span class="sxs-lookup"><span data-stu-id="8b6b2-1246">Portable Class Libraries <a name="portable" /></span></span>

<span data-ttu-id="8b6b2-1247">Visual Studio 2012'deki Taşınabilir Sınıf Kitaplığı projesi (ve sonraki sürümler) birden çok .NET Framework platformunda çalışan yönetilen derlemeler yazmanızı ve oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1247">The Portable Class Library project in Visual Studio 2012 (and later versions) enables you to write and build managed assemblies that work on multiple .NET Framework platforms.</span></span> <span data-ttu-id="8b6b2-1248">Taşınabilir Sınıf Kitaplığı projesini kullanarak, hedeflemek için platformları (Windows Phone ve .NET windows 8.x Store uygulamaları için) seçersiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1248">Using a Portable Class Library project, you choose the platforms (such as Windows Phone and .NET for Windows 8.x Store apps) to target.</span></span> <span data-ttu-id="8b6b2-1249">Projenizdeki kullanılabilir türler ve üyeler, bu platformlardaki ortak türler ve üyelerle otomatik olarak sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1249">The available types and members in your project are automatically restricted to the common types and members across these platforms.</span></span> <span data-ttu-id="8b6b2-1250">Daha fazla bilgi için Bkz. [Taşınabilir Sınıf Kitaplığı.](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1250">For more information, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8b6b2-1251">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1251">See also</span></span>

- [<span data-ttu-id="8b6b2-1252">.NET Framework ve Bant Dışı Yayınlar</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1252">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
- [<span data-ttu-id="8b6b2-1253">.NET Framework'de erişilebilirlikte yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1253">What's new in accessibility in the .NET Framework</span></span>](whats-new-in-accessibility.md)
- [<span data-ttu-id="8b6b2-1254">Visual Studio 2017'de Yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1254">What's New in Visual Studio 2017</span></span>](/visualstudio/ide/whats-new-visual-studio-2017)
- [<span data-ttu-id="8b6b2-1255">Visual Studio 2019'da Yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1255">What's New in Visual Studio 2019</span></span>](/visualstudio/ide/whats-new-visual-studio-2019)
- [<span data-ttu-id="8b6b2-1256">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1256">ASP.NET</span></span>](/aspnet)
- [<span data-ttu-id="8b6b2-1257">Visual Studio'da C++ İçin Yenilikler</span><span class="sxs-lookup"><span data-stu-id="8b6b2-1257">What's New for C++ in Visual Studio</span></span>](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
