---
title: 'Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: dfe1fac4285b915c316fb70d1e3bd1e7b99f145a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Algılama ve birden çok kullanıcı değişiklikleri veritabanına gövdesi çakışmalarını çözme için birçok kaynaklar sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: yönetmek değişiklik çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `try` / `catch` yakalar blok bir <xref:System.Data.Linq.ChangeConflictException> özel durum. Varlık ve üye bilgilerini her çakışma için konsol penceresinde görüntülenir.  
  
> [!NOTE]
>  Eklemelisiniz `using System.Reflection` yönergesi (`Imports System.Reflection` Visual Basic'te) bilgi alma desteklemek için. Daha fazla bilgi için bkz. <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Değişiklikleri Yapma ve Gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
