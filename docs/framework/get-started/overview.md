---
title: ".NET Framework'e Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
caps.latest.revision: "34"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de9d94c9b4dfbdccb4ea5b3a7281715460d076a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="overview-of-the-net-framework"></a>.NET Framework'e Genel Bakış

.NET Framework oluşturmak ve yeni nesil XML Web Hizmetleri ve uygulamaları çalıştırmak destekleyen bir teknolojidir. .NET Framework aşağıdaki hedefleri karşılamak üzere tasarlanmıştır:

- Tutarlı bir sağlamak için nesne odaklı programlama ortamlarının nesne kodu depolanır ve yerel olarak yürütülen olup olmadığını, Internet dağıtılmış veya uzaktan yürütülen yerel olarak yürütülür.

- Kod yürütme ortamı sağlamak için yazılım dağıtımı ve sürüm çakışmaları azaltır.

- Kodun bir bilinmeyen veya yarı güvenilir üçüncü taraf tarafından oluşturulan kodu da dahil olmak üzere, güvenli yürütülmesini yükseltir bir kod yürütme ortamı sağlamak için.

- Kod yürütmeyi sağlamak için performans sorunlarını ortadan ortamı komut dosyası veya ortamlar yorumlanır.

- Deneyimi Geliştirici uygulamaları, Windows tabanlı uygulamalar ve Web tabanlı uygulamalar gibi yaygın olarak değişen türleri arasında tutarlı yapmak için.

- .NET Framework temel alınarak kodu başka bir kod ile tümleşir emin olmak için endüstri standartları üzerinde tüm iletişimi oluşturmak için.

> [!NOTE]
> Kullanıcılar ve geliştiriciler için .NET Framework genel bir giriş için bkz: [Başlarken](../../../docs/framework/get-started/index.md).

.NET Framework ortak dil çalışma zamanı (CLR) ve .NET Framework sınıf kitaplığı oluşur. Ortak dil çalışma zamanı .NET Framework'ün oluşturmaktadır. Çalışma zamanı de kesin tür güvenliği ve güvenlik ve sağlamlık yükseltmek diğer kod doğruluğu biçimlerini zorlarken bellek yönetimi, iş parçacığı yönetimi ve Uzaktan iletişimini gibi Çekirdek Hizmetleri sağlayan kodu yürütme zaman yöneten bir aracı olarak düşünün. Aslında, kod Yönetimi kavramı çalışma zamanının temel bir ilkesidir. Kod hedefleri çalışma zamanı hedef değil kod yönetilmeyen kodu olarak bilinen sırada yönetilen kod çalışma zamanı denir. Sınıf kitaplığı kapsamlı, nesne yönelimli geleneksel komut satırı veya grafik kullanıcı arabirimi (GUI) uygulamaları Web gibi ASP.NET tarafından sağlanan en son yenilikleri dayalı uygulamalar arasında değişen uygulama geliştirmek için kullandığınız yeniden kullanılabilir türler koleksiyonudur Formlar ve XML Web Hizmetleri.

.NET Framework ortak dil çalışma zamanı süreçlerinin yüklemek ve yönetilen kod yürütmeyi başlatmak yönetilmeyen bileşenler tarafından böylece yönetilen ve yönetilmeyen özellikleri yararlanan bir yazılım ortamı oluşturma barındırılabilir. .NET Framework yalnızca birkaç çalışma zamanı ana bilgisayarları sağlar ancak üçüncü taraf çalışma zamanı hosts geliştirmeyi de destekler.

Örneğin, ASP.NET, yönetilen kod için ölçeklenebilir, sunucu tarafı bir ortam sağlamak için çalışma zamanı barındırır. ASP.NET uygulamaları ve XML Web Hizmetleri, her ikisi de bu konunun ilerleyen bölümlerinde açıklanan etkinleştirmek için doğrudan çalışma zamanı ile ASP.NET çalışır.

