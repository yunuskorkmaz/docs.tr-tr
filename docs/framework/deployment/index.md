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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b7380556e13e17e26ffb2f8c5fbbc7136a1fb5e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59481333"
---
# <a name="deploying-the-net-framework-and-applications"></a>.NET Framework ve Uygulamaları Dağıtma

Bu makalede, uygulamanızla birlikte .NET Framework'ü dağıtma başlamanıza yardımcı olur. İlgili bilgilerin çoğunu geliştiriciler, OEM'ler ve kuruluş yöneticileri için tasarlanmıştır. Kendi bilgisayarlarına .NET Framework'ü yüklemek isteyen kullanıcıların kimler [.NET Framework yükleme](~/docs/framework/install/index.md).

## <a name="key-deployment-resources"></a>Anahtar Dağıtım Kaynakları

Dağıtma ve .NET Framework bakım hakkında ayrıntılı bilgi için MSDN diğer konular için aşağıdaki bağlantıları kullanın.

**Kurulum ve dağıtım**

- Genel yükleyici ve dağıtım bilgileri:

  - Yükleyici seçenekleri:

    - [Web yükleyicisi](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Çevrimdışı yükleyici](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Yükleme modu:

    - [Sessiz yükleme](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)

    - [Bir kullanıcı Arabirimi görüntüleme](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)

  - [Sistem .NET Framework 4.5 yüklemeleri sırasında yeniden başlatmalarını azaltma](../../../docs/framework/deployment/reducing-system-restarts.md)

  - [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)

- .NET Framework istemci uygulaması ile (geliştiriciler için) dağıtma:

  - [InstallShield kullanarak](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) Kurulum ve dağıtım projesindeki

  - [Visual Studio ClickOnce uygulaması kullanma](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)

  - [WiX kurulum paketi oluşturuluyor](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)

  - [Özel bir yükleyici kullanarak](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)

  - [Ek bilgi](../../../docs/framework/deployment/deployment-guide-for-developers.md) geliştiricileri için

- .NET Framework'ü (OEM'ler ve Yöneticiler) dağıtma:

  - [Windows değerlendirme ve dağıtım Seti'nin (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Yönetici Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md)

**Bakım**

- Genel bilgi için bkz. [.NET Framework blogu](https://go.microsoft.com/fwlink/p/?LinkId=254977)

- [Sürümlerini algılamaya](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)

- [Hizmet paketleri ve güncelleştirmeler algılanıyor](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Dağıtım basitleştiren özellikleri

.NET Framework ve uygulamalarınızı daha kolay hale getirmek temel özellikleri sağlar:

- Etkisiz uygulamalar.

     Bu özellik, uygulama yalıtımı sağlar ve DLL çakışmalarını ortadan kaldırır. Varsayılan olarak, bileşenleri, diğer uygulamaları etkilemez.

- Özel bileşenler varsayılan olarak.

     Varsayılan olarak, bileşenleri uygulama dizinine dağıtılır ve yalnızca içeren uygulamaya görülebilir.

- Kod paylaşımını denetlenir.

     Kod paylaşımını açıkça kod varsayılan davranışı olan yerine paylaşmak için kullanılabilir olmasını gerektirir.

- Yan yana sürüm oluşturma.

     Bir bileşen ya da uygulama birden çok sürümünü bir arada var olabilen kullanmak için hangi sürümlerin seçebilirsiniz ve ortak dil çalışma zamanı sürüm ilkesini zorlar.

- XCOPY dağıtım ve çoğaltma.

     Şirket içinde açıklanan ve kendi başına bileşenler ve uygulamalar, kayıt defteri girdileri veya bağımlılıkları dağıtılabilir.

- Üzerinde halindeyken güncelleştirmeler.

     Yöneticiler, ASP.NET gibi bir ana bilgisayar programı DLL'leri, uzak bilgisayarlarda bile güncelleştirmek için kullanabilirsiniz.

- Windows Installer ile tümleştirme.

     Reklam, yayımlama, onarım ve isteğe bağlı yükleme uygulamanızı dağıtırken tüm kullanılabilir.

- Kurumsal Dağıtım.

     Bu özellik, kolay yazılım dağıtımı, Active Directory kullanma dahil olmak üzere sağlar.

- İndirme ve önbelleğe alma.

     Artımlı indirme daha küçük indirmeler tutun ve bileşenleri yalnızca low Impact dağıtım için uygulama tarafından kullanılmak üzere ayrılmış olabilir.

- Kısmen güvenilen kod.

     Kimlik kodu kullanıcı yerine temel alır ve hiçbir sertifika iletişim kutusu görünür.

## <a name="packaging-and-distributing-net-framework-applications"></a>Paketleme ve .NET Framework uygulamalarını dağıtma

Bazı paketleme ve dağıtım bilgileri için .NET Framework belgelerinin diğer bölümlerinde açıklanmıştır. Bu bölümler adlı kendiliğinden açıklayıcı birimleri hakkında bilgi sağlamak [derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), hiçbir kayıt defteri girdilerini gerektir [tanımlayıcı adlı derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md), adının benzersiz olmasını sağlamak ve ad engelleme yanıltma, ve [derleme sürümlendirme](../../../docs/framework/app-domains/assembly-versioning.md), hangi adresleri birçok DLL çakışmaları ile ilgili sorunlar. Aşağıdaki bölümlerde, paketleme ve .NET Framework uygulamalarını dağıtmak hakkında bilgi sağlar.

### <a name="packaging"></a>Paketleme

.NET Framework uygulama paketleme için aşağıdaki seçenekleri sağlar:

- Tek bir derleme veya derlemeler koleksiyonu olarak.

     Oluşturuldukları gibi bu seçenek, sadece .dll veya .exe dosyaları kullanın.

- Dolap (CAB) dosyaları olarak.

     Bu seçenek belirtilmişse, dağıtım yapmak veya daha az zaman alan indirmek için bir .cab dosyasına dosyaları sıkıştırın.

- Bir Windows Installer paketi olarak veya diğer yükleyici biçimleri.

     Bu seçenek, .msi dosyaları kullanmak için Windows Installer ile oluşturabilir veya diğer bir yükleyici ile kullanmak için uygulama paketi.

### <a name="distribution"></a>Dağıtım

.NET Framework uygulamalarını dağıtmak için aşağıdaki seçenekleri sağlar:

- XCOPY veya FTP kullanın.

     Ortak dil çalışma zamanı uygulamaları kendiliğinden açıklayıcı ve kayıt defteri girdisi gerekli olduğundan uygulamaya uygun bir dizine kopyalamak XCOPY veya FTP kullanabilirsiniz. Uygulama bu dizinden çalıştırabilirsiniz.

- Kod indirmeyi kullanın.

     Uygulamanız Internet üzerinden veya kurumsal bir intranet üzerinden dağıtıyorsanız, yalnızca kod bir bilgisayara indirebilir ve var. uygulamayı çalıştırın.

- Windows Installer 2.0 gibi bir yükleyici programı kullanın.

     Windows Installer 2.0 yükleyin, onarın veya .NET Framework derlemeleri genel derleme önbelleğini ve özel dizinleri kaldırın.

### <a name="installation-location"></a>Yükleme Konumu

Çalışma zamanı tarafından bulunabilir bu nedenle, uygulamanızın derlemeleri dağıtılacağı yeri belirlemek için bkz: [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).

Uygulama dağıtımı güvenlik konuları da etkileyebilir. Kodun bulunduğu yere göre yönetilen kod için güvenlik izinleri verilir. Bir uygulama veya bileşenin nereden sınırları Internet gibi çok az güven aldığı bir konuma dağıtma ne uygulamanın veya bileşenin yapabilirsiniz. Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için bkz. [kod erişimi güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Ortak dil çalışma zamanının hangi derleme bağlama isteğini yerine getirmek için kullanılacak etiketleneceğini nasıl açıklar.|
|[Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|Yol açabilir türü kimliği sorunları önlemek için yollar ele alınmaktadır <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hataları.|
|[.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](../../../docs/framework/deployment/reducing-system-restarts.md)|Yeniden başlatma Yöneticisi önleyen mümkün olduğunda yeniden başlatır ve .NET Framework yükleme uygulamaları bu Avantajdan nasıl alabilir açıklanmaktadır.|
|[Yöneticiler için Dağıtım Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md)|Nasıl bir Sistem Yöneticisi .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden System Center Configuration Manager (SCCM) kullanarak dağıtılacağı açıklanmaktadır.|
|[Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)|Geliştiriciler uygulamalarını ile kullanıcıların bilgisayarlarına .NET Framework nasıl yükleyebilirsiniz açıklar.|
|[Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma](/visualstudio/deployment/deploying-applications-services-and-components)|ClickOnce ve Windows Installer teknolojilerini kullanarak uygulama yayımlama yönergeleri de dahil olmak üzere Visual Studio dağıtım seçenekleri ele alınmaktadır.|
|[ClickOnce Uygulamalarını Yayımlama](/visualstudio/deployment/publishing-clickonce-applications)|Bir Windows Forms uygulaması'nı paketlemek ve ağdaki istemci bilgisayarları ile ClickOnce dağıtma işlemini açıklamaktadır.|
|[Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|Paketleme ve dağıtma kaynakları için kullandığı .NET Framework merkez ve ışınsal modelini açıklar; Kaynak adlandırma kuralları, geri dönüş işlemi ve paketleme seçenekleri ele alınmaktadır.|
|[Birlikte Çalışma Uygulamasını Dağıtma](../../../docs/framework/interop/deploying-an-interop-application.md)|Gönderin ve genellikle bir .NET Framework istemci bütünleştirilmiş kodu ayrı bir COM tür kitaplıkları temsil eden bir veya daha fazla birlikte çalışma derlemelerini içeren, birlikte çalışma uygulamaları ve bir veya daha fazla kayıtlı COM bileşenlerini yüklemek açıklanmaktadır.|
|[Nasıl yapılır: .NET Framework 4.5 yükleyicisinden ilerleme durumunu Al](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Sessizce başlatmak ve kendi görünüm Kurulum sürecinizin gösterirken .NET Framework Kurulum sürecini izlemek açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
