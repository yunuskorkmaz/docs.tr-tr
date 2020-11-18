---
title: XSLT Parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: c203e17e327cf64690c2748c7f3a4e74b5306501
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818303"
---
# <a name="xslt-parameters"></a><span data-ttu-id="17fbe-102">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="17fbe-102">XSLT Parameters</span></span>
<span data-ttu-id="17fbe-103">XSLT parametreleri yöntemi kullanılarak öğesine eklenir <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="17fbe-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="17fbe-104">Tam ad ve ad alanı URI 'SI parametre nesnesiyle ilişkili zamanda ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="17fbe-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="17fbe-105">XSLT parametresi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="17fbe-105">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="17fbe-106"><xref:System.Xml.Xsl.XsltArgumentList>Yöntemini kullanarak bir nesne oluşturun ve parametresini ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="17fbe-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="17fbe-107">Stil sayfasından parametresini çağırın.</span><span class="sxs-lookup"><span data-stu-id="17fbe-107">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="17fbe-108"><xref:System.Xml.Xsl.XsltArgumentList>Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="17fbe-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="17fbe-109">Parametre Türleri</span><span class="sxs-lookup"><span data-stu-id="17fbe-109">Parameter Types</span></span>  
 <span data-ttu-id="17fbe-110">Parameter nesnesi bir W3C türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="17fbe-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="17fbe-111">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer Microsoft .NET sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="17fbe-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="17fbe-112">W3C türü</span><span class="sxs-lookup"><span data-stu-id="17fbe-112">W3C type</span></span>|<span data-ttu-id="17fbe-113">Eşdeğer .NET sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="17fbe-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="17fbe-114">XPath veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="17fbe-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="17fbe-115">XPath</span><span class="sxs-lookup"><span data-stu-id="17fbe-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="17fbe-116">XPath</span><span class="sxs-lookup"><span data-stu-id="17fbe-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="17fbe-117">XPath</span><span class="sxs-lookup"><span data-stu-id="17fbe-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="17fbe-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="17fbe-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="17fbe-119">XPath</span><span class="sxs-lookup"><span data-stu-id="17fbe-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="17fbe-120">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="17fbe-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="17fbe-121">XPath</span><span class="sxs-lookup"><span data-stu-id="17fbe-121">XPath</span></span>|  
  
 <span data-ttu-id="17fbe-122">\* Bu, tek bir düğüm içeren bir düğüm kümesine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="17fbe-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="17fbe-123">Parametre nesnesi yukarıdaki sınıflardan biri değilse, aşağıdaki kurallara göre dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="17fbe-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="17fbe-124">Ortak dil çalışma zamanı (CLR) sayısal türleri öğesine dönüştürülür <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="17fbe-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="17fbe-125"><xref:System.DateTime>Tür öğesine dönüştürülür <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="17fbe-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="17fbe-126"><xref:System.Xml.XPath.IXPathNavigable> türler öğesine dönüştürülür <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="17fbe-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="17fbe-127">**XPathNavigator []** , öğesine dönüştürüldü <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="17fbe-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="17fbe-128">Diğer tüm türler bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="17fbe-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17fbe-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="17fbe-129">Example</span></span>  
 <span data-ttu-id="17fbe-130">Aşağıdaki örnek, <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan indirim tarihini tutacak bir parametre oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="17fbe-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="17fbe-131">İndirim tarihi, sipariş tarihinden itibaren 20 gün olacak şekilde hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="17fbe-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="17fbe-132">Giriş</span><span class="sxs-lookup"><span data-stu-id="17fbe-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="17fbe-133">order.xml</span><span class="sxs-lookup"><span data-stu-id="17fbe-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="17fbe-134">Discount. Xsl</span><span class="sxs-lookup"><span data-stu-id="17fbe-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="17fbe-135">Çıkış</span><span class="sxs-lookup"><span data-stu-id="17fbe-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="17fbe-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17fbe-136">See also</span></span>

- [<span data-ttu-id="17fbe-137">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="17fbe-137">XSLT Transformations</span></span>](xslt-transformations.md)
