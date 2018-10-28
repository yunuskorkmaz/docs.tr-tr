---
title: 'Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: afc89d14623a25dbaa1ac5c9a58e11dd3e963617
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50088682"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma
Windows Communication Foundation (WCF) tarafından istemcileri ve Hizmetleri birbirine kimlik doğrulaması birkaç modu sağlar. Güvenlik bağlama öğeleri bu kimlik doğrulama modları için statik yöntemler kullanarak oluşturabileceğiniz <xref:System.ServiceModel.Channels.SecurityBindingElement> sınıfı veya aşağıdaki örnekte gösterildiği gibi yapılandırma yoluyla.  
  
 18 kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [SecurityBindingElement kimlik doğrulama modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, çeşitli kimlik doğrulama modları için bağlamaları oluşturmak için yöntemleri gösterir.  
  
> [!NOTE]
>  Bir kez örneğini <xref:System.ServiceModel.Channels.SecurityBindingElement> nesnesi oluşturulur, çeşitli özellikleri gibi sabit <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> ve <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Çağırma `set` gibi özellikleri üzerinde bunları değiştirmez.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SecurityBindingElement Kimlik Doğrulama Modları](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
