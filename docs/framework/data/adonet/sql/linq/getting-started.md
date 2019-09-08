---
title: Başlarken
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793919"
---
# <a name="getting-started"></a><span data-ttu-id="0c7cb-102">Başlarken</span><span class="sxs-lookup"><span data-stu-id="0c7cb-102">Getting Started</span></span>
<span data-ttu-id="0c7cb-103">Kullanarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], bir bellek içi koleksiyona erişirken [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] olduğu gibi SQL veritabanlarına erişmek için de teknolojiyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-103">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="0c7cb-104">Örneğin, `nw` aşağıdaki koddaki nesne `London` `Customers` `Northwind` veritabanını temsil etmek için oluşturulmuştur, tablo hedeflenir, satırlar `Customers` kaynağından filtrelenir ve için `CompanyName` bir dize seçilir alma için.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-104">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="0c7cb-105">Döngü yürütüldüğünde, `CompanyName` değerler koleksiyonu alınır.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-105">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="0c7cb-106">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="0c7cb-106">Next Steps</span></span>  
 <span data-ttu-id="0c7cb-107">Ekleme ve güncelleştirme gibi bazı ek örnekler için, [LINQ to SQL Ile neler yapabileceğinizi](what-you-can-do-with-linq-to-sql.md)görün.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-107">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="0c7cb-108">Daha sonra, kullanma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]konusunda uygulamalı bir deneyim sunmak için bazı izlenecek yollar ve öğreticiler deneyin.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-108">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="0c7cb-109">Bkz. [Gözden Geçirdiklerinizi öğrenme](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="0c7cb-109">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="0c7cb-110">Son olarak, [LINQ to SQL kullanmak için tipik adımları](typical-steps-for-using-linq-to-sql.md)okuyarak kendi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projenize nasıl başlaleyeceğinizi öğrenin.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-110">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c7cb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c7cb-111">See also</span></span>

- [<span data-ttu-id="0c7cb-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0c7cb-112">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="0c7cb-113">LINQ (C#) uygulamasına giriş</span><span class="sxs-lookup"><span data-stu-id="0c7cb-113">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="0c7cb-114">LINQ 'e giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c7cb-114">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="0c7cb-115">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="0c7cb-115">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
