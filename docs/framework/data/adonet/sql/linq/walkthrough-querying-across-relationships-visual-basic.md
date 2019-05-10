---
title: 'İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 0852622811b5efb362937b3af37f2b9d81b2d1ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626434"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)
Bu izlenecek yolda kullanımını gösteren [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ilişkilendirmeleri* veritabanında yabancı anahtar ilişkileri göstermek için.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Tamamlamış olmanız gerekir [izlenecek yol: Basit Nesne modeli ve sorgu (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md). Bu izlenecek yol, northwnd.mdf dosyasının varlığını c:\linqtest dahil olmak üzere bunu üzerine inşa edilmiştir.  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuzda üç ana görevden oluşur:  
  
- Northwind örnek veritabanındaki Siparişler tablosunu temsil edecek bir varlık sınıfı ekleniyor.  
  
- Ek açıklamalar ekleme `Customer` sınıfı arasındaki ilişkiyi geliştirmek için `Customer` ve `Order` sınıfları.  
  
- Oluşturma ve alma işlemini test etmek için bir sorgu çalıştırma `Order` kullanarak bilgi `Customer` sınıfı.  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasındaki ilişkileri eşleme  
 Sonra `Customer` sınıf tanımını, oluşturma `Order` bildiren aşağıdaki kodu içeren varlık sınıf tanımı `Orders.Customer` yabancı anahtar olarak ilişkili `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Sipariş varlık sınıfı eklemek için  
  
- Sonra aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıf ek açıklama ekleme  
 Bu adımda, ek açıklama `Customer` ilişkisini belirtmek için sınıf `Order` sınıfı. (Herhangi bir yönde ilişkiyi tanımlamadan bağlantıyı oluşturmak yeterli olduğundan bu eklenmesi kesinlikle gerekli değildir. Ancak bu ek açıklama ekleme nesneleri herhangi bir yönde kolayca gidin.)  
  
#### <a name="to-annotate-the-customer-class"></a>Müşteri sınıf ek açıklama eklemek için  
  
- İçine aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Oluşturma ve müşteri sipariş ilişki sorgu çalıştırma  
 Artık erişebilirsiniz `Order` doğrudan nesneleri `Customer` nesneleri veya ters sırada. Açık bir gerekmeyen *birleştirme* müşterilerle siparişler arasındaki.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Erişim için müşteri nesnesi kullanarak nesneleri  
  
1. Değiştirme `Sub Main` yazarak veya yönteme aşağıdaki kodu kopyalayıp yapıştırmak yöntemi:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     İleti kutusunda iki ad görünür ve konsol penceresinde oluşturulan SQL kodu gösterir.  
  
3. Hata ayıklamayı durdurmak için ileti kutusunu kapatın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünüm oluşturma  
 Bir veritabanınız kesin türü belirtilmiş görünüm ile başlamak kolaydır. Kesin yazarak <xref:System.Data.Linq.DataContext> nesne çağrıları gerektirmeyen <xref:System.Data.Linq.DataContext.GetTable%2A>. Kesin olarak belirlenmiş kullandığınızda tüm sorgularınızdaki kesin türü belirtilmiş tabloları kullanabilir <xref:System.Data.Linq.DataContext> nesne.  
  
 Aşağıdaki adımlarda, oluşturacağınız `Customers` veritabanındaki Müşteriler tablosunu eşlendiği kesin türü belirtilmiş bir tablo olarak.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Kesin DataContext nesne yazmak için  
  
1. Yukarıdaki aşağıdaki kodu ekleyin `Customer` sınıfının bildirimi.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. Değiştirme `Sub Main` kesin olarak belirlenmiş kullanılacak <xref:System.Data.Linq.DataContext> gibi:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi çıktısı şöyledir:  
  
     `ID=WHITC`  
  
4. Konsol penceresinde uygulamayı kapatmak için Enter tuşuna basın.  
  
5. Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** bu uygulamayı kaydetmek istiyorsanız.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki izlenecek ([izlenecek yol: Verileri düzenleme (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) verileri işlemek nasıl gösterir. Bu izlenecek yol, iki izlenecek yollar zaten tamamladığınız bu dizide Kaydet gerektirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
