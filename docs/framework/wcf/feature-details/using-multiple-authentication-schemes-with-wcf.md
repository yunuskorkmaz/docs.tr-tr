---
title: WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 140211f10f7cdc88a3df8eb8ea1c30df73b0c4c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498452"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
WCF artık tek bir noktadaki birden çok kimlik doğrulama şemasını belirtmenize olanak tanır. Ayrıca barındırılan web hizmetleri doğrudan IIS kimlik doğrulaması ayarlarını devralabilirsiniz. Kendini barındıran Hizmetleri düzenleri kullanılabilmesi için hangi kimlik doğrulama belirtebilirsiniz. IIS'de kimlik doğrulama ayarlarını ayarlama hakkında daha fazla bilgi için bkz: [IIS kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS barındırılan hizmetleri  
 IIS barındırılan hizmetler için IIS içinde kullanmak istediğiniz kimlik doğrulama şemasını ayarlayın. Ardından hizmetinizin web.config dosyasına bağlama yapılandırmanızda clientCredential türü "InheritedFromHost" olarak aşağıdaki XML parçacığında gösterildiği gibi belirtin:  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Yalnızca bir alt kümesini ServiceAuthenticationBehavior kullanarak, hizmetiniz ile kullanılacak kimlik doğrulama şemasını istediğinizi belirtin veya \<serviceAuthenticationManager > öğesi. Bu kodda yapılandırırken ServiceAuthenticationBehavior aşağıdaki kod parçacığında gösterildiği gibi kullanın.  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Bu yapılandırma dosyasında yapılandırırken kullandığınız \<serviceAuthenticationManager > aşağıdaki XML parçacığında gösterildiği gibi öğesi.  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Bu, yalnızca bir alt kümesini burada listelenen kimlik doğrulama şemasını IIS'de belirlemiş bağlı olarak hizmet uç noktası üzerinde uygulamak için değerlendirilir güvence altına alır. Bir geliştirici dışlayabilirsiniz Bunun anlamı deyin listeden temel kimlik doğrulama serviceAuthenticationManager listeden kaldırarak ve IIS etkinleştirilmiş olsa dahi, üzerinde hizmet uç noktası uygulanmaz  
  
## <a name="self-hosted-services"></a>Kendini barındıran Hizmetleri  
 Ayarları devralmak için hiçbir IIS olduğundan kendini barındıran Hizmetleri biraz farklı bir şekilde yapılandırılır. Burada kullandığınız \<serviceAuthenticationManager > öğesi veya ServiceAuthenticationBehavior devralınır kimlik doğrulama ayarlarını belirtin. Kodda şöyle görünür:  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 Yapılandırma dosyasında şöyle görünür:  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 Ve ardından aşağıdaki XML parçacığında gösterildiği gibi bağlama ayarlarında InheritFromHost belirtebilirsiniz.  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 Alternatif olarak, kimlik doğrulama şemasını özel bir bağlama belirtin, ayarlayarak HTTP kimlik doğrulama şemasını bağlama öğesi, aşağıdaki yapılandırma parçacığında gösterildiği gibi taşıma.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamalar ve Güvenlik](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Özel Bağlamalarla Güvenlik Özellikleri](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Bağlamalar](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Özel Bağlamalar](../../../../docs/framework/wcf/extending/custom-bindings.md)
