---
title: XSLT parametreleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef57d16c52100398919563205a97205be3c5dd7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570646"
---
# <a name="xslt-parameters"></a><span data-ttu-id="6dc67-102">XSLT parametreleri</span><span class="sxs-lookup"><span data-stu-id="6dc67-102">XSLT Parameters</span></span>
<span data-ttu-id="6dc67-103">XSLT parametreleri eklenir <xref:System.Xml.Xsl.XsltArgumentList> kullanarak <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6dc67-103">XSLT parameters are added to the <xref:System.Xml.Xsl.XsltArgumentList> using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span> <span data-ttu-id="6dc67-104">Bir tam adı ve ad alanı URI'si o anda parametre nesnesi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="6dc67-104">A qualified name and namespace URI are associated with the parameter object at that time.</span></span>  
  
### <a name="to-use-an-xslt-parameter"></a><span data-ttu-id="6dc67-105">XSLT parametresini kullanma</span><span class="sxs-lookup"><span data-stu-id="6dc67-105">To use an XSLT parameter</span></span>  
  
1.  <span data-ttu-id="6dc67-106">Oluşturma bir <xref:System.Xml.Xsl.XsltArgumentList> nesne ve parametresini kullanarak eklemek <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6dc67-106">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the parameter using the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method.</span></span>  
  
2.  <span data-ttu-id="6dc67-107">Parametresi, stil sayfası içinden çağırın.</span><span class="sxs-lookup"><span data-stu-id="6dc67-107">Call the parameter from the style sheet.</span></span>  
  
3.  <span data-ttu-id="6dc67-108">Geçirmek <xref:System.Xml.Xsl.XsltArgumentList> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6dc67-108">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="parameter-types"></a><span data-ttu-id="6dc67-109">Parametre türleri</span><span class="sxs-lookup"><span data-stu-id="6dc67-109">Parameter Types</span></span>  
 <span data-ttu-id="6dc67-110">Parametre nesnesi W3C türüne karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="6dc67-110">The parameter object should correspond to a W3C type.</span></span> <span data-ttu-id="6dc67-111">W3C türü bir XPath türü veya XSLT türü olup ve eşdeğer Microsoft .NET sınıfları (yazın) karşılık gelen W3C türleri aşağıdaki tabloda gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dc67-111">The following table shows the corresponding W3C types, the equivalent Microsoft .NET classes (type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="6dc67-112">W3C türü</span><span class="sxs-lookup"><span data-stu-id="6dc67-112">W3C type</span></span>|<span data-ttu-id="6dc67-113">Eşdeğer .NET sınıfı (tür)</span><span class="sxs-lookup"><span data-stu-id="6dc67-113">Equivalent .NET class (type)</span></span>|<span data-ttu-id="6dc67-114">XPath veya XSLT türü</span><span class="sxs-lookup"><span data-stu-id="6dc67-114">XPath or XSLT type</span></span>|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="6dc67-115">XPath</span><span class="sxs-lookup"><span data-stu-id="6dc67-115">XPath</span></span>|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="6dc67-116">XPath</span><span class="sxs-lookup"><span data-stu-id="6dc67-116">XPath</span></span>|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="6dc67-117">XPath</span><span class="sxs-lookup"><span data-stu-id="6dc67-117">XPath</span></span>|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="6dc67-118">XSLT</span><span class="sxs-lookup"><span data-stu-id="6dc67-118">XSLT</span></span>|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|<span data-ttu-id="6dc67-119">XPath</span><span class="sxs-lookup"><span data-stu-id="6dc67-119">XPath</span></span>|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> <span data-ttu-id="6dc67-120">**XPathNavigator]**</span><span class="sxs-lookup"><span data-stu-id="6dc67-120">**XPathNavigator[]**</span></span>|<span data-ttu-id="6dc67-121">XPath</span><span class="sxs-lookup"><span data-stu-id="6dc67-121">XPath</span></span>|  
  
 <span data-ttu-id="6dc67-122">\* Bu, tek bir düğüm içeren düğüm kümesi eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6dc67-122">\*This is equivalent to a node set that contains a single node.</span></span>  
  
 <span data-ttu-id="6dc67-123">Parametre nesnesi yukarıdaki sınıflarından biri değilse, aşağıdaki kurallara göre dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="6dc67-123">If the parameter object is not one of the above classes, it is converted according to the following rules.</span></span> <span data-ttu-id="6dc67-124">Ortak dil çalışma zamanı (CLR) sayısal türler dönüştürülür <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="6dc67-124">Common language runtime (CLR) numeric types are converted to <xref:System.Double>.</span></span> <span data-ttu-id="6dc67-125"><xref:System.DateTime> Türü için dönüştürülür <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6dc67-125">The <xref:System.DateTime> type is converted to <xref:System.String>.</span></span> <span data-ttu-id="6dc67-126"><xref:System.Xml.XPath.IXPathNavigable> türlerine dönüştürülür <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="6dc67-126"><xref:System.Xml.XPath.IXPathNavigable> types are converted to <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="6dc67-127">**XPathNavigator []** dönüştürülür <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="6dc67-127">**XPathNavigator[]** is converted to <xref:System.Xml.XPath.XPathNodeIterator>.</span></span>  
  
 <span data-ttu-id="6dc67-128">Tüm diğer türleri hata atar.</span><span class="sxs-lookup"><span data-stu-id="6dc67-128">All other types throw an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dc67-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="6dc67-129">Example</span></span>  
 <span data-ttu-id="6dc67-130">Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> hesaplanan tutmak için bir parametre oluşturmak için yöntemi indirim tarih.</span><span class="sxs-lookup"><span data-stu-id="6dc67-130">The following example uses the <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> method to create a parameter to hold calculated discount date.</span></span> <span data-ttu-id="6dc67-131">İndirim tarih sırası 20 gün olarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="6dc67-131">The discount date is calculated to be 20 days from the order date.</span></span>  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a><span data-ttu-id="6dc67-132">Giriş</span><span class="sxs-lookup"><span data-stu-id="6dc67-132">Input</span></span>  
  
##### <a name="orderxml"></a><span data-ttu-id="6dc67-133">Order.XML</span><span class="sxs-lookup"><span data-stu-id="6dc67-133">order.xml</span></span>  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a><span data-ttu-id="6dc67-134">discount.xsl</span><span class="sxs-lookup"><span data-stu-id="6dc67-134">discount.xsl</span></span>  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a><span data-ttu-id="6dc67-135">Çıkış</span><span class="sxs-lookup"><span data-stu-id="6dc67-135">Output</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6dc67-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6dc67-136">See Also</span></span>  
 [<span data-ttu-id="6dc67-137">XSLT Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="6dc67-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)
