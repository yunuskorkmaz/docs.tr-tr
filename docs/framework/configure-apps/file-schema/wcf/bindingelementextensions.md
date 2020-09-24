---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 6ba97adfa696e00b4d6b75faf104c31436e25447
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151147"
---
# \<bindingElementExtensions>

<span data-ttu-id="22f27-101">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="22f27-101">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="22f27-102">Anahtar sözcüğünü kullanarak bu koleksiyona özel bir bağlama öğesi ekleyebilir `add` ve `type` öğesinin özniteliğini bir bağlama öğesi uzantısına ve `name` özniteliği de özel bağlama öğesine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22f27-102">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="22f27-103">Bağlama uzantıları, kullanıcının özel bağlamaların parçası olarak kullanılmak üzere Kullanıcı tanımlı bağlama öğeleri oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="22f27-103">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="22f27-104">Programlı olarak, bağlama uzantısı soyut sınıfı uygulayan bir türdür <xref:System.ServiceModel.Channels.BindingElement> .</span><span class="sxs-lookup"><span data-stu-id="22f27-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="22f27-105">Yapılandırma dosyasında, `bindingElementExtensions` bölümü bir uzantı öğesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="22f27-105">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="22f27-106">Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne bir bağlama uzantısı eklemek için öğesini ve özniteliğini kullanır `bindingElementExtensions` .</span><span class="sxs-lookup"><span data-stu-id="22f27-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingElementExtensions>
      <add name="udpTransport"
           type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingElementExtensions>
  </extensions>
</system.serviceModel>
```  
  
 <span data-ttu-id="22f27-107">Öğeye yapılandırma becerileri eklemek için, kullanıcının bir öğesi yazması ve kaydetmesi gerekir `bindingElementExtensionSection` .</span><span class="sxs-lookup"><span data-stu-id="22f27-107">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="22f27-108">Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="22f27-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="22f27-109">Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi özel bağlamanın bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="22f27-109">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>
  <binding name="test2">
    <udpTransport />
    <binaryMessageEncoding maxReadPoolSize="211"
                           maxWritePoolSize="2132"
                           maxSessionSize="3141" />
  </binding>
</customBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="22f27-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22f27-110">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="22f27-111">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="22f27-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
