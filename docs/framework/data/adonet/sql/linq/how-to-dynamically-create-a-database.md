---
title: "Nasıl yapılır: dinamik olarak bir veritabanı oluşturun"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5374c5a7954a8a31736e62c7f954e3fc5a1b937b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dynamically-create-a-database"></a>Nasıl yapılır: dinamik olarak bir veritabanı oluşturun
LINQ-SQL, nesne modeli ilişkisel bir veritabanına eşlenir. Eşleme ilişkisel veritabanı yapısını tanımlamak için öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanarak etkindir. Her iki senaryoda kullanarak veritabanını yeni bir örneğini oluşturabilirsiniz ilişkisel veritabanı hakkında yeterli bilgi yok <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemi.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, nesne modelinde kodlanmış bilgilerin kapsamını veritabanına yalnızca bir kopyasını oluşturur. Dosya ve nesne modeli öznitelikleri eşleme varolan bir veritabanını yapısı hakkında her şeyi kodlayın değil. Eşleme bilgileri değil kullanıcı tanımlı işlevler, saklı yordamlar, Tetikleyiciler içeriğini temsil veya denetim kısıtlamaları. Bu davranış, çeşitli veritabanları için yeterlidir.  
  
 Kullanabileceğiniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> senaryolarında özellikle Microsoft SQL Server 2008 gibi bilinen veri sağlayıcısı kullanılabilir olduğunda, herhangi bir sayıda yöntemi. Tipik senaryolar aşağıdakileri içerir:  
  
-   Otomatik olarak kendisini bir müşteri sistemde yükleyen bir uygulama oluşturmakta olduğunuz.  
  
-   Yerel bir veritabanı çevrimdışı durumunu kaydetmek için gereken bir istemci uygulaması oluşturuyorsanız.  
  
 Aynı zamanda <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .mdf dosyasını veya bağlantı dizenizi bağlı olarak bir katalog adı kullanarak SQL Server ile yöntemi. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullandığı bağlantı dizesi oluşturulacak veritabanının tanımlamanızı ve hangi sunucuda veritabanı oluşturulacak.  
  
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
 [Öznitelik tabanlı eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [Dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [SQL CLR türü eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Arka plan bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Sağlama ve veri değişiklikleri gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
