---
title: XPath Ad Alanı Gezintisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: f35318b1439b762bf7c87cff217ed1787e8d007c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156328"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="3a88d-102">XPath Ad Alanı Gezintisi</span><span class="sxs-lookup"><span data-stu-id="3a88d-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="3a88d-103">XML belgeleriyle XPath sorguları kullanmak için, XML ad alanlarını ve ad alanları tarafından içerilen öğeleri doğru bir şekilde ele almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3a88d-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="3a88d-104">Ad alanları, adlar birden fazla bağlamda kullanıldığında oluşabilecek belirsizlikleri önler; Örneğin, ad `ID` bir XML belgesinin farklı öğeleriyle ilişkili birden fazla tanımlayıcıya başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="3a88d-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="3a88d-105">Ad alanı sözdizimi, bir XML belgesinin öğelerini ayırt eden URI 'Leri, adları ve önekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="3a88d-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="3a88d-106">Bu konudaki örnekte, ile <xref:System.Xml.XPath.XPathNavigator>bir XML belgesinde gezinme içindeki ön eklerin kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3a88d-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="3a88d-107">Ad alanları ve sözdizimi hakkında daha fazla bilgi için bkz. [XML Files: XML ad alanlarını anlama](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="3a88d-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="3a88d-108">Ad alanı bildirimleri</span><span class="sxs-lookup"><span data-stu-id="3a88d-108">Namespace Declarations</span></span>  
 <span data-ttu-id="3a88d-109">Ad alanı bildirimleri, bir örneği kullanılırken bir XML belgesinin öğelerini ayırt edilemez ve adreslenebilir hale getirir <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3a88d-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="3a88d-110">Ad alanı önekleri ad alanlarını adresleme için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a88d-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="3a88d-111">Ön ekler form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Bu sözdiziminde, "`e`" ön eki, ad alanının biçimsel URI 'si için bir kısaltmadır.</span><span class="sxs-lookup"><span data-stu-id="3a88d-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="3a88d-112">`Body` Öğesini, sözdizimini kullanarak `Envelope` ad alanının bir üyesi olarak tanımlayabilirsiniz: `e:Body`.</span><span class="sxs-lookup"><span data-stu-id="3a88d-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="3a88d-113">Sonraki bölümde gezinti örneğinde olduğu gibi `response.xml` , aşağıdaki XML belgesine başvurulur.</span><span class="sxs-lookup"><span data-stu-id="3a88d-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="3a88d-114">Ad alanı ön ekine göre gezinti</span><span class="sxs-lookup"><span data-stu-id="3a88d-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="3a88d-115">Bu bölümdeki kod, bir önceki <xref:System.Xml.XPath.XPathNavigator> bölümdeki <xref:System.Xml.XmlNamespaceManager> XML belgesinden `Search` öğeyi seçmek için ve nesnelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a88d-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="3a88d-116">Sorgu `xpath` , yoldaki her öğe için ad alanı öneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3a88d-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="3a88d-117">Her bir öğeyi içeren ad alanlarının kesin kimliğini belirtmek, `Search` <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemi tarafından öğesine doğru gezinmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3a88d-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="3a88d-118">Tam nitelikli ad alanları ve adların duyarlığı bir rahatlığından daha fazla.</span><span class="sxs-lookup"><span data-stu-id="3a88d-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="3a88d-119">Belge tanımı ve önceki örneklerde bulunan kod içeren küçük bir deneme, tam olarak nitelenen öğe adları olmayan gezinmenin özel durum oluşturduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="3a88d-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="3a88d-120">Örneğin, öğe tanımı: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, ve sorgu: öğesinde ad alanı `xpath = "/s:Envelope/s:Body/Search";` öneki `Search` olmayan dize `null` `Search` öğesi yerine döner.</span><span class="sxs-lookup"><span data-stu-id="3a88d-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a88d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a88d-121">See also</span></span>

- [<span data-ttu-id="3a88d-122">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="3a88d-122">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="3a88d-123">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="3a88d-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
