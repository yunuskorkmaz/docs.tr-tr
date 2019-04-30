---
title: 'Nasıl yapılır: (WCF) bir sertifika alın'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 21e9e0609ed63c4398f2df7ba718f8af17464b0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683642"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="dca25-102">Nasıl yapılır: (WCF) bir sertifika alın</span><span class="sxs-lookup"><span data-stu-id="dca25-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="dca25-103">Windows Communication Foundation (WCF) kullanmak için yalnızca ilk sertifikaları almak, X.509 sertifikaları, özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="dca25-103">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="dca25-104">Bir X.509 sertifikası almak için</span><span class="sxs-lookup"><span data-stu-id="dca25-104">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="dca25-105">Aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="dca25-105">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="dca25-106">VeriSign gibi bir sertifika yetkilisinden bir sertifika satın alın</span><span class="sxs-lookup"><span data-stu-id="dca25-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="dca25-107">Kendi sertifika hizmetini ayarlama ve bir sertifika yetkilisi sertifikaları imzalamak sahip.</span><span class="sxs-lookup"><span data-stu-id="dca25-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="dca25-108">, Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 veri merkezi sunucusu destekleyen ortak anahtar altyapısı (PKI) Sertifika Hizmetleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dca25-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="dca25-109">Windows Server 2008'de kullanmak [Active Directory Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkID=153483) bir sertifika yetkilisi yönetmek için rol.</span><span class="sxs-lookup"><span data-stu-id="dca25-109">In Windows Server 2008, use the [Active Directory Certificate Services](https://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="dca25-110">Kendi sertifika hizmetini ayarlama ve yapmak sahip sertifikaları imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="dca25-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dca25-111">Yaklaşımı, uygulamanız, alıcı X.509 sertifikasını içeren SOAP isteğinin X.509 sertifikası güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="dca25-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="dca25-112">Başka bir deyişle, X.509 sertifika veya sertifika zincirinde bir veren güvenilir kişiler sertifika deposunda olduğunu ve X.509 sertifika güvenilmeyen bir sertifika deposunda değil.</span><span class="sxs-lookup"><span data-stu-id="dca25-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca25-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dca25-113">See also</span></span>

- [<span data-ttu-id="dca25-114">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="dca25-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="dca25-115">Nasıl yapılır: Geliştirme sırasında kullanmak için geçici sertifikalar oluşturma</span><span class="sxs-lookup"><span data-stu-id="dca25-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
