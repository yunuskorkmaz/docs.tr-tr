---
title: Windows Forms'a Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- smart clients
- Windows Forms, about Windows Forms
ms.assetid: 3a2b6284-c8d6-4e1c-8c69-0bed38f38cd4
ms.openlocfilehash: 897d6fb8e0a150cc7fa498bb904b10d89ece9943
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486241"
---
# <a name="windows-forms-overview"></a>Windows Forms'a Genel Bakış
Aşağıdaki genel akıllı istemci uygulamaları, Windows Forms programlama ve günümüzde kuruluşların ve son kullanıcıların ihtiyaçlarını akıllı istemciler oluşturmak için Windows Forms nasıl kullanabileceğinizi ana özelliklerini avantajları anlatılmaktadır.  
  
## <a name="windows-forms-and-smart-client-applications"></a>Windows Forms ve akıllı istemci uygulamaları  
 Windows Forms ile akıllı istemciler geliştirin. *Akıllı istemciler* dağıtmak ve güncelleştirmek kolay bir görsel açıdan zengin uygulamalar bağlı veya bağlantısı kesilmiş Internet'ten çalışabilir ve yerel bilgisayardaki kaynaklara daha güvenli bir şekilde daha geleneksel erişebilirsiniz Windows tabanlı uygulamalar.  
  
