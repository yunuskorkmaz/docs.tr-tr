---
title: 'Nasıl yapılır: Üye çakışma bilgilerini alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 478781e6c8ee31ebf6f5edd0e243a81d9e0524f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669568"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Nasıl yapılır: Üye çakışma bilgilerini alma
Kullanabileceğiniz <xref:System.Data.Linq.MemberChangeConflict> çakışan tek tek üyeleri hakkında bilgi almak için sınıf. Bu aynı bağlamda herhangi bir üyesi için özel işleme çakışmanın sağlayabilir. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod gezinir <xref:System.Data.Linq.ObjectChangeConflict> nesneleri. Her bir nesne için ardından gezinir <xref:System.Data.Linq.MemberChangeConflict> nesneleri.  
  
> [!NOTE]
>  Dahil <xref:System.Reflection> sağlamak amacıyla <xref:System.Data.Linq.MemberChangeConflict.Member%2A> bilgileri.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
