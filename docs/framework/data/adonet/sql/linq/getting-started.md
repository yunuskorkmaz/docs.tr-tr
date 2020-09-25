---
title: Başlarken
description: Bu örnek kod ile, bir bellek içi koleksiyona erişirken olduğu gibi SQL veritabanlarına erişmek için LINQ teknolojisini kullanmak üzere LINQ to SQL kullanmaya başlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: b886518d4cff687a18f363c3e3ba43b40631a22f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194381"
---
# <a name="getting-started"></a>Başlarken

Kullanarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bir bellek içi koleksiyona erişirken olduğu gıbı SQL veritabanlarına erişmek IÇIN LINQ teknolojisini kullanabilirsiniz.  
  
 Örneğin, `nw` aşağıdaki koddaki nesne veritabanını temsil etmek için oluşturulur `Northwind` , `Customers` tablo hedeflenir, satırlar kaynağından filtrelenir `Customers` `London` ve `CompanyName` alma için bir dizesi seçilidir.  
  
 Döngü yürütüldüğünde, `CompanyName` değerler koleksiyonu alınır.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Sonraki Adımlar  

 Ekleme ve güncelleştirme gibi bazı ek örnekler için, [LINQ to SQL Ile neler yapabileceğinizi](what-you-can-do-with-linq-to-sql.md)görün.  
  
 Daha sonra, kullanma konusunda uygulamalı bir deneyim sunmak için bazı izlenecek yollar ve öğreticiler deneyin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Bkz. [Gözden Geçirdiklerinizi öğrenme](learning-by-walkthroughs.md).  
  
 Son olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] [LINQ to SQL kullanmak Için tipik adımları](typical-steps-for-using-linq-to-sql.md)okuyarak kendi projenize nasıl başlaleyeceğinizi öğrenin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL](index.md)
- [LINQ 'e giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ 'e giriş (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [LINQ to SQL Nesne Modeli](the-linq-to-sql-object-model.md)
