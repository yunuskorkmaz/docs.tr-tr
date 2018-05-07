---
title: Windows Forms'a Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 50c88aec8ac57be2ab317ac91464d68503607738
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-overview"></a>Windows Forms'a Genel Bakış
Aşağıdaki özette akıllı istemci uygulamaları, Windows Forms programlama ve bugünün kuruluşlar ve son kullanıcıların ihtiyaçlarını karşılamak akıllı istemciler oluşturmak için Windows Forms nasıl kullanabileceğiniz ana özelliklerini avantajları açıklanır.  
  
## <a name="windows-forms-and-smart-client-applications"></a>Windows Forms ve akıllı istemci uygulamaları  
 Windows Forms ile akıllı istemciler geliştirin. *Akıllı istemciler* kolay dağıtmak ve güncelleştirme, grafik zengin uygulamalar bağlı veya Internet bağlantısı kesilmiş çalışabilir ve daha güvenli bir şekilde daha geleneksel yerel bilgisayardaki kaynaklara erişebilir Windows tabanlı uygulamalar.  
  
### <a name="building-rich-interactive-user-interfaces"></a>Yapı zengin ve etkileşimli kullanıcı arabirimleri  
 Windows Forms için bir akıllı istemci teknolojisidir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], okuma ve dosya sistemine yazma gibi ortak uygulama görevlerini basitleştirmek yönetilen kitaplıkları kümesi. Visual Studio gibi bir geliştirme ortamı kullandığınızda, bir ağ üzerinden uzak bilgisayarlarla iletişim bilgilerini görüntülemek ve giriş kullanıcılarından istemek Windows Forms akıllı istemci uygulamaları oluşturabilirsiniz.  
  
 Windows Forms'ta bir *form* üzerinde görüntü bilgileri kullanıcıya görsel bir yüzey. Normalde formlarına denetimler ekleme ve fare tıklamaları veya anahtar basarsa gibi kullanıcı eylemlerini yanıtlarını geliştirerek Windows Forms uygulamaları oluşturun. A *denetim* veri girişi kabul eder ya da verileri görüntüleyen bir ayrık kullanıcı arabirimi (UI) öğesidir.  
  
 Bir kullanıcı bir şey formunuz veya denetimlerinden birine yaptığında, eylem bir olay oluşturur. Uygulamanız kod kullanarak bu olaylara yanıt verir ve bunlar ortaya çıktığında olayları işler. Daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
 Windows Forms formlarına ekleme denetimlerini çeşitli içerir: metin kutuları, düğmeler, aşağı açılan kutuları, radyo düğmeleri ve bile Web sayfalarını görüntüleyen denetimler. Bir form üzerinde kullanabileceğiniz tüm denetimler listesi için bkz: [Windows Forms'ta kullanılacak denetimler](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Varolan bir denetim ihtiyaçlarınızı karşılamıyorsa kullanarak kendi özel denetimler oluşturma Windows Forms de destekler <xref:System.Windows.Forms.UserControl> sınıfı.  
  
 Windows Forms özellikleri Microsoft Office gibi gelişmiş uygulamalarda öykünmek zengin UI denetimleri vardır. Kullandığınızda <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip> denetim, araç çubukları ve alt menüler görüntülemek ve metin kutuları ve birleşik giriş kutuları gibi diğer denetimleri konak metin ve görüntüler içeren menüleri oluşturabilirsiniz.  
  
 Visual Studio sürükle ve bırak Windows Form Tasarımcısı ile Windows Forms uygulamaları kolayca oluşturabilirsiniz. Yalnızca imlecinizi denetimleriyle seçin ve form üzerinde istediğiniz yere ekleyin. Tasarımcı denetimleri hizalama dışında mücadele olabilmesi için kılavuz çizgileri ve ek satırları gibi araçlar sağlar. Visual Studio'yu kullanın ya da komut satırında derleme olup olmadığını kullanabileceğiniz <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.SplitContainer> Gelişmiş oluşturmak için denetimleri form düzenleri daha kısa sürede.  
  
 Son olarak, kendi özel kullanıcı Arabirimi öğeleri oluşturmanız gerekiyorsa <xref:System.Drawing> ad alanı, büyük seçimi çizgiler, daireler ve diğer şekiller doğrudan bir form üzerinde işlemek için sınıflar içerir.  
  
> [!NOTE]
>  Windows Forms denetimleri uygulama etki alanları arasında sıralanması için tasarlanmamıştır. Bu nedenle, Microsoft Windows Forms denetimi arasında geçirme desteklemez bir <xref:System.AppDomain> sınır, olsa bile <xref:System.Windows.Controls.Control> temel türü <xref:System.MarshalByRefObject> mümkün olduğunu belirtmek için göründüğü. Windows Forms denetimleri uygulama etki alanı sınırlarında geçirilir sürece birden çok uygulama etki alanları Windows Forms uygulamaları desteklenir.  
  
#### <a name="help-creating-forms-and-controls"></a>Yardım formlar ve denetimler oluşturma  
 Bu özellikler kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Form üzerinde denetimleri kullanma|[Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|  
|Kullanarak <xref:System.Windows.Forms.ToolStrip> denetimi|[Nasıl yapılır: Tasarımcı Kullanarak Standart Öğelerle Temel bir ToolStrip Oluşturma](../../../docs/framework/winforms/controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|  
|Grafik oluşturma <xref:System.Drawing>|[Grafik Programlamaya Başlarken](../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl Sınıfından Devralma](../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
### <a name="displaying-and-manipulating-data"></a>Verileri görüntüleme ve düzenleme  
 Birçok uygulama, verileri bir veritabanı, XML dosyası, XML Web hizmeti veya başka bir veri kaynağını görüntülemeniz gerekir. Windows Forms adlı esnek bir denetim sağlar <xref:System.Windows.Forms.DataGridView> her veri parçası kendi hücrenin kapladığı bir geleneksel bir satır ve sütun biçiminde, bu tür tablo verilerini görüntüleme için denetim. Kullandığınızda <xref:System.Windows.Forms.DataGridView>, tek tek hücrelerin görünüşünü özelleştirme, rasgele satırları kilitlemek ve sütunlarında yerleştirin ve diğer özellikler arasında hücreleri içinde karmaşık denetimleri görüntüler.  
  
 Bir ağ üzerinden veri kaynaklarına bağlanma, Windows Forms akıllı istemcilerle basit bir görevdir. <xref:System.Windows.Forms.BindingSource> Bileşeni, yeni Windows Forms'ta ile [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ve [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], bir veri kaynağına bağlantıyı temsil eder ve önceki ve sonraki kayıtlara gezinme, kayıtları düzenleme ve kaydetme denetimlere veri bağlama için yöntemleri gösterir özgün kaynağına değişiklikler. <xref:System.Windows.Forms.BindingNavigator> Denetim üzerinden basit bir arabirim sağlar <xref:System.Windows.Forms.BindingSource> kayıtlar arasında gezinmek kullanıcılar için bileşen.  
  
 Veri Kaynakları penceresini kullanarak verilere bağlı denetimler kolayca oluşturabilirsiniz. Pencerenin veritabanları, Web Hizmetleri ve nesneleri gibi veri kaynakları projenize görüntüler. Veri bağlama denetimleri projenizdeki forms üzerine bu pencereden öğeleri sürükleyerek oluşturabilirsiniz. Ayrıca veri mevcut denetimleri verileri için mevcut denetimleri üzerine veri kaynakları penceresinden nesneleri sürükleyerek bağlama.  
  
 Windows Forms'ta yönetebileceğiniz veri bağlamanın başka bir tür *ayarları*. Çoğu akıllı istemci uygulamaları, forms, bilinen son boyutu gibi kendi çalışma zamanı durumu hakkındaki bazı bilgileri korumak ve kaydedilen dosyaları için varsayılan konumları gibi kullanıcı tercihi verileri korur. Uygulama ayarları özellik ayarları her iki tür istemci bilgisayarda depolamak için kolay bir yol sağlayarak bu gereksinimleri karşılar. Visual Studio veya kod düzenleyicisini kullanarak bu ayarları tanımladıktan sonra ayarları XML olarak kalıcı ve çalışma zamanında otomatik olarak geri belleğe okuyun.  
  
#### <a name="help-displaying-and-manipulating-data"></a>Verileri Yardım görüntüleme ve düzenleme  
 Bu özellikler kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Kullanarak <xref:System.Windows.Forms.BindingSource> bileşeni|[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama](../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|İle çalışma [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] veri kaynakları|[Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme](../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|  
|Veri Kaynakları penceresini kullanma|[İzlenecek yol: Bir Windows formunda veri görüntüleme](http://msdn.microsoft.com/library/f6e08c2c-c792-43de-adf3-3e52c0100225)|  
|Uygulama ayarları kullanma|[Nasıl yapılır: Uygulama Ayarları Oluşturma](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)|  
  
### <a name="deploying-applications-to-client-computers"></a>İstemci bilgisayarlara uygulamaları dağıtma  
 Uygulamanızı yazdıktan sonra yükleyebilir ve kendi istemci bilgisayarlarda çalıştırmak için kullanıcılarınızın uygulamaya göndermeniz gerekir. Kullandığınızda [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] teknolojisi uygulamalarınızdan Visual Studio içinde yalnızca birkaç tıklama kullanarak dağıtabilir ve Web uygulamanıza işaret eden bir URL ile kullanıcılarınız sağlayın. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] tüm öğeleri ve bağımlılıklarını, uygulamanızda yönetir ve uygulama, istemci bilgisayarda doğru şekilde yüklendiğini sağlar.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulamaları yalnızca kullanıcı ağa bağlandığında çalıştırmak için veya her ikisi de çevrimiçi çalıştırmak için yapılandırılmış ve çevrimdışı olabilir. Bir uygulama çevrimdışı işlemi desteklemesi gereken belirttiğinizde [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] kullanıcının uygulamanızda bir bağlantı ekler **Başlat** menüsü. Kullanıcı uygulamayı açabilir ve URL'yi kullanarak olmadan.  
  
 Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve yeni bir kopya uygulamanızın Web sunucunuza yayımlayın. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] bir güncelleştirme kullanılabilir olduğunu algılar ve kullanıcının yüklemeyi yükseltme; özel programlama eski derlemeleri güncelleştirmek için gereklidir.  
  
#### <a name="help-deploying-clickonce-applications"></a>ClickOnce uygulamaları dağıtma Yardımı  
 Bir tam giriş için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment). Bu özellikler kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın,  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Kullanarak bir uygulamayı dağıtma [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Güncelleştirme bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımı|[Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Güvenlik ile yönetme [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
### <a name="other-controls-and-features"></a>Diğer denetimleri ve özellikleri  
 Windows Forms'ta uygulama ortak görevleri hızlı ve kolay iletişim kutuları oluşturma, yazdırma, Yardım ve belgeler ekleme ve uygulamanız birden çok dilde yerelleştirme için destek gibi olun birçok özelliği vardır. Ayrıca, Windows Forms güçlü güvenlik sistemde dayanır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bu sistemiyle müşterileriniz için daha güvenli uygulamalar serbest bırakabilirsiniz.  
  
#### <a name="help-implementing-other-controls-and-features"></a>Diğer denetimleri ve özellikleri uygulama Yardım  
 Bu özellikler kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Form içeriğinin yazdırma|[Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|  
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'ta Güvenliğe Genel Bakış](../../../docs/framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'a Başlarken](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Yeni bir Windows Formu Oluşturma](../../../docs/framework/winforms/creating-a-new-windows-form.md)  
 [ToolStrip Denetimine Genel Bakış](../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [DataGridView Denetimine Genel Bakış](../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [BindingSource Bileşenine Genel Bakış](../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
