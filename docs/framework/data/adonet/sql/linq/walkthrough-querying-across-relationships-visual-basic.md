---
title: "İzlenecek yol: İlişkiler (Visual Basic) arasında sorgulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 638382d21818bf879132461f3a6a74336d4ebd19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a><span data-ttu-id="4c27f-102">İzlenecek yol: İlişkiler (Visual Basic) arasında sorgulama</span><span class="sxs-lookup"><span data-stu-id="4c27f-102">Walkthrough: Querying Across Relationships (Visual Basic)</span></span>
<span data-ttu-id="4c27f-103">Bu kılavuzda kullanımını gösteren [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *ilişkilendirmeleri* veritabanında yabancı anahtar ilişkileri temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="4c27f-103">This walkthrough demonstrates the use of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *associations* to represent foreign-key relationships in the database.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="4c27f-104">Bu kılavuz, Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4c27f-104">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4c27f-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4c27f-105">Prerequisites</span></span>  
 <span data-ttu-id="4c27f-106">Tamamlamış olmanız gerekir [izlenecek yol: Basit Nesne modeli ve sorgu (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span><span class="sxs-lookup"><span data-stu-id="4c27f-106">You must have completed [Walkthrough: Simple Object Model and Query (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md).</span></span> <span data-ttu-id="4c27f-107">Bu kılavuzda northwnd.mdf dosyasının varlığı, c:\linqtest dahil olmak üzere bir, inşa edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4c27f-107">This walkthrough builds on that one, including the presence of the northwnd.mdf file in c:\linqtest.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="4c27f-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4c27f-108">Overview</span></span>  
 <span data-ttu-id="4c27f-109">Bu kılavuzda üç ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="4c27f-109">This walkthrough consists of three main tasks:</span></span>  
  
-   <span data-ttu-id="4c27f-110">Örnek Northwind veritabanı Siparişler tablosunda temsil etmek için bir varlık sınıfı ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="4c27f-110">Adding an entity class to represent the Orders table in the sample Northwind database.</span></span>  
  
-   <span data-ttu-id="4c27f-111">Ek açıklamalar ekleme `Customer` arasındaki ilişkiyi geliştirmek için sınıf `Customer` ve `Order` sınıfları.</span><span class="sxs-lookup"><span data-stu-id="4c27f-111">Supplementing annotations to the `Customer` class to enhance the relationship between the `Customer` and `Order` classes.</span></span>  
  
-   <span data-ttu-id="4c27f-112">Oluşturma ve alma işlemini test etmek için bir sorgu çalıştırılarak `Order` kullanarak bilgi `Customer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4c27f-112">Creating and running a query to test the process of obtaining `Order` information by using the `Customer` class.</span></span>  
  
## <a name="mapping-relationships-across-tables"></a><span data-ttu-id="4c27f-113">Tablolar arasında ilişkiler eşleme</span><span class="sxs-lookup"><span data-stu-id="4c27f-113">Mapping Relationships across Tables</span></span>  
 <span data-ttu-id="4c27f-114">Sonra `Customer` sınıf tanımının, oluşturma `Order` belirten aşağıdaki kodu içeren varlık sınıf tanımını `Orders.Customer` bir yabancı anahtar olarak ilişkili `Customers.CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="4c27f-114">After the `Customer` class definition, create the `Order` entity class definition that includes the following code, which indicates that `Orders.Customer` relates as a foreign key to `Customers.CustomerID`.</span></span>  
  
#### <a name="to-add-the-order-entity-class"></a><span data-ttu-id="4c27f-115">Sipariş varlık sınıfı eklemek için</span><span class="sxs-lookup"><span data-stu-id="4c27f-115">To add the Order entity class</span></span>  
  
-   <span data-ttu-id="4c27f-116">Sonra aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4c27f-116">Type or paste the following code after the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a><span data-ttu-id="4c27f-117">Müşteri sınıf yorumlama</span><span class="sxs-lookup"><span data-stu-id="4c27f-117">Annotating the Customer Class</span></span>  
 <span data-ttu-id="4c27f-118">Bu adımda, ek açıklama `Customer` ilişkisini belirtmek için sınıf `Order` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4c27f-118">In this step, you annotate the `Customer` class to indicate its relationship to the `Order` class.</span></span> <span data-ttu-id="4c27f-119">(Her iki yönde ilişkiyi tanımlamadan bağlantıyı oluşturmak için yeterli olduğundan bu eklenmesi kesinlikle gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="4c27f-119">(This addition is not strictly necessary, because defining the relationship in either direction is sufficient to create the link.</span></span> <span data-ttu-id="4c27f-120">Ancak bu ek açıklama ekleme her iki yönde nesneleri kolayca gidin.)</span><span class="sxs-lookup"><span data-stu-id="4c27f-120">But adding this annotation does enable you to easily navigate objects in either direction.)</span></span>  
  
#### <a name="to-annotate-the-customer-class"></a><span data-ttu-id="4c27f-121">Müşteri sınıf ek açıklama eklemek için</span><span class="sxs-lookup"><span data-stu-id="4c27f-121">To annotate the Customer class</span></span>  
  
-   <span data-ttu-id="4c27f-122">Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Customer` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="4c27f-122">Type or paste the following code into the `Customer` class:</span></span>  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a><span data-ttu-id="4c27f-123">Oluşturma ve bir sorgu müşteri siparişi ilişki çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4c27f-123">Creating and Running a Query across the Customer-Order Relationship</span></span>  
 <span data-ttu-id="4c27f-124">Artık erişebilirsiniz `Order` doğrudan nesneleri `Customer` nesneleri veya ters sırada.</span><span class="sxs-lookup"><span data-stu-id="4c27f-124">You can now access `Order` objects directly from the `Customer` objects, or in the opposite order.</span></span> <span data-ttu-id="4c27f-125">Açık bir gerekmez *birleştirme* müşteriler ve Siparişler arasında.</span><span class="sxs-lookup"><span data-stu-id="4c27f-125">You do not need an explicit *join* between customers and orders.</span></span>  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a><span data-ttu-id="4c27f-126">Müşteri nesneleri kullanılarak sipariş nesnelere erişmek için</span><span class="sxs-lookup"><span data-stu-id="4c27f-126">To access Order objects by using Customer objects</span></span>  
  
1.  <span data-ttu-id="4c27f-127">Değiştirme `Sub Main` yazarak veya yöntemine aşağıdaki kodu yapıştırma yöntemi:</span><span class="sxs-lookup"><span data-stu-id="4c27f-127">Modify the `Sub Main` method by typing or pasting the following code into the method:</span></span>  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="4c27f-128">Uygulamanızda hata ayıklama için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c27f-128">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="4c27f-129">İleti kutusu içinde iki adları görüntülenir ve konsol penceresine oluşturulan SQL kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c27f-129">Two names appear in the message box, and the Console window shows the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="4c27f-130">Hata ayıklamayı durdurmak için ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="4c27f-130">Close the message box to stop debugging.</span></span>  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a><span data-ttu-id="4c27f-131">Veritabanınızın kesin türü belirtilmiş bir görünüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="4c27f-131">Creating a Strongly Typed View of Your Database</span></span>  
 <span data-ttu-id="4c27f-132">Veritabanınızın kesin türü belirtilmiş görünüm ile başlatmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="4c27f-132">It is much easier to start with a strongly typed view of your database.</span></span> <span data-ttu-id="4c27f-133">Kesinlikle yazarak <xref:System.Data.Linq.DataContext> nesne çağrıları gerektirmeyen <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="4c27f-133">By strongly typing the <xref:System.Data.Linq.DataContext> object, you do not need calls to <xref:System.Data.Linq.DataContext.GetTable%2A>.</span></span> <span data-ttu-id="4c27f-134">Kesin türü belirtilmiş kullandığınızda, tüm sorgularda kesin türü belirtilmiş tabloları kullanabilir <xref:System.Data.Linq.DataContext> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4c27f-134">You can use strongly typed tables in all your queries when you use the strongly typed <xref:System.Data.Linq.DataContext> object.</span></span>  
  
 <span data-ttu-id="4c27f-135">Aşağıdaki adımlarda oluşturacağınız `Customers` veritabanı Müşteriler tablosunda eşlendiği kesin türü belirtilmiş bir tablo olarak.</span><span class="sxs-lookup"><span data-stu-id="4c27f-135">In the following steps, you will create `Customers` as a strongly typed table that maps to the Customers table in the database.</span></span>  
  
#### <a name="to-strongly-type-the-datacontext-object"></a><span data-ttu-id="4c27f-136">Kesinlikle DataContext nesne türü için</span><span class="sxs-lookup"><span data-stu-id="4c27f-136">To strongly type the DataContext object</span></span>  
  
1.  <span data-ttu-id="4c27f-137">Yukarıdaki aşağıdaki kodu ekleyin `Customer` sınıf bildiriminin.</span><span class="sxs-lookup"><span data-stu-id="4c27f-137">Add the following code above the `Customer` class declaration.</span></span>  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  <span data-ttu-id="4c27f-138">Değiştirme `Sub Main` kesin türü belirtilmiş kullanmak için <xref:System.Data.Linq.DataContext> gibi:</span><span class="sxs-lookup"><span data-stu-id="4c27f-138">Modify `Sub Main` to use the strongly typed <xref:System.Data.Linq.DataContext> as follows:</span></span>  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  <span data-ttu-id="4c27f-139">Uygulamanızda hata ayıklama için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c27f-139">Press F5 to debug your application.</span></span>  
  
     <span data-ttu-id="4c27f-140">Konsol penceresi çıktısı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="4c27f-140">The Console window output is:</span></span>  
  
     `ID=WHITC`  
  
4.  <span data-ttu-id="4c27f-141">Konsol penceresinde uygulamayı kapatmak için Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4c27f-141">Press Enter in the Console window to close the application.</span></span>  
  
5.  <span data-ttu-id="4c27f-142">Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet** bu uygulamayı kaydetmek istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="4c27f-142">On the **File** menu, click **Save All** if you want to save this application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4c27f-143">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="4c27f-143">Next Steps</span></span>  
 <span data-ttu-id="4c27f-144">Sonraki Kılavuzu ([izlenecek yol: veri düzenleme (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) verileri işlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4c27f-144">The next walkthrough ([Walkthrough: Manipulating Data (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) demonstrates how to manipulate data.</span></span> <span data-ttu-id="4c27f-145">Bu izlenecek yol iki izlenecek yollar önceden tamamlamış bu dizide Kaydet gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="4c27f-145">That walkthrough does not require that you save the two walkthroughs in this series that you have already completed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c27f-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4c27f-146">See Also</span></span>  
 [<span data-ttu-id="4c27f-147">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="4c27f-147">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
