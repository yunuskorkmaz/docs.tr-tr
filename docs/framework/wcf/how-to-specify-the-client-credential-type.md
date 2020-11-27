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
ms.openlocfilehash: b45d7b58d8a1fe79f9d7a8cff6e328b46633985c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293682"
---
# <a name="how-to-specify-the-client-credential-type"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme

Bir güvenlik modu (aktarım veya ileti) ayarladıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır. Bu özellik, istemcinin kimlik doğrulaması için hizmete sağlaması gereken kimlik bilgilerinin türünü belirtir. Güvenlik modunu ayarlama hakkında daha fazla bilgi için (istemci kimlik bilgisi türünü ayarlamadan önce gerekli bir adım), bkz. [nasıl yapılır: güvenlik modunu ayarlama](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Kodda istemci kimlik bilgisi türünü ayarlamak için  
  
1. Hizmetin kullanacağı bağlamanın bir örneğini oluşturun. Bu örnek, <xref:System.ServiceModel.WSHttpBinding> bağlamayı kullanır.  
  
2. <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>Özelliği uygun bir değere ayarlayın. Bu örnek Ileti modunu kullanır.  
  
3. <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A>Özelliği uygun bir değere ayarlayın. Bu örnek, Windows kimlik doğrulaması () kullanmak üzere ayarlar <xref:System.ServiceModel.MessageCredentialType.Windows> .  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Yapılandırmada istemci kimlik bilgisi türünü ayarlamak için  
  
1. [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md)Yapılandırma dosyasına bir öğe ekleyin.  
  
2. Alt öğe olarak bir [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin.  
  
3. Uygun bir bağlama ekleyin. Bu örnek öğesini kullanır [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) .  
  
4. Bir [\<binding>](../configure-apps/file-schema/wcf/bindings.md) öğesi ekleyin ve `name` özniteliği uygun bir değere ayarlayın. Bu örnekte "SecureBinding" adı kullanılmaktadır.  
  
5. Bağlama ekleyin `<security>` . `mode`Özniteliği uygun bir değere ayarlayın. Bu örnek olarak ayarlanır `"Message"` .  
  
6. `<message>` `<transport>` Güvenlik modu tarafından belirlendiği şekilde ya da öğesini ekleyin. `clientCredentialType`Özniteliği uygun bir değere ayarlayın. Bu örnekte, kullanılır `"Windows"` .  
  
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
