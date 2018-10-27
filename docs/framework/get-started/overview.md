---
title: .NET Framework'e Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8519f7ecfc430aaa9b888f9239f669e6e54eb02
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192752"
---
# <a name="overview-of-the-net-framework"></a>.NET Framework'e Genel Bakış

.NET Framework'ü oluşturma ve çalıştırma yeni nesil uygulamaların ve XML Web Hizmetleri destekleyen bir teknolojidir. .NET Framework, şu hedefleri yerine getirmek için tasarlanmıştır:

- Tutarlı sağlamak için nesne yönelimli nesne kodunun saklandığı ve yerel olarak yürütüldüğü programlama ortamı, Internet dağıtılmış veya uzaktan yürütüldü yerel olarak yürütülür.

- Bir kod yürütme ortamı sağlamak için yazılım dağıtımı ve sürüm oluşturma çakışmalarını en aza.

- Bilinmeyen veya yarı güvenilir üçüncü taraflarca oluşturulan kod da dahil olmak üzere, kodun güvenli yürütülmesini yükseltir bir kod yürütme ortamı sağlamak için.

- Bir kod yürütme sağlamak için performans sorunlarını ortadan kaldıran ortamı Script veya yorumlanan ortamların.

- Geliştirici deneyiminin uygulamaları, Windows tabanlı uygulamalar ve Web tabanlı uygulamalar gibi çok çeşitlilik gösteren türleri arasında tutarlı olmak için.

- Yapı tüm iletişimi endüstri standartları, .NET Framework tabanlı kodun başka tüm kodlarla tümleştiğinden emin olmak için.

> [!NOTE]
> Kullanıcılara ve geliştiricilere yönelik .NET Framework'e Genel bir giriş için bkz: [Başlarken](../../../docs/framework/get-started/index.md).

.NET Framework ortak dil çalışma zamanı (CLR) ve .NET Framework sınıf kitaplığından oluşur. Ortak dil çalışma zamanı, .NET Framework'ün temelidir. Çalışma zamanını, bellek yönetimi ve iş parçacığı yönetimi uzaktan iletişimini gibi temel hizmetleri de katı tür güvenliği ve güvenlik ve sağlamlık diğer kod doğruluğu formlarını sağlayan yürütme zamanında kodu yöneten aracı olarak düşünün. Aslında, kod Yönetimi kavramı çalışma zamanı temel bir ilkesidir. Kod hedefleri çalışma zamanı hedeflemiyor kod yönetilmeyen kod olarak bilinir sırasında yönetilen kod çalışma zamanı bilinir. Sınıf kitaplığı kapsamlı ve nesne odaklı geleneksel komut satırı veya grafiksel kullanıcı arabirimi (GUI) uygulamaları, Web gibi ASP.NET tarafından sağlanan en son yenilikleri temel uygulamaları arasında değişen uygulamalar geliştirmek için kullandığınız tipler koleksiyonudur Forms ve XML Web Hizmetleri.

.NET Framework, böylece hem yönetilen hem de yönetilmeyen özelliklerden yararlanan bir yazılım ortamı oluşturma, ortak dil çalışma zamanı kendi süreçlerine yükleyen ve yönetilen kodun yürütülmesini başlatan, yönetilmeyen bileşenler tarafından barındırılabilir. .NET Framework yalnızca birkaç çalışma zamanı ana bilgisayarları sağlar ancak aynı zamanda üçüncü taraf çalışma zamanı ana bilgisayarları için geliştirmeyi destekler.

Örneğin, ASP.NET çalışma zamanı, yönetilen kod için ölçeklenebilir, sunucu tarafı bir ortam sağlamak üzere barındırır. ASP.NET, ASP.NET uygulamaları ve XML Web Hizmetleri, ikisi için de bu konunun ilerleyen bölümlerinde açıklanan etkinleştirmek için doğrudan çalışma zamanı ile çalışır.

