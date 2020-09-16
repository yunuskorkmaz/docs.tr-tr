---
title: XML ve SOAP Serileştirme
description: Bu genel bakış, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için kullanılabilen XML serileştirmesini açıklar.
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: f7ad7732f929ac3599942c5440b173ea226cca87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544992"
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="4514d-103">XML ve SOAP serileştirmesi</span><span class="sxs-lookup"><span data-stu-id="4514d-103">XML and SOAP serialization</span></span>

<span data-ttu-id="4514d-104">XML serileştirme, bir nesnenin ortak alanlarını ve özelliklerini, parametreleri ve dönüş değerlerini belirli bir XML şeması tanım dili (XSD) belgesine uygun bir XML akışına dönüştürür (seri hale getirir).</span><span class="sxs-lookup"><span data-stu-id="4514d-104">XML serialization converts (serializes) the public fields and properties of an object, and the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="4514d-105">XML serileştirme, genel özellikler ve depolama ya da taşıma için bir seri biçimine (Bu örnekte XML) dönüştürülen alanları kesin olarak belirlenmiş sınıflarla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="4514d-105">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>

<span data-ttu-id="4514d-106">XML açık bir standart olduğu için XML akışı, platformdan bağımsız olarak, gerektiğinde herhangi bir uygulama tarafından işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="4514d-106">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="4514d-107">Örneğin, ASP.NET kullanılarak oluşturulan XML Web Hizmetleri, XML <xref:System.Xml.Serialization.XmlSerializer> Web hizmeti uygulamaları arasında verileri Internet üzerinden veya intranetlerde GEÇIREN XML akışları oluşturmak için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4514d-107">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="4514d-108">Buna karşılık, seri durumdan çıkarma böyle bir XML akışı alır ve nesneyi yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4514d-108">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>

<span data-ttu-id="4514d-109">XML serileştirme Ayrıca, nesneleri SOAP belirtimine uygun XML akışlarına seri hale getirmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4514d-109">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="4514d-110">SOAP, özellikle XML kullanan yordam çağrılarını aktarmak için tasarlanan XML tabanlı bir protokoldür.</span><span class="sxs-lookup"><span data-stu-id="4514d-110">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>

<span data-ttu-id="4514d-111">Serileştirmek veya seri durumdan nesneleri için kullanmak <xref:System.Xml.Serialization.XmlSerializer> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4514d-111">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="4514d-112">Serileştirilecek sınıflar oluşturmak için XML şema tanımı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="4514d-112">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="4514d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4514d-113">See also</span></span>

- [<span data-ttu-id="4514d-114">İkili serileştirme</span><span class="sxs-lookup"><span data-stu-id="4514d-114">Binary Serialization</span></span>](binary-serialization.md)
- <span data-ttu-id="4514d-115">[ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4514d-115">[XML Web Services created using ASP.NET and XML Web Service clients](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))</span></span>
