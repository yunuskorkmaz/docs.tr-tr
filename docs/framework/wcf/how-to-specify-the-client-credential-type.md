---
title: 'Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: df18f89ee18bfa33ecc0aced617d168c805e3515
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138570"
---
# <a name="how-to-specify-the-client-credential-type"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme
Bir güvenlik modu (aktarım veya ileti) ayarladıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır. Bu özellik, istemcinin kimlik doğrulaması için hizmete sağlaması gereken kimlik bilgilerinin türünü belirtir. Güvenlik modunu ayarlama hakkında daha fazla bilgi için (istemci kimlik bilgisi türünü ayarlamadan önce gerekli bir adım), bkz. [nasıl yapılır: güvenlik modunu ayarlama](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Kodda istemci kimlik bilgisi türünü ayarlamak için  
  
1. Hizmetin kullanacağı bağlamanın bir örneğini oluşturun. Bu örnek <xref:System.ServiceModel.WSHttpBinding> bağlamasını kullanır.  
  
2. <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini uygun bir değer olarak ayarlayın. Bu örnek Ileti modunu kullanır.  
  
3. <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliğini uygun bir değer olarak ayarlayın. Bu örnek, Windows kimlik doğrulaması (<xref:System.ServiceModel.MessageCredentialType.Windows>) kullanacak şekilde ayarlar.  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Yapılandırmada istemci kimlik bilgisi türünü ayarlamak için  
  
1. Yapılandırma dosyasına bir [\<System. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) öğesi ekleyin.  
  
2. Alt öğe olarak bir [\<bağlamaları >](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.  
  
3. Uygun bir bağlama ekleyin. Bu örnek [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) öğesini kullanır.  
  
4. [\<bağlama >](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin ve `name` özniteliğini uygun bir değere ayarlayın. Bu örnekte "SecureBinding" adı kullanılmaktadır.  
  
5. `<security>` bağlama ekleyin. `mode` özniteliğini uygun bir değere ayarlayın. Bu örnek, `"Message"`olarak ayarlar.  
  
6. Güvenlik modu tarafından belirlendiği şekilde bir `<message>` veya `<transport>` öğesi ekleyin. `clientCredentialType` özniteliğini uygun bir değere ayarlayın. Bu örnek `"Windows"`kullanır.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetleri Güvenli Hale Getirme](securing-services.md)
- [Nasıl yapılır: Güvenlik Modunu Ayarlama](how-to-set-the-security-mode.md)
