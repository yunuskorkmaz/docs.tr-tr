---
title: 'Nasıl yapılır: Sorguları Depolama ve Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: 1aac20c3f9c421d353938a83b9e321d35abd244e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084202"
---
# <a name="how-to-store-and-reuse-queries"></a>Nasıl yapılır: Sorguları Depolama ve Yeniden Kullanma
Birden çok kez yapısal olarak benzer sorguları yürüten bir uygulamanız varsa, genellikle bir kez sorgu derleyerek ve birkaç kez farklı parametrelerle yürütme performansı artırabilirsiniz. Örneğin, bir uygulamanın nerede Şehir çalışma zamanında bir forma kullanıcı tarafından belirtilen, belirli bir şehirdeki olan tüm müşterileri alma gerekebilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler *derlenmiş sorgular* bu amaç için.  
  
> [!NOTE]
>  Bu düzen kullanım derlenmiş sorgular için en yaygın kullanımı temsil eder. Diğer yaklaşımlar mümkündür. Örneğin, derlenmiş sorgular, tasarımcı tarafından oluşturulan kodu genişleten bir parçalı sınıf statik üyeleri olarak depolanabilir.  
  
## <a name="example"></a>Örnek  
 Pek çok senaryoda sorguları, iş parçacığı sınırları arasında yeniden isteyebilirsiniz. Statik değişkenler derlenmiş sorgular depolama gibi durumlarda, özellikle etkili olur. Aşağıdaki kod örneği varsayar bir `Queries` depolamak üzere tasarlanmış sınıf derlenmiş sorgular ve türü kesin belirlenmiş temsil eden bir Northwind sınıf varsayar <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Örnek  
 Döndüren sorgular deposunda (statik değişkenler) şu anda yapamazsınız bir *anonim tür*, genel bir bağımsız değişken olarak sağlamak için adı türü yok. Aşağıdaki örnek, sonucu temsil eder ve ardından genel bir bağımsız değişken olarak kullanan bir tür oluşturarak bu sorunu geçici olarak nasıl çalışabileceğini gösterir.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.Linq.CompiledQuery>
- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
