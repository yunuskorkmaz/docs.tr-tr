---
title: 'Nasıl yapılır: İstemci kimlik bilgileri türünü belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: 9fe999c4ee27d4a78bfad185fa3bcc065d74708a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643387"
---
# <a name="how-to-specify-the-client-credential-type"></a>Nasıl yapılır: İstemci kimlik bilgileri türünü belirtme
(Aktarım veya iletisi) bir güvenlik modu ayarlandıktan sonra istemci kimlik bilgisi türünü ayarlama seçeneğiniz vardır. Bu özellik, istemci hizmete kimlik doğrulaması için kimlik bilgisi türü sağlamanız gerekir belirtir. (İstemci kimlik bilgisi türü ayarlamadan önce gerekli bir adım) güvenlik modunu ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>İstemci kimlik bilgisi türü kodunda ayarlamak için  
  
1.  Hizmetini kullanacak olan bağlama örneği oluşturun. Bu örnekte <xref:System.ServiceModel.WSHttpBinding> bağlama.  
  
2.  Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> özelliğini uygun bir değer. Bu örnek, mesajı modunu kullanır.  
  
3.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> özelliğini uygun bir değer. Bu örnekte Windows kimlik doğrulaması kullanacak şekilde ayarlar (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>İstemci kimlik bilgisi türü yapılandırmada ayarlamak için  
  
1.  Ekleme bir [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma dosyasına öğesi.  
  
2.  Bir alt öğesi ekleyin bir [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.  
  
3.  Uygun bir bağlaması ekleyin. Bu örnekte [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.  
  
4.  Ekleme bir [ \<bağlama >](../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` özniteliği için uygun bir değer. Bu örnek, "SecureBinding" adını kullanır.  
  
5.  Ekleme bir `<security>` bağlama. Ayarlama `mode` özniteliği için uygun bir değer. Bu örnek ayarlar `"Message"`.  
  
6.  Ekleyin ya da bir `<message>` veya `<transport>` güvenlik modu tarafından belirlenen şekilde öğesi. Ayarlama `clientCredentialType` özniteliği için uygun bir değer. Bu örnekte `"Windows"`.  
  
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
- [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)
- [Nasıl yapılır: Güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
