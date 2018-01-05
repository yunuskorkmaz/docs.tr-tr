---
title: "HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="e2e11-102">HTTPS, TCP üzerinden SSL ve SOAP Güvenliği Arasındaki Sertifika Doğrulama Farkları</span><span class="sxs-lookup"><span data-stu-id="e2e11-102">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>
<span data-ttu-id="e2e11-103">Sertifikaları kullanabilirsiniz [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] HTTP (HTTPS) veya TCP üzerinden Aktarım Katmanı Güvenliği (TLS) yanı sıra ileti katmanlı (SOAP) güvenlik ile.</span><span class="sxs-lookup"><span data-stu-id="e2e11-103">You can use certificates in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="e2e11-104">Bu konuda bu tür sertifikalar doğrulanır farklılıklar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e2e11-104">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="e2e11-105">HTTPS istemci sertifikalarının doğrulama</span><span class="sxs-lookup"><span data-stu-id="e2e11-105">Validation of HTTPS Client Certificates</span></span>  
 <span data-ttu-id="e2e11-106">Bir istemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, bir hizmetin kimliğini istemcinin kullandığı sertifika zinciri güven desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2e11-106">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="e2e11-107">Diğer bir deyişle, güvenilen kök sertifika yetkilisine zincirleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2e11-107">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="e2e11-108">Değilse, HTTP katman geçirirse bir <xref:System.Net.WebException> iletiyle "uzak sunucusu bir hata döndürdü: (403) Yasak."</span><span class="sxs-lookup"><span data-stu-id="e2e11-108">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e2e11-109">Bu özel durum olarak ortaya çıkarır bir <xref:System.ServiceModel.Security.MessageSecurityException>.</span><span class="sxs-lookup"><span data-stu-id="e2e11-109"> surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="e2e11-110">HTTPS hizmet sertifika doğrulama</span><span class="sxs-lookup"><span data-stu-id="e2e11-110">Validation of HTTPS Service Certificates</span></span>  
 <span data-ttu-id="e2e11-111">Bir istemci ve hizmet arasında iletişim kurmak için HTTPS kullanırken, sunucu kimlik doğrulamasını sertifika zinciri güven varsayılan olarak desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2e11-111">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="e2e11-112">Diğer bir deyişle, güvenilen kök sertifika yetkilisine zincirleme gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2e11-112">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="e2e11-113">Çevrimiçi Denetimsiz sertifikanın iptal edilmediğini görmek için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e2e11-113">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="e2e11-114">Kaydederek bu davranışı geçersiz kılabilirsiniz bir <xref:System.Net.Security.RemoteCertificateValidationCallback> aşağıdaki kodda gösterildiği gibi geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="e2e11-114">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="e2e11-115">Burada imza için `ValidateServerCertificate` aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e2e11-115">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="e2e11-116">Uygulama `ValidateServerCertificate` istemci uygulama geliştiricisi hizmet sertifikasını doğrulamak üzere gerekli uymak açısından gerekli olduğunu, denetimleri gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2e11-116">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="e2e11-117">TCP veya SOAP güvenliği üzerinden SSL istemci sertifikalarının doğrulama</span><span class="sxs-lookup"><span data-stu-id="e2e11-117">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  
 <span data-ttu-id="e2e11-118">Ne zaman Güvenli Yuva Katmanı (SSL) kullanarak TCP veya (SOAP) ileti güvenliği, istemci sertifikalarını doğrulanma göre <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2e11-118">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="e2e11-119">Özellik biri olarak ayarlanmışsa <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="e2e11-119">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="e2e11-120">İptal denetimi değerlerini göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2e11-120">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="e2e11-121">Özellik biri olarak ayarlanmışsa <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="e2e11-121">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="e2e11-122">SSL TCP ve SOAP güvenliği üzerinden hizmet sertifikasında doğrulanması</span><span class="sxs-lookup"><span data-stu-id="e2e11-122">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  
 <span data-ttu-id="e2e11-123">SSL TCP veya (SOAP) ileti güvenliği kullanırken, hizmet sertifikaları göre doğrulanır <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2e11-123">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="e2e11-124">Özellik biri olarak ayarlanmışsa <xref:System.ServiceModel.Security.X509CertificateValidationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="e2e11-124">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="e2e11-125">İptal denetimi değerlerini göre gerçekleştirilir <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> özellik değerinin <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e2e11-125">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="e2e11-126">Özellik biri olarak ayarlanmışsa <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> değerleri.</span><span class="sxs-lookup"><span data-stu-id="e2e11-126">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e2e11-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2e11-127">See Also</span></span>  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [<span data-ttu-id="e2e11-128">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e2e11-128">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
