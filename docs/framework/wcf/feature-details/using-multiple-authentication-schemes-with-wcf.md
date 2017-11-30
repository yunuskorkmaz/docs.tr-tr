---
title: "WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: db2545470c416fe066226124fb7833ef5d9e5d13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="42fa8-102">WCF ile Birden Fazla Kimlik Doğrulama Şeması Kullanma</span><span class="sxs-lookup"><span data-stu-id="42fa8-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="42fa8-103">WCF artık tek bir noktadaki birden çok kimlik doğrulama şemasını belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="42fa8-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="42fa8-104">Ayrıca barındırılan web hizmetleri doğrudan IIS kimlik doğrulaması ayarlarını devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42fa8-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="42fa8-105">Kendini barındıran Hizmetleri düzenleri kullanılabilmesi için hangi kimlik doğrulama belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42fa8-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="42fa8-106">IIS'de kimlik doğrulama ayarlarını ayarlama hakkında daha fazla bilgi için bkz: [IIS kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="42fa8-106">For more information about setting authentication settings in IIS, see [IIS Authentication](http://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="42fa8-107">IIS barındırılan hizmetleri</span><span class="sxs-lookup"><span data-stu-id="42fa8-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="42fa8-108">IIS barındırılan hizmetler için IIS içinde kullanmak istediğiniz kimlik doğrulama şemasını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="42fa8-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="42fa8-109">Ardından hizmetinizin web.config dosyasına bağlama yapılandırmanızda clientCredential türü "InheritedFromHost" olarak aşağıdaki XML parçacığında gösterildiği gibi belirtin:</span><span class="sxs-lookup"><span data-stu-id="42fa8-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
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
  
 <span data-ttu-id="42fa8-110">Yalnızca bir alt kümesini ServiceAuthenticationBehavior kullanarak, hizmetiniz ile kullanılacak kimlik doğrulama şemasını istediğinizi belirtin veya \<serviceAuthenticationManager > öğesi.</span><span class="sxs-lookup"><span data-stu-id="42fa8-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="42fa8-111">Bu kodda yapılandırırken ServiceAuthenticationBehavior aşağıdaki kod parçacığında gösterildiği gibi kullanın.</span><span class="sxs-lookup"><span data-stu-id="42fa8-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="42fa8-112">Bu yapılandırma dosyasında yapılandırırken kullandığınız \<serviceAuthenticationManager > aşağıdaki XML parçacığında gösterildiği gibi öğesi.</span><span class="sxs-lookup"><span data-stu-id="42fa8-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="42fa8-113">Bu, yalnızca bir alt kümesini burada listelenen kimlik doğrulama şemasını IIS'de belirlemiş bağlı olarak hizmet uç noktası üzerinde uygulamak için değerlendirilir güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="42fa8-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="42fa8-114">Bir geliştirici dışlayabilirsiniz Bunun anlamı deyin listeden temel kimlik doğrulama serviceAuthenticationManager listeden kaldırarak ve IIS etkinleştirilmiş olsa dahi, üzerinde hizmet uç noktası uygulanmaz</span><span class="sxs-lookup"><span data-stu-id="42fa8-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="42fa8-115">Kendini barındıran Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="42fa8-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="42fa8-116">Ayarları devralmak için hiçbir IIS olduğundan kendini barındıran Hizmetleri biraz farklı bir şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="42fa8-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="42fa8-117">Burada kullandığınız \<serviceAuthenticationManager > öğesi veya ServiceAuthenticationBehavior devralınır kimlik doğrulama ayarlarını belirtin.</span><span class="sxs-lookup"><span data-stu-id="42fa8-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="42fa8-118">Kodda şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="42fa8-118">In code it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="42fa8-119">Yapılandırma dosyasında şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="42fa8-119">In config, it looks like this:</span></span>  
  
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
  
 <span data-ttu-id="42fa8-120">Ve ardından aşağıdaki XML parçacığında gösterildiği gibi bağlama ayarlarında InheritFromHost belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42fa8-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
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
  
 <span data-ttu-id="42fa8-121">Alternatif olarak, kimlik doğrulama şemasını özel bir bağlama belirtin, ayarlayarak HTTP kimlik doğrulama şemasını bağlama öğesi, aşağıdaki yapılandırma parçacığında gösterildiği gibi taşıma.</span><span class="sxs-lookup"><span data-stu-id="42fa8-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42fa8-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42fa8-122">See Also</span></span>  
 [<span data-ttu-id="42fa8-123">Bağlamalar ve güvenlik</span><span class="sxs-lookup"><span data-stu-id="42fa8-123">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="42fa8-124">Uç noktalar: Adresler, bağlamalar ve sözleşmeler</span><span class="sxs-lookup"><span data-stu-id="42fa8-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
 [<span data-ttu-id="42fa8-125">Sistem tarafından sağlanan bağlamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="42fa8-125">Configuring System-Provided Bindings</span></span>](../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="42fa8-126">Özel bağlamalarla güvenlik özellikleri</span><span class="sxs-lookup"><span data-stu-id="42fa8-126">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="42fa8-127">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="42fa8-127">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="42fa8-128">Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="42fa8-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="42fa8-129">Özel bağlamalar</span><span class="sxs-lookup"><span data-stu-id="42fa8-129">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
