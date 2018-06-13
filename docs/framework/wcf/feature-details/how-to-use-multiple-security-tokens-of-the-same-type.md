---
title: 'Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 67a9fd51377294ab6afb5a3d7deaec19fb134b21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490753"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a>Nasıl yapılır: Aynı Türde Birden Fazla Belirteç Kullanma
-   İçinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, bir istemci iletisi yalnızca kapsanan bir belirteç herhangi bir türde. Şimdi istemci iletileri bir türde birden çok belirteç içerebilir. Bu konuda, bir istemci iletiye aynı türde birden çok belirteç gösterilmektedir.  
  
-   Bu şekilde bir hizmet yapılandıramazsınız Not: bir hizmetin yalnızca bir destekleme belirteci içerebilir.  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a>Aynı türde birden çok güvenlik belirteçleri kullanmak için  
  
1.  Doldurulması için boş bağlama öğesi koleksiyon oluşturun.  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  Oluşturma bir <xref:System.ServiceModel.Channels.SecurityBindingElement> çağırarak <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  Oluşturma bir <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> koleksiyonu.  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  SAML belirteçleri koleksiyona ekleyin.  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  Koleksiyona eklemek <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  Bağlama öğeleri bağlama öğesi koleksiyonuna ekleyin.  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  Bağlama öğesi koleksiyonundan oluşturulan yeni bir özel bağlama döndür.  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a>Örnek  
 Yukarıdaki yordam tarafından açıklanan tüm yöntemi verilmiştir.  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik mimarisi](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
