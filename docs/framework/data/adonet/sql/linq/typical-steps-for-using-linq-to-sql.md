---
title: LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: dc8c4be1e895ee5c4c7947e6311e5bf71008490f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164266"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="32756-102">LINQ to SQL Kullanmaya İlişkin Tipik Adımlar</span><span class="sxs-lookup"><span data-stu-id="32756-102">Typical Steps for Using LINQ to SQL</span></span>

<span data-ttu-id="32756-103">Bir uygulamayı uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bu konunun ilerleyen kısımlarında açıklanan adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="32756-103">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="32756-104">Birçok adım isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32756-104">Note that many steps are optional.</span></span> <span data-ttu-id="32756-105">Nesne modelinizi varsayılan durumunda kullanabilmeniz oldukça olasıdır.</span><span class="sxs-lookup"><span data-stu-id="32756-105">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="32756-106">Gerçekten hızlı bir başlangıç için, nesne modelinizi oluşturmak ve sorgularınızı kodlamaya başlamak için Nesne İlişkisel Tasarımcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="32756-106">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="32756-107">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="32756-107">Creating the Object Model</span></span>  

 <span data-ttu-id="32756-108">İlk adım, varolan bir ilişkisel veritabanının meta verilerinden bir nesne modeli oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="32756-108">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="32756-109">Nesne modeli, geliştiricinin programlama diline göre veritabanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="32756-109">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="32756-110">Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="32756-110">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="32756-111">1. modeli oluşturmak için bir araç seçin.</span><span class="sxs-lookup"><span data-stu-id="32756-111">1. Select a tool to create the model.</span></span>  

 <span data-ttu-id="32756-112">Modeli oluşturmak için üç araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="32756-112">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="32756-113">Nesne İlişkisel Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="32756-113">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="32756-114">Bu tasarımcı, var olan bir veritabanından nesne modeli oluşturmak için zengin bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32756-114">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="32756-115">Bu araç, Visual Studio IDE 'nin bir parçasıdır ve küçük veya orta ölçekli veritabanlarına en uygun seçenektir.</span><span class="sxs-lookup"><span data-stu-id="32756-115">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="32756-116">SQLMetal kod oluşturma aracı</span><span class="sxs-lookup"><span data-stu-id="32756-116">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="32756-117">Bu komut satırı yardımcı programı O/R Tasarımcısı 'ndan biraz farklı bir seçenek kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32756-117">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="32756-118">Büyük veritabanlarının modellenmesi, bu araç kullanılarak en iyi şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="32756-118">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="32756-119">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="32756-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="32756-120">Bir kod Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="32756-120">A code editor</span></span>  
  
     <span data-ttu-id="32756-121">Visual Studio Code Editor ya da başka bir düzenleyiciyi kullanarak kendi kodunuzu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32756-121">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="32756-122">Var olan bir veritabanınız olduğunda ve O veya SQLMetal aracını kullandığınızda hatalara yol gösteren bu yaklaşımı önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="32756-122">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="32756-123">Ancak, kod Düzenleyicisi, zaten diğer araçları kullanarak oluşturmuş olduğunuz kodu belirginleştirirken veya değiştirirken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="32756-123">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="32756-124">Daha fazla bilgi için bkz. [nasıl yapılır: kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md).</span><span class="sxs-lookup"><span data-stu-id="32756-124">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="32756-125">2. oluşturmak istediğiniz kod türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="32756-125">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="32756-126">Öznitelik tabanlı eşleme için bir C# veya Visual Basic kaynak kodu dosyası.</span><span class="sxs-lookup"><span data-stu-id="32756-126">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="32756-127">Daha sonra bu kod dosyasını Visual Studio projenize dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="32756-127">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="32756-128">Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="32756-128">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="32756-129">Dış eşleme için bir XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="32756-129">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="32756-130">Bu yaklaşımı kullanarak, eşleme meta verilerini uygulama kodunuzun dışında tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32756-130">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="32756-131">Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="32756-131">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="32756-132">O/R Tasarımcısı dış eşleme dosyalarının oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="32756-132">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="32756-133">Bu özelliği uygulamak için SQLMetal aracını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="32756-133">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="32756-134">Son kod dosyası oluşturmadan önce değiştirebileceğiniz bir DBML dosyası.</span><span class="sxs-lookup"><span data-stu-id="32756-134">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="32756-135">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="32756-135">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="32756-136">3. kod dosyasını uygulamanızın ihtiyaçlarını yansıtacak şekilde daraltın.</span><span class="sxs-lookup"><span data-stu-id="32756-136">3. Refine the code file to reflect the needs of your application.</span></span>  

 <span data-ttu-id="32756-137">Bu amaçla, O/R tasarımcısını ya da kod düzenleyicisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32756-137">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="32756-138">Nesne modelini kullanma</span><span class="sxs-lookup"><span data-stu-id="32756-138">Using the Object Model</span></span>  

 <span data-ttu-id="32756-139">Aşağıdaki çizimde, iki katmanlı bir senaryoda geliştirici ve veriler arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="32756-139">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="32756-140">Diğer senaryolar için, [LINQ to SQL Ile N katmanlı ve uzak uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32756-140">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="32756-142">Artık nesne modeline sahip olduğunuza göre, bilgi isteklerini tanımlayabilir ve bu model içindeki verileri yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32756-142">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="32756-143">Nesne modelinizdeki nesnelerin ve özelliklerin yanı sıra veritabanının satırları ve sütunları açısından değil, nesneleri ve özellikleri düşünün.</span><span class="sxs-lookup"><span data-stu-id="32756-143">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="32756-144">Veritabanıyla doğrudan işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="32756-144">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="32756-145">Daha önce tanımladığınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veya yaptığınız verileri çağıran bir sorguyu yürütmeyi söylemek istediğinizde veritabanı `SubmitChanges()` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dilinde veritabanıyla iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="32756-145">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="32756-146">Aşağıda, oluşturduğunuz nesne modelini kullanmanın tipik adımları temsil etmektedir.</span><span class="sxs-lookup"><span data-stu-id="32756-146">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="32756-147">1. veritabanından bilgi almak için sorgular oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32756-147">1. Create queries to retrieve information from the database.</span></span>  

 <span data-ttu-id="32756-148">Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md) ve [sorgu örnekleri](query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="32756-148">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="32756-149">2. Insert, Update ve delete için varsayılan davranışları geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="32756-149">2. Override default behaviors for Insert, Update, and Delete.</span></span>  

 <span data-ttu-id="32756-150">Bu adım isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32756-150">This step is optional.</span></span> <span data-ttu-id="32756-151">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="32756-151">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="32756-152">3. eşzamanlılık çakışmalarını algılamak ve raporlamak için uygun seçenekleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="32756-152">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  

 <span data-ttu-id="32756-153">Eşzamanlılık çakışmalarını işlemek için modelinize varsayılan değerleri bırakabilir veya sizin amacınıza uyacak şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32756-153">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="32756-154">Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirleme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) ve [nasıl yapılır: eşzamanlılık özel durumlarının ne zaman oluşturulacağını belirtme](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span><span class="sxs-lookup"><span data-stu-id="32756-154">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="32756-155">4. devralma hiyerarşisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32756-155">4. Establish an inheritance hierarchy.</span></span>  

 <span data-ttu-id="32756-156">Bu adım isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32756-156">This step is optional.</span></span> <span data-ttu-id="32756-157">Daha fazla bilgi için bkz. [Devralma desteği](inheritance-support.md).</span><span class="sxs-lookup"><span data-stu-id="32756-157">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="32756-158">5. uygun bir kullanıcı arabirimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="32756-158">5. Provide an appropriate user interface.</span></span>  

 <span data-ttu-id="32756-159">Bu adım isteğe bağlıdır ve uygulamanızın nasıl kullanılacağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="32756-159">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="32756-160">6. uygulamanızı hata ayıklayın ve test edin.</span><span class="sxs-lookup"><span data-stu-id="32756-160">6. Debug and test your application.</span></span>  

 <span data-ttu-id="32756-161">Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="32756-161">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32756-162">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32756-162">See also</span></span>

- [<span data-ttu-id="32756-163">Başlarken</span><span class="sxs-lookup"><span data-stu-id="32756-163">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="32756-164">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="32756-164">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="32756-165">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="32756-165">Stored Procedures</span></span>](stored-procedures.md)
