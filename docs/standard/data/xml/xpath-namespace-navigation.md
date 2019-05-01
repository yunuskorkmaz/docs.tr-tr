---
title: XPath Ad Alanı Gezintisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbc45d2c6587f5ff94c5cfbe0251d4b0ebca4231
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026802"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="3ee8a-102">XPath Ad Alanı Gezintisi</span><span class="sxs-lookup"><span data-stu-id="3ee8a-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="3ee8a-103">XPath sorguları ile XML belgeleri kullanmak için doğru adres XML ad alanları ve ad alanları tarafından içerilen öğelerin sahip.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="3ee8a-104">Ad alanları, adları, birden fazla bağlamında kullanıldığında oluşabilecek belirsizlikleri önleyebilir. Örneğin, adı `ID` farklı bir XML belgesi öğelerle ilişkili birden fazla tanımlayıcı bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="3ee8a-105">Namespace sözdizimi URI'ler, adları ve bir XML belgesinin öğelerini ayırt önekler belirtir.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="3ee8a-106">Bu konudaki örnek, bir XML belgesi ile gezinme, ön ekleri kullanımını gösterir <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="3ee8a-107">Ad alanları ve söz dizimi hakkında daha fazla bilgi için bkz: [XML dosyaları: XML ad alanları anlama](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="3ee8a-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="3ee8a-108">Namespace bildirimi</span><span class="sxs-lookup"><span data-stu-id="3ee8a-108">Namespace Declarations</span></span>  
 <span data-ttu-id="3ee8a-109">Namespace bildirimi bir XML belgesinin öğelerini ayrılabilen ve hale adreslenebilir bir örneğini kullanırken <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="3ee8a-110">Namespace ön ekleri, ad alanları ele almak için kısa bir söz dizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="3ee8a-111">Ön ekleri form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Bu sözdizimi ön eki "`e`" ad alanı için biçimsel URI kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="3ee8a-112">Tanımlayabilirsiniz `Body` öğesi bir üyesi olarak `Envelope` sözdizimini kullanarak ad alanı: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="3ee8a-113">Aşağıdaki XML belgesi olarak başvurulan `response.xml` Gezinti örnekte sonraki bölümde yer.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"   
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="3ee8a-114">Gezinti Namespace ön eke göre</span><span class="sxs-lookup"><span data-stu-id="3ee8a-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="3ee8a-115">Bu bölümdeki kod <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.Xml.XmlNamespaceManager> nesnelerin `Search` öğeden bir önceki bölümdeki XML belgesi.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="3ee8a-116">Sorgu `xpath` ad alanı öneklerini her öğe üzerinde yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="3ee8a-117">Her öğe içeren ad alanlarını kesin kimliğini belirterek garantiler doğru gitme `Search` öğe tarafından <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```  
using (XmlReader reader = XmlReader.Create("response.xml"))  
            {  
                XPathDocument doc = new XPathDocument(reader);  
                XPathNavigator nav = doc.CreateNavigator();  
                XmlNamespaceManager nsmgr =  
                         new XmlNamespaceManager(nav.NameTable);  
                nsmgr.AddNamespace("e",   
                         @"http://schemas.xmlsoap.org/soap/envelope/");  
                nsmgr.AddNamespace("s",   
                            @"http://schemas.microsoft.com/v1/Search");  
                nsmgr.AddNamespace("r",   
                   @"http://schemas.microsoft.com/v1/Search/metadata");  
                nsmgr.AddNamespace("i",   
                         @"http://www.w3.org/2001/XMLSchema-instance");  
  
                string xpath = "/e:Envelope/e:Body/s:Search";  
  
                XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
                Console.WriteLine("Element Prefix:" + element.Prefix +   
                           " Local name:" + element.LocalName);  
                Console.WriteLine("Namespace URI: " +   
                            element.NamespaceURI);  
  
            }  
```  
  
 <span data-ttu-id="3ee8a-118">Tam ad alanları ve adlarını niteleme duyarlılık kolaylık sağlamak amacıyla büyük.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="3ee8a-119">Biraz deneme belge tanımı ve kod önceki örneklerde, tam öğe adları olmadan Gezinti istisnalar fırlatıyorsa doğrular.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="3ee8a-120">Örneğin, öğe tanımı: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`ve sorgu: dize `xpath = "/s:Envelope/s:Body/Search";` ad alanı öneki olmadan `Search` öğeyi döndürür `null` yerine `Search` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee8a-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ee8a-121">See also</span></span>

- [<span data-ttu-id="3ee8a-122">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="3ee8a-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3ee8a-123">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="3ee8a-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
