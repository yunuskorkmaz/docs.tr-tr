---
title: WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 1874963573a6ec12939bd12b79574f1e2c889bfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600224"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a>WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
WCF artık tek bir uç noktada birden çok kimlik doğrulama düzeni belirtmenize olanak tanır. Ayrıca, Web 'de barındırılan hizmetlerin kimlik doğrulama ayarlarını doğrudan IIS 'den devralmasını sağlayabilirsiniz. Şirket içinde barındırılan hizmetler, hangi kimlik doğrulama düzenlerinin kullanılabileceğini belirtebilir. IIS 'de kimlik doğrulama ayarlarını ayarlama hakkında daha fazla bilgi için bkz. [IIS kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=232458)  
  
## <a name="iis-hosted-services"></a>IIS tarafından barındırılan hizmetler  
 IIS tarafından barındırılan hizmetler için, IIS 'de kullanmak istediğiniz kimlik doğrulama düzenlerini ayarlayın. Ardından, hizmetinizin Web. config dosyasında, bağlama yapılandırmanızda, aşağıdaki XML kod parçacığında gösterildiği gibi clientCredential türünü "ınheritedfromhost" olarak belirtin:  
  
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
  
 ServiceAuthenticationBehavior veya öğesini kullanarak hizmetinize yalnızca bir kimlik doğrulama şemaları alt kümesinin kullanılmasını istediğinizi belirtebilirsiniz \<serviceAuthenticationManager> . Bu kodda yapılandırırken, aşağıdaki kod parçacığında gösterildiği gibi ServiceAuthenticationBehavior kullanın.  
  
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
  
 Bunu bir yapılandırma dosyasında yapılandırırken, \<serviceAuthenticationManager> AŞAĞıDAKI XML kod parçacığında gösterildiği gibi öğesini kullanın.  
  
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
  
 Bu, IIS 'de neyin seçildiğine bağlı olarak, burada listelenen kimlik doğrulama düzenlerinin yalnızca bir alt kümesinin hizmet uç noktasına uygulanması için değerlendirildiğinden emin olur. Bu, bir geliştiricinin, serviceAuthenticationManager listesinden devre dışı bırakarak ve IIS 'de etkinleştirilmiş olsa bile, bir geliştiricinin temel kimlik doğrulaması 'nı hariç bırakabileceği anlamına gelir, hizmet uç noktasına uygulanmaz  
  
## <a name="self-hosted-services"></a>Şirket içinde barındırılan hizmetler  
 Ayarları devraldığı bir IIS olmadığından, şirket içinde barındırılan hizmetler biraz farklı şekilde yapılandırılır. Burada, \<serviceAuthenticationManager> devralınacak kimlik doğrulama ayarlarını belirtmek için öğesini veya ServiceAuthenticationBehavior öğesini kullanın. Kodda şöyle görünür:  
  
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
  
 Yapılandırma bölümünde şöyle görünür:  
  
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
  
 Daha sonra, aşağıdaki XML kod parçacığında gösterildiği gibi, bağlama ayarlarınızda ınherfromhost belirtebilirsiniz.  
  
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
  
 Alternatif olarak, aşağıdaki yapılandırma parçacığında gösterildiği gibi, HTTP taşıma bağlama öğesinde kimlik doğrulama düzenlerini ayarlayarak özel bir bağlamada kimlik doğrulama düzenlerini belirtebilirsiniz.  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamalar ve Güvenlik](bindings-and-security.md)
- [Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar](endpoints-addresses-bindings-and-contracts.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](configuring-system-provided-bindings.md)
- [Özel Bağlamalarla Güvenlik Özellikleri](security-capabilities-with-custom-bindings.md)
- [Bağlamalar](bindings.md)
- [Özel Bağlamalar](../extending/custom-bindings.md)
