---
title: "Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek"
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
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8eb2e27ab034d464ba6978d9ddc063e623812619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Algılama ve birden çok kullanıcı değişiklikleri veritabanına gövdesi çakışmalarını çözme için birçok kaynaklar sağlar. Daha fazla bilgi için bkz: [nasıl yapılır: yönetmek değişiklik çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir `try` / `catch` yakalar blok bir <xref:System.Data.Linq.ChangeConflictException> özel durum. Varlık ve üye bilgilerini her çakışma için konsol penceresinde görüntülenir.  
  
> [!NOTE]
>  Eklemelisiniz `using System.Reflection` yönergesi (`Imports System.Reflection` Visual Basic'te) bilgi alma desteklemek için. Daha fazla bilgi için bkz. <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sağlama ve veri değişiklikleri gönderme](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Nasıl yapılır: değişiklik çakışmalarını yönetin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
