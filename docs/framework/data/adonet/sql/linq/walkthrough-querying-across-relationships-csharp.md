---
title: "İzlenecek yol: Sorgulama ilişkiler arasında (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 61586b8d556a9edccace25b75ceb2696ec675dd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-querying-across-relationships-c"></a>İzlenecek yol: Sorgulama ilişkiler arasında (C#)
Bu kılavuzda kullanımını gösteren [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ilişkilendirmeleri* veritabanında yabancı anahtar ilişkileri temsil etmek için.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Bu kılavuz, Visual C# geliştirme ayarları kullanılarak yazılmıştır.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Tamamlamış olmanız gerekir [izlenecek yol: Basit Nesne modeli ve sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Bu kılavuzda northwnd.mdf dosyasının varlığı, c:\linqtest5 dahil olmak üzere bir, inşa edilmiştir.  
  
## <a name="overview"></a>Genel Bakış  
 Bu kılavuzda üç ana görevden oluşur:  
  
-   Örnek Northwind veritabanı Siparişler tablosunda temsil etmek için bir varlık sınıfı ekleniyor.  
  
-   Ek açıklamalar ekleme `Customer` arasındaki ilişkiyi geliştirmek için sınıf `Customer` ve `Order` sınıfları.  
  
-   Oluşturma ve alma test etmek için bir sorgu çalıştırılarak `Order` kullanarak bilgi `Customer` sınıfı.  
  
## <a name="mapping-relationships-across-tables"></a>Tablolar arasında ilişkiler eşleme  
 Sonra `Customer` sınıf tanımının, oluşturma `Order` belirten aşağıdaki kodu içeren varlık sınıf tanımını `Order.Customer` bir yabancı anahtar olarak ilişkili `Customer.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Sipariş varlık sınıfı eklemek için  
  
-   Sonra aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Müşteri sınıf yorumlama  
 Bu adımda, ek açıklama `Customer` ilişkisini belirtmek için sınıf `Order` sınıfı. (Her iki yönde ilişkiyi tanımlamadan bağlantıyı oluşturmak için yeterli olduğundan bu eklenmesi kesinlikle gerekli değildir. Ancak bu ek açıklama ekleme her iki yönde nesneleri kolayca gidin.)  
  
#### <a name="to-annotate-the-customer-class"></a>Müşteri sınıf ek açıklama eklemek için  
  
-   Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Oluşturma ve bir sorgu müşteri siparişi ilişki çalıştırma  
 Artık erişebilirsiniz `Order` doğrudan nesneleri `Customer` nesneleri veya ters sırada. Açık bir gerekmez *birleştirme* müşteriler ve Siparişler arasında.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Müşteri nesneleri kullanılarak sipariş nesnelere erişmek için  
  
1.  Değiştirme `Main` yazarak veya yöntemine aşağıdaki kodu yapıştırma yöntemi:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  Uygulamanızda hata ayıklama için F5 tuşuna basın.  
  
    > [!NOTE]
    >  Konsol penceresinde SQL kodunu çıkışı yorum tarafından çıkarabilirsiniz `db.Log = Console.Out;`.  
  
3.  Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Veritabanınızın kesin türü belirtilmiş bir görünüm oluşturma  
 Veritabanınızın kesin türü belirtilmiş görünüm ile başlatmak daha kolaydır. Kesinlikle yazarak <xref:System.Data.Linq.DataContext> nesne çağrıları gerektirmeyen <xref:System.Data.Linq.DataContext.GetTable%2A>. Kesin türü belirtilmiş kullandığınızda, tüm sorgularda kesin türü belirtilmiş tabloları kullanabilir <xref:System.Data.Linq.DataContext> nesnesi.  
  
 Aşağıdaki adımlarda oluşturacağınız `Customers` veritabanı Müşteriler tablosunda eşlendiği kesin türü belirtilmiş bir tablo olarak.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Kesinlikle DataContext nesne türü için  
  
1.  Yukarıdaki aşağıdaki kodu ekleyin `Customer` sınıf bildiriminin.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  Değiştirme `Main` kesin türü belirtilmiş kullanılacak yöntemi <xref:System.Data.Linq.DataContext> gibi:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  Uygulamanızda hata ayıklama için F5 tuşuna basın.  
  
     Konsol penceresi çıktısı şöyledir:  
  
     `ID=WHITC`  
  
4.  Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Sonraki Kılavuzu ([izlenecek yol: veri düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) verileri işlemek gösterilmiştir. Bu izlenecek yol iki izlenecek yollar önceden tamamlamış bu dizide Kaydet gerektirmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek Yollarla Öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
