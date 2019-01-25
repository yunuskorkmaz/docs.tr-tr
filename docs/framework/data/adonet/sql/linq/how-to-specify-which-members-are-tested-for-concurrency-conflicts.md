---
title: 'Nasıl yapılır: Üyeleri eşzamanlılık çakışmaları için test edildiğini belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: 1007cbc0961d01574fd60ec50eb63406ec7adef9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724586"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Nasıl yapılır: Üyeleri eşzamanlılık çakışmaları için test edildiğini belirtme
Üç numaralandırmalar için biriyle karşılaşmış [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliği bir <xref:System.Data.Linq.Mapping.ColumnAttribute> hangi üyelerin güncelleştirmede dahil edileceğini belirtmek için özniteliği algılanması iyimser eşzamanlılık çakışmaları için denetler.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Tasarım zamanında eşlenen) özelliği, eşzamanlılık çalışma zamanı özellikleri ile birlikte kullanılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Hiç üye olarak tanımlanan sürece özgün üye değerlerinin geçerli veritabanı durumu ile karşılaştırılır `IsVersion=true`. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Kod örnekleri için bkz: <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Her zaman bu üye çakışmaları algılamak için kullanın.  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerini `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Hiçbir zaman bu üye çakışmaları algılamak için kullanın.  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerini `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Bu üye, yalnızca uygulama üyenin değeri değiştiğinde çakışmaları algılamak için kullanmak için  
  
1.  Ekleme <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğini <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliği.  
  
2.  Ayarlama <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özellik değerini `WhenChanged`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek belirten `HomePage` nesneleri hiçbir zaman test edilemez güncelleştirme denetimler sırasında. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
