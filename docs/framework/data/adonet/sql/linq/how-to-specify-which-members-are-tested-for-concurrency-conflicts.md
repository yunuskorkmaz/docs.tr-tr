---
title: "Nasıl yapılır: hangi üyeleri eşzamanlılık çakışmalar için test edildiğini belirtin"
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
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 06a34c5d68e12793b5638bcb292dc44f7abae777
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Nasıl yapılır: hangi üyeleri eşzamanlılık çakışmalar için test edildiğini belirtin
Üç numaralandırmaları biri geçerli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> olan üyeleri güncelleştirmede dahil edileceğini belirlemek için öznitelik iyimser eşzamanlılık çakışma algılaması için denetler.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Tasarım zamanında eşlenen) özelliği, eşzamanlılık çalışma zamanı özellikleri ile birlikte kullanılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Hiç üye olarak tasarlanmış sürece özgün üye değerlerinin geçerli veritabanı durumu ile karşılaştırılır `IsVersion=true`. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Her zaman bu üye çakışmaları algılamak için kullanmak için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerine `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Hiçbir zaman bu üye çakışmaları algılamak için kullanın.  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerine `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Bu üye, yalnızca uygulama üyesinin değerini değiştiğinde çakışmaları algılamak için kullanmak için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğine <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerine `WhenChanged`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek belirleyen `HomePage` nesneleri hiçbir zaman test sırasında güncelleştirme denetler. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
