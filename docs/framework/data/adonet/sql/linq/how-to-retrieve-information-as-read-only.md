---
title: "Nasıl yapılır: salt okunur olarak bilgisi alma"
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
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a9765d8d8330c7ad2a6e8cb25166427cdd9414a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a>Nasıl yapılır: salt okunur olarak bilgisi alma
Verileri değiştirmek düşünmüyorsanız, salt okunur sonuçları aramayı tarafından sorguların performansını artırabilir.  
  
 Salt okunur işleme ayarlayarak uygulamak <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> için `false`.  
  
> [!NOTE]
>  Zaman <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ayarlanır `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> örtük olarak ayarlandığında `false`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod çalışan işe alma tarihleri salt okunur bir koleksiyonunu alır.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Veritabanı sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [Ertelenmiş karşı hemen yükleniyor](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
