---
title: Serileştirme-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053354"
---
# <a name="serialization-in-net"></a><span data-ttu-id="6039e-102">.NET içinde serileştirme</span><span class="sxs-lookup"><span data-stu-id="6039e-102">Serialization in .NET</span></span>

<span data-ttu-id="6039e-103">Serileştirme, bir nesnenin durumunu kalıcı veya taşınan bir biçime dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="6039e-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="6039e-104">Serileştirme tamamlayıcısı, bir akışı nesnesine dönüştüren seri hale getirme ' dir.</span><span class="sxs-lookup"><span data-stu-id="6039e-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="6039e-105">Birlikte, bu süreçler verilerin depolanmasını ve aktarılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="6039e-105">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="6039e-106">.NET özellikleri aşağıdaki serileştirme teknolojilerine sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6039e-106">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="6039e-107">[İkili serileştirme](binary-serialization.md) , bir uygulamanın farklı etkinleştirmeleri arasında bir nesnenin durumunu korumak için yararlı olan tür aslına uygunluk düzeyini korur.</span><span class="sxs-lookup"><span data-stu-id="6039e-107">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="6039e-108">Örneğin, bir nesne panoya serileştirmek tarafından farklı uygulamalar arasında paylaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6039e-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="6039e-109">Bir nesneyi bir akışa, diske, belleğe, ağ üzerinden, vb. olarak seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6039e-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="6039e-110">Uzaktan iletişim serileştirme "değeri tarafından" nesnelerini geçirmek için bir bilgisayar veya uygulama etki alanından diğerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="6039e-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="6039e-111">[XML ve SOAP serileştirme](xml-and-soap-serialization.md) yalnızca ortak özellikleri ve alanları serileştirir ve tür aslına uygunluk koruması yapmaz.</span><span class="sxs-lookup"><span data-stu-id="6039e-111">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="6039e-112">Bu, verileri kullanan uygulamayı kısıtlamadan verileri sağlamak veya kullanmak istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="6039e-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="6039e-113">XML açık bir standart olduğundan, verileri Web genelinde paylaşmak için çekici bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="6039e-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="6039e-114">SOAP aynı şekilde bir açık standarttır ve bu da etkileyici bir seçenek sunar.</span><span class="sxs-lookup"><span data-stu-id="6039e-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="6039e-115">[JSON serileştirme](system-text-json-overview.md) yalnızca ortak özellikleri serileştirir ve tür uygunluğa sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="6039e-115">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="6039e-116">JSON, web genelinde veri paylaşımı için çekici bir seçim olan açık bir standarttır.</span><span class="sxs-lookup"><span data-stu-id="6039e-116">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="6039e-117">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6039e-117">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="6039e-118">Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6039e-118">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="6039e-119">Nesneleri XML biçimli belge veya akışlara seri hale getirmek için kullanılabilecek sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6039e-119">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="6039e-120">Nesneleri JSON biçimli belgeler veya akışlara seri hale getirmek için kullanılabilecek sınıfları içerir.</span><span class="sxs-lookup"><span data-stu-id="6039e-120">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
