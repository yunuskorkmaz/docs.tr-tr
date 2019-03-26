---
title: WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 9f2c9944b424ba527fb20562706d5ad7fc3f8359
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465501"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="22690-102">WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma</span><span class="sxs-lookup"><span data-stu-id="22690-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="22690-103">WCF artık tek bir uç noktada birden çok kimlik doğrulama düzenleri belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="22690-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="22690-104">Ayrıca barındırılan web hizmetleri doğrudan IIS kimlik doğrulaması ayarlarını devralabilir.</span><span class="sxs-lookup"><span data-stu-id="22690-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="22690-105">Şirket içinde barındırılan hizmetler, hangi kimlik doğrulama düzenleri kullanılabilir belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22690-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="22690-106">IIS kimlik doğrulaması ayarlarını ayarlama hakkında daha fazla bilgi için bkz. [IIS kimlik doğrulaması](https://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="22690-106">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="22690-107">IIS barındırılan hizmetler</span><span class="sxs-lookup"><span data-stu-id="22690-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="22690-108">IIS barındırılan hizmetler için IIS içinde kullanmak istediğiniz kimlik doğrulama şeması ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="22690-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="22690-109">Ardından hizmetinizin web.config dosyasında bağlama Yapılandırması'nda clientCredential türü "InheritedFromHost" olarak aşağıdaki XML kod parçacığında gösterildiği gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="22690-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="22690-110">Yalnızca bir alt kümesini ServiceAuthenticationBehavior kullanarak hizmetinize kullanılacak kimlik doğrulama düzenleri istediğinizi belirtin veya \<serviceAuthenticationManager > öğesi.</span><span class="sxs-lookup"><span data-stu-id="22690-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="22690-111">Bu kodda yapılandırırken ServiceAuthenticationBehavior aşağıdaki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="22690-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="22690-112">Bu yapılandırma dosyasında yapılandırırken, kullandığınız \<serviceAuthenticationManager > aşağıdaki XML kod parçacığında gösterildiği gibi bir öğe.</span><span class="sxs-lookup"><span data-stu-id="22690-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="22690-113">Bu, yalnızca bir alt kümesini burada listelenen kimlik doğrulama düzenleri IIS'de ne seçili olursa bağlı olarak, hizmet uç noktasında uygulamak için kabul edilir garanti eder.</span><span class="sxs-lookup"><span data-stu-id="22690-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="22690-114">Bir geliştirici hariç tutabilirsiniz Bunun anlamı serviceAuthenticationManager listeden gt;(yok) listeden temel kimlik doğrulaması deyin ve IIS'de etkin olsa bile, bu hizmet uç noktasında uygulanmaz</span><span class="sxs-lookup"><span data-stu-id="22690-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="22690-115">Şirket içinde barındırılan hizmetleri</span><span class="sxs-lookup"><span data-stu-id="22690-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="22690-116">Ayarları devralmak için hiçbir IIS olduğundan şirket içinde barındırılan hizmetler biraz farklı bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="22690-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="22690-117">Burada kullandığınız \<serviceAuthenticationManager > öğesi veya ServiceAuthenticationBehavior devralınır kimlik doğrulama ayarlarını belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="22690-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="22690-118">Kod şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="22690-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="22690-119">Yapılandırmada şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="22690-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="22690-120">' İ tıklatın ve sonra aşağıdaki XML kod parçacığında gösterildiği gibi bağlama ayarlarında InheritFromHost belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22690-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="22690-121">Alternatif olarak, özel bir bağlama kimlik doğrulama düzeni belirtebilirsiniz, ayarlayarak kimlik doğrulama düzeni HTTP bağlama öğesi aşağıdaki yapılandırma kod parçacığında gösterildiği gibi taşıma.</span><span class="sxs-lookup"><span data-stu-id="22690-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22690-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22690-122">See also</span></span>
- [<span data-ttu-id="22690-123">Bağlamalar ve Güvenlik</span><span class="sxs-lookup"><span data-stu-id="22690-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="22690-124">Uç noktalar: Adresleri, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="22690-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="22690-125">Sistem Tarafından Sağlanan Bağlamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="22690-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="22690-126">Özel Bağlamalarla Güvenlik Özellikleri</span><span class="sxs-lookup"><span data-stu-id="22690-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="22690-127">Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="22690-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)
- [<span data-ttu-id="22690-128">Özel Bağlamalar</span><span class="sxs-lookup"><span data-stu-id="22690-128">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
