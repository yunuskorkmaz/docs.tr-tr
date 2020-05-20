---
title: Modern Masaüstü Uygulamalarını Dağıtma
description: Modern masaüstü uygulamaları dağıtma hakkında bilmeniz gereken her şey.
ms.date: 05/12/2020
ms.openlocfilehash: 4a4d93caf1c2f8f58d48ee3199bbe6983fa939f4
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423259"
---
# <a name="deploying-modern-desktop-applications"></a>Modern Masaüstü Uygulamalarını Dağıtma

Masaüstü uygulamaları geliştirirken, uygulamanızın paketlenmesi ve kullanıcıların makinelerine dağıtılması, dikkate alınması gereken bir şeydir. Paketleme, dağıtım ve yükleme ile ilgili sorun, genellikle geliştiricilerden farklı şeyler hakkında bilgi veren BT uzmanlarının genellerine denk gelmiştir.

Bu günlerde, geliştiricilerin ve BT uzmanlarının uygulamaları üretim ortamlarına taşımak için yakından çalıştığı DevOps kavramıyla karşılaşıyoruz. Ancak, 10 yıldan daha uzun bir süredir masaüstü Savaşı ile karşılaşdıysanız aşağıdaki hikayeyi gördünüz. Geliştiricilerin bir ekibi, proje son tarihlerini karşılamak için sabit bir şekilde birlikte çalışmaktadır. İş kullanıcıları, bir kullanıcının şirketi çalıştırmak için birçok kullanıcının makinesi üzerinde çalışan bir sisteme ihtiyacı olduğundan nervous. "D-Day" üzerinde, proje yöneticisi her bir geliştiricinin kod iyi çalışır durumda olduğunu ve her şeyin iyi olduğunu denetler, böylece sevk edebilirler. Ardından paket ekibi uygulama için kurulum oluşturma, uygulamayı her bir Kullanıcı makinesine dağıtma ve uygulamayı çalıştıran bir test kullanıcıları kümesi ile birlikte sunulur. Her türlü Kullanıcı arabirimini göstermeden önce, uygulamanın "yöntem ~ nesne ~ başarısız oldu" ifadesini belirten bir özel durum oluşturduğundan, bu yöntemler de çalışır. Panic, uçak aracılığıyla akışa başlar ve üçüncü taraf bir denetim sunan bir genç ve yorgun geliştiriciye yönelik olarak "geliştirme makinesinde çalıştı" adlı bir kısa araştırma noktası sağlar.

Masaüstü uygulamalarının yüklenmesi, iki ana nedenden dolayı geleneksel olarak bir nightmıledir:

- Geliştirme ve BT takımları arasında kapalı işbirliği kültürünün eksik olması.
- Üzerinde oluşturabileceğiniz bir katı paketleme ve dağıtım teknolojisinin olmaması.

Aslında, bazı durumlarda bir uygulamayı yükledikten sonra bir uygulama yükletireceğiz, çünkü

- Makinenizde bazı istenmeyen yan etkileri vardır.
- Daha önce yüklenmiş bazı uygulamalar çalışmayı durdurur.

Ayrıca, uygulamayı kaldırarak sistemi özgün durumuna geri yüklemeniz yeterli değildir. "DLL Hell" veya "Winrot" gibi terimleri sevdiğimiz bu durumu canlı olarak kullandık.

Bu bölümde, MALTıDAN bahsereceğiz. MSIX, Microsoft 'un, daha sonra paketleme teknolojisine yönelik sağlam bir temel sağlamak üzere önceki teknolojilerin en iyi şekilde yakalanmaya çalışan yepyeni yeni bir teknolojidir.

Bir paketleme teknolojisinin modernleştirme ile ne yapması gerekir? Ayrıca, bu paketleme, çok fazla para yatırılmış olan kurumsal BT için temel düzeyde kullanıma yöneliktir. Modernleştirme yalnızca en son teknolojileri kullanmayla ilgili değildir. Şirketiniz özelliği istemcinize yönlendirene kadar bir iş gereksiniminin tanımlandığı zamandan itibaren Pazar süresini azaltmaya de yardımcı olur.

## <a name="the-modern-application-lifecycle"></a>Modern uygulama yaşam döngüsü

