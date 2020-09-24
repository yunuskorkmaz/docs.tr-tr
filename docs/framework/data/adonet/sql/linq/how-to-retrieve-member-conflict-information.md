---
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 4848ef69914f0520d2365538faea7fa064c1a15c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155815"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Nasıl yapılır: Üye Çakışma Bilgilerini Alma

<xref:System.Data.Linq.MemberChangeConflict>Çakışan ayrı Üyeler hakkında bilgi almak için sınıfını kullanabilirsiniz. Aynı bağlamda, her üye için çakışmayı özel olarak işleme sağlayabilirsiniz. Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod nesneler boyunca yinelenir <xref:System.Data.Linq.ObjectChangeConflict> . Her nesne için, daha sonra nesneler boyunca yinelenir <xref:System.Data.Linq.MemberChangeConflict> .  
  
> [!NOTE]
> <xref:System.Reflection>Bilgi sağlamak için dahil edin <xref:System.Data.Linq.MemberChangeConflict.Member%2A> .  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
