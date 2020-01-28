---
title: Genel bakış
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: c3a8394086c9d744630179b089a1f986af12b339
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734543"
---
# <a name="windows-forms-overview"></a>Windows Forms genel bakış

Aşağıdaki genel bakışta, akıllı istemci uygulamalarının avantajları, Windows Forms programlamanın ana özellikleri ve günümüzdeki kuruluşların ve son kullanıcıların ihtiyaçlarını karşılayan akıllı istemciler oluşturmak için Windows Forms nasıl kullanabileceğiniz açıklanır.

## <a name="windows-forms-and-smart-client-apps"></a>Windows Forms ve akıllı istemci uygulamaları

 Windows Forms, akıllı istemciler geliştirirsiniz. *Akıllı istemciler* , dağıtılması ve güncelleştirilmesi kolay grafiksel bir şekilde zengin uygulamalardır, Internet 'e bağlı olduklarında veya bağlantısı kesildiğinde çalışabilir ve geleneksel Windows tabanlı uygulamalardan daha güvenli bir şekilde yerel bilgisayardaki kaynaklara erişebilir.

### <a name="build-rich-interactive-user-interfaces"></a>Zengin, etkileşimli kullanıcı arabirimleri oluşturun

 Windows Forms, dosya sistemine okuma ve yazma gibi yaygın uygulama görevlerini kolaylaştıran bir dizi yönetilen kitaplık olan .NET Framework için bir akıllı istemci teknolojisidir. Visual Studio gibi bir geliştirme ortamı kullandığınızda, bilgi görüntüleyen, kullanıcılardan giriş isteyen ve uzak bilgisayarlarla ağ üzerinden iletişim kuran Windows Forms akıllı istemci uygulamaları oluşturabilirsiniz.

 Windows Forms, *form* , kullanıcıya bilgi görüntüleyen görsel bir yüzeydir. Genellikle formlara denetimler ekleyerek ve fare tıklamaları veya tuşa basma gibi kullanıcı eylemlerine yanıt geliştirmeye göre Windows Forms uygulamalar derleyebilirsiniz. *Denetim* , verileri görüntüleyen veya veri girişini kabul eden ayrı bir kullanıcı ARABIRIMI (UI) öğesidir.

 Bir Kullanıcı formunuza veya denetimlerinden birine bir şey yaparken eylem bir olay oluşturur. Uygulamanız kodu kullanarak bu olaylara tepki verir ve olayları gerçekleştiğinde işler. Daha fazla bilgi için [Windows Forms'ta olay işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md).

 Windows Forms formlara ekleyebileceğiniz çeşitli denetimler içerir: metin kutularını, düğmeleri, açılan kutuları, radyo düğmelerini ve hatta Web sayfalarını görüntüleyen denetimler. Bir formda kullanabileceğiniz tüm denetimlerin listesi için, bkz. [Windows Forms kullanılacak denetimler](./controls/controls-to-use-on-windows-forms.md). Mevcut bir denetim gereksinimlerinizi karşılamıyorsa, Windows Forms <xref:System.Windows.Forms.UserControl> sınıfını kullanarak kendi özel denetimlerinizi oluşturmayı da destekler.

 Windows Forms, Microsoft Office gibi yüksek kaliteli uygulamalardaki özellikleri taklit eden zengin Kullanıcı arabirimi denetimlerine sahiptir. <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip> denetimini kullandığınızda, metin ve görüntü içeren araç çubukları ve menüler oluşturabilir, alt menüler görüntüleyebilir ve metin kutuları ve Birleşik giriş kutuları gibi diğer denetimleri barındırabilirsiniz.

 Visual Studio 'daki sürükle ve bırak **Windows Form Tasarımcısı** , kolayca Windows Forms uygulamalar oluşturabilirsiniz. İmlecinizin bulunduğu denetimleri seçip form üzerinde istediğiniz yere eklemeniz yeterlidir. Tasarımcı, denetimleri hizalamayı sağlamak için kılavuz çizgileri ve yapışma çizgileri gibi araçlar sağlar. Visual Studio 'Yu veya komut satırında derlemeyi kullanıp kullanmayacağınızı, gelişmiş form düzenlerini daha az zaman oluşturmak için <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.SplitContainer> denetimleri kullanabilirsiniz.

 Son olarak, kendi özel kullanıcı arabirimi öğelerinizi oluşturmanız gerekiyorsa, <xref:System.Drawing> ad alanı çizgileri, daireleri ve diğer şekilleri doğrudan form üzerinde işlemek için büyük bir sınıf seçimi içerir.

> [!NOTE]
> Windows Forms denetimleri, uygulama etki alanları arasında sıralanabilen şekilde tasarlanmamıştır. Bu nedenle, Microsoft, <xref:System.MarshalByRefObject> <xref:System.Windows.Controls.Control> taban türü bunun mümkün olmasına rağmen bir <xref:System.AppDomain> sınırında Windows Forms denetimini geçirmeyi desteklemez. Birden çok uygulama etki alanına sahip Windows Forms uygulamalar, uygulama etki alanı sınırları arasında Windows Forms denetimleri geçirilmedikçe desteklenir.

#### <a name="create-forms-and-controls"></a>Form ve denetimler oluşturma

Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.

|Açıklama|Yardım konusu|
|-----------------|----------------|
|Formlarda denetimleri kullanma|[Nasıl yapılır: Windows Forms’a Denetimler Ekleme](./controls/how-to-add-controls-to-windows-forms.md)|
|<xref:System.Windows.Forms.ToolStrip> denetimini kullanma|[Nasıl yapılır: Tasarımcı Kullanarak Standart Öğelerle Temel bir ToolStrip Oluşturma](./controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|
|<xref:System.Drawing> ile grafik oluşturma|[Grafik Programlamaya Başlarken](./advanced/getting-started-with-graphics-programming.md)|
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl Sınıfından Devralma](./controls/how-to-inherit-from-the-usercontrol-class.md)|

### <a name="display-and-manipulate-data"></a>Verileri görüntüleme ve değiştirme
 Birçok uygulamanın, verileri bir veritabanından, XML dosyasından, XML Web hizmetinden veya başka bir veri kaynağından görüntülemesi gerekir. Windows Forms, bu tür tablosal verileri geleneksel bir satır ve sütun biçiminde görüntülemek için <xref:System.Windows.Forms.DataGridView> denetimi adlı esnek bir denetim sağlar, böylece her veri parçası kendi hücresini kaplar. <xref:System.Windows.Forms.DataGridView>kullandığınızda, tek tek hücrelerin görünümünü özelleştirebilir, rastgele satırları ve sütunları bir yere kilitleyebilir ve diğer özellikler arasında hücrelerde karmaşık denetimleri görüntüleyebilirsiniz.

 Ağ üzerinden veri kaynaklarına bağlanmak, Windows Forms akıllı istemcileri olan basit bir görevdir. <xref:System.Windows.Forms.BindingSource> bileşeni bir veri kaynağıyla bağlantıyı temsil eder ve verileri denetimlere bağlama, önceki ve sonraki kayıtlara gitme, kayıtları düzenlemeyle ve değişiklikleri özgün kaynağa geri kaydetme yöntemlerini sunar. <xref:System.Windows.Forms.BindingNavigator> denetimi, kullanıcıların kayıtlar arasında gezindiği <xref:System.Windows.Forms.BindingSource> bileşen üzerinde basit bir arabirim sağlar.

 Veri Kaynakları penceresini kullanarak veri bağlantılı denetimleri kolayca oluşturabilirsiniz. Pencere, projenizdeki veritabanları, Web Hizmetleri ve nesneler gibi veri kaynaklarını görüntüler. Öğeleri bu pencereden projenizdeki formlara sürükleyerek veriye göre bağlantılı denetimler oluşturabilirsiniz. Ayrıca, nesneleri veri kaynakları penceresinden var olan denetimlere sürükleyerek verileri verilere bağlayabilirsiniz.

 Windows Forms ' de yönetebileceğiniz başka bir veri bağlama türü *ayarlarından*oluşur. Çoğu akıllı istemci uygulaması, son bilinen form boyutu gibi bazı bilgileri korumalıdır ve kayıtlı dosyaların varsayılan konumları gibi Kullanıcı tercihi verilerini korur. Uygulama ayarları özelliği, istemci bilgisayardaki her iki ayar türünü depolamanın kolay bir yolunu sağlayarak bu gereksinimleri ele alır. Bu ayarları Visual Studio 'Yu veya bir kod düzenleyicisini kullanarak tanımladıktan sonra, ayarlar XML olarak kalıcı hale getirilir ve çalışma zamanında otomatik olarak belleğe geri okur.

#### <a name="display-and-manipulate-data"></a>Verileri görüntüleme ve değiştirme

Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.

|Açıklama|Yardım konusu|
|-----------------|----------------|
|<xref:System.Windows.Forms.BindingSource> bileşenini kullanma|[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama](./controls/bind-wf-controls-with-the-bindingsource.md)|
|ADO.NET veri kaynaklarıyla çalışma|[Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme](./controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Veri Kaynakları penceresini kullanma|[Visual Studio'da verilere Windows Forms denetimleri bağlama](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio)|
|Uygulama ayarlarını kullanma|[Nasıl yapılır: Uygulama Ayarları Oluşturma](./advanced/how-to-create-application-settings.md)|

### <a name="deploy-apps-to-client-computers"></a>Uygulamaları istemci bilgisayarlara dağıtma

Uygulamanızı yazdıktan sonra, uygulamayı kendi istemci bilgisayarlarına yükleyip çalıştırabilmeleri için kullanıcılarınıza göndermeniz gerekir. ClickOnce teknolojisini kullanırken, yalnızca birkaç tıklama kullanarak uygulamalarınızı Visual Studio içinden dağıtabilir ve kullanıcılarınıza Web üzerinde uygulamanıza işaret eden bir URL sağlayabilirsiniz. ClickOnce uygulamanızdaki tüm öğeleri ve bağımlılıkları yönetir ve uygulamanın istemci bilgisayara doğru şekilde yüklenmesini sağlar.

ClickOnce uygulamaları yalnızca Kullanıcı ağa bağlıyken çalışacak şekilde veya hem çevrimiçi hem de çevrimdışı çalıştırıldığında çalıştırılacak şekilde yapılandırılabilir. Bir uygulamanın çevrimdışı işlemi desteklemesi gerektiğini belirttiğinizde, ClickOnce kullanıcının **Başlat** menüsünde uygulamanıza bir bağlantı ekler. Kullanıcı, URL 'YI kullanmadan uygulamayı açabilir.

Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve uygulamanızın yeni bir kopyasını Web sunucunuza yayımlarsınız. ClickOnce, kullanılabilir bir güncelleştirme olduğunu algılayacak ve kullanıcının yüklemesini yükseltmeyecektir. Eski derlemeleri güncelleştirmek için özel programlama gerekmez.

#### <a name="deploy-clickonce-apps"></a>ClickOnce uygulamalarını dağıtma

ClickOnce 'a tam giriş için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment). Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.

|Açıklama|Yardım konusu|
|-----------------|----------------|
|ClickOnce kullanarak uygulama dağıtma|[Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|ClickOnce dağıtımını güncelleştirme|[Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|ClickOnce ile güvenliği yönetme|[Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

### <a name="other-controls-and-features"></a>Diğer denetimler ve Özellikler

Windows Forms ' de, iletişim kutuları oluşturma, yazdırma, yardım ve belge ekleme ve uygulamanızı birden çok dile yerelleştirme gibi genel görevleri hızlı ve kolay bir şekilde uygulamayı sağlayan birçok farklı özelliği vardır. Ayrıca, Windows Forms .NET Framework güçlü güvenlik sistemine bağlıdır. Bu sistemle, müşterilerinize daha güvenli uygulamalar bırakabilirsiniz.

#### <a name="implement-other-controls-and-features"></a>Diğer denetimleri ve özellikleri uygulama

Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.

|Açıklama|Yardım konusu|
|-----------------|----------------|
|Form içeriğini yazdırma|[Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](./advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](./advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'ta Güvenliğe Genel Bakış](security-in-windows-forms-overview.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
- [Yeni bir Windows Formu Oluşturma](creating-a-new-windows-form.md)
- [ToolStrip Denetimine Genel Bakış](./controls/toolstrip-control-overview-windows-forms.md)
- [DataGridView Denetimine Genel Bakış](./controls/datagridview-control-overview-windows-forms.md)
- [BindingSource Bileşenine Genel Bakış](./controls/bindingsource-component-overview.md)
- [Uygulama Ayarlarına Genel Bakış](./advanced/application-settings-overview.md)
- [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
