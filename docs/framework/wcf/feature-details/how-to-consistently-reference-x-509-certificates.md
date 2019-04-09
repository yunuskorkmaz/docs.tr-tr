---
title: 'Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: bd911b1586f7f4a4816efa32480ef99ca12404f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59176208"
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="e7009-102">Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="e7009-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="e7009-103">Sertifika çeşitli yollarla tanımlayabilirsiniz: Sertifika Karması, veren ve seri numarası veya konu anahtarı tanımlayıcısı (KAYAK).</span><span class="sxs-lookup"><span data-stu-id="e7009-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="e7009-104">KAYAK sertifikanın konu ortak anahtarı için benzersiz bir kimlik sağlar ve XML dijital imza ile çalışırken sık sık kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e7009-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="e7009-105">KAYAK değeri genellikle X.509 sertifikası olarak bir parçası olan bir *X.509 Sertifika uzantısı*.</span><span class="sxs-lookup"><span data-stu-id="e7009-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> <span data-ttu-id="e7009-106">Windows Communication Foundation (WCF) sahip bir varsayılan *stil başvuran* , kullanıyorsa veren ve seri numarasını KAYAK uzantı sertifikası eksik.</span><span class="sxs-lookup"><span data-stu-id="e7009-106">Windows Communication Foundation (WCF) has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="e7009-107">Sertifika KAYAK uzantısı içeriyorsa, varsayılan stili başvuran KAYAK sertifikanıza işaret edecek kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7009-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="e7009-108">Orta yolu, bir uygulamanın geliştirilmesi aracılığıyla KAYAK uzantısı kullanan sertifikaları için KAYAK uzantısı kullanmayın sertifikaları kullanarak, geçiş, WCF tarafından oluşturulan iletilerde kullanılan başvuru stili da değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e7009-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in WCF-generated messages also changes.</span></span>  
  
 <span data-ttu-id="e7009-109">KAYAK uzantısı varlığı bağımsız olarak tutarlı bir başvuru stili gerekiyorsa, aşağıdaki kodda gösterildiği gibi gerekli başvuru stili yapılandırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e7009-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7009-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="e7009-110">Example</span></span>  
 <span data-ttu-id="e7009-111">Aşağıdaki örnek, tek bir tutarlı başvuru stili, verenin adı ve seri numarası kullanan bir özel güvenlik bağlama öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e7009-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7009-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e7009-112">Compiling the Code</span></span>  
 <span data-ttu-id="e7009-113">Aşağıdaki ad alanlarını, kodu derlemek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="e7009-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="e7009-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7009-114">See also</span></span>

- [<span data-ttu-id="e7009-115">Sertifikalarla Çalışma</span><span class="sxs-lookup"><span data-stu-id="e7009-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
