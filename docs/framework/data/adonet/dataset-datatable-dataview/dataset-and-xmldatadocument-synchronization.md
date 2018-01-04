---
title: "Veri kümesi ve XmlDataDocument eşitleme"
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
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: acc68fd36d2887e5e951f9ba5adc20e8cfd87fd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="8101e-102">Veri kümesi ve XmlDataDocument eşitleme</span><span class="sxs-lookup"><span data-stu-id="8101e-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="8101e-103">ADO.NET <xref:System.Data.DataSet> ile ilişkisel bir veri gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8101e-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="8101e-104">Hiyerarşik veri erişimi için .NET Framework kullanılabilen XML sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8101e-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="8101e-105">Tarihsel olarak, bu iki veri sunumu ayrı olarak kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="8101e-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="8101e-106">Ancak, .NET Framework verilerine ilişkisel ve hiyerarşik gösterimlerini gerçek zamanlı, zaman uyumlu erişimini etkinleştirir **DataSet** nesne ve <xref:System.Xml.XmlDataDocument> nesnesi, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8101e-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="8101e-107">Zaman bir **DataSet** ile eşitlenen bir **XmlDataDocument**, hem nesnelerini tek bir veri kümesi ile çalışma.</span><span class="sxs-lookup"><span data-stu-id="8101e-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="8101e-108">Bunun anlamı bir değişiklik yapılırsa **DataSet**, değişiklik yansıtılır **XmlDataDocument**, bunun tam tersi.</span><span class="sxs-lookup"><span data-stu-id="8101e-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="8101e-109">Arasındaki ilişkiyi **DataSet** ve **XmlDataDocument** büyük esneklik yerleşik hizmetlerin tüm suite erişimi için tek bir veri kümesi kullanarak tek bir uygulama vererek oluşturur geçici **DataSet** (örneğin, Web formları ve Windows Forms denetimleri ve Visual Studio .NET tasarımcıları), Genişletilebilir Stil sayfası Dili'nin (XML), XSL Dönüşümleri (XSLT) ve XML Path dahil olmak üzere XML hizmetlerinin paketinin yanı sıra Dili (XPath).</span><span class="sxs-lookup"><span data-stu-id="8101e-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="8101e-110">Hangi hizmetlerin hedef uygulamayla kümesini seçin gerekmez; her ikisi de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8101e-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="8101e-111">Eşitleyebilirsiniz birkaç yolu vardır bir **DataSet** ile bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8101e-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="8101e-112">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8101e-112">You can:</span></span>  
  
