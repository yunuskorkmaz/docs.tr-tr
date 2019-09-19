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
ms.openlocfilehash: f1d13c4c3e27b5af5b3c3e84995cae3df94a307d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052074"
---
# <a name="deploying-the-net-framework-and-applications"></a>.NET Framework ve Uygulamaları Dağıtma

Bu makale, .NET Framework uygulamanıza dağıtmaya başlamanıza yardımcı olur. Bilgilerin çoğu geliştiriciler, OEM 'Ler ve kuruluş yöneticileri için tasarlanmıştır. .NET Framework bilgisayarlarına yüklemek isteyen kullanıcılar [.NET Framework yüklemeyi](../install/index.md)okumalı.

## <a name="key-deployment-resources"></a>Anahtar dağıtım kaynakları

.NET Framework dağıtma ve bakım hakkında belirli bilgiler için diğer MSDN konularına yönelik aşağıdaki bağlantıları kullanın.

**Kurulum ve dağıtım**

- Genel yükleyici ve dağıtım bilgileri:

  - Yükleyici seçenekleri:

    - [Web Yükleyicisi](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [Çevrimdışı yükleyici](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - Yükleme modları:

    - [Sessiz yükleme](deployment-guide-for-developers.md#chaining_custom)

    - [Kullanıcı arabirimini görüntüleme](deployment-guide-for-developers.md#chaining_default)

  - [.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma](reducing-system-restarts.md)

  - [Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- .NET Framework bir istemci uygulamasıyla dağıtma (geliştiriciler için):

  - Kurulum ve dağıtım projesinde [InstallShield kullanma](deployment-guide-for-developers.md#installshield-deployment)

  - [Visual Studio ClickOnce uygulaması kullanma](deployment-guide-for-developers.md#clickonce-deployment)

  - [WiX yükleme paketi oluşturma](deployment-guide-for-developers.md#wix)

  - [Özel bir yükleyici kullanma](deployment-guide-for-developers.md#chaining)

  - Geliştiriciler için [ek bilgiler](deployment-guide-for-developers.md)

- .NET Framework dağıtma (OEM 'Ler ve yöneticiler için):

  - [Windows değerlendirme ve Dağıtım Seti (ADK)](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [Yönetici Kılavuzu](guide-for-administrators.md)

**Bakım**

- Genel bilgiler için [.NET Framework bloguna](https://go.microsoft.com/fwlink/p/?LinkId=254977) bakın

- [Sürümler algılanıyor](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [Hizmet paketleri ve güncelleştirmeler algılanıyor](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a>Dağıtımı basitleştiren Özellikler

.NET Framework, uygulamalarınızı dağıtmayı kolaylaştıran bir dizi temel özellik sağlar:

- Etkili olmayan uygulamalar.

     Bu özellik uygulama yalıtımı sağlar ve DLL çakışmalarını ortadan kaldırır. Varsayılan olarak, bileşenler diğer uygulamaları etkilemez.

- Varsayılan olarak özel bileşenler.

     Varsayılan olarak, bileşenler uygulama dizinine dağıtılır ve yalnızca içeren uygulama için görülebilir.

- Denetlenen kod paylaşımı.

     Kod paylaşımı, varsayılan davranış yerine kodu paylaşıma açık bir şekilde yapmanızı gerektirir.

- Yan yana sürüm oluşturma.

     Bir bileşenin veya uygulamanın birden çok sürümü birlikte bulunabilir, hangi sürümlerin kullanılacağını seçebilirsiniz ve ortak dil çalışma zamanı sürüm oluşturma ilkesini zorunlu kılar.

- XCOPY dağıtımı ve çoğaltma.

     Kendi kendine tanımlanmış ve bağımsız bileşenler ve uygulamalar kayıt defteri girişleri veya bağımlılıklar olmadan dağıtılabilir.

- Anında güncelleştirmeler.

     Yöneticiler, uzak bilgisayarlarda bile program dll 'Lerini güncelleştirmek için ASP.NET gibi Konakları kullanabilir.

- Windows Installer ile tümleştirme.

     Uygulamanızı dağıttığınızda tanıtım, yayımlama, onarma ve isteğe bağlı olarak kurma kullanılabilir.

- Kurumsal Dağıtım.

     Bu özellik Active Directory kullanımı dahil olmak üzere kolay yazılım dağıtımı sağlar.

- İndiriliyor ve önbelleğe alınıyor.

     Artımlı indirmeler İndirmeleri daha küçük tutun ve bileşenler yalnızca uygulama tarafından düşük etkili dağıtım için kullanılmak üzere yalıtılabilir.

- Kısmen güvenilen kod.

     Kimlik, Kullanıcı yerine kodu temel alır ve sertifika iletişim kutusu görüntülenmez.

## <a name="packaging-and-distributing-net-framework-applications"></a>.NET Framework uygulamalarını paketleme ve dağıtma

.NET Framework yönelik paketleme ve dağıtım bilgilerinin bazıları, belgelerinin diğer bölümlerinde açıklanmıştır. Bu bölümler, hiçbir kayıt defteri girişi gerektirmeyen [derleme](../../standard/assembly/index.md)adlı, [tanımlayıcı adlı derlemelerin](../../standard/assembly/strong-named.md)yanı sıra ad yanıltmayı ve [derleme sürümü oluşturmayı](../../standard/assembly/versioning.md) önleyen, kendi kendini açıklayan birimler hakkında bilgi sağlar , DLL çakışmaları ile ilişkili birçok sorunu ele alınmaktadır. Aşağıdaki bölümlerde .NET Framework uygulamalarını paketleme ve dağıtma hakkında bilgi sağlanmaktadır.

### <a name="packaging"></a>Paketleme

.NET Framework paketleme uygulamaları için aşağıdaki seçenekleri sağlar:

- Tek bir derleme veya derlemelerin koleksiyonu olarak.

     Bu seçenekle, yalnızca. dll veya. exe dosyalarını oluşturulduğu gibi kullanırsınız.

- As dolap (CAB) dosyaları.

     Bu seçenekle, dağıtım yapmak veya daha az zaman kullanmak için dosyaları. cab dosyalarına sıkıştırursunuz.

- Windows Installer paketi veya diğer yükleyici biçimlerinde.

     Bu seçenekle, Windows Installer ile kullanmak üzere. msi dosyaları oluşturur veya uygulamanızı başka bir yükleyiciyle kullanmak üzere paketlemenize yardımcı olursunuz.

### <a name="distribution"></a>Dağıtım

.NET Framework, uygulamaları dağıtmak için aşağıdaki seçenekleri sağlar:

- XCOPY veya FTP kullanın.

     Ortak dil çalışma zamanı uygulamaları kendi kendini betimleyen ve kayıt defteri girişi gerektirmeyen için, yalnızca uygulamayı uygun bir dizine kopyalamak üzere XCOPY veya FTP kullanabilirsiniz. Uygulama daha sonra bu dizinden çalıştırılabilir.

- Kod indirmeyi kullanın.

     Uygulamanızı Internet üzerinden veya kurumsal bir intranet üzerinden dağıtıyorsanız, kodu bir bilgisayara indirebilir ve uygulamayı orada çalıştırmanız yeterlidir.

- Windows Installer 2,0 gibi bir yükleyici programı kullanın.

     Windows Installer 2,0, genel derleme önbelleğinde ve özel dizinlerde .NET Framework derlemeleri yükleyebilir, onarabilir veya kaldırabilir.

### <a name="installation-location"></a>Yükleme Konumu

Çalışma zamanı tarafından bulunabilmeleri için uygulamanızın derlemelerinin nereye dağıtılacağını öğrenmek için, bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](how-the-runtime-locates-assemblies.md).

Güvenlik konuları, uygulamanızı nasıl dağıtabileceğinizi da etkileyebilir. Güvenlik izinleri, kodun bulunduğu yere göre yönetilen koda verilir. Bir uygulama veya bileşeni Internet gibi küçük bir güven aldığı bir konuma dağıtmak, uygulamanın veya bileşenin neler yapabileceğini kısıtlar. Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../misc/code-access-security-basics.md).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](how-the-runtime-locates-assemblies.md)|Ortak dil çalışma zamanının, bir bağlama isteğini karşılamak için hangi derlemeyi kullanacağınızı nasıl belirlediğini açıklar.|
|[Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler](best-practices-for-assembly-loading.md)|<xref:System.InvalidCastException> ,<xref:System.MissingMethodException>, Ve diğer hatalara yol açabilecek kimlik tür sorunlarından kaçınmanın yollarını açıklar.|
|[.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma](reducing-system-restarts.md)|Mümkün olan her durumda yeniden başlatma Işlemini önleyen ve .NET Framework yükleyen uygulamaların nasıl yararlanacağı açıklanmaktadır.|
|[Yöneticiler için Dağıtım Kılavuzu](guide-for-administrators.md)|Bir sistem yöneticisinin, System Center Configuration Manager (SCCM) kullanarak bir ağ üzerinde .NET Framework ve sistem bağımlılıklarını nasıl dağıtabilebileceğini açıklar.|
|[Geliştiriciler için Dağıtım Kılavuzu](deployment-guide-for-developers.md)|Geliştiricilerin kullanıcıların bilgisayarlarına uygulamalarına .NET Framework nasıl yükleyebileceğini açıklar.|
|[Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma](/visualstudio/deployment/deploying-applications-services-and-components)|ClickOnce ve Windows Installer teknolojilerini kullanarak uygulama yayımlama yönergeleri de dahil olmak üzere Visual Studio 'da dağıtım seçeneklerini açıklar.|
|[ClickOnce Uygulamalarını Yayımlama](/visualstudio/deployment/publishing-clickonce-applications)|Bir Windows Forms uygulamasının nasıl paketleneceğini ve bir ağdaki istemci bilgisayarlara ClickOnce ile nasıl dağıtılacağını açıklar.|
|[Kaynakları Paketleme ve Dağıtma](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|.NET Framework, kaynakları paketlemek ve dağıtmak için kullandığı hub ve bağlı bileşen modelini açıklar; Kaynak adlandırma kurallarını, geri dönüş işlemini ve paketleme alternatiflerini içerir.|
|[Birlikte Çalışma Uygulamasını Dağıtma](../interop/deploying-an-interop-application.md)|Genellikle bir .NET Framework istemci derlemesi, farklı COM tür kitaplıklarını temsil eden bir veya daha fazla birlikte çalışma derlemesi ve bir veya daha fazla kayıtlı COM bileşeni içeren birlikte çalışma uygulamalarının nasıl teslim edileceğini ve yükleneceğini açıklar.|
|[Nasıl yapılır: .NET Framework 4,5 Yükleyicisinden Ilerleme durumunu alın](how-to-get-progress-from-the-dotnet-installer.md)|Kurulum ilerleme durumunun kendi görünümünü gösterirken .NET Framework kurulum işleminin sessizce nasıl başlatılmasını ve izleneceğini açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Geliştirme Kılavuzu](../development-guide.md)
