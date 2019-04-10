---
title: 'İzlenecek yol: İlişkilerde Sorgulama (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: 6bd3255b49676b61a99f8416ab71c217d342e799
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59325377"
---
# <a name="walkthrough-querying-across-relationships-c"></a><span data-ttu-id="1b2c5-102">İzlenecek yol: İlişkilerde Sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="1b2c5-102">Walkthrough: Querying Across Relationships (C#)</span></span>
<span data-ttu-id="1b2c5-103">Bu izlenecek yolda kullanımını gösteren [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ilişkilendirmeleri* veritabanında yabancı anahtar ilişkileri göstermek için.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="1b2c5-104">Bu izlenecek yol, Visual kullanılarak yazılmış olduğundan C# geliştirme ayarları.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-104">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1b2c5-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="1b2c5-105">Prerequisites</span></span>  
 <span data-ttu-id="1b2c5-106">Tamamlamış olmanız gerekir [izlenecek yol: Basit Nesne modeli ve sorgu (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="1b2c5-106">You must have completed [Walkthrough: Simple Object Model and Query (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md).</span></span> <span data-ttu-id="1b2c5-107">Bu izlenecek yol, northwnd.mdf dosyasının varlığını c:\linqtest5 dahil olmak üzere bunu üzerine inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest5.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1b2c5-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1b2c5-108">Overview</span></span>  
 <span data-ttu-id="1b2c5-109">Bu kılavuzda üç ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="1b2c5-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="1b2c5-110">Northwind örnek veritabanındaki Siparişler tablosunu temsil edecek bir varlık sınıfı ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="1b2c5-111">Ek açıklamalar ekleme `Customer` sınıfı arasındaki ilişkiyi geliştirmek için `Customer` ve `Order` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="1b2c5-112">Oluşturma ve alma test etmek için bir sorgu çalıştırma `Order` kullanarak bilgi `Customer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-112">Creating and running a query to test obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="1b2c5-113">Tablolar arasındaki ilişkileri eşleme</span><span class="sxs-lookup"><span data-stu-id="1b2c5-113">Mapping Relationships Across Tables</span></span>  
 <span data-ttu-id="1b2c5-114">Sonra `Customer` sınıf tanımını, oluşturma `Order` bildiren aşağıdaki kodu içeren varlık sınıf tanımı `Order.Customer` yabancı anahtar olarak ilişkili `Customer.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Order.Customer` relates as a foreign key to `Customer.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="1b2c5-115">Sipariş varlık sınıfı eklemek için</span><span class="sxs-lookup"><span data-stu-id="1b2c5-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="1b2c5-116">Sonra aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="1b2c5-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="1b2c5-117">Müşteri sınıf ek açıklama ekleme</span><span class="sxs-lookup"><span data-stu-id="1b2c5-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="1b2c5-118">Bu adımda, ek açıklama `Customer` ilişkisini belirtmek için sınıf `Order` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="1b2c5-119">(Herhangi bir yönde ilişkiyi tanımlamadan bağlantıyı oluşturmak yeterli olduğundan bu eklenmesi kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="1b2c5-120">Ancak bu ek açıklama ekleme nesneleri herhangi bir yönde kolayca gidin.)</span><span class="sxs-lookup"><span data-stu-id="1b2c5-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="1b2c5-121">Müşteri sınıf ek açıklama eklemek için</span><span class="sxs-lookup"><span data-stu-id="1b2c5-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="1b2c5-122">İçine aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="1b2c5-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="1b2c5-123">Oluşturma ve müşteri sipariş ilişki sorgu çalıştırma</span><span class="sxs-lookup"><span data-stu-id="1b2c5-123">Creating and Running a Query Across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="1b2c5-124">Artık erişebilirsiniz `Order` doğrudan nesneleri `Customer` nesneleri veya ters sırada.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="1b2c5-125">Açık bir gerekmeyen *birleştirme* müşterilerle siparişler arasındaki.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="1b2c5-126">Erişim için müşteri nesnesi kullanarak nesneleri</span><span class="sxs-lookup"><span data-stu-id="1b2c5-126">To access Order objects by using Customer objects</span></span>  
  
1. <span data-ttu-id="1b2c5-127">Değiştirme `Main` yazarak veya yönteme aşağıdaki kodu kopyalayıp yapıştırmak yöntemi:</span><span class="sxs-lookup"><span data-stu-id="1b2c5-127">Modify the `Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="1b2c5-128">Uygulamanızda hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-128">Press F5 to debug your application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1b2c5-129">Çıkış açıklama satırı yaparak konsol penceresinde SQL kodu çıkarabilirsiniz `db.Log = Console.Out;`.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-129">You can eliminate the SQL code in the Console window by commenting out `db.Log = Console.Out;`.</span></span>  
  
3. <span data-ttu-id="1b2c5-130">Konsol penceresinde, hata ayıklamayı durdurmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-130">Press Enter in the Console window to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="1b2c5-131">Veritabanınızın kesin türü belirtilmiş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="1b2c5-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="1b2c5-132">Bir veritabanınız kesin türü belirtilmiş görünüm ile başlamak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="1b2c5-133">Kesin yazarak <xref:System.Data.Linq.DataContext> nesne çağrıları gerektirmeyen <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="1b2c5-134">Kesin olarak belirlenmiş kullandığınızda tüm sorgularınızdaki kesin türü belirtilmiş tabloları kullanabilir <xref:System.Data.Linq.DataContext> nesne.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="1b2c5-135">Aşağıdaki adımlarda, oluşturacağınız `Customers` veritabanındaki Müşteriler tablosunu eşlendiği kesin türü belirtilmiş bir tablo olarak.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="1b2c5-136">Kesin DataContext nesne yazmak için</span><span class="sxs-lookup"><span data-stu-id="1b2c5-136">To strongly type the DataContext object</span></span>  
  
1. <span data-ttu-id="1b2c5-137">Yukarıdaki aşağıdaki kodu ekleyin `Customer` sınıfının bildirimi.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. <span data-ttu-id="1b2c5-138">Değiştirme `Main` kesin olarak belirlenmiş yöntemini <xref:System.Data.Linq.DataContext> gibi:</span><span class="sxs-lookup"><span data-stu-id="1b2c5-138">Modify the `Main` method to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. <span data-ttu-id="1b2c5-139">Uygulamanızda hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="1b2c5-140">Konsol penceresi çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="1b2c5-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4. <span data-ttu-id="1b2c5-141">Konsol penceresinde, hata ayıklamayı durdurmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-141">Press Enter in the console window to stop debugging.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="1b2c5-142">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="1b2c5-142">Next Steps</span></span>  
 <span data-ttu-id="1b2c5-143">Sonraki izlenecek ([izlenecek yol: Verileri düzenleme (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) verileri işlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-143">The next walkthrough ([Walkthrough: Manipulating Data (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="1b2c5-144">Bu izlenecek yol, iki izlenecek yollar zaten tamamladığınız bu dizide Kaydet gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-144">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b2c5-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b2c5-145">See also</span></span>

- [<span data-ttu-id="1b2c5-146">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="1b2c5-146">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
