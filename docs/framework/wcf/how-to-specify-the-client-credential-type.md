---
title: "Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme"
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
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 35c3b5ee429f7c9337fa3c3e3eb0d0476e3f56d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-the-client-credential-type"></a>Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme
Bir güvenlik modunu (taşıma veya ileti) ayarladıktan sonra istemci ayar kimlik bilgisi türü seçeneğiniz vardır. Bu özellik ne tür bir kimlik bilgisi istemci kimlik doğrulaması için hizmet sağlamalısınız belirtir. [!INCLUDE[crabout](../../../includes/crabout-md.md)]bkz: (istemci kimlik bilgisi türü ayarlamadan önce gerekli bir adım), güvenlik modu ayarı [nasıl yapılır: güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>İstemci kimlik bilgisi türü kodda ayarlamak için  
  
1.  Hizmet kullanacak bağlama örneği oluşturun. Bu örnekte <xref:System.ServiceModel.WSHttpBinding> bağlama.  
  
2.  Ayarlama <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> uygun bir değere özelliği. Bu örnek ileti modu kullanır.  
  
3.  Ayarlama <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> uygun bir değere özelliği. Bu örnekte Windows kimlik doğrulaması kullanacak şekilde ayarlar (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>İstemci kimlik bilgisi türü yapılandırmasında ayarlamak için  
  
1.  Ekleme bir [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) yapılandırma dosyası öğesi.  
  
2.  Bir alt öğesi Ekle bir [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi.  
  
3.  Uygun bir bağlaması ekleyin. Bu örnekte [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) öğesi.  
  
4.  Ekleme bir [ \<bağlama >](../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` öznitelik için uygun bir değer. Bu örnekte "SecureBinding" adını kullanır.  
  
5.  Ekleme bir `<security>` bağlama. Ayarlama `mode` öznitelik için uygun bir değer. Bu örnek ayarlar `"Message"`.  
  
6.  Ekleyip ya da bir `<message>` veya `<transport>` güvenlik modu tarafından belirlenen öğesi. Ayarlama `clientCredentialType` öznitelik için uygun bir değer. Bu örnekte `"Windows"`.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md)  
 [Nasıl yapılır: güvenlik modunu ayarlama](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
