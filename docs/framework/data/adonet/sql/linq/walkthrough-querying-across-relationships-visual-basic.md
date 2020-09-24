---
title: 'İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: ce5323b4ecd7bd0c4337d4632eff209e4d0ebd42
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163992"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>İzlenecek yol: İlişkilerde Sorgulama (Visual Basic)

Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanındaki yabancı anahtar ilişkilerini temsil etmek için *ilişkilerin* kullanımını gösterir.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Ön koşullar  

 Gözden geçirmeyi tamamlamış olmanız gerekir [: basit nesne modeli ve sorgu (Visual Basic)](walkthrough-simple-object-model-and-query-visual-basic.md). Bu izlenecek yol, c:\linqtestiçindeki kuzeydoğu. mdf dosyasının varlığı da dahil olmak üzere bunun üzerine oluşturulur.  
  
## <a name="overview"></a>Genel Bakış  

 Bu izlenecek yol üç ana görevden oluşur:  
  
- Örnek Northwind veritabanındaki Orders tablosunu temsil eden bir varlık sınıfı ekleme.  
  
- `Customer`Ve sınıfları arasındaki ilişkiyi iyileştirmek için sınıfa ek açıklamalar eklemek `Customer` `Order` .  
  
- Sınıfını kullanarak bilgi alma sürecini test etmek için bir sorgu oluşturma ve çalıştırma `Order` `Customer` .  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasında Ilişkileri eşleme  

 `Customer`Sınıf tanımından sonra, `Order` `Orders.Customer` bir yabancı anahtar olarak ilişkili olduğunu gösteren aşağıdaki kodu içeren varlık sınıfı tanımını oluşturun `Customers.CustomerID` .  
  
#### <a name="to-add-the-order-entity-class"></a>Order Entity sınıfını eklemek için  
  
- Aşağıdaki kodu sınıftan sonra yazın veya yapıştırın `Customer` :  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıfına açıklama ekleme  

 Bu adımda, sınıfıyla `Customer` ilişkisini göstermek için sınıfına açıklama ekleyin `Order` . (Bu ekleme kesinlikle gerekli değildir, çünkü ilişkinin iki yönde tanımlanması bağlantıyı oluşturmak için yeterlidir. Ancak bu ek açıklamanın eklenmesi, nesneleri her iki yönde kolayca gezinmenizi sağlar.)  
  
#### <a name="to-annotate-the-customer-class"></a>Müşteri sınıfına açıklama eklemek için  
  
- Aşağıdaki kodu sınıfına yazın veya yapıştırın `Customer` :  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Müşteri siparişi Ilişkisi genelinde sorgu oluşturma ve çalıştırma  

 Artık `Order` nesnelere doğrudan `Customer` nesnelerden veya ters sırada erişebilirsiniz. Müşteriler ve siparişler arasında açık bir *birleşime* gerek yoktur.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Müşteri nesnelerini kullanarak sıralama nesnelerine erişim  
  
1. Yöntemine `Sub Main` aşağıdaki kodu yazarak veya yapıştırarak yöntemi değiştirin:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     İleti kutusunda iki ad görünür ve konsol penceresinde oluşturulan SQL kodu görüntülenir.  
  
3. Hata ayıklamayı durdurmak için ileti kutusunu kapatın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünümünü oluşturma  

 Veritabanınızın kesin türü belirtilmiş bir görünümüyle başlamak çok daha kolay. Nesneyi kesin olarak yazarak <xref:System.Data.Linq.DataContext> , ' a çağrı gerekmez <xref:System.Data.Linq.DataContext.GetTable%2A> . Kesin olarak belirlenmiş nesneyi kullandığınızda tüm sorgularınızda kesin türü belirtilmiş tabloları kullanabilirsiniz <xref:System.Data.Linq.DataContext> .  
  
 Aşağıdaki adımlarda, `Customers` veritabanında müşteriler tablosuyla eşleşen türü kesin belirlenmiş bir tablo olarak oluşturacaksınız.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>DataContext nesnesini kesin olarak yazmak için  
  
1. Aşağıdaki kodu sınıf bildiriminin üstüne ekleyin `Customer` .  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. `Sub Main`Kesin olarak belirlenmiş türü kullanmak için <xref:System.Data.Linq.DataContext> aşağıdaki gibi değiştirin:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi çıkışı:  
  
     `ID=WHITC`  
  
4. Uygulamayı kapatmak için konsol penceresinde ENTER tuşuna basın.  
  
5. Bu uygulamayı kaydetmek istiyorsanız **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  

 Sonraki izlenecek yol ([Izlenecek yol: verileri düzenleme (Visual Basic)](walkthrough-manipulating-data-visual-basic.md)), verilerin nasıl değiştirileceğini gösterir. Bu izlenecek yol, zaten tamamladığınız bu serideki iki izlenecek yolu kaydetmenizi gerektirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](learning-by-walkthroughs.md)
