---
title: "İzlenecek yol: Kullanarak yalnızca (C#) saklı yordamlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 52c9cfeab362a1603c1d18a9caa1601cd76711b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-using-only-stored-procedures-c"></a>İzlenecek yol: Kullanarak yalnızca (C#) saklı yordamlar
Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yürüterek verilere erişmek için senaryo saklı yordamlar yalnızca. Bu yaklaşım, genellikle veri deposu nasıl erişilir sınırlamak için Veritabanı yöneticileri tarafından kullanılır.  
  
> [!NOTE]
>  Saklı yordamların de kullanabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle için varsayılan davranışı geçersiz kılmak için uygulamalar `Create`, `Update`, ve `Delete` işlemler. Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
  
 Bu kılavuzda amaçları doğrultusunda, Northwind örnek veritabanı saklı yordamlarda eşlenen iki yöntemi kullanır: CustOrdersDetail ve CustOrderHist. Bir C# dosyası oluşturmak için SqlMetal komut satırı aracını çalıştırdığınızda eşleme oluşur. Daha fazla bilgi için bu kılavuzda daha sonra Önkoşullar bölümüne bakın.  
  
 Bu kılavuzda üzerinde bağlı değildir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Kullanan geliştiriciler [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] de kullanabilirsiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] saklı yordam işlevleri uygulamak için. Bkz: [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu kılavuz, Visual C# geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu kılavuz aşağıdakileri gerektirir:  
  
-   Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest7") kullanılır. İzlenecek yol başlamadan önce bu klasörü oluşturun.  
  
-   Northwind örnek veritabanı.  
  
     Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz. Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md). Veritabanı indirdikten sonra northwnd.mdf dosyasını c:\linqtest7 klasörüne kopyalayın.  
  
-   Northwind veritabanından oluşturulan bir C# kod dosyası.  
  
     Bu kılavuz, aşağıdaki komut satırı ile SqlMetal aracı kullanılarak yazılmış olduğundan:  
  
     **sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / çoğul**  
  
     Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuz altı ana görevden oluşur:  
  
-   Ayarlama [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çözümde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].  
  
-   System.Data.Linq derleme projesine ekleniyor.  
  
-   Veritabanı kod dosyası projesine ekleniyor.  
  
-   Veritabanıyla bağlantı oluşturma.  
  
-   Kullanıcı arabirimi ayarlama.  
  
-   Çalıştıran ve uygulamayı test etme.  
  
## <a name="creating-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturma  
 Bu ilk görevde oluşturduğunuz bir [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] derlemek ve çalıştırmak için gerekli başvuruları içeren çözüm bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>Bir LINQ to SQL çözümü oluşturmak için  
  
1.  Üzerinde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **dosya** menüsündeki **yeni**ve ardından **proje**.  
  
2.  İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual C#**.  
  
3.  İçinde **şablonları** bölmesinde tıklatın **Windows Forms uygulaması**.  
  
4.  İçinde **adı** kutusuna **SprocOnlyApp**.  
  
5.  İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.  
  
6.  **Tamam**'ı tıklatın.  
  
     Windows Forms Tasarımcısı'nı açar.  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a>LINQ SQL derleme başvurusu ekleme  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Standart Windows Forms uygulaması şablonunda derleme dahil değildir. Aşağıdaki adımlarda açıklandığı gibi derleme kendiniz eklemeniz gerekir:  
  
#### <a name="to-add-systemdatalinqdll"></a>System.Data.Linq.dll eklemek için  
  
1.  İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.  
  
2.  İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.  
  
     Derleme projeye eklenir.  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye ekleme  
 Bu adım, Northwind örnek veritabanı'ndaki bir kod dosyası oluşturmak için SqlMetal Aracı'nı kullandığınızı varsayar. Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Northwind kod dosyası projeye eklemek için  
  
1.  Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.  
  
2.  İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest7\northwind.cs taşıyın ve ardından **Ekle**.  
  
     Northwind.cs dosyası projeye eklenir.  
  
## <a name="creating-a-database-connection"></a>Veritabanı bağlantısı oluşturma  
 Bu adımda, Northwind örnek veritabanı için bağlantı tanımlayın. Bu izlenecek yolu olarak "c:\linqtest7\northwnd.mdf" kullanır.  
  
#### <a name="to-create-the-database-connection"></a>Veritabanı bağlantısı oluşturmak için  
  
1.  İçinde **Çözüm Gezgini**, sağ **Form1.cs**ve ardından **görünümü kodu**.  
  
