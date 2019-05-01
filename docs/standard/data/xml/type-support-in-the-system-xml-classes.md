---
title: System.Xml Sınıflarında Tür Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026893"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="41e92-102">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="41e92-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="41e92-103">.NET Framework sürüm 2. 0'da, çekirdek XML sınıfı türü destek özellikleri içerecek şekilde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="41e92-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="41e92-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları XML Şeması türleri ve ortak dil çalışma zamanı (CLR) türler arasında dönüştürme olanağı dahil olmak üzere türü desteği özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="41e92-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="41e92-105">.NET Framework sürüm 2.0 <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları geliştirilmiş tür desteği özelliklerini dahil etmek için.</span><span class="sxs-lookup"><span data-stu-id="41e92-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="41e92-106"><xref:System.Xml.XmlReader> Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları her bir **adet Schemaınfo** şema bilgileri bir düğümde döndüren özellik.</span><span class="sxs-lookup"><span data-stu-id="41e92-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="41e92-107">**ReadContentAs** ve **ReadElementContentAs** ve yöntemlere <xref:System.Xml.XmlReader> sınıfı bir metin değerini okur ve tek bir yöntem çağrısı bir CLR değere Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="41e92-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="41e92-108"><xref:System.Xml.XmlWriter.WriteValue%2A> Metodunda <xref:System.Xml.XmlWriter> sınıfı XML'yi yazarken bu CLR türü bir XML Şeması türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="41e92-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="41e92-109">**Değerlerini** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özellikleri <xref:System.Xml.XPath.XPathNavigator> sınıfı bir düğüm değer döndürmez ve tek bir yöntem çağrısı bir CLR değere Dönüştür.</span><span class="sxs-lookup"><span data-stu-id="41e92-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41e92-110">.NET Framework sürüm 1.0 <xref:System.Xml.XmlConvert> sınıfı, XML şema ve CLR türleri arasında dönüştürme yapmak gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="41e92-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41e92-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="41e92-111">In This Section</span></span>  
 [<span data-ttu-id="41e92-112">XML Veri Türlerini CLR Türleriyle Eşleme</span><span class="sxs-lookup"><span data-stu-id="41e92-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="41e92-113">Varsayılan eşlemeleri CLR türlerine XML veri türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="41e92-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="41e92-114">XML Tür Desteği Uygulama Notları</span><span class="sxs-lookup"><span data-stu-id="41e92-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="41e92-115">Tür desteği uygulama ayrıntılarının bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="41e92-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="41e92-116">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="41e92-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="41e92-117">Nasıl kullanılacağını açıklar <xref:System.Xml.XmlConvert> XML şeması ve CLR türleri arasında dönüştürme yapmak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="41e92-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41e92-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="41e92-118">Related Sections</span></span>  
 [<span data-ttu-id="41e92-119">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="41e92-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
