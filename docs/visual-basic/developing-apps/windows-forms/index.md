---
title: Windows Forms Uygulaması Temelleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: b900b85b4e3e56dbc587a15edea40f6e3032cbd1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521671"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Forms Uygulaması Temelleri (Visual Basic)
Visual Basic önemli bir parçası, kullanıcıların bilgisayarlarında yerel olarak çalışan Windows Forms uygulamaları oluşturmak için olanağıdır. Visual Studio, Windows formları kullanarak uygulama ve kullanıcı arabirimi oluşturmak için kullanabilirsiniz. Bir Windows Forms uygulaması sınıflardan geliştirilmiştir <xref:System.Windows.Forms> ad alanı.  
  
## <a name="designing-windows-forms-applications"></a>Tasarlama Windows Forms uygulamaları  
 Visual Studio ile Windows Forms ve Windows hizmet uygulamaları oluşturabilirsiniz. Daha fazla bilgi için aşağıdaki konulara bakın:  
  
-   [Windows Forms'a Başlarken](../../../framework/winforms/getting-started-with-windows-forms.md). Oluşturma ve Windows Forms programı hakkında bilgi sağlar.  
   
-   [Windows Forms denetimlerine](../../../framework/winforms/controls/index.md). Windows Forms denetimlerini gerçekleşen konuları koleksiyonu.  
  
-   [Windows hizmet uygulamaları](../../../framework/windows-services/index.md). Windows Hizmetleri oluşturma işlemleri açıklanmaktadır konuları listeler.  
  
## <a name="building-rich-interactive-user-interfaces"></a>Yapı zengin, etkileşimli kullanıcı arabirimleri  
 Windows Forms akıllı istemci bileşeni olan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], dosya sistemine yazma ve okuma gibi ortak uygulama görevleri sağlayan yönetilen kitaplığı kümesi. Visual Studio gibi bir geliştirme ortamı kullanarak, bir ağ üzerinden uzak bilgisayarlarla iletişim bilgilerini görüntülemek ve kullanıcıların giriş istek Windows Forms uygulamaları oluşturabilirsiniz.  
  
 Windows Forms'ta bir form üzerinde kullanıcıya bilgi göstermek bir görsel bir yüzeydir. Yaygın olarak formlarında denetimleri yerleştirme ve fare tıklamasına veya tuş basışlarını gibi kullanıcı eylemlerini yanıtlarını geliştirmeye göre Windows Forms uygulamaları oluşturun. A *denetimi* veri girişi kabul eder ya da veri görüntüleyen bir ayrık bir kullanıcı arabirimi (UI) öğesidir.  
  