2.  Aşağıdaki kodu yazın `Form1` sınıfı:  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a>Kullanıcı arabirimi ayarlama  
 Bu görevde kullanıcıların veritabanındaki verilere erişmek için saklı yordamlar çalıştırabilmeniz için bir arabirim ayarlayın. Bu kılavuzda ile geliştirdiğiniz uygulamalarda yalnızca uygulama içinde katıştırılmış saklı yordamları kullanarak veritabanındaki verileri kullanıcılar erişebilir.  
  
#### <a name="to-set-up-the-user-interface"></a>Kullanıcı arabirimini oluşturan ayarlamak için  
  
1.  Return Windows Forms Tasarımcısı (**Form1.cs[Design]**).  
  
2.  Üzerinde **Görünüm** menüsünde tıklatın **araç**.  
  
     Araç kutusu açılır.  
  
    > [!NOTE]
    >  Tıklatın **AutoHide** Raptiye kalan gerçekleştirirken araç kutusunu açık tutmak için bu bölümdeki adımları.  
  
3.  Sürükleme iki düğmeler, iki metin kutusu ve iki etiket Kutusu'ndan **Form1**.  
  
     Denetimleri eşlik eden çizim olduğu gibi düzenleyin. Genişletme **Form1** denetimleri kolayca uyacak şekilde.  
  
4.  Sağ **label1**ve ardından **özellikleri**.  
  
5.  Değişiklik **metin** özelliğinden **label1** için **OrderID girin:**.  
  
6.  İçin de aynı şekilde **label2**, değiştirme **metin** özelliğinden **label2** için **CustomerID girin:**.  
  
7.  Aynı şekilde değiştirme **metin** özelliği için **button1** için **sipariş ayrıntılarını**.  
  
8.  Değişiklik **metin** özelliği için **button2** için **siparişi geçmişi**.  
  
     Tüm metni görünür olmasını sağlamak düğmesi denetimleri genişletir.  
  
#### <a name="to-handle-button-clicks"></a>Düğme tıklamaları işlemek için  
  
1.  Çift **sipariş ayrıntılarını** üzerinde **Form1** button1 olay işleyicisi Kod düzenleyicisinde açın.  
  
2.  Aşağıdaki kodu yazın `button1` işleyici:  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  Şimdi çift **button2** üzerinde **Form1** açmak için `button2` işleyicisi  
  
4.  Aşağıdaki kodu yazın `button2` işleyici:  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Artık uygulamanızı test etmek için zaman yapılır. Veri deposu ile ilgili iki saklı yordamlar hangi eylemleri için sınırlı olduğunu unutmayın. Bu, girdiğiniz tüm OrderID için eklenen ürünlerle döndürülecek veya girdiğiniz tüm CustomerID sipariş ürünleri geçmişini dönmek için eylemlerdir.  
  
#### <a name="to-test-the-application"></a>Uygulamayı test etmek için  
  
1.  Hata ayıklamayı başlatmak için F5 tuşuna basın.  
  
     Form1 görüntülenir.  
  
2.  İçinde **girin OrderID** kutusuna `10249`ve ardından **sipariş ayrıntılarını**.  
  
     Bir ileti kutusu 10249 sırada dahil olduğu ürünleri listeler.  
  
     Tıklatın **Tamam** ileti kutusunu kapatın.  
  
3.  İçinde **girin CustomerID** kutusuna `ALFKI`ve ardından **siparişi geçmişi**.  
  
     ALFKI müşteri siparişi geçmişi listeleyen bir ileti kutusu görünür.  
  
     Tıklatın **Tamam** ileti kutusunu kapatın.  
  
4.  İçinde **girin OrderID** kutusuna `123`ve ardından **sipariş ayrıntılarını**.  
  
     "Sonuç yok." görüntüleyen bir ileti kutusu görünür  
  
     Tıklatın **Tamam** ileti kutusunu kapatın.  
  
5.  Üzerinde **hata ayıklama** menüsünde tıklatın **hata ayıklamayı durdurun**.  
  
     Hata ayıklama oturumu kapatır.  
  
6.  Denemeler bitirdikten, tıklayabilirsiniz **Projeyi Kapat** üzerinde **dosya** menüsünde ve istendiğinde projeyi kaydedin.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bazı değişiklikler yaparak bu proje geliştirebilirsiniz. Örneğin, liste kutusunda kullanılabilir saklı yordamları listeler, kullanıcı yürütmek için hangi yordamların Seç içerir. Ayrıca bir metin dosyasına raporları çıkış akış.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğrenme tarafından izlenecek yollar](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [Saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
