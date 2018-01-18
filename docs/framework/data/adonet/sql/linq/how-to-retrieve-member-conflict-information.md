---
title: "Nasıl yapılır: üye çakışma bilgisi alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fab9111bb14b41244fab3bcd9c2ea0b0f91d72ce
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-retrieve-member-conflict-information"></a>Nasıl yapılır: üye çakışma bilgisi alma
Kullanabileceğiniz <xref:System.Data.Linq.MemberChangeConflict> çakışan tek tek üyeleri hakkında bilgi almak için sınıf. Aynı bu bağlamda herhangi bir üyesi için özel işleme çakışmanın sağlayabilir. Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod dolaşır <xref:System.Data.Linq.ObjectChangeConflict> nesneleri. Her bir nesne için ardından dolaşır <xref:System.Data.Linq.MemberChangeConflict> nesneleri.  
  
> [!NOTE]
>  Dahil <xref:System.Reflection> sağlamak amacıyla <xref:System.Data.Linq.MemberChangeConflict.Member%2A> bilgi.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
