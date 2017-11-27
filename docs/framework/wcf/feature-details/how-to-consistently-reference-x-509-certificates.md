---
title: "Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma"
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
helpviewer_keywords: certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d42af919b9792fc5a5303737187be7ffef6405d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a><span data-ttu-id="350eb-102">Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma</span><span class="sxs-lookup"><span data-stu-id="350eb-102">How to: Consistently Reference X.509 Certificates</span></span>
<span data-ttu-id="350eb-103">Bir sertifika çeşitli şekillerde tanımlayabilirsiniz: Sertifika Karması, veren ve seri numarası veya konu anahtarı tanımlayıcısı (SKI).</span><span class="sxs-lookup"><span data-stu-id="350eb-103">You can identify a certificate in several ways: by the hash of the certificate, by the issuer and serial number, or by the subject key identifier (SKI).</span></span> <span data-ttu-id="350eb-104">SKI ve XML dijital imza ile çalışırken sık kullanılan sertifikanın konu ortak anahtarı için benzersiz bir kimlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="350eb-104">The SKI provides a unique identification for the certificate's subject public key and is often used when working with XML digital signing.</span></span> <span data-ttu-id="350eb-105">SKI değeri genellikle X.509 sertifikası olarak parçası olan bir *X.509 Sertifika uzantısı*.</span><span class="sxs-lookup"><span data-stu-id="350eb-105">The SKI value is usually part of the X.509 certificate as an *X.509 certificate extension*.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="350eb-106">bir varsayılan *stili başvuran* , kullanıyorsa veren ve seri numarasını SKI uzantısı sertifikası eksik.</span><span class="sxs-lookup"><span data-stu-id="350eb-106"> has a default *referencing style* that uses the issuer and serial number if the SKI extension is missing from the certificate.</span></span> <span data-ttu-id="350eb-107">Sertifika SKI uzantısı içeriyorsa, stil başvuran varsayılan SKI sertifikaya işaret edecek şekilde kullanır.</span><span class="sxs-lookup"><span data-stu-id="350eb-107">If the certificate contains the SKI extension, the default referencing style uses the SKI to point to the certificate.</span></span> <span data-ttu-id="350eb-108">Orta yolu, bir uygulamanın geliştirilmesi aracılığıyla SKI uzantısı kullanan sertifikaları SKI uzantı kullanmayın sertifikaları kullanarak geçiş, başvuru stili kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-da oluşturulan değişiklikleri iletileri.</span><span class="sxs-lookup"><span data-stu-id="350eb-108">If mid-way through development of an application, you switch from using certificates that do not use the SKI extension to certificates that use the SKI extension, the referencing style used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-generated messages also changes.</span></span>  
  
 <span data-ttu-id="350eb-109">SKI uzantısı varlığı bağımsız olarak tutarlı bir başvuru stili gerekiyorsa, gerekli başvuru stili aşağıdaki kodda gösterildiği şekilde yapılandırmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="350eb-109">If a consistent referencing style is required regardless of SKI extension presence, it is possible to configure the desired referencing style as shown in the following code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="350eb-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="350eb-110">Example</span></span>  
 <span data-ttu-id="350eb-111">Aşağıdaki örnek, tek bir tutarlı başvuru stili, verenin adı ve seri numarasını kullanan bir özel güvenlik bağlama öğesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="350eb-111">The following example creates a custom security binding element that uses a single consistent referencing style, the issuer name and serial number.</span></span>  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="350eb-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="350eb-112">Compiling the Code</span></span>  
 <span data-ttu-id="350eb-113">Şu ad alanlarından Kodu derlemek için gereklidir:</span><span class="sxs-lookup"><span data-stu-id="350eb-113">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a><span data-ttu-id="350eb-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="350eb-114">See Also</span></span>  
 [<span data-ttu-id="350eb-115">Sertifikalar ile çalışma</span><span class="sxs-lookup"><span data-stu-id="350eb-115">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
