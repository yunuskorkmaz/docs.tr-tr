---
title: 'Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 92db9bdb209a542cc4fa269b35bfa98f8f20d2b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940080"
---
# <a name="how-to-dynamically-create-a-database"></a>Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma
LINQ to SQL, bir nesne modeli ilişkisel veritabanıyla eşlenir. Eşleme, ilişkisel veritabanının yapısını betimleyen öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanılarak etkinleştirilir. Her iki senaryoda da, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> yöntemini kullanarak veritabanının yeni bir örneğini oluşturabileceğiniz ilişkisel veritabanı hakkında yeterli bilgi vardır.  
  
 Yöntemi <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> , veritabanının bir çoğaltmasını yalnızca nesne modelinde kodlanan bilgilerin kapsamına oluşturur. Nesne modelinizdeki dosya ve öznitelikleri eşleme, var olan bir veritabanının yapısıyla ilgili her şeyi kodlayamayabilir. Eşleme bilgileri Kullanıcı tanımlı işlevlerin, saklı yordamların, tetikleyicilerin veya denetim kısıtlamalarının içeriğini temsil etmez. Bu davranış çeşitli veritabanları için yeterlidir.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> Yöntemi, özellikle de Microsoft SQL Server 2008 gibi bilinen bir veri sağlayıcısı varsa dilediğiniz sayıda senaryoda kullanabilirsiniz. Tipik senaryolar şunlardır:  
  
- Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama derleniyor.  
  
- Çevrimdışı durumunu kaydetmek için yerel bir veritabanına ihtiyacı olan bir istemci uygulaması derleniyor.  
  
 Ayrıca, bağlantı dizeniz <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> temelinde bir. mdf dosyası veya bir katalog adı kullanarak SQL Server yöntemini kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oluşturulacak veritabanını ve veritabanının oluşturulacağı sunucuyu tanımlamak için bağlantı dizesini kullanır.  
  
> [!NOTE]
> Mümkün olduğunda, bağlantı dizesinde parolaların gerekli olmaması için veritabanına bağlanmak üzere Windows tümleşik güvenliği kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, MyDVD 'Ler. mdf adlı yeni bir veritabanının nasıl oluşturulacağı hakkında bir örnek sağlar.  
  
 [!code-csharp[DLinqSubmittingChanges#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#5)]
 [!code-vb[DLinqSubmittingChanges#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki işlemleri yaparak bir veritabanı oluşturmak için nesne modelini kullanabilirsiniz:  
  
 [!code-csharp[DLinqSubmittingChanges#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#6)]
 [!code-vb[DLinqSubmittingChanges#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#6)]  
  
## <a name="example"></a>Örnek  
 Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama oluştururken, veritabanının zaten var olup olmadığını ve yeni bir tane oluşturmadan önce onu bırakıp bırakmaya bakın. Sınıfı, <xref:System.Data.Linq.DataContext.DatabaseExists%2A> bu işlemle ilgili <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> size yardımcı olmak için ve yöntemlerini sağlar. <xref:System.Data.Linq.DataContext>  
  
 Aşağıdaki örnek bu yaklaşımı uygulamak için bu yöntemlerin kullanılabileceği bir yolu göstermektedir:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [Dış Eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
- [SQL-CLR Tür Eşlemesi](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Arka Plan Bilgileri](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
