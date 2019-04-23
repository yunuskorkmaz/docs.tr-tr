---
title: XSLT Parametreleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e76e0f35dd95c34d3a6fc81c2f6f3504591387cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306323"
---
# <a name="xslt-parameters"></a><span data-ttu-id="ab83f-102">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="ab83f-102">XSLT Parameters</span></span>
<span data-ttu-id="ab83f-103">XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab83f-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="ab83f-104">Bir tam adı ve ad alanı URI o anda parametresi nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="ab83f-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="ab83f-105">XSLT parametresini kullanma</span><span class="sxs-lookup"><span data-stu-id="ab83f-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="ab83f-106">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve parametresini kullanarak ekleme <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab83f-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="ab83f-107">Parametresi, stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="ab83f-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="ab83f-108">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab83f-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="ab83f-109">Parametre türleri</span><span class="sxs-lookup"><span data-stu-id="ab83f-109">Parameter Types</span></span>  
 <span data-ttu-id="ab83f-110">Parametre nesnesine W3C türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="ab83f-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="ab83f-111">Eşdeğer Microsoft .NET sınıfları (tür), aşağıdaki tablo W3C türleri karşılık gelen gösterir ve W3C türün bir XPath türü veya XSLT türü olup.</span><span class="sxs-lookup"><span data-stu-id="ab83f-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="ab83f-112">W3C türü</span><span class="sxs-lookup"><span data-stu-id="ab83f-112">W3C type</span></span>|<span data-ttu-id="ab83f-113">Eşdeğeri .NET sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="ab83f-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="ab83f-114">XPath veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="ab83f-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="ab83f-115">XPath</span><span class="sxs-lookup"><span data-stu-id="ab83f-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="ab83f-116">XPath</span><span class="sxs-lookup"><span data-stu-id="ab83f-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="ab83f-117">XPath</span><span class="sxs-lookup"><span data-stu-id="ab83f-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="ab83f-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="ab83f-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="ab83f-119">XPath</span><span class="sxs-lookup"><span data-stu-id="ab83f-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="ab83f-120">**XPathNavigator]**</span><span class="sxs-lookup"><span data-stu-id="ab83f-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="ab83f-121">XPath</span><span class="sxs-lookup"><span data-stu-id="ab83f-121">XPath</span></span>|  
  
 <span data-ttu-id="ab83f-122">\* Bu, tek bir düğüm içeren bir düğüm kümesi olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ab83f-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="ab83f-123">Parametre nesnesine yukarıdaki sınıflardan biri değilse, aşağıdaki kurallara göre dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ab83f-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="ab83f-124">Ortak dil çalışma zamanı (CLR) sayısal türleri dönüştürülür <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="ab83f-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="ab83f-125"><xref:System.DateTime> Türüne dönüştürülür <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="ab83f-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="ab83f-126"><xref:System.Xml.XPath.IXPathNavigable> türleri dönüştürülür <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="ab83f-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="ab83f-127">**XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="ab83f-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="ab83f-128">Diğer tüm türlerin bir hata atar.</span><span class="sxs-lookup"><span data-stu-id="ab83f-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab83f-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab83f-129">Example</span></span>  
 <span data-ttu-id="ab83f-130">Aşağıdaki örnekte <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan tutmak için bir parametre yöntemini indirim tarih.</span><span class="sxs-lookup"><span data-stu-id="ab83f-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="ab83f-131">İndirimi tarihini, sipariş tarihi 20 gün olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="ab83f-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="ab83f-132">Giriş</span><span class="sxs-lookup"><span data-stu-id="ab83f-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="ab83f-133">Order.XML</span><span class="sxs-lookup"><span data-stu-id="ab83f-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="ab83f-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="ab83f-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="ab83f-135">Çıkış</span><span class="sxs-lookup"><span data-stu-id="ab83f-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab83f-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab83f-136">See also</span></span>

- [<span data-ttu-id="ab83f-137">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="ab83f-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
