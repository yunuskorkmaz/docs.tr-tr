---
title: 'Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 9d71ca82c3fe1abd23a82d952d38c3ea23a7f1c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197124"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme

İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Data.Linq.ChangeConflictException> iyimser eşzamanlılık çakışmaları nedeniyle nesneler güncelleştirmediği zaman bir özel durum oluşturulur. Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
 Değişikliklerinizi veritabanına göndermeden önce, eşzamanlılık özel durumlarının ne zaman oluşturulması gerektiğini belirtebilirsiniz:  
  
- İlk hatada () özel durumu oluşturur <xref:System.Data.Linq.ConflictMode.FailOnFirstConflict> .  
  
- Tüm güncelleştirme denemelerinden sonuna kadar tüm sorunları biriktir ve özel durum () içinde birikmiş sorunları bildirin <xref:System.Data.Linq.ConflictMode.ContinueOnConflict> .  
  
 Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum bir koleksiyona erişim sağlar <xref:System.Data.Linq.ChangeConflictCollection> . Bu koleksiyon, koleksiyona erişim de dahil olmak üzere her bir çakışmaya ilişkin ayrıntıları (tek bir başarısız güncelleştirme denemeye eşlenir) sağlar <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> . Her üye çakışması, güncelleştirmede eşzamanlılık denetimini başarısız olan tek bir üyeye eşlenir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod her iki değerin örneklerini gösterir.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
