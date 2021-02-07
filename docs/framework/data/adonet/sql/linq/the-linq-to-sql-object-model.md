---
description: 'Hakkında daha fazla bilgi edinin: LINQ to SQL nesne modeli'
title: LINQ to SQL Nesne Modeli
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: be4021019d09d1479364b25268eefda50b6eaa6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681272"
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="0a4a7-103">LINQ to SQL Nesne Modeli</span><span class="sxs-lookup"><span data-stu-id="0a4a7-103">The LINQ to SQL Object Model</span></span>

<span data-ttu-id="0a4a7-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, geliştiricinin programlama dilinde ifade edilen bir nesne modeli, ilişkisel bir veritabanının veri modeliyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="0a4a7-105">Daha sonra, veriler üzerindeki işlemler nesne modeline göre yürütülür.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-105">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="0a4a7-106">Bu senaryoda veritabanına veritabanı komutları (örneğin,) yayınlamayın `INSERT` .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-106">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="0a4a7-107">Bunun yerine, değerleri değiştirirsiniz ve nesne modelinizdeki yöntemleri yürütün.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-107">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="0a4a7-108">Veritabanını sorgulamak veya değişiklikleri göndermek istediğinizde, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] isteklerinizi doğru SQL komutlarına çevirir ve bu komutları veritabanına gönderir.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-108">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 ![LINQ nesne modelini gösteren ekran görüntüsü.](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="0a4a7-110">Nesne modelindeki en temel öğeler [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve ilişkisel veri modelindeki öğelerle ilişkisi aşağıdaki tabloda özetlenmiştir:</span><span class="sxs-lookup"><span data-stu-id="0a4a7-110">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="0a4a7-111">LINQ to SQL nesne modeli</span><span class="sxs-lookup"><span data-stu-id="0a4a7-111">LINQ to SQL Object Model</span></span>|<span data-ttu-id="0a4a7-112">İlişkisel veri modeli</span><span class="sxs-lookup"><span data-stu-id="0a4a7-112">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="0a4a7-113">Varlık sınıfı</span><span class="sxs-lookup"><span data-stu-id="0a4a7-113">Entity class</span></span>|<span data-ttu-id="0a4a7-114">Tablo</span><span class="sxs-lookup"><span data-stu-id="0a4a7-114">Table</span></span>|  
|<span data-ttu-id="0a4a7-115">Sınıf üyesi</span><span class="sxs-lookup"><span data-stu-id="0a4a7-115">Class member</span></span>|<span data-ttu-id="0a4a7-116">Sütun</span><span class="sxs-lookup"><span data-stu-id="0a4a7-116">Column</span></span>|  
|<span data-ttu-id="0a4a7-117">Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0a4a7-117">Association</span></span>|<span data-ttu-id="0a4a7-118">Yabancı anahtar ilişkisi</span><span class="sxs-lookup"><span data-stu-id="0a4a7-118">Foreign-key relationship</span></span>|  
|<span data-ttu-id="0a4a7-119">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0a4a7-119">Method</span></span>|<span data-ttu-id="0a4a7-120">Saklı yordam veya Işlev</span><span class="sxs-lookup"><span data-stu-id="0a4a7-120">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="0a4a7-121">Aşağıdaki açıklamalarda, ilişkisel veri modeli ve kurallarıyla ilgili temel bilgilere sahip olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-121">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="0a4a7-122">LINQ to SQL varlık sınıfları ve veritabanı tabloları</span><span class="sxs-lookup"><span data-stu-id="0a4a7-122">LINQ to SQL Entity Classes and Database Tables</span></span>  

 <span data-ttu-id="0a4a7-123">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]' De, bir veritabanı tablosu bir *varlık sınıfı* tarafından temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-123">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="0a4a7-124">Bir varlık sınıfı, sınıfının bir veritabanı tablosuyla ilişkilenme özel bilgilerini kullanarak açıklama ekleyerek, oluşturabileceğiniz diğer herhangi bir sınıf gibidir.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-124">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="0a4a7-125"><xref:System.Data.Linq.Mapping.TableAttribute>Aşağıdaki örnekte olduğu gibi, sınıf bildirimidir özel bir öznitelik () ekleyerek bu ek açıklamayı yaparsınız:</span><span class="sxs-lookup"><span data-stu-id="0a4a7-125">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a4a7-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a4a7-126">Example</span></span>  

 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="0a4a7-127">Yalnızca tablo (yani varlık sınıfları) olarak tanımlanan sınıfların örnekleri veritabanına kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-127">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="0a4a7-128">Daha fazla bilgi için [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)tablo özniteliği bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-128">For more information, see the Table Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="0a4a7-129">Sınıf üyeleri ve veritabanı sütunları LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0a4a7-129">LINQ to SQL Class Members and Database Columns</span></span>  

 <span data-ttu-id="0a4a7-130">Sınıfları tablolarla ilişkilendirmenin yanı sıra, alanları veya özellikleri veritabanı sütunlarını temsil edecek şekilde belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-130">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="0a4a7-131">Bu amaçla, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> Aşağıdaki örnekte olduğu gibi özniteliğini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="0a4a7-131">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a4a7-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a4a7-132">Example</span></span>  

 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="0a4a7-133">Yalnızca sütunlara eşlenen alanlar ve Özellikler veritabanına kalıcı olarak kaydedilir veya veritabanından alınır.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-133">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="0a4a7-134">Sütun olarak bildirilmeyen uygulamalar, uygulama mantığınızın geçici bölümleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-134">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="0a4a7-135"><xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği sütunları temsil eden bu üyeleri özelleştirmek için kullanabileceğiniz çeşitli özelliklere sahiptir (örneğin, bir üyeyi birincil anahtar sütununu temsil edecek şekilde belirleme).</span><span class="sxs-lookup"><span data-stu-id="0a4a7-135">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="0a4a7-136">Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)sütun özniteliği bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-136">For more information, see the Column Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="0a4a7-137">LINQ to SQL Ilişkilendirmeleri ve veritabanı yabancı anahtar Ilişkileri</span><span class="sxs-lookup"><span data-stu-id="0a4a7-137">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  

 <span data-ttu-id="0a4a7-138">' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , özniteliğini uygulayarak veritabanı ilişkilendirmelerini (birincil anahtar için yabancı anahtar ilişkileri gibi) temsil edersiniz <xref:System.Data.Linq.Mapping.AssociationAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-138">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="0a4a7-139">Aşağıdaki kod segmentinde, `Order` sınıfı özniteliği olan bir özelliği içerir `Customer` <xref:System.Data.Linq.Mapping.AssociationAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-139">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="0a4a7-140">Bu özellik ve özniteliği sınıfı `Order` ile bir ilişki sağlar `Customer` .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-140">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="0a4a7-141">Aşağıdaki kod örneği `Customer` sınıfından özelliğini gösterir `Order` .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-141">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a4a7-142">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a4a7-142">Example</span></span>  

 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="0a4a7-143">Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md)ilişkilendirme özniteliği bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-143">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="0a4a7-144">LINQ to SQL yöntemleri ve veritabanı saklı yordamları</span><span class="sxs-lookup"><span data-stu-id="0a4a7-144">LINQ to SQL Methods and Database Stored Procedures</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0a4a7-145">saklı yordamları ve Kullanıcı tanımlı işlevleri destekler.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-145">supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="0a4a7-146">' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bu veritabanı tanımlı soyutlamaları istemci nesnelerinde kesin olarak belirlenmiş bir şekilde erişebileceğiniz şekilde, istemci nesneleriyle eşlersiniz.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-146">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="0a4a7-147">Yöntem imzaları, veritabanında tanımlanan yordamlar ve işlevler için olası imzalara benzer.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-147">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="0a4a7-148">Bu yöntemleri saptamak için IntelliSense 'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-148">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="0a4a7-149">Eşlenmiş yordama yapılan bir çağrı tarafından döndürülen bir sonuç kümesi, türü kesin belirlenmiş bir koleksiyondur.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-149">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="0a4a7-150">ve özniteliklerini kullanarak saklı yordamları ve işlevleri yöntemlere eşler <xref:System.Data.Linq.Mapping.FunctionAttribute> <xref:System.Data.Linq.Mapping.ParameterAttribute> .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-150">maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="0a4a7-151">Saklı yordamları temsil eden yöntemler, özelliği tarafından Kullanıcı tanımlı işlevlerden temsil eden uygulamalardan ayırt edilir <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> .</span><span class="sxs-lookup"><span data-stu-id="0a4a7-151">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="0a4a7-152">Bu özellik `false` (varsayılan) olarak ayarlandıysa, yöntemi saklı prosedürü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-152">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="0a4a7-153">Olarak ayarlanırsa `true` , yöntemi bir veritabanı işlevini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-153">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a4a7-154">Visual Studio kullanıyorsanız, saklı yordamlara ve Kullanıcı tanımlı işlevlere eşlenmiş Yöntemler oluşturmak için Nesne İlişkisel Tasarımcısı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-154">If you are using Visual Studio, you can use the Object Relational Designer to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0a4a7-155">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a4a7-155">Example</span></span>  

 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="0a4a7-156">Daha fazla bilgi için, [öznitelik tabanlı eşlemenin](attribute-based-mapping.md) ve [saklı yordamların](stored-procedures.md)Işlev özniteliği, saklı yordam özniteliği ve parametre özniteliği bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-156">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](attribute-based-mapping.md) and [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a4a7-157">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a4a7-157">See also</span></span>

- [<span data-ttu-id="0a4a7-158">Öznitelik Tabanlı Eşleme</span><span class="sxs-lookup"><span data-stu-id="0a4a7-158">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="0a4a7-159">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="0a4a7-159">Background Information</span></span>](background-information.md)
