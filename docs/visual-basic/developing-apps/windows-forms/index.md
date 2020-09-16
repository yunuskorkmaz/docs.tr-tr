---
title: Windows Forms Uygulaması Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- Windows applications
- Windows Forms, Visual Basic
ms.assetid: 0b919d30-7fd6-42db-85c8-543d15312441
ms.openlocfilehash: 9d061aeccb914cce80e02bb7df44dae2edf25412
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557025"
---
# <a name="windows-forms-application-basics-visual-basic"></a>Windows Forms Uygulaması Temelleri (Visual Basic)

Visual Basic önemli bir kısmı, kullanıcıların bilgisayarlarında yerel olarak çalışan Windows Forms uygulamalar oluşturma olanağıdır. Windows Forms kullanarak uygulamayı ve Kullanıcı arabirimini oluşturmak için Visual Studio 'Yu kullanabilirsiniz. Windows Forms bir uygulama, ad alanından sınıflar üzerine kurulmuştur <xref:System.Windows.Forms> .

## <a name="designing-windows-forms-applications"></a>Windows Forms uygulamaları tasarlama

Visual Studio ile Windows Forms ve Windows hizmet uygulamaları oluşturabilirsiniz. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Windows Forms](/dotnet/desktop/winforms/getting-started-with-windows-forms)kullanmaya başlama. Windows Forms ve program oluşturma hakkında bilgi sağlar.

- [Windows Forms denetimleri](/dotnet/desktop/winforms/controls/). Windows Forms denetimlerinin kullanımını ayrıntılandıran konuların toplanması.

- [Windows hizmeti uygulamaları](../../../framework/windows-services/index.md). Windows Hizmetleri oluşturmayı açıklayan konuları listeler.

## <a name="building-rich-interactive-user-interfaces"></a>Zengin, etkileşimli kullanıcı arabirimleri oluşturma

Windows Forms, dosya sistemine okuma ve yazma gibi yaygın uygulama görevlerini etkinleştiren bir dizi yönetilen kitaplık olan .NET Framework akıllı istemci bileşenidir. Visual Studio gibi bir geliştirme ortamı kullanarak, bilgi görüntüleyen, kullanıcılardan giriş isteyen ve uzak bilgisayarlarla ağ üzerinden iletişim kuran Windows Forms uygulamalar oluşturabilirsiniz.

Windows Forms, form, kullanıcıya bilgi görüntüleyen görsel bir yüzeydir. Genellikle form üzerinde denetimler yerleştirerek ve fare tıklamaları veya tuşa basma gibi kullanıcı eylemlerine yanıtlar geliştirirken Windows Forms uygulamalar oluşturabilirsiniz. *Denetim* , verileri görüntüleyen veya veri girişini kabul eden ayrı bir kullanıcı ARABIRIMI (UI) öğesidir.

### <a name="events"></a>Ekinlikler

Bir Kullanıcı formunuza veya denetimlerinden birine bir şey yaparken bir olay oluşturur. Uygulamanız kodu kullanarak bu olaylara tepki verir ve olayları gerçekleştiğinde işler. Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms).

### <a name="controls"></a>Denetimler

Windows Forms, formlara yerleştirebileceğiniz çeşitli denetimler içerir: metin kutularını, düğmeleri, açılan kutuları, radyo düğmelerini ve hatta Web sayfalarını görüntüleyen denetimler. Bir formda kullanabileceğiniz tüm denetimlerin listesi için, bkz. [Windows Forms kullanılacak denetimler](/dotnet/desktop/winforms/controls/controls-to-use-on-windows-forms). Mevcut bir denetim gereksinimlerinizi karşılamıyorsa, Windows Forms sınıfı kullanarak kendi özel denetimlerinizi oluşturmayı da destekler <xref:System.Windows.Forms.UserControl> .

Windows Forms, Microsoft Office gibi yüksek kaliteli uygulamalardaki özellikleri taklit eden zengin Kullanıcı arabirimi denetimlerine sahiptir. <xref:System.Windows.Forms.ToolStrip>Ve denetimini kullanarak <xref:System.Windows.Forms.MenuStrip> metin ve görüntü içeren araç çubukları ve menüler oluşturabilir, alt menüler görüntüleyebilir ve metin kutuları ve Birleşik giriş kutuları gibi diğer denetimleri barındırabilirsiniz.

