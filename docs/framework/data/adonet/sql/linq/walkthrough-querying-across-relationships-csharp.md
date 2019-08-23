---
title: 'İzlenecek yol: İlişkilerde Sorgulama (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a9e0583b14c07df2b1de23ba37fa88552a4c5c7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946954"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="5d71c-102">İzlenecek yol: İlişkilerde Sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="5d71c-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="5d71c-103">Bu izlenecek yol, veritabanındaki yabancı [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] anahtar ilişkilerini temsil etmek için *ilişkilerin* kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d71c-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="5d71c-104">Bu izlenecek yol, Visual C# Development ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5d71c-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5d71c-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5d71c-105">Prerequisites</span></span>  
 <span data-ttu-id="5d71c-106">Gözden geçirmeyi tamamlamış [olmanız gerekir: Basit nesne modeli ve sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="5d71c-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="5d71c-107">Bu izlenecek yol, c:\linqtest5' teki kuzeydoğu. mdf dosyasının varlığı da dahil olmak üzere bunun üzerine oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d71c-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5d71c-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5d71c-108">Overview</span></span>  
 <span data-ttu-id="5d71c-109">Bu izlenecek yol üç ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="5d71c-109">This walkthrough consists of three main tasks:</span></span>  
  
- <span data-ttu-id="5d71c-110">Örnek Northwind veritabanındaki Orders tablosunu temsil eden bir varlık sınıfı ekleme.</span><span class="sxs-lookup"><span data-stu-id="5d71c-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
- <span data-ttu-id="5d71c-111">Ve`Customer` `Customer` sınıflarıarasındakiilişkiyiiyileştirmekiçinsınıfa`Order` ek açıklamalar eklemek.</span><span class="sxs-lookup"><span data-stu-id="5d71c-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
- <span data-ttu-id="5d71c-112">Sınıfını kullanarak bilgi edinmeyi `Order` test etmek için bir sorgu oluşturma ve çalıştırma. `Customer`</span><span class="sxs-lookup"><span data-stu-id="5d71c-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="5d71c-113">Tablolar arasında Ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="5d71c-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="5d71c-114">Sınıf tanımından sonra, bir yabancı anahtar `Order` `Customer.CustomerID`olarak ilişkili olduğunu `Order.Customer` gösteren aşağıdaki kodu içeren varlık sınıfı tanımını oluşturun. `Customer`</span><span class="sxs-lookup"><span data-stu-id="5d71c-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="5d71c-115">Order Entity sınıfını eklemek için</span><span class="sxs-lookup"><span data-stu-id="5d71c-115">To add the Order entity class</span></span>  
  
- <span data-ttu-id="5d71c-116">Aşağıdaki kodu `Customer` sınıftan sonra yazın veya yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="5d71c-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="5d71c-117">Müşteri sınıfına açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="5d71c-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="5d71c-118">Bu adımda, sınıfıyla ilişkisini `Customer` `Order` göstermek için sınıfına açıklama ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5d71c-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="5d71c-119">(Bu ekleme kesinlikle gerekli değildir, çünkü ilişkinin iki yönde tanımlanması bağlantıyı oluşturmak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5d71c-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="5d71c-120">Ancak bu ek açıklamanın eklenmesi, nesneleri her iki yönde kolayca gezinmenizi sağlar.)</span><span class="sxs-lookup"><span data-stu-id="5d71c-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="5d71c-121">Müşteri sınıfına açıklama eklemek için</span><span class="sxs-lookup"><span data-stu-id="5d71c-121">To annotate the Customer class</span></span>  
  
- <span data-ttu-id="5d71c-122">Aşağıdaki kodu `Customer` sınıfına yazın veya yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="5d71c-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="5d71c-123">Müşteri siparişi Ilişkisi genelinde sorgu oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="5d71c-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="5d71c-124">Artık nesnelere doğrudan `Customer` nesnelerden `Order` veya ters sırada erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d71c-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="5d71c-125">Müşteriler ve siparişler arasında açık bir *birleşime* gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="5d71c-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="5d71c-126">Müşteri nesnelerini kullanarak sıralama nesnelerine erişim</span><span class="sxs-lookup"><span data-stu-id="5d71c-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="5d71c-127">Yöntemine aşağıdaki kodu yazarak veya yapıştırarak yöntemideğiştirin:`Main`</span><span class="sxs-lookup"><span data-stu-id="5d71c-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="5d71c-128">Uygulamanızda hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5d71c-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d71c-129">Konsol penceresinde SQL kodunu, açıklama `db.Log = Console.Out;`ekleyerek ortadan kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d71c-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="5d71c-130">Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5d71c-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="5d71c-131">Veritabanınızın kesin türü belirtilmiş bir görünümünü oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d71c-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="5d71c-132">Veritabanınızın kesin türü belirtilmiş bir görünümüyle başlamak çok daha kolay.</span><span class="sxs-lookup"><span data-stu-id="5d71c-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="5d71c-133"><xref:System.Data.Linq.DataContext> Nesneyi kesin olarak yazarak, ' a <xref:System.Data.Linq.DataContext.GetTable%2A>çağrı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5d71c-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="5d71c-134">Kesin olarak belirlenmiş <xref:System.Data.Linq.DataContext> nesneyi kullandığınızda tüm sorgularınızda kesin türü belirtilmiş tabloları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d71c-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="5d71c-135">Aşağıdaki adımlarda, veritabanında müşteriler tablosuyla eşleşen türü `Customers` kesin belirlenmiş bir tablo olarak oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="5d71c-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="5d71c-136">DataContext nesnesini kesin olarak yazmak için</span><span class="sxs-lookup"><span data-stu-id="5d71c-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="5d71c-137">Aşağıdaki kodu `Customer` sınıf bildiriminin üstüne ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5d71c-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="5d71c-138">Yöntemi, `Main` türü kesin belirlenmiş <xref:System.Data.Linq.DataContext> olarak kullanmak için aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5d71c-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="5d71c-139">Uygulamanızda hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5d71c-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="5d71c-140">Konsol penceresi çıkışı:</span><span class="sxs-lookup"><span data-stu-id="5d71c-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="5d71c-141">Hata ayıklamayı durdurmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5d71c-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5d71c-142">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="5d71c-142">Next Steps</span></span>  
 <span data-ttu-id="5d71c-143">Sonraki izlenecek yol ([izlenecek yol: Verileri düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)), verilerin nasıl değiştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d71c-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="5d71c-144">Bu izlenecek yol, zaten tamamladığınız bu serideki iki izlenecek yolu kaydetmenizi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5d71c-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d71c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d71c-145">See also</span></span>

- [<span data-ttu-id="5d71c-146">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="5d71c-146">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
