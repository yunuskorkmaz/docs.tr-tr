---
title: DataSet ve XmlDataDocument eşitlemesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 5360a7bce1b5470271bc6b512484964ebb9fd8d1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587784"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="8376e-102">DataSet ve XmlDataDocument eşitlemesi</span><span class="sxs-lookup"><span data-stu-id="8376e-102">DataSet and XmlDataDocument Synchronization</span></span>
<span data-ttu-id="8376e-103">ADO.NET <xref:System.Data.DataSet> verilerin ilişkisel bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8376e-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="8376e-104">Hiyerarşik veri erişimi için .NET Framework XML sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8376e-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="8376e-105">Tarihsel olarak, bu iki verilerini sunumu ayrı olarak kullanılmış.</span><span class="sxs-lookup"><span data-stu-id="8376e-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="8376e-106">Ancak, .NET Framework verilerine ilişkisel ve hiyerarşik temsillerini gerçek zamanlı, zaman uyumlu erişiminizi sağlar **veri kümesi** nesne ve <xref:System.Xml.XmlDataDocument> nesne, sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="8376e-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="8376e-107">Olduğunda bir **veri kümesi** ile eşitlenen bir **XmlDataDocument**, her iki nesne tek bir veri kümesiyle çalıştığınız.</span><span class="sxs-lookup"><span data-stu-id="8376e-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="8376e-108">Bunun anlamı bir değişiklik yapılırsa **veri kümesi**, değişiklik yansıtılır **XmlDataDocument**ve bunun tersi de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="8376e-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="8376e-109">Arasındaki ilişkiyi **veri kümesi** ve **XmlDataDocument** büyük esneklik yerleşik hizmetler tüm paketini erişmek için tek bir veri kümesini kullanarak tek bir uygulama vererek oluşturur. geçici bir çözüm **veri kümesi** (örneğin, Web Forms ve Windows Forms denetimleri ve Visual Studio .NET tasarımcıları), Genişletilebilir Stil Sayfası Dili (XSL), XSLT Dönüşümleri (XSLT) ve XML Path gibi XML Hizmetleri paketi yanı sıra Dil (XPath).</span><span class="sxs-lookup"><span data-stu-id="8376e-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="8376e-110">Hedef uygulama ile Hizmetleri ayarladığı vermeyeceklerini yoktur; her ikisi de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8376e-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="8376e-111">Eşitleyebilirsiniz birkaç şekilde bir **veri kümesi** ile bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8376e-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="8376e-112">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8376e-112">You can:</span></span>  
  
-   <span data-ttu-id="8376e-113">Doldurma bir **veri kümesi** şeması (diğer bir deyişle, ilişkisel bir yapısı) ve verilerle ve ardından yeni bir eşitleme **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8376e-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="8376e-114">Bu, hiyerarşik bir görünümü var olan ilişkisel veri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8376e-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="8376e-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8376e-115">For example:</span></span>  
  
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
  
-   <span data-ttu-id="8376e-116">Doldurma bir **veri kümesi** yalnızca şema ile (bir türü kesin belirlenmiş gibi **veri kümesi**), ile eşitlemek bir **XmlDataDocument**ve ardından Yük  **XmlDataDocument** XML belgesinden.</span><span class="sxs-lookup"><span data-stu-id="8376e-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="8376e-117">Bu, var olan hiyerarşik verilerin ilişkisel bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="8376e-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="8376e-118">Sütun adlarının ve tablo adları, **veri kümesi** şema ile eşitlenme istediğiniz XML öğeleri adları aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8376e-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="8376e-119">Bu eşleştirme büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8376e-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="8376e-120">Unutmayın, şema **veri kümesi** yalnızca ilişkisel görünümünüzde kullanıma sunmak istiyorsanız XML öğeleri ile eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8376e-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="8376e-121">Bu şekilde, çok büyük bir XML belgesi ve oldukça küçük bir ilişkisel "Pencere" Bu belge üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="8376e-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="8376e-122">**XmlDataDocument** tüm XML belgesi olsa bile korur **veri kümesi** yalnızca küçük bir kısmını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8376e-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="8376e-123">(Bu ayrıntılı bir örnek için bkz. [bir DataSet'i bir XmlDataDocument ile eşitleme](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="8376e-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="8376e-124">Aşağıdaki kod örneği oluşturma adımlarını gösteren bir **veri kümesi** ve şeması doldurma, ardından ile eşitleme bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8376e-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="8376e-125">Unutmayın **veri kümesi** şema yalnızca gerekli öğeleri eşleştirilecek **XmlDataDocument** kullanarak kullanıma sunmak istediğiniz **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="8376e-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="8376e-126">Yüklenemiyor bir **XmlDataDocument** ile eşitlenmişse bir **veri kümesi** verilerini içeren.</span><span class="sxs-lookup"><span data-stu-id="8376e-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="8376e-127">bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8376e-127">An exception will be thrown.</span></span>  
  
