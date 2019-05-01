---
title: 'Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: f82e347ecdb3c69cee3749855d1e4cb457a460f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033624"
---
# <a name="how-to-turn-off-deferred-loading"></a>Nasıl yapılır: Geciktirilmiş Yüklemeyi Kapatma
Geciktirilmiş yüklemeyi ayarlayarak kapatabilirsiniz <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`. Daha fazla bilgi için [Ertelenen hemen yükleme](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).  
  
> [!NOTE]
>  Ertelenen yükleme izleme nesnesi kapalı olduğunda dolaylı kapalıdır. Daha fazla bilgi için [nasıl yapılır: Salt okunur olarak bilgileri almak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-information-as-read-only.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geciktirilmiş yüklemeyi ayarlayarak kapatma işlemi gösterilmektedir <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> için `false`.  
  
 [!code-csharp[DLinqQuerying#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#3)]
 [!code-vb[DLinqQuerying#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
