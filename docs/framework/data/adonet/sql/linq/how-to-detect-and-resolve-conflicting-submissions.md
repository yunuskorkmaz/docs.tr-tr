---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: çakışan gönderimleri algılama ve çözme'
title: 'Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 7ccfc9aeba8a21c3f5e950569d7650af087416a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739046"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , çok kullanıcılı değişikliklerden oluşan çakışmaları saptamak ve çözmek için çok sayıda kaynak sağlar. Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek `try` / `catch` bir özel durumu yakalayan bir bloğu gösterir <xref:System.Data.Linq.ChangeConflictException> . Her çakışma için varlık ve üye bilgileri konsol penceresinde görüntülenir.  
  
> [!NOTE]
> `using System.Reflection` `Imports System.Reflection` Bilgi alımını desteklemek için yönergesini (Visual Basic) eklemeniz gerekir. Daha fazla bilgi için bkz. <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Değişiklikleri Yapma ve Gönderme](making-and-submitting-data-changes.md)
- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
