---
title: LINQ-SQL ile yapabilecekleriniz
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
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: d8393866d8a13121913348404edd8e356f691b7e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="f49aa-102">LINQ-SQL ile yapabilecekleriniz</span><span class="sxs-lookup"><span data-stu-id="f49aa-102">What You Can Do With LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f49aa-103">SQL geliştirici olarak beklediğiniz tüm anahtar özelliklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f49aa-103"> supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="f49aa-104">Bilgi için sorgu ve Ekle, Güncelleştir ve bilgileri tablodan silin.</span><span class="sxs-lookup"><span data-stu-id="f49aa-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="f49aa-105">Seçme</span><span class="sxs-lookup"><span data-stu-id="f49aa-105">Selecting</span></span>  
 <span data-ttu-id="f49aa-106">Seçme (*projeksiyon*) yalnızca yazarak elde edilen bir [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] sorgu kendi programlama dilinde ve sonuçları almak için sorgu yürütme.</span><span class="sxs-lookup"><span data-stu-id="f49aa-106">Selecting (*projection*) is achieved by just writing a [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f49aa-107">kendisini bilginiz gerekli SQL işlemleri gerekli tüm işlemlere çevirir.</span><span class="sxs-lookup"><span data-stu-id="f49aa-107"> itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="f49aa-108">Daha fazla bilgi için bkz: [LINQ-SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="f49aa-108">For more information, see [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md).</span></span>  
  
 <span data-ttu-id="f49aa-109">Aşağıdaki örnekte, Londra müşterilerden şirket adlarını alınır ve konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f49aa-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="f49aa-110">Ekleme</span><span class="sxs-lookup"><span data-stu-id="f49aa-110">Inserting</span></span>  
 <span data-ttu-id="f49aa-111">Bir SQL yürütmek için `Insert`, yalnızca nesneler oluşturdunuz nesne modeli ve arama Ekle <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="f49aa-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="f49aa-112">Aşağıdaki örnekte, yeni müşteri ve müşteri hakkındaki bilgiler eklenen `Customers` kullanarak tablo <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span><span class="sxs-lookup"><span data-stu-id="f49aa-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="f49aa-113">Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="f49aa-113">Updating</span></span>  
 <span data-ttu-id="f49aa-114">İçin `Update` bir veritabanı girişi ilk öğe almak ve doğrudan nesne modelinde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="f49aa-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="f49aa-115">Nesne değiştirdikten sonra arama <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> veritabanını güncelleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="f49aa-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="f49aa-116">Aşağıdaki örnekte, Londra'dan olan tüm müşterilerin alınır.</span><span class="sxs-lookup"><span data-stu-id="f49aa-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="f49aa-117">Ardından şehrin adı "İçin Londra – Metro" "Londra'dan" değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="f49aa-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="f49aa-118">Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> değişiklikleri veritabanına göndermek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f49aa-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="f49aa-119">Silme</span><span class="sxs-lookup"><span data-stu-id="f49aa-119">Deleting</span></span>  
 <span data-ttu-id="f49aa-120">İçin `Delete` bir öğe öğenin ait olduğu koleksiyonu ve ardından arama kaldırın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> üzerinde <xref:System.Data.Linq.DataContext> değişikliği kaydetmek için.</span><span class="sxs-lookup"><span data-stu-id="f49aa-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f49aa-121">Art arda silme işlemleri tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="f49aa-121"> does not recognize cascade-delete operations.</span></span> <span data-ttu-id="f49aa-122">Tablodaki satır silmek istiyorsanız, bunu karşı kısıtlamalarına sahip, bkz: [nasıl yapılır: Sil satırları veritabanından](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="f49aa-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="f49aa-123">Aşağıdaki örnekte, olan müşteri `CustomerID` , `98128` veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="f49aa-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="f49aa-124">Ardından, müşteri satır alındığını onaylayan sonra <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> söz konusu nesne koleksiyondan kaldırmak için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f49aa-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="f49aa-125">Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanı silme iletmek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f49aa-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f49aa-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f49aa-126">See Also</span></span>  
 [<span data-ttu-id="f49aa-127">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f49aa-127">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="f49aa-128">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="f49aa-128">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="f49aa-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="f49aa-129">Getting Started</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
