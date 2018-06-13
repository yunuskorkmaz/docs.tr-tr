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
ms.openlocfilehash: dca675b8d5774948bffd936d146cb0e1dd9aa62d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496737"
---
# <a name="how-to-set-a-max-clock-skew"></a>Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama
İki bilgisayardaki saat ayarları farklıysa zaman açısından kritik işlevler derailed. Bu olasılığını azaltmak için ayarlayabileceğiniz `MaxClockSkew` özelliğine bir <xref:System.TimeSpan>. Bu özellik üzerinde iki sınıf bulunmaktadır:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Önemli için güvenli bir konuşma değişiklikler `MaxClockSkew` özelliği, hizmet veya istemci önyükleme içinde olduğunda sunulmalıdır. Bunu yapmak için özellik üzerinde ayarlamalısınız <xref:System.ServiceModel.Channels.SecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Sistem tarafından sağlanan bağlamalar birinde özelliğini değiştirmek için güvenlik bağlama öğesi bağlamaları koleksiyonunda bulmak ve ayarlayın `MaxClockSkew` özelliği için yeni bir değer. İki sınıf türetin <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Güvenlik bağlama koleksiyondan alırken, bu türden biri için doğru şekilde ayarlanması için atamalısınız `MaxClockSkew` özelliği. Aşağıdaki örnek kullanan bir <xref:System.ServiceModel.WSHttpBinding>, kullanan <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Her sistem tarafından sağlanan bağlaması kullanmak için güvenlik bağlama hangi türünü belirten bir listesi için bkz: [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Yeni bir saat ile özel bağlama oluşturmak için kod değerinde eğme  
  
1.  > [!WARNING]
    >  Şu ad alanlarından kodunuzda Ekle başvurular dikkat edin: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, ve <xref:System.ServiceModel.Security.Tokens>.  
  
     Bir örneğini oluşturmak bir <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Yeni bir örneğini oluşturmak <xref:System.ServiceModel.Channels.BindingElementCollection> çağırarak sınıfı <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.  
  
3.  Kullanım <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemi <xref:System.ServiceModel.Channels.BindingElementCollection> sınıfı güvenlik bağlama öğesi bulunamıyor.  
  
4.  Kullanırken <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> gerçek türe yöntemi. Yayınları için aşağıdaki örnekte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türü.  
  
5.  Ayarlama <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> güvenlik bağlama öğesi özelliği.  
  
6.  Oluşturma bir <xref:System.ServiceModel.ServiceHost> uygun hizmet türü ve temel adresi.  
  
7.  Kullanım <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> bir uç nokta ekleyin ve dahil etmek için yöntemi <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>MaxClockSkew yapılandırmasında ayarlamak için  
  
1.  Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) içinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümü.  
  
2.  Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` öznitelik için uygun bir değer. Aşağıdaki örnek, ayarlar `MaxClockSkewBinding`.  
  
3.  Bir kodlama öğesi ekleyin. Aşağıdaki örnek, bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Ekleme bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi ve kümesi `authenticationMode` öznitelik için uygun bir ayar. Aşağıdaki örnek özniteliği olarak ayarlanmış `Kerberos` belirtmek için hizmet Windows kimlik doğrulaması kullanın.  
  
5.  Ekleme bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` biçiminde bir değer özniteliğini `"##:##:##"`. Aşağıdaki örnek 7 dakika olarak ayarlar. İsteğe bağlı olarak ekleyin bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ve `maxClockSkew` öznitelik için uygun bir ayar.  
  
6.  Bir taşıma öğesi ekleyin. Aşağıdaki örnek kullanan bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Güvenli bir konuşma için güvenlik ayarlarını önyükleme sırasında gerçekleşmelidir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Nasıl yapılır: SecurityBindingElement Kullanarak Özel Bağlama Oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
