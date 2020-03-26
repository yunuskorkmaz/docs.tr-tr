---
title: .NET Framework'e Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- application development [.NET Framework]
- common language runtime
- common language runtime, about
- common language runtime, overview
ms.assetid: 29848c96-fc36-462d-8072-ba223a40b697
ms.openlocfilehash: ace42738118cde4bcda4b78607d7bdb045d3501e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248927"
---
# <a name="overview-of-net-framework"></a>.NET Framework'e Genel Bakış

.NET Framework, Windows uygulamaları ve web hizmetleri oluşturmayı ve çalıştırmayı destekleyen bir teknolojidir. .NET Framework aşağıdaki hedefleri gerçekleştirmek için tasarlanmıştır:

- Nesne kodunun yerel olarak depolanıp yürütülüp yürütülmediği, yerel olarak yürütülüp yürütülmediği veya web tarafından dağıtılıp yürütülmediği veya uzaktan yürütülüp yürütülmediği tutarlı bir nesne yönelimli programlama ortamı sağlamak için.

- Yazılım dağıtımını ve sürüm çakışmalarını en aza indiren bir kod yürütme ortamı sağlamak için.

- Bilinmeyen veya yarı güvenilen bir üçüncü taraf tarafından oluşturulan kod da dahil olmak üzere kodun güvenli bir şekilde yürütülmesini destekleyen bir kod yürütme ortamı sağlamak için.

- Komut dosyası veya yorumlanan ortamların performans sorunlarını ortadan kaldıran bir kod yürütme ortamı sağlamak.

- Geliştirici deneyimini Windows tabanlı uygulamalar ve Web tabanlı uygulamalar gibi çok çeşitli uygulama türlerinde tutarlı hale getirmek için.

- .NET Framework'e dayalı kodun diğer kodlarla tümlağandığından emin olmak için endüstri standartlarında tüm iletişimi oluşturmak.

> [!NOTE]
> Hem kullanıcılar hem de geliştiriciler için .NET Framework'e genel bir giriş için [bkz.](index.md)

.NET Framework ortak dil çalışma süresi (CLR) ve .NET Framework sınıf kitaplığından oluşur. Ortak dil çalışma süresi .NET Framework'ün temelidir. Çalışma zamanını yürütme sırasında kodu yöneten, bellek yönetimi, iş parçacığı yönetimi ve remoting gibi temel hizmetleri sağlayan ve aynı zamanda sıkı tür güvenliğini ve güvenliği ve sağlamlığı teşvik eden diğer kod doğruluğu biçimlerini uygulayan bir aracı olarak düşünün. Aslında, kod yönetimi kavramı çalışma zamanının temel bir ilkesidir. Çalışma saatini hedefleyen kod yönetilen kod olarak bilinirken, çalışma süresini hedeflemeyen kod yönetilmeyen kod olarak bilinir. Sınıf kitaplığı, geleneksel komut satırı veya grafik kullanıcı arabirimi (GUI) uygulamalarından, web gibi ASP.NET tarafından sağlanan en son yeniliklere dayalı uygulamalara kadar çeşitli uygulamalar geliştirmek için kullandığınız yeniden kullanılabilir türlerin kapsamlı, nesne yönelimli bir koleksiyonudur Formlar ve XML web hizmetleri.

.NET Framework, ortak dil çalışma süresini kendi süreçlerine yükleyen ve yönetilen kodun yürütülmesini başlatan ve bu nedenle hem yönetilen hem de yönetilmeyen özelliklerden yararlanan bir yazılım ortamı oluşturan yönetilmeyen bileşenler tarafından barındırılabilir. .NET Framework yalnızca birkaç çalışma zamanı ana bilgisayar sağlamaz, aynı zamanda üçüncü taraf çalışma zamanı ana bilgisayarlarının geliştirilmesini de destekler.

Örneğin, ASP.NET yönetilen kod için ölçeklenebilir, sunucu tarafı ortamı sağlamak için çalışma saatini barındırAbilir. ASP.NET, her ikisi de bu makalede daha sonra tartışılan ASP.NET uygulamaları ve XML web hizmetlerini etkinleştirmek için çalışma süresiyle doğrudan çalışır.

