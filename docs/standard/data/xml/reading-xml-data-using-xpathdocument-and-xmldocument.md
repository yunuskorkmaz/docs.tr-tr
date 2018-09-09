---
title: XPathDocument ve XmlDocument kullanarak XML verilerini okuma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 5711b225-6aa2-4e4f-9898-19f2d518ad1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e22328c39ae68acc4baff12775b49fbac80696
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252837"
---
# <a name="reading-xml-data-using-xpathdocument-and-xmldocument"></a><span data-ttu-id="d1c21-102">XPathDocument ve XmlDocument kullanarak XML verilerini okuma</span><span class="sxs-lookup"><span data-stu-id="d1c21-102">Reading XML Data using XPathDocument and XmlDocument</span></span>
<span data-ttu-id="d1c21-103">Bir XML belgesinde okumak için iki yolla <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d1c21-103">There are two ways to read an XML document in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d1c21-104">Salt okunur kullanarak bir XML belgesi okumak için biridir <xref:System.Xml.XPath.XPathDocument> sınıfı ve diğer olan düzenlenebilir kullanarak bir XML belgesi okumak için <xref:System.Xml.XmlDocument> sınıfını <xref:System.Xml?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d1c21-104">One is to read an XML document using the read-only <xref:System.Xml.XPath.XPathDocument> class and the other is to read an XML document using the editable <xref:System.Xml.XmlDocument> class in the <xref:System.Xml?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="reading-xml-documents-using-the-xpathdocument-class"></a><span data-ttu-id="d1c21-105">Okuma XML belgeleri XPathDocument sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="d1c21-105">Reading XML Documents using the XPathDocument Class</span></span>  
 <span data-ttu-id="d1c21-106"><xref:System.Xml.XPath.XPathDocument> Sınıfı XPath veri modelini kullanarak bir XML belgesi hızlı, salt okunur, bellek içi bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d1c21-106">The <xref:System.Xml.XPath.XPathDocument> class provides a fast, read-only, in-memory representation of an XML document using the XPath data model.</span></span> <span data-ttu-id="d1c21-107">Örneklerini <xref:System.Xml.XPath.XPathDocument> sınıf kendi altı oluşturucular biri kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d1c21-107">Instances of the <xref:System.Xml.XPath.XPathDocument> class are created using one of its six constructors.</span></span> <span data-ttu-id="d1c21-108">Bu oluşturucular kullanarak bir XML belgesi okumak izin bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi yanı sıra `string` bir XML dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="d1c21-108">These constructors allow you to read an XML document using a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="d1c21-109">Kullanarak aşağıdaki örnekte gösterildiği <xref:System.Xml.XPath.XPathDocument> sınıfın `string` bir XML belgesi okumak için oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="d1c21-109">The following example illustrates using the <xref:System.Xml.XPath.XPathDocument> class's `string` constructor to read an XML document.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
```  
  
## <a name="reading-xml-documents-using-the-xmldocument-class"></a><span data-ttu-id="d1c21-110">Okuma XML belgeleri XmlDocument sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="d1c21-110">Reading XML Documents using the XmlDocument Class</span></span>  
 <span data-ttu-id="d1c21-111"><xref:System.Xml.XmlDocument> Düzenlenebilir bir bellek içi temsili W3C belge nesne modeli (DOM) Düzey 1 çekirdek ve çekirdek DOM Düzey 2 uygulama bir XML belgesi bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="d1c21-111">The <xref:System.Xml.XmlDocument> class is an editable in-memory representation of an XML document implementing W3C Document Object Model (DOM) Level 1 Core and Core DOM Level 2.</span></span> <span data-ttu-id="d1c21-112">Örneklerini <xref:System.Xml.XmlDocument> sınıfı üç kendi oluşturucular biri kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d1c21-112">Instances of the <xref:System.Xml.XmlDocument> class are created using one of its three constructors.</span></span> <span data-ttu-id="d1c21-113">Yeni, boş oluşturabilirsiniz <xref:System.Xml.XmlDocument> çağırarak <xref:System.Xml.XmlDocument> sınıf oluşturucusu parametresiz.</span><span class="sxs-lookup"><span data-stu-id="d1c21-113">You can create a new, empty <xref:System.Xml.XmlDocument> object by calling the <xref:System.Xml.XmlDocument> class constructor with no parameters.</span></span> <span data-ttu-id="d1c21-114">Oluşturucu çağrıldıktan sonra kullanmak <xref:System.Xml.XmlDocument.Load%2A> yeni XML verilerini yüklemek için gereken yöntemini <xref:System.Xml.XmlDocument> nesnesinden bir <xref:System.IO.Stream>, <xref:System.IO.TextReader>, veya <xref:System.Xml.XmlReader> nesnesi yanı sıra `string` bir XML dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="d1c21-114">After calling the constructor, use the <xref:System.Xml.XmlDocument.Load%2A> method to load XML data into the new <xref:System.Xml.XmlDocument> object from a <xref:System.IO.Stream>, <xref:System.IO.TextReader>, or <xref:System.Xml.XmlReader> object, as well as the `string` path to an XML file.</span></span>  
  
 <span data-ttu-id="d1c21-115">Kullanarak aşağıdaki örnekte gösterildiği <xref:System.Xml.XmlDocument> sınıf oluşturucusu parametresiz ve <xref:System.Xml.XmlDocument.Load%2A> bir XML belgesi okumak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d1c21-115">The following example illustrates using the <xref:System.Xml.XmlDocument> class constructor with no parameters and the <xref:System.Xml.XmlDocument.Load%2A> method to read an XML document.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
```  
  
