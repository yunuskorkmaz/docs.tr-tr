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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cc313be8c3d6325630e57e0b0e845ad4902bd2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-consistently-reference-x509-certificates"></a>Nasıl yapılır: X.509 Sertifikalarına Tutarlı Olarak Başvuru Yapma
Bir sertifika çeşitli şekillerde tanımlayabilirsiniz: Sertifika Karması, veren ve seri numarası veya konu anahtarı tanımlayıcısı (SKI). SKI ve XML dijital imza ile çalışırken sık kullanılan sertifikanın konu ortak anahtarı için benzersiz bir kimlik sağlar. SKI değeri genellikle X.509 sertifikası olarak parçası olan bir *X.509 Sertifika uzantısı*. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]bir varsayılan *stili başvuran* , kullanıyorsa veren ve seri numarasını SKI uzantısı sertifikası eksik. Sertifika SKI uzantısı içeriyorsa, stil başvuran varsayılan SKI sertifikaya işaret edecek şekilde kullanır. Orta yolu, bir uygulamanın geliştirilmesi aracılığıyla SKI uzantısı kullanan sertifikaları SKI uzantı kullanmayın sertifikaları kullanarak geçiş, başvuru stili kullanılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-da oluşturulan değişiklikleri iletileri.  
  
 SKI uzantısı varlığı bağımsız olarak tutarlı bir başvuru stili gerekiyorsa, gerekli başvuru stili aşağıdaki kodda gösterildiği şekilde yapılandırmak mümkündür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tek bir tutarlı başvuru stili, verenin adı ve seri numarasını kullanan bir özel güvenlik bağlama öğesi oluşturur.  
  
 [!code-csharp[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_referencingcertificatesconsistently/cs/source.cs#1)]
 [!code-vb[c_ReferencingCertificatesConsistently#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_referencingcertificatesconsistently/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Şu ad alanlarından Kodu derlemek için gereklidir:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Security.Tokens>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
