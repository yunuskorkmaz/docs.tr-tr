---
title: 'Nasıl yapılır: Sertifika edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: e720a6742506f6270fda65de12f510c2a6224873
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929185"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="40790-102">Nasıl yapılır: Sertifika edinme (WCF)</span><span class="sxs-lookup"><span data-stu-id="40790-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="40790-103">X. 509.440 sertifikalarını kullanan Windows Communication Foundation (WCF) özelliklerinden herhangi birini kullanmak için öncelikle sertifikaları edinmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="40790-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="40790-104">X. 509.440 sertifikası almak için</span><span class="sxs-lookup"><span data-stu-id="40790-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="40790-105">Aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="40790-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="40790-106">VeriSign, Inc. bir sertifika yetkilisinden sertifika satın alın.</span><span class="sxs-lookup"><span data-stu-id="40790-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="40790-107">Kendi sertifika hizmetinizi kurun ve sertifikaları imzalamak için bir sertifika yetkilisine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="40790-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="40790-108">, Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 Datacenter Server hepsi ortak anahtar altyapısını (PKI) destekleyen sertifika hizmetlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="40790-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="40790-109">Windows Server 2008 ' de, sertifika yetkilisini yönetmek için [Active Directory Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=153483) rolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="40790-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="40790-110">Kendi sertifika hizmetinizi kurun ve sertifikalara kaydolmayın.</span><span class="sxs-lookup"><span data-stu-id="40790-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="40790-111">Hangi yaklaşımı kullanırsanız, X. 509.440 sertifikasını içeren SOAP isteğinin alıcısı X. 509.440 sertifikasına güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="40790-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="40790-112">Yani, sertifika zincirindeki X. 509.440 sertifikası veya veren, güvenilen kişiler sertifika deposunda ve X. 509.440 sertifikasının Güvenilmeyen sertifikalar deposunda olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40790-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40790-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40790-113">See also</span></span>

- [<span data-ttu-id="40790-114">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="40790-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="40790-115">Nasıl yapılır: Geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="40790-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
