---
title: 'Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: e774935827934ae73873247def049b4045535272
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197150"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> İyimser eşzamanlılık çakışmalarının algılanması için güncelleştirme denetimlerinde hangi üyelerin ekleneceğini belirtmek üzere bir öznitelik üzerinde özelliğe üç Numaralandırmalardan birini uygulayın.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği (tasarım zamanında eşlenir), içindeki çalışma zamanı eşzamanlılık özellikleriyle birlikte kullanılır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Özgün üye değerleri, hiçbir üye olarak belirlenmedikçe geçerli veritabanı durumuyla karşılaştırılır `IsVersion=true` . Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> ..  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Çakışmaları saptamak için her zaman bu üyeyi kullanmak için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özellik değerini olarak ayarlayın `Always` .  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Çakışmaları saptamak için bu üyeyi hiçbir şekilde kullanmayın  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özellik değerini olarak ayarlayın `Never` .  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Bu üyeyi yalnızca uygulama üyenin değerini değiştirdiği zaman çakışmaları saptamak için kullanmak için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özelliği <xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>Özellik değerini olarak ayarlayın `WhenChanged` .  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `HomePage` güncelleştirme denetimleri sırasında nesnelerin hiçbir şekilde sınanmayacağını belirtir. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