-   <span data-ttu-id="8101e-113">Doldurmak bir **DataSet** şeması (diğer bir deyişle, ilişkisel bir yapısı) ve verilerle ve ardından yeni bir eşitleme **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8101e-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="8101e-114">Bu, varolan ilişkisel veri hiyerarşik bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8101e-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="8101e-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8101e-115">For example:</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema and data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema and data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    ```  
  
-   <span data-ttu-id="8101e-116">Doldurmak bir **DataSet** yalnızca şemasıyla (kesin türü belirtilmiş gibi **DataSet**), ile eşitlemek bir **XmlDataDocument**ve ardından Yük  **XmlDataDocument** bir XML belgesinden.</span><span class="sxs-lookup"><span data-stu-id="8101e-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="8101e-117">Bu, mevcut hiyerarşik verileri ilişkisel bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8101e-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="8101e-118">Sütun adlarının ve tablo adlarının, **DataSet** şema ile eşitlenme istediğiniz XML öğelerinin adlarını eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8101e-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="8101e-119">Bu eşleştirme büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8101e-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="8101e-120">Unutmayın şeması **DataSet** yalnızca ilişkisel görünümünüzde kullanıma sunmak istediğiniz XML öğeleri ile eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8101e-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="8101e-121">Bu şekilde, çok büyük bir XML belgesi ve çok küçük bir ilişkisel "Pencere" Bu belge üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="8101e-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="8101e-122">**XmlDataDocument** tüm XML belgesi rağmen korur **DataSet** yalnızca küçük bir kısmı kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8101e-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="8101e-123">(Bu ayrıntılı bir örnek için bkz: [XmlDataDocument ile bir veri eşitleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="8101e-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="8101e-124">Aşağıdaki kod örneği oluşturmak için gereken adımları gösterir bir **DataSet** ve şemasına doldurma ardından ile eşitleme bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8101e-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="8101e-125">Unutmayın **DataSet** şema yalnızca gereken öğeleri eşleşecek şekilde **XmlDataDocument** kullanarak kullanıma sunmak istediğiniz **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8101e-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
    ```vb  
    Dim dataSet As DataSet = New DataSet  
  
    ' Add code here to populate the DataSet with schema, but not data.  
  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument(dataSet)  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    DataSet dataSet = new DataSet();  
  
    // Add code here to populate the DataSet with schema, but not data.  
  
    XmlDataDocument xmlDoc = new XmlDataDocument(dataSet);  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
     <span data-ttu-id="8101e-126">Yüklenemiyor bir **XmlDataDocument** ile eşitlenmişse bir **DataSet** veri içeren.</span><span class="sxs-lookup"><span data-stu-id="8101e-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="8101e-127">Bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8101e-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="8101e-128">Yeni bir **XmlDataDocument** bir XML belgesinden yük ve verileri kullanarak ilişkisel görünümünü erişim **DataSet** özelliği **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8101e-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="8101e-129">Şeması ayarlamak gereken **DataSet** verileri görüntüleyebilmeniz **XmlDataDocument** kullanarak **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8101e-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="8101e-130">Tablo adlarının, sütun yeniden adları, **DataSet** şema ile eşitlenme istediğiniz XML öğelerinin adlarını eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8101e-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="8101e-131">Bu eşleştirme büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8101e-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="8101e-132">Aşağıdaki kod örneği, verileri ilişkisel görünümünü erişmek gösterilmiştir bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8101e-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
    ```vb  
    Dim xmlDoc As XmlDataDocument = New XmlDataDocument  
    Dim dataSet As DataSet = xmlDoc.DataSet  
  
    ' Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml")  
    ```  
  
    ```csharp  
    XmlDataDocument xmlDoc = new XmlDataDocument();  
    DataSet dataSet = xmlDoc.DataSet;  
  
    // Add code here to create the schema of the DataSet to view the data.  
  
    xmlDoc.Load("XMLDocument.xml");  
    ```  
  
 <span data-ttu-id="8101e-133">Eşitleme başka bir avantajı bir **XmlDataDocument** ile bir **DataSet** bir XML belgesi kalitesini korunur.</span><span class="sxs-lookup"><span data-stu-id="8101e-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="8101e-134">Varsa **DataSet** kullanarak bir XML belgesi doldurulur **ReadXml**, verileri kullanarak bir XML belgesi olarak geri yazıldığında **WriteXml** , önemli ölçüde farklı olabilir Özgün XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="8101e-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="8101e-135">Bunun nedeni, **DataSet** , boşluk veya XML belgesinden öğe sırası gibi hiyerarşik bilgileri gibi biçimlendirme korumaz.</span><span class="sxs-lookup"><span data-stu-id="8101e-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="8101e-136">**DataSet** de şeması eşleşmediğinden yoksayıldı öğeleri XML belgesinden içermiyor **Dataset**.</span><span class="sxs-lookup"><span data-stu-id="8101e-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="8101e-137">Eşitleme bir **XmlDataDocument** ile bir **DataSet** içinde korunmasını özgün XML belgesi biçimlendirme ve hiyerarşik öğesi yapısını sağlayan **XmlDataDocument**, sırada **DataSet** yalnızca veri ve şema bilgilerini uygun içeren **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8101e-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="8101e-138">Eşitleme yaparken bir **DataSet** ile bir **XmlDataDocument**, sonuçları olup olmadığını bağlı olarak değişebilir, <xref:System.Data.DataRelation> nesneleri iç içe geçmiş.</span><span class="sxs-lookup"><span data-stu-id="8101e-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="8101e-139">Daha fazla bilgi için bkz: [iç içe geçme DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="8101e-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8101e-140">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8101e-140">In This Section</span></span>  
 [<span data-ttu-id="8101e-141">DataSet’i bir XmlDataDocument ile Eşitleme</span><span class="sxs-lookup"><span data-stu-id="8101e-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="8101e-142">Kesin türü belirtilmiş eşitleme gösteren **DataSet**, en az şemasıyla ile bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8101e-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="8101e-143">DataSet Üzerinde XPath Sorgusu Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8101e-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="8101e-144">İçeriğine XPath sorgusunu gerçekleştirme gösteren bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8101e-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="8101e-145">DataSet’e XSLT Dönüşümü Uygulama</span><span class="sxs-lookup"><span data-stu-id="8101e-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="8101e-146">İçeriği için bir XSLT dönüşümü uygulanarak gösteren bir **DataSet**.</span><span class="sxs-lookup"><span data-stu-id="8101e-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8101e-147">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8101e-147">Related Sections</span></span>  
 [<span data-ttu-id="8101e-148">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="8101e-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="8101e-149">Açıklar nasıl **DataSet** yükleme ve içeriği kalıcı yapma dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir **DataSet** XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="8101e-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="8101e-150">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="8101e-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="8101e-151">Önem düzeyi açıklanmaktadır iç içe geçmiş **DataRelation** nesneleri içeriğini temsil eden olduğunda bir **DataSet** XML verileri olarak ve bu ilişkileri oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="8101e-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="8101e-152">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8101e-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="8101e-153">Açıklar **DataSet** ve uygulama verilerini yönetmek ve ilişkisel veritabanları ve XML gibi veri kaynakları ile etkileşim kurmak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="8101e-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="8101e-154">Hakkında başvuru bilgileri içerir **XmlDataDocument** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8101e-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8101e-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8101e-155">See Also</span></span>  
 [<span data-ttu-id="8101e-156">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8101e-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
