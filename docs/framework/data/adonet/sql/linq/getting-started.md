---
title: Başlarken
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634701"
---
# <a name="getting-started"></a><span data-ttu-id="493ab-102">Başlarken</span><span class="sxs-lookup"><span data-stu-id="493ab-102">Getting Started</span></span>
<span data-ttu-id="493ab-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanarak, bir bellek içi koleksiyona erişirken olduğu gibi SQL veritabanlarına erişmek için LINQ teknolojisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="493ab-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="493ab-104">Örneğin, `Northwind` veritabanını temsil etmek için aşağıdaki kodda `nw` nesnesi oluşturulur, `Customers` tablosu hedeflenmiş, satırlar `London``Customers` için filtrelenmiştir ve alma için `CompanyName` için bir dize seçilir.</span><span class="sxs-lookup"><span data-stu-id="493ab-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="493ab-105">Döngü yürütüldüğünde `CompanyName` değerleri koleksiyonu alınır.</span><span class="sxs-lookup"><span data-stu-id="493ab-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="493ab-106">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="493ab-106">Next Steps</span></span>  
 <span data-ttu-id="493ab-107">Ekleme ve güncelleştirme gibi bazı ek örnekler için, [LINQ to SQL Ile neler yapabileceğinizi](what-you-can-do-with-linq-to-sql.md)görün.</span><span class="sxs-lookup"><span data-stu-id="493ab-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="493ab-108">Daha sonra, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanma konusunda uygulamalı bir deneyim sunmak için bazı izlenecek yollar ve öğreticiler deneyin.</span><span class="sxs-lookup"><span data-stu-id="493ab-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="493ab-109">Bkz. [Gözden Geçirdiklerinizi öğrenme](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="493ab-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="493ab-110">Son olarak, [LINQ to SQL kullanmaya yönelik tipik adımları](typical-steps-for-using-linq-to-sql.md)okuyarak kendi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projenize nasıl başlaleyeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="493ab-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="493ab-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="493ab-111">See also</span></span>

- [<span data-ttu-id="493ab-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="493ab-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="493ab-113">LINQ (C#) uygulamasına giriş</span><span class="sxs-lookup"><span data-stu-id="493ab-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="493ab-114">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="493ab-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="493ab-115">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="493ab-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
