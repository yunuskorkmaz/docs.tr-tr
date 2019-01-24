---
title: 'Nasıl yapılır: Dinamik olarak veritabanı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: a73efb334fddc7e0bbfbaca53f0d5026105dd22c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597040"
---
# <a name="how-to-dynamically-create-a-database"></a>Nasıl yapılır: Dinamik olarak veritabanı oluşturma
LINQ to SQL nesne modeli, bir ilişkisel veritabanına eşlenir. İlişkisel veritabanının yapısını tanımlamak için öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanarak eşleme etkindir. Her iki senaryoda veritabanı kullanarak yeni bir örneğini oluşturabilirsiniz ilişkisel veritabanı hakkında yeterli bilgi yok <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, nesne modelinde kodlanmış bilgilerin kapsamını veritabanına yalnızca bir kopyasını oluşturur. Dosyaları ve öznitelikler, nesne modelinden var olan bir veritabanının yapısı hakkında her şeyi kodlamamayı. Eşleme bilgileri değil kullanıcı tarafından tanımlanan İşlevler, saklı yordamlar, Tetikleyiciler içeriğini temsil veya denetim kısıtlamaları. Bu davranış, çeşitli veritabanları için yeterli olur.  
  
 Kullanabileceğiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> senaryoları, özellikle de Microsoft SQL Server 2008 gibi bir bilinen veri sağlayıcısı kullanılabilir olduğunda herhangi bir sayıda yöntem. Tipik senaryolar aşağıdakileri içerir:  
  
-   Otomatik olarak kendisini bir müşteri sisteminde yükleyen bir uygulama oluşturuyorsanız.  
  
-   Yerel bir veritabanı çevrimdışı durumunu kaydetmek için gereken bir istemci uygulaması oluşturuyorsunuz.  
  
 Ayrıca <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .mdf dosyası veya bağlantı dizenizi bağlı olarak bir katalog adı'nı kullanarak SQL Server ile yöntemi. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullandığı bağlantı dizesi oluşturulacak veritabanının tanımlamak için ve hangi sunucuda veritabanı oluşturulacak.  
  
> [!NOTE]
>  Mümkün olduğunda, böylece bağlantı dizesinde parola gerekli değildir veritabanına bağlanmak için Windows tümleşik güvenliği kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod MyDVDs.mdf adlı yeni bir veritabanı oluşturmak nasıl bir örnek sağlar.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdakileri yaparak bir veritabanı oluşturmak için nesne modeli kullanabilirsiniz:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Otomatik olarak uygulama oluşturma kendisi bir müşteri sistemine yükler veritabanı zaten var ve yeni bir tane oluşturmadan önce bırak görürsünüz. <xref:System.Data.Linq.DataContext> Sağlar sınıfını <xref:System.Data.Linq.DataContext.DatabaseExists%2A> ve <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> bu işlemde size yardımcı olacak yöntemler.  
  
 Aşağıdaki örnek bu yaklaşımı uygulamak için bu yöntemleri kullanılabilir yollarından biri gösterilmektedir:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