-   <span data-ttu-id="8376e-128">Yeni bir **XmlDataDocument** XML belgesinden yükleyin ve ardından ilişkisel görünümünü kullanarak veri erişim **veri kümesi** özelliği **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8376e-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="8376e-129">Şemasını ayarlamanız gerekir **veri kümesi** veri görmeden önce **XmlDataDocument** kullanarak **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="8376e-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="8376e-130">Tablo adlarının, sütun yeniden adları, **veri kümesi** şema ile eşitlenme istediğiniz XML öğeleri adları aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8376e-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="8376e-131">Bu eşleştirme büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8376e-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="8376e-132">Aşağıdaki kod örneği, verilerin ilişkisel görünümüne erişime izin gösterilmiştir bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8376e-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="8376e-133">Başka bir avantajı, eşitleme bir **XmlDataDocument** ile bir **veri kümesi** bir XML belgesi kalitesini korunmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8376e-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="8376e-134">Varsa **veri kümesi** kullanarak bir XML belgesi doldurulur **ReadXml**, verileri kullanarak bir XML belgesi olarak geri yazıldığında **WriteXml** , önemli ölçüde farklı olabilir Orijinal XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="8376e-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="8376e-135">Bunun nedeni, **veri kümesi** boşluk veya, XML belgesi öğe sırası gibi hiyerarşik bilgileri gibi biçimlendirme korumaz.</span><span class="sxs-lookup"><span data-stu-id="8376e-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="8376e-136">**Veri kümesi** ayrıca şemasını eşleşmediğinden yoksayıldı öğeleri XML belgesindeki içermiyor **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="8376e-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="8376e-137">Eşitleme bir **XmlDataDocument** ile bir **veri kümesi** içinde tutulması için özgün XML belgesi hiyerarşik ve biçimlendirme öğesi yapısını sağlayan **XmlDataDocument**, ancak **veri kümesi** sadece veri ve şema bilgilerini uygun içeren **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="8376e-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="8376e-138">Eşitlerken bir **veri kümesi** ile bir **XmlDataDocument**, sonuçları alınıp alınmayacağını bağlı olarak farklı olabilir, <xref:System.Data.DataRelation> nesneler iç içe.</span><span class="sxs-lookup"><span data-stu-id="8376e-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="8376e-139">Daha fazla bilgi için [iç içe DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="8376e-139">For more information, see [Nesting DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8376e-140">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8376e-140">In This Section</span></span>  
 [<span data-ttu-id="8376e-141">DataSet’i bir XmlDataDocument ile Eşitleme</span><span class="sxs-lookup"><span data-stu-id="8376e-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="8376e-142">Türü kesin belirlenmiş eşitleme gösterir **veri kümesi**, en az şeması ile bir **XmlDataDocument**.</span><span class="sxs-lookup"><span data-stu-id="8376e-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="8376e-143">DataSet Üzerinde XPath Sorgusu Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="8376e-143">Performing an XPath Query on a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="8376e-144">Bir XPath sorgusu gerçekleştirme içeriğine gösterir bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="8376e-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="8376e-145">DataSet’e XSLT Dönüşümü Uygulama</span><span class="sxs-lookup"><span data-stu-id="8376e-145">Applying an XSLT Transform to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="8376e-146">XSLT dönüşümü uygulama içeriğini gösteren bir **veri kümesi**.</span><span class="sxs-lookup"><span data-stu-id="8376e-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8376e-147">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8376e-147">Related Sections</span></span>  
 [<span data-ttu-id="8376e-148">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="8376e-148">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="8376e-149">Açıklayan nasıl **veri kümesi** yükleniyor ve içeriğini kalıcı dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir **veri kümesi** XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="8376e-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="8376e-150">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="8376e-150">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="8376e-151">Önemini açıklar iç içe geçmiş **DataRelation** nesneleri içeriğini temsil eden, bir **veri kümesi** XML verileri olarak ve bu ilişkileri nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="8376e-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="8376e-152">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="8376e-152">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="8376e-153">Açıklar **veri kümesi** ve uygulama verilerini yönetmek ve ilişkisel veritabanları ve XML gibi veri kaynaklarıyla etkileşim kurmak için kullanma.</span><span class="sxs-lookup"><span data-stu-id="8376e-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="8376e-154">Hakkında başvuru bilgileri içerir **XmlDataDocument** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8376e-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8376e-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8376e-155">See also</span></span>
- [<span data-ttu-id="8376e-156">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8376e-156">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
