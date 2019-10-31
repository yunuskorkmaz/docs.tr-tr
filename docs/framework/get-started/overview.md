---
title: .NET Framework'e Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
ms.openlocfilehash: b5dacad4511df0476dded6ac3784014665234077
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123243"
---
# <a name="overview-of-the-net-framework"></a>.NET Framework'e Genel Bakış

.NET Framework, yeni nesil uygulamalar ve XML Web Hizmetleri oluşturmayı ve çalıştırmayı destekleyen bir teknolojidir. .NET Framework, aşağıdaki hedefleri yerine getirmek için tasarlanmıştır:

- Nesne kodunun yerel olarak depolandığını ve yürütüldüğünü, yerel olarak yürütüldüğünü ancak Internet 'e dağıtıldığını veya uzaktan yürütüldüğünü, tutarlı bir nesne odaklı programlama ortamı sağlamak için.

- Yazılım dağıtımını ve sürüm çakışmalarını en aza indiren bir kod yürütme ortamı sağlamak için.

- Bilinmeyen veya yarı güvenilir üçüncü taraflarca oluşturulan kod dahil olmak üzere kodun güvenli yürütülmesini sağlayan kod yürütme ortamı sağlamak için.

- Betikleştirilmiş veya yorumlanan ortamların performans sorunlarını ortadan kaldıran kod yürütme ortamı sağlamak için.

- Geliştirici deneyimini, Windows tabanlı uygulamalar ve Web tabanlı uygulamalar gibi yaygın olarak değişen türde uygulamalar arasında tutarlı hale getirmek için.

- .NET Framework temel alan kodun diğer kodla tümleştirilebildiğinden emin olmak için endüstri standartları üzerinde tüm iletişimi oluşturmak için.

> [!NOTE]
> Hem kullanıcılar hem de geliştiriciler için .NET Framework genel bir giriş için [bkz. Başlarken](index.md).

.NET Framework, ortak dil çalışma zamanı (CLR) ve .NET Framework sınıf kitaplığından oluşur. Ortak dil çalışma zamanı .NET Framework temelidir. Çalışma zamanını, yürütme zamanında kodu yöneten bir aracı olarak düşünün; bellek yönetimi, iş parçacığı yönetimi ve uzaktan iletişim gibi Çekirdek Hizmetleri, ayrıca katı tür güvenliği ve güvenlik ve sağlamlık düzeyini destekleyen diğer kod doğruluğu biçimlerini de zorunlu olarak sağlar. Aslında kod yönetimi kavramı, çalışma zamanının temel bir ilkesidir. Çalışma zamanını hedefleyen kod, yönetilen kod olarak bilinir, ancak çalışma zamanını hedeflemeyen kod, yönetilmeyen kod olarak bilinir. Sınıf kitaplığı, geleneksel komut satırı veya grafik kullanıcı arabirimi (GUI) uygulamalarından, Web gibi ASP.NET tarafından sunulan en son yeniliklere dayalı olarak uygulamalara yönelik uygulamalar geliştirmek için kullandığınız, kapsamlı bir yeniden kullanılabilir türler koleksiyonudur. Forms ve XML Web Hizmetleri.

.NET Framework, ortak dil çalışma zamanını işlemlerine yükleyen ve yönetilen kodun yürütülmesini Başlatan yönetilmeyen bileşenler tarafından barındırılabilir ve bu sayede hem yönetilen hem de yönetilmeyen özelliklerden yararlanan bir yazılım ortamı oluşturulur. .NET Framework yalnızca birkaç çalışma zamanı Konağı sağlamaz, ancak üçüncü taraf çalışma zamanı ana bilgisayarlarının geliştirilmesini da destekler.

Örneğin, ASP.NET, yönetilen kod için ölçeklenebilir, sunucu tarafı bir ortam sağlamak üzere çalışma zamanını barındırır. ASP.NET, her ikisi de bu konunun ilerleyen kısımlarında açıklanan ASP.NET uygulamalarını ve XML Web hizmetlerini etkinleştirmek için doğrudan çalışma zamanına göre çalışmaktadır.