### <a name="building-rich-interactive-user-interfaces"></a>Yapı zengin, etkileşimli kullanıcı arabirimleri  
 Windows Forms için bir akıllı istemci teknolojisidir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], dosya sistemine yazma ve okuma gibi ortak uygulama görevleri basitleştirmek yönetilen kitaplığı kümesi. Visual Studio gibi bir geliştirme ortamı kullandığınızda, bir ağ üzerinden uzak bilgisayarlarla iletişim bilgilerini görüntülemek ve kullanıcıların giriş istek Windows Forms akıllı istemci uygulamaları oluşturabilirsiniz.  
  
 Windows Forms'ta bir *form* üzerinde görüntü bilgileri kullanıcıya görsel bir yüzeydir. Normalde formlarına denetimler ekleme ve fare tıklamasına veya tuş basışlarını gibi kullanıcı eylemlerini yanıtlarını geliştirmeye göre Windows Forms uygulamaları oluşturun. A *denetimi* veri girişi kabul eder ya da veri görüntüleyen bir ayrık bir kullanıcı arabirimi (UI) öğesidir.  
  
 Bir kullanıcı bir şey formunuza veya denetimlerinden birini yaptığında, eylem, bir olay oluşturur. Uygulamanız kod kullanarak bu olaylara yanıt verir ve bunlar ortaya çıktığında olayları işler. Daha fazla bilgi için [Windows Forms'ta olay işleyicileri oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).  
  
 Windows Forms formlara ekleyebilirsiniz denetimleri çeşitli içerir: metin kutuları, düğmeler, aşağı açılan kutusu, radyo düğmeleri ve bile Web sayfalarını görüntüleyen denetimler. Bir form üzerinde kullanabileceğiniz tüm denetimleri listesi için bkz. [Windows Forms'da kullanılacak denetimler](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md). Varolan bir denetimi gereksinimlerinizi karşılamıyorsa, Windows Forms Ayrıca kendi özel denetimler kullanarak oluşturulmasını destekler <xref:System.Windows.Forms.UserControl> sınıfı.  
  
 Windows Forms, yüksek kaliteli uygulamalar Microsoft Office gibi özellikleri öykünmek zengin kullanıcı Arabirimi denetimlerine sahiptir. Kullanırken <xref:System.Windows.Forms.ToolStrip> ve <xref:System.Windows.Forms.MenuStrip> denetimi araç çubuklarında ve menülerde menülerinde görüntülemek ve metin kutuları ve birleşik giriş kutuları gibi diğer denetimleri barındıran metin ve görüntüleri içeren oluşturabilirsiniz.  
  
 Visual Studio sürükle ve bırak Windows Form Tasarımcısı ile Windows Forms uygulamaları kolayca oluşturabilirsiniz. Yalnızca imlecinizi denetimleriyle seçin ve form üzerinde istediğiniz yere ekleyin. Tasarımcı denetimleri hizalama dışında zahmetini için kılavuz çizgilerini ve ek satırlar gibi araçları sağlar. Visual Studio kullanıyorsanız veya komut satırında derleme olup olmadığını kullanabileceğiniz <xref:System.Windows.Forms.FlowLayoutPanel>, <xref:System.Windows.Forms.TableLayoutPanel> ve <xref:System.Windows.Forms.SplitContainer> Gelişmiş oluşturmak için denetimleri form düzenlerini daha kısa sürede.  
  
 Son olarak, kendi özel kullanıcı Arabirimi öğeleri oluşturmanız gerekirse <xref:System.Drawing> ad alanı yelpazesinden seçim satırları, daire ve diğer şekiller bir form üzerinde doğrudan işlemek için sınıflar içerir.  
  
> [!NOTE]
>  Windows Forms denetimleri, uygulama etki alanları arasında sıralanması için tasarlanmamıştır. Bu nedenle, Microsoft genelinde bir Windows Forms denetimi geçirme desteklemiyor bir <xref:System.AppDomain> sınır, olsa bile <xref:System.Windows.Controls.Control> temel türü <xref:System.MarshalByRefObject> mümkün olduğunu belirtmek için görünen. Hiçbir Windows Forms denetimleri uygulama etki alanı sınırları arasında geçirilen sürece birden çok uygulama etki alanları Windows Forms uygulamaları desteklenir.  
  
#### <a name="help-creating-forms-and-controls"></a>Formlar ve denetimler oluşturma konusunda Yardım  
 Bu özelliklerin nasıl kullanılacağını hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Form üzerinde denetimleri kullanma|[Nasıl yapılır: Windows Forms’a Denetimler Ekleme](../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)|  
|Kullanarak <xref:System.Windows.Forms.ToolStrip> denetimi|[Nasıl yapılır: Tasarımcı Kullanarak Standart Öğelerle Temel bir ToolStrip Oluşturma](../../../docs/framework/winforms/controls/create-a-basic-wf-toolstrip-with-standard-items-using-the-designer.md)|  
|Grafik oluşturma <xref:System.Drawing>|[Grafik Programlamaya Başlarken](../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)|  
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl Sınıfından Devralma](../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)|  
  
### <a name="displaying-and-manipulating-data"></a>Verileri görüntüleme ve düzenleme  
 Birçok uygulama, verileri bir veritabanından, XML dosyası, XML Web hizmeti veya başka bir veri kaynağı görüntülemeniz gerekir. Windows Forms adlı esnek bir denetim sağlar <xref:System.Windows.Forms.DataGridView> kendi hücrenin her veri parçası kapladığı bir tablo gibi veri geleneksel bir satır ve sütun biçiminde, görüntüleme için denetimi. Kullanırken <xref:System.Windows.Forms.DataGridView>, tek tek hücrelerin görünüşünü özelleştirme, rastgele satırları kilitlemek ve sütunlardaki yerleştirin ve karmaşık denetimlerin yanı sıra başka özellikler hücreleri içine görüntülemek.  
  
 Bir ağ üzerinden veri kaynaklarına bağlanma, Windows Forms akıllı istemciler ile basit bir görevdir. <xref:System.Windows.Forms.BindingSource> Bileşeni, Windows Forms ile yeni [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] ve [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], bir veri kaynağı bağlantısını temsil eder ve önceki ve sonraki kayıtlara gezinme, kayıtları düzenleme ve kaydetme denetimlere veri bağlama için yöntemleri sunar. özgün kaynağına değişiklikler. <xref:System.Windows.Forms.BindingNavigator> Denetim sağlayan basit bir arabirim üzerinden <xref:System.Windows.Forms.BindingSource> kayıtlar arasında gezinmek kullanıcılar için bileşen.  
  
 Veri Kaynakları penceresini kullanarak kolayca verilere bağlı denetimler oluşturabilirsiniz. Pencere nesneleri veritabanları ve Web Hizmetleri gibi veri kaynakları projenizde görüntüler. Öğeleri bu pencereden projenizdeki formlara sürükleyerek veriye bağlı denetimler oluşturabilirsiniz. Ayrıca veri mevcut denetimleri için veri nesnelerini veri kaynakları penceresinden mevcut denetimlerin üzerine sürükleyerek bağlama.  
  
 Windows Forms'ta yönetebileceğiniz veri bağlama başka bir tür *ayarları*. Çoğu akıllı istemci uygulamaları, forms, bilinen son boyutu gibi çalışma zamanı durumlarını hakkında bazı bilgiler korumak ve kaydedilen dosyalar için varsayılan konumları gibi kullanıcı tercihi verileri korur. Uygulama ayarları özellik ayarları her iki türde istemci bilgisayarda depolamak için kolay bir yol sağlayarak bu gereksinimleri ele alır. Visual Studio veya bir kod Düzenleyicisi'ni kullanarak bu ayarları tanımladıktan sonra ayarları XML olarak kalıcı ve otomatik olarak çalışma zamanında belleğe geri okuyun.  
  
#### <a name="help-displaying-and-manipulating-data"></a>Verileri Yardım görüntüleme ve düzenleme  
 Bu özelliklerin nasıl kullanılacağını hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Kullanarak <xref:System.Windows.Forms.BindingSource> bileşeni|[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama](../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md)|  
|Çalışma [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] veri kaynakları|[Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme](../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)|  
|Veri Kaynakları penceresini kullanma|[İzlenecek yol: Bir Windows formunda veri görüntüleme](https://msdn.microsoft.com/library/f6e08c2c-c792-43de-adf3-3e52c0100225)|  
|Uygulama ayarlarını kullanma|[Nasıl yapılır: Uygulama Ayarları Oluşturma](../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)|  
  
### <a name="deploying-applications-to-client-computers"></a>İstemci bilgisayarlara uygulamaları dağıtma  
 Uygulamanızı yazdıktan sonra kullanıcılarınıza uygulama yükleyebilir ve kendi istemci bilgisayarlarda çalıştırmak göndermeniz gerekir. Kullanırken [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] teknolojisi, uygulamalarınızı Visual Studio'dan yalnızca birkaç tıklamayla kullanarak dağıtabilir ve kullanıcılarınızın Web uygulamanıza işaret eden bir URL sağlar. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] tüm öğeleri ve bağımlılıkları uygulamanızdaki yönetir ve uygulama istemci bilgisayarda doğru şekilde yüklendiğini sağlar.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] uygulamalar, yalnızca kullanıcı ağa bağlandığında çalıştırmak için veya her ikisi de çevrimiçi çalıştırmak için yapılandırılmış ve çevrimdışı olabilir. Uygulama çevrimdışı işlemi desteklemelidir belirttiğinizde [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] kullanıcının uygulamanızda bir bağlantı ekler **Başlat** menüsü. Kullanıcı daha sonra uygulama URL'sini kullanmadan açabilirsiniz.  
  
 Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve yeni bir kopya, uygulamanızın Web sunucunuza yayımlayın. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] bir güncelleştirme kullanılabilir olduğunu algılar ve kullanıcının yüklemeyi yükseltme; özel programlama eski derlemeleri güncelleştirmek için gereklidir.  
  
#### <a name="help-deploying-clickonce-applications"></a>ClickOnce uygulamaları dağıtma Yardımı  
 Tam bir giriş için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment). Bu özelliklerin nasıl kullanılacağını hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın,  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Kullanarak bir uygulama dağıtma [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|  
|Güncelleştirme bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtım|[Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|  
|İle güvenliği yönetme [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]|[Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|  
  
### <a name="other-controls-and-features"></a>Diğer denetimler ve özellikleri  
 Windows Forms'ta olun uygulayan ortak görevleri hızlı ve kolay, iletişim kutuları oluşturma, yazdırma, Yardım ve belgeler ekleme ve uygulamanızı birden çok dilde yerelleştirme desteği gibi diğer birçok özellik vardır. Ayrıca, Windows Forms sağlam güvenlik sistemine bağlıdır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Bu sistem ile müşterilerinize daha güvenli uygulamalar serbest bırakabilirsiniz.  
  
#### <a name="help-implementing-other-controls-and-features"></a>Yardım diğer denetimler ve özellikleri uygulama  
 Bu özelliklerin nasıl kullanılacağını hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.  
  
|Açıklama|Yardım konusu|  
|-----------------|----------------|  
|Form içeriklerini yazdırma|[Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)<br /><br /> [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)|  
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'ta Güvenliğe Genel Bakış](../../../docs/framework/winforms/security-in-windows-forms-overview.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'a Başlarken](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [Yeni bir Windows Formu Oluşturma](../../../docs/framework/winforms/creating-a-new-windows-form.md)  
 [ToolStrip Denetimine Genel Bakış](../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [DataGridView Denetimine Genel Bakış](../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [BindingSource Bileşenine Genel Bakış](../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Uygulama Ayarlarına Genel Bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)
