---
title: 'Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma'
description: Bir sınıfı tanımlayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için XML şema tanımı aracını nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 21ce4ad846e21a328ba199f6253bd259be9d932b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379530"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="f75a8-103">Nasıl yapılır: Sınıflar ve XML Şeması Belgeleri Oluşturmak için XML Şema Tanımı Aracını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f75a8-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="f75a8-104">XML şema tanımı Aracı (XSD.exe'nin), bir sınıf açıklayan bir XML şeması oluşturmak veya bir XML şeması tarafından tanımlanan sınıfı oluşturmak için sağlar.</span><span class="sxs-lookup"><span data-stu-id="f75a8-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="f75a8-105">Aşağıdaki yordamlar bu işlemleri gerçekleştirmek nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="f75a8-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="f75a8-106">XML şema tanımı Aracı (xsd. exe) genellikle şu yolda bulunabilir: </span><span class="sxs-lookup"><span data-stu-id="f75a8-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="f75a8-107">_C: \\ Program Files (x86) \\ Microsoft SDK 'ları \\ Windows \\ {Version} \\ bin \\ Netfx {Version} araçları\\_</span><span class="sxs-lookup"><span data-stu-id="f75a8-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="f75a8-108">Belirli bir şemaya uygun sınıflar oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f75a8-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="f75a8-109">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="f75a8-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="f75a8-110">XML şeması için XML Şeması, örneğin tam olarak eşleştirilir sınıf kümesi oluşturur XML şema tanımı aracı için bağımsız değişken olarak geçir:</span><span class="sxs-lookup"><span data-stu-id="f75a8-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="f75a8-111">Araç yalnızca 16 Mart 2001 World Wide Web Consortium XML belirtimi başvuran şemaları işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f75a8-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="f75a8-112">Diğer bir deyişle, aşağıdaki örnekte gösterildiği gibi XML şeması ad alanı " http://www.w3.org/2001/XMLSchema " olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f75a8-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="f75a8-113">Yöntemler, özellikler veya alanları, sınıflar gerektiği şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f75a8-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="f75a8-114">Öznitelikleri olan bir sınıfı değiştirme hakkında daha fazla bilgi için bkz. XML serileştirme 'i, [KODLANMıŞ SOAP serileştirmesini denetleyen](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)öznitelikler ve öznitelikler [kullanarak denetleme](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) .</span><span class="sxs-lookup"><span data-stu-id="f75a8-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="f75a8-115">Genellikle bir sınıfın (veya sınıfların) örnekleri serileştirildiğinde oluşturulan XML akışının şemasını incelemek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="f75a8-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="f75a8-116">Örneğin, şemanızı başkalarının kullanması için yayımlayabilirsiniz veya bu şemayı, uyum elde etmek istediğiniz bir şemayla karşılaştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f75a8-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="f75a8-117">Bir XML Şeması belge sınıfları kümesinden oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="f75a8-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="f75a8-118">Sınıf veya sınıfların bir DLL içine derleyin.</span><span class="sxs-lookup"><span data-stu-id="f75a8-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="f75a8-119">Bir komut istemi açın.</span><span class="sxs-lookup"><span data-stu-id="f75a8-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="f75a8-120">DLL bağımsız değişken olarak XSD.exe'nin için örneğin Geçir:</span><span class="sxs-lookup"><span data-stu-id="f75a8-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="f75a8-121">Şema (veya şemaları) adı "schema0.xsd" ile başlayan yazılır.</span><span class="sxs-lookup"><span data-stu-id="f75a8-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75a8-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f75a8-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="f75a8-123">XML Şema Tanımı Aracı ve XML Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f75a8-123">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="f75a8-124">XML Serileştirmeye Giriş</span><span class="sxs-lookup"><span data-stu-id="f75a8-124">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="f75a8-125">XML şema tanımı Aracı (xsd. exe)</span><span class="sxs-lookup"><span data-stu-id="f75a8-125">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="f75a8-126">Nasıl yapılır: Nesne Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f75a8-126">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="f75a8-127">Nasıl yapılır: Nesneyi Seri Durumdan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="f75a8-127">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
