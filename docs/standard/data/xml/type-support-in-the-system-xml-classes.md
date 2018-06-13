---
title: System.Xml sınıflardaki türü desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb47eec7153624b1822b6393bb4a1621b1cd63db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569700"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="d7814-102">System.Xml sınıflardaki türü desteği</span><span class="sxs-lookup"><span data-stu-id="d7814-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="d7814-103">.NET Framework sürüm 2. 0'da, temel XML sınıfları türü destek özellikleri içerecek şekilde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7814-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="d7814-104"><xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, Ve <xref:System.Xml.XPath.XPathNavigator> sınıfları XML Şeması türleri ve ortak dil çalışma zamanı (CLR) türler arasında dönüştürme yeteneği dahil olmak üzere türü destek özellikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d7814-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="d7814-105">.NET Framework sürüm 2.0, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları türü destek özellikleri içerecek şekilde geliştirildi.</span><span class="sxs-lookup"><span data-stu-id="d7814-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
-   <span data-ttu-id="d7814-106"><xref:System.Xml.XmlReader> Ve <xref:System.Xml.XPath.XPathNavigator> sınıflar her içeren bir **SchemaInfo** bir düğümde şema bilgileri döndüren özelliği.</span><span class="sxs-lookup"><span data-stu-id="d7814-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
-   <span data-ttu-id="d7814-107">**ReadContentAs** ve **ReadElementContentAs** ve yöntemlere <xref:System.Xml.XmlReader> sınıfı bir metin değeri okuma ve tek yöntem çağrısı CLR değerinde dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d7814-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
-   <span data-ttu-id="d7814-108"><xref:System.Xml.XmlWriter.WriteValue%2A> Yöntemi <xref:System.Xml.XmlWriter> sınıfı XML'yi yazılırken bu CLR türü bir XML Şeması türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d7814-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
-   <span data-ttu-id="d7814-109">**Değerlerini** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> özellikleri <xref:System.Xml.XPath.XPathNavigator> sınıfı bir düğüm değeri dönün ve tek yöntem çağrısı CLR değerinde dönüştürün.</span><span class="sxs-lookup"><span data-stu-id="d7814-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7814-110">.NET Framework sürüm 1.0 <xref:System.Xml.XmlConvert> sınıfı XML şeması ve CLR türleri arasında dönüştürme için gerekli.</span><span class="sxs-lookup"><span data-stu-id="d7814-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7814-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d7814-111">In This Section</span></span>  
 [<span data-ttu-id="d7814-112">XML Veri Türlerini CLR Türleriyle Eşleme</span><span class="sxs-lookup"><span data-stu-id="d7814-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="d7814-113">CLR türlerine XML veri türlerinin varsayılan eşlemeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d7814-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="d7814-114">XML Tür Desteği Uygulama Notları</span><span class="sxs-lookup"><span data-stu-id="d7814-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="d7814-115">Tür destek uygulama ayrıntılarını bazıları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d7814-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="d7814-116">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d7814-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="d7814-117">Nasıl kullanılacağını açıklar <xref:System.Xml.XmlConvert> XML şeması ve CLR türleri arasında dönüştürme için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d7814-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7814-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d7814-118">Related Sections</span></span>  
 [<span data-ttu-id="d7814-119">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="d7814-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
