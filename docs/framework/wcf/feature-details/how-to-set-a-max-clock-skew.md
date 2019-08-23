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
ms.openlocfilehash: 3bcd128e6e9f53f662dd3fc99336b5b45faebf5f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943125"
---
# <a name="how-to-set-a-max-clock-skew"></a>Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama
İki bilgisayardaki saat ayarları farklıysa, zaman açısından kritik işlevler derlenebilir. Bu olasılığa karşı azaltmak için `MaxClockSkew` özelliği bir <xref:System.TimeSpan>olarak ayarlayabilirsiniz. Bu özellik iki sınıfta kullanılabilir:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> Güvenli bir konuşma için, hizmet veya istemci `MaxClockSkew` önyüklendi olduğunda özellikte değişiklikler yapılmalıdır. Bunu yapmak için, özelliği <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> tarafından döndürülen özelliğini ayarlamanız gerekir.  
  
 Sistem tarafından belirtilen bağlamalardan birindeki özelliği değiştirmek için, bağlama koleksiyonunda güvenlik bağlama öğesini bulmanız ve `MaxClockSkew` özelliği yeni bir değere ayarlamanız gerekir. İki sınıf öğesinden <xref:System.ServiceModel.Channels.SecurityBindingElement>türetilir: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Koleksiyondan güvenlik bağlamasını alırken, `MaxClockSkew` özelliği doğru bir şekilde ayarlamak için bu türlerden birine atamalısınız. Aşağıdaki örnek öğesini <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>kullanan bir <xref:System.ServiceModel.WSHttpBinding>kullanır. Sistem tarafından belirtilen her bağlamada kullanılacak güvenlik bağlamasının türünü belirten bir liste için, bkz. [sistem tarafından sunulan bağlamalar](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Kodda yeni saat eğriltme değeri ile özel bir bağlama oluşturmak için  
  
> [!WARNING]
> Kodunuzda aşağıdaki ad alanlarına başvurular ekleyin <xref:System.ServiceModel.Channels>:, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, ve <xref:System.ServiceModel.Security.Tokens>.  
  
1. Bir <xref:System.ServiceModel.WSHttpBinding> sınıfın örneğini oluşturun ve güvenlik modunu olarak <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>ayarlayın.  
  
2. Yöntemini çağırarak sınıfının<xref:System.ServiceModel.Channels.BindingElementCollection> yeni bir örneğini oluşturun. <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>  
  
3. Güvenlik bağlama öğesini bulmak için <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfının yönteminikullanın.<xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A>  
  
4. <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> Yöntemini kullanırken gerçek türe atayın. Aşağıdaki <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> örnek türe yayınlar.  
  
5. Güvenlik bağlama öğesinde özelliği ayarlayın. <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A>  
  
6. Uygun bir <xref:System.ServiceModel.ServiceHost> hizmet türü ve temel adres ile oluşturun.  
  
7. Bir uç nokta eklemek ve <xref:System.ServiceModel.Channels.CustomBinding>dahil etmek için yönteminikullanın.<xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a>Yapılandırmada MaxClockSkew ayarlamak için  
  
1. Bağlama > öğesi bölümünde bir [ \<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) [> oluşturun. \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
2. Bağlama > öğesi oluşturun ve özniteliğiuygunbirdeğereayarlayın.`name` [ \<](../../../../docs/framework/misc/binding.md) Aşağıdaki örnek olarak `MaxClockSkewBinding`ayarlanır.  
  
3. Bir Encoding öğesi ekleyin. Aşağıdaki örnek bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)ekler.  
  
4. [ Bir\<güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `authenticationMode` öğesi ekleyin ve özniteliği uygun bir ayara ayarlayın. Aşağıdaki örnek, hizmetinin Windows kimlik doğrulamasını `Kerberos` kullanmasını belirtmek için özniteliğini olarak ayarlar.  
  
5. Bir `maxClockSkew` [ \<LocalServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ekleyin ve özniteliği biçimindeki `"##:##:##"`bir değere ayarlayın. Aşağıdaki örnek, 7 dakika olarak ayarlanır. İsteğe bağlı olarak, bir [ \<LocalServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ekleyin ve `maxClockSkew` özniteliği uygun bir ayara ayarlayın.  
  
6. Bir Transport öğesi ekleyin. Aşağıdaki örnek bir [ \<HttpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)kullanır.  
  
7. Güvenli bir konuşma için, güvenlik ayarları [ \<securekonuşmayı tionbootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesinde önyükleme sırasında gerçekleşmelidir.  
  
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
- [Nasıl yapılır: SecurityBindingElement kullanarak özel bağlama oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
