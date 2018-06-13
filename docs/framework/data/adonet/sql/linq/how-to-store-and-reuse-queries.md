---
title: 'Nasıl yapılır: depolamak ve yeniden sorgular'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: a2d16cd5dce033c563783a0882f3de73194cf2d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360144"
---
# <a name="how-to-store-and-reuse-queries"></a>Nasıl yapılır: depolamak ve yeniden sorgular
Birçok kez yapısal olarak benzer sorguları yürüten bir uygulamanız varsa, genellikle bir kez sorgu derleme ve farklı parametrelerle birkaç kez yürütme tarafından performansını artırabilirsiniz. Örneğin, burada Şehir çalışma zamanında bir form kullanıcı tarafından belirtilen belirli bir şehir bulunan tüm müşterilerin almak bir uygulama olabilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kullanımını destekleyen *sorguları derlenmiş* bu amaç için.  
  
> [!NOTE]
>  Bu desen kullanımı, derlenmiş sorguları için en yaygın kullanımı temsil eder. Diğer yaklaşımlar mümkündür. Örneğin, derlenmiş sorgu tasarımcısı tarafından oluşturulan kodu genişleten bir parçalı sınıf statik üyeleri olarak depolanabilir.  
  
## <a name="example"></a>Örnek  
 Birçok senaryoda iş parçacığı sınırları boyunca sorguları yeniden isteyebilirsiniz. Statik değişkenler derlenmiş sorguları depolamak bu gibi durumlarda, özellikle etkili olur. Aşağıdaki kod örneğinde varsayar bir `Queries` depolamak için tasarlanan sınıfı sorguları derlenmiş ve kesin türü belirtilmiş temsil eden bir Northwind sınıf varsayar <xref:System.Data.Linq.DataContext>.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Örnek  
 Şu anda döndüren deposunda (statik değişkenler) sorgular olamaz bir *anonim tür*, genel bir bağımsız değişken olarak sağlamak için adı türü yok. Aşağıdaki örnek, sonucunu temsil eder ve daha genel bir bağımsız değişken olarak kullanan bir tür oluşturarak sorunu nasıl çalışabileceğini gösterir.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Data.Linq.CompiledQuery>  
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
