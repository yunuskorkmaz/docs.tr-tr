---
title: 'Hizmet: Hatalı Çağrılar'
ms.date: 03/30/2017
ms.assetid: 6da7f100-3f61-4b3c-9409-fe1360829b8a
ms.openlocfilehash: 613de88df8aaa955539a4e9586dacd64e155161e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252939"
---
# <a name="service-calls-faulted"></a><span data-ttu-id="edb34-102">Hizmet: Hatalı Çağrılar</span><span class="sxs-lookup"><span data-stu-id="edb34-102">Service: Calls Faulted</span></span>

<span data-ttu-id="edb34-103">Sayaç adı: Hatalı çağrılar.</span><span class="sxs-lookup"><span data-stu-id="edb34-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="edb34-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edb34-104">Description</span></span>  

 <span data-ttu-id="edb34-105">Bu hizmete hata döndüren çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="edb34-105">Number of calls to this service that have returned faults.</span></span> <span data-ttu-id="edb34-106">Windows Communication Foundation (WCF) uygulamalarında, hizmet yöntemleri SOAP hata iletilerini kullanarak işlem hata bilgilerini iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="edb34-106">In Windows Communication Foundation (WCF) applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="edb34-107">SOAP hataları, bir hizmet işleminin meta verilerinde bulunan ileti türleridir ve bu nedenle, istemcilerinin yürütmesini daha sağlam veya etkileşimli hale getirmek için kullanabileceği bir hata sözleşmesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="edb34-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="edb34-108">SOAP hataları, XML biçiminde istemcilere belirtilediğinden, bunlar çok fazla kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="edb34-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edb34-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edb34-109">See also</span></span>

- [<span data-ttu-id="edb34-110">Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme</span><span class="sxs-lookup"><span data-stu-id="edb34-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
