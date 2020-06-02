---
title: Başlarken
description: Bu örnek kod ile, bir bellek içi koleksiyona erişirken olduğu gibi SQL veritabanlarına erişmek için LINQ teknolojisini kullanmak üzere LINQ to SQL kullanmaya başlayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: a46c42e917bdab0d32ee594bbcd604ee9e3d26bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286423"
---
# <a name="getting-started"></a><span data-ttu-id="0faba-103">Başlarken</span><span class="sxs-lookup"><span data-stu-id="0faba-103">Getting Started</span></span>
<span data-ttu-id="0faba-104">Kullanarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bir bellek içi koleksiyona erişirken olduğu gıbı SQL veritabanlarına erişmek IÇIN LINQ teknolojisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0faba-104">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="0faba-105">Örneğin, `nw` aşağıdaki koddaki nesne veritabanını temsil etmek için oluşturulur `Northwind` , `Customers` tablo hedeflenir, satırlar kaynağından filtrelenir `Customers` `London` ve `CompanyName` alma için bir dizesi seçilidir.</span><span class="sxs-lookup"><span data-stu-id="0faba-105">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="0faba-106">Döngü yürütüldüğünde, `CompanyName` değerler koleksiyonu alınır.</span><span class="sxs-lookup"><span data-stu-id="0faba-106">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="0faba-107">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0faba-107">Next Steps</span></span>  
 <span data-ttu-id="0faba-108">Ekleme ve güncelleştirme gibi bazı ek örnekler için, [LINQ to SQL Ile neler yapabileceğinizi](what-you-can-do-with-linq-to-sql.md)görün.</span><span class="sxs-lookup"><span data-stu-id="0faba-108">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="0faba-109">Daha sonra, kullanma konusunda uygulamalı bir deneyim sunmak için bazı izlenecek yollar ve öğreticiler deneyin [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0faba-109">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="0faba-110">Bkz. [Gözden Geçirdiklerinizi öğrenme](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="0faba-110">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="0faba-111">Son olarak, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] [LINQ to SQL kullanmak Için tipik adımları](typical-steps-for-using-linq-to-sql.md)okuyarak kendi projenize nasıl başlaleyeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0faba-111">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faba-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0faba-112">See also</span></span>

- [<span data-ttu-id="0faba-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0faba-113">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="0faba-114">LINQ 'e giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="0faba-114">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="0faba-115">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0faba-115">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="0faba-116">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="0faba-116">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
