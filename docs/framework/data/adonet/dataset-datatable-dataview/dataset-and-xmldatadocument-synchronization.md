---
title: DataSet ve XmlDataDocument Eşitlemesi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0ce3793d-54b2-47e4-8cf7-b0591cc4dd21
ms.openlocfilehash: 2790f0a9edd5bfde96683e00725dd04555379adf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153306"
---
# <a name="dataset-and-xmldatadocument-synchronization"></a><span data-ttu-id="314a8-102">DataSet ve XmlDataDocument Eşitlemesi</span><span class="sxs-lookup"><span data-stu-id="314a8-102">DataSet and XmlDataDocument Synchronization</span></span>

<span data-ttu-id="314a8-103">ADO.NET, <xref:System.Data.DataSet> size verilerin ilişkisel bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="314a8-103">The ADO.NET <xref:System.Data.DataSet> provides you with a relational representation of data.</span></span> <span data-ttu-id="314a8-104">Hiyerarşik veri erişimi için .NET Framework bulunan XML sınıflarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="314a8-104">For hierarchical data access, you can use the XML classes available in the .NET Framework.</span></span> <span data-ttu-id="314a8-105">Geçmişte, bu iki veri gösterimi ayrı olarak kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="314a8-105">Historically, these two representations of data have been used separately.</span></span> <span data-ttu-id="314a8-106">Ancak .NET Framework, veri **kümesi** nesnesi ve nesnesi aracılığıyla hem ilişkisel hem de verilerin hiyerarşik temsillerine gerçek zamanlı, zaman uyumlu erişim sağlar <xref:System.Xml.XmlDataDocument> .</span><span class="sxs-lookup"><span data-stu-id="314a8-106">However, the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the **DataSet** object and the <xref:System.Xml.XmlDataDocument> object, respectively.</span></span>  
  
 <span data-ttu-id="314a8-107">Bir **veri kümesi** bir **XmlDataDocument**ile eşitlendiğinde, her iki nesne de tek bir veri kümesiyle çalışır.</span><span class="sxs-lookup"><span data-stu-id="314a8-107">When a **DataSet** is synchronized with an **XmlDataDocument**, both objects are working with a single set of data.</span></span> <span data-ttu-id="314a8-108">Bu, **veri kümesinde**bir değişiklik yapılırsa, değişikliğin **XmlDataDocument**'te yansıtıldığı ve tam tersi anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="314a8-108">This means that if a change is made to the **DataSet**, the change will be reflected in the **XmlDataDocument**, and vice versa.</span></span> <span data-ttu-id="314a8-109">**Veri kümesi** ile **XmlDataDocument** arasındaki ilişki, tek bir uygulamaya izin vererek harika esneklik oluşturur, tek bir veri kümesi **kullanarak veri kümesinin (Web Forms** ve Windows Forms denetimleri ve Visual Studio .net tasarımcıları gibi) yerleşik olarak bulunan tüm hizmet paketine, Genişletilebilir Stil sayfası dili (XSL), XSL dönüştürmeleri (XSLT) ve XML yol dili (XPath) dahil olmak üzere XML Hizmetleri paketini de erişin.</span><span class="sxs-lookup"><span data-stu-id="314a8-109">The relationship between the **DataSet** and the **XmlDataDocument** creates great flexibility by allowing a single application, using a single set of data, to access the entire suite of services built around the **DataSet** (such as Web Forms and Windows Forms controls, and Visual Studio .NET designers), as well as the suite of XML services including Extensible Stylesheet Language (XSL), XSL Transformations (XSLT), and XML Path Language (XPath).</span></span> <span data-ttu-id="314a8-110">Uygulamayla hedeflediğiniz hizmet kümesini seçmeniz gerekmez; her ikisi de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="314a8-110">You do not have to choose which set of services to target with the application; both are available.</span></span>  
  
 <span data-ttu-id="314a8-111">Bir **veri kümesini** **XmlDataDocument**ile eşzamanlı hale getirmek için kullanabileceğiniz çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="314a8-111">There are several ways that you can synchronize a **DataSet** with an **XmlDataDocument**.</span></span> <span data-ttu-id="314a8-112">Seçenekleriniz şunlardır:</span><span class="sxs-lookup"><span data-stu-id="314a8-112">You can:</span></span>  
  
