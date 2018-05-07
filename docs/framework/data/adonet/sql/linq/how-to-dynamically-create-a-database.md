---
title: 'Nasıl yapılır: dinamik olarak bir veritabanı oluşturun'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 122eb705838da00fedd77a01a5d8c4bd3b5f774e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dynamically-create-a-database"></a>Nasıl yapılır: dinamik olarak bir veritabanı oluşturun
LINQ-SQL, nesne modeli ilişkisel bir veritabanına eşlenir. Eşleme ilişkisel veritabanı yapısını tanımlamak için öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanarak etkindir. Her iki senaryoda kullanarak veritabanını yeni bir örneğini oluşturabilirsiniz ilişkisel veritabanı hakkında yeterli bilgi yok <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, nesne modelinde kodlanmış bilgilerin kapsamını veritabanına yalnızca bir kopyasını oluşturur. Dosya ve nesne modeli öznitelikleri eşleme varolan bir veritabanını yapısı hakkında her şeyi kodlayın değil. Eşleme bilgileri değil kullanıcı tanımlı işlevler, saklı yordamlar, Tetikleyiciler içeriğini temsil veya denetim kısıtlamaları. Bu davranış, çeşitli veritabanları için yeterlidir.  
  
 Kullanabileceğiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> senaryolarında özellikle Microsoft SQL Server 2008 gibi bilinen veri sağlayıcısı kullanılabilir olduğunda, herhangi bir sayıda yöntemi. Tipik senaryolar aşağıdakileri içerir:  
  
-   Otomatik olarak kendisini bir müşteri sistemde yükleyen bir uygulama oluşturmakta olduğunuz.  
  
-   Yerel bir veritabanı çevrimdışı durumunu kaydetmek için gereken bir istemci uygulaması oluşturuyorsanız.  
  
 Aynı zamanda <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .mdf dosyasını veya bağlantı dizenizi bağlı olarak bir katalog adı kullanarak SQL Server ile yöntemi. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullandığı bağlantı dizesi oluşturulacak veritabanının tanımlamanızı ve hangi sunucuda veritabanı oluşturulacak.  
  
> [!NOTE]
>  Mümkün olduğunda, böylece parolaları bağlantı dizesinde gerekli değildir veritabanına bağlanmak için Windows tümleşik güvenliğini kullan.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod MyDVDs.mdf adlı yeni bir veritabanı oluşturmak nasıl bir örnek sağlar.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdakileri yaparak bir veritabanı oluşturmak için nesne modeli kullanabilirsiniz:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Otomatik olarak uygulama oluşturma kendisini bir müşteri sistemde yüklendiğinde, veritabanı zaten var ve yenisini oluşturmadan önce bırakma bakın. <xref:System.Data.Linq.DataContext> SAX <xref:System.Data.Linq.DataContext.DatabaseExists%2A> ve <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> bu işlemde size yardımcı olacak yöntemler.  
  
 Aşağıdaki örnek, bu yöntemleri bu yaklaşımı uygulamak için kullanılan bir yolu gösterir:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
