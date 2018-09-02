---
title: 'İzlenecek Yol: DataRepeater Denetimindeki Verileri Görüntüleme (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388558"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>İzlenecek Yol: DataRepeater Denetimindeki Verileri Görüntüleme (Visual Studio)
Bu izlenecek yolda ilişkili verileri görüntülemek için temel bir başlangıç ve bitiş senaryosu sağlar. bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
## <a name="prerequisite"></a>Önkoşul  
 Bu izlenecek yol, Northwind örnek veritabanıyla kurulan gerektirir.  
  
 Geliştirme bilgisayarınızda bu veritabanı yoksa Microsoft Download Center'dan gelen indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuzun ilk bölümü dört ana görevden oluşur:  
  
-   Bir çözüm oluşturma.  
  
-   Ekleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
-   Veri kaynağı ekleme.  
  
-   Verilere bağlı denetimler ekleme.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>DataRepeater çözümü oluşturma  
 Bu adımda, bir proje ve çözüm oluşturun.  
  
#### <a name="to-create-a-datarepeater-solution"></a>DataRepeater çözüm oluşturmak için  
  
1.  Visual Studio **dosya** menüsünü tıklatın **yeni proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusunda **Visual Basic**ve ardından **Windows**.  
  
3.  İçinde **şablonları** bölmesinde tıklayın **Windows Forms uygulaması**.  
  
4.  İçinde **adı** kutusuna `DataRepeaterApp`.  
  
5.  **Tamam**'ı tıklatın.  
  
     Windows Forms Tasarımcısı'nı açar.  
  
6.  Formu Windows Form Tasarımcısı'nda seçin. İçinde **özellikleri** penceresinde **boyutu** özelliğini `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>DataRepeater denetimi ekleme  
 Bu adımda eklediğiniz bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> forma.  
  
#### <a name="to-add-a-datarepeater-control"></a>DataRepeater denetimi eklemek için  
  
1.  Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.  
  
     **Araç kutusu** açılır.  
  
2.  Seçin **Visual Basic PowerPacks** sekmesi.  
  
3.  Sürükleme bir <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi **Form1**.  
  
4.  Özellikler penceresinde ayarlayın **konumu** özelliğini `0, 25`.  
  
5.  Ayarlama **boyutu** özelliğini `460, 600`.  
  
## <a name="adding-a-data-source"></a>Veri kaynağı ekleme  
 Bu adımda, bir veri kaynağı için eklediğiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
#### <a name="to-add-a-data-source"></a>Bir veri kaynağı eklemek için  
  
1.  Üzerinde **veri** menüsünü tıklatın **veri kaynaklarını Göster**.  
  
2.  İçinde **veri kaynakları** penceresinde tıklayın **yeni veri kaynağı Ekle**.  
  
3.  Seçin **veritabanı** üzerinde **bir veri kaynağı türü seçin** sayfasında ve ardından **sonraki**.  
  
4.  Üzerinde **veri bağlantınızı seçin** sayfasında, aşağıdaki adımlardan birini gerçekleştirin:  
  
    -   Northwind örnek veritabanıyla kurulan veri bağlantısı açılan listede kullanılabilir durumdaysa bu bağlantıya tıklayın.  
  
         veya  
  
    -   Tıklayın **yeni bağlantı** yeni bir veri bağlantısı yapılandırmak için. Daha fazla bilgi için [yeni bağlantı ekleme](/visualstudio/data-tools/add-new-connections).  
  
5.  Veritabanına parola gerekiyorsa, hassas verileri eklemek ve ardından seçeneğini **sonraki**.  
  
    > [!NOTE]
    >  Bir iletişim kutusu görüntülenirse, tıklayın **Evet** dosyayı projenize kaydetmek için.  
  
6.  Tıklayın **sonraki** üzerinde **bağlantı dizesini uygulama yapılandırma dosyasına Kaydet** sayfası.  
  
7.  Genişletin **tabloları** düğümde **veritabanı nesnelerinizi seçin** sayfası.  
  
8.  Yanındaki onay kutularını işaretleyin **müşteriler** ve **siparişler** tablolar ve ardından **son**.  
  
     **NorthwindDataSet** projenize eklenir ve **müşteriler** ve **siparişler** tablolar görünür **veri kaynakları** penceresi.  
  
## <a name="adding-data-bound-controls"></a>Verilere bağlı denetimler ekleme  
 Bu adımda, verilere bağlı denetimler ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Verilere bağlı denetimler eklemek için  
  
1.  İçinde **veri kaynakları** penceresinde için üst düzey düğümü seçmek **müşteriler** tablo.  
  
2.  Tabloya bırakma türünü değiştirme **ayrıntıları** tıklayarak **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
3.  Seçin **müşteriler** tablo düğüm ve öğe şablonu bölgesi (üst bölge) sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
     A <xref:System.Windows.Forms.BindingNavigator> denetimi forma eklenir ve **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, ve **CustomersBindingNavigator** bileşenler, bileşen tepsisine eklenir.  
  
4.  Tüm alanları ve bunların ilişkili etiketleri seçin ve bunları öğesi şablon alanının sol kenardaki konumlandırın.  
  
5.  Son beş alanları seçin (**bölge**, **posta kodu**, **Ülke**, **telefon**, ve **faks**) ve kendi ilişkili etiketleri ve yukarı ve sağa ilk altı alanların taşıyın.  
  
6.  Öğe şablonu (üst bölge denetimin) seçin.  
  
