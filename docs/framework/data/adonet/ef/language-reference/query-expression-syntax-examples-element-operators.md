---
title: 'Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 32268fe2-de18-4065-8060-f250def83837
ms.openlocfilehash: 1b73e22e79c665763390561a1e48b2583ec6cd27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215514"
---
# <a name="query-expression-syntax-examples-element-operators"></a>Sorgu İfadesi Söz Dizimi Örnekleri: Öğe İşleçleri
Bu konudaki örnekler nasıl kullanılacağını gösteren <xref:System.Linq.Enumerable.First%2A> sorgu yöntemine [AdventureWorks satışları modeli](https://archive.codeplex.com/?p=msftdbprodsamples) sorgu ifadesi söz dizimini kullanarak. Bu örneklerde kullanılan AdventureWorks satışları modeli kişi, adres, ürün, SalesOrderHeader ve satış siparişi ayrıntısını tablolarda AdventureWorks örnek veritabanı oluşturulur.  
  
 Aşağıdaki örneklerde bu konudaki `using` / `Imports` ifadeleri:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="first"></a>ilk  
  
### <a name="example"></a>Örnek  
 Aşağıdaki örnekte <xref:System.Linq.Enumerable.First%2A> yöntemi ilk kişinin ilk adı döndürülecek olan "Brooke".  
  
 [!code-csharp[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#firstsimple)]
 [!code-vb[DP L2E Examples#FirstSimple](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#firstsimple)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to Entities Sorguları](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
