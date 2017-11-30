---
title: "Windows Forms Uygulaması Temelleri (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c5355f10fba2d1d18bc514c93f31051781bed14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Forms Uygulaması Temelleri (Visual Basic)
Önemli bir kısmını [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kullanıcıların bilgisayarlarına yerel olarak çalışan Windows Forms uygulamaları oluşturma yeteneği. Windows Forms kullanan uygulama ve kullanıcı arabirimini oluşturmak için Visual Studio'yu kullanabilirsiniz. Bir Windows Forms uygulaması sınıflardan üzerine inşa edilmiştir <xref:System.Windows.Forms> ad alanı.  
  
## <a name="designing-windows-forms-applications"></a>Forms uygulamaları Windows tasarlama  
 Windows Forms ve Windows hizmet uygulamaları ile oluşturabileceğiniz [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Windows Forms'a Başlarken](https://msdn.microsoft.com/library/ms229601.aspx). Oluşturma ve Windows Forms program bilgiler verilmektedir.  
   
-   [Windows Forms denetimleri](https://msdn.microsoft.com/library/ettb6e2a.aspx). Windows Forms denetimlerini ayrıntılı konulara koleksiyonu.  
  
-   [Windows hizmet uygulamaları](https://msdn.microsoft.com/library/y817hyb6.aspx). Windows Hizmetleri oluşturma açıklayan konulara listeler.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Yapı zengin ve etkileşimli kullanıcı arabirimleri  
 Windows Forms bileşenidir akıllı istemci [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], okuma ve dosya sistemine yazma gibi ortak uygulama görevlerini etkinleştirmek yönetilen kitaplıkları kümesi. Gibi bir geliştirme ortamı kullanarak [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], bir ağ üzerinden uzak bilgisayarlarla bilgilerini görüntülemek, kullanıcılardan giriş istemek ve iletişim kuran Windows Forms uygulamaları oluşturabilirsiniz.  
  
 Windows Forms'ta bir kullanıcıya bilgi görüntü üzerinde bir görsel yüzey biçimidir. Windows Forms uygulamaları formlarında denetimleri yerleştirme ve fare tıklamaları veya anahtar basarsa gibi kullanıcı eylemlerini yanıtlarını geliştirerek yaygın olarak oluşturun. A *denetim* veri girişi kabul eder ya da verileri görüntüleyen bir ayrık kullanıcı arabirimi (UI) öğesidir.  
  
### <a name="events"></a>Olaylar  
 Bir kullanıcı bir şey formunuz veya denetimlerinden birine yaptığında, bir olay oluşturur. Uygulamanız kod kullanarak bu olaylara yanıt verir ve bunlar ortaya çıktığında olayları işler. Daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](https://msdn.microsoft.com/library/dacysss4.aspx).  
  
### <a name="controls"></a>Denetimler  
 Windows Forms formlarında yerleştirebilirsiniz denetimleri çeşitli içerir: metin kutuları, düğmeler, aşağı açılan kutuları, radyo düğmeleri ve bile Web sayfalarını görüntüleyen denetimler. Bir form üzerinde kullanabileceğiniz tüm denetimler listesi için bkz: [Windows Forms'ta kullanılacak denetimler](https://msdn.microsoft.com/library/3xdhey7w.aspx). Varolan bir denetim ihtiyaçlarınızı karşılamıyorsa kullanarak kendi özel denetimler oluşturma Windows Forms de destekler <xref:System.Windows.Forms.UserControl> sınıfı.  
  
 Windows Forms özellikleri Microsoft Office gibi gelişmiş uygulamalarda öykünmek zengin UI denetimleri vardır. Kullanarak <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip> denetim, araç çubukları ve alt menüler görüntülemek ve metin kutuları ve birleşik giriş kutuları gibi diğer denetimleri konak metin ve görüntüler içeren menüleri oluşturabilirsiniz.  
  
 İle [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] sürükle ve bırak forms Tasarımcısı Windows Forms uygulamaları kolayca oluşturabilirsiniz: yalnızca imlecinizi denetimleriyle seçin ve form üzerinde istediğiniz yere yerleştirin. Kılavuz çizgileri ve "dayama çizgileri" gibi araçları tasarımcı sağlar denetimleri hizalama dışında mücadele gerçekleştirilecek. Ve kullansanız [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] veya derleme komut satırında, kullandığınız <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.SplitContainer> denetimleri Gelişmiş oluşturmak için en az zaman ve çaba düzenleriyle form.  
  
### <a name="custom-ui-elements"></a>Özel kullanıcı Arabirimi öğeleri  
 Son olarak, kendi özel kullanıcı Arabirimi öğeleri oluşturmanız gerekiyorsa <xref:System.Drawing> ad alanı, tüm çizgiler, daireler ve diğer şekiller doğrudan bir form üzerinde işlemek için gereken sınıfları içerir.  
  
 Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Yeni bir Windows Forms uygulaması oluşturma[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]|[İzlenecek yol: basit bir Windows formu oluşturma](http://msdn.microsoft.com/en-us/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Formlarında denetimleri kullanın|[Nasıl yapılır: Windows formlarına denetimler ekleme](https://msdn.microsoft.com/library/0h5y8567.aspx)|   
|Grafik oluşturma<xref:System.Drawing>|[Grafik programlamaya Başlarken](https://msdn.microsoft.com/library/da0f23z7.aspx)|  
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl sınıfından devralma](https://msdn.microsoft.com/library/00ctb4z0.aspx)|  
  
## <a name="displaying-and-manipulating-data"></a>Verileri görüntüleme ve düzenleme  
 Birçok uygulama, verileri bir veritabanı, XML dosyası, XML Web hizmeti veya başka bir veri kaynağını görüntülemeniz gerekir. Windows Forms adlı esnek bir denetim sağlar <xref:System.Windows.Forms.DataGridView> her veri parçası kendi hücrenin kapladığı bir geleneksel satır ve sütun biçiminde tablo bu tür veri işleme için denetim. Kullanarak <xref:System.Windows.Forms.DataGridView> tek tek hücrelerin görünüşünü özelleştirme, rasgele satırları ve sütunları yerinde kilitlemek ve karmaşık denetimler diğer özellikler arasında hücreleri içinde görüntüler.  
  
 Bir ağ üzerinden veri kaynaklarına bağlanma, Windows Forms akıllı istemcilerle basit bir görevdir. <xref:System.Windows.Forms.BindingSource> Bileşeni, yeni Windows Forms'ta ile [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] ve [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], bir veri kaynağına bağlantıyı temsil eder ve önceki ve sonraki kayıtlara gezinme, kayıtları düzenleme ve kaydetme denetimlere veri bağlama için yöntemleri gösterir özgün kaynağına değişiklikler. <xref:System.Windows.Forms.BindingNavigator> Denetim üzerinden basit bir arabirim sağlar <xref:System.Windows.Forms.BindingSource> kayıtlar arasında gezinmek kullanıcılar için bileşen.  
  
### <a name="data-bound-controls"></a>Veri bağlama denetimleri  
 Verilere bağlı denetimler kolayca veritabanları, Web Hizmetleri ve nesneleri gibi veri kaynakları projenize görüntüler veri kaynakları penceresini kullanarak oluşturabilirsiniz. Veri bağlama denetimleri projenizdeki forms üzerine bu pencereden öğeleri sürükleyerek oluşturabilirsiniz. Ayrıca veri mevcut denetimleri verileri için mevcut denetimleri üzerine veri kaynakları penceresinden nesneleri sürükleyerek bağlama.  
  
### <a name="settings"></a>Ayarlar  
 Windows Forms'ta yönetebilmeniz için veri bağlama başka bir tür ayarlarıdır. Çoğu akıllı istemci uygulamaları, forms, bilinen son boyutu gibi kendi çalışma zamanı durumu hakkındaki bazı bilgileri korumak ve kaydedilen dosyaları için varsayılan konumları gibi kullanıcı tercihi verileri tut. Uygulama ayarları özellik ayarları her iki tür istemci bilgisayarda depolamak için kolay bir yol sağlayarak bu gereksinimleri karşılar. Kullanarak kez tanımlanmış [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ya da bir kod düzenleyicisinde, bu ayarlar XML olarak kalıcı ve çalışma zamanında otomatik olarak geri belleğe okuyun.  
  
 Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Kullanım <xref:System.Windows.Forms.BindingSource> bileşeni|[Nasıl yapılır: Windows Forms denetimlerini Tasarımcısı'nı kullanarak BindingSource bileşeni ile bağlama](https://msdn.microsoft.com/library/801dxw2t.aspx)|  
|Çalışmak [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kaynakları|[Nasıl yapılır: Windows Forms BindingSource bileşeni ile ADO.NET verilerini sıralama ve filtreleme](https://msdn.microsoft.com/library/ya3sah92.aspx)|  
|Veri Kaynakları penceresini kullanma|[İzlenecek yol: Bir Windows formunda veri görüntüleme](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>İstemci bilgisayarlara uygulamaları dağıtma  
 Uygulamanızı yazıldıktan sonra yükleyebilir ve kendi istemci bilgisayarlarda çalıştırmak için bunu kullanıcılarınıza göndermelidir. Kullanarak [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] teknolojisi, dağıtabileceğiniz uygulamalarınızdan içinde [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] göre yalnızca birkaç tıklama kullanılması ve Web uygulamanıza işaret eden bir URL ile kullanıcılar sağlar. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]tüm öğeleri ve bağımlılıklarını, uygulamanızda yönetir ve uygulama istemci bilgisayara düzgün yüklendiğini sağlar.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]uygulamaları yalnızca kullanıcı ağa bağlandığında çalıştırmak için veya her ikisi de çevrimiçi çalıştırmak için yapılandırılmış ve çevrimdışı olabilir. Bir uygulama çevrimdışı işlemi desteklemesi gereken belirttiğinizde [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] kullanıcının uygulamanızda bir bağlantı ekler **Başlat** menüsünde, böylece kullanıcı URL kullanmadan açabilir.  
  
 Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve yeni bir kopya uygulamanızın Web sunucunuza yayımlayın. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]olmadığını güncelleştirmesi mevcut olduğunu ve kullanıcının yükleme yükseltmeler algılar; özel programlama eski derlemeleri güncelleştirmek için gereklidir.  
  
 Bir tam giriş için [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment). Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Bir uygulama oluşturup dağıtın[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: Bir ClickOnce uygulamasını el ile dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Güncelleştirme bir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] dağıtımı|[Nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|Güvenlik ile yönetme[!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Nasıl yapılır: ClickOnce güvenlik ayarlarını etkinleştir](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Diğer denetimleri ve özellikleri  
 Windows Forms'ta uygulama ortak görevleri hızlı ve kolay iletişim kutuları oluşturma, yazdırma, Yardım ve belgeler ekleme ve uygulamanız birden çok dilde yerelleştirme için destek gibi olun birçok özelliği vardır. Ayrıca, Windows Forms güçlü güvenlik sistemde dayanır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], müşterilerinize daha güvenli uygulamalar yayımlamayı etkinleştirme.  
  
 Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Bir form alanının içindekileri yazdırın|[Nasıl yapılır: Windows Forms'ta grafik yazdırma](https://msdn.microsoft.com/library/741a0ktc.aspx)<br /><br /> [Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](https://msdn.microsoft.com/library/cwbe712d.aspx)|   
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'a genel bakış güvenliği](https://msdn.microsoft.com/library/90k49ccb.aspx)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 [Windows Forms'a genel bakış](https://msdn.microsoft.com/library/8bxxy49h.aspx)  
 [My.Forms nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
