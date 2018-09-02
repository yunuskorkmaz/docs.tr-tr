---
title: WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: cdf40d6c0ca25a21cbdac07abab04d2bc144bf69
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408979"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
WCF artık tek bir uç noktada birden çok kimlik doğrulama düzenleri belirtmenizi sağlar. Ayrıca barındırılan web hizmetleri doğrudan IIS kimlik doğrulaması ayarlarını devralabilir. Şirket içinde barındırılan hizmetler, hangi kimlik doğrulama düzenleri kullanılabilir belirtebilirsiniz. IIS kimlik doğrulaması ayarlarını ayarlama hakkında daha fazla bilgi için bkz. [IIS kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS barındırılan hizmetler  
 IIS barındırılan hizmetler için IIS içinde kullanmak istediğiniz kimlik doğrulama şeması ayarlayın. Ardından hizmetinizin web.config dosyasında bağlama Yapılandırması'nda clientCredential türü "InheritedFromHost" olarak aşağıdaki XML kod parçacığında gösterildiği gibi belirtin:  
  
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
  
 Yalnızca bir alt kümesini ServiceAuthenticationBehavior kullanarak hizmetinize kullanılacak kimlik doğrulama düzenleri istediğinizi belirtin veya \<serviceAuthenticationManager > öğesi. Bu kodda yapılandırırken ServiceAuthenticationBehavior aşağıdaki kod parçacığında gösterildiği gibi kullanın.  
  
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
  
 Bu yapılandırma dosyasında yapılandırırken, kullandığınız \<serviceAuthenticationManager > aşağıdaki XML kod parçacığında gösterildiği gibi bir öğe.  
  
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
  
 Bu, yalnızca bir alt kümesini burada listelenen kimlik doğrulama düzenleri IIS'de ne seçili olursa bağlı olarak, hizmet uç noktasında uygulamak için kabul edilir garanti eder. Bir geliştirici hariç tutabilirsiniz Bunun anlamı serviceAuthenticationManager listeden gt;(yok) listeden temel kimlik doğrulaması deyin ve IIS'de etkin olsa bile, bu hizmet uç noktasında uygulanmaz  
  
## <a name="self-hosted-services"></a>Şirket içinde barındırılan hizmetleri  
 Ayarları devralmak için hiçbir IIS olduğundan şirket içinde barındırılan hizmetler biraz farklı bir şekilde yapılandırılır. Burada kullandığınız \<serviceAuthenticationManager > öğesi veya ServiceAuthenticationBehavior devralınır kimlik doğrulama ayarlarını belirtmek için. Kod şöyle görünür:  
  
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
  
 Yapılandırmada şöyle görünür:  
  
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
  
 ' İ tıklatın ve sonra aşağıdaki XML kod parçacığında gösterildiği gibi bağlama ayarlarında InheritFromHost belirtebilirsiniz.  
  
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
  
 Alternatif olarak, özel bir bağlama kimlik doğrulama düzeni belirtebilirsiniz, ayarlayarak kimlik doğrulama düzeni HTTP bağlama öğesi aşağıdaki yapılandırma kod parçacığında gösterildiği gibi taşıma.  
  
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
