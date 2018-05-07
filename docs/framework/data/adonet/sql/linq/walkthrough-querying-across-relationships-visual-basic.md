---
title: 'İzlenecek yol: İlişkiler (Visual Basic) arasında sorgulama'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: aa98a823a5d97d86144ea2f76953e990cde8edec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>İzlenecek yol: İlişkiler (Visual Basic) arasında sorgulama
Bu kılavuzda kullanımını gösteren [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ilişkilendirmeleri* veritabanında yabancı anahtar ilişkileri temsil etmek için.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu kılavuz, Visual Basic geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Tamamlamış olmanız gerekir [izlenecek yol: Basit Nesne modeli ve sorgu (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md). Bu kılavuzda northwnd.mdf dosyasının varlığı, c:\linqtest dahil olmak üzere bir, inşa edilmiştir.  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuzda üç ana görevden oluşur:  
  
-   Örnek Northwind veritabanı Siparişler tablosunda temsil etmek için bir varlık sınıfı ekleniyor.  
  
-   Ek açıklamalar ekleme `Customer` arasındaki ilişkiyi geliştirmek için sınıf `Customer` ve `Order` sınıfları.  
  
-   Oluşturma ve alma işlemini test etmek için bir sorgu çalıştırılarak `Order` kullanarak bilgi `Customer` sınıfı.  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasında ilişkiler eşleme  
 Sonra `Customer` sınıf tanımının, oluşturma `Order` belirten aşağıdaki kodu içeren varlık sınıf tanımını `Orders.Customer` bir yabancı anahtar olarak ilişkili `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Sipariş varlık sınıfı eklemek için  
  
-   Sonra aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıf yorumlama  
 Bu adımda, ek açıklama `Customer` ilişkisini belirtmek için sınıf `Order` sınıfı. (Her iki yönde ilişkiyi tanımlamadan bağlantıyı oluşturmak için yeterli olduğundan bu eklenmesi kesinlikle gerekli değildir. Ancak bu ek açıklama ekleme her iki yönde nesneleri kolayca gidin.)  
  
#### <a name="to-annotate-the-customer-class"></a>Müşteri sınıf ek açıklama eklemek için  
  
-   Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Oluşturma ve bir sorgu müşteri siparişi ilişki çalıştırma  
 Artık erişebilirsiniz `Order` doğrudan nesneleri `Customer` nesneleri veya ters sırada. Açık bir gerekmez *birleştirme* müşteriler ve Siparişler arasında.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Müşteri nesneleri kullanılarak sipariş nesnelere erişmek için  
  
1.  Değiştirme `Sub Main` yazarak veya yöntemine aşağıdaki kodu yapıştırma yöntemi:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  Uygulamanızda hata ayıklama için F5 tuşuna basın.  
  
     İleti kutusu içinde iki adları görüntülenir ve konsol penceresine oluşturulan SQL kodu gösterir.  
  
3.  Hata ayıklamayı durdurmak için ileti kutusunu kapatın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünüm oluşturma  
 Veritabanınızın kesin türü belirtilmiş görünüm ile başlatmak daha kolaydır. Kesinlikle yazarak <xref:System.Data.Linq.DataContext> nesne çağrıları gerektirmeyen <xref:System.Data.Linq.DataContext.GetTable%2A>. Kesin türü belirtilmiş kullandığınızda, tüm sorgularda kesin türü belirtilmiş tabloları kullanabilir <xref:System.Data.Linq.DataContext> nesnesi.  
  
 Aşağıdaki adımlarda oluşturacağınız `Customers` veritabanı Müşteriler tablosunda eşlendiği kesin türü belirtilmiş bir tablo olarak.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Kesinlikle DataContext nesne türü için  
  
1.  Yukarıdaki aşağıdaki kodu ekleyin `Customer` sınıf bildiriminin.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  Değiştirme `Sub Main` kesin türü belirtilmiş kullanmak için <xref:System.Data.Linq.DataContext> gibi:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  Uygulamanızda hata ayıklama için F5 tuşuna basın.  
  
     Konsol penceresi çıktısı şöyledir:  
  
     `ID=WHITC`  
  
4.  Konsol penceresinde uygulamayı kapatmak için Enter tuşuna basın.  
  
5.  Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** bu uygulamayı kaydetmek istiyorsanız.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki Kılavuzu ([izlenecek yol: veri düzenleme (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) verileri işlemek gösterilmiştir. Bu izlenecek yol iki izlenecek yollar önceden tamamlamış bu dizide Kaydet gerektirmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
