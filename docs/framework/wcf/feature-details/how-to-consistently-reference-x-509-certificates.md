---
description: 'Daha fazla bilgi edinin: nasıl yapılır: sürekli olarak X. 509.440 sertifikalarına başvuru'
title: 'Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: cdf5535373490e8cb78e28a8fc0cf881df40e041
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734808"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="25654-103">Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="25654-103">How to: Consistently Reference X.509 Certificates</span></span>

<span data-ttu-id="25654-104">Sertifikayı çeşitli yollarla tanımlayabilirsiniz: sertifikanın karması ile, veren ve seri numarası veya konu anahtar tanımlayıcısı (kayak).</span><span class="sxs-lookup"><span data-stu-id="25654-104">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="25654-105">Kayak, sertifikanın konu ortak anahtarı için benzersiz bir kimlik sağlar ve genellikle XML dijital imzalama ile çalışırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="25654-105">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="25654-106">Kayak değeri genellikle x. 509.440 sertifikasının *x. 509.440 sertifika uzantısı* olarak bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="25654-106">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="25654-107">Windows Communication Foundation (WCF), Kayak uzantısı sertifikada yoksa veren ve seri numarasını kullanan bir varsayılan *başvuru stiline* sahiptir.</span><span class="sxs-lookup"><span data-stu-id="25654-107">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="25654-108">Sertifika Kayak uzantısını içeriyorsa, varsayılan başvuru stili sertifikayı işaret etmek için kayak kullanır.</span><span class="sxs-lookup"><span data-stu-id="25654-108">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="25654-109">Bir uygulamanın geliştirilmesi ile ilgili olarak, Kayak uzantısını kullanmayan sertifikaları Kayak uzantısını kullanan sertifikalara geçiş yaparsanız, WCF tarafından oluşturulan iletilerde kullanılan başvuru stili de değişir.</span><span class="sxs-lookup"><span data-stu-id="25654-109">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="25654-110">Kayak Extension varlığından bağımsız olarak tutarlı bir başvuru stili gerekliyse, istenen başvuru stilini aşağıdaki kodda gösterildiği gibi yapılandırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="25654-110">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25654-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="25654-111">Example</span></span>  

 <span data-ttu-id="25654-112">Aşağıdaki örnek, tek bir tutarlı başvuru stili, verenin adı ve seri numarası kullanan özel bir güvenlik bağlama öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="25654-112">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="25654-113">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="25654-113">Compiling the Code</span></span>  

 <span data-ttu-id="25654-114">Kodu derlemek için aşağıdaki ad alanları gereklidir:</span><span class="sxs-lookup"><span data-stu-id="25654-114">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="25654-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25654-115">See also</span></span>

- [<span data-ttu-id="25654-116">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="25654-116">Working with Certificates</span></span>](working-with-certificates.md)