Internet Explorer çalışma zamanını (bir MIME türü uzantı biçiminde) barındıran yönetilmeyen uygulama örneğidir. Çalışma zamanını barındırmak için Internet Explorer'ı kullanarak yönetilen bileşenleri veya Windows Forms denetimlerini, HTML belgelerine katıştırmanıza olanak sağlar. Bu şekilde çalışma zamanı barındırma yönetilen mobil kodu mümkün kılar, ancak önemli gelişmeler ile yalnızca yönetilen kod, yarı güvenli yürütme ve yalıtılmış dosya depolama gibi sunar.

Aşağıda, ortak dil çalışma zamanı ve sınıf kitaplığı, uygulamalarınıza ve genel sisteminizle ilişkisi gösterilmiştir. Yönetilen kod gösterimde ayrıca daha büyük bir mimaride çalışır.

![Yönetilen kod içinde daha büyük bir mimarinin](../../../docs/framework/get-started/media/circle.gif "daire") NET Framework bağlamında

Aşağıdaki bölümlerde daha ayrıntılı .NET Framework'ün ana özellikleri açıklanmaktadır.

## <a name="features-of-the-common-language-runtime"></a>Ortak dil çalışma zamanı özellikleri

Ortak dil çalışma zamanı, bellek, iş parçacığı, kod yürütmeyi, kod güvenlik onaylamayı, derlemeyi ve diğer sistem hizmetlerini yönetir. Bu özellikler, ortak dil çalışma zamanında çalışan yönetilen kod için içsel.

Güvenlik, güven, bunların kaynağını (örneğin, Internet, kurumsal ağ veya yerel bilgisayar) içeren bir dizi etkene bağlı olarak değişen düzeylerde yönetilen bileşenleri kazanırsınız. Başka bir deyişle, yönetilen bir bileşen olabilir veya aynı etkin uygulamada kullanıldığında bile dosya erişimi işlemlerini, kayıt defteri erişim işlemlerini veya diğer önemli işlevleri gerçekleştirmek mümkün olmayabilir.

Çalışma zamanı Ayrıca ortak tür sistemi (CTS) adı verilen sıkı bir tür ve kod doğrulama altyapısını uygulayarak kod sağlamlığı zorlar. CTS, tüm yönetilen kodun kendiliğinden açıklayıcı olmasını sağlar. Çeşitli Microsoft ve üçüncü taraf dil derleyicileri CTS ile uyumlu yönetilen kod oluşturur. Bu, yönetilen kod diğer yönetilen türleri ve örnekleri, tür uygunluğunu ve tür güvenliği kesinlikle zorlarken tüketmediğinden emin anlamına gelir.

Ayrıca, çalışma zamanının yönetilen ortamı birçok genel yazılım sorununu ortadan kaldırır. Örneğin, çalışma zamanı otomatik olarak nesne düzeni işler ve artık kullanıldığı sırada bırakmadan nesnelere başvurular yönetir. Bu otomatik bellek yönetimi, iki en yaygın uygulama hataları, bellek sızıntılarını ve geçersiz bellek referanslarını çözümler.

Çalışma zamanı, aynı zamanda Geliştirici üretkenliğini de hızlandırır. Örneğin, programcılar kendi tercih ettiğiniz geliştirme dilde uygulamalar yazmak henüz çalışma zamanı, sınıf kitaplığı ve diğer geliştiriciler tarafından diğer dillerde yazılmış bileşenler tam anlamıyla. Çalışma zamanını hedef olarak seçen bir derleyici tedarikçisi bunu yapabilirsiniz. .NET Framework'ü hedefleyen dil derleyicileri özellikler .NET Framework'ün mevcut uygulamalar için geçiş işlemini büyük ölçüde kolaylaştırma o dilde yazılmış varolan kod tarafından kullanılabilir hale getirir.

Çalışma zamanı gelecek yazılım için tasarlandığından, bugün ve Dünkü yazılımları da destekler. Yönetilen ve yönetilmeyen kod arasındaki birlikte işlerlik, geliştiricilerin gerekli COM bileşenlerini ve DLL'leri kullanmaya devam etmek sağlar.

Çalışma zamanı, performansı artırmak için tasarlanmıştır. Ortak dil çalışma zamanının birçok standart çalışma zamanı Hizmetleri sağlasa da, yönetilen kod asla yorumlanmaz. Just-ın-time (JIT) derleme olarak adlandırılan bir özellik çalıştırma yürütülmekte olan sistemin yerel makine dilinde işletilecek yönetilen kodun sağlar. Bu arada bellek yöneticisi, parçalanmış bellek olasılıklarını kaldırır ve bellek konumu daha da performansı artırmak için başvuru artırır.

