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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e7144863e43ec816ad2359c6c48f6d38babb3b46
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
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
 [Sorgu Kavramları](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Veritabanını Sorgulama](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [Ertelenmiş ve Hemen Yükleme Karşılaştırması](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
