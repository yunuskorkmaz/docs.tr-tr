---
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: fae1513e7a7ead98318d907b220b7510758c9ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037615"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Nasıl yapılır: Üye Çakışma Bilgilerini Alma
Kullanabileceğiniz <xref:System.Data.Linq.MemberChangeConflict> çakışan tek tek üyeleri hakkında bilgi almak için sınıf. Bu aynı bağlamda herhangi bir üyesi için özel işleme çakışmanın sağlayabilir. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod gezinir <xref:System.Data.Linq.ObjectChangeConflict> nesneleri. Her bir nesne için ardından gezinir <xref:System.Data.Linq.MemberChangeConflict> nesneleri.  
  
> [!NOTE]
>  Dahil <xref:System.Reflection> sağlamak amacıyla <xref:System.Data.Linq.MemberChangeConflict.Member%2A> bilgileri.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
