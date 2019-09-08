---
title: 'Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: de7109e0fed0eb7c1975ad7360a7588ef9b294ef
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793147"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Nasıl yapılır: Hangi Üyelerin Eşzamanlılık Çakışmaları için Test Edildiğini Belirtme
İyimser eşzamanlılık çakışmalarının algılanması için güncelleştirme denetimlerinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] hangi üyelerin ekleneceğini <xref:System.Data.Linq.Mapping.ColumnAttribute> belirtmek üzere bir öznitelik üzerinde <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> özelliğe üç Numaralandırmalardan birini uygulayın.  
  
 Özelliği (tasarım zamanında eşlenir), içindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]çalışma zamanı eşzamanlılık özellikleriyle birlikte kullanılır. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.  
  
> [!NOTE]
> Özgün üye değerleri, hiçbir üye olarak `IsVersion=true`belirlenmedikçe geçerli veritabanı durumuyla karşılaştırılır. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Kod örnekleri için bkz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Çakışmaları saptamak için her zaman bu üyeyi kullanmak için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. Özellik değerini olarak `Always`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Çakışmaları saptamak için bu üyeyi hiçbir şekilde kullanmayın  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. Özellik değerini olarak `Never`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Bu üyeyi yalnızca uygulama üyenin değerini değiştirdiği zaman çakışmaları saptamak için kullanmak için  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Özelliği<xref:System.Data.Linq.Mapping.ColumnAttribute> özniteliğine ekleyin.  
  
2. Özellik değerini olarak `WhenChanged`ayarlayın. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, güncelleştirme denetimleri `HomePage` sırasında nesnelerin hiçbir şekilde sınanmayacağını belirtir. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
