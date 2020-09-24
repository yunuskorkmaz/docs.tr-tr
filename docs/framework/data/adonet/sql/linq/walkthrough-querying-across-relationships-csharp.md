---
title: 'İzlenecek yol: İlişkilerde Sorgulama (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 9dfe34136f2d0a14a12f72e22a96d1882ddbce49
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164022"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="693a8-102">İzlenecek yol: İlişkilerde Sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="693a8-102">Walkthrough: Querying Across Relationships (C#)</span></span>

<span data-ttu-id="693a8-103">Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanındaki yabancı anahtar ilişkilerini temsil etmek için *ilişkilerin* kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="693a8-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="693a8-104">Bu izlenecek yol, Visual C# geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="693a8-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="693a8-105">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="693a8-105">Prerequisites</span></span>  

 <span data-ttu-id="693a8-106">Gözden geçirmeyi tamamlamış olmanız gerekir [: basit nesne modeli ve sorgu (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="693a8-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="693a8-107">Bu izlenecek yol, c:\linqtest5' teki kuzeydoğu. mdf dosyasının varlığı da dahil olmak üzere bunun üzerine oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="693a8-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="693a8-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="693a8-108">Overview</span></span>  

 <span data-ttu-id="693a8-109">Bu izlenecek yol üç ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="693a8-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="693a8-110">Örnek Northwind veritabanındaki Orders tablosunu temsil eden bir varlık sınıfı ekleme.</span><span class="sxs-lookup"><span data-stu-id="693a8-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="693a8-111">`Customer`Ve sınıfları arasındaki ilişkiyi iyileştirmek için sınıfa ek açıklamalar eklemek `Customer` `Order` .</span><span class="sxs-lookup"><span data-stu-id="693a8-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="693a8-112">Sınıfını kullanarak bilgi edinmeyi test etmek için bir sorgu oluşturma ve çalıştırma `Order` `Customer` .</span><span class="sxs-lookup"><span data-stu-id="693a8-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="693a8-113">Tablolar arasında Ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="693a8-113">Mapping Relationships Across Tables</span></span>  

 <span data-ttu-id="693a8-114">`Customer`Sınıf tanımından sonra, `Order` `Order.Customer` bir yabancı anahtar olarak ilişkili olduğunu gösteren aşağıdaki kodu içeren varlık sınıfı tanımını oluşturun `Customer.CustomerID` .</span><span class="sxs-lookup"><span data-stu-id="693a8-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="693a8-115">Order Entity sınıfını eklemek için</span><span class="sxs-lookup"><span data-stu-id="693a8-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="693a8-116">Aşağıdaki kodu sınıftan sonra yazın veya yapıştırın `Customer` :</span><span class="sxs-lookup"><span data-stu-id="693a8-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="693a8-117">Müşteri sınıfına açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="693a8-117">Annotating the Customer Class</span></span>  

 <span data-ttu-id="693a8-118">Bu adımda, sınıfıyla `Customer` ilişkisini göstermek için sınıfına açıklama ekleyin `Order` .</span><span class="sxs-lookup"><span data-stu-id="693a8-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="693a8-119">(Bu ekleme kesinlikle gerekli değildir, çünkü ilişkinin iki yönde tanımlanması bağlantıyı oluşturmak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="693a8-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="693a8-120">Ancak bu ek açıklamanın eklenmesi, nesneleri her iki yönde kolayca gezinmenizi sağlar.)</span><span class="sxs-lookup"><span data-stu-id="693a8-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="693a8-121">Müşteri sınıfına açıklama eklemek için</span><span class="sxs-lookup"><span data-stu-id="693a8-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="693a8-122">Aşağıdaki kodu sınıfına yazın veya yapıştırın `Customer` :</span><span class="sxs-lookup"><span data-stu-id="693a8-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="693a8-123">Müşteri siparişi Ilişkisi genelinde sorgu oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="693a8-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  

 <span data-ttu-id="693a8-124">Artık `Order` nesnelere doğrudan `Customer` nesnelerden veya ters sırada erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="693a8-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="693a8-125">Müşteriler ve siparişler arasında açık bir *birleşime* gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="693a8-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="693a8-126">Müşteri nesnelerini kullanarak sıralama nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="693a8-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="693a8-127">Yöntemine `Main` aşağıdaki kodu yazarak veya yapıştırarak yöntemi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="693a8-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="693a8-128">Uygulamanızda hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="693a8-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="693a8-129">Konsol penceresinde SQL kodunu, açıklama ekleyerek ortadan kaldırabilirsiniz `db.Log = Console.Out;` .</span><span class="sxs-lookup"><span data-stu-id="693a8-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="693a8-130">Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="693a8-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="693a8-131">Veritabanınızın kesin türü belirtilmiş bir görünümünü oluşturma</span><span class="sxs-lookup"><span data-stu-id="693a8-131">Creating a Strongly Typed View of Your Database</span></span>  

 <span data-ttu-id="693a8-132">Veritabanınızın kesin türü belirtilmiş bir görünümüyle başlamak çok daha kolay.</span><span class="sxs-lookup"><span data-stu-id="693a8-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="693a8-133">Nesneyi kesin olarak yazarak <xref:System.Data.Linq.DataContext> , ' a çağrı gerekmez <xref:System.Data.Linq.DataContext.GetTable%2A> .</span><span class="sxs-lookup"><span data-stu-id="693a8-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="693a8-134">Kesin olarak belirlenmiş nesneyi kullandığınızda tüm sorgularınızda kesin türü belirtilmiş tabloları kullanabilirsiniz <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="693a8-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="693a8-135">Aşağıdaki adımlarda, `Customers` veritabanında müşteriler tablosuyla eşleşen türü kesin belirlenmiş bir tablo olarak oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="693a8-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="693a8-136">DataContext nesnesini kesin olarak yazmak için</span><span class="sxs-lookup"><span data-stu-id="693a8-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="693a8-137">Aşağıdaki kodu sınıf bildiriminin üstüne ekleyin `Customer` .</span><span class="sxs-lookup"><span data-stu-id="693a8-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="693a8-138">Yöntemi, `Main` türü kesin belirlenmiş olarak kullanmak için <xref:System.Data.Linq.DataContext> aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="693a8-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="693a8-139">Uygulamanızda hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="693a8-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="693a8-140">Konsol penceresi çıkışı:</span><span class="sxs-lookup"><span data-stu-id="693a8-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="693a8-141">Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="693a8-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="693a8-142">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="693a8-142">Next Steps</span></span>  

 <span data-ttu-id="693a8-143">Sonraki izlenecek yol ([Izlenecek yol: verileri düzenleme (C#)](walkthrough-manipulating-data-csharp.md)), verilerin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="693a8-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="693a8-144">Bu izlenecek yol, zaten tamamladığınız bu serideki iki izlenecek yolu kaydetmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="693a8-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="693a8-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="693a8-145">See also</span></span>

- [<span data-ttu-id="693a8-146">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="693a8-146">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
