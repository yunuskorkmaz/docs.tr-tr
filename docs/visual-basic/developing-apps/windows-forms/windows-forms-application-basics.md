---
title: Windows Forms Uygulaması Temelleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 051c2be00ca18799eeb2f5253a9b236bbcf82d21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592385"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Forms Uygulaması Temelleri (Visual Basic)
Önemli Visual Basic kullanıcıların bilgisayarlarına yerel olarak çalışan Windows Forms uygulamaları oluşturma olanağı bir parçasıdır. Windows Forms kullanan uygulama ve kullanıcı arabirimini oluşturmak için Visual Studio'yu kullanabilirsiniz. Bir Windows Forms uygulaması sınıflardan üzerine inşa edilmiştir <xref:System.Windows.Forms> ad alanı.  
  
## <a name="designing-windows-forms-applications"></a>Forms uygulamaları Windows tasarlama  
 Visual Studio ile Windows Forms ve Windows hizmet uygulamaları oluşturabilirsiniz. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Windows Forms'a Başlarken](../../../framework/winforms/getting-started-with-windows-forms.md). Oluşturma ve Windows Forms program bilgiler verilmektedir.  
   
-   [Windows Forms denetimleri](../../../framework/winforms/controls/index.md). Windows Forms denetimlerini ayrıntılı konulara koleksiyonu.  
  
-   [Windows hizmet uygulamaları](../../../framework/windows-services/index.md). Windows Hizmetleri oluşturma açıklayan konulara listeler.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Yapı zengin ve etkileşimli kullanıcı arabirimleri  
 Windows Forms bileşenidir akıllı istemci [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], okuma ve dosya sistemine yazma gibi ortak uygulama görevlerini etkinleştirmek yönetilen kitaplıkları kümesi. Visual Studio gibi bir geliştirme ortamı kullanarak, bir ağ üzerinden uzak bilgisayarlarla bilgilerini görüntülemek, kullanıcılardan girdi istemek ve iletişim kuran Windows Forms uygulamaları oluşturabilirsiniz.  
  
 Windows Forms'ta bir kullanıcıya bilgi görüntü üzerinde bir görsel yüzey biçimidir. Windows Forms uygulamaları formlarında denetimleri yerleştirme ve fare tıklamaları veya anahtar basarsa gibi kullanıcı eylemlerini yanıtlarını geliştirerek yaygın olarak oluşturun. A *denetim* veri girişi kabul eder ya da verileri görüntüleyen bir ayrık kullanıcı arabirimi (UI) öğesidir.  
  
