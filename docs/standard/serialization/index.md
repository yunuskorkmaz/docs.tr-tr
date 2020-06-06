---
title: Serileştirme-.NET
description: Bu makalede ikili serileştirme, XML ve SOAP serileştirme ve JSON serileştirme dahil .NET serileştirme teknolojileri hakkında bilgi sağlanır.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83377242"
---
# <a name="serialization-in-net"></a><span data-ttu-id="61c3d-103">.NET içinde serileştirme</span><span class="sxs-lookup"><span data-stu-id="61c3d-103">Serialization in .NET</span></span>

<span data-ttu-id="61c3d-104">Serileştirme, bir nesnenin durumunu kalıcı veya taşınan bir biçime dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-104">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="61c3d-105">Serileştirme tamamlayıcısı, bir akışı nesnesine dönüştüren seri hale getirme ' dir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-105">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="61c3d-106">Birlikte, bu süreçler verilerin depolanmasını ve aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="61c3d-106">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="61c3d-107">.NET özellikleri aşağıdaki serileştirme teknolojilerine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="61c3d-107">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="61c3d-108">[İkili serileştirme](binary-serialization.md) , bir uygulamanın farklı etkinleştirmeleri arasında bir nesnenin durumunu korumak için yararlı olan tür aslına uygunluk düzeyini korur.</span><span class="sxs-lookup"><span data-stu-id="61c3d-108">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="61c3d-109">Örneğin, bir nesne panoya serileştirmek tarafından farklı uygulamalar arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61c3d-109">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="61c3d-110">Bir nesneyi bir akışa, diske, belleğe, ağ üzerinden, vb. olarak seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61c3d-110">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="61c3d-111">Uzaktan iletişim serileştirme "değeri tarafından" nesnelerini geçirmek için bir bilgisayar veya uygulama etki alanından diğerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="61c3d-111">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="61c3d-112">[XML ve SOAP serileştirme](xml-and-soap-serialization.md) yalnızca ortak özellikleri ve alanları serileştirir ve tür aslına uygunluk koruması yapmaz.</span><span class="sxs-lookup"><span data-stu-id="61c3d-112">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="61c3d-113">Bu, verileri kullanan uygulamayı kısıtlamadan verileri sağlamak veya kullanmak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="61c3d-113">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="61c3d-114">XML açık bir standart olduğundan, verileri Web genelinde paylaşmak için çekici bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-114">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="61c3d-115">SOAP aynı şekilde bir açık standarttır ve bu da etkileyici bir seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="61c3d-115">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="61c3d-116">[JSON serileştirme](system-text-json-overview.md) yalnızca ortak özellikleri serileştirir ve tür uygunluğa sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-116">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="61c3d-117">JSON, web genelinde veri paylaşımı için çekici bir seçim olan açık bir standarttır.</span><span class="sxs-lookup"><span data-stu-id="61c3d-117">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="61c3d-118">Başvuru</span><span class="sxs-lookup"><span data-stu-id="61c3d-118">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="61c3d-119">Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-119">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="61c3d-120">Nesneleri XML biçimli belge veya akışlara seri hale getirmek için kullanılabilecek sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-120">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="61c3d-121">Nesneleri JSON biçimli belgeler veya akışlara seri hale getirmek için kullanılabilecek sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="61c3d-121">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
