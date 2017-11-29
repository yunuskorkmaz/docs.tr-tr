---
title: "Nasıl yapılır: zaman eşzamanlılık özel durumlar belirtin"
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
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8af833574544410977b9f881f9b2db4e6d88aa73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Nasıl yapılır: zaman eşzamanlılık özel durumlar belirtin
İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> nesneleri iyimser eşzamanlılık çakışmaları nedeniyle güncelleştirdiğinizde değil, özel durum. Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Değişiklikler veritabanına göndermeden önce eşzamanlılık özel durum olduğunda belirtebilirsiniz:  
  
-   İlk hata özel durum (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
-   Tüm güncelleştirme çalıştığında son, tüm hataları biriktirmesi ve özel durum birikmiş hataları rapor (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum erişim sağlayan bir <xref:System.Data.Linq.ChangeConflictCollection> koleksiyonu. Bu koleksiyon (bir tek başarısız güncelleştirme try eşlenen) her çakışma dahil olmak üzere ayrıntılarını sağlar <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> koleksiyonu. Tek bir üye olarak tutarlılık denetimi başarısız güncelleştirme her üye çakışma eşler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod iki değer örnekleri gösterir.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: değişiklik çakışmalarını yönetin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Sağlama ve veri değişiklikleri gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
