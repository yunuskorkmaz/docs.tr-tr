---
title: 'Nasıl yapılır: Varlık Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: e8c548ac632454d9c488ebd5f7b471f6759418fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155880"
---
# <a name="how-to-retrieve-entity-conflict-information"></a>Nasıl yapılır: Varlık Çakışma Bilgilerini Alma

<xref:System.Data.Linq.ObjectChangeConflict>Özel durumlar tarafından ortaya çıkan çakışmalar hakkında bilgi sağlamak için sınıfının nesnelerini kullanabilirsiniz <xref:System.Data.Linq.ChangeConflictException> . Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, birikmiş çakışmaların bir listesi üzerinden yinelenir.  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