Internet Explorer, çalışma zamanı (bir MIME türü uzantısı biçiminde) barındıran yönetilmeyen bir uygulama örneğidir. Çalışma zamanı barındırmak için Internet Explorer'ı kullanarak yönetilen bileşenleri ya da Windows Forms denetimleri HTML belgelere katıştırma sağlar. Bu şekilde çalışma zamanı barındırma yönetilen mobil kod mümkün hale getirir, ancak ile önemli geliştirmeler, yalnızca yönetilen kod, yarı güvenilir yürütme ve yalıtılmış dosya depolama gibi sağlar.

Aşağıdaki çizimde, ortak dil çalışma zamanı ve uygulamalarınızı ve genel sistem sınıf kitaplığı ilişkiyi gösterir. Çizimde de nasıl yönetilen kod gösterilmektedir büyük mimari içinde çalışır.

![Yönetilen kod büyük mimari içinde](../../../docs/framework/get-started/media/circle.gif "daire") bağlamda .NET Framework

Aşağıdaki bölümlerde daha ayrıntılı .NET Framework'ün önemli özellikleri açıklanmaktadır.

## <a name="features-of-the-common-language-runtime"></a>Ortak dil çalışma zamanı özellikleri

Ortak dil çalışma zamanı bellek, iş parçacığı, kod yürütmeyi, kod güvenlik doğrulama, derleme ve diğer sistem hizmetleri yönetir. Bu özellikler, ortak dil çalışma zamanı üzerinde çalışan yönetilen kod için iç.

Güvenlik ile ilgili güven, kendi kaynak (örneğin, Internet, Kurumsal ağa veya yerel bilgisayar) dahil faktörlerinin bağlı olarak çeşitli derecelerde yönetilen bileşenleri kazanırsınız. Başka bir deyişle, yönetilen bir bileşen olabilir veya aynı etkin uygulamada kullanılsa bile dosya erişim işlemleri, kayıt defteri erişimi işlemler veya diğer önemli işlevleri gerçekleştirmek mümkün olmayabilir.

Çalışma zamanı ortak tür sistemi (CTS) adlı bir katı türü ve kod doğrulama altyapısı uygulayarak kod sağlamlık ayrıca zorlar. CTS tüm yönetilen kod kendiliğinden açıklayıcı olmasını sağlar. Çeşitli Microsoft ve üçüncü taraf dil derleyicileri CTS uyumlu yönetilen kod oluşturur. Bu yönetilen kod diğer yönetilen türler ve örnekleri, tür uygunluğunu ve tür güvenliği kesinlikle zorlarken tüketebileceği anlamına gelir.

Ayrıca, çalışma zamanının yönetilen ortamı birçok genel yazılım sorununu ortadan kaldırır. Örneğin, çalışma zamanı otomatik olarak nesne düzenini işler ve artık kullanıldığı sırada serbest nesnelere başvurular yönetir. Bu otomatik bellek yönetimi iki en yaygın uygulama hataları ve bellek sızıntıları geçersiz bellek başvuruları çözümler.

Çalışma zamanı ayrıca Geliştirici üretkenliği hızlandırır. Örneğin, programcıları kendi seçtikleri geliştirme dilde uygulamalar yazmayı henüz çalışma zamanı, sınıf kitaplığı ve bileşenlerinin başka dillerde diğer geliştiriciler tarafından yazılan tüm avantajlarından yararlanın. Çalışma zamanı hedeflemek için seçen derleyici satıcı bunu yapabilirsiniz. .NET Framework hedefleyen dil derleyicileri, .NET Framework'ün özellikleri olan mevcut uygulamalar için geçiş işlemi büyük ölçüde kolaylaştırma bu dilinde yazılmış varolan kod kullanılabilmesini sağlar.

Çalışma zamanı gelecekteki yazılım için tasarlandığından, bugün ve dün yazılım da destekler. Yönetilen ve yönetilmeyen kod birlikte çalışabilirliği gerekli COM bileşenleri ve DLL'ler kullanmaya devam etmek geliştiricilerin sağlar.

Çalışma zamanı performansı artırmak için tasarlanmıştır. Ortak dil çalışma zamanı birçok standart çalışma zamanı Hizmetleri sağlasa da, yönetilen kod asla yorumlanır. Tam zamanında (JIT) derleme adlı bir özelliği, yürütülmekte olduğu sistem yerel makine dilinde çalıştırmak için tüm yönetilen kod sağlar. Bu sırada, bellek yöneticisi parçalanmış bellek olasılıklar kaldırır ve bellek yere göre-daha fazla performansı artırmak için başvuru artırır.

