---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: sertifika edinme (WCF)'
title: 'Nası yapılır: Sertifika Edinme (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 2ca40c9646bbdeb6c29a94966fd24ec00d9b5306
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793707"
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="08c3a-103">Nası yapılır: Sertifika Edinme (WCF)</span><span class="sxs-lookup"><span data-stu-id="08c3a-103">How to: Obtain a Certificate (WCF)</span></span>

<span data-ttu-id="08c3a-104">X. 509.440 sertifikalarını kullanan Windows Communication Foundation (WCF) özelliklerinden herhangi birini kullanmak için öncelikle sertifikaları edinmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="08c3a-104">To use any of the Windows Communication Foundation (WCF) features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="08c3a-105">X. 509.440 sertifikası almak için</span><span class="sxs-lookup"><span data-stu-id="08c3a-105">To obtain an X.509 certificate</span></span>  
  
1. <span data-ttu-id="08c3a-106">Aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="08c3a-106">Choose one of the following:</span></span>  
  
    - <span data-ttu-id="08c3a-107">VeriSign, Inc. bir sertifika yetkilisinden sertifika satın alın.</span><span class="sxs-lookup"><span data-stu-id="08c3a-107">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    - <span data-ttu-id="08c3a-108">Kendi sertifika hizmetinizi kurun ve sertifikaları imzalamak için bir sertifika yetkilisine sahip olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08c3a-108">Set up your own certificate service and have a certification authority sign the certificates.</span></span> <span data-ttu-id="08c3a-109">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 Datacenter Server hepsi ortak anahtar altyapısını (PKI) destekleyen sertifika hizmetlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="08c3a-109">Windows Server 2003, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="08c3a-110">Windows Server 2008 ' de, sertifika yetkilisini yönetmek için [Active Directory Sertifika Hizmetleri](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) rolünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="08c3a-110">In Windows Server 2008, use the [Active Directory Certificate Services](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731564(v=ws.10)) role to manage a certification authority.</span></span>  
  
    - <span data-ttu-id="08c3a-111">Kendi sertifika hizmetinizi kurun ve sertifikalara kaydolmayın.</span><span class="sxs-lookup"><span data-stu-id="08c3a-111">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="08c3a-112">Hangi yaklaşımı kullanırsanız, X. 509.440 sertifikasını içeren SOAP isteğinin alıcısı X. 509.440 sertifikasına güvenmelidir.</span><span class="sxs-lookup"><span data-stu-id="08c3a-112">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="08c3a-113">Yani, sertifika zincirindeki X. 509.440 sertifikası veya veren, güvenilen kişiler sertifika deposunda ve X. 509.440 sertifikasının Güvenilmeyen sertifikalar deposunda olmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="08c3a-113">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c3a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08c3a-114">See also</span></span>

- [<span data-ttu-id="08c3a-115">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="08c3a-115">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="08c3a-116">Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="08c3a-116">How to: Create Temporary Certificates for Use During Development</span></span>](how-to-create-temporary-certificates-for-use-during-development.md)
