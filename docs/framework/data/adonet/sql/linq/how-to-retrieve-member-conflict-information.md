---
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928626"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Nasıl yapılır: Üye Çakışma Bilgilerini Alma
Çakışan ayrı Üyeler hakkında <xref:System.Data.Linq.MemberChangeConflict> bilgi almak için sınıfını kullanabilirsiniz. Aynı bağlamda, her üye için çakışmayı özel olarak işleme sağlayabilirsiniz. Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)bakış.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod <xref:System.Data.Linq.ObjectChangeConflict> nesneler boyunca yinelenir. Her nesne için, daha sonra <xref:System.Data.Linq.MemberChangeConflict> nesneler boyunca yinelenir.  
  
> [!NOTE]
> Bilgi <xref:System.Reflection> sağlamak<xref:System.Data.Linq.MemberChangeConflict.Member%2A> için dahil edin.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