- <span data-ttu-id="314a8-113">Bir **veri kümesini** şema (yani, ilişkisel bir yapı) ve verilerle doldurun ve ardından yeni bir **XmlDataDocument**ile eşitler.</span><span class="sxs-lookup"><span data-stu-id="314a8-113">Populate a **DataSet** with schema (that is, a relational structure) and data and then synchronize it with a new **XmlDataDocument**.</span></span> <span data-ttu-id="314a8-114">Bu, varolan ilişkisel verilerin hiyerarşik bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="314a8-114">This provides a hierarchical view of existing relational data.</span></span> <span data-ttu-id="314a8-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="314a8-115">For example:</span></span>  
  
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
  
- <span data-ttu-id="314a8-116">Bir **veri kümesini** yalnızca şemayla (türü kesin belirlenmiş bir **veri kümesi**) doldurun, bir **XmlDataDocument**ile eşitler ve ardından bir XML belgesinden **XmlDataDocument** öğesini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="314a8-116">Populate a **DataSet** with schema only (such as a strongly typed **DataSet**), synchronize it with an **XmlDataDocument**, and then load the **XmlDataDocument** from an XML document.</span></span> <span data-ttu-id="314a8-117">Bu, varolan hiyerarşik verilerin ilişkisel bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="314a8-117">This provides a relational view of existing hierarchical data.</span></span> <span data-ttu-id="314a8-118">**Veri kümesi** şemanızın tablo adları ve sütun adları, EŞITLENMESINI istediğiniz XML öğelerinin adlarıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="314a8-118">The table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="314a8-119">Bu eşleştirme, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="314a8-119">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="314a8-120">**Veri kümesi** şemasının yalnızca ilişkisel görünüminizdeki göstermek istediğiniz XML öğeleriyle eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="314a8-120">Note that the schema of the **DataSet** only needs to match the XML elements that you want to expose in your relational view.</span></span> <span data-ttu-id="314a8-121">Bu şekilde, bu belgede çok büyük bir XML belgeniz ve çok küçük bir ilişkisel "pencere" olabilir.</span><span class="sxs-lookup"><span data-stu-id="314a8-121">This way, you can have a very large XML document and a very small relational "window" on that document.</span></span> <span data-ttu-id="314a8-122">**Veri kümesi** yalnızca küçük bir kısmını kullanıma sunsa, **XmlDataDocument** tüm XML belgesini korur.</span><span class="sxs-lookup"><span data-stu-id="314a8-122">The **XmlDataDocument** preserves the entire XML document even though the **DataSet** only exposes a small portion of it.</span></span> <span data-ttu-id="314a8-123">(Bunun ayrıntılı bir örneği için bkz. [bir veri kümesini XmlDataDocument Ile eşitleme](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span><span class="sxs-lookup"><span data-stu-id="314a8-123">(For a detailed example of this, see [Synchronizing a DataSet with an XmlDataDocument](synchronizing-a-dataset-with-an-xmldatadocument.md).)</span></span>  
  
     <span data-ttu-id="314a8-124">Aşağıdaki kod örneği, bir **veri kümesi** oluşturma ve şemasını doldurma ve sonra onu bir **XmlDataDocument**ile eşitleme adımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="314a8-124">The following code example shows the steps for creating a **DataSet** and populating its schema, then synchronizing it with an **XmlDataDocument**.</span></span> <span data-ttu-id="314a8-125">**Veri kümesi** şemasının yalnızca **veri kümesini**kullanarak sergilemek istediğiniz **XmlDataDocument** nesnesinden öğelerle eşleşmesi gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="314a8-125">Note that the **DataSet** schema only needs to match the elements from the **XmlDataDocument** that you want to expose using the **DataSet**.</span></span>  
  
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
  
     <span data-ttu-id="314a8-126">Veri içeren bir veri **kümesiyle** eşitlendiğinde **XmlDataDocument** ' i yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="314a8-126">You cannot load an **XmlDataDocument** if it is synchronized with a **DataSet** that contains data.</span></span> <span data-ttu-id="314a8-127">Bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="314a8-127">An exception will be thrown.</span></span>  
  
- <span data-ttu-id="314a8-128">Yeni bir **XmlDataDocument** oluşturun ve bunu bir XML belgesinden yükleyin ve ardından **XmlDataDocument**'in **DataSet** özelliğini kullanarak verilerin ilişkisel görünümüne erişin.</span><span class="sxs-lookup"><span data-stu-id="314a8-128">Create a new **XmlDataDocument** and load it from an XML document, and then access the relational view of the data using the **DataSet** property of the **XmlDataDocument**.</span></span> <span data-ttu-id="314a8-129">Veri **kümesini**kullanarak **XmlDataDocument** 'teki herhangi bir veriyi görüntüleyebilmeniz için veri **kümesinin** şemasını ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="314a8-129">You need to set the schema of the **DataSet** before you can view any of the data in the **XmlDataDocument** using the **DataSet**.</span></span> <span data-ttu-id="314a8-130">Yine, **veri kümesi** şemanızda tablo adları ve sütun adları, EŞITLENMELERINI istediğiniz XML öğelerinin adlarıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="314a8-130">Again, the table names and column names in your **DataSet** schema must match the names of the XML elements that you want them synchronized with.</span></span> <span data-ttu-id="314a8-131">Bu eşleştirme, büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="314a8-131">This matching is case-sensitive.</span></span>  
  
     <span data-ttu-id="314a8-132">Aşağıdaki kod örneğinde, bir **XmlDataDocument**'teki verilerin ilişkisel görünümüne nasıl erişebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="314a8-132">The following code example shows how to access the relational view of the data in an **XmlDataDocument**.</span></span>  
  
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
  
 <span data-ttu-id="314a8-133">Bir **XmlDataDocument** Ile bir **veri kümesiyle** eşitlemenin başka BIR avantajı da bir XML belgesinin uygunlubir korunabilmesidir.</span><span class="sxs-lookup"><span data-stu-id="314a8-133">Another advantage of synchronizing an **XmlDataDocument** with a **DataSet** is that the fidelity of an XML document is preserved.</span></span> <span data-ttu-id="314a8-134">Veri **kümesi** , **READXML**kullanılarak bir XML belgesinden doldurulursa, VERILER **WriteXml** kullanılarak bir XML BELGESI olarak geri yazıldığında, özgün XML belgesinden önemli ölçüde farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="314a8-134">If the **DataSet** is populated from an XML document using **ReadXml**, when the data is written back as an XML document using **WriteXml** it may differ dramatically from the original XML document.</span></span> <span data-ttu-id="314a8-135">Bunun nedeni, **veri kümesinin** boşluk gibi BIÇIMLENDIRMELERI veya XML belgesinden öğe sırası gibi hiyerarşik bilgileri korumadığından kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="314a8-135">This is because the **DataSet** does not maintain formatting, such as white space, or hierarchical information, such as element order, from the XML document.</span></span> <span data-ttu-id="314a8-136">**Veri kümesi** , **veri kümesinin**ŞEMASıYLA eşleşmediği için yoksayılan XML belgesinden öğeleri içermez.</span><span class="sxs-lookup"><span data-stu-id="314a8-136">The **DataSet** also does not contain elements from the XML document that were ignored because they did not match the schema of the **Dataset**.</span></span> <span data-ttu-id="314a8-137">Bir **XmlDataDocument** Ile bir **veri kümesiyle** eşitleme, özgün XML belgesinin biçimlendirme ve hiyerarşik öğe yapısının **XmlDataDocument**'te tutulmasını sağlar, ancak veri kümesi yalnızca veri **kümesine**uygun veri ve şema **bilgilerini içerir.**</span><span class="sxs-lookup"><span data-stu-id="314a8-137">Synchronizing an **XmlDataDocument** with a **DataSet** allows the formatting and hierarchical element structure of the original XML document to be maintained in the **XmlDataDocument**, while the **DataSet** contains only data and schema information appropriate to the **DataSet**.</span></span>  
  
 <span data-ttu-id="314a8-138">Bir **veri kümesini** **XmlDataDocument**ile eşitlerken sonuçlar, <xref:System.Data.DataRelation> nesnelerinizin iç içe yerleştirilmiş olmasına bağlı olarak farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="314a8-138">When synchronizing a **DataSet** with an **XmlDataDocument**, results may differ depending on whether or not your <xref:System.Data.DataRelation> objects are nested.</span></span> <span data-ttu-id="314a8-139">Daha fazla bilgi için bkz. [DataRelation Ile Iç Içe geçme](nesting-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="314a8-139">For more information, see [Nesting DataRelations](nesting-datarelations.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="314a8-140">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="314a8-140">In This Section</span></span>  

 [<span data-ttu-id="314a8-141">DataSet’i bir XmlDataDocument ile Eşitleme</span><span class="sxs-lookup"><span data-stu-id="314a8-141">Synchronizing a DataSet with an XmlDataDocument</span></span>](synchronizing-a-dataset-with-an-xmldatadocument.md)  
 <span data-ttu-id="314a8-142">Türü kesin belirlenmiş bir **veri kümesinin**, en az şemayla, **XmlDataDocument**ile eşitlenmesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="314a8-142">Demonstrates synchronizing a strongly typed **DataSet**, with minimal schema, with an **XmlDataDocument**.</span></span>  
  
 [<span data-ttu-id="314a8-143">DataSet Üzerinde XPath Sorgusu Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="314a8-143">Performing an XPath Query on a DataSet</span></span>](performing-an-xpath-query-on-a-dataset.md)  
 <span data-ttu-id="314a8-144">Bir **veri kümesinin**içeriğinde XPath sorgusu gerçekleştirmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="314a8-144">Demonstrates performing an XPath query on the contents of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="314a8-145">DataSet’e XSLT Dönüşümü Uygulama</span><span class="sxs-lookup"><span data-stu-id="314a8-145">Applying an XSLT Transform to a DataSet</span></span>](applying-an-xslt-transform-to-a-dataset.md)  
 <span data-ttu-id="314a8-146">Bir **veri kümesinin**içeriğine XSLT dönüşümü uygulamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="314a8-146">Demonstrates applying an XSLT transform to the contents of a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="314a8-147">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="314a8-147">Related Sections</span></span>  

 [<span data-ttu-id="314a8-148">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="314a8-148">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="314a8-149">Veri kümesinin, XML verileri olarak bir veri **kümesinin** içeriğini yükleme ve kalıcı hale getirme da dahil olmak üzere XML ile XML ile **nasıl etkileşime** gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="314a8-149">Describes how the **DataSet** interacts with XML as a data source, including loading and persisting the contents of a **DataSet** as XML data.</span></span>  
  
 [<span data-ttu-id="314a8-150">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="314a8-150">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="314a8-151">Bir **veri kümesinin** içeriğini XML verisi olarak temsil eden Iç içe **DataRelation** nesnelerinin önemini açıklar ve bu ilişkilerin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="314a8-151">Discusses the importance of nested **DataRelation** objects when representing the contents of a **DataSet** as XML data, and describes how to create these relations.</span></span>  
  
 [<span data-ttu-id="314a8-152">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="314a8-152">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="314a8-153">Veri **kümesini** ve uygulama verilerini yönetmek ve ilişkisel VERITABANLARı ile XML dahil veri kaynaklarıyla etkileşim kurmak için kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="314a8-153">Describes the **DataSet** and how to use it to manage application data and to interact with data sources including relational databases and XML.</span></span>  
  
 <xref:System.Xml.XmlDataDocument>  
 <span data-ttu-id="314a8-154">**XmlDataDocument** sınıfı hakkında başvuru bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="314a8-154">Contains reference information about the **XmlDataDocument** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="314a8-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="314a8-155">See also</span></span>

- [<span data-ttu-id="314a8-156">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="314a8-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
