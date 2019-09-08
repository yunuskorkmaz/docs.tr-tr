---
title: 'İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: 3164656bb183e7773b098cab79d8fe5e0dc5de34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792149"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)
Bu izlenecek yol, veritabanındaki yabancı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] anahtar ilişkilerini temsil etmek için *ilişkilerin* kullanımını gösterir.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Gözden geçirmeyi tamamlamış [olmanız gerekir: Basit nesne modeli ve sorgu (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md). Bu izlenecek yol, c:\linqtestiçindeki kuzeydoğu. mdf dosyasının varlığı da dahil olmak üzere bunun üzerine oluşturulur.  
  
## <a name="overview"></a>Genel Bakış  
 Bu izlenecek yol üç ana görevden oluşur:  
  
- Örnek Northwind veritabanındaki Orders tablosunu temsil eden bir varlık sınıfı ekleme.  
  
- Ve`Customer` `Customer` sınıflarıarasındakiilişkiyiiyileştirmekiçinsınıfa`Order` ek açıklamalar eklemek.  
  
- Sınıfını kullanarak bilgi alma `Order` sürecini test etmek için bir sorgu oluşturma ve çalıştırma. `Customer`  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasında Ilişkileri eşleme  
 Sınıf tanımından sonra, bir yabancı anahtar `Order` `Customers.CustomerID`olarak ilişkili olduğunu `Orders.Customer` gösteren aşağıdaki kodu içeren varlık sınıfı tanımını oluşturun. `Customer`  
  
#### <a name="to-add-the-order-entity-class"></a>Order Entity sınıfını eklemek için  
  
- Aşağıdaki kodu `Customer` sınıftan sonra yazın veya yapıştırın:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıfına açıklama ekleme  
 Bu adımda, sınıfıyla ilişkisini `Customer` `Order` göstermek için sınıfına açıklama ekleyin. (Bu ekleme kesinlikle gerekli değildir, çünkü ilişkinin iki yönde tanımlanması bağlantıyı oluşturmak için yeterlidir. Ancak bu ek açıklamanın eklenmesi, nesneleri her iki yönde kolayca gezinmenizi sağlar.)  
  
#### <a name="to-annotate-the-customer-class"></a>Müşteri sınıfına açıklama eklemek için  
  
- Aşağıdaki kodu `Customer` sınıfına yazın veya yapıştırın:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Müşteri siparişi Ilişkisi genelinde sorgu oluşturma ve çalıştırma  
 Artık nesnelere doğrudan `Customer` nesnelerden `Order` veya ters sırada erişebilirsiniz. Müşteriler ve siparişler arasında açık bir *birleşime* gerek yoktur.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Müşteri nesnelerini kullanarak sıralama nesnelerine erişim  
  
1. Yöntemine aşağıdaki kodu yazarak veya yapıştırarak yöntemideğiştirin:`Sub Main`  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     İleti kutusunda iki ad görünür ve konsol penceresinde oluşturulan SQL kodu görüntülenir.  
  
3. Hata ayıklamayı durdurmak için ileti kutusunu kapatın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünümünü oluşturma  
 Veritabanınızın kesin türü belirtilmiş bir görünümüyle başlamak çok daha kolay. <xref:System.Data.Linq.DataContext> Nesneyi kesin olarak yazarak, ' a <xref:System.Data.Linq.DataContext.GetTable%2A>çağrı gerekmez. Kesin olarak belirlenmiş <xref:System.Data.Linq.DataContext> nesneyi kullandığınızda tüm sorgularınızda kesin türü belirtilmiş tabloları kullanabilirsiniz.  
  
 Aşağıdaki adımlarda, veritabanında müşteriler tablosuyla eşleşen türü `Customers` kesin belirlenmiş bir tablo olarak oluşturacaksınız.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>DataContext nesnesini kesin olarak yazmak için  
  
1. Aşağıdaki kodu `Customer` sınıf bildiriminin üstüne ekleyin.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. Kesin `Sub Main` olarak belirlenmiş <xref:System.Data.Linq.DataContext> türü kullanmak için aşağıdaki gibi değiştirin:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi çıkışı:  
  
     `ID=WHITC`  
  
4. Uygulamayı kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
5. Bu uygulamayı kaydetmek istiyorsanız **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki izlenecek yol ([izlenecek yol: Verileri düzenleme (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)), verilerin nasıl değiştirileceğini gösterir. Bu izlenecek yol, zaten tamamladığınız bu serideki iki izlenecek yolu kaydetmenizi gerektirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
