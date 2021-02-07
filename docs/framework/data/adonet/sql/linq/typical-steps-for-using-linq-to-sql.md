---
description: Hakkında daha fazla bilgi için bkz. LINQ to SQL kullanımı için tipik adımlar
title: LINQ to SQL Kullanmaya İlişkin Tipik Adımlar
ms.date: 03/30/2017
ms.assetid: 9a88bd51-bd74-48f7-a9b1-f650e8d55a3e
ms.openlocfilehash: eb35b983471db8926646418352b01e1186e235e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680973"
---
# <a name="typical-steps-for-using-linq-to-sql"></a><span data-ttu-id="e421d-103">LINQ to SQL Kullanmaya İlişkin Tipik Adımlar</span><span class="sxs-lookup"><span data-stu-id="e421d-103">Typical Steps for Using LINQ to SQL</span></span>

<span data-ttu-id="e421d-104">Bir uygulamayı uygulamak için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bu konunun ilerleyen kısımlarında açıklanan adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="e421d-104">To implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application, you follow the steps described later in this topic.</span></span> <span data-ttu-id="e421d-105">Birçok adım isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e421d-105">Note that many steps are optional.</span></span> <span data-ttu-id="e421d-106">Nesne modelinizi varsayılan durumunda kullanabilmeniz oldukça olasıdır.</span><span class="sxs-lookup"><span data-stu-id="e421d-106">It is very possible that you can use your object model in its default state.</span></span>  
  
 <span data-ttu-id="e421d-107">Gerçekten hızlı bir başlangıç için, nesne modelinizi oluşturmak ve sorgularınızı kodlamaya başlamak için Nesne İlişkisel Tasarımcısı kullanın.</span><span class="sxs-lookup"><span data-stu-id="e421d-107">For a really fast start, use the Object Relational Designer to create your object model and start coding your queries.</span></span>  
  