Visual Studio sürükle ve bırak formları Tasarımcısı ile kolayca Windows Forms uygulamalar oluşturabilirsiniz: imlecinizin bulunduğu denetimleri seçmeniz ve bunları form üzerinde istediğiniz yere yerleştirmeniz yeterlidir. Tasarımcı, denetimleri hizalamayı ortadan kaldırmaya yönelik kılavuz çizgileri ve "satırları Yasla" gibi araçlar sağlar. Visual Studio 'Yu veya komut satırında derlemeyi kullanıp kullanmayacağınızı, <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.SplitContainer> en az zaman ve çaba ile gelişmiş form düzenleri oluşturmak için ve denetimlerini kullanabilirsiniz.

### <a name="custom-ui-elements"></a>Özel Kullanıcı arabirimi öğeleri

Son olarak, kendi özel kullanıcı arabirimi öğelerinizi oluşturmanız gerekiyorsa, <xref:System.Drawing> ad alanı, satırları, daireleri ve diğer şekilleri doğrudan form üzerinde işlemek için ihtiyacınız olan tüm sınıfları içerir.

Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.

|Amaç|Bkz.|
|--------|---------|
|Visual Studio ile yeni bir Windows Forms uygulaması oluşturma|[Öğretici 1: resim görüntüleyici oluşturma](/visualstudio/ide/tutorial-1-create-a-picture-viewer)|
|Formlarda denetimleri kullanma|[Nasıl yapılır: Windows Forms’a Denetimler Ekleme](/dotnet/desktop/winforms/controls/how-to-add-controls-to-windows-forms)|
|İle grafik oluşturma <xref:System.Drawing>|[Grafik Programlamaya Başlarken](/dotnet/desktop/winforms/advanced/getting-started-with-graphics-programming)|
|Özel denetimler oluşturma|[Nasıl yapılır: UserControl Sınıfından Devralma](/dotnet/desktop/winforms/controls/how-to-inherit-from-the-usercontrol-class)|

## <a name="displaying-and-manipulating-data"></a>Verileri görüntüleme ve düzenleme

Birçok uygulamanın, verileri bir veritabanından, XML dosyasından, XML Web hizmetinden veya başka bir veri kaynağından görüntülemesi gerekir. Windows Forms <xref:System.Windows.Forms.DataGridView> , her veri parçasının kendi hücresini kaplayacağı şekilde, bu tür tablosal verileri geleneksel bir satır ve sütun biçiminde işlemeye yönelik denetim adlı esnek bir denetim sağlar. ' Yi kullanarak <xref:System.Windows.Forms.DataGridView> , tek tek hücrelerin görünümünü özelleştirebilir, rastgele satırları ve sütunları bir yere kilitleyebilir ve diğer özellikler arasında hücrelerde karmaşık denetimleri görüntüleyebilirsiniz.

Ağ üzerinden veri kaynaklarına bağlanmak, Windows Forms akıllı istemcileri olan basit bir görevdir. <xref:System.Windows.Forms.BindingSource>Visual Studio 2005 ve .NET Framework 2,0 ' de Windows Forms yeni olan bileşen, bir veri kaynağına bağlantıyı temsil eder ve verileri denetimlere bağlama, önceki ve sonraki kayıtlara gitme, kayıtları düzenlemeyle ve değişiklikleri özgün kaynağa geri kaydetme yöntemlerini gösterir. <xref:System.Windows.Forms.BindingNavigator>Denetim, <xref:System.Windows.Forms.BindingSource> kullanıcıların kayıtlar arasında gezindiği bileşen üzerinde basit bir arabirim sağlar.

### <a name="data-bound-controls"></a>Veri bağlantılı denetimler

Projenizdeki veritabanları, Web Hizmetleri ve nesneler gibi veri kaynaklarını görüntüleyen Veri Kaynakları penceresini kullanarak veriye dayalı denetimler oluşturabilirsiniz. Öğeleri bu pencereden projenizdeki formlara sürükleyerek veriye göre bağlantılı denetimler oluşturabilirsiniz. Ayrıca, nesneleri veri kaynakları penceresinden var olan denetimlere sürükleyerek verileri verilere bağlayabilirsiniz.

### <a name="settings"></a>Ayarlar

Windows Forms ' de yönetebileceğiniz başka bir veri bağlama türü ayarlarından oluşur. Çoğu akıllı istemci uygulaması, son bilinen form boyutu gibi çalışma zamanı durumuyla ilgili bazı bilgileri korumalıdır ve kayıtlı dosyalar için varsayılan konumlar gibi Kullanıcı tercihi verilerini korur. Uygulama ayarları özelliği, istemci bilgisayardaki her iki ayar türünü depolamanın kolay bir yolunu sağlayarak bu gereksinimleri ele alır. Visual Studio ya da bir kod Düzenleyicisi kullanılarak tanımlandıktan sonra, bu ayarlar XML olarak kalıcı hale getirilir ve çalışma zamanında otomatik olarak belleğe geri okur.

Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın.

