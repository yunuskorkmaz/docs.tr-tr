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
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="468fe-102">XML ve SOAP serileştirme</span><span class="sxs-lookup"><span data-stu-id="468fe-102">XML and SOAP serialization</span></span>

<span data-ttu-id="468fe-103">XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini ve yöntemlerin parametrelerini ve dönüş değerlerini belirli bir XML Şema tanım dili (XSD) belgesine uygun bir XML akışına dönüştürür (serileştirir).</span><span class="sxs-lookup"><span data-stu-id="468fe-103">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="468fe-104">XML serileştirme, depolama veya taşıma için seri biçimine (bu durumda XML) dönüştürülen ortak özelliklere ve alanlara sahip güçlü bir şekilde yazılan sınıflara neden olur.</span><span class="sxs-lookup"><span data-stu-id="468fe-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="468fe-105">XML açık bir standart olduğundan, XML akışı platformdan bağımsız olarak gerektiğinde herhangi bir uygulama tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="468fe-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="468fe-106">Örneğin, ASP.NET kullanılarak oluşturulan XML <xref:System.Xml.Serialization.XmlSerializer> Web hizmetleri, Internet'teki veya intranet'lerde XML Web hizmeti uygulamaları arasında veri aktaran XML akışları oluşturmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="468fe-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="468fe-107">Tersine, deserialization böyle bir XML akışı alır ve nesne yi yeniden yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="468fe-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="468fe-108">XML serileştirme, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="468fe-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="468fe-109">SOAP, XML kullanarak yordam çağrılarını taşımak için özel olarak tasarlanmış XML tabanlı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="468fe-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="468fe-110">Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="468fe-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="468fe-111">Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="468fe-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="468fe-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="468fe-112">See also</span></span>

- [<span data-ttu-id="468fe-113">İkili Serileştirme</span><span class="sxs-lookup"><span data-stu-id="468fe-113">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="468fe-114">[ASP.NET ve XML Web Hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="468fe-114">[XML Web Services created using ASP.NET and XML Web Service clients](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