Internet Explorer, çalışma zamanını (bir MIME türü uzantısı biçiminde) barındıran yönetilmeyen bir uygulamaya bir örnektir. Çalışma zamanını barındırmak için Internet Explorer 'ın kullanılması, yönetilen bileşenleri veya Windows Forms denetimleri HTML belgelerinde eklemenize olanak sağlar. Çalışma zamanının bu şekilde barındırılması, yönetilen mobil kodu mümkün kılar, ancak yarı güvenilen yürütme ve yalıtılmış dosya depolaması gibi yalnızca yönetilen kodun sunduğu önemli geliştirmelerle sağlanır.

Aşağıdaki çizimde, ortak dil çalışma zamanının ve sınıf kitaplığının uygulamalarınıza ve genel sisteme ilişkisi gösterilmektedir. Çizimde ayrıca yönetilen kodun daha büyük bir mimari içinde nasıl çalıştığı gösterilmektedir.

![Yönetilen kodun daha büyük bir mimari içinde nasıl çalıştığını gösteren ekran görüntüsü.](./media/overview/language-runtime-class-library-relationship.gif)

Aşağıdaki bölümlerde .NET Framework ana özellikleri daha ayrıntılı olarak açıklanır.

## <a name="features-of-the-common-language-runtime"></a>Ortak dil çalışma zamanının özellikleri

Ortak dil çalışma zamanı belleği, iş parçacığı yürütmeyi, kod yürütmeyi, kod güvenliği doğrulamasını, derlemeyi ve diğer sistem hizmetlerini yönetir. Bu özellikler, ortak dil çalışma zamanında çalışan yönetilen koda yönelik bir iç özelliklerdir.

Güvenlikle ilgili olarak, yönetilen bileşenlere, bunların kaynağını (Internet, kurumsal ağ veya yerel bilgisayar gibi) içeren bir dizi etkene bağlı olarak farklı güven dereceleri dağıtılır. Bu, yönetilen bir bileşenin aynı etkin uygulamada kullanılsa bile dosya erişim işlemleri, kayıt defteri erişim işlemleri veya diğer hassas işlevleri gerçekleştiremeyeceği anlamına gelir.

Çalışma zamanı ayrıca ortak tür sistemi (CTS) adlı katı bir tür ve kod doğrulama altyapısı uygulayarak kod sağlamlığı uygular. CTS, tüm yönetilen kodların kendi kendine açıklanmasını sağlar. Çeşitli Microsoft ve üçüncü taraf dil derleyicileri, CTS 'ye uygun yönetilen kod oluşturur. Bu, yönetilen kodun diğer yönetilen türleri ve örnekleri tüketebileceği, ancak tür uygunluğa ve tür güvenliği zorlarken emin olmak anlamına gelir.

Ayrıca, çalışma zamanının yönetilen ortamı birçok yaygın yazılım sorununu ortadan kaldırır. Örneğin, çalışma zamanı nesne yerleşimini otomatik olarak işler ve nesneleri artık kullanılmadıklarında serbest bırakır ve nesneler için başvuruları yönetir. Bu otomatik bellek yönetimi, en yaygın iki uygulama hatasını, bellek sızıntılarını ve geçersiz bellek başvurularını çözümler.

Çalışma zamanı geliştirici üretkenliğini da hızlandırır. Örneğin, programcılar geliştirme dillerinde uygulamalar yazarak, çalışma zamanının, sınıf kitaplığının ve diğer geliştiriciler tarafından diğer dillerde yazılmış bileşenlerin tam avantajlarından yararlanın. Çalışma zamanını hedeflemek üzere seçen tüm derleyici satıcıları bunu yapabilir. .NET Framework hedefleyen dil derleyicileri, mevcut uygulamalar için geçiş sürecini büyük ölçüde kolaylaştırmakta olan .NET Framework özelliklerini bu dilde yazılmış mevcut kod için kullanılabilir hale getirir.

Çalışma zamanı gelecekteki yazılım için tasarlanırken, bugün ve dün yazılımlarını da destekler. Yönetilen ve yönetilmeyen kod arasında birlikte çalışabilirlik, geliştiricilerin gerekli COM bileşenlerini ve DLL 'Leri kullanmaya devam etmesine olanak sağlar.