## <a name="determining-the-encoding-of-an-xml-document"></a><span data-ttu-id="d1c21-116">Bir XML belgesi kodlamasıyla belirleme</span><span class="sxs-lookup"><span data-stu-id="d1c21-116">Determining the Encoding of an XML Document</span></span>  
 <span data-ttu-id="d1c21-117">Bir <xref:System.Xml.XmlReader> nesnesi, bir XML belgesi okumak ve oluşturmak için kullanılabilir <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> nesneleri önceki bölümlerde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="d1c21-117">An <xref:System.Xml.XmlReader> object can be used to read an XML document and to create <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> objects as shown in the previous sections.</span></span> <span data-ttu-id="d1c21-118">Ancak, bir <xref:System.Xml.XmlReader> nesne kodlanmamış ve sonuç olarak, kodlama herhangi bir bilgi sağlamaz verileri okuma.</span><span class="sxs-lookup"><span data-stu-id="d1c21-118">However, an <xref:System.Xml.XmlReader> object may read data that is not encoded and as a result does not provide any encoding information.</span></span>  
  
 <span data-ttu-id="d1c21-119"><xref:System.Xml.XmlTextReader> Sınıfının devraldığı <xref:System.Xml.XmlReader> sınıfı, kodlama bilgileriyle sağlar, <xref:System.Xml.XmlTextReader.Encoding%2A> özelliği ve oluşturmak için kullanılan bir <xref:System.Xml.XPath.XPathDocument> nesne veya <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="d1c21-119">The <xref:System.Xml.XmlTextReader> class inherits from the <xref:System.Xml.XmlReader> class, provides encoding information using its <xref:System.Xml.XmlTextReader.Encoding%2A> property, and can be used to create an <xref:System.Xml.XPath.XPathDocument> object or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 <span data-ttu-id="d1c21-120">Tarafından sağlanan kodlama bilgileri hakkında daha fazla bilgi için <xref:System.Xml.XmlTextReader> sınıfı <xref:System.Xml.XmlTextReader.Encoding%2A> özelliğinde <xref:System.Xml.XmlTextReader> sınıfı başvuru belgeleri.</span><span class="sxs-lookup"><span data-stu-id="d1c21-120">For more information about the encoding information provided by the <xref:System.Xml.XmlTextReader> class, see the <xref:System.Xml.XmlTextReader.Encoding%2A> property in the <xref:System.Xml.XmlTextReader> class reference documentation.</span></span>  
  
## <a name="creating-xpathnavigator-objects"></a><span data-ttu-id="d1c21-121">XPathNavigator nesneleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="d1c21-121">Creating XPathNavigator Objects</span></span>  
 <span data-ttu-id="d1c21-122">Bir XML belgesi okuduktan sonra bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi oluşturmak için kullanabileceğiniz bir <xref:System.Xml.XPath.XPathNavigator> seçin, değerlendirmek, gidin ve bazı durumlarda, temel alınan XML verileri düzenlemek için nesne.</span><span class="sxs-lookup"><span data-stu-id="d1c21-122">After you have read an XML document into either an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, you can create an <xref:System.Xml.XPath.XPathNavigator> object to select, evaluate, navigate, and in some cases, edit the underlying XML data.</span></span>  
  
 <span data-ttu-id="d1c21-123">Hem <xref:System.Xml.XPath.XPathDocument> ve <xref:System.Xml.XmlDocument> ayrıca için sınıfları <xref:System.Xml.XmlNode> sınıfı, uygulama <xref:System.Xml.XPath.IXPathNavigable> arabiriminin <xref:System.Xml.XPath?displayProperty=nameWithType> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="d1c21-123">Both the <xref:System.Xml.XPath.XPathDocument> and <xref:System.Xml.XmlDocument> classes, in addition to the <xref:System.Xml.XmlNode> class, implement the <xref:System.Xml.XPath.IXPathNavigable> interface of the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d1c21-124">Sonuç olarak, tüm üç sınıfları sağlar bir <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> döndüren yöntem bir <xref:System.Xml.XPath.XPathNavigator> nesne.</span><span class="sxs-lookup"><span data-stu-id="d1c21-124">As a result, all three classes provide a <xref:System.Xml.XPath.IXPathNavigable.CreateNavigator%2A> method that returns an <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
