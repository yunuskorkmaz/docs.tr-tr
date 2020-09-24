---
title: 'Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 96e96208d9bb28092701164e6cd5943ef81515a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147729"
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
