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
ms.openlocfilehash: 2686d0db966192606656167d6e505f34ded333f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396535"
---
# <a name="deploying-the-net-framework-and-applications"></a>.NET Framework ve Uygulamaları Dağıtma
Bu makale .NET Framework ile uygulamanızı dağıtımına başlamak yardımcı olur. Bilgilerin çoğunu geliştiriciler, OEM'ler ve kuruluş yöneticileri için tasarlanmıştır. .NET Framework'ü bilgisayarlarında yüklemek istediğiniz kullanıcıları kimler [.NET Framework yükleme](~/docs/framework/install/index.md).  
  
## <a name="key-deployment-resources"></a>Anahtar Dağıtım Kaynakları  
 Dağıtma ve .NET Framework hizmet hakkında ayrıntılı bilgi için MSDN diğer konular için aşağıdaki bağlantıları kullanın.  
  
 **Kurulum ve dağıtım**  
  
-   Genel yükleyici ve dağıtım bilgileri:  
  
    -   Yükleyici seçenekleri:  
  
        -   [Web yükleyicisi](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [Çevrimdışı yükleyici](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   Yükleme modu:  
  
        -   [Sessiz yükleme](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [Bir kullanıcı Arabirimi görüntüleme](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [Sistem .NET Framework 4.5 yüklemeleri sırasında yeniden başlatmalarını azaltma](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   Bir istemci uygulaması ile .NET Framework (geliştiriciler için) dağıtma:  
  
    -   [InstallShield kullanarak](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) Kurulum ve dağıtım projesindeki  
  
    -   [Visual Studio ClickOnce uygulamasını kullanma](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [WiX yükleme paketi oluşturma](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [Özel bir yükleyici kullanarak](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   [Ek bilgi](../../../docs/framework/deployment/deployment-guide-for-developers.md) geliştiricileri için  
  
-   .NET Framework (OEM'ler ve Yöneticiler) dağıtma:  
  
    -   [Windows değerlendirme ve Dağıtım Seti (ADK)](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [Yönetici Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 **Bakım**  
  
-   Genel bilgi için bkz: [.NET Framework blogu](http://go.microsoft.com/fwlink/p/?LinkId=254977)  
  
-   [Sürümleri algılama](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [Hizmet paketlerini ve güncelleştirmelerini algılama](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a>Dağıtım basitleştiren özellikleri  
 .NET Framework uygulamalarınızı dağıtma kolaylaştırmak temel özelliklerini sağlar:  
  
-   Hayır etkisi uygulamalar.  
  
     Bu özellik, uygulama yalıtımı sağlar ve DLL çakışmaları ortadan kaldırır. Varsayılan olarak, diğer uygulamaların bileşenleri etkilemez.  
  
-   Özel bileşenler varsayılan olarak.  
  
     Varsayılan olarak, bileşenleri uygulama dizinine dağıtılır ve yalnızca içeren uygulamaya görülebilir.  
  
-   Kod paylaşımını denetlenir.  
  
     Kod paylaşımını açıkça kod varsayılan davranışı yerine paylaşımı için kullanılabilir olmasını gerektirir.  
  
-   Yan yana sürüm oluşturma.  
  
     Bir bileşeni ya da uygulama birden fazla sürümünü bir arada var olabilen, kullanmak için hangi sürümlerinin seçebilirsiniz ve ortak dil çalışma zamanı sürüm ilkesini zorlar.  
  
-   XCOPY dağıtımı ve çoğaltma.  
  
     Kendi kendine açıklanan ve müstakil bileşenleri ve uygulamaları kayıt defteri girdileri veya bağımlılıkları dağıtılabilir.  
  
-   Üzerinde-çalışma sırasında güncelleştirmeler.  
  
     Yöneticiler gibi ASP.NET, ana bilgisayar programı DLL'ler, uzak bilgisayarlarda bile güncelleştirmek için kullanabilirsiniz.  
  
-   Windows Installer ile tümleştirme.  
  
     Reklam, yayımlama, onarma ve isteğe bağlı yükleme uygulamanızı dağıtırken tüm kullanılabilir.  
  
-   Kurumsal Dağıtım.  
  
     Bu özellik, kolay yazılım dağıtımı, Active Directory kullanımı dahil olmak üzere sağlar.  
  
-   İndirme ve önbelleğe alma.  
  
     Artımlı yüklemeleri yüklemeleri daha küçük olmasını ve bileşenleri yalnızca low Impact dağıtımı için uygulama tarafından kullanılmak üzere ayrılmış olabilir.  
  
-   Kısmen güvenilen kod.  
  
     Kimlik kullanıcı yerine kodu temel alır ve hiç sertifika iletişim kutusu görünür.  
  
## <a name="packaging-and-distributing-net-framework-applications"></a>Paketleme ve .NET Framework uygulamalarını dağıtma  
 Bazı paketleme ve dağıtım bilgileri için .NET Framework belgenin diğer bölümlerinde tanımlanmıştır. Bu bölümler olarak adlandırılan kendiliğinden açıklayıcı birimler hakkında bilgi sağlar [derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), hiçbir kayıt defteri girdileri gerektiren [tanımlayıcı adlı derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md), hangi adının benzersiz olduğundan emin olup adı önlemek kimlik sahtekarlığı, ve [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md), hangi adresleri birçok DLL çakışmaları ile ilgili sorunları. Aşağıdaki bölümlerde paketleme ve .NET Framework uygulamaları dağıtma hakkında bilgi sağlar.  
  
### <a name="packaging"></a>Paketleme  
 .NET Framework uygulama paketleme için aşağıdaki seçenekleri sağlar:  
  
-   Tek bir derleme veya derlemelerin bir koleksiyon olarak.  
  
     Bunlar oluşturulan gibi bu seçenekle, yalnızca .dll veya .exe dosyaları kullanın.  
  
-   Dolap (CAB) dosyası.  
  
     Bu seçenek ile .cab dosyalarına dağıtım yapmak veya daha az zaman alan indirmek için dosyaları sıkıştırın.  
  
-   Bir Windows Installer paketi olarak veya diğer yükleyici biçimleri.  
  
     Bu seçeneği, Windows Installer ile kullanmak için .msi dosyaları oluşturun veya başka bir yükleyici ile kullanmak için uygulama paketini.  
  
### <a name="distribution"></a>Dağıtım  
 .NET Framework uygulamalarını dağıtmak için aşağıdaki seçenekleri sağlar:  
  
-   XCOPY veya FTP kullanın.  
  
     Ortak dil çalışma zamanı uygulamaları kendiliğinden açıklayıcı ve kayıt defteri girdisi iste olduğundan yalnızca uygun bir dizini uygulamaya kopyalamak için XCOPY veya FTP kullanabilirsiniz. Uygulama, diğer dizinden çalıştırabilirsiniz.  
  
-   Kodu indirme kullanın.  
  
     Internet üzerinden veya Kurumsal intranet üzerinden uygulamanızı dağıtıyorsanız, yalnızca bir bilgisayara kodu indirin ve uygulama var. çalıştırın.  
  
-   Windows Installer 2.0 gibi bir yükleyici programı kullanın.  
  
     Windows Installer 2.0 yükleyin, onarın veya .NET Framework derlemeleri genel derleme önbelleği ve özel dizinleri kaldırın.  
  
### <a name="installation-location"></a>Yükleme Konumu  
 Çalışma zamanı tarafından bulunan şekilde uygulamanızın derlemeleri dağıtma nereye belirlemek için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Güvenlik konuları da uygulamanızı dağıtmak nasıl etkileyebilir. Kod bulunduğu göre yönetilen kod için güvenlik izinleri verilir. Bir uygulama veya bileşenin burada sınırları Internet gibi az güven aldığı bir konuma dağıtma hangi uygulamanın veya bileşenin yapabilirsiniz. Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Hangi derleme bağlama isteği yerine getirmek için kullanılacak ortak dil çalışma zamanı nasıl belirlediğini açıklar.|  
|[Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|Yol açabilir türü kimliğinin sorunları önlemek için yollarını tartışmaktadır <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hataları.|  
|[.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](../../../docs/framework/deployment/reducing-system-restarts.md)|Yeniden başlatma Yöneticisi önleyen mümkün olduğunca yeniden başlatır ve nasıl .NET Framework'ü yüklemek uygulamalar, bu yararlanabilir açıklanmaktadır.|  
|[Yöneticiler için Dağıtım Kılavuzu](../../../docs/framework/deployment/guide-for-administrators.md)|Nasıl bir Sistem Yöneticisi .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden System Center Configuration Manager (SCCM) kullanarak dağıtabilirsiniz açıklar.|  
|[Geliştiriciler için Dağıtım Kılavuzu](../../../docs/framework/deployment/deployment-guide-for-developers.md)|Geliştiriciler kendi uygulamalarla bunların kullanıcıların bilgisayarlarına .NET Framework nasıl yükleyebileceğinizi açıklanmaktadır.|  
|[Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma](/visualstudio/deployment/deploying-applications-services-and-components)|ClickOnce ve Windows Installer teknolojileri kullanarak bir uygulamayı yayımlamak için yönergeler de dahil olmak üzere Visual Studio dağıtım seçenekleri ele alınmaktadır.| 
|[ClickOnce Uygulamalarını Yayımlama](/visualstudio/deployment/publishing-clickonce-applications)|Bir Windows Forms uygulaması paketini ve ağdaki istemci bilgisayarlarını ClickOnce ile dağıtmak açıklar.|  
|[Kaynakları Paketleme ve Dağıtma](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|.NET Framework paketini ve kaynakları dağıtmak için kullandığı hub ve bağlı bileşen modeli açıklar; adlandırma kuralları, geri dönüş işlemi ve paketleme alternatifleri kaynak kapsar.|  
|[Birlikte Çalışma Uygulamasını Dağıtma](../../../docs/framework/interop/deploying-an-interop-application.md)|Sevk ve genellikle bir .NET Framework istemci derleme ayrı COM tür kitaplıklarının temsil eden bir veya daha fazla birlikte çalışma derlemeleri içerir, birlikte çalışma uygulamaları ve bir veya daha fazla kayıtlı COM bileşenleri yüklemek açıklanmaktadır.|  
|[Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|Sessiz bir şekilde başlatın ve Kurulum ilerleme kendi görünüm gösterirken .NET Framework Kurulum işlemi izlemek açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)
