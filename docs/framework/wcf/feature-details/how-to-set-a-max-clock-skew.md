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
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141650"
---
# <a name="how-to-set-a-max-clock-skew"></a>Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama
İki bilgisayardaki saat ayarları farklıysa, zaman açısından kritik işlevler derlenebilir. Bu olasılığa karşı azaltmak için `MaxClockSkew` özelliğini bir <xref:System.TimeSpan>olarak ayarlayabilirsiniz. Bu özellik iki sınıfta kullanılabilir:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> Güvenli konuşma için, hizmet veya istemci önyüklendi olduğunda `MaxClockSkew` özelliğindeki değişiklikler yapılmalıdır. Bunu yapmak için, <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> özelliği tarafından döndürülen <xref:System.ServiceModel.Channels.SecurityBindingElement> özelliğini ayarlamanız gerekir.  
  
 Sistem tarafından belirtilen bağlamalardan birindeki özelliği değiştirmek için, bağlama koleksiyonunda güvenlik bağlama öğesini bulmanız ve `MaxClockSkew` özelliğini yeni bir değere ayarlamanız gerekir. İki sınıf <xref:System.ServiceModel.Channels.SecurityBindingElement>türetilir: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Koleksiyondan güvenlik bağlamasını alırken, `MaxClockSkew` özelliğini doğru bir şekilde ayarlamak için bu türlerden birine dönüştürmeniz gerekir. Aşağıdaki örnek, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>kullanan bir <xref:System.ServiceModel.WSHttpBinding>kullanır. Sistem tarafından belirtilen her bağlamada kullanılacak güvenlik bağlamasının türünü belirten bir liste için, bkz. [sistem tarafından sunulan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Kodda yeni saat eğriltme değeri ile özel bir bağlama oluşturmak için  
  
> [!WARNING]
> Kodunuzda aşağıdaki ad alanlarına başvurular ekleyin: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>ve <xref:System.ServiceModel.Security.Tokens>.  
  
1. <xref:System.ServiceModel.WSHttpBinding> sınıfının bir örneğini oluşturun ve güvenlik modunu <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>olarak ayarlayın.  
  
2. <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> metodunu çağırarak <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının yeni bir örneğini oluşturun.  
  
3. Güvenlik bağlama öğesini bulmak için <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemini kullanın.  
  
4. <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemi kullanılırken gerçek türe atayın. Aşağıdaki örnek <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türüne yayınlar.  
  
5. Güvenlik bağlama öğesindeki <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> özelliğini ayarlayın.  
  
6. Uygun hizmet türü ve temel adresi olan bir <xref:System.ServiceModel.ServiceHost> oluşturun.  
  
7. Uç nokta eklemek ve <xref:System.ServiceModel.Channels.CustomBinding>eklemek için <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> yöntemi kullanın.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Yapılandırmada MaxClockSkew ayarlamak için  
  
1. [\<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümünde bir [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) oluşturun.  
  
2. [\<bağlama >](../../configure-apps/file-schema/wcf/bindings.md) öğesi oluşturun ve `name` özniteliğini uygun bir değere ayarlayın. Aşağıdaki örnek, `MaxClockSkewBinding`olarak ayarlar.  
  
3. Bir Encoding öğesi ekleyin. Aşağıdaki örnek bir [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)ekler.  
  
4. \<bir [güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi ekleyin ve `authenticationMode` özniteliğini uygun bir ayar olarak ayarlayın. Aşağıdaki örnek, hizmetin Windows kimlik doğrulamasını kullanmasını belirtmek için özniteliğini `Kerberos` olarak ayarlar.  
  
5. [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ekleyin ve `maxClockSkew` özniteliğini `"##:##:##"`biçimindeki bir değere ayarlayın. Aşağıdaki örnek, 7 dakika olarak ayarlanır. İsteğe bağlı olarak, bir [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ekleyin ve `maxClockSkew` özniteliğini uygun bir ayar olarak ayarlayın.  
  
6. Bir Transport öğesi ekleyin. Aşağıdaki örnek bir [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)kullanır.  
  
7. Güvenli bir konuşma için, güvenlik ayarları [\<Securekonuşmayı tionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesinde önyükleme sırasında gerçekleşmelidir.  
  
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
- [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