Çalışma zamanı, performansı artırmak için tasarlanmıştır. Ortak dil çalışma zamanı birçok standart çalışma zamanı hizmeti sağlasa da, yönetilen kod hiçbir şekilde yorumlanmaz. Tam zamanında (JıT) derleme adlı bir özellik, tüm yönetilen kodun, yürütüldüğü sistemin yerel makine dilinde çalışmasını sağlar. Bu arada, bellek Yöneticisi parçalanmış belleğin olanaklarını ortadan kaldırır ve performansı daha da artırmak için bellek başvurularını artırır.

Son olarak, çalışma zamanı Microsoft SQL Server ve Internet Information Services (IIS) gibi yüksek performanslı, sunucu tarafı uygulamalar tarafından barındırılabilir. Bu altyapı, iş mantığınızı yazmak için yönetilen kod kullanmanıza olanak sağlarken, sektördeki en iyi kurumsal sunucuların çalışma zamanı barındırmayı destekleyen üstün performansından de yararlanmaya devam eder.

## <a name="net-framework-class-library"></a>.NET Framework sınıf kitaplığı

.NET Framework sınıf kitaplığı, ortak dil çalışma zamanıyla sıkı bir şekilde tümleştirilen yeniden kullanılabilir türlerin bir koleksiyonudur. Sınıf kitaplığı, kendi yönetilen kodunuzun işlevselliği türettiği türler sağlayan nesne yönelimlidir. Bu yalnızca .NET Framework türlerini kullanımı kolay hale getirir, ancak aynı zamanda .NET Framework yeni özellikleriyle ilgili süreyi de azaltır. Ayrıca, üçüncü taraf bileşenleri .NET Framework sınıflarla sorunsuz bir şekilde tümleşir.

Örneğin, .NET Framework koleksiyon sınıfları kendi koleksiyon sınıflarınızı geliştirmek için bir dizi arabirim uygular. Koleksiyon sınıflarınız .NET Framework sınıflarla sorunsuz bir şekilde Blend.

Nesne yönelimli bir sınıf kitaplığından bekleneceğiniz gibi .NET Framework türler, dize yönetimi, veri toplama, veritabanı bağlantısı ve dosya erişimi gibi görevler de dahil olmak üzere bir dizi ortak programlama görevini gerçekleştirmenize olanak tanır. Bu ortak görevlere ek olarak, sınıf kitaplığı çeşitli özel geliştirme senaryolarını destekleyen türler içerir. Aşağıdaki uygulama ve hizmet türlerini geliştirmek için .NET Framework kullanın:

- Konsol uygulamaları. Bkz. [konsol uygulamaları oluşturma](../../standard/building-console-apps.md).

- Windows GUI uygulamaları (Windows Forms). Bkz. [Windows Forms](../winforms/index.md).

- Windows Presentation Foundation (WPF) uygulamaları. Bkz. [Windows Presentation Foundation](../wpf/index.md).

- ASP.NET uygulamaları. Bkz. [ASP.net Ile web uygulamaları](../develop-web-apps-with-aspnet.md).

- Windows hizmetleri. Bkz. [Windows hizmet uygulamalarına giriş](../windows-services/introduction-to-windows-service-applications.md).

- Windows Communication Foundation (WCF) kullanan hizmet odaklı uygulamalar. [WCF Ile hizmet odaklı uygulamalara](../wcf/index.md)bakın.

- Windows Workflow Foundation (WF) kullanan iş akışı etkin uygulamalar. Bkz. [Windows Workflow Foundation](../windows-workflow-foundation/index.md).

Windows Forms sınıfları, Windows GUI geliştirmeyi basitleştirecek olan kapsamlı bir yeniden kullanılabilir türler kümesidir. Bir ASP.NET Web formu uygulaması yazarsanız Web Forms sınıflarını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Gereksinimleri](system-requirements.md)
- [Yükleme kılavuzu](../install/index.md)
- [Geliştirme Kılavuzu](../development-guide.md)
- [Araçlar](../tools/index.md)
- [.NET örnekleri ve öğreticiler](../../samples-and-tutorials/index.md)
- [.NET Framework sınıf kitaplığı](https://go.microsoft.com/fwlink/?LinkID=227195)
