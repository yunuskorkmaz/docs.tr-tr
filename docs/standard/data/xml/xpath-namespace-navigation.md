---
title: XPath Ad Alanı Gezintisi
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: dce7d81d4249cb40c3be6dee4b8bd25951ccb10a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283214"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="53e0d-102">XPath Ad Alanı Gezintisi</span><span class="sxs-lookup"><span data-stu-id="53e0d-102">XPath Namespace Navigation</span></span>
<span data-ttu-id="53e0d-103">XML belgeleriyle XPath sorguları kullanmak için, XML ad alanlarını ve ad alanları tarafından içerilen öğeleri doğru bir şekilde ele almanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="53e0d-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="53e0d-104">Ad alanları, adlar birden fazla bağlamda kullanıldığında oluşabilecek belirsizlikleri önler; Örneğin, ad `ID` BIR XML belgesinin farklı öğeleriyle ilişkili birden fazla tanımlayıcıya başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="53e0d-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="53e0d-105">Ad alanı sözdizimi, bir XML belgesinin öğelerini ayırt eden URI 'Leri, adları ve önekleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="53e0d-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="53e0d-106">Bu konudaki örnekte, ile bir XML belgesinde gezinme içindeki ön eklerin kullanımı gösterilmektedir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="53e0d-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="53e0d-107">Ad alanları ve sözdizimi hakkında daha fazla bilgi için bkz. [XML Files: XML ad alanlarını anlama](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="53e0d-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](https://docs.microsoft.com/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="53e0d-108">Ad alanı bildirimleri</span><span class="sxs-lookup"><span data-stu-id="53e0d-108">Namespace Declarations</span></span>  
 <span data-ttu-id="53e0d-109">Ad alanı bildirimleri, bir örneği kullanılırken bir XML belgesinin öğelerini ayırt edilemez ve adreslenebilir hale getirir <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="53e0d-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="53e0d-110">Ad alanı önekleri ad alanlarını adresleme için kısa bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="53e0d-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="53e0d-111">Ön ekler form tarafından tanımlanır: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` Bu sözdiziminde, "" ön eki, `e` ad alanının biçimsel URI 'si için bir kısaltmadır.</span><span class="sxs-lookup"><span data-stu-id="53e0d-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="53e0d-112">`Body`Öğesini, `Envelope` sözdizimini kullanarak ad alanının bir üyesi olarak tanımlayabilirsiniz: `e:Body` .</span><span class="sxs-lookup"><span data-stu-id="53e0d-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="53e0d-113">Sonraki bölümde gezinti örneğinde olduğu gibi, aşağıdaki XML belgesine başvurulur `response.xml` .</span><span class="sxs-lookup"><span data-stu-id="53e0d-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
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
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="53e0d-114">Ad alanı ön ekine göre gezinti</span><span class="sxs-lookup"><span data-stu-id="53e0d-114">Navigation by Namespace Prefix</span></span>  
 <span data-ttu-id="53e0d-115">Bu bölümdeki kod, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlNamespaceManager> `Search` önceki bölümdeki XML belgesinden öğeyi seçmek için ve nesnelerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="53e0d-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="53e0d-116">Sorgu, `xpath` yoldaki her öğe için ad alanı öneklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="53e0d-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="53e0d-117">Her bir öğeyi içeren ad alanlarının kesin kimliğini belirtmek, yöntemi tarafından öğesine doğru gezinmeyi sağlar `Search` <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> .</span><span class="sxs-lookup"><span data-stu-id="53e0d-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="53e0d-118">Tam nitelikli ad alanları ve adların duyarlığı bir rahatlığından daha fazla.</span><span class="sxs-lookup"><span data-stu-id="53e0d-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="53e0d-119">Belge tanımı ve önceki örneklerde bulunan kod içeren küçük bir deneme, tam olarak nitelenen öğe adları olmayan gezinmenin özel durum oluşturduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="53e0d-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="53e0d-120">Örneğin, öğe tanımı: `<Search xmlns="http://schemas.microsoft.com/v1/Search">` , ve sorgu: öğesinde `xpath = "/s:Envelope/s:Body/Search";` ad alanı öneki olmayan dize `Search` `null` öğesi yerine döner `Search` .</span><span class="sxs-lookup"><span data-stu-id="53e0d-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e0d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53e0d-121">See also</span></span>

- [<span data-ttu-id="53e0d-122">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="53e0d-122">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="53e0d-123">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="53e0d-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
