---
title: ".NET içinde seri hale getirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab8f86b66e92ea250fbe20e8bcb27e6706302db4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="serialization-in-net"></a><span data-ttu-id="05b1e-102">.NET içinde seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="05b1e-102">Serialization in .NET</span></span>
<span data-ttu-id="05b1e-103">Seri hale getirme kalıcı veya taşınan bir forma bir nesnenin durumu dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="05b1e-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="05b1e-104">Seri hale getirme tamamlama bir akış bir nesnesine dönüştürür seri kaldırma ' dir.</span><span class="sxs-lookup"><span data-stu-id="05b1e-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="05b1e-105">Birlikte, bu işlemlerin kolayca depolanan ve aktarılan veri izin verin.</span><span class="sxs-lookup"><span data-stu-id="05b1e-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="05b1e-106">.NET iki serileştirme teknolojileri özellikleri:</span><span class="sxs-lookup"><span data-stu-id="05b1e-106">.NET features two serialization technologies:</span></span>  
  
-   <span data-ttu-id="05b1e-107">Bir uygulamanın farklı çağrılarını arasında bir nesne durumunu korumak için kullanışlıdır türü uygunluk, ikili serileştirme korur.</span><span class="sxs-lookup"><span data-stu-id="05b1e-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="05b1e-108">Örneğin, bir nesne panoya serileştirmek tarafından farklı uygulamalar arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="05b1e-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="05b1e-109">Nesneyi bir akışa, diske, belleğe, ağ üzerinden seri hale getirmek ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="05b1e-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="05b1e-110">Uzaktan iletişim serileştirme "değeri tarafından" nesnelerini geçirmek için bir bilgisayar veya uygulama etki alanından diğerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="05b1e-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
-   <span data-ttu-id="05b1e-111">XML serileştirme yalnızca ortak özellikler ve alanları serileştirir ve türü kalitesini korumak değil.</span><span class="sxs-lookup"><span data-stu-id="05b1e-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="05b1e-112">Sağlayın veya veriyi kullanan uygulamayı kısıtlamadan veri tüketmek istediğinizde kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="05b1e-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="05b1e-113">XML açık bir standart olduğundan, Web üzerinden veri paylaşımı için çekici bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="05b1e-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="05b1e-114">SOAP benzer şekilde yayınlayabilirsiniz kolaylaştırır açık bir standart olan.</span><span class="sxs-lookup"><span data-stu-id="05b1e-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05b1e-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="05b1e-115">In This Section</span></span>  
[<span data-ttu-id="05b1e-116">Serileştirme Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="05b1e-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="05b1e-117">Bu bölümde bulunan nasıl yapılır konulara bağlantılar listeler.</span><span class="sxs-lookup"><span data-stu-id="05b1e-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="05b1e-118">İkili seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="05b1e-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="05b1e-119">Ortak dil çalışma zamanı ile içerdiği ikili serileştirme mekanizması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05b1e-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="05b1e-120">XML ve SOAP seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="05b1e-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="05b1e-121">Ortak dil çalışma zamanı ile içerdiği XML ve SOAP serileştirme mekanizması açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="05b1e-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="05b1e-122">Seri hale getirme araçları</span><span class="sxs-lookup"><span data-stu-id="05b1e-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="05b1e-123">Bu araçlar serileştirme kod geliştirmelerine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="05b1e-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="05b1e-124">Seri hale getirme örnekleri</span><span class="sxs-lookup"><span data-stu-id="05b1e-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="05b1e-125">Örnekler serileştirme nasıl ekleyebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="05b1e-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="05b1e-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="05b1e-126">Reference</span></span>
<span data-ttu-id="05b1e-127"><xref:System.Runtime.Serialization>Seri hale getirme ve nesneleri seri durumdan çıkarmak için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="05b1e-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="05b1e-128">XML biçimli belgeler veya akışları nesneleri serileştirmek için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="05b1e-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>