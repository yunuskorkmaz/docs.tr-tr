---
title: 'İzlenecek yol: Verileri Düzenleme (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: dbf18273e69ff0977f5d16ff179b8659865ef696
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164057"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a>İzlenecek yol: Verileri Düzenleme (Visual Basic)

Bu izlenecek yol [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bir veritabanındaki verileri eklemek, değiştirmek ve silmek için temel uçtan uca bir senaryo sağlar. Müşteri eklemek, bir müşterinin adını değiştirmek ve bir siparişi silmek için örnek Northwind veritabanının bir kopyasını kullanacaksınız.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Ön koşullar  

 Bu izlenecek yol aşağıdakileri gerektirir:  
  
- Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest2") kullanır. Yönergeye başlamadan önce bu klasörü oluşturun.  
  
- Northwind örnek veritabanı.  
  
     Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz. Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md). Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest2 klasörüne kopyalayın.  
  
- Northwind veritabanından oluşturulan Visual Basic kod dosyası.  
  
     Bu dosyayı Nesne İlişkisel Tasarımcısı ya da SQLMetal aracını kullanarak oluşturabilirsiniz. Bu izlenecek yol, aşağıdaki komut satırı ile SQLMetal Aracı kullanılarak yazılmıştır:  
  
     **SqlMetal/Code: "c:\linqtest2\northwind.exe"/Language: vb "C:\linqtest2\kuzeydoğu WND.exe"/plurleştir**  
  
     Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).  
  
## <a name="overview"></a>Genel Bakış  

 Bu izlenecek yol altı ana görevden oluşur:  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözüm oluşturma.  
  
- Veritabanı kod dosyası projeye ekleniyor.  
  
- Yeni bir müşteri nesnesi oluşturuluyor.  
  
- Müşterinin kişi adını değiştirme.  
  
- Bir siparişi silme.  
  
- Bu değişiklikler Northwind veritabanına gönderiliyor.  
  
## <a name="creating-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturma  

 Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
#### <a name="to-create-a-linq-to-sql-solution"></a>LINQ to SQL çözümü oluşturmak için  
  
1. Visual Studio **Dosya** menüsünde **Yeni proje**' ye tıklayın.  
  
2. **Yeni proje** Iletişim kutusundaki **proje türleri** bölmesinde **Visual Basic**' ye tıklayın.  
  
3. **Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.  
  
4. **Ad** kutusuna **Linqdatalationtionapp**yazın.  
  
5. **Tamam**'a tıklayın.  
  
## <a name="adding-linq-references-and-directives"></a>LINQ başvuruları ve yönergeleri ekleme  

 Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır. `System.Data.Linq`Projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **tüm dosyaları göster** ' e tıklayın ve **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.  
  
#### <a name="to-add-systemdatalinq"></a>System. Data. LINQ eklemek için  
  
1. **Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.  
  
2. **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.  
  
     Derleme projeye eklenir.  
  
3. Kod Düzenleyicisi 'nde, aşağıdaki yönergeleri **Module1**öğesine ekleyin:  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a>Northwind kod dosyasını projeye ekleme  

 Bu adımlarda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SQLMetal aracını kullandığınız varsayılır. Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a>Projeye Northwind kod dosyasını eklemek için  
  
1. **Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.  
  
2. **Varolan öğe Ekle** iletişim kutusunda c:\linqtest2\northwind.exe konumuna gidin ve ardından **Ekle**' ye tıklayın.  
  
     Northwind. vb dosyası projeye eklenir.  
  
## <a name="setting-up-the-database-connection"></a>Veritabanı bağlantısını ayarlama  

 İlk olarak, Veritabanı bağlantınızı test edin. Özellikle, Kuzey WND adlı veritabanının adının bir i karakteri olmadığını unutmayın. Sonraki adımlarda hata oluşturursanız Northwind. vb dosyasını gözden geçirerek Northwind kısmi sınıfının nasıl yazıldığını belirleyebilirsiniz.  
  
#### <a name="to-set-up-and-test-the-database-connection"></a>Veritabanı bağlantısını ayarlama ve test etme  
  
1. Aşağıdaki kodu yazın veya içine yapıştırın `Sub Main` :  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. Bu noktada uygulamayı test etmek için F5 tuşuna basın.  
  
     Bir **konsol** penceresi açılır.  
  
     **Konsol** penceresinde ENTER tuşuna basarak veya Visual Studio **hata ayıklama** menüsünde **hata ayıklamayı Durdur** ' u tıklatarak uygulamayı kapatın.  
  
## <a name="creating-a-new-entity"></a>Yeni varlık oluşturma  

 Yeni varlık oluşturma basittir. `Customer`Anahtar sözcüğünü kullanarak nesneler (gibi) oluşturabilirsiniz `New` .  
  
 Bu ve aşağıdaki bölümlerde yalnızca yerel önbellekte değişiklik yapmakta olursunuz. Bu izlenecek yolun sonuna doğru çağrı yapana kadar veritabanına hiçbir değişiklik gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .  
  
#### <a name="to-add-a-new-customer-entity-object"></a>Yeni bir müşteri varlık nesnesi eklemek için  
  
1. `Customer`' Den önce aşağıdaki kodu ekleyerek yeni bir oluşturun `Console.ReadLine` `Sub Main` :  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. Çözümde hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresinde gösterilen sonuçlar şunlardır:  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     Yeni satırın sonuçlarda görünmediğini unutmayın. Yeni veriler henüz veritabanına gönderilmedi.  
  
3. Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın.  
  
## <a name="updating-an-entity"></a>Bir varlığı güncelleştirme  

 Aşağıdaki adımlarda, bir `Customer` nesnesi alacak ve özelliklerinden birini değiştirecaksınız.  
  
#### <a name="to-change-the-name-of-a-customer"></a>Müşterinin adını değiştirmek için  
  
- Aşağıdaki kodu yukarıya ekleyin `Console.ReadLine()` :  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a>Bir varlığı silme  

 Aynı müşteri nesnesini kullanarak, ilk siparişi silebilirsiniz.  
  
 Aşağıdaki kod, satırlar arasındaki ilişkilerin nasıl oluşturulduğunu ve veritabanından bir satırın nasıl silineceğini gösterir.  
  
#### <a name="to-delete-a-row"></a>Bir satırı silmek için  
  
- Aşağıdaki kodu hemen yukarıya ekleyin `Console.ReadLine()` :  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a>Değişiklikleri veritabanına gönderme  

 Nesneleri oluşturmak, güncelleştirmek ve silmek için gereken son adım aslında değişiklikleri veritabanına göndermeleridir. Bu adım olmadan yaptığınız değişiklikler yalnızca yereldir ve sorgu sonuçlarında görünmez.  
  
#### <a name="to-submit-changes-to-the-database"></a>Değişiklikleri veritabanına göndermek için  
  
1. Aşağıdaki kodu hemen yukarıya ekleyin `Console.ReadLine` :  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. `SubmitChanges`Değişiklikleri gönderme etkilerine ilişkin önceki ve sonraki etkileri göstermek için aşağıdaki kodu (sonra) ekleyin:  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. Çözümde hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi şu şekilde görünür:  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın.  
  
> [!NOTE]
> Değişiklikleri göndererek yeni müşteriyi ekledikten sonra, aynı müşteriyi olduğu gibi yeniden ekleyemediği için bu çözümü olduğu gibi yeniden yürütemezsiniz. Çözümü yeniden yürütmek için, eklenecek müşteri KIMLIĞI değerini değiştirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