7.  Özellikler penceresinde ayarlayın **boyutu** özelliğini `427, 170`.  
  
 Bu noktada, yinelenen müşterilerin listesini görüntüleyen bir çalışan uygulamanız var. Uygulamayı çalıştırmak, verileri değiştirme ve ekleyin veya müşteri kayıtları silmek için F5 tuşuna basabilirsiniz.  
  
 İsteğe bağlı sonraki adımlarda nasıl özelleştirileceğini öğreneceksiniz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
## <a name="next-steps-optional"></a>Sonraki adımlar (isteğe bağlı)  
 Kılavuzun bu bölümü, dört isteğe bağlı görevden oluşur:  
  
-   Görünümünü değiştirme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
-   Kullanıcıların ekleme veya kayıt silme engelliyor.  
  
-   Arama özelliği ekleniyor <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
-   Bir ana ve ayrıntı tablosunu ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>DataRepeater denetiminin görünümünü değiştirme  
 İsteğe bağlı Bu adımda, değiştirdiğiniz `BackColor` , <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> tasarım zamanında denetimi. Ayrıca değişen renklerde satırları görüntülemek ve bir etiketin değiştirmek için kod ekleme `ForeColor` koşullu olarak.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Denetiminin görünümünü değiştirmek için  
  
1.  Windows Form Tasarımcısı'nda (alt) ana bölgesi seçin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
2.  Özellikler penceresinde ayarlayın `BackColor` beyaz özelliği.  
  
3.  Çift <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kod Düzenleyicisi'ni açın.  
  
4.  Kod Düzenleyicisi'nde olay açılan listesinde, **DrawItem**.  
  
5.  İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi için alternatif aşağıdaki kodu ekleyin `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  İçinde <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> olay işleyicisi değiştirmek için aşağıdaki kodu ekleyin `ForeColor` bir koşula bağlı bir etiketin:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Uygulamayı çalıştırmak ve istediğiniz özelleştirmeleri görmek için F5 tuşuna basın.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Kullanıcıların eklemek veya kayıtları silme  
 İsteğe bağlı Bu adımda, kullanıcıların ekleme veya kayıt silme engelleyen kod ekleme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Ekleme ve silme kayıtlarını kullanıcıların engellemek için  
  
1.  Windows Form Tasarımcısı'nda, formun Kod Düzenleyicisi'ni açmak için çift tıklayın.  
  
2.  Aşağıdaki kodu ekleyin `Form_Load` olay:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Sınıf adı aşağı açılan listesinde, tıklayın **BindingNavigatorDeleteItem**. Yöntem adı aşağı açılan listesinde, tıklayın **EnabledChanged**.  
  
4.  Aşağıdaki kodu ekleyin `BindingNavigatorDeleteItem_EnabledChanged` olay işleyicisi:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Bu adım gereklidir çünkü <xref:System.Windows.Forms.BindingSource> etkinleştirecek **DeleteItem** düğmesi geçerli kayıtta değişiklikleri her zaman.  
  
5.  Uygulamayı çalıştırmak için F5 tuşuna basın. Dikkat **DeleteItem** düğmesi devre dışıdır ve DELETE tuşuna basarak öğeleri, silemezsiniz.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>DataRepeater denetimine arama özelliği ekleniyor  
 İsteğe bağlı Bu adımda, bir değer için arama olanağı uygulamak <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Arama dizesi bulunursa denetim öğesi görünüme gelene ve değeri içeren öğeyi seçer.  
  
#### <a name="to-add-search-capability"></a>Arama özelliği eklemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TextBox> denetimi **araç kutusu** içeren form üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
     Altında konumlandırın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
2.  Özellikler penceresinde değişiklik **adı** özelliğini **SearchTextBox**.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.Button> denetimi **araç kutusu** içeren form üzerine <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi. Altında konumlandırın <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
4.  Özellikler penceresinde değişiklik **adı** özelliğini **SearchButton**. Değişiklik **metin** özelliğini **arama**.  
  
5.  Çift <xref:System.Windows.Forms.Button> Kod Düzenleyicisi'ni açmak için Denetim ve aşağıdaki kodu ekleyin `SearchButton_Click` olay işleyicisi.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Uygulamayı çalıştırmak için F5 tuşuna basın. Bir müşteri kimliği türü **SearchTextBox** tıklatıp **arama** düğmesi.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Bir ana ve ayrıntı tablosunu DataRepeater için ekleme  
 Bu isteğe bağlı adımda eklediğiniz ikinci <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> her bir müşterinin ilgili siparişlerini görüntülemek üzere Denetim.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Bir ana ve ayrıntı tablosunu eklemek için  
  
1.  İkinci sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi **Visual Basic PowerPacks** sekmesinde **araç kutusu** forma.  
  
2.  Özellikler penceresinde ayarlayın **konumu** özelliğini `465, 25`.  
  
3.  Ayarlama **boyutu** özelliğini `315, 600`.  
  
4.  İçinde **veri kaynakları** penceresini genişletin **müşteriler** ayrıntı düğüm için düğüm tablosunu seçip **siparişler** tablo.  
  
5.  Bırakma türünü bu değiştirme **siparişler** ayrıntıları tabloya tıklayarak **ayrıntıları** Tablo düğümü aşağı açılan listesinde.  
  
6.  Bu sürükleyin **siparişler** ikinci öğe şablonu bölgesi (üst bölge) tablo düğüme <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
     Bir **OrdersBindingSource** bileşeni ve bir **OrdersTableAdapter** bileşeni bileşen tepsisine eklenir.  
  
7.  Uygulamayı çalıştırmak için F5 tuşuna basın. İlk her müşteri seçtiğinizde, <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetlemek, siparişler, müşteri görüntülenir için ikinci <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> denetimi.  
  
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