### <a name="events"></a>Olaylar  
 Bir kullanıcı bir şey formunuz veya denetimlerinden birine yaptığında, bir olay oluşturur. Uygulamanız kod kullanarak bu olaylara yanıt verir ve bunlar ortaya çıktığında olayları işler. Daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Denetimler  
 Windows Forms formlarında yerleştirebilirsiniz denetimleri çeşitli içerir: metin kutuları, düğmeler, aşağı açılan kutuları, radyo düğmeleri ve bile Web sayfalarını görüntüleyen denetimler. Bir form üzerinde kullanabileceğiniz tüm denetimler listesi için bkz: [Windows Forms'ta kullanılacak denetimler](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Varolan bir denetim ihtiyaçlarınızı karşılamıyorsa kullanarak kendi özel denetimler oluşturma Windows Forms de destekler <xref:System.Windows.Forms.UserControl> sınıfı.  
  
 Windows Forms özellikleri Microsoft Office gibi gelişmiş uygulamalarda öykünmek zengin UI denetimleri vardır. Kullanarak <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip> denetim, araç çubukları ve alt menüler görüntülemek ve metin kutuları ve birleşik giriş kutuları gibi diğer denetimleri konak metin ve görüntüler içeren menüleri oluşturabilirsiniz.  
  
 Visual Studio sürükle ve bırak forms Tasarımcısı ile Windows Forms uygulamaları kolayca oluşturabilirsiniz: yalnızca imlecinizi denetimleriyle seçin ve form üzerinde istediğiniz yere yerleştirin. Kılavuz çizgileri ve "dayama çizgileri" gibi araçları tasarımcı sağlar denetimleri hizalama dışında mücadele gerçekleştirilecek. Visual Studio'yu kullanın ya da komut satırında derleme olup olmadığını kullanabileceğiniz <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.SplitContainer> denetimleri Gelişmiş oluşturmak için en az zaman ve çaba düzenleriyle form.  
  
### <a name="custom-ui-elements"></a>Özel kullanıcı Arabirimi öğeleri  
 Son olarak, kendi özel kullanıcı Arabirimi öğeleri oluşturmanız gerekiyorsa <xref:System.Drawing> ad alanı, tüm çizgiler, daireler ve diğer şekiller doğrudan bir form üzerinde işlemek için gereken sınıfları içerir.  
  
 Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Visual Studio ile yeni bir Windows Forms uygulaması oluşturma|[İzlenecek yol: basit bir Windows formu oluşturma](http://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Formlarında denetimleri kullanın|[Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Grafik oluşturma <xref:System.Drawing>|[Grafik Programlamaya Başlarken](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl Sınıfından Devralma](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Verileri görüntüleme ve düzenleme  
 Birçok uygulama, verileri bir veritabanı, XML dosyası, XML Web hizmeti veya başka bir veri kaynağını görüntülemeniz gerekir. Windows Forms adlı esnek bir denetim sağlar <xref:System.Windows.Forms.DataGridView> her veri parçası kendi hücrenin kapladığı bir geleneksel satır ve sütun biçiminde tablo bu tür veri işleme için denetim. Kullanarak <xref:System.Windows.Forms.DataGridView> tek tek hücrelerin görünüşünü özelleştirme, rasgele satırları ve sütunları yerinde kilitlemek ve karmaşık denetimler diğer özellikler arasında hücreleri içinde görüntüler.  
  
 Bir ağ üzerinden veri kaynaklarına bağlanma, Windows Forms akıllı istemcilerle basit bir görevdir. <xref:System.Windows.Forms.BindingSource> Bileşeni, yeni Windows Forms'ta ile [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] ve [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], bir veri kaynağına bağlantıyı temsil eder ve önceki ve sonraki kayıtlara gezinme, kayıtları düzenleme ve kaydetme denetimlere veri bağlama için yöntemleri gösterir özgün kaynağına değişiklikler. <xref:System.Windows.Forms.BindingNavigator> Denetim üzerinden basit bir arabirim sağlar <xref:System.Windows.Forms.BindingSource> kayıtlar arasında gezinmek kullanıcılar için bileşen.  
  
### <a name="data-bound-controls"></a>Veri bağlama denetimleri  
 Verilere bağlı denetimler kolayca veritabanları, Web Hizmetleri ve nesneleri gibi veri kaynakları projenize görüntüler veri kaynakları penceresini kullanarak oluşturabilirsiniz. Veri bağlama denetimleri projenizdeki forms üzerine bu pencereden öğeleri sürükleyerek oluşturabilirsiniz. Ayrıca veri mevcut denetimleri verileri için mevcut denetimleri üzerine veri kaynakları penceresinden nesneleri sürükleyerek bağlama.  
  
### <a name="settings"></a>Ayarlar  
 Windows Forms'ta yönetebilmeniz için veri bağlama başka bir tür ayarlarıdır. Çoğu akıllı istemci uygulamaları, forms, bilinen son boyutu gibi kendi çalışma zamanı durumu hakkındaki bazı bilgileri korumak ve kaydedilen dosyaları için varsayılan konumları gibi kullanıcı tercihi verileri tut. Uygulama ayarları özellik ayarları her iki tür istemci bilgisayarda depolamak için kolay bir yol sağlayarak bu gereksinimleri karşılar. Visual Studio ya da bir kod düzenleyicisini kullanarak tanımlanan sonra bu ayarları XML olarak kalıcı ve çalışma zamanında otomatik olarak geri belleğe okuyun.  
  
 Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Kullanım <xref:System.Windows.Forms.BindingSource> bileşeni|[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Çalışmak [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kaynakları|[Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Veri Kaynakları penceresini kullanma|[İzlenecek yol: Bir Windows formunda veri görüntüleme](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>İstemci bilgisayarlara uygulamaları dağıtma  
 Uygulamanızı yazıldıktan sonra yükleyebilir ve kendi istemci bilgisayarlarda çalıştırmak için bunu kullanıcılarınıza göndermelidir. Kullanarak [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] teknolojisi, yalnızca birkaç tıklama kullanarak Visual Studio'dan uygulamalarınızı dağıtma ve kullanıcılara Web uygulamanıza işaret eden bir URL sağlamak. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] tüm öğeleri ve bağımlılıklarını, uygulamanızda yönetir ve uygulama istemci bilgisayara düzgün yüklendiğini sağlar.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamaları yalnızca kullanıcı ağa bağlandığında çalıştırmak için veya her ikisi de çevrimiçi çalıştırmak için yapılandırılmış ve çevrimdışı olabilir. Bir uygulama çevrimdışı işlemi desteklemesi gereken belirttiğinizde [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] kullanıcının uygulamanızda bir bağlantı ekler **Başlat** menüsünde, böylece kullanıcı URL kullanmadan açabilir.  
  
 Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve yeni bir kopya uygulamanızın Web sunucunuza yayımlayın. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] olmadığını güncelleştirmesi mevcut olduğunu ve kullanıcının yükleme yükseltmeler algılar; özel programlama eski derlemeleri güncelleştirmek için gereklidir.  
  
 Bir tam giriş için [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment). Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Bir uygulama oluşturup dağıtın [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Güncelleştirme bir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] dağıtımı|[Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Güvenlik ile yönetme [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Diğer denetimleri ve özellikleri  
 Windows Forms'ta uygulama ortak görevleri hızlı ve kolay iletişim kutuları oluşturma, yazdırma, Yardım ve belgeler ekleme ve uygulamanız birden çok dilde yerelleştirme için destek gibi olun birçok özelliği vardır. Ayrıca, Windows Forms güçlü güvenlik sistemde dayanır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], müşterilerinize daha güvenli uygulamalar yayımlamayı etkinleştirme.  
  
 Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Bir form alanının içindekileri yazdırın|[Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'ta Güvenliğe Genel Bakış](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Windows Forms'a Genel Bakış](../../../framework/winforms/windows-forms-overview.md)  
 [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
