---
title: 'Nasıl yapılır: X.509 sertifikalarına tutarlı olarak başvuru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], referencing X.509 certificates
ms.assetid: a6de1c63-e450-4640-ad08-ad7302dbfbfc
ms.openlocfilehash: 2468faabfbca57e7d905a592b6743c43cb2ccd56
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731978"
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Nasıl yapılır: X.509 sertifikalarına tutarlı olarak başvuru
Sertifika çeşitli yollarla tanımlayabilirsiniz: Sertifika Karması, veren ve seri numarası veya konu anahtarı tanımlayıcısı (KAYAK). KAYAK sertifikanın konu ortak anahtarı için benzersiz bir kimlik sağlar ve XML dijital imza ile çalışırken sık sık kullanılır. KAYAK değeri genellikle X.509 sertifikası olarak bir parçası olan bir *X.509 Sertifika uzantısı*. Windows Communication Foundation (WCF) sahip bir varsayılan *stil başvuran* , kullanıyorsa veren ve seri numarasını KAYAK uzantı sertifikası eksik. Sertifika KAYAK uzantısı içeriyorsa, varsayılan stili başvuran KAYAK sertifikanıza işaret edecek kullanır. Orta yolu, bir uygulamanın geliştirilmesi aracılığıyla KAYAK uzantısı kullanan sertifikaları için KAYAK uzantısı kullanmayın sertifikaları kullanarak, geçiş, WCF tarafından oluşturulan iletilerde kullanılan başvuru stili da değiştirir.  
  
 KAYAK uzantısı varlığı bağımsız olarak tutarlı bir başvuru stili gerekiyorsa, aşağıdaki kodda gösterildiği gibi gerekli başvuru stili yapılandırmak mümkündür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir tutarlı başvuru stili, verenin adı ve seri numarası kullanan bir özel güvenlik bağlama öğesi oluşturur.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Aşağıdaki ad alanlarını, kodu derlemek için gereklidir:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
