---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f68db5a5a0092fc4cf37746f2a4dc81e40ee4a9d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938684"
---
# <a name="how-to-turn-off-deferred-loading"></a>Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma
Giderek ertelenmiş yüklemeyi <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [ertelenmiş ve hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
> Ertelenmiş yükleme, nesne izleme kapalıyken etkili bir şekilde kapalıdır. Daha fazla bilgi için [nasıl yapılır: Bilgileri salt okuma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md)olarak alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ' i ' ye <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> `false`ayarlayarak ertelenmiş yüklemenin nasıl kapatılacağı gösterilmektedir.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