## <a name="creating-the-object-model"></a><span data-ttu-id="e421d-108">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e421d-108">Creating the Object Model</span></span>  

 <span data-ttu-id="e421d-109">İlk adım, varolan bir ilişkisel veritabanının meta verilerinden bir nesne modeli oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e421d-109">The first step is to create an object model from the metadata of an existing relational database.</span></span> <span data-ttu-id="e421d-110">Nesne modeli, geliştiricinin programlama diline göre veritabanını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e421d-110">The object model represents the database according to the programming language of the developer.</span></span> <span data-ttu-id="e421d-111">Daha fazla bilgi için bkz. [LINQ to SQL nesne modeli](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-111">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
### <a name="1-select-a-tool-to-create-the-model"></a><span data-ttu-id="e421d-112">1. modeli oluşturmak için bir araç seçin.</span><span class="sxs-lookup"><span data-stu-id="e421d-112">1. Select a tool to create the model.</span></span>  

 <span data-ttu-id="e421d-113">Modeli oluşturmak için üç araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e421d-113">Three tools are available for creating the model.</span></span>  
  
- <span data-ttu-id="e421d-114">Nesne İlişkisel Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="e421d-114">The Object Relational Designer</span></span>  
  
     <span data-ttu-id="e421d-115">Bu tasarımcı, var olan bir veritabanından nesne modeli oluşturmak için zengin bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e421d-115">This designer provides a rich user interface for creating an object model from an existing database.</span></span> <span data-ttu-id="e421d-116">Bu araç, Visual Studio IDE 'nin bir parçasıdır ve küçük veya orta ölçekli veritabanlarına en uygun seçenektir.</span><span class="sxs-lookup"><span data-stu-id="e421d-116">This tool is part of the Visual Studio IDE, and is best suited to small or medium databases.</span></span>  
  
- <span data-ttu-id="e421d-117">SQLMetal kod oluşturma aracı</span><span class="sxs-lookup"><span data-stu-id="e421d-117">The SQLMetal code-generation tool</span></span>  
  
     <span data-ttu-id="e421d-118">Bu komut satırı yardımcı programı O/R Tasarımcısı 'ndan biraz farklı bir seçenek kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e421d-118">This command-line utility provides a slightly different set of options from the O/R Designer.</span></span> <span data-ttu-id="e421d-119">Büyük veritabanlarının modellenmesi, bu araç kullanılarak en iyi şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="e421d-119">Modeling large databases is best done by using this tool.</span></span> <span data-ttu-id="e421d-120">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-120">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
- <span data-ttu-id="e421d-121">Bir kod Düzenleyicisi</span><span class="sxs-lookup"><span data-stu-id="e421d-121">A code editor</span></span>  
  
     <span data-ttu-id="e421d-122">Visual Studio Code Editor ya da başka bir düzenleyiciyi kullanarak kendi kodunuzu yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e421d-122">You can write your own code by using either the Visual Studio code editor or another editor.</span></span> <span data-ttu-id="e421d-123">Var olan bir veritabanınız olduğunda ve O veya SQLMetal aracını kullandığınızda hatalara yol gösteren bu yaklaşımı önermiyoruz.</span><span class="sxs-lookup"><span data-stu-id="e421d-123">We do not recommend this approach, which can be prone to errors, when you have an existing database and can use either the O/R Designer or the SQLMetal tool.</span></span> <span data-ttu-id="e421d-124">Ancak, kod Düzenleyicisi, zaten diğer araçları kullanarak oluşturmuş olduğunuz kodu belirginleştirirken veya değiştirirken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e421d-124">However, the code editor can be valuable for refining or modifying code you have already generated by using other tools.</span></span> <span data-ttu-id="e421d-125">Daha fazla bilgi için bkz. [nasıl yapılır: kod düzenleyicisini kullanarak varlık sınıflarını özelleştirme](how-to-customize-entity-classes-by-using-the-code-editor.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-125">For more information, see [How to: Customize Entity Classes by Using the Code Editor](how-to-customize-entity-classes-by-using-the-code-editor.md).</span></span>  
  
### <a name="2-select-the-kind-of-code-you-want-to-generate"></a><span data-ttu-id="e421d-126">2. oluşturmak istediğiniz kod türünü seçin.</span><span class="sxs-lookup"><span data-stu-id="e421d-126">2. Select the kind of code you want to generate.</span></span>  
  
- <span data-ttu-id="e421d-127">Öznitelik tabanlı eşleme için bir C# veya Visual Basic kaynak kodu dosyası.</span><span class="sxs-lookup"><span data-stu-id="e421d-127">A C# or Visual Basic source code file for attribute-based mapping.</span></span>  
  
     <span data-ttu-id="e421d-128">Daha sonra bu kod dosyasını Visual Studio projenize dahil edersiniz.</span><span class="sxs-lookup"><span data-stu-id="e421d-128">You then include this code file in your Visual Studio project.</span></span> <span data-ttu-id="e421d-129">Daha fazla bilgi için bkz. [öznitelik tabanlı eşleme](attribute-based-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-129">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
- <span data-ttu-id="e421d-130">Dış eşleme için bir XML dosyası.</span><span class="sxs-lookup"><span data-stu-id="e421d-130">An XML file for external mapping.</span></span>  
  
     <span data-ttu-id="e421d-131">Bu yaklaşımı kullanarak, eşleme meta verilerini uygulama kodunuzun dışında tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e421d-131">By using this approach, you can keep the mapping metadata out of your application code.</span></span> <span data-ttu-id="e421d-132">Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-132">For more information, see [External Mapping](external-mapping.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e421d-133">O/R Tasarımcısı dış eşleme dosyalarının oluşturulmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e421d-133">The O/R Designer does not support the generation of external mapping files.</span></span> <span data-ttu-id="e421d-134">Bu özelliği uygulamak için SQLMetal aracını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e421d-134">You must use the SQLMetal tool to implement this feature.</span></span>  
  
- <span data-ttu-id="e421d-135">Son kod dosyası oluşturmadan önce değiştirebileceğiniz bir DBML dosyası.</span><span class="sxs-lookup"><span data-stu-id="e421d-135">A DBML file, which you can modify before generating a final code file.</span></span>  
  
     <span data-ttu-id="e421d-136">Bu gelişmiş bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="e421d-136">This is an advanced feature.</span></span>  
  
### <a name="3-refine-the-code-file-to-reflect-the-needs-of-your-application"></a><span data-ttu-id="e421d-137">3. kod dosyasını uygulamanızın ihtiyaçlarını yansıtacak şekilde daraltın.</span><span class="sxs-lookup"><span data-stu-id="e421d-137">3. Refine the code file to reflect the needs of your application.</span></span>  

 <span data-ttu-id="e421d-138">Bu amaçla, O/R tasarımcısını ya da kod düzenleyicisini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e421d-138">For this purpose, you can use either the O/R Designer or the code editor.</span></span>  
  
## <a name="using-the-object-model"></a><span data-ttu-id="e421d-139">Nesne modelini kullanma</span><span class="sxs-lookup"><span data-stu-id="e421d-139">Using the Object Model</span></span>  

 <span data-ttu-id="e421d-140">Aşağıdaki çizimde, iki katmanlı bir senaryoda geliştirici ve veriler arasındaki ilişki gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e421d-140">The following illustration shows the relationship between the developer and the data in a two-tier scenario.</span></span> <span data-ttu-id="e421d-141">Diğer senaryolar için, [LINQ to SQL Ile N katmanlı ve uzak uygulamalar](n-tier-and-remote-applications-with-linq-to-sql.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e421d-141">For other scenarios, see [N-Tier and Remote Applications with LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md).</span></span>  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="e421d-143">Artık nesne modeline sahip olduğunuza göre, bilgi isteklerini tanımlayabilir ve bu model içindeki verileri yönetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e421d-143">Now that you have the object model, you describe information requests and manipulate data within that model.</span></span> <span data-ttu-id="e421d-144">Nesne modelinizdeki nesnelerin ve özelliklerin yanı sıra veritabanının satırları ve sütunları açısından değil, nesneleri ve özellikleri düşünün.</span><span class="sxs-lookup"><span data-stu-id="e421d-144">You think in terms of the objects and properties in your object model and not in terms of the rows and columns of the database.</span></span> <span data-ttu-id="e421d-145">Veritabanıyla doğrudan işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e421d-145">You do not deal directly with the database.</span></span>  
  
 <span data-ttu-id="e421d-146">Daha önce tanımladığınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veya yaptığınız verileri çağıran bir sorguyu yürütmeyi söylemek istediğinizde veritabanı `SubmitChanges()` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dilinde veritabanıyla iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="e421d-146">When you instruct [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] to either execute a query that you have described or call `SubmitChanges()` on data that you have manipulated, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] communicates with the database in the language of the database.</span></span>  
  
 <span data-ttu-id="e421d-147">Aşağıda, oluşturduğunuz nesne modelini kullanmanın tipik adımları temsil etmektedir.</span><span class="sxs-lookup"><span data-stu-id="e421d-147">The following represents typical steps for using the object model that you have created.</span></span>  
  
### <a name="1-create-queries-to-retrieve-information-from-the-database"></a><span data-ttu-id="e421d-148">1. veritabanından bilgi almak için sorgular oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e421d-148">1. Create queries to retrieve information from the database.</span></span>  

 <span data-ttu-id="e421d-149">Daha fazla bilgi için bkz. [sorgu kavramları](query-concepts.md) ve [sorgu örnekleri](query-examples.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-149">For more information, see [Query Concepts](query-concepts.md) and [Query Examples](query-examples.md).</span></span>  
  
### <a name="2-override-default-behaviors-for-insert-update-and-delete"></a><span data-ttu-id="e421d-150">2. Insert, Update ve delete için varsayılan davranışları geçersiz kılın.</span><span class="sxs-lookup"><span data-stu-id="e421d-150">2. Override default behaviors for Insert, Update, and Delete.</span></span>  

 <span data-ttu-id="e421d-151">Bu adım isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e421d-151">This step is optional.</span></span> <span data-ttu-id="e421d-152">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-152">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
### <a name="3-set-appropriate-options-to-detect-and-report-concurrency-conflicts"></a><span data-ttu-id="e421d-153">3. eşzamanlılık çakışmalarını algılamak ve raporlamak için uygun seçenekleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e421d-153">3. Set appropriate options to detect and report concurrency conflicts.</span></span>  

 <span data-ttu-id="e421d-154">Eşzamanlılık çakışmalarını işlemek için modelinize varsayılan değerleri bırakabilir veya sizin amacınıza uyacak şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e421d-154">You can leave your model with its default values for handling concurrency conflicts, or you can change it to suit your purposes.</span></span> <span data-ttu-id="e421d-155">Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirleme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) ve [nasıl yapılır: eşzamanlılık özel durumlarının ne zaman oluşturulacağını belirtme](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-155">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md) and [How to: Specify When Concurrency Exceptions are Thrown](how-to-specify-when-concurrency-exceptions-are-thrown.md).</span></span>  
  
### <a name="4-establish-an-inheritance-hierarchy"></a><span data-ttu-id="e421d-156">4. devralma hiyerarşisi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e421d-156">4. Establish an inheritance hierarchy.</span></span>  

 <span data-ttu-id="e421d-157">Bu adım isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e421d-157">This step is optional.</span></span> <span data-ttu-id="e421d-158">Daha fazla bilgi için bkz. [Devralma desteği](inheritance-support.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-158">For more information, see [Inheritance Support](inheritance-support.md).</span></span>  
  
### <a name="5-provide-an-appropriate-user-interface"></a><span data-ttu-id="e421d-159">5. uygun bir kullanıcı arabirimi sağlayın.</span><span class="sxs-lookup"><span data-stu-id="e421d-159">5. Provide an appropriate user interface.</span></span>  

 <span data-ttu-id="e421d-160">Bu adım isteğe bağlıdır ve uygulamanızın nasıl kullanılacağına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e421d-160">This step is optional, and depends on how your application will be used.</span></span>  
  
### <a name="6-debug-and-test-your-application"></a><span data-ttu-id="e421d-161">6. uygulamanızı hata ayıklayın ve test edin.</span><span class="sxs-lookup"><span data-stu-id="e421d-161">6. Debug and test your application.</span></span>  

 <span data-ttu-id="e421d-162">Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="e421d-162">For more information, see [Debugging Support](debugging-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e421d-163">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e421d-163">See also</span></span>

- [<span data-ttu-id="e421d-164">Başlarken</span><span class="sxs-lookup"><span data-stu-id="e421d-164">Getting Started</span></span>](getting-started.md)
- [<span data-ttu-id="e421d-165">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e421d-165">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="e421d-166">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="e421d-166">Stored Procedures</span></span>](stored-procedures.md)
