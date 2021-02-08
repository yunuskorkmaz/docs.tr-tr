---
description: 'Daha fazla bilgi edinin: XSLT parametreleri'
title: XSLT Parametreleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: 2d6d3b239d3c442e01e71fc943dedde9292cc344
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782526"
---
# <a name="xslt-parameters"></a><span data-ttu-id="94957-103">XSLT Parametreleri</span><span class="sxs-lookup"><span data-stu-id="94957-103">XSLT Parameters</span></span>

<span data-ttu-id="94957-104">XSLT parametreleri yöntemi kullanılarak öğesine eklenir <xref:System.Xml.Xsl.XsltArgumentList> <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="94957-104">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="94957-105">Tam ad ve ad alanı URI 'SI parametre nesnesiyle ilişkili zamanda ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="94957-105">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="94957-106">XSLT parametresi kullanmak için</span><span class="sxs-lookup"><span data-stu-id="94957-106">To use an XSLT parameter</span></span>  
  
1. <span data-ttu-id="94957-107"><xref:System.Xml.Xsl.XsltArgumentList>Yöntemini kullanarak bir nesne oluşturun ve parametresini ekleyin <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> .</span><span class="sxs-lookup"><span data-stu-id="94957-107">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2. <span data-ttu-id="94957-108">Stil sayfasından parametresini çağırın.</span><span class="sxs-lookup"><span data-stu-id="94957-108">Call the parameter from the style sheet.</span></span>  
  
3. <span data-ttu-id="94957-109"><xref:System.Xml.Xsl.XsltArgumentList>Nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirin.</span><span class="sxs-lookup"><span data-stu-id="94957-109">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="94957-110">Parametre Türleri</span><span class="sxs-lookup"><span data-stu-id="94957-110">Parameter Types</span></span>  

 <span data-ttu-id="94957-111">Parameter nesnesi bir W3C türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="94957-111">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="94957-112">Aşağıdaki tabloda karşılık gelen W3C türleri, eşdeğer Microsoft .NET sınıfları (türü) ve W3C türünün bir XPath türü veya XSLT türü olup olmadığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94957-112">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="94957-113">W3C türü</span><span class="sxs-lookup"><span data-stu-id="94957-113">W3C type</span></span>|<span data-ttu-id="94957-114">Eşdeğer .NET sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="94957-114">Equivalent .NET class (type)</span></span>|<span data-ttu-id="94957-115">XPath veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="94957-115">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="94957-116">XPath</span><span class="sxs-lookup"><span data-stu-id="94957-116">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="94957-117">XPath</span><span class="sxs-lookup"><span data-stu-id="94957-117">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="94957-118">XPath</span><span class="sxs-lookup"><span data-stu-id="94957-118">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="94957-119">XSLT</span><span class="sxs-lookup"><span data-stu-id="94957-119">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="94957-120">XPath</span><span class="sxs-lookup"><span data-stu-id="94957-120">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="94957-121">**XPathNavigator []**</span><span class="sxs-lookup"><span data-stu-id="94957-121">**XPathNavigator[]**</span></span>|<span data-ttu-id="94957-122">XPath</span><span class="sxs-lookup"><span data-stu-id="94957-122">XPath</span></span>|  
  
 <span data-ttu-id="94957-123">\* Bu, tek bir düğüm içeren bir düğüm kümesine eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="94957-123">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="94957-124">Parametre nesnesi yukarıdaki sınıflardan biri değilse, aşağıdaki kurallara göre dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="94957-124">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="94957-125">Ortak dil çalışma zamanı (CLR) sayısal türleri öğesine dönüştürülür <xref:System.Double> .</span><span class="sxs-lookup"><span data-stu-id="94957-125">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="94957-126"><xref:System.DateTime>Tür öğesine dönüştürülür <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="94957-126">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="94957-127"><xref:System.Xml.XPath.IXPathNavigable> türler öğesine dönüştürülür <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="94957-127"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="94957-128">**XPathNavigator []** , öğesine dönüştürüldü <xref:System.Xml.XPath.XPathNodeIterator> .</span><span class="sxs-lookup"><span data-stu-id="94957-128">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="94957-129">Diğer tüm türler bir hata oluşturur.</span><span class="sxs-lookup"><span data-stu-id="94957-129">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94957-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="94957-130">Example</span></span>  

 <span data-ttu-id="94957-131">Aşağıdaki örnek, <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan indirim tarihini tutacak bir parametre oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="94957-131">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="94957-132">İndirim tarihi, sipariş tarihinden itibaren 20 gün olacak şekilde hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="94957-132">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="94957-133">Giriş</span><span class="sxs-lookup"><span data-stu-id="94957-133">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="94957-134">order.xml</span><span class="sxs-lookup"><span data-stu-id="94957-134">order.xml</span></span>  

 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="94957-135">Discount. Xsl</span><span class="sxs-lookup"><span data-stu-id="94957-135">discount.xsl</span></span>  

 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="94957-136">Çıktı</span><span class="sxs-lookup"><span data-stu-id="94957-136">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="94957-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94957-137">See also</span></span>

- [<span data-ttu-id="94957-138">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="94957-138">XSLT Transformations</span></span>](xslt-transformations.md)
