---
title: XPathNavigator kullanarak XML verilerini düzenleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b1f91616-3115-4264-9821-c66589d11d11
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5361ef036d91435b674a1637ac8c2a9a757bf8ab
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367766"
---
# <a name="editing-xml-data-using-xpathnavigator"></a><span data-ttu-id="0ece1-102">XPathNavigator kullanarak XML verilerini düzenleme</span><span class="sxs-lookup"><span data-stu-id="0ece1-102">Editing XML Data using XPathNavigator</span></span>
<span data-ttu-id="0ece1-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı eklemek, değiştirmek ve düğüm kaldırmak için yöntemler sağlar ve değerlerinden bir XML belgesi içinde barındırılan bir <xref:System.Xml.XmlDocument> nesne.</span><span class="sxs-lookup"><span data-stu-id="0ece1-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert, modify and remove nodes and values from an XML document contained in an <xref:System.Xml.XmlDocument> object.</span></span> <span data-ttu-id="0ece1-104">Bu yöntemlerin herhangi biriyle eklemek, değiştirmek ve düğümleri ve değerleri kaldırmak üzere kullanmak için <xref:System.Xml.XPath.XPathNavigator> nesne olmalıdır düzenlenemez, diğer bir deyişle, kendi <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği true olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ece1-104">In order to use any of these methods to insert, modify, and remove nodes and values, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be true.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ece1-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0ece1-105">In This Section</span></span>  
 [<span data-ttu-id="0ece1-106">XPathNavigator Kullanarak XML Verileri Ekleme</span><span class="sxs-lookup"><span data-stu-id="0ece1-106">Insert XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="0ece1-107">Eşdüzey, alt, öznitelik düğümleri ve değerleri için nasıl ekleneceğini açıklar bir <xref:System.Xml.XmlDocument> kullanarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0ece1-107">Describes how to insert sibling, child, attribute nodes and values in to an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="0ece1-108">XPathNavigator Kullanarak XML Verilerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0ece1-108">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="0ece1-109">Düğümleri değiştirmeyi açıklar ve değerler bir <xref:System.Xml.XmlDocument> kullanarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0ece1-109">Describes how to modify nodes and values in an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="0ece1-110">XPathNavigator Kullanarak XML Verilerini Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0ece1-110">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="0ece1-111">Düğümleri kaldırmayı açıklar ve değerlerini bir <xref:System.Xml.XmlDocument> kullanarak nesne <xref:System.Xml.XPath.XPathNavigator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0ece1-111">Describes how to remove nodes and values from an <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ece1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ece1-112">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="0ece1-113">XPath Veri Modelini Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="0ece1-113">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="0ece1-114">XPathDocument ve XmlDocument Kullanarak XML Verilerini Okuma</span><span class="sxs-lookup"><span data-stu-id="0ece1-114">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
- [<span data-ttu-id="0ece1-115">XPathNavigator Kullanarak XML Verileri Seçme, Değerlendirme ve Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="0ece1-115">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="0ece1-116">XPathNavigator Kullanarak XML Verilerine Erişme</span><span class="sxs-lookup"><span data-stu-id="0ece1-116">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)  
- [<span data-ttu-id="0ece1-117">XPathNavigator Kullanarak Şema Doğrulama</span><span class="sxs-lookup"><span data-stu-id="0ece1-117">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