### <a name="editing-xml-documents-using-the-xpathnavigator-class"></a><span data-ttu-id="d1c21-125">XML belgelerini XPathNavigator sınıfını kullanarak düzenleme</span><span class="sxs-lookup"><span data-stu-id="d1c21-125">Editing XML Documents using the XPathNavigator Class</span></span>  
 <span data-ttu-id="d1c21-126">Ek olarak seçme, değerlendirme ve XML verilerinde gezinme <xref:System.Xml.XPath.XPathNavigator> sınıfı, bazı durumlarda, oluşturduğu nesneye bağlı bir XML belgesi düzenlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1c21-126">In addition to selecting, evaluating, and navigating XML data, the <xref:System.Xml.XPath.XPathNavigator> class can be used to edit an XML document in some cases, based on the object that created it.</span></span>  
  
 <span data-ttu-id="d1c21-127"><xref:System.Xml.XPath.XPathDocument> Sınıfı, salt okunur sırasında <xref:System.Xml.XmlDocument> sınıfıdır düzenlenebilir ve sonuç olarak, <xref:System.Xml.XPath.XPathNavigator> oluşturulan nesneleri bir <xref:System.Xml.XPath.XPathDocument> bağlanırken oluşturulan bir XML belgesi düzenlemek için nesne kullanılamaz bir <xref:System.Xml.XmlDocument> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d1c21-127">The <xref:System.Xml.XPath.XPathDocument> class is read-only while the <xref:System.Xml.XmlDocument> class is editable and as a result, <xref:System.Xml.XPath.XPathNavigator> objects created from an <xref:System.Xml.XPath.XPathDocument> object cannot be used to edit an XML document while those created from an <xref:System.Xml.XmlDocument> object can.</span></span> <span data-ttu-id="d1c21-128"><xref:System.Xml.XPath.XPathDocument> Sınıfı, yalnızca bir XML belgesi okumak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1c21-128">The <xref:System.Xml.XPath.XPathDocument> class should be used to read an XML document only.</span></span> <span data-ttu-id="d1c21-129">Bir XML belgesi düzenlemek ya da tarafından sağlanan ek işlevsellik erişmesi gerektiğinde burada <xref:System.Xml.XmlDocument> olay işlemede gibi bir sınıf <xref:System.Xml.XmlDocument> sınıfı kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d1c21-129">In cases where you need to edit an XML document, or require access to the additional functionality provided by the <xref:System.Xml.XmlDocument> class, like event handling, the <xref:System.Xml.XmlDocument> class should be used.</span></span>  
  
 <span data-ttu-id="d1c21-130"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfını belirtir bir <xref:System.Xml.XPath.XPathNavigator> nesne XML verileri düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1c21-130">The <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class specifies if an <xref:System.Xml.XPath.XPathNavigator> object may edit XML data.</span></span>  
  
 <span data-ttu-id="d1c21-131">Aşağıdaki tabloda değerinin açıklanmıştır <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> her sınıf için özellik.</span><span class="sxs-lookup"><span data-stu-id="d1c21-131">The following table describes the value of the <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property for each class.</span></span>  
  
|<span data-ttu-id="d1c21-132"><xref:System.Xml.XPath.IXPathNavigable> Uygulama</span><span class="sxs-lookup"><span data-stu-id="d1c21-132"><xref:System.Xml.XPath.IXPathNavigable> Implementation</span></span>|<span data-ttu-id="d1c21-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Değer</span><span class="sxs-lookup"><span data-stu-id="d1c21-133"><xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> Value</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Xml.XPath.XPathDocument>|`false`|  
|<xref:System.Xml.XmlDocument>|`true`|  
  
## <a name="see-also"></a><span data-ttu-id="d1c21-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1c21-134">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="d1c21-135">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="d1c21-135">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="d1c21-136">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="d1c21-136">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="d1c21-137">XPathNavigator Kullanarak XML Verilerini Düzenleme</span><span class="sxs-lookup"><span data-stu-id="d1c21-137">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="d1c21-138">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="d1c21-138">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
