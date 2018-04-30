---
title: 'Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29637ea7f0a1e533a6735ebfa6f428fe20039e48
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a><span data-ttu-id="07e95-102">Nasıl yapılır: İmzaları Doğrulamak için Kullanılan Sertifika Yetkilendirme Sertifika Zincirini Belirtme (WCF)</span><span class="sxs-lookup"><span data-stu-id="07e95-102">How to: Specify the Certificate Authority Certificate Chain Used to Verify Signatures (WCF)</span></span>
<span data-ttu-id="07e95-103">Zaman [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] varsayılan doğrular X.509 sertifikası güvenilen bir sertifika yetkilisi tarafından verilmiş bir X.509 sertifikası ile imzalanmış bir SOAP iletisi alır.</span><span class="sxs-lookup"><span data-stu-id="07e95-103">When [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] receives a SOAP message signed using an X.509 certificate, by default it verifies that the X.509 certificate was issued by a trusted certification authority.</span></span> <span data-ttu-id="07e95-104">Bu sertifika deposunda bakarak ve sertifika, sertifika yetkilisi olarak belirlendiyse için güvenilir belirleme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="07e95-104">This is done by looking in a certificate store and determining if the certificate for that certification authority has been designated as trusted.</span></span> <span data-ttu-id="07e95-105">Sırayla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bunun belirlenmesi için sertifika yetkilendirme sertifika zincirini doğru sertifika depolama alanına yüklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="07e95-105">In order for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to make this determination, the certification authority certificate chain must be installed in the correct certificate store.</span></span>  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a><span data-ttu-id="07e95-106">Bir sertifika yetkilendirme sertifika zincirini yüklemek için</span><span class="sxs-lookup"><span data-stu-id="07e95-106">To install a certification authority certificate chain</span></span>  
  
-   <span data-ttu-id="07e95-107">SOAP ileti alıcısı X.509 sertifikaları veren güven amaçlayan her sertifika yetkilisi için yükleme sertifikanın sertifika yetkilisi sertifikası zincirine depolamak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikaları almak için yapılandırılmış Kaynak.</span><span class="sxs-lookup"><span data-stu-id="07e95-107">For each certification authority that a SOAP message recipient intends to trust X.509 certificates issued from, install the certification authority certificate chain into the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is configured to retrieve X.509 certificates from.</span></span>  
  
     <span data-ttu-id="07e95-108">Örneğin, bir SOAP iletisi alıcı Microsoft tarafından verilen X.509 sertifikalarının güvenmeyi çalışırsa, sertifika yetkilendirme sertifika zincirini Microsoft Sertifika yüklenmelidir için depolanacak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikalarını aramak için ayarlama Kaynak.</span><span class="sxs-lookup"><span data-stu-id="07e95-108">For instance, if a SOAP message recipient intends to trust X.509 certificates issued by Microsoft, the certification authority certificate chain for Microsoft must be installed in the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is set up to look for X.509 certificates from.</span></span> <span data-ttu-id="07e95-109">Sertifika deposunda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] X.509 sertifikalarını kod veya yapılandırma belirtilen için arar.</span><span class="sxs-lookup"><span data-stu-id="07e95-109">The certificate store in which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] looks for X.509 certificates can be specified in code or configuration.</span></span> <span data-ttu-id="07e95-110">Örneğin, bu kodu kullanarak belirtilebilir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi ya da dahil olmak üzere birkaç şekilde yapılandırmasında [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="07e95-110">For example, this can be specified in code using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method or in configuration a few ways, including the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span></span>  
  
     <span data-ttu-id="07e95-111">Varsayılan Sertifika zincirleri güvenilen sertifika yetkilileri için bir dizi Windows birlikte olduğundan, tüm sertifika yetkilileri sertifika zinciri yüklemek gerekli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="07e95-111">Because Windows ships with a set of default certificate chains for trusted certificate authorities, it may not be necessary to install the certificate chain for all certificate authorities.</span></span>  
  
    1.  <span data-ttu-id="07e95-112">Sertifika Yetkilendirme sertifika zincirini verin.</span><span class="sxs-lookup"><span data-stu-id="07e95-112">Export the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="07e95-113">Tam olarak bunun nasıl yapılacağı sertifika yetkilisinde bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="07e95-113">Exactly how this is done depends on the certification authority.</span></span> <span data-ttu-id="07e95-114">Sertifika yetkilisi Microsoft Sertifika Hizmetleri çalıştırılıyorsa seçin **bir CA sertifikası, sertifika zinciri veya CRL indir**ve ardından **CA sertifikasını indir**.</span><span class="sxs-lookup"><span data-stu-id="07e95-114">If the certification authority is running Microsoft Certificate Services, select **Download a CA certificate, certificate chain, or CRL**, and then choose **Download CA certificate**.</span></span>  
  
    2.  <span data-ttu-id="07e95-115">Sertifika Yetkilendirme sertifika zincirini içeri aktarın.</span><span class="sxs-lookup"><span data-stu-id="07e95-115">Import the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="07e95-116">Microsoft Yönetim Konsolu (MMC)'da, Sertifikalar ek bileşenini açın.</span><span class="sxs-lookup"><span data-stu-id="07e95-116">In the Microsoft Management Console (MMC), open the Certificates snap-in.</span></span> <span data-ttu-id="07e95-117">Sertifika için depolama [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] seçin, X.509 sertifikaları almak için yapılandırılmış **güvenilen kök** **sertifika yetkilileri**klasör.</span><span class="sxs-lookup"><span data-stu-id="07e95-117">For the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is configured to retrieve X.509 certificates from, select the **Trusted Root** **Certification Authorities**folder.</span></span> <span data-ttu-id="07e95-118">Altında **güvenilen kök sertifika yetkilileri** klasörünü sağ tıklatın **sertifikaları**klasörünü **tüm görevler**ve ardından **alma** .</span><span class="sxs-lookup"><span data-stu-id="07e95-118">Under the **Trusted Root Certification Authorities** folder, right-click the **Certificates**folder, point to **All Tasks**, and then click **Import**.</span></span> <span data-ttu-id="07e95-119">Adımda dışarı dosyası sağlamanız bir.</span><span class="sxs-lookup"><span data-stu-id="07e95-119">Provide the file exported in step a.</span></span>  
  
         <span data-ttu-id="07e95-120">Sertifikalar ek bileşenini MMC ile kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="07e95-120">For more information about using the Certificates snap-in with MMC, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e95-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07e95-121">See Also</span></span>  
 [<span data-ttu-id="07e95-122">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="07e95-122">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
