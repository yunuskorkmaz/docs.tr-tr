---
title: DataSet içinde XML kullanma
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: e133da727887271af3bc5330a5779df4af58a37e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201193"
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="d4357-102">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="d4357-102">Using XML in a DataSet</span></span>

<span data-ttu-id="d4357-103">ADO.NET ile bir <xref:System.Data.DataSet> XML akışından veya belgesinden bir örneği doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4357-103">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="d4357-104">XML akışını veya belgeyi, <xref:System.Data.DataSet> verileri, şema bilgilerini ya da her ikisini sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d4357-104">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="d4357-105">XML akışından veya belgesinden sağlanan bilgiler, içinde zaten mevcut olan mevcut verilerle veya şema bilgileriyle birleştirilebilir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-105">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="d4357-106">Ayrıca, <xref:System.Data.DataSet> <xref:System.Data.DataSet> başka bir uygulama veya XML özellikli platform tarafından kullanılmak üzere http üzerinden taşımak için, şeması ile veya olmadan bir XML temsili oluşturmanıza da olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4357-106">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="d4357-107">Bir öğesinin XML gösteriminde <xref:System.Data.DataSet> , VERILER XML biçiminde yazılır ve bu şema, temsilde satır içi IÇERIYORSA XML şeması tanım dili (xsd) kullanılarak yazılır.</span><span class="sxs-lookup"><span data-stu-id="d4357-107">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="d4357-108">XML ve XML şeması, <xref:System.Data.DataSet> uzak istemcilerden ve içindeki içeriğini aktarmaya yönelik kolay bir biçim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d4357-108">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4357-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d4357-109">In This Section</span></span>  

 [<span data-ttu-id="d4357-110">DiffGrams</span><span class="sxs-lookup"><span data-stu-id="d4357-110">DiffGrams</span></span>](diffgrams.md)  
 <span data-ttu-id="d4357-111">Öğesinin içeriğini okumak ve yazmak için kullanılan bir XML biçimi olan DiffGram üzerinde ayrıntılar sağlar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-111">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d4357-112">XML’den DataSet Yükleme</span><span class="sxs-lookup"><span data-stu-id="d4357-112">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)  
 <span data-ttu-id="d4357-113">Bir XML belgesinden bir öğesinin içeriğini yüklerken göz önünde bulundurmanız gereken farklı seçenekleri açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-113">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="d4357-114">XML Verileri Olarak DataSet İçeriği Yazma</span><span class="sxs-lookup"><span data-stu-id="d4357-114">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="d4357-115">Bir <xref:System.Data.DataSet> as XML verisi içeriğini ve kullanabileceğiniz farklı XML biçimi seçeneklerini nasıl üretebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4357-115">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="d4357-116">XML’den DataSet Schema Bilgilerini Yükleme</span><span class="sxs-lookup"><span data-stu-id="d4357-116">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="d4357-117"><xref:System.Data.DataSet>XML 'nin şemasını yüklemek için kullanılan yöntemleri açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-117">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="d4357-118">XSD Olarak DataSet Schema Bilgilerini Yazma</span><span class="sxs-lookup"><span data-stu-id="d4357-118">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="d4357-119">Bir XML şeması için kullanımları ve öğesinden bir oluşturma hakkında ele alınmaktadır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-119">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="d4357-120">DataSet ve XmlDataDocument Eşitlemesi</span><span class="sxs-lookup"><span data-stu-id="d4357-120">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="d4357-121">Tek bir veri kümesinin hem ilişkisel hem de hiyerarşik görünümlerine zaman uyumlu erişim .NET Framework, ve arasında zaman uyumlu bir ilişki oluşturmayı gösteren özelliği ele alır <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> .</span><span class="sxs-lookup"><span data-stu-id="d4357-121">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="d4357-122">DataRelations’ı İç İçe Yerleştirme</span><span class="sxs-lookup"><span data-stu-id="d4357-122">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="d4357-123"><xref:System.Data.DataRelation>XML verilerinin bir as içeriğini temsil eden iç içe nesnelerin önemini açıklar <xref:System.Data.DataSet> ve bunların nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4357-123">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="d4357-124">XML Şemasından (XSD) DataSet İlişkisel Yapısını Türetme</span><span class="sxs-lookup"><span data-stu-id="d4357-124">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d4357-125">XML şemasından oluşturulan öğesinin ilişkisel yapısını veya şemasını açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-125">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="d4357-126">XML’den DataSet İlişkisel Yapısını Çıkarma</span><span class="sxs-lookup"><span data-stu-id="d4357-126">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="d4357-127">XML öğelerinden çıkarlandığınızda oluşturulan öğesinin elde edilen ilişkisel yapısını veya şemasını açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="d4357-127">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d4357-128">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d4357-128">Related Sections</span></span>  

 [<span data-ttu-id="d4357-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4357-129">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="d4357-130">ADO.NET mimarisini ve bileşenlerini ve mevcut veri kaynaklarına erişmek için bunların yanı sıra uygulama verilerini yönetmek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d4357-130">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4357-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4357-131">See also</span></span>

- [<span data-ttu-id="d4357-132">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="d4357-132">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="d4357-133">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d4357-133">ADO.NET Overview</span></span>](../ado-net-overview.md)
