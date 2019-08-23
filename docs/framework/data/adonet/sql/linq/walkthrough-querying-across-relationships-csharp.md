---
title: 'İzlenecek yol: İlişkilerde Sorgulama (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a9e0583b14c07df2b1de23ba37fa88552a4c5c7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946954"
---
# <a name="walkthrough-querying-across-relationships-c"></a>İzlenecek yol: İlişkilerde Sorgulama (C#)
Bu izlenecek yol, veritabanındaki yabancı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] anahtar ilişkilerini temsil etmek için *ilişkilerin* kullanımını gösterir.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu izlenecek yol, Visual C# Development ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Gözden geçirmeyi tamamlamış [olmanız gerekir: Basit nesne modeli ve sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Bu izlenecek yol, c:\linqtest5' teki kuzeydoğu. mdf dosyasının varlığı da dahil olmak üzere bunun üzerine oluşturulur.  
  
## <a name="overview"></a>Genel Bakış  
 Bu izlenecek yol üç ana görevden oluşur:  
  
- Örnek Northwind veritabanındaki Orders tablosunu temsil eden bir varlık sınıfı ekleme.  
  
- Ve`Customer` `Customer` sınıflarıarasındakiilişkiyiiyileştirmekiçinsınıfa`Order` ek açıklamalar eklemek.  
  
- Sınıfını kullanarak bilgi edinmeyi `Order` test etmek için bir sorgu oluşturma ve çalıştırma. `Customer`  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasında Ilişkileri eşleme  
 Sınıf tanımından sonra, bir yabancı anahtar `Order` `Customer.CustomerID`olarak ilişkili olduğunu `Order.Customer` gösteren aşağıdaki kodu içeren varlık sınıfı tanımını oluşturun. `Customer`  
  
### <a name="to-add-the-order-entity-class"></a>Order Entity sınıfını eklemek için  
  
- Aşağıdaki kodu `Customer` sınıftan sonra yazın veya yapıştırın:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıfına açıklama ekleme  
 Bu adımda, sınıfıyla ilişkisini `Customer` `Order` göstermek için sınıfına açıklama ekleyin. (Bu ekleme kesinlikle gerekli değildir, çünkü ilişkinin iki yönde tanımlanması bağlantıyı oluşturmak için yeterlidir. Ancak bu ek açıklamanın eklenmesi, nesneleri her iki yönde kolayca gezinmenizi sağlar.)  
  
### <a name="to-annotate-the-customer-class"></a>Müşteri sınıfına açıklama eklemek için  
  
- Aşağıdaki kodu `Customer` sınıfına yazın veya yapıştırın:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Müşteri siparişi Ilişkisi genelinde sorgu oluşturma ve çalıştırma  
 Artık nesnelere doğrudan `Customer` nesnelerden `Order` veya ters sırada erişebilirsiniz. Müşteriler ve siparişler arasında açık bir *birleşime* gerek yoktur.  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a>Müşteri nesnelerini kullanarak sıralama nesnelerine erişim  
  
1. Yöntemine aşağıdaki kodu yazarak veya yapıştırarak yöntemideğiştirin:`Main`  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
    > [!NOTE]
    > Konsol penceresinde SQL kodunu, açıklama `db.Log = Console.Out;`ekleyerek ortadan kaldırabilirsiniz.  
  
3. Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünümünü oluşturma  
 Veritabanınızın kesin türü belirtilmiş bir görünümüyle başlamak çok daha kolay. <xref:System.Data.Linq.DataContext> Nesneyi kesin olarak yazarak, ' a <xref:System.Data.Linq.DataContext.GetTable%2A>çağrı gerekmez. Kesin olarak belirlenmiş <xref:System.Data.Linq.DataContext> nesneyi kullandığınızda tüm sorgularınızda kesin türü belirtilmiş tabloları kullanabilirsiniz.  
  
 Aşağıdaki adımlarda, veritabanında müşteriler tablosuyla eşleşen türü `Customers` kesin belirlenmiş bir tablo olarak oluşturacaksınız.  
  
### <a name="to-strongly-type-the-datacontext-object"></a>DataContext nesnesini kesin olarak yazmak için  
  
1. Aşağıdaki kodu `Customer` sınıf bildiriminin üstüne ekleyin.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. Yöntemi, `Main` türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> olarak kullanmak için aşağıdaki gibi değiştirin:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. Uygulamanızda hata ayıklamak için F5 tuşuna basın.  
  
     Konsol penceresi çıkışı:  
  
     `ID=WHITC`  
  
4. Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki izlenecek yol ([izlenecek yol: Verileri düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)), verilerin nasıl değiştirileceğini gösterir. Bu izlenecek yol, zaten tamamladığınız bu serideki iki izlenecek yolu kaydetmenizi gerektirmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