Günümüzde, geliştiriciler bir uygulamanın kodunu yazar ve derler ve sonra oluşturulan varlıkları BT uzmanlarına iletir. Ardından, BT uzmanları uygulamayı yeniden yapılandırır ve genellikle bir App-V paketleme biçiminde bir MSI veya daha yakın zamanda yeniden paketleyebilir. Uygulama daha sonra farklı kanallar ve araçlar aracılığıyla dağıtılır. Bu yaklaşımın ana sorunlarından biri genellikle "paketleme Paralysis" olarak bilinir. Bu, bir uygulama güncelleştirmesi veya bir işletim sistemi güncelleştirmesi her seferinde bu döngüsünün tekrarlandığı bir sorundur.

İşlemin aşağıdaki resme yansıtıldığını görebilirsiniz:

![Modern BT yaşam döngüsünü gösteren diyagram](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

Şirketlerin bu paketleme döngüsünü üç bağımsız döngüye bölmek için bir yol gerekir:

- İşletim sistemi güncelleştirmeleri
- Uygulama güncelleştirmeleri
- Özelleştirme

![Modern BT sanallaştırma döngüsünü gösteren diyagram](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

Önceki diyagramda şunları yapabilirsiniz:

- Uygulamalarınızı yeniden paketlemenize gerek kalmadan temel alınan işletim sistemini güncelleştirin.
- Özgün Geliştirici paketini yeniden paketlemenize gerek kalmadan, özelleştirmeleri bu bilgisayardan etkinleştirin.

Bu radikal değişiklik, aşağıdaki resimde gösterildiği gibi yeni ve modern BT yaşam döngüsünü bize yönlendirir:

![Microsoft araçları kullanarak uygulama yaşam döngüsünü gösteren diyagram](./media/deploy-modern-applications/microsoft-it-tools.png)

Geliştiriciler uygulamayı oluşturur ve BT uzmanlarının yeniden paketleme gereksinimi olmadan tükettiği ve yapılandırabileceği bir MSIX paketi oluşturur. Microsoft, MSIX teknolojisinin yanı sıra paketleri yeniden paketlemeden özelleştirmenize ve yapılandırmanıza izin veren araçlar oluşturmuştur.

## <a name="msix-the-next-generation-of-deployment"></a>MSIX: sonraki nesil dağıtım

MALTıDAN önce, kurulum sihirbazları, MSI, ClickOnce, App-V ve betik gibi çeşitli Paketleme Teknolojileri bulunmaktadır. Bu teknolojilerin her biri kendi gücünü içerir ve Microsoft, MALTıYı derlemek için en iyi olanı seçmeyi kararmıştır. MSIX, her birinin en iyi şekilde seçilmesi için mevcut teknolojilerin temelleri üzerine kurulmuştur:

- App-V = \> containerleştirme
- ClickOnce = \> Otomatik güncelleştirme
- MSI = \> dağıtımı kolay

MSIX ile, tüm bu özelliklerle bir yükleyici teknolojisi alırsınız.

![MSIX oluşturma üzerinde etkisi olan farklı teknolojileri gösteren diyagram](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a>MALTıLARıN avantajları

#### <a name="never-regret-installing-an-app"></a>Hiçbir uygulamayı yükleme

MSIX, öngörülebilir, güvenilir ve güvenli bir dağıtım sağlar. Paket bildiriminde bulunan bildirim temelli yöntemi, işletim sisteminin uygulamanızın ihtiyaç duyacağı her varlığı izlemesine olanak sağlar. Ayrıca yan etkileri olmayan doğru bir temiz kaldırma de sağlar.

#### <a name="disk-space-optimization"></a>Disk alanı iyileştirmesi

MSIX, bir uygulamanın kullanıcının makine disk alanında sahip olduğu parmak izini azaltmak için iyileştirilmiştir. Dosyalarınızın tek bir örnek depolaması oluşturur. Diğer bir deyişle, aynı DLL ile iki farklı paketleriniz varsa, DLL iki kez yüklenmez. Bu sorun, belirli bir uygulamanın yüklediği tüm dosyaları, bildirime dayalı olarak teşekkürler, bu sorunu ele alır. Ayrıca, bir DLL 'nin yan yana farklı sürümlerine sahip etmenize de olanak tanır.

Kaynak paketlerinin kullanımı sayesinde, kolayca çok dilli uygulamalar oluşturabilirsiniz ve işletim sistemi, kullanılan uygulamaları yüklemeyi de gerçekleştirir.

#### <a name="network-optimization"></a>Ağ iyileştirmesi

MSIX, fark güncelleştirmeleri olarak adlandırılan bir özelliği etkinleştiren bayt blok düzeyindeki dosyalardaki farklılıkları algılar. Bu, uygulama güncelleştirmelerinde yalnızca güncelleştirilmiş bayt bloklarının indirileceği anlamına gelir.

![MSIX 'ın fark güncelleştirmelerini nasıl yönettiğini gösteren bir diyagram](./media/deploy-modern-applications/msix-managing-updates.png)

Akış yüklemesi sayesinde, uygulamanın diğer bölümleri arka planda indirilirken, Kullanıcı uygulamanız üzerinde çalışmaya hızlı bir başlangıç yapabilir. Bu özellik kullanıcılarınız için etkileyici bir deneyime katkıda bulunur.

İsteğe bağlı paketler özelliği sayesinde uygulama dağıtımınızda bileşen elde edersiniz. böylece, gerektiğinde bunları indirebilirsiniz.

#### <a name="simple-packaging-and-deployment"></a>Basit paketleme ve dağıtım

AppManifest, sürüm oluşturmayı bildirir ve her uygulama için standart bir şekilde tanımlanır. Ayrıca, bir katı güvenlik temeli sağlayan varlıklarınızı imzalamanız için bir yol sağlar.

#### <a name="os-managed"></a>İşletim sistemi yönetiliyor

İşletim sistemi, bir uygulamayı yüklemek, güncelleştirmek ve kaldırmak için tüm işlemlerin tamamını işler. Uygulamalar Kullanıcı başına yüklenir ancak yalnızca bir kez indirilir ve disk parmak izini en aza indirir. Microsoft, Windows 7 ' de MALTıDA deneyim sağlamaya çalışmaktadır.

#### <a name="windows-provides-integrity-for-the-app"></a>Windows uygulama için bütünlük sağlar

Dijital imzaların kullanımıyla, güvenilmeyen kaynaklardan bir uygulama yüklememeniz garanti edebilirsiniz. MSIX, şu nedenle de değişiklik yapılmasını engelliyor:

- Dosya karmalarının kaydını tutar.
- Yükleme sonrasında bir dosyanın değiştirilip değiştirilmediğini algılar.

#### <a name="works-for-the-entire-app-catalog"></a>Tüm uygulama kataloğu için geçerlidir

MALTıYA ilişkin en az şeylerden biri, xCopy dağıtımı, ClickOnce veya mağazaya gitmek istediğinizden bile, tüm uygulama kataloğu, Windows Forms, WPF, MFC/ATL, Delfi için çalışmadır. aynı MSIX paketini kullanabilirsiniz.

### <a name="tools"></a>Araçlar

#### <a name="windows-application-packaging-project"></a>Windows Uygulaması Paketleme Projesi

 **Windows Application Packaging Project**   Masaüstü uygulamanız için bir paket oluşturmak üzere Visual Studio 'Da Windows uygulama paketleme proje projesini kullanabilirsiniz. Ardından, bu paketi Microsoft Store yayımlayabilir veya bir veya daha fazla bilgisayara yükleyebilirsiniz.

#### <a name="msix-packaging-tool"></a>MSIX paketleme aracı

MSIX paketleme aracı mevcut Win32 uygulamalarınızı MSIX biçimine yeniden paketlemenize olanak sağlar. Dönüşümler için hem etkileşimli bir kullanıcı arabirimi hem de bir komut satırı sunar ve kaynak kodu olmadan bir uygulamayı dönüştürebilme olanağı sağlar.

![MSIX paketleme aracı](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a>Paket desteği çerçevesi

Paket desteği çerçevesi, kaynak koda erişiminiz olmadığında var olan Win32 uygulamanıza düzeltmeler uygulamanıza yardımcı olan bir açık kaynaklı pakettir. Bu, bir MSIX kapsayıcısında çalıştırılabilir. Paket desteği çerçevesi, uygulamanızın modern çalışma zamanı ortamının en iyi yöntemlerini izlemesini sağlar.

#### <a name="app-installer"></a>Uygulama yükleyicisi

Uygulama yükleyicisi, uygulama paketine çift tıklayarak Windows 10 uygulamalarının yüklenmesine izin verir. Bu, kullanıcıların Windows 10 uygulamalarını dağıtmak için PowerShell veya diğer geliştirici araçlarını kullanması gerekmediği anlamına gelir. Uygulama yükleyicisi de Web, isteğe bağlı paketler ve ilgili kümelerden bir uygulama yükleyebilir.

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a>Mevcut bir Win32 masaüstü uygulamasından MSIX paketi oluşturma

Var olan bir Win32 uygulamasından bir MSIX paketi oluşturma işlemini ilerlim. Bu örnekte, Windows Forms bir uygulama kullanacağız.

Başlamak için çözümünüze yeni bir proje ekleyin, Windows uygulama paketleme projesini seçin ve bir ad verin.

![Yeni Windows uygulaması paketleme projesi ekleniyor](./media/deploy-modern-applications/add-packaging-project.png)

Paketleme projesinin yapısını görebilir ve *uygulamalar*adlı özel bir klasör görürsünüz. Bu klasörün içinde, pakete dahil etmek istediğiniz uygulamaları belirtebilirsiniz. Birden fazla olabilir.

![Paketleme projesinin yapısı](./media/deploy-modern-applications/packaging-project.png)

*Uygulamalar* klasörüne sağ tıklayın ve Visual Studio çözümünden paketlemek istediğiniz Windows Forms projeyi seçin.

![Paketleme projesine Windows Forms projesi ekleme](./media/deploy-modern-applications/add-winforms-project.png)

Bu noktada, paketi derleyip oluşturabilir, ancak birkaç şeyi inceleyelim. Daha iyi bir kullanıcı deneyimi sağlamak için, Visual Studio, modern bir uygulamanın kutucuk çubuğu ve Başlat menüsü için simgeleri ve kutucuk varlıklarını işlemesi gereken tüm görsel varlıkları otomatik olarak oluşturabilir. Bildirim tasarımcısına erişmek için *Package. appxmanifest* dosyasını açın. Daha sonra, **Oluştur**' a tıklayarak projenizde bulunan belirli bir görüntüden tüm görsel varlıkları oluşturabilirsiniz.

![Visual Studio 'da bildirim Tasarımcısı 'nın ekran görüntüsü](./media/deploy-modern-applications/manifest-designer.png)

*Package. appxmanifest* dosyası için kodu açarsanız, birçok ilginç şeyi görebilirsiniz.

Sağ tarafta `<Package>` bir `<Identity>` düğüm vardır. Bu, paketlenmiş uygulamanızın, işletim sistemi tarafından yönetilecek kimliğini alacağınız yerdir.

![Kimlik düğümü](./media/deploy-modern-applications/identity-node.png)

Düğümünde, `<Capabilities>` uygulamanın ihtiyacı olan tüm gereksinimleri bulabilir ve bu, `<rescap:Capability Name="runFullTrust" \>` işletim sisteminin bir Win32 uygulaması olduğundan, uygulamayı tam güven modunda çalıştırmasını söyler.

![Yetenekler düğümü](./media/deploy-modern-applications/capabilities-node.png)

Paketleme projesini çözüm için başlangıç projesi olarak ayarlayın ve *Çalıştır*' ı seçin. Bu, şu şekilde yapılır:

- Windows Forms uygulamayı derleyin.
- Derleme sonuçlarından bir MSIX paketi oluşturun.
- Paketleri dağıtın.
- Geliştirme makinesine yerel olarak yükler.
- Uygulamayı başlatma.

![Yüklü uygulamamız](./media/deploy-modern-applications/our-installed-application.png)

Bu sayede, MSIX 'nin Windows 10 ' da tam olarak tümleşik olması için temiz yükleme ve kaldırma deneyiminden sahip olursunuz.

Son aşama, MSIX paketini başka bir makineye nasıl dağıtabileceğinizi öğrenin.

Paketleme projesine sağ tıklayın, **Mağaza** menüsünü seçin ve ardından **uygulama paketleri oluştur** seçeneğini belirleyin.

Ardından, depoya yüklemek veya dışarıdan yükleme paketleri oluşturmak için paket oluşturma arasında seçim yapabilirsiniz. Birçok modernleştirme senaryosunda, **Dışarıdan yükleme paketleri oluşturmak istiyorum**' u seçin.

![Paketleri yapılandırma](./media/deploy-modern-applications/configuring-packages.png)

Aynı MDıSIX paketine istediğiniz kadar dahil olmak üzere hedeflemek istediğiniz farklı mimarilerin arasından seçim yapabilirsiniz.

Son adım, son yükleme varlıklarını nereye dağıtmak istediğinizi bildirmaktır.

![Güncelleştirme ayarlarını yapılandırma](./media/deploy-modern-applications/configure-update-settings.png)

Kurumsal dosya sunucularınızda paylaşılan bir UNC yolunun Web sunucusunu kullanmayı seçebilirsiniz. Uygulamanızı nasıl güncellemek istediğinizi belirtmek için ayarlara dikkat edin. Uygulama güncelleştirmelerini bir sonraki bölümde ele alacağız.

Ayrıntılı adım adım kılavuz için bkz. [Visual Studio kullanarak kaynak koddan bir masaüstü uygulaması paketleme](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).

## <a name="auto-updates-in-msix"></a>MSIX 'de otomatik güncelleştirmeler

Windows Mağazası Windows Update kullanarak harika bir güncelleştirme mekanizması içerir. Çoğu kurumsal senaryoda, masaüstü uygulamalarınızı dağıtmak için mağazayı kullanamazsınız. Bu nedenle, uygulamanız için güncelleştirmeleri yapılandırmak ve bunları kullanıcılarınıza çekmek için benzer bir yönteme ihtiyacınız vardır.

Windows 10 özelliklerinin ve MSIX paketlerinin bir birleşimini kullanarak kullanıcılarınız için harika bir güncelleştirme deneyimi sağlayabilirsiniz. Aslında kullanıcının her türlü teknik olması gerekmez, ancak sorunsuz bir uygulama güncelleştirme deneyiminden de faydalanır.

Güncellemelerinizi kullanıcıyla iki farklı şekilde etkileşimde bulunmak üzere yapılandırabilirsiniz:

- Kullanıcı tarafından istenen güncelleştirmeler: işletim sistemi, uygulamanın yüklenmek üzere olduğunu kullanıcıya bildirmek için bazı otomatik oluşturulmuş iyi Kullanıcı arabirimini gösterir. Bu Kullanıcı arabirimini, yükleme dosyalarınızda belirttiğiniz özelliklere göre oluşturur.

- Arka planda sessiz güncelleştirmeler. Bu seçenekle kullanıcılarınızın güncelleştirmelerin farkında olması gerekmez.

Ayrıca, uygulama ne zaman veya düzenli olarak başlatıldığında güncelleştirmeler gerçekleştirmek istediğinizi de yapılandırabilirsiniz. Dışarıdan yükleme özellikleri sayesinde, uygulama çalışırken bu güncelleştirmeleri de alabilirsiniz.

Bu tür bir dağıtım kullandığınızda *. AppInstaller*adlı özel bir dosya oluşturulur. Bu basit dosya aşağıdaki bölümleri içerir:

- *. AppInstaller* dosyasının konumu
- Uygulamanın ana MDıSIX paketi özellikleri
- Güncelleştirme davranışı

![. AppInstaller dosyası](./media/deploy-modern-applications/appinstaller-file.png)

Bu dosya ile birlikte, Microsoft bir bağlantıdan yükleme işlemini başlatmak için özel bir URL protokolü tasarlamıştır:

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

Bu protokol tüm tarayıcılarda çalışarak Windows 10 ' da harika bir kullanıcı deneyimiyle yükleme işlemini başlatır. İşletim sistemi yükleme işlemini yönettiğinden, bu uygulamanın ' dan yüklendiği konumdan haberdar olur ve işlemden etkilenen tüm dosyaları izler.

MSIX, paketin bazı özelliklerini otomatik olarak göstermek için bir kullanıcı arabirimi oluşturur. Bu, her uygulama için ortak bir yükleme deneyimi sağlar.

Yeni MSIX paketini oluşturduktan ve dağıtım sunucusuna taşındıktan sonra, bu değişiklikleri yansıtmak için *. AppInstaller* dosyasını düzenlemeniz gerekir, bu da genellikle yeni msix dosyasının sürümü ve yoludur. Kullanıcı uygulamayı bir sonraki başlattığında, sistem değişikliği algılayacak ve yeni sürüm için dosyaları arka planda indirirler. Bu işlem tamamlandığında, yükleme, kullanıcılarınız için şeffaf yeni uygulama başlatıldığında yürütülür.

>[!div class="step-by-step"]
>[Önceki](example-migration-core.md)