Son olarak, çalışma zamanı, Microsoft SQL Server ve Internet Information Services (IIS) gibi yüksek performanslı, sunucu tarafı uygulamaları tarafından barındırılabilir. Bu altyapı, yönetilen kod çalışma zamanı barındırmayı destekleyen sektördeki en iyi Kurumsal sunucuları, üstün performans hala çıkarırken iş mantığınızı yazmanıza olanak sağlar.

## <a name="net-framework-class-library"></a>.NET Framework sınıf kitaplığı

.NET Framework sınıf kitaplığı, ortak dil çalışma zamanıyla sıkı bir şekilde tümleştirilen tipler koleksiyonudur. Sınıf kitaplığı türleri kendi yönetilen kodunuzun işlevselliği türetildiği sağlayan, nesne odaklı olup. Bu yalnızca .NET Framework türlerini kullanımı kolay hale getirir, ancak .NET Framework'ün yeni özelliklerini öğrenmeyle ilişkili süreyi de azaltır. Ayrıca, üçüncü taraf bileşenler, .NET Framework'teki sınıflarla sorunsuzca tümleştirin.

Örneğin, .NET Framework koleksiyon sınıfları kendi koleksiyon sınıflarınızı geliştirmek için arabirimleri kümesi uygulayın. Koleksiyon sınıfları .NET Framework sınıfları ile sorunsuz bir şekilde karışır.

Bir nesne yönelimli sınıf kitaplığından beklediğiniz gibi .NET Framework türleri bir dizi dize yönetimi, veri toplama, veritabanı bağlantısı ve dosya erişimi gibi görevler de dahil olmak üzere ortak programlama görevlerini gerçekleştirmenize olanak tanır. Bu ortak görevlerin yanı sıra, sınıf kitaplığı çeşitli özel geliştirme senaryolarını destekleyen türleri içerir. Aşağıdaki türde uygulamaları ve hizmetleri geliştirmek için .NET Framework'ü kullanın:

- Konsol uygulamaları. Bkz: [konsol uygulamaları oluşturma](../../../docs/standard/building-console-apps.md).

- Windows GUI uygulamaları (Windows Forms). Bkz: [Windows Forms](../../../docs/framework/winforms/index.md).

- Windows Presentation Foundation (WPF) uygulamaları. Bkz: [Windows Presentation Foundation](../../../docs/framework/wpf/index.md).

- ASP.NET uygulamaları. Bkz: [Web uygulamaları ASP.NET ile](../../../docs/framework/develop-web-apps-with-aspnet.md).

- Windows hizmetleri. Bkz: [giriş Windows hizmet uygulamaları](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md).

- Windows Communication Foundation (WCF) kullanan hizmet odaklı uygulamalar. Bkz: [WCF ile hizmet odaklı uygulamalar](../../../docs/framework/wcf/index.md).

- Windows Workflow Foundation (WF) kullanan iş akışı etkin uygulamalar. Bkz: [.NET Framework'te iş akışları oluşturarak](https://msdn.microsoft.com/library/cbf3880f-dc7b-466d-b808-1109b1223f4a).

Windows Forms sınıfları Windows GUI geliştirmeyi büyük ölçüde kolaylaştıran tipler kapsamlı bir kümesidir. Bir ASP.NET Web formu uygulaması yazıyorsanız, Web formu sınıflarını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Gereksinimleri](../../../docs/framework/get-started/system-requirements.md)   
- [Yükleme kılavuzu](../../../docs/framework/install/index.md)   
- [Geliştirme Kılavuzu](../../../docs/framework/development-guide.md)   
- [Araçlar](../../../docs/framework/tools/index.md)   
- [.NET framework örnekleri](https://msdn.microsoft.com/library/177055f8-4a1f-43e7-aee6-995c196079b1)   
- [.NET framework sınıf kitaplığı](https://go.microsoft.com/fwlink/?LinkID=227195)
