---
title: XPath Namespace gezinme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8cc8d1f031b3f00cdf2b698514220c25c9fec7be
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="f1808-102">XPath Namespace gezinme</span><span class="sxs-lookup"><span data-stu-id="f1808-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="f1808-103">XPath sorguları XML belgeleri ile kullanmak için doğru adres XML ad alanları ve ad alanları tarafından bulunan öğeleri olması.</span><span class="sxs-lookup"><span data-stu-id="f1808-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="f1808-104">Ad alanları adları birden fazla bağlamında kullanıldığında oluşabilecek belirsizlikleri önleyebilir. Örneğin, adı `ID` farklı bir XML belgesi öğelerle ilişkili birden fazla tanımlayıcısına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="f1808-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="f1808-105">Namespace sözdizimi URI, adları ve bir XML belgesi öğelerini ayırt öneklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f1808-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="f1808-106">Bu konudaki örnek bir XML belgesi gezinme içinde önekleri kullanımını gösteren <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f1808-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="f1808-107">Ad alanları ve sözdizimi hakkında daha fazla bilgi için bkz: [anlama XML ad alanları](https://msdn.microsoft.com/library/aa468565.aspx).</span><span class="sxs-lookup"><span data-stu-id="f1808-107">For more information about namespaces and syntax, see [Understanding XML Namespaces](https://msdn.microsoft.com/library/aa468565.aspx).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="f1808-108">Namespace bildirimi</span><span class="sxs-lookup"><span data-stu-id="f1808-108">Namespace Declarations</span></span>  
 <span data-ttu-id="f1808-109">Namespace bildirimi bir XML belgesi öğelerini ayrılabilen ve olun adreslenebilir örneğini kullanırken <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="f1808-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="f1808-110">Namespace önekleri ad alanları adreslemek için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1808-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="f1808-111">Önekleri form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` bu sözdiziminde öneki "`e`" ad alanı resmi URI'sini ifadesinin kısaltmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f1808-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="f1808-112">Tanımlayabilirsiniz `Body` öğesi bir üyesi olarak `Envelope` sözdizimini kullanarak ad alanı: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="f1808-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="f1808-113">Aşağıdaki XML belgesi olarak başvurulan `response.xml` sonraki bölümde Gezinti örnekte.</span><span class="sxs-lookup"><span data-stu-id="f1808-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="f1808-114">Namespace ön eke göre gezinme</span><span class="sxs-lookup"><span data-stu-id="f1808-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="f1808-115">Bu bölümdeki kod kullanır <xref:System.Xml.XPath.XPathNavigator> ve <xref:System.Xml.XmlNamespaceManager> seçmek için nesneleri `Search` önceki bölümdeki XML belgesinden öğesi.</span><span class="sxs-lookup"><span data-stu-id="f1808-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="f1808-116">Sorgu `xpath` ad alanı öneklerini her öğe üzerinde yolu içerir.</span><span class="sxs-lookup"><span data-stu-id="f1808-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="f1808-117">Her öğe içeren ad alanları kesin kimliğini belirten doğru gezinme sağlar `Search` öğesi tarafından <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f1808-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="f1808-118">Tam ad alanları ve adları uygun duyarlık kolaylık sağlamak amacıyla büyük.</span><span class="sxs-lookup"><span data-stu-id="f1808-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="f1808-119">Küçük bir deneme belge tanımı ve önceki örnek kodda Gezinti tam öğe adları olmadan özel durumları oluşturur doğrular.</span><span class="sxs-lookup"><span data-stu-id="f1808-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="f1808-120">Örneğin, öğe tanımında: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`ve sorgu: dize `xpath = "/s:Envelope/s:Body/Search";` ad alanı öneki olmadan `Search` öğesi döndürür `null` yerine `Search` öğesi.</span><span class="sxs-lookup"><span data-stu-id="f1808-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1808-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1808-121">See Also</span></span>  
 [<span data-ttu-id="f1808-122">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="f1808-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="f1808-123">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="f1808-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
