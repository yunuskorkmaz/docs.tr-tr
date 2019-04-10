---
title: 'İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 1527e3b4b614d4e700ae0c2c0fc555e14c7bc8d2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314834"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a>İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)
Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryosu kullanarak verilerine erişmek için saklı yordamlar yalnızca. Bu yaklaşım, genellikle veri deposu nasıl erişilir sınırlamak için Veritabanı yöneticileri tarafından kullanılır.  
  
> [!NOTE]
>  Saklı yordamları kullanabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle de varsayılan davranışı geçersiz kılmak için uygulamaları `Create`, `Update`, ve `Delete` işlemler. Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Bu izlenecek yolda amacı doğrultusunda, Northwind örnek veritabanındaki saklı yordamlar için eşlenen iki yöntemi kullanır: CustOrdersDetail ve CustOrderHist. Eşleme, bir Visual Basic dosyası oluşturmak için SqlMetal komut satırı aracını çalıştırdığınız oluşur. Daha fazla bilgi için bu kılavuzda daha sonra Önkoşullar bölümüne bakın.  
  
 Bu izlenecek yol üzerinde kullanmayan [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Visual Studio kullanan geliştiricilerin de kullanabilir [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] saklı yordam işlevselliği uygulamak için. Bkz: [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu izlenecek yol aşağıdakileri gerektirir:  
  
-   Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest3") kullanır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Northwind örnek veritabanı.  
  
     Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz. Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest3 klasöre kopyalayın.  
  
-   Northwind veritabanından oluşturulan Visual Basic kod dosyası.  
  
     Bu izlenecek yol, şu komut satırıyla SqlMetal Aracı'nı kullanarak yazılmıştır:  
  
     **sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize**  
  
     Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Ayarlama [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.  
  
-   System.Data.Linq derleme projeye ekleniyor.  
  
-   Veritabanı kod dosyası projeye ekleniyor.  
  
-   Veritabanına bir bağlantı oluşturuluyor.  
  
-   Kullanıcı arabirimi ayarlama.  
  
-   Çalıştıran ve uygulamayı test etme.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1. Visual Studio **dosya** menüsünü tıklatın **yeni proje**.  
  
2. İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusunda **Visual Basic**ve ardından **Windows**.  
  
3. İçinde **şablonları** bölmesinde tıklayın **Windows Forms uygulaması**.  
  
4. İçinde **adı** kutusuna **SprocOnlyApp**.  
  
5. **Tamam**'ı tıklatın.  
  
     Windows Forms Tasarımcısı'nı açar.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>LINQ SQL bütünleştirilmiş kod başvurusu ekleme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Derleme standart Windows Forms uygulaması şablonu dahil değildir. Aşağıdaki adımlarda açıklandığı gibi derleme kendiniz eklemeniz gerekir:  
  
#### <a name="to-add-systemdatalinqdll"></a>System.Data.Linq.dll eklemek için  
  
1. İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**.  
  
2. İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
3. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.  
  
     Derleme, projeye eklenir.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye ekleniyor  
 Bu adım Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SqlMetal Aracı'nı kullandığınızı varsayar. Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye eklemek için  
  
1. Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
2. İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest3\northwind.vb taşıyın ve ardından **Ekle**.  
  
     Northwind.vb dosya projeye eklenir.  
  
## <a name="creating-a-database-connection"></a>Veritabanı bağlantısı oluşturma  
 Bu adımda, Northwind örnek veritabanına bir bağlantı tanımlayın. Bu izlenecek yolu olarak "c:\linqtest3\northwnd.mdf" kullanır.  
  
#### <a name="to-create-the-database-connection"></a>Veritabanı bağlantısı oluşturmak için  
  
1. İçinde **Çözüm Gezgini**, sağ **Form1.vb**ve ardından **kodu görüntüle**.  
  
     `Class Form1` Kod Düzenleyicisi'nde görünür.  
  
2. Aşağıdaki kodu yazın `Form1` kod bloğu:  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a>Kullanıcı arabirimi ayarlama  
 Bu görevde, böylece kullanıcılar, veritabanındaki verilere erişmek için saklı yordamlar yürütebilir bir arabirim oluşturun. Bu izlenecek yol ile geliştirdiğiniz uygulamada yalnızca katıştırılmış uygulama içinde saklı yordamları kullanarak veritabanındaki verileri kullanıcılar erişebilir.  
  
#### <a name="to-set-up-the-user-interface"></a>Kullanıcı arabirimi oluşturan ayarlamak için  
  
1. İade için Windows Forms Tasarımcısı (**Form1.vb[Design]**).  
  
2. Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.  
  
     Araç kutusu açılır.  
  
    > [!NOTE]
    >  Tıklayın **AutoHide** Raptiye kalan gerçekleştirirken araç kutusu açık tutmak için bu bölümdeki adımlar.  
  
3. Sürükleyin iki düğme, iki metin kutuları ve iki etiket araç kutusundan **Form1**.  
  
     Eşlik eden resimde olduğu gibi denetimleri düzenleyin. Genişletin **Form1** denetimleri bir kolayca uyacak şekilde.  
  
4. Sağ **Label1**ve ardından **özellikleri**.  
  
5. Değişiklik **metin** özelliğinden **Label1** için **OrderID girin:**.  
  
6. Aynı şekilde **etiket 2**, değiştirme **metin** özelliğinden **etiket 2** için **CustomerID girin:**.  
  
7. Aynı şekilde değiştirme **metin** özelliği **Button1** için **sipariş ayrıntıları**.  
  
8. Değişiklik **metin** özelliği **Button2** için **siparişi geçmişi**.  
  
     Tüm metni görünür olması düğme denetimleri genişletebilirsiniz.  
  
#### <a name="to-handle-button-clicks"></a>Düğme tıklamaları işlemek için  
  
1. Çift **sipariş ayrıntıları** üzerinde **Form1** oluşturmak için `Button1` olay işleyicisi ve Kod Düzenleyicisi'ni açın.  
  
2. Aşağıdaki kodu yazın `Button1` işleyicisi:  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. Şimdi çift **Button2** oluşturmak için Form1 üzerinde `Button2` olay işleyicisi ve Kod Düzenleyicisi'ni açın.  
  
4. Aşağıdaki kodu yazın `Button2` işleyicisi:  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık uygulamanızı test etmek için zamanı geldi. Veri deposu ile ilgili iki saklı yordam hangi eylemleri için sınırlı olduğunu unutmayın. Bu, girdiğiniz tüm OrderID için dahil edilen ürünleri döndürmek için veya bir geçmiş girdiğiniz CustomerID sipariş edilen ürünleri döndürmek için eylemlerdir.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1. Hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
     Form1 görünür.  
  
2. İçinde **girin OrderID** kutusuna **10249** ve ardından **sipariş ayrıntıları**.  
  
     Bir ileti kutusu 10249 siparişteki ürünleri listeler.  
  
     Tıklayın **Tamam** ileti kutusunu kapatın.  
  
3. İçinde **girin CustomerID** kutusuna `ALFKI`ve ardından **siparişi geçmişi**.  
  
     Bir ileti kutusu ALFKI müşteri siparişi geçmişi listeler.  
  
     Tıklayın **Tamam** ileti kutusunu kapatın.  
  
4. İçinde **girin OrderID** kutusuna `123`ve ardından **sipariş ayrıntıları**.  
  
     "Sonuç yok." bir ileti kutusu görüntüler  
  
     Tıklayın **Tamam** ileti kutusunu kapatın.  
  
5. Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı durdurmak**.  
  
     Hata ayıklama oturumunu kapatır.  
  
6. Denemeler tamamladınız, tıklayabilirsiniz **Projeyi Kapat** üzerinde **dosya** menüsünde ve istendiğinde projenizi kaydedin.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu proje, bazı değişiklikler yaparak geliştirebilirsiniz. Örneğin, bir liste kutusunda mevcut saklı yordamları listeler ve yürütmek için hangi yordamların seçmesine sahip. Ayrıca, raporları bir metin dosyasına çıkışı akış.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [Saklı Yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
