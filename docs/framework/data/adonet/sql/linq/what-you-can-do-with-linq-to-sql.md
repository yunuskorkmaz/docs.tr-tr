---
title: LINQ to SQL ile Yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: efb7b86c3add99e596e6798c8267c09689899d56
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231584"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="deb55-102">LINQ to SQL ile Yapabilecekleriniz</span><span class="sxs-lookup"><span data-stu-id="deb55-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="deb55-103">bir SQL geliştirici olarak beklediğiniz tüm anahtar özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="deb55-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="deb55-104">Bilgiler için Sorgulayabileceğiniz ve ekleme, güncelleştirme ve tablolarından bilgi Sil.</span><span class="sxs-lookup"><span data-stu-id="deb55-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="deb55-105">Seçme</span><span class="sxs-lookup"><span data-stu-id="deb55-105">Selecting</span></span>  
 <span data-ttu-id="deb55-106">Seçme (*projeksiyon*) yalnızca yazarak elde edilen bir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] kendi programlama diliyle sorgulayın ve ardından sonuçları almak için bu sorguyu yürütme.</span><span class="sxs-lookup"><span data-stu-id="deb55-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="deb55-107">kendisini bilginiz gerekli SQL işlemleri gerekli tüm işlemlere çevirir.</span><span class="sxs-lookup"><span data-stu-id="deb55-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="deb55-108">Daha fazla bilgi için [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="deb55-108">For more information, see [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="deb55-109">Aşağıdaki örnekte, şirket adlarını londralı müşteriler alınır ve konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="deb55-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="deb55-110">Ekleme</span><span class="sxs-lookup"><span data-stu-id="deb55-110">Inserting</span></span>  
 <span data-ttu-id="deb55-111">Bir SQL yürütme `Insert`, nesneleri oluşturduğunuz nesne modeli ve çağrı eklemeniz yeterlidir <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="deb55-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="deb55-112">Aşağıdaki örnekte, yeni müşteri ve müşteri hakkındaki bilgiler eklenen `Customers` kullanarak tablo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="deb55-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="deb55-113">Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="deb55-113">Updating</span></span>  
 <span data-ttu-id="deb55-114">İçin `Update` bir veritabanı girişi, ilk öğeyi almak ve doğrudan nesne modelinde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="deb55-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="deb55-115">Nesne değiştirdikten sonra çağrı <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> veritabanını güncellemek için.</span><span class="sxs-lookup"><span data-stu-id="deb55-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="deb55-116">Aşağıdaki örnekte, Londra'dan tüm müşterileri alınır.</span><span class="sxs-lookup"><span data-stu-id="deb55-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="deb55-117">Ardından şehir adı "London" "London – Metro için" değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="deb55-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="deb55-118">Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanına değişiklikleri göndermek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="deb55-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="deb55-119">Silme</span><span class="sxs-lookup"><span data-stu-id="deb55-119">Deleting</span></span>  
 <span data-ttu-id="deb55-120">İçin `Delete` , öğenin ait olduğu koleksiyon ve sonra çağrı öğesini kaldırmak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> değişikliği kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="deb55-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="deb55-121">Art arda silme işlemleri algılamaz.</span><span class="sxs-lookup"><span data-stu-id="deb55-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="deb55-122">Bunlara karşı kısıtlamaları olan bir tablosunda bir satıra silmek istiyorsanız, bkz: [nasıl yapılır: Veritabanından satır silme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="deb55-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="deb55-123">Aşağıdaki örnekte, olan müşteri `CustomerID` , `98128` veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="deb55-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="deb55-124">Ardından, müşteri satır alındığını onayladıktan sonra <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> o nesneyi koleksiyondan kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="deb55-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="deb55-125">Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanına silme iletmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="deb55-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="deb55-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="deb55-126">See also</span></span>

- [<span data-ttu-id="deb55-127">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="deb55-127">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)
- [<span data-ttu-id="deb55-128">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="deb55-128">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="deb55-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="deb55-129">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
