---
title: 'İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 159b65b4b58b9142a168401ea2a881af2714df5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946636"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)
Bu izlenecek yol, yalnızca saklı yordamlar kullanılarak verilere erişmek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için temel uçtan uca bir senaryo sağlar. Bu yaklaşım genellikle veritabanı yöneticileri tarafından veri deposuna nasıl erişildiğini sınırlamak için kullanılır.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Uygulamalarda saklı yordamları, özellikle, `Update`ve `Delete` işlemleri için `Create`varsayılan davranışı geçersiz kılmak için de kullanabilirsiniz. Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Bu izlenecek yolun amaçları doğrultusunda, Northwind örnek veritabanındaki Saklı yordamlarla eşleştirilmiş iki yöntem kullanacaksınız: CustOrdersDetail ve CustOrderHist. Eşleme, bir Visual Basic dosyası oluşturmak için SqlMetal komut satırı aracını çalıştırdığınızda oluşur. Daha fazla bilgi için bu izlenecek yolun ilerleyen kısımlarında yer aldığı Önkoşullar bölümüne bakın.  
  
 Bu izlenecek yol, Nesne İlişkisel Tasarımcısı bağlı değildir. Visual Studio kullanan geliştiriciler, saklı yordam işlevselliğini uygulamak için O/R tasarımcısını da kullanabilir. Bkz. [Visual Studio 'da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yol aşağıdakileri gerektirir:  
  
- Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest3") kullanır. Yönergeye başlamadan önce bu klasörü oluşturun.  
  
- Northwind örnek veritabanı.  
  
     Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest3 klasörüne kopyalayın.  
  
- Northwind veritabanından oluşturulan Visual Basic kod dosyası.  
  
     Bu izlenecek yol, aşağıdaki komut satırı ile SqlMetal Aracı kullanılarak yazılmıştır:  
  
     **sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**  
  
     Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu izlenecek yol altı ana görevden oluşur:  
  
- Visual Studio 'da çözümü kurma. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- System. Data. LINQ bütünleştirilmiş kodu projeye ekleniyor.  
  
- Veritabanı kod dosyası projeye ekleniyor.  
  
- Veritabanına bağlantı oluşturuluyor.  
  
- Kullanıcı arabirimini ayarlama.  
  
- Uygulamayı çalıştırma ve test etme.  
  
## <a name="creating-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturma  
 Bu ilk görevde, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz.  
  
### <a name="to-create-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturmak için  
  
1. Visual Studio **Dosya** menüsünde **Yeni proje**' ye tıklayın.  
  
2. **Yeni proje** Iletişim kutusundaki **proje türleri** bölmesinde **Visual Basic**öğesini genişletin ve ardından **Windows**' a tıklayın.  
  
3. **Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.  
  
4. **Ad** kutusuna **SprocOnlyApp**yazın.  
  
5. **Tamam**'ı tıklatın.  
  
     Windows Form Tasarımcısı açılır.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>LINQ to SQL bütünleştirilmiş kod başvurusu ekleniyor  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Derleme, standart Windows Forms uygulama şablonuna dahil değildir. Aşağıdaki adımlarda açıklandığı gibi derlemeyi kendiniz eklemeniz gerekir:  
  
### <a name="to-add-systemdatalinqdll"></a>System. Data. LINQ. dll eklemek için  
  
1. **Çözüm Gezgini**, **tüm dosyaları göster**' e tıklayın.  
  
2. **Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.  
  
3. **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.  
  
     Derleme projeye eklenir.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyasını projeye ekleme  
 Bu adımda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SqlMetal aracını kullandığınız varsayılır. Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a>Projeye Northwind kod dosyasını eklemek için  
  
1. **Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.  
  
2. **Varolan öğe Ekle** iletişim kutusunda c:\linqtest3\northwind.exe ' e gidin ve ardından **Ekle**' ye tıklayın.  
  
     Northwind. vb dosyası projeye eklenir.  
  
## <a name="creating-a-database-connection"></a>Veritabanı bağlantısı oluşturma  
 Bu adımda, Northwind örnek veritabanına olan bağlantıyı tanımlarsınız. Bu izlenecek yol, yol olarak "c:\linqtest3\kuzeydoğu WND.exe" kullanır.  
  
### <a name="to-create-the-database-connection"></a>Veritabanı bağlantısını oluşturmak için  
  
1. **Çözüm Gezgini**, **Form1. vb**öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.  
  
     `Class Form1`Kod düzenleyicisinde görünür.  
  
2. `Form1` Kod bloğuna aşağıdaki kodu yazın:  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Kullanıcı arabirimini ayarlama  
 Bu görevde, kullanıcıların veritabanındaki verilere erişmek için saklı yordamları yürütebilmesi için bir arabirim oluşturursunuz. Bu kılavuzlarla geliştirdiğiniz uygulamada, kullanıcılar veritabanındaki verilere yalnızca uygulamada gömülü saklı yordamları kullanarak erişebilirler.  
  
### <a name="to-set-up-the-user-interface"></a>Kullanıcı arabirimini ayarlamak için  
  
1. Windows Form Tasarımcısı dön (**Form1. vb [Design]** ).  
  
2. **Görünüm** menüsünde **araç kutusu**' na tıklayın.  
  
     Araç kutusu açılır.  
  
    > [!NOTE]
    > Bu bölümde kalan adımları gerçekleştirirken araç kutusunu açık tutmak için otomatik **gizleme** raptiye ' ye tıklayın.  
  
3. İki düğme, iki metin kutusu ve iki etiketi araç kutusundan **Form1**üzerine sürükleyin.  
  
     Denetimleri, eşlik eden çizimde olduğu gibi düzenleyin. Denetimlerin kolayca sığması için **Form1** ' i genişletin.  
  
4. **Label1**öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
5. **Text** özelliğini **Label1** olarak değiştirin, **OrderID: yazın**.  
  
6. **Etiket 2**için aynı şekilde, **Etiket 2** ' deki **Text** özelliğini CustomerID olarak değiştirin **:** .  
  
7. Aynı şekilde, **button1** için **metin** özelliğini **sipariş ayrıntıları**olarak değiştirin.  
  
8. **Button2** için **metin** özelliğini **sıra geçmişiyle**değiştirin.  
  
     Düğme denetimlerini tüm metinlerin görünür olması için genişletebilirsiniz.  
  
### <a name="to-handle-button-clicks"></a>Düğme tıklamalarını işlemek için  
  
1. `Button1` Olay işleyicisini oluşturmak ve kod düzenleyicisini açmak için **Form1** üzerindeki **Düzen ayrıntıları** ' na çift tıklayın.  
  
2. `Button1` İşleyiciye aşağıdaki kodu yazın:  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. Şimdi, `Button2` olay işleyicisini oluşturmak ve kod düzenleyicisini açmak için Form1 üzerinde **button2** 'e çift tıklayın.  
  
4. `Button2` İşleyiciye aşağıdaki kodu yazın:  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık uygulamanızı test etmek zaman alabilir. Veri deposu ile kişinizin, iki saklı yordamın gerçekleştirebileceği eylemlerle sınırlı olduğunu unutmayın. Bu eylemler, girdiğiniz herhangi bir OrderID 'ye dahil edilen ürünleri döndürmek veya girdiğiniz her bir müşteri için sipariş edilen ürünlerin geçmişini döndürmemelidir.  
  
### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1. Hata ayıklamayı başlatmak için F5 'e basın.  
  
     Form1 görüntülenir.  
  
2. **OrderID girin** kutusuna **10249** yazın ve ardından **sipariş ayrıntıları**' na tıklayın.  
  
     Sipariş 10249 ' de yer alan ürünler bir ileti kutusunda listelenir.  
  
     İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
3. **CustomerID girin** kutusuna yazın `ALFKI`ve ardından **Sipariş geçmişi**' ne tıklayın.  
  
     Bir ileti kutusu, müşteri ALFKI için sipariş geçmişini listeler.  
  
     İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
4. **OrderID girin** kutusuna yazın `123`ve ardından **sipariş ayrıntıları**' na tıklayın.  
  
     İleti kutusu "sonuç yok" iletisini görüntüler.  
  
     İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
5. **Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' u tıklatın.  
  
     Hata ayıklama oturumu kapanır.  
  
6. Deneme işleminizi tamamladıysanız **Dosya** menüsünde **Projeyi Kapat** ' a tıklayabilir ve istendiğinde projenizi kaydedebilirsiniz.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu projeyi, bazı değişiklikler yaparak geliştirebilirsiniz. Örneğin, kullanılabilir saklı yordamları bir liste kutusunda listeleyebilir ve kullanıcının hangi yordamları yürütebileceği seçmesini sağlayabilirsiniz. Ayrıca raporların çıkışını bir metin dosyasına akışla aktarabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
