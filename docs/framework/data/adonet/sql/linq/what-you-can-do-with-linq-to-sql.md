---
title: LINQ to SQL ile Yapabilecekleriniz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 061d98b2-baa7-4336-8ad2-c14de8134d91
ms.openlocfilehash: a2e65cb558eec3cec21ea0efbcc66bb8c56ec7b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163927"
---
# <a name="what-you-can-do-with-linq-to-sql"></a><span data-ttu-id="c4c46-102">LINQ to SQL ile Yapabilecekleriniz</span><span class="sxs-lookup"><span data-stu-id="c4c46-102">What You Can Do With LINQ to SQL</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c4c46-103">, bir SQL geliştiricisi olarak bekleeceğiniz tüm önemli özellikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="c4c46-103">supports all the key capabilities you would expect as a SQL developer.</span></span> <span data-ttu-id="c4c46-104">Bilgileri sorgulayabilir ve tablolardan bilgi ekleyebilir, güncelleştirebilir ve silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c4c46-104">You can query for information, and insert, update, and delete information from tables.</span></span>  
  
## <a name="selecting"></a><span data-ttu-id="c4c46-105">Seçiminde</span><span class="sxs-lookup"><span data-stu-id="c4c46-105">Selecting</span></span>  

 <span data-ttu-id="c4c46-106">(*Projeksiyon*) seçeneği, yalnızca kendi programlama DILINIZDE bir LINQ sorgusu yazarak ve ardından sonuçları almak için bu sorguyu yürüterek elde edilir.</span><span class="sxs-lookup"><span data-stu-id="c4c46-106">Selecting (*projection*) is achieved by just writing a LINQ query in your own programming language, and then executing that query to retrieve the results.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c4c46-107">, tüm gerekli işlemleri, bildiğiniz gerekli SQL işlemlerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="c4c46-107">itself translates all the necessary operations into the necessary SQL operations that you are familiar with.</span></span> <span data-ttu-id="c4c46-108">Daha fazla bilgi için bkz. [LINQ to SQL](index.md).</span><span class="sxs-lookup"><span data-stu-id="c4c46-108">For more information, see [LINQ to SQL](index.md).</span></span>  
  
 <span data-ttu-id="c4c46-109">Aşağıdaki örnekte, Londra 'daki müşterilerin şirket adları, konsol penceresinde alınır ve görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="c4c46-109">In the following example, the company names of customers from London are retrieved and displayed in the console window.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="inserting"></a><span data-ttu-id="c4c46-110">Takma</span><span class="sxs-lookup"><span data-stu-id="c4c46-110">Inserting</span></span>  

 <span data-ttu-id="c4c46-111">Bir SQL yürütmek için `Insert` , yalnızca oluşturduğunuz nesne modeline nesne ekleyin ve üzerinde öğesini çağırın <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="c4c46-111">To execute a SQL `Insert`, just add objects to the object model you have created, and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="c4c46-112">Aşağıdaki örnekte, kullanarak tabloya yeni bir müşteri ve müşteri hakkındaki bilgiler eklenir `Customers` <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A> .</span><span class="sxs-lookup"><span data-stu-id="c4c46-112">In the following example, a new customer and information about the customer is added to the `Customers` table by using <xref:System.Data.Linq.Table%601.InsertOnSubmit%2A>.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#2)]
 [!code-vb[DLinqGettingStarted#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#2)]  
  
## <a name="updating"></a><span data-ttu-id="c4c46-113">Bilen</span><span class="sxs-lookup"><span data-stu-id="c4c46-113">Updating</span></span>  

 <span data-ttu-id="c4c46-114">`Update`Bir veritabanı girişinde, önce öğeyi alın ve doğrudan nesne modelinde düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="c4c46-114">To `Update` a database entry, first retrieve the item and edit it directly in the object model.</span></span> <span data-ttu-id="c4c46-115">Nesneyi değiştirdikten sonra, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> veritabanını güncelleştirmek için üzerinde öğesini çağırın <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="c4c46-115">After you have modified the object, call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to update the database.</span></span>  
  
 <span data-ttu-id="c4c46-116">Aşağıdaki örnekte, Londra 'dan gelen tüm müşteriler alınır.</span><span class="sxs-lookup"><span data-stu-id="c4c46-116">In the following example, all customers who are from London are retrieved.</span></span> <span data-ttu-id="c4c46-117">Ardından, şehir adı "Londra" iken "Londra-Metro" olarak değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c4c46-117">Then the name of the city is changed from "London" to "London - Metro".</span></span> <span data-ttu-id="c4c46-118">Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> değişiklikleri veritabanına göndermek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c4c46-118">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to send the changes to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#3)]
 [!code-vb[DLinqGettingStarted#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#3)]  
  
## <a name="deleting"></a><span data-ttu-id="c4c46-119">Siliniyor</span><span class="sxs-lookup"><span data-stu-id="c4c46-119">Deleting</span></span>  

 <span data-ttu-id="c4c46-120">`Delete`Bir öğe için, öğeyi ait olduğu koleksiyondan kaldırın ve ardından <xref:System.Data.Linq.DataContext.SubmitChanges%2A> <xref:System.Data.Linq.DataContext> değişikliği uygulamak için üzerinde öğesini çağırın.</span><span class="sxs-lookup"><span data-stu-id="c4c46-120">To `Delete` an item, remove the item from the collection to which it belongs, and then call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext> to commit the change.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="c4c46-121">basamaklı silme işlemlerini tanımıyor.</span><span class="sxs-lookup"><span data-stu-id="c4c46-121">does not recognize cascade-delete operations.</span></span> <span data-ttu-id="c4c46-122">Kısıtlama içeren bir tablodaki bir satırı silmek isterseniz, bkz. [nasıl yapılır: satırları veritabanından silme](how-to-delete-rows-from-the-database.md).</span><span class="sxs-lookup"><span data-stu-id="c4c46-122">If you want to delete a row in a table that has constraints against it, see [How to: Delete Rows From the Database](how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="c4c46-123">Aşağıdaki örnekte, çalıştıran müşteri `CustomerID` `98128` veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="c4c46-123">In the following example, the customer who has `CustomerID` of `98128` is retrieved from the database.</span></span> <span data-ttu-id="c4c46-124">Daha sonra, müşteri satırının alındığını onayladıktan sonra, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> Bu nesneyi koleksiyondan kaldırmak için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c4c46-124">Then, after confirming that the customer row was retrieved, <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> is called to remove that object from the collection.</span></span> <span data-ttu-id="c4c46-125">Son olarak, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> silme işlemini veritabanına iletmek için çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c4c46-125">Finally, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called to forward the deletion to the database.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#4)]
 [!code-vb[DLinqGettingStarted#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c4c46-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4c46-126">See also</span></span>

- [<span data-ttu-id="c4c46-127">Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c4c46-127">Programming Guide</span></span>](programming-guide.md)
- [<span data-ttu-id="c4c46-128">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="c4c46-128">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="c4c46-129">Başlarken</span><span class="sxs-lookup"><span data-stu-id="c4c46-129">Getting Started</span></span>](getting-started.md)
