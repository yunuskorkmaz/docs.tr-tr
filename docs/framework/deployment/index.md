---
title: .NET Framework ve Uygulamaları Dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716472"
---
# <a name="deploying-the-net-framework-and-applications"></a>.NET Framework ve Uygulamaları Dağıtma

Bu makale, .NET Framework'u uygulamanızla birlikte dağıtmaya başlamanıza yardımcı olur. Bilgilerin çoğu geliştiriciler, OEM'ler ve kurumsal yöneticiler için tasarlanmıştır. .NET Framework'u bilgisayarlarına yüklemek isteyen kullanıcılar [.NET Framework'ün yüklenmesini](../install/index.md)okumalıdır.

## <a name="key-deployment-resources"></a>Anahtar Dağıtım Kaynakları

.NET Framework'ün dağıtımı ve servisi hakkında belirli bilgiler için diğer MSDN konularına aşağıdaki bağlantıları kullanın.

**Kurulum ve dağıtım**

- Genel yükleyici ve dağıtım bilgileri:

  - Yükleyici seçenekleri:

    - [Web yükleyici](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Çevrimdışı yükleyici](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Yükleme modları:

    - [Sessiz yükleme](deployment-guide-for-developers.md#chaining_custom)

    - [UI görüntüleme](deployment-guide-for-developers.md#chaining_default)

  - [.NET Framework 4.5 kurulumları sırasında sistem yeniden başlatmayı azaltma](reducing-system-restarts.md)

  - [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- .NET Framework'ü istemci uygulamasıyla dağıtma (geliştiriciler için):

  - Kurulum ve dağıtım projesinde [InstallShield'i kullanma](deployment-guide-for-developers.md#installshield-deployment)

  - [Visual Studio ClickOnce uygulamasını kullanma](deployment-guide-for-developers.md#clickonce-deployment)

  - [WiX yükleme paketi oluşturma](deployment-guide-for-developers.md#wix)

  - [Özel yükleyici kullanma](deployment-guide-for-developers.md#chaining)

  - Geliştiriciler için [ek bilgiler](deployment-guide-for-developers.md)

- .NET Framework'ün dağıtılması (OEM'ler ve yöneticiler için):

  - [Windows Değerlendirme ve Dağıtım Seti (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Yönetici kılavuzu](guide-for-administrators.md)

**Bakım**

- Genel bilgi için [.NET Framework bloguna](https://devblogs.microsoft.com/dotnet/)bakın.

- [Sürümleri algılama](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [Servis paketlerini ve güncelleştirmelerini algılama](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Dağıtımı Basitleştiren Özellikler

.NET Framework, uygulamalarınızı dağıtmayı kolaylaştıran bir dizi temel özellik sağlar:

- Etkilenmez uygulamalar.

     Bu özellik uygulama yalıtımı sağlar ve DLL çakışmalarını ortadan kaldırır. Varsayılan olarak, bileşenler diğer uygulamaları etkilemez.

- Varsayılan olarak özel bileşenler.

     Varsayılan olarak, bileşenler uygulama dizinine dağıtılır ve yalnızca içeren uygulama tarafından görülebilir.

- Kontrollü kod paylaşımı.

     Kod paylaşımı, varsayılan davranış olmak yerine kodu paylaşım için açıkça kullanılabilir hale getirmenizi gerektirir.

- Yan yana sürüm.

     Bir bileşenin veya uygulamanın birden çok sürümü bir arada bulunabilir, hangi sürümleri kullanacağınızı seçebilirsiniz ve ortak dil çalışma zamanı sürüm ilkesini zorlar.

- XCOPY dağıtımı ve çoğaltma.

     Kendi kendine tanımlanmış ve bağımsız bileşenler ve uygulamalar kayıt defteri girişleri veya bağımlılıkları olmadan dağıtılabilir.

- Anında güncellemeler.

     Yöneticiler, uzak bilgisayarlarda bile program DL'lerini güncelleştirmek için ASP.NET gibi ana bilgisayarları kullanabilir.

- Windows Yükleyici ile tümleştirme.

     Uygulamanızı dağıtırken reklam, yayımlama, onarım ve isteğe bağlı yükleme mevcuttur.

- Kurumsal dağıtım.

     Bu özellik, Active Directory'yi kullanmak da dahil olmak üzere kolay yazılım dağıtımı sağlar.

- İndirme ve önbelleğe alma.

     Artımlı indirmeler indirmeleri daha küçük tutar ve bileşenler yalnızca düşük etkili dağıtım uygulaması tarafından kullanılmak üzere yalıtılabilir.

- Kısmen güvenilen kod.

     Kimlik, kullanıcı yerine koda dayanır ve sertifika iletişim kutusu görünmez.

## <a name="packaging-and-distributing-net-framework-applications"></a>.NET Çerçeve Uygulamalarının Paketlenmesi ve Dağıtılması

.NET Framework'ün bazı paketleme ve dağıtım bilgileri belgelerin diğer bölümlerinde açıklanmıştır. Bu [bölümler,](../../standard/assembly/index.md)hiçbir kayıt defteri girişi, [güçlü adlandırılmış derlemeler](../../standard/assembly/strong-named.md), ad tekliği sağlamak ve ad sızdırma önlemek ve [derleme sürümü](../../standard/assembly/versioning.md), DLL çakışmaları ile ilişkili sorunların çoğunu giderir, derleme ler, derlemeler olarak adlandırılan kendi kendini açıklayan birimler hakkında bilgi sağlar. Aşağıdaki bölümlerde .NET Framework uygulamalarının paketlenmesi ve dağıtılması hakkında bilgi verilmiştir.

### <a name="packaging"></a>Paketleme

.NET Framework, ambalaj uygulamaları için aşağıdaki seçenekleri sunar:

- Tek bir derleme olarak veya derlemeler topluluğu olarak.

     Bu seçenekle,..dll veya .exe dosyalarını oluşturulurken kullanmanız yeterlidir.

- Dolap (CAB) dosyaları olarak.

     Bu seçenekle, dağıtım yapmak veya daha az zaman alan bir şekilde indirmek için dosyaları .cab dosyalarına sıkıştırırsınız.

- Windows Installer paketi olarak veya diğer yükleyici biçimlerinde.

     Bu seçenekle, Windows Yükleyiciile kullanılmak üzere .msi dosyaları oluşturursunuz veya uygulamanızı başka bir yükleyiciyle kullanmak üzere paketlersiniz.

### <a name="distribution"></a>Dağıtım

.NET Framework, uygulamaları dağıtmak için aşağıdaki seçenekleri sağlar:

- XCOPY veya FTP kullanın.

     Ortak dil çalışma zamanı uygulamaları kendi kendini tanımladığından ve kayıt defteri girişi gerektirmediği için, uygulamayı yalnızca uygun bir dizine kopyalamak için XCOPY veya FTP'yi kullanabilirsiniz. Uygulama daha sonra bu dizinden çalıştırılabilir.

- Kod karşıdan yüklemeyi kullanın.

     Uygulamanızı Internet üzerinden veya kurumsal bir intranet üzerinden dağıtıyorsanız, kodu bir bilgisayara indirebilir ve uygulamayı orada çalıştırabilirsiniz.

- Windows Installer 2.0 gibi bir yükleyici programı kullanın.

     Windows Installer 2.0, genel derleme önbelleğinde ve özel dizinlerde .NET Framework derlemelerini yükleyebilir, onarabilir veya kaldırabilir.

### <a name="installation-location"></a>Yükleme Konumu

Çalışma süresine kadar bulunabilmeleri için uygulamanızın derlemelerini nereye dağıtacağınızı belirlemek için [Çalışma Zamanı Derlemeleri'ni nasıl bulur'a](how-the-runtime-locates-assemblies.md)bakın.

Güvenlik hususları, uygulamanızı nasıl dağıtdığınızı da etkileyebilir. Güvenlik izinleri, kodun bulunduğu yere göre yönetilen koda verilir. Bir uygulamayı veya bileşeni Internet gibi çok az güven aldığı bir konuma dağıtmak, uygulamanın veya bileşenin yapabileceklerini sınırlar. Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../misc/code-access-security-basics.md)bakın.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Çalışma Zamanının Derlemelerin Konumunu Bulması](how-the-runtime-locates-assemblies.md)|Ortak dil çalışma zamanının bağlayıcı bir isteği yerine getirmek için hangi derlemenin kullanılacağını nasıl belirlediğini açıklar.|
|[Derleme Yükleme için En İyi Yöntemler](best-practices-for-assembly-loading.md)|Tür kimliği, "ve <xref:System.InvalidCastException> <xref:System.MissingMethodException>diğer hatalara" yol açabilecek sorunlardan kaçınmanın yollarını tartışır.|
|[.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](reducing-system-restarts.md)|Mümkün olduğunda yeniden başlatmayı önleyen yeniden başlatma yöneticisini açıklar ve .NET Framework'ü yükleyen uygulamaların bundan nasıl yararlanabileceğini açıklar.|
|[Yöneticiler için Dağıtım Kılavuzu](guide-for-administrators.md)|Bir sistem yöneticisinin Microsoft Endpoint Configuration Manager'ı kullanarak .NET Framework'ünü ve sistem bağımlılıklarını ağ da nasıl dağıtabileceğini açıklar.|
|[Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)|Geliştiricilerin .NET Framework'u uygulamalarıyla birlikte kullanıcılarının bilgisayarlarına nasıl yükleyebileceğini açıklar.|
|[Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma](/visualstudio/deployment/deploying-applications-services-and-components)|Visual Studio'da ClickOnce ve Windows Installer teknolojilerini kullanarak bir uygulamayı yayımlama yönergeleri de dahil olmak üzere dağıtım seçeneklerini tartışır.|
|[ClickOnce Uygulamalarını Yayımlama](/visualstudio/deployment/publishing-clickonce-applications)|Windows Forms uygulamasını nasıl paketleyip ClickOnce ile ağdaki istemci bilgisayarlara nasıl dağıtılanın açıklar.|
|[Kaynakları Paketleme ve Dağıtma](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|.NET Framework'ün kaynakları paketlemek ve dağıtmak için kullandığı hub ve spoke modelini açıklar; kaynak adlandırma kuralları, geri dönüş süreci ve paketleme alternatiflerini kapsar.|
|[Birlikte Çalışma Uygulamasını Dağıtma](../interop/deploying-an-interop-application.md)|Genellikle bir .NET Framework istemci derlemesi, farklı COM türü kitaplıklarını temsil eden bir veya daha fazla interop derlemesi ve bir veya daha fazla kayıtlı COM bileşeni içeren interop uygulamalarının nasıl gönderililip yüklenirolduğunu açıklar.|
|[Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](how-to-get-progress-from-the-dotnet-installer.md)|Kurulum ilerlemesini kendi görünümünüz gösterirken .NET Framework kurulum işlemini sessizce nasıl başlatıp izleyeceğinizi açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme Kılavuzu](../development-guide.md)
