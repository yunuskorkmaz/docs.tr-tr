---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: varlık çakışma bilgilerini alma'
title: 'Nasıl yapılır: Varlık Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: dde11a431ae977595b9845444e48705a4552fb23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767758"
---
# <a name="how-to-retrieve-entity-conflict-information"></a>Nasıl yapılır: Varlık Çakışma Bilgilerini Alma

<xref:System.Data.Linq.ObjectChangeConflict>Özel durumlar tarafından ortaya çıkan çakışmalar hakkında bilgi sağlamak için sınıfının nesnelerini kullanabilirsiniz <xref:System.Data.Linq.ChangeConflictException> . Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, birikmiş çakışmaların bir listesi üzerinden yinelenir.  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