### <a name="events"></a>Olaylar  
 Bir kullanıcı bir şey formunuza veya denetimlerinden birini yaptığında, bir olay oluşturur. Uygulamanız kod kullanarak bu olaylara yanıt verir ve bunlar ortaya çıktığında olayları işler. Daha fazla bilgi için [Windows Forms'ta olay işleyicileri oluşturma](../../../framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
### <a name="controls"></a>Denetimler  
 Windows Forms formlarını yerleştirebilirsiniz denetimleri çeşitli içerir: metin kutuları, düğmeler, aşağı açılan kutusu, radyo düğmeleri ve bile Web sayfalarını görüntüleyen denetimler. Bir form üzerinde kullanabileceğiniz tüm denetimleri listesi için bkz. [Windows Forms'da kullanılacak denetimler](../../../framework/winforms/controls/controls-to-use-on-windows-forms.md). Varolan bir denetimi gereksinimlerinizi karşılamıyorsa, Windows Forms Ayrıca kendi özel denetimler kullanarak oluşturulmasını destekler <xref:System.Windows.Forms.UserControl> sınıfı.  
  
 Windows Forms, yüksek kaliteli uygulamalar Microsoft Office gibi özellikleri öykünmek zengin kullanıcı Arabirimi denetimlerine sahiptir. Kullanarak <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip> denetimi araç çubuklarında ve menülerde menülerinde görüntülemek ve metin kutuları ve birleşik giriş kutuları gibi diğer denetimleri barındıran metin ve görüntüleri içeren oluşturabilirsiniz.  
  
 Visual Studio sürükle ve bırak Form Tasarımcısı ile Windows Forms uygulamaları kolayca oluşturabilirsiniz: yalnızca imlecinizi denetimleriyle seçin ve form üzerinde istediğiniz yere yerleştirin. Tasarımcı kılavuz çizgileri ve "ek satırlar" gibi araçlar sağlayan denetimleri hizalama dışında zahmetini için. Visual Studio kullanıyorsanız veya komut satırında derleme olup olmadığını kullanabileceğiniz <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.SplitContainer> form düzeni en az zaman ve çaba ile Gelişmiş oluşturmak için denetimi.  
  
### <a name="custom-ui-elements"></a>Özel kullanıcı Arabirimi öğeleri  
 Son olarak, kendi özel kullanıcı Arabirimi öğeleri oluşturmanız gerekirse <xref:System.Drawing> ad alanı tüm satırları, daire ve diğer şekiller bir form üzerinde doğrudan işlemek için sınıflar içerir.  
  
 Bu özellikleri kullanmaya hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Visual Studio ile yeni bir Windows Forms uygulaması oluşturma|[İzlenecek yol: basit bir Windows formu oluşturma](https://msdn.microsoft.com/library/2d9daec0-0543-41d0-acb1-964f685bddbb)|  
|Form üzerinde denetimleri kullanın|[Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|   
|Grafik oluşturma <xref:System.Drawing>|[Grafik Programlamaya Başlarken](../../../framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl Sınıfından Devralma](../../../framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
## <a name="displaying-and-manipulating-data"></a>Verileri görüntüleme ve düzenleme  
 Birçok uygulama, verileri bir veritabanından, XML dosyası, XML Web hizmeti veya başka bir veri kaynağı görüntülemeniz gerekir. Windows Forms adlı esnek bir denetim sağlar <xref:System.Windows.Forms.DataGridView> kendi hücrenin her veri parçası kapladığı bir geleneksel satır ve sütun biçiminde tablo gibi veri işleme için denetimi. Kullanarak <xref:System.Windows.Forms.DataGridView> bireysel hücrelerin görünüşünü özelleştirme, rastgele satırları ve sütunları yerinde kilitleyebilir ve karmaşık denetimlerin yanı sıra başka özellikler hücreleri içine görüntüleme.  
  
 Bir ağ üzerinden veri kaynaklarına bağlanma, Windows Forms akıllı istemciler ile basit bir görevdir. <xref:System.Windows.Forms.BindingSource> Bileşeni, Windows Forms ile yeni [!INCLUDE[vsprvslong](~/includes/vsprvslong-md.md)] ve [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)], bir veri kaynağı bağlantısını temsil eder ve önceki ve sonraki kayıtlara gezinme, kayıtları düzenleme ve kaydetme denetimlere veri bağlama için yöntemleri sunar. özgün kaynağına değişiklikler. <xref:System.Windows.Forms.BindingNavigator> Denetim sağlayan basit bir arabirim üzerinden <xref:System.Windows.Forms.BindingSource> kayıtlar arasında gezinmek kullanıcılar için bileşen.  
  
### <a name="data-bound-controls"></a>Verilere bağlı denetimler  
 Veritabanları, Web servisleri ve nesneler gibi veri kaynakları projenizde görüntüler veri kaynakları penceresini kullanarak kolayca verilere bağlı denetimler oluşturabilirsiniz. Öğeleri bu pencereden projenizdeki formlara sürükleyerek veriye bağlı denetimler oluşturabilirsiniz. Ayrıca veri mevcut denetimleri için veri nesnelerini veri kaynakları penceresinden mevcut denetimlerin üzerine sürükleyerek bağlama.  
  
### <a name="settings"></a>Ayarlar  
 Windows Forms'ta yönetebileceğiniz veri bağlama başka bir tür ayarlarıdır. Çoğu akıllı istemci uygulamaları, forms, bilinen son boyutu gibi çalışma zamanı durumlarını hakkında bazı bilgiler korumak ve kaydedilen dosyalar için varsayılan konumları gibi kullanıcı tercihi verileri korur. Uygulama ayarları özellik ayarları her iki türde istemci bilgisayarda depolamak için kolay bir yol sağlayarak bu gereksinimleri ele alır. Visual Studio veya bir kod Düzenleyicisi'ni kullanarak tanımlandıktan sonra bu ayarlar kalıcı XML ve otomatik olarak çalışma zamanında belleğe geri okuyun.  
  
 Bu özellikleri kullanmaya hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Kullanım <xref:System.Windows.Forms.BindingSource> bileşeni|[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama](../../../framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Çalışmak [!INCLUDE[vstecado](~/includes/vstecado-md.md)] veri kaynakları|[Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme](../../../framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|
|Veri Kaynakları penceresini kullanma|[İzlenecek yol: Bir Windows formunda veri görüntüleme](/visualstudio/data-tools/accessing-data-in-visual-studio)|  
  
## <a name="deploying-applications-to-client-computers"></a>İstemci bilgisayarlara uygulamaları dağıtma  
 Uygulamanızı yazmış sonra yükleyebilir ve kendi istemci bilgisayarlarda çalıştırmak, kullanıcılarınıza göndermelisiniz. Kullanarak [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] teknolojisi, uygulamalarınızı Visual Studio'dan yalnızca birkaç tıklamayla kullanarak dağıtma ve kullanıcılara Web uygulamanıza işaret eden bir URL sağlar. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] tüm öğeleri ve bağımlılıkları uygulamanızdaki yönetir ve uygulama istemci bilgisayara düzgün yüklendiğini sağlar.  
  
 [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] uygulamalar, yalnızca kullanıcı ağa bağlandığında çalıştırmak için veya her ikisi de çevrimiçi çalıştırmak için yapılandırılmış ve çevrimdışı olabilir. Uygulama çevrimdışı işlemi desteklemelidir belirttiğinizde [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] kullanıcının uygulamanızda bir bağlantı ekler **Başlat** menüsünde, böylece kullanıcı, URL kullanmadan açabilirsiniz.  
  
 Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve yeni bir kopya, uygulamanızın Web sunucunuza yayımlayın. [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] bir güncelleştirme kullanılabilir olmadığını ve kullanıcının yükleme yükseltir algılar. özel programlama eski derlemeleri güncelleştirmek için gereklidir.  
  
 Tam bir giriş için [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment). Bu özellikleri kullanmaya hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|İle uygulama dağıtma [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Güncelleştirme bir [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] dağıtım|[Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|İle güvenliği yönetme [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)]|[Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
## <a name="other-controls-and-features"></a>Diğer denetimler ve özellikleri  
 Windows Forms'ta olun uygulayan ortak görevleri hızlı ve kolay, iletişim kutuları oluşturma, yazdırma, Yardım ve belgeler ekleme ve uygulamanızı birden çok dilde yerelleştirme desteği gibi diğer birçok özellik vardır. Ayrıca, Windows Forms sağlam güvenlik sistemine bağlıdır [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], böylece müşterilerinize daha güvenli uygulamaları yayınlayın.  
  
 Bu özellikleri kullanmaya hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:  
  
|Bitiş|Bkz. |  
|--------|---------|  
|Form içeriklerini yazdırma|[Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](../../../framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](../../../framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|   
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'ta Güvenliğe Genel Bakış](../../../framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
- [Windows Forms'a Genel Bakış](../../../framework/winforms/windows-forms-overview.md)  
- [My.Forms Nesnesi](../../../visual-basic/language-reference/objects/my-forms-object.md)
