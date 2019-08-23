---
title: System.Xml Sınıflarında Tür Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954ff12ae1ac8b4d601c35fcd76ea35b2bb3acbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939445"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="f90d5-102">System.Xml Sınıflarında Tür Desteği</span><span class="sxs-lookup"><span data-stu-id="f90d5-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="f90d5-103">.NET Framework sürüm 2,0 ' de, çekirdek XML sınıfları tür desteği özelliklerini içerecek şekilde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f90d5-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="f90d5-104"><xref:System.Xml.XmlReader>, Vesınıfları<xref:System.Xml.XPath.XPathNavigator> , XML şema türleri ve ortak dil çalışma zamanı (CLR) türleri arasında dönüştürme özelliği de dahil olmak üzere tür desteği özelliklerini içerir. <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="f90d5-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="f90d5-105">.NET Framework sürüm 2,0 ' <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>de,, ve <xref:System.Xml.XPath.XPathNavigator> sınıfları tür desteği özelliklerini içerecek şekilde geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f90d5-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="f90d5-106"><xref:System.Xml.XmlReader> Ve<xref:System.Xml.XPath.XPathNavigator> sınıfları, bir düğümdeki şema bilgilerini döndüren bir **fermainınfo** özelliği içerir.</span><span class="sxs-lookup"><span data-stu-id="f90d5-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="f90d5-107">**ReadContentAs** ve **ReadElementContentAs** ve <xref:System.Xml.XmlReader> sınıfındaki Yöntemler bir metin değerini okur ve tek bir yöntem çağrısında bir CLR değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f90d5-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="f90d5-108"><xref:System.Xml.XmlWriter> Sınıfındaki yöntemi, <xref:System.Xml.XmlWriter.WriteValue%2A> XML 'yi yazarken bir clr türünü bir XML şema türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f90d5-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="f90d5-109"><xref:System.Xml.XPath.XPathNavigator> Sınıftaki **ValueAs** ve <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> Özellikler bir düğüm değeri döndürür ve tek bir yöntem çağrısında bir CLR değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f90d5-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f90d5-110">.NET Framework sürüm 1,0 ' de, <xref:System.Xml.XmlConvert> XML şeması ve clr türleri arasında dönüştürme yapmak için sınıf gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="f90d5-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f90d5-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f90d5-111">In This Section</span></span>  
 [<span data-ttu-id="f90d5-112">XML Veri Türlerini CLR Türleriyle Eşleme</span><span class="sxs-lookup"><span data-stu-id="f90d5-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="f90d5-113">XML veri türlerinin CLR türlerine varsayılan eşlemelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f90d5-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="f90d5-114">XML Tür Desteği Uygulama Notları</span><span class="sxs-lookup"><span data-stu-id="f90d5-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="f90d5-115">Bazı tür destek uygulama ayrıntılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f90d5-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="f90d5-116">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="f90d5-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="f90d5-117">XML şeması ve clr türleri <xref:System.Xml.XmlConvert> arasında dönüştürme yapmak için sınıfının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f90d5-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f90d5-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f90d5-118">Related Sections</span></span>  
 [<span data-ttu-id="f90d5-119">XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="f90d5-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
