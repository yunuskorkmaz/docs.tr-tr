---
title: 'Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: f8231acade6821c95a76a608633fe443f4add8ab
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586923"
---
# <a name="how-to-set-a-max-clock-skew"></a>Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama
İki bilgisayardaki saat ayarları farklıysa, zaman açısından kritik işlevler derlenebilir. Bu olasılığa karşı azaltmak için `MaxClockSkew` özelliği bir olarak ayarlayabilirsiniz <xref:System.TimeSpan> . Bu özellik iki sınıfta kullanılabilir:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> Güvenli bir konuşma için, `MaxClockSkew` hizmet veya istemci önyüklendi olduğunda özellikte değişiklikler yapılmalıdır. Bunu yapmak için, özelliği tarafından döndürülen özelliğini ayarlamanız gerekir <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> .  
  
 Sistem tarafından belirtilen bağlamalardan birindeki özelliği değiştirmek için, bağlama koleksiyonunda güvenlik bağlama öğesini bulmanız ve `MaxClockSkew` özelliği yeni bir değere ayarlamanız gerekir. İki sınıf öğesinden türetilir <xref:System.ServiceModel.Channels.SecurityBindingElement> : <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> . Koleksiyondan güvenlik bağlamasını alırken, özelliği doğru bir şekilde ayarlamak için bu türlerden birine atamalısınız `MaxClockSkew` . Aşağıdaki örnek öğesini kullanan bir kullanır <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> . Sistem tarafından belirtilen her bağlamada kullanılacak güvenlik bağlamasının türünü belirten bir liste için, bkz. [sistem tarafından sunulan bağlamalar](../system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Kodda yeni saat eğriltme değeri ile özel bir bağlama oluşturmak için  
  
> [!WARNING]
> Kodunuzda aşağıdaki ad alanlarına başvurular ekleyin: <xref:System.ServiceModel.Channels> , <xref:System.ServiceModel.Description> , <xref:System.Security.Permissions> , ve <xref:System.ServiceModel.Security.Tokens> .  
  
1. Bir sınıfın örneğini oluşturun <xref:System.ServiceModel.WSHttpBinding> ve güvenlik modunu olarak ayarlayın <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType> .  
  
2. Yöntemini çağırarak sınıfının yeni bir örneğini oluşturun <xref:System.ServiceModel.Channels.BindingElementCollection> <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> .  
  
3. <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> <xref:System.ServiceModel.Channels.BindingElementCollection> Güvenlik bağlama öğesini bulmak için sınıfının yöntemini kullanın.  
  
4. <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>Yöntemini kullanırken gerçek türe atayın. Aşağıdaki örnek <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türe yayınlar.  
  
5. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A>Güvenlik bağlama öğesinde özelliği ayarlayın.  
  
6. Uygun bir <xref:System.ServiceModel.ServiceHost> hizmet türü ve temel adres ile oluşturun.  
  
7. <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>Bir uç nokta eklemek ve dahil etmek için yöntemini kullanın <xref:System.ServiceModel.Channels.CustomBinding> .  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Yapılandırmada MaxClockSkew ayarlamak için  
  
1. [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)Öğe bölümünde bir oluşturun [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) .  
  
2. Bir [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun ve `name` özniteliği uygun bir değere ayarlayın. Aşağıdaki örnek olarak ayarlanır `MaxClockSkewBinding` .  
  
3. Bir Encoding öğesi ekleyin. Aşağıdaki örnek bir ekler [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) .  
  
4. Bir [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) öğe ekleyin ve `authenticationMode` özniteliği uygun bir ayara ayarlayın. Aşağıdaki örnek, `Kerberos` hizmetinin Windows kimlik doğrulamasını kullanmasını belirtmek için özniteliğini olarak ayarlar.  
  
5. ' A ekleyin [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` özniteliği biçimindeki bir değere ayarlayın `"##:##:##"` . Aşağıdaki örnek, 7 dakika olarak ayarlanır. İsteğe bağlı olarak, bir ekleyin [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` özniteliği uygun bir ayara ayarlayın.  
  
6. Bir Transport öğesi ekleyin. Aşağıdaki örnek bir kullanır [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) .  
  
7. Güvenli bir konuşma için, güvenlik ayarları öğesindeki önplanda gerçekleşmelidir [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) .  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
