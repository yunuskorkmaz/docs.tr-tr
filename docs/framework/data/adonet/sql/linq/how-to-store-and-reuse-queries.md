---
title: 'Nasıl yapılır: Sorguları Depolama ve Yeniden Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a012bd79-1809-45e3-adea-0229532396cc
ms.openlocfilehash: f8400b214bc9ba3a28eeec05f6171953b42bc6f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938738"
---
# <a name="how-to-store-and-reuse-queries"></a>Nasıl yapılır: Sorguları Depolama ve Yeniden Kullanma
Yapısal olarak benzer sorguları birçok kez yürüten bir uygulamanız varsa, genellikle sorguyu bir kez derleyerek ve farklı parametrelerle birkaç kez yürüterek performansı artırabilirsiniz. Örneğin, bir uygulamanın belirli bir şehirde yer alan tüm müşterileri alması gerekebilir. burada şehir, bir formdaki Kullanıcı tarafından çalışma zamanında belirtilir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu amaçla *derlenen sorguların* kullanımını destekler.  
  
> [!NOTE]
> Bu kullanım stili, derlenmiş sorgular için en yaygın kullanımı temsil eder. Diğer yaklaşımlar mümkündür. Örneğin, derlenmiş sorgular, tasarımcı tarafından oluşturulan kodu genişleten kısmi bir sınıfta statik üye olarak depolanabilir.  
  
## <a name="example"></a>Örnek  
 Birçok senaryoda sorguları iş parçacığı sınırları genelinde yeniden kullanmak isteyebilirsiniz. Bu gibi durumlarda, derlenmiş sorguları statik değişkenlerde depolamak özellikle etkilidir. Aşağıdaki kod örneği, derlenmiş sorguları `Queries` depolamak için tasarlanan bir sınıfı varsayar ve kesin bir şekilde yazılmış <xref:System.Data.Linq.DataContext>bir Northwind sınıfının olduğunu varsayar.  
  
 [!code-csharp[DLinqQuerying#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#6)]
 [!code-vb[DLinqQuerying#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#6)]  
  
 [!code-csharp[DLinqQuerying#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#7)]
 [!code-vb[DLinqQuerying#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#7)]  
  
## <a name="example"></a>Örnek  
 Şu anda, türün genel bir bağımsız değişken olarak sağlanacak bir adı olmadığından, *anonim bir tür*döndüren sorgularda (statik değişkenler içinde) depolama alanı oluşturamazsınız. Aşağıdaki örnek, sonucu temsil eden bir tür oluşturarak ve sonra genel bir bağımsız değişken olarak kullanarak soruna geçici bir çözüm nasıl kullanabileceğinizi gösterir.  
  
 [!code-csharp[DLinqQuerying#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#8)]
 [!code-vb[DLinqQuerying#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Data.Linq.CompiledQuery>
- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
