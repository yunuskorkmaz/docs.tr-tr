---
title: 'Nasıl yapılır: Algılamak ve çözmek çakışan gönderimleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ab1b56d409a3b185be15ebc8dc119a57038d55bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510513"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Nasıl yapılır: Algılamak ve çözmek çakışan gönderimleri
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] birden çok kullanıcı değişiklikleri veritabanına kökü çakışmaları algılama ve çözümleme için çok sayıda kaynak sağlar. Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `try` / `catch` yakalayan blok bir <xref:System.Data.Linq.ChangeConflictException> özel durum. Her çakışma için varlık ve üye bilgileri, konsol penceresinde görüntülenir.  
  
> [!NOTE]
>  Eklemelisiniz `using System.Reflection` yönergesi (`Imports System.Reflection` Visual Basic'te) bilgi alma desteklemek için. Daha fazla bilgi için bkz. <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