Internet Explorer, çalışma zamanını barındıran (MIME türü uzantısı biçiminde) yönetilmeyen bir uygulama örneğidir. Çalışma süresini barındırmak için Internet Explorer'ı kullanmak, yönetilen bileşenleri veya Windows Formları denetimlerini HTML belgelerine gömmenize olanak tanır. Çalışma süresini bu şekilde barındırmak yönetilen mobil kodu mümkün kılar, ancak yalnızca yarı güvenilen yürütme ve yalıtılmış dosya depolama gibi kod tekliflerini yöneten önemli geliştirmelerle.

Aşağıdaki resimde, ortak dil çalışma zamanı ve sınıf kitaplığı ile uygulamalarınız ve genel sistem arasındaki ilişki gösterilmektedir. Resimde ayrıca yönetilen kodun daha büyük bir mimari içinde nasıl çalıştığı da gösterilmektedir.

![Yönetilen kodun daha büyük bir mimari içinde nasıl çalıştığını gösteren ekran görüntüsü.](./media/overview/language-runtime-class-library-relationship.gif)

Aşağıdaki bölümlerde .NET Framework'ün ana özellikleri daha ayrıntılı olarak açıklayınız.

## <a name="features-of-the-common-language-runtime"></a>Ortak dil çalışma zamanının özellikleri

Ortak dil çalışma süresi bellek, iş parçacığı yürütme, kod yürütme, kod güvenliği doğrulama, derleme ve diğer sistem hizmetlerini yönetir. Bu özellikler, ortak dil çalışma zamanında çalışan yönetilen kodiçin içseldir.

Güvenlikle ilgili olarak, yönetilen bileşenler, kökenlerini (Internet, kurumsal ağ veya yerel bilgisayar gibi) içeren bir dizi etkene bağlı olarak çeşitli güven derecelerine verilir. Bu, yönetilen bir bileşenin aynı etkin uygulamada kullanılsa bile dosya erişim işlemleri, kayıt defteri erişim işlemleri veya diğer hassas işlevleri gerçekleştirebileceği veya gerçekleştiremediği anlamına gelir.

Çalışma süresi ayrıca, ortak tür sistemi (CTS) adı verilen katı bir tür ve kod doğrulama altyapısı uygulayarak kod sağlamlığını da zorlar. CTS, yönetilen tüm kodun kendi kendini tanımlamasını sağlar. Çeşitli Microsoft ve üçüncü taraf dil derleyicileri CTS'ye uygun yönetilen kod oluşturur. Bu, yönetilen kodun diğer yönetilen türleri ve örnekleri tüketebilirken, tür sadakatini ve tür güvenliğini sıkı bir şekilde uygulayabileceği anlamına gelir.

Buna ek olarak, çalışma zamanının yönetilen ortamı birçok yaygın yazılım sorunlarını ortadan kaldırır. Örneğin, çalışma zamanı nesne düzenini otomatik olarak işler ve nesneleri başvuruları yönetir ve artık kullanılmadıklarında serbest bırakılır. Bu otomatik bellek yönetimi, en yaygın iki uygulama hatasını, bellek sızıntılarını ve geçersiz bellek başvurularını giderir.

Çalışma süresi aynı zamanda geliştirici üretkenliğini de hızlandırır. Örneğin, programcılar uygulamalarını seçtikleri geliştirme dillerinde yazar, ancak çalışma süresi, sınıf kitaplığı ve diğer geliştiriciler tarafından diğer dillerde yazılmış bileşenlerden tam olarak yararlanır. Çalışma saatini hedeflemeyi seçen herhangi bir derleyici satıcısı bunu yapabilir. .NET Framework'ü hedefleyen dil derleyicileri,.NET Framework'ün özelliklerini o dilde yazılmış varolan koda uygun hale getirerek varolan uygulamalar için geçiş işlemini büyük ölçüde kolaylaştırır.

Çalışma süresi geleceğin yazılımı için tasarlanmış olsa da, aynı zamanda bugünün ve dünün yazılımLarını destekler. Yönetilen ve yönetilmeyen kodlar arasında birlikte çalışabilirlik, geliştiricilerin gerekli COM bileşenlerini ve DL'leri kullanmaya devam etmesini sağlar.