|Amaç|Bkz.|
|--------|---------|
|Bileşeni kullanma <xref:System.Windows.Forms.BindingSource>|[Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Denetimlerini BindingSource Bileşeni ile Bağlama](/dotnet/desktop/winforms/controls/bind-wf-controls-with-the-bindingsource)|
|ADO.NET veri kaynaklarıyla çalışma|[Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme](/dotnet/desktop/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component)|
|Veri Kaynakları penceresini kullanma|[İzlenecek yol: Windows formunda verileri görüntüleme](/visualstudio/data-tools/accessing-data-in-visual-studio)|

## <a name="deploying-applications-to-client-computers"></a>Istemci bilgisayarlara uygulama dağıtma

Uygulamanızı yazdıktan sonra, kendi istemci bilgisayarlarına yükleyip çalıştırabilmeleri için bu uygulamayı kullanıcılarınıza göndermeniz gerekir. ClickOnce teknolojisini kullanarak uygulamalarınızı Visual Studio 'dan yalnızca birkaç tıklamayla dağıtabilir ve kullanıcılara web üzerinde uygulamanıza işaret eden bir URL sağlayabilirsiniz. ClickOnce, uygulamanızdaki tüm öğeleri ve bağımlılıkları yönetir ve uygulamanın istemci bilgisayara düzgün şekilde yüklenmesini sağlar.

ClickOnce uygulamaları yalnızca Kullanıcı ağa bağlıyken çalışacak şekilde veya hem çevrimiçi hem de çevrimdışı çalıştırıldığında çalıştırılacak şekilde yapılandırılabilir. Bir uygulamanın çevrimdışı işlemi desteklemesi gerektiğini belirttiğinizde, ClickOnce kullanıcının **Başlangıç** menüsünde uygulamanıza bir bağlantı ekler, böylece Kullanıcı bunu URL kullanmadan açabilir.

Uygulamanızı güncelleştirdiğinizde, yeni bir dağıtım bildirimi ve uygulamanızın yeni bir kopyasını Web sunucunuza yayımlarsınız. ClickOnce, kullanılabilir bir güncelleştirme olduğunu algılar ve kullanıcının yüklemesini yükseltir; Eski derlemeleri güncelleştirmek için özel programlama gerekmez.

ClickOnce 'a tam giriş için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment). Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:

|Amaç|Bkz.|
|--------|---------|
|ClickOnce ile uygulama dağıtma|[Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](/visualstudio/deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard)<br /><br /> [İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)|
|ClickOnce dağıtımını güncelleştirme|[Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](/visualstudio/deployment/how-to-manage-updates-for-a-clickonce-application)|
|ClickOnce ile güvenliği yönetme|[Nasıl yapılır: ClickOnce Güvenlik Ayarlarını Etkinleştirme](/visualstudio/deployment/how-to-enable-clickonce-security-settings)|

## <a name="other-controls-and-features"></a>Diğer denetimler ve Özellikler

Windows Forms ' de, iletişim kutuları oluşturma, yazdırma, yardım ve belge ekleme ve uygulamanızı birden çok dile yerelleştirme gibi genel görevleri hızlı ve kolay bir şekilde uygulamayı sağlayan birçok farklı özelliği vardır. Ayrıca, Windows Forms, müşterilerinize daha güvenli uygulamalar yayınlemenize olanak tanıyan .NET Framework güçlü güvenlik sistemine bağlıdır.

Bu özellikleri kullanma hakkında adım adım bilgiler için aşağıdaki Yardım konularına bakın:

|Amaç|Bkz.|
|--------|---------|
|Form içeriğini yazdırma|[Nasıl yapılır: Windows Forms'da Grafik Yazdırma](/dotnet/desktop/winforms/advanced/how-to-print-graphics-in-windows-forms)<br /><br /> [Nasıl yapılır: Windows Forms'da Çok Sayfalı Metin Dosyası Yazdırma](/dotnet/desktop/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms)|
|Windows Forms güvenliği hakkında daha fazla bilgi edinin|[Windows Forms'ta Güvenliğe Genel Bakış](/dotnet/desktop/winforms/security-in-windows-forms-overview)|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- [Windows Forms'a Genel Bakış](/dotnet/desktop/winforms/windows-forms-overview)
- [My.Forms Nesnesi](../../language-reference/objects/my-forms-object.md)
