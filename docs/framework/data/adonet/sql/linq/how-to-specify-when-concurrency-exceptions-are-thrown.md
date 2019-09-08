---
title: 'Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781611"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], iyimser <xref:System.Data.Linq.ChangeConflictException> eşzamanlılık çakışmaları nedeniyle nesneler güncelleştirmediği zaman bir özel durum oluşturulur. Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.  
  
 Değişikliklerinizi veritabanına göndermeden önce, eşzamanlılık özel durumlarının ne zaman oluşturulması gerektiğini belirtebilirsiniz:  
  
- İlk hatada (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>) özel durumu oluşturur.  
  
- Tüm güncelleştirme denemelerinden sonuna kadar tüm sorunları biriktir ve özel durum (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>) içinde birikmiş sorunları bildirin.  
  
 Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum bir <xref:System.Data.Linq.ChangeConflictCollection> koleksiyona erişim sağlar. Bu koleksiyon, <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> koleksiyona erişim de dahil olmak üzere her bir çakışmaya ilişkin ayrıntıları (tek bir başarısız güncelleştirme denemeye eşlenir) sağlar. Her üye çakışması, güncelleştirmede eşzamanlılık denetimini başarısız olan tek bir üyeye eşlenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod her iki değerin örneklerini gösterir.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