Çalışma süresi performansı artırmak için tasarlanmıştır. Ortak dil çalışma süresi birçok standart çalışma zamanı hizmeti sağlasa da, yönetilen kod hiçbir zaman yorumlanamaz. Tam zamanında (JIT) derleme adı verilen bir özellik, yönetilen tüm kodların yürütüldettiği sistemin ana makine dilinde çalışmasını sağlar. Bu arada, bellek yöneticisi parçalanmış bellek olanaklarını kaldırır ve performansı daha da artırmak için bellek yerelliğini artırır.

Son olarak, çalışma süresi Microsoft SQL Server ve Internet Information Services (IIS) gibi yüksek performanslı, sunucu tarafındaki uygulamalar tarafından barındırılabilir. Bu altyapı, işletme mantığınızı yazmak için yönetilen kodu kullanmanıza olanak sağlarken, aynı zamanda çalışma zamanı barındırmayı destekleyen endüstrinin en iyi kurumsal sunucularının üstün performansının keyfini çıkarır.

## <a name="net-framework-class-library"></a>.NET Framework sınıf kitaplığı

.NET Framework sınıf kitaplığı, ortak dil çalışma süresiyle sıkı bir şekilde tümleşen yeniden kullanılabilir türler topluluğudur. Sınıf kitaplığı, kendi yönetilen kodunuzu işlevsellik türeten türleri sağlayan nesne yönelimlidir. Bu sadece .NET Framework türlerinin kullanımını kolaylaştırmakla kalmıyor, aynı zamanda .NET Framework'ün yeni özelliklerini öğrenmeyle ilişkili süreyi de azaltır. Buna ek olarak, üçüncü taraf bileşenleri .NET Framework'deki sınıflarla sorunsuz bir şekilde tümleşir.

Örneğin, .NET Framework toplama sınıfları kendi koleksiyon sınıflarınızı geliştirmek için bir dizi arabirim uygular. Koleksiyon sınıflarınız .NET Framework'deki sınıflarla sorunsuz bir şekilde uyum sağlar.

Nesne yönelimli sınıf kitaplığından beklediğiniz gibi,.NET Framework türleri dize yönetimi, veri toplama, veritabanı bağlantısı ve dosya erişimi gibi bir dizi ortak programlama görevini gerçekleştirmenize olanak tanır. Bu ortak görevlere ek olarak, sınıf kitaplığı çeşitli özel geliştirme senaryolarını destekleyen türleri içerir. .NET Framework'ü aşağıdaki uygulama ve hizmet türlerini geliştirmek için kullanabilirsiniz:

- Konsol uygulamaları. [Yapı Konsolu Uygulamalarına](../../standard/building-console-apps.md)bakın.

- Windows GUI uygulamaları (Windows Forms). [Bkz. Windows Formları](../winforms/index.md).

- Windows Presentation Foundation (WPF) uygulamaları. [Bkz. Windows Sunu Vakfı.](../wpf/index.md)

- ASP.NET uygulamalar. [ASP.NET ile Web Uygulamaları'na](../develop-web-apps-with-aspnet.md)bakın.

- Windows hizmetleri. [Bkz. Windows Hizmet Uygulamalarına Giriş](../windows-services/introduction-to-windows-service-applications.md).

- Windows Communication Foundation (WCF) kullanan hizmet odaklı uygulamalar. [WCF ile Hizmet Odaklı Uygulamalara](../wcf/index.md)Bakın.

- Windows İş Akışı Temeli 'ni (WF) kullanarak iş akışı etkin uygulamalar. [Bkz. Windows İş Akışı Temeli.](../windows-workflow-foundation/index.md)

Windows Forms sınıfları, Windows GUI geliştirmeyi büyük ölçüde basitleştiren kapsamlı bir yeniden kullanılabilir tür kümesidir. bir ASP.NET Web Formu uygulaması yazarsanız, Web Formları sınıflarını kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sistem Gereksinimleri](system-requirements.md)
- [Yükleme kılavuzu](../install/index.md)
- [Geliştirme rehberi](../development-guide.md)
- [Araçlar](../tools/index.md)
- [.NET örnekleri ve eğitimleri](../../samples-and-tutorials/index.md)
- [.NET API tarayıcısı](../../../api/index.md)
