---
title: 'Nasıl yapılır: Geciktirilmiş yüklemeyi kapatma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b84b852-3cad-41a7-8077-149a70d50c8b
ms.openlocfilehash: 9878ec468333ba79d0171d0bf96235d48273e03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669542"
---
# <a name="how-to-turn-off-deferred-loading"></a>Nasıl yapılır: Geciktirilmiş yüklemeyi kapatma
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
