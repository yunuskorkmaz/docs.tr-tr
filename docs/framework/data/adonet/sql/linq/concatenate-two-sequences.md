---
title: "İki dizileri birleştirme"
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
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a73ace484c3ca519f250069063a9222b75ef6c17
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="concatenate-two-sequences"></a>İki dizileri birleştirme
Kullanım <xref:System.Linq.Queryable.Concat%2A> iki sıraları birleştirmek için işleci.  
  
 <xref:System.Linq.Queryable.Concat%2A> İşleci alıcı ve bağımsız değişkeni siparişleri bulunduğu aynı sıralı multisets için tanımlanır.  
  
 Sonuçları üretilen önce SQL'de sıralama son adımdır. Bu nedenle, <xref:System.Linq.Queryable.Concat%2A> işleci kullanılarak gerçekleştirilen `UNION ALL` ve bağımsız değişkenlerini sırasını korumaz. Sıralama emin olmak için sonuçları doğru olduğundan, açıkça sonuçları sıralamak emin olun.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` telefon ve Faks numaraları.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Linq.Queryable.Concat%2A> tüm bir dizi döndürülecek `Customer` ve `Employee` adı ve telefon numarası eşlemeleri.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sorgu Örnekleri](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Standart Sorgu İşleci Çevirisi](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
