---
title: 'İzlenecek Yol: DataRepeater Denetimindeki Verileri Görüntüleme (Visual Studio)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93072bf30c8ee2a4a44c4862de0882072c298f8b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>İzlenecek Yol: DataRepeater Denetimindeki Verileri Görüntüleme (Visual Studio)
Bu kılavuzda ilişkili verileri görüntülemek için bir temel başlangıç-bitiş senaryo sağlar bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
## <a name="prerequisite"></a>Önkoşul  
 Bu kılavuz, Northwind örnek veritabanı gerektirir.  
  
 Bu veritabanı geliştirme bilgisayarınızda yoksa, buradan indirebilirsiniz [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Yönergeler için bkz: [örnek veritabanları yükleme](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuzun ilk bölümü dört ana görevden oluşur:  
  
-   Bir çözümü oluşturma.  
  
-   Ekleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
-   Veri kaynağı ekleme.  
  
-   Verilere bağlı denetimler ekleme.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>DataRepeater çözümü oluşturma  
 İlk adımda bir proje ve çözüm oluşturun.  
  
#### <a name="to-create-a-datarepeater-solution"></a>DataRepeater çözüm oluşturmak için  
  
1.  Visual Studio üzerinde **dosya** menüsünde tıklatın **yeni proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusunda, genişletin **Visual Basic**ve ardından **Windows**.  
  
3.  İçinde **şablonları** bölmesinde tıklatın **Windows Forms uygulaması**.  
  
4.  İçinde **adı** kutusuna `DataRepeaterApp`.  
  
5.  **Tamam**'ı tıklatın.  
  
     Windows Forms Tasarımcısı'nı açar.  
  
6.  Windows Forms Tasarımcısı'nda formu seçin. İçinde **özellikleri** penceresindeki ayarlayın **boyutu** özelliğine `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>DataRepeater denetimi ekleme  
 Bu adımda eklediğiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> forma denetim.  
  
#### <a name="to-add-a-datarepeater-control"></a>DataRepeater denetimi eklemek için  
  
1.  Üzerinde **Görünüm** menüsünde tıklatın **araç**.  
  
     **Araç** açar.  
  
2.  Seçin **Visual Basic PowerPacks** sekmesi.  
  
3.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> üzerine kontrol **Form1**.  
  
4.  Özellikler penceresinde ayarlayın **konumu** özelliğine `0, 25`.  
  
5.  Ayarlama **boyutu** özelliğine `460, 600`.  
  
## <a name="adding-a-data-source"></a>Veri kaynağı ekleme  
 Bu adımda, bir veri kaynağı için ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
#### <a name="to-add-a-data-source"></a>Bir veri kaynağı eklemek için  
  
1.  Üzerinde **veri** menüsünde tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde tıklatın **yeni veri kaynağı Ekle**.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seç** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı** sayfasında, aşağıdaki adımlardan birini gerçekleştirin:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı açılan listede kullanılabilir durumdaysa bu bağlantıya tıklayın.  
  
         veya  
  
    -   Tıklatın **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için. Daha fazla bilgi için bkz: [yeni bağlantılar eklemek](/visualstudio/data-tools/add-new-connections).  
  
5.  Veritabanı parola gerektiriyorsa, hassas bilgileri Ekle ve ardından seçeneğini **sonraki**.  
  
    > [!NOTE]
    >  Bir iletişim kutusu görüntülenirse, tıklatın **Evet** dosyayı projenize kaydetmek için.  
  
6.  Tıklatın **sonraki** üzerinde **uygulama yapılandırma dosyasında bağlantı dizesini kaydedin** sayfası.  
  
7.  Genişletme **tabloları** düğümde **veritabanı nesnelerinizi** sayfası.  
  
8.  Onay kutularını işaretleyin **müşteriler** ve **siparişleri** tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** ve **siparişleri** tabloları görünür **veri kaynakları** penceresi.  
  
## <a name="adding-data-bound-controls"></a>Verilere bağlı denetimler ekleme  
 Bu adımda, verilere bağlı denetimler ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Verilere bağlı denetimler eklemek için  
  
1.  İçinde **veri kaynakları** penceresi, üst düzey düğümü seçin **müşteriler** tablo.  
  
2.  Tabloya açılan türünü değiştirme **ayrıntıları** tıklayarak **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
3.  Seçin **müşteriler** Tablo düğümü ve Madde şablonu bölgesini (üst bölge) sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
     A <xref:System.Windows.Forms.BindingNavigator> denetimi forma eklenir ve **NorthwindDataSet**, **CustomersBindingSource**, **TableAdapter**,  **TableAdapterManager**, ve **CustomersBindingNavigator** bileşenleri bileşen Tepsisi eklenir.  
  
4.  Tüm alanları ve bunların ilişkili etiketleri seçin ve Madde şablonu bölgesi sol kenarı yerleştir.  
  
5.  Son beş alanları seçin (**bölge**, **posta kodu**, **Ülke**, **telefon**, ve **faks**) ve bunların ilişkili etiketleri ve en fazla ve ilk altı alanlarının sağa taşıyın.  
  
6.  Öğe şablonu (Denetim üst bölge) seçin.  
  
7.  Özellikler penceresinde ayarlayın **boyutu** özelliğine `427, 170`.  
  
 Bu noktada, yinelenen müşterilerin listesini görüntüler ve çalışan bir uygulama vardır. Uygulamayı çalıştırın, verileri değiştirebilir ve eklemek veya Müşteri kayıtlarını silmek için F5 tuşuna basabilirsiniz.  
  
 İsteğe bağlı sonraki adımlarda özelleştirme hakkında bilgi edineceksiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
## <a name="next-steps-optional"></a>Sonraki adımlar (isteğe bağlı)  
 Kılavuzun bu bölümü dört isteğe bağlı görevden oluşur:  
  
-   Görünümünü değiştirme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
-   Kullanıcıların ekleme veya kayıt silme engelliyor.  
  
-   İçin arama yeteneğine ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
-   Ana ve ayrıntı tabloya ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>DataRepeater denetiminin görünümünü değiştirme  
 Bu isteğe bağlı adım, değişiklik `BackColor` , <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> tasarım zamanında denetim. Ayrıca değişen renklerde satırları görüntülemek ve bir etiketin değiştirmek için kodu ekleyin `ForeColor` koşullu.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Denetimin görünümünü değiştirmek için  
  
1.  Windows Forms Tasarımcısı'nda ana (alt) bölgesini seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
2.  Özellikler penceresinde ayarlayın `BackColor` beyaz özelliği.  
  
3.  Çift <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kod Düzenleyicisi'ni açın.  
  
4.  Kod Düzenleyicisi'nde olay açılan listesinde, **DrawItem**.  
  
5.  İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi için alternatif aşağıdaki kodu ekleyin `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi değiştirmek için aşağıdaki kodu ekleyin `ForeColor` etiket bağlı bir koşul olarak:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Uygulamayı çalıştırın ve özelleştirmeleri görmek için F5 tuşuna basın.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Kullanıcıların ekleme veya kayıt silme önleme  
 İsteğe bağlı Bu adımda, kullanıcıların ekleme veya kayıt silme engeller kodu ekleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Kayıtları ekleme ve silme kullanıcıların engellemek için  
  
1.  Windows Forms Tasarımcısı'nda formun Kod Düzenleyicisi'ni açmak için çift tıklayın.  
  
2.  Aşağıdaki kodu ekleyin `Form_Load` olay:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Sınıf adı açılan listeye tıklayın **BindingNavigatorDeleteItem**. Yöntem adı açılan listeye tıklayın **EnabledChanged**.  
  
4.  Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesini geçerli kayıt değişiklikleri her zaman.  
  
5.  Uygulamayı çalıştırmak için F5 tuşuna basın. Dikkat **DeleteItem** düğmesi devre dışıdır ve DELETE tuşuna basarak öğelerini, silemezsiniz.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>DataRepeater denetimi için arama yeteneğine ekleme  
 İsteğe bağlı Bu adımda, bir değer için arama yeteneği uygulamak <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Arama dizesi bulunursa, denetim değeri içeren ve öğe görünüme gelene öğeyi seçer.  
  
#### <a name="to-add-search-capability"></a>Arama özelliği eklemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> gelen denetim **araç** içeren forma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
     Bunun altına getirin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
2.  Özellikler penceresinde değiştirin **adı** özelliğine **SearchTextBox**.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> gelen denetim **araç** içeren forma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim. Bunun altına getirin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
4.  Özellikler penceresinde değiştirin **adı** özelliğine **SearchButton**. Değişiklik **metin** özelliğine **arama**.  
  
5.  Çift <xref:System.Windows.Forms.Button> Kod Düzenleyicisi'ni açmak için Denetim ve aşağıdaki kodu ekleyin `SearchButton_Click` olay işleyicisi.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Uygulamayı çalıştırmak için F5 tuşuna basın. Bir müşteri kimliği yazın **SearchTextBox** tıklatıp **arama** düğmesi.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Ana ve ayrıntı tablosunu DataRepeater ekleme  
 İsteğe bağlı Bu adımda eklediğiniz ikinci bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> her müşteri için ilgili siparişleri görüntülemek için denetimi.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Ana ve ayrıntı tablo eklemek için  
  
1.  İkinci bir sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> gelen denetim **Visual Basic PowerPacks** sekmesinde **araç** forma.  
  
2.  Özellikler penceresinde ayarlayın **konumu** özelliğine `465, 25`.  
  
3.  Ayarlama **boyutu** özelliğine `315, 600`.  
  
4.  İçinde **veri kaynakları** penceresinde genişletin **müşteriler** Tablo düğümü ve ayrıntı düğümü seçin **siparişleri** tablo.  
  
5.  Bu açılan türünü değiştirme **siparişleri** tıklatarak ayrıntıları tabloya **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
6.  Bu sürükleme **siparişleri** Tablo düğümü ikinci öğe şablonu bölgesi (üst bölge) üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
     Bir **OrdersBindingSource** bileşeni ve bir **OrdersTableAdapter** bileşen için bileşen Tepsisi eklenir.  
  
7.  Uygulamayı çalıştırmak için F5 tuşuna basın. Her bir müşteri ilk seçtiğinizde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek, siparişler o müşteri görüntülenir için ikinci <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetim.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataRepeater Denetimine Giriş](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Bağlı Verileri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimindeki İlişkisiz Denetimleri Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetimi Düzenini Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Öğe Üst Bilgilerini Görüntüleme](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Denetiminde Veri Arama](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [Nasıl yapılır: iki DataRepeater denetimi (Visual Studio) kullanarak ana/ayrıntı formu oluşturma](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Nasıl Yapılır: DataRepeater Denetiminin Görünümünü Değiştirme](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Nasıl Yapılır: DataRepeater Öğelerini Eklemeyi ve Silmeyi Devre Dışı Bırakma](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [DataRepeater Denetiminde Sorun Giderme](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
