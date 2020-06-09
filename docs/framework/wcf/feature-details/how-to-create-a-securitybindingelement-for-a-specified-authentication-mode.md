---
title: 'Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
ms.openlocfilehash: 9aebe6d8cc82c454161daead49b55f02a1cca4a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598950"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Nasıl yapılır: Belirtilen Bir Kimlik Doğrulama Modu için SecurityBindingElement Oluşturma
Windows Communication Foundation (WCF), istemcilerin ve hizmetlerin bir diğeri üzerinde kimlik doğrulaması yaptığı çeşitli modlar sağlar. <xref:System.ServiceModel.Channels.SecurityBindingElement>Aşağıdaki örnekte gösterildiği gibi, sınıftaki statik yöntemleri kullanarak veya yapılandırma yoluyla bu kimlik doğrulama modları için güvenlik bağlama öğeleri oluşturabilirsiniz.  
  
 18 kimlik doğrulama modları hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, çeşitli kimlik doğrulama modları için bağlama oluşturma yöntemlerini gösterir.  
  
> [!NOTE]
> Nesne örneği oluşturulduktan sonra <xref:System.ServiceModel.Channels.SecurityBindingElement> , ve gibi birçok özellik sabittir <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> . `set`Bu tür özellikleri çağırmak bunları değiştirmez.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SecurityBindingElement Kimlik Doğrulama Modları](securitybindingelement-authentication-modes.md)
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
