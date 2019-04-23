---
title: 'Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 30dd83c68472ecd3244cfc87b6df97b948b9a84f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182994"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> iyimser eşzamanlılık çakışmaları nedeniyle nesne güncelleştirme sırasında özel durum oluştu. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Yaptığınız değişiklikleri veritabanına göndermeden önce eşzamanlılık özel durumları oluşturulduğu durumlar belirtebilirsiniz:  
  
-   Özel durum ilk arıza (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
-   Tüm güncelleştirme çalıştığında son, biriken tüm hataları ve özel durum birikmiş hataları rapor (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Oluşturulduğunda, <xref:System.Data.Linq.ChangeConflictException> özel erişim sağlar bir <xref:System.Data.Linq.ChangeConflictCollection> koleksiyonu. Bu koleksiyon (eşlenmiş bir tek bir başarısız güncelleştirme deneyin), her bir çakışma dahil olmak üzere ayrıntılarını sağlar <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> koleksiyonu. Eşzamanlılık denetimi başarısız olan güncelleştirmeyi tek bir üye için her üye çakışma eşler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, her iki değer örnekleri gösterir.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
