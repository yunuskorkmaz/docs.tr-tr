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
ms.openlocfilehash: e487da6316ec381c2009ee33575848dd80df8ab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076634"
---
# <a name="how-to-set-a-max-clock-skew"></a>Nasıl yapılır: Maksimum Saat Eğriltme Ayarlama
İki bilgisayar saat ayarları farklı ise, zaman açısından kritik işlevler derailed. Bu olasılığını azaltmak için ayarlayabileceğiniz `MaxClockSkew` özelliğini bir <xref:System.TimeSpan>. Bu özellik, iki sınıf üzerinde kullanılabilir:  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
>  Önemli için bir güvenli konuşma değişiklikleri `MaxClockSkew` özelliği, hizmet veya istemcinin önyüklenemez olduğunda sunulmalıdır. Bunu yapmak için özelliğin üzerinde ayarlamalısınız <xref:System.ServiceModel.Channels.SecurityBindingElement> tarafından döndürülen <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A>.  
  
 Sistem tarafından sağlanan bağlamalar birinde özelliğini değiştirmek için bağlamaları koleksiyonda güvenliği bağlama öğesini bulun ve ayarlamak `MaxClockSkew` özelliğini yeni bir değer. İki sınıf türetilir <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> ve <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>. Güvenlik bağlama koleksiyondan alınırken şu türlerden birine doğru şekilde ayarlanması için dönüştürmelisiniz `MaxClockSkew` özelliği. Aşağıdaki örnekte bir <xref:System.ServiceModel.WSHttpBinding>, kullanan <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>. Hangi güvenlik her sistem tarafından sağlanan bir bağlamayı içinde kullanılacak bağlama türünü belirten bir listesi için bkz [System-Provided bağlamaları](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
### <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a>Yeni bir saat ile özel bir bağlama oluşturmak için kod değerinde eğme  
  
1.  > [!WARNING]
    >  Kodunuzda aşağıdaki ad alanlarına Başvuru Ekle unutmayın: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, ve <xref:System.ServiceModel.Security.Tokens>.  
  
     Bir örneğini oluşturmak bir <xref:System.ServiceModel.WSHttpBinding> sınıfı ve kendi güvenlik modunu ayarlama <xref:System.ServiceModel.SecurityMode.Message>.  
  
2.  Yeni bir örneğini oluşturma <xref:System.ServiceModel.Channels.BindingElementCollection> çağırarak sınıfı <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> yöntemi.  
  
3.  Kullanım <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> yöntemi <xref:System.ServiceModel.Channels.BindingElementCollection> güvenliği bağlama öğesini bulmak için sınıf.  
  
4.  Kullanırken <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> gerçek türüne yöntemi. Yayınları için aşağıdaki örnekte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> türü.  
  
5.  Ayarlama <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> güvenlik bağlama öğesi özelliği.  
  
6.  Oluşturma bir <xref:System.ServiceModel.ServiceHost> uygun hizmet türü ve temel adresine sahip.  
  
7.  Kullanım <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> bir uç nokta ekleyin ve eklemek için yöntem <xref:System.ServiceModel.Channels.CustomBinding>.  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
### <a name="to-set-the-maxclockskew-in-configuration"></a>MaxClockSkew yapılandırmada ayarlamak için  
  
1.  Oluşturma bir [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) içinde [ \<bağlamaları >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) öğesi bölümü.  
  
2.  Oluşturma bir [ \<bağlama >](../../../../docs/framework/misc/binding.md) öğesi ve kümesi `name` özniteliği için uygun bir değer. Aşağıdaki örnek ayarlar `MaxClockSkewBinding`.  
  
3.  Bir kodlama öğesi ekleyin. Aşağıdaki örnekte ekler bir [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
4.  Ekleme bir [ \<Güvenlik >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) öğesi ve kümesi `authenticationMode` özniteliği için uygun bir ayar. Aşağıdaki örnek özniteliği olarak ayarlanmış `Kerberos` hizmet Windows kimlik doğrulaması kullandığını belirtmek için.  
  
5.  Ekleme bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ayarlayıp `maxClockSkew` biçiminde bir değer özniteliği `"##:##:##"`. Aşağıdaki örnek, 7 dakika olarak ayarlar. İsteğe bağlı olarak, ekleme bir [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) ayarlayıp `maxClockSkew` özniteliği için uygun bir ayar.  
  
6.  Bir transport öğesi ekleyin. Aşağıdaki örnekte bir [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
7.  Güvenli bir konuşma için güvenlik ayarlarını önyükleme içinde gerçekleşmelidir [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) öğesi.  
  
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
