---
title: XSLT Parametreleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: cc412042e69a43bbecec9dbe68618e2d307ca793
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709705"
---
# <a name="xslt-parameters"></a><span data-ttu-id="dbba4-102">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="dbba4-102">XSLT Parameters</span></span>
<span data-ttu-id="dbba4-103">XSLT parametreleri <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi kullanılarak öğesine eklenir.</span><span class="sxs-lookup"><span data-stu-id="dbba4-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="dbba4-104">Tam ad ve ad alanı URI 'SI parametre nesnesiyle ilişkili zamanda ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="dbba4-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="dbba4-105">XSLT parametresi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="dbba4-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="dbba4-106"><xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> Yöntemini kullanarak bir <xref:System.Xml.Xsl.XsltArgumentList> nesne oluşturun ve parametresini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="dbba4-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="dbba4-107">Stil sayfasından parametresini çağırın.</span><span class="sxs-lookup"><span data-stu-id="dbba4-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="dbba4-108"><xref:System.Xml.Xsl.XsltArgumentList> Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="dbba4-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="dbba4-109">Parametre Türleri</span><span class="sxs-lookup"><span data-stu-id="dbba4-109">Parameter Types</span></span>  
 <span data-ttu-id="dbba4-110">Parameter nesnesi bir W3C türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="dbba4-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="dbba4-111">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer Microsoft .NET sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dbba4-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="dbba4-112">W3C türü</span><span class="sxs-lookup"><span data-stu-id="dbba4-112">W3C type</span></span>|<span data-ttu-id="dbba4-113">Eşdeğer .NET sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="dbba4-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="dbba4-114">XPath veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="dbba4-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="dbba4-115">XPath</span><span class="sxs-lookup"><span data-stu-id="dbba4-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="dbba4-116">XPath</span><span class="sxs-lookup"><span data-stu-id="dbba4-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="dbba4-117">XPath</span><span class="sxs-lookup"><span data-stu-id="dbba4-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="dbba4-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="dbba4-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="dbba4-119">XPath</span><span class="sxs-lookup"><span data-stu-id="dbba4-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="dbba4-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="dbba4-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="dbba4-121">XPath</span><span class="sxs-lookup"><span data-stu-id="dbba4-121">XPath</span></span>|  
  
 <span data-ttu-id="dbba4-122">\* Bu, tek bir düğüm içeren bir düğüm kümesine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="dbba4-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="dbba4-123">Parametre nesnesi yukarıdaki sınıflardan biri değilse, aşağıdaki kurallara göre dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dbba4-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="dbba4-124">Ortak dil çalışma zamanı (CLR) sayısal türleri öğesine <xref:System.Double>dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dbba4-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="dbba4-125"><xref:System.DateTime> Tür öğesine <xref:System.String>dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dbba4-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="dbba4-126"><xref:System.Xml.XPath.IXPathNavigable>türler öğesine <xref:System.Xml.XPath.XPathNavigator>dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="dbba4-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="dbba4-127">**XPathNavigator []** , öğesine <xref:System.Xml.XPath.XPathNodeIterator>dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="dbba4-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="dbba4-128">Diğer tüm türler bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbba4-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbba4-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbba4-129">Example</span></span>  
 <span data-ttu-id="dbba4-130">Aşağıdaki örnek, hesaplanan indirim <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> tarihini tutacak bir parametre oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbba4-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="dbba4-131">İndirim tarihi, sipariş tarihinden itibaren 20 gün olacak şekilde hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="dbba4-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="dbba4-132">Giriş</span><span class="sxs-lookup"><span data-stu-id="dbba4-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="dbba4-133">Order. xml</span><span class="sxs-lookup"><span data-stu-id="dbba4-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="dbba4-134">Discount. Xsl</span><span class="sxs-lookup"><span data-stu-id="dbba4-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="dbba4-135">Çıktı</span><span class="sxs-lookup"><span data-stu-id="dbba4-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbba4-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbba4-136">See also</span></span>

- [<span data-ttu-id="dbba4-137">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="dbba4-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
