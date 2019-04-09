---
title: 'İzlenecek yol: İlişkilerde Sorgulama (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 52623b79492908a6c387715fef002d4b8927169c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184892"
---
# <a name="walkthrough-querying-across-relationships-c"></a>İzlenecek yol: İlişkilerde Sorgulama (C#)
Bu izlenecek yolda kullanımını gösteren [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ilişkilendirmeleri* veritabanında yabancı anahtar ilişkileri göstermek için.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual kullanılarak yazılmış olduğundan C# geliştirme ayarları.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Tamamlamış olmanız gerekir [izlenecek yol: Basit Nesne modeli ve sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Bu izlenecek yol, northwnd.mdf dosyasının varlığını c:\linqtest5 dahil olmak üzere bunu üzerine inşa edilmiştir.  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuzda üç ana görevden oluşur:  
  
-   Northwind örnek veritabanındaki Siparişler tablosunu temsil edecek bir varlık sınıfı ekleniyor.  
  
-   Ek açıklamalar ekleme `Customer` sınıfı arasındaki ilişkiyi geliştirmek için `Customer` ve `Order` sınıfları.  
  
-   Oluşturma ve alma test etmek için bir sorgu çalıştırma `Order` kullanarak bilgi `Customer` sınıfı.  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasındaki ilişkileri eşleme  
 Sonra `Customer` sınıf tanımını, oluşturma `Order` bildiren aşağıdaki kodu içeren varlık sınıf tanımı `Order.Customer` yabancı anahtar olarak ilişkili `Customer.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Sipariş varlık sınıfı eklemek için  
  
-   Sonra aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıf ek açıklama ekleme  
 Bu adımda, ek açıklama `Customer` ilişkisini belirtmek için sınıf `Order` sınıfı. (Herhangi bir yönde ilişkiyi tanımlamadan bağlantıyı oluşturmak yeterli olduğundan bu eklenmesi kesinlikle gerekli değildir. Ancak bu ek açıklama ekleme nesneleri herhangi bir yönde kolayca gidin.)  
  
#### <a name="to-annotate-the-customer-class"></a>Müşteri sınıf ek açıklama eklemek için  
  
-   İçine aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Oluşturma ve müşteri sipariş ilişki sorgu çalıştırma  
 Artık erişebilirsiniz `Order` doğrudan nesneleri `Customer` nesneleri veya ters sırada. Açık bir gerekmeyen *birleştirme* müşterilerle siparişler arasındaki.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Erişim için müşteri nesnesi kullanarak nesneleri  
  
1.  Değiştirme `Main` yazarak veya yönteme aşağıdaki kodu kopyalayıp yapıştırmak yöntemi:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
    > [!NOTE]
    >  Çıkış açıklama satırı yaparak konsol penceresinde SQL kodu çıkarabilirsiniz `db.Log = Console.Out;`.  
  
3.  Konsol penceresinde, hata ayıklamayı durdurmak için ENTER tuşuna basın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünüm oluşturma  
 Bir veritabanınız kesin türü belirtilmiş görünüm ile başlamak kolaydır. Kesin yazarak <xref:System.Data.Linq.DataContext> nesne çağrıları gerektirmeyen <xref:System.Data.Linq.DataContext.GetTable%2A>. Kesin olarak belirlenmiş kullandığınızda tüm sorgularınızdaki kesin türü belirtilmiş tabloları kullanabilir <xref:System.Data.Linq.DataContext> nesne.  
  
 Aşağıdaki adımlarda, oluşturacağınız `Customers` veritabanındaki Müşteriler tablosunu eşlendiği kesin türü belirtilmiş bir tablo olarak.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Kesin DataContext nesne yazmak için  
  
1.  Yukarıdaki aşağıdaki kodu ekleyin `Customer` sınıfının bildirimi.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  Değiştirme `Main` kesin olarak belirlenmiş yöntemini <xref:System.Data.Linq.DataContext> gibi:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi çıktısı şöyledir:  
  
     `ID=WHITC`  
  
4.  Konsol penceresinde, hata ayıklamayı durdurmak için ENTER tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki izlenecek ([izlenecek yol: Verileri düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) verileri işlemek nasıl gösterir. Bu izlenecek yol, iki izlenecek yollar zaten tamamladığınız bu dizide Kaydet gerektirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
