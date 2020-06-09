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
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="4020f-102">WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma</span><span class="sxs-lookup"><span data-stu-id="4020f-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="4020f-103">WCF artık tek bir uç noktada birden çok kimlik doğrulama düzeni belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4020f-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="4020f-104">Ayrıca, Web 'de barındırılan hizmetlerin kimlik doğrulama ayarlarını doğrudan IIS 'den devralmasını sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4020f-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="4020f-105">Şirket içinde barındırılan hizmetler, hangi kimlik doğrulama düzenlerinin kullanılabileceğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="4020f-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="4020f-106">IIS 'de kimlik doğrulama ayarlarını ayarlama hakkında daha fazla bilgi için bkz. [IIS kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="4020f-106">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="4020f-107">IIS tarafından barındırılan hizmetler</span><span class="sxs-lookup"><span data-stu-id="4020f-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="4020f-108">IIS tarafından barındırılan hizmetler için, IIS 'de kullanmak istediğiniz kimlik doğrulama düzenlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4020f-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="4020f-109">Ardından, hizmetinizin Web. config dosyasında, bağlama yapılandırmanızda, aşağıdaki XML kod parçacığında gösterildiği gibi clientCredential türünü "ınheritedfromhost" olarak belirtin:</span><span class="sxs-lookup"><span data-stu-id="4020f-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="4020f-110">ServiceAuthenticationBehavior veya öğesini kullanarak hizmetinize yalnızca bir kimlik doğrulama şemaları alt kümesinin kullanılmasını istediğinizi belirtebilirsiniz \<serviceAuthenticationManager> .</span><span class="sxs-lookup"><span data-stu-id="4020f-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="4020f-111">Bu kodda yapılandırırken, aşağıdaki kod parçacığında gösterildiği gibi ServiceAuthenticationBehavior kullanın.</span><span class="sxs-lookup"><span data-stu-id="4020f-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="4020f-112">Bunu bir yapılandırma dosyasında yapılandırırken, \<serviceAuthenticationManager> AŞAĞıDAKI XML kod parçacığında gösterildiği gibi öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4020f-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="4020f-113">Bu, IIS 'de neyin seçildiğine bağlı olarak, burada listelenen kimlik doğrulama düzenlerinin yalnızca bir alt kümesinin hizmet uç noktasına uygulanması için değerlendirildiğinden emin olur.</span><span class="sxs-lookup"><span data-stu-id="4020f-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="4020f-114">Bu, bir geliştiricinin, serviceAuthenticationManager listesinden devre dışı bırakarak ve IIS 'de etkinleştirilmiş olsa bile, bir geliştiricinin temel kimlik doğrulaması 'nı hariç bırakabileceği anlamına gelir, hizmet uç noktasına uygulanmaz</span><span class="sxs-lookup"><span data-stu-id="4020f-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="4020f-115">Şirket içinde barındırılan hizmetler</span><span class="sxs-lookup"><span data-stu-id="4020f-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="4020f-116">Ayarları devraldığı bir IIS olmadığından, şirket içinde barındırılan hizmetler biraz farklı şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4020f-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="4020f-117">Burada, \<serviceAuthenticationManager> devralınacak kimlik doğrulama ayarlarını belirtmek için öğesini veya ServiceAuthenticationBehavior öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="4020f-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="4020f-118">Kodda şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="4020f-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="4020f-119">Yapılandırma bölümünde şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="4020f-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="4020f-120">Daha sonra, aşağıdaki XML kod parçacığında gösterildiği gibi, bağlama ayarlarınızda ınherfromhost belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4020f-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="4020f-121">Alternatif olarak, aşağıdaki yapılandırma parçacığında gösterildiği gibi, HTTP taşıma bağlama öğesinde kimlik doğrulama düzenlerini ayarlayarak özel bir bağlamada kimlik doğrulama düzenlerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4020f-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4020f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4020f-122">See also</span></span>

- [<span data-ttu-id="4020f-123">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="4020f-123">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="4020f-124">Uç Noktalar: Adresler, Bağlamalar ve Anlaşmalar</span><span class="sxs-lookup"><span data-stu-id="4020f-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="4020f-125">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4020f-125">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)
- [<span data-ttu-id="4020f-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="4020f-126">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="4020f-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4020f-127">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="4020f-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="4020f-128">Custom Bindings</span></span>](../extending/custom-bindings.md)