Son olarak, çalışma zamanı, Microsoft SQL Server ve Internet Information Services (IIS) gibi yüksek performanslı, sunucu tarafı uygulamalar tarafından barındırılabilir. Bu altyapı hala üstün çalışma zamanı barındırma destekleyen sektörün en iyi Kurumsal sunucularının performansı tadını çıkarmaya çalışırken, iş mantığı yazmak için yönetilen kodu kullanmanıza olanak sağlar.

## <a name="net-framework-class-library"></a>.NET Framework sınıf kitaplığı

.NET Framework sınıf kitaplığı, ortak dil çalışma zamanı ile sıkı tümleştirme yeniden kullanılabilir tür koleksiyonudur. Sınıf kitaplığı, yönetilen kodunuzu işlevselliği türetilen türler sağlar ve yönelik, nesnesidir. Bu yalnızca .NET Framework türleri kullanımı kolay hale getirir, ancak ayrıca .NET Framework'ün yeni özellikler öğrenmeye gereken süreyi kısaltır. Ayrıca, üçüncü taraf bileşenleri, .NET Framework'teki sınıflarla sorunsuz şekilde tümleşir.

Örneğin, .NET Framework koleksiyon sınıfları kendi koleksiyon sınıfları geliştirmek için arabirimleri kümesi uygular. Koleksiyon sınıfları, .NET Framework'teki sınıflarla sorunsuz bir şekilde karışır.

Bir nesne yönelimli Sınıf Kitaplığı'ndan beklediğiniz gibi .NET Framework türleri, bir dizi dize yönetimi, veri toplama, veritabanı bağlantısını ve dosya erişimi gibi görevleri de dahil olmak üzere genel programlama görevleri gerçekleştirmenize olanak sağlar. Bu ortak görevlere ek olarak, sınıf kitaplığı çeşitli özel geliştirme senaryolarını destekleyen türler içerir. .NET Framework uygulamaları ve Hizmetleri aşağıdaki türlerini geliştirmek için kullanın:

- Konsol uygulamaları. Bkz: [konsol uygulamaları oluşturma](../../../docs/standard/building-console-apps.md).

- Windows GUI uygulamaları (Windows Forms). Bkz: [Windows Forms](../../../docs/framework/winforms/index.md).

- Windows Presentation Foundation (WPF) uygulamaları. Bkz: [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).

- ASP.NET uygulamaları. Bkz: [Web uygulamaları ASP.NET ile](../../../docs/framework/develop-web-apps-with-aspnet.md).

- Windows hizmetleri. Bkz: [giriş Windows hizmet uygulamaları](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).

- Windows Communication Foundation (WCF) kullanan hizmet odaklı uygulamalar. Bkz: [WCF ile hizmet odaklı uygulamalar](../../../docs/framework/wcf/index.md).

- Windows Workflow Foundation (WF) kullanan iş akışı özellikli uygulamalar. Bkz: [.NET Framework'teki iş akışlarının oluşturulmasını](http://msdn.microsoft.com/en-us/cbf3880f-dc7b-466d-b808-1109b1223f4a).

Windows Forms, böylelikle Windows GUI geliştirmeyi kolaylaştıran yeniden kullanılabilir türleri kapsamlı bir kümesini sınıflarıdır. Bir ASP.NET Web formu uygulama yazarsanız, Web Forms sınıflarını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[Sistem gereksinimleri](../../../docs/framework/get-started/system-requirements.md)   
[Yükleme Kılavuzu](../../../docs/framework/install/index.md)   
[Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)   
[Araçları](../../../docs/framework/tools/index.md)   
[.NET framework örnekleri](http://msdn.microsoft.com/en-us/177055f8-4a1f-43e7-aee6-995c196079b1)   
[.NET framework sınıf kitaplığı](http://go.microsoft.com/fwlink/?LinkID=227195)
