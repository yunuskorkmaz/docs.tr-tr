---
title: "Nası yapılır: Sertifika Edinme (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5dcefa658aec37b9af3c4f9285ec76a0d549b868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="47436-102">Nası yapılır: Sertifika Edinme (WCF)</span><span class="sxs-lookup"><span data-stu-id="47436-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="47436-103">Herhangi birini kullanmak için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] , özelliklerini kullanmak X.509 sertifikalarını, yalnızca ilk sertifikaları edinin.</span><span class="sxs-lookup"><span data-stu-id="47436-103">To use any of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="47436-104">Bir X.509 sertifikası almak için</span><span class="sxs-lookup"><span data-stu-id="47436-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="47436-105">Aşağıdakilerden birini seçin:</span><span class="sxs-lookup"><span data-stu-id="47436-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="47436-106">VeriSign, Inc. gibi bir sertifika yetkilisinden bir sertifika satın alın</span><span class="sxs-lookup"><span data-stu-id="47436-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="47436-107">Kendi sertifika hizmetini kurma ve sertifika imzalama sertifika yetkilisine sahip.</span><span class="sxs-lookup"><span data-stu-id="47436-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="47436-108">, Windows 2000 Server, Windows 2000 Server Datacenter ve Windows 2000 Datacenter Server destekleyen ortak anahtar altyapısı (PKI) Sertifika Hizmetleri içerir.</span><span class="sxs-lookup"><span data-stu-id="47436-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="47436-109">Windows Server 2008'de kullanmak [Active Directory Sertifika Hizmetleri](http://go.microsoft.com/fwlink/?LinkID=153483) bir sertifika yetkilisi yönetmek için rol.</span><span class="sxs-lookup"><span data-stu-id="47436-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="47436-110">Kendi sertifika hizmetini kurma ve yapın sahip Sertifika imzalı değil.</span><span class="sxs-lookup"><span data-stu-id="47436-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="47436-111">Uygulamanız, yaklaşımı X.509 sertifikasını içeren SOAP isteği alıcısı X.509 sertifikası güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="47436-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="47436-112">Bunun anlamı X.509 sertifika veya sertifika zincirinde bir veren güvenilir kişiler sertifika deposunda olduğunu ve X.509 sertifikası Güvenilmeyen Sertifikalar deposunda değil.</span><span class="sxs-lookup"><span data-stu-id="47436-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47436-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47436-113">See Also</span></span>  
 [<span data-ttu-id="47436-114">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="47436-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="47436-115">Nasıl yapılır: Geliştirme Sırasında Kullanmak için Geçici Sertifikalar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="47436-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
