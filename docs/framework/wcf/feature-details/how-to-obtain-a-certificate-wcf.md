---
title: 'Nası yapılır: Sertifika Edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 664eb62997123ea248b0b69700b86bf794646d4b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519228"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="94982-102">Nası yapılır: Sertifika Edinme (WCF)</span><span class="sxs-lookup"><span data-stu-id="94982-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="94982-103">Windows Communication Foundation (WCF) kullanmak için yalnızca ilk sertifikaları almak, X.509 sertifikaları, özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94982-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="94982-104">Bir X.509 sertifikası almak için</span><span class="sxs-lookup"><span data-stu-id="94982-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="94982-105">Aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="94982-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="94982-106">VeriSign gibi bir sertifika yetkilisinden bir sertifika satın alın</span><span class="sxs-lookup"><span data-stu-id="94982-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="94982-107">Kendi sertifika hizmetini ayarlama ve bir sertifika yetkilisi sertifikaları imzalamak sahip.</span><span class="sxs-lookup"><span data-stu-id="94982-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="94982-108">, Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 veri merkezi sunucusu destekleyen ortak anahtar altyapısı (PKI) Sertifika Hizmetleri içerir.</span><span class="sxs-lookup"><span data-stu-id="94982-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="94982-109">Windows Server 2008'de kullanmak [Active Directory Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=153483) bir sertifika yetkilisi yönetmek için rol.</span><span class="sxs-lookup"><span data-stu-id="94982-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="94982-110">Kendi sertifika hizmetini ayarlama ve yapmak sahip sertifikaları imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="94982-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="94982-111">Yaklaşımı, uygulamanız, alıcı X.509 sertifikasını içeren SOAP isteğinin X.509 sertifikası güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="94982-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="94982-112">Başka bir deyişle, X.509 sertifika veya sertifika zincirinde bir veren güvenilir kişiler sertifika deposunda olduğunu ve X.509 sertifika güvenilmeyen bir sertifika deposunda değil.</span><span class="sxs-lookup"><span data-stu-id="94982-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94982-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94982-113">See Also</span></span>  
 [<span data-ttu-id="94982-114">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="94982-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="94982-115">Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="94982-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
