---
title: 'Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fb7f23c4-4572-4c38-9898-a287807d070c
ms.openlocfilehash: 95073eed3e0534a74272ee426ac6e329954c85a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173490"
---
# <a name="how-to-dynamically-create-a-database"></a>Nasıl yapılır: Dinamik Olarak Veritabanı Oluşturma

LINQ to SQL, bir nesne modeli ilişkisel veritabanıyla eşlenir. Eşleme, ilişkisel veritabanının yapısını betimleyen öznitelik tabanlı eşleme veya bir dış eşleme dosyası kullanılarak etkinleştirilir. Her iki senaryoda da, yöntemini kullanarak veritabanının yeni bir örneğini oluşturabileceğiniz ilişkisel veritabanı hakkında yeterli bilgi vardır <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> .  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>Yöntemi, veritabanının bir çoğaltmasını yalnızca nesne modelinde kodlanan bilgilerin kapsamına oluşturur. Nesne modelinizdeki dosya ve öznitelikleri eşleme, var olan bir veritabanının yapısıyla ilgili her şeyi kodlayamayabilir. Eşleme bilgileri Kullanıcı tanımlı işlevlerin, saklı yordamların, tetikleyicilerin veya denetim kısıtlamalarının içeriğini temsil etmez. Bu davranış çeşitli veritabanları için yeterlidir.  
  
 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>Yöntemi, özellikle de Microsoft SQL Server 2008 gibi bilinen bir veri sağlayıcısı varsa dilediğiniz sayıda senaryoda kullanabilirsiniz. Tipik senaryolar şunlardır:  
  
- Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama derleniyor.  
  
- Çevrimdışı durumunu kaydetmek için yerel bir veritabanına ihtiyacı olan bir istemci uygulaması derleniyor.  
  
 Ayrıca, <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> bağlantı dizeniz temelinde bir. mdf dosyası veya bir katalog adı kullanarak SQL Server yöntemini kullanabilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturulacak veritabanını ve veritabanının oluşturulacağı sunucuyu tanımlamak için bağlantı dizesini kullanır.  
  
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

 Kendisini bir müşteri sistemine otomatik olarak yükleyen bir uygulama oluştururken, veritabanının zaten var olup olmadığını ve yeni bir tane oluşturmadan önce onu bırakıp bırakmaya bakın. <xref:System.Data.Linq.DataContext>Sınıfı, <xref:System.Data.Linq.DataContext.DatabaseExists%2A> <xref:System.Data.Linq.DataContext.DeleteDatabase%2A> Bu işlemle ilgili size yardımcı olmak için ve yöntemlerini sağlar.  
  
 Aşağıdaki örnek bu yaklaşımı uygulamak için bu yöntemlerin kullanılabileceği bir yolu göstermektedir:  
  
 [!code-csharp[DLinqSubmittingChanges#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#7)]
 [!code-vb[DLinqSubmittingChanges#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öznitelik Tabanlı Eşleme](attribute-based-mapping.md)
- [Dış Eşleme](external-mapping.md)
- [SQL-CLR Tür Eşlemesi](sql-clr-type-mapping.md)
- [Arka Plan Bilgileri](background-information.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
