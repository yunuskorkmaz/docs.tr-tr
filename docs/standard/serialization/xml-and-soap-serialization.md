---
title: XML ve SOAP Serileştirme
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: dcb2ed1703473be582a12f430d2e051d8a420230
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588370"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="10d96-102">XML ve SOAP serileştirmesi</span><span class="sxs-lookup"><span data-stu-id="10d96-102">XML and SOAP serialization</span></span>

<span data-ttu-id="10d96-103">XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini, parametreleri ve dönüş değerlerini belirli bir XML şeması tanım dili (XSD) belgesine uygun bir XML akışına dönüştürür (seri hale getirir).</span><span class="sxs-lookup"><span data-stu-id="10d96-103">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="10d96-104">XML serileştirme, genel özellikler ve depolama ya da taşıma için bir seri biçimine (Bu örnekte XML) dönüştürülen alanları kesin olarak belirlenmiş sınıflarla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="10d96-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="10d96-105">XML açık bir standart olduğu için XML akışı, platformdan bağımsız olarak, gerektiğinde herhangi bir uygulama tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="10d96-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="10d96-106">Örneğin, ASP.NET kullanılarak oluşturulan XML Web Hizmetleri, XML Web <xref:System.Xml.Serialization.XmlSerializer> hizmeti uygulamaları arasında verileri Internet üzerinden veya intranetlerde geçiren XML akışları oluşturmak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="10d96-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="10d96-107">Buna karşılık, seri durumdan çıkarma böyle bir XML akışı alır ve nesneyi yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="10d96-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="10d96-108">XML serileştirme Ayrıca, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="10d96-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="10d96-109">SOAP, özellikle XML kullanan yordam çağrılarını aktarmak için tasarlanan XML tabanlı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="10d96-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="10d96-110">Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="10d96-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="10d96-111">Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="10d96-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="10d96-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10d96-112">See also</span></span>

- [<span data-ttu-id="10d96-113">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="10d96-113">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="10d96-114">[ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="10d96-114">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
