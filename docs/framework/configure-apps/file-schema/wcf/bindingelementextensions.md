---
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: c323a65ace332d2ecd1e03330dddbe7ca17ff5bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926364"
---
# <a name="bindingelementextensions"></a><span data-ttu-id="ada80-101">\<bindingElementExtensions ></span><span class="sxs-lookup"><span data-stu-id="ada80-101">\<bindingElementExtensions></span></span>
<span data-ttu-id="ada80-102">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="ada80-102">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="ada80-103">`add` Anahtar sözcüğünü kullanarak bu koleksiyona özel bir bağlama öğesi ekleyebilir ve öğesinin `type` özniteliğini bir bağlama öğesi uzantısına `name` ve özniteliği de özel bağlama öğesine ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ada80-103">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="ada80-104">Bağlama uzantıları, kullanıcının özel bağlamaların parçası olarak kullanılmak üzere Kullanıcı tanımlı bağlama öğeleri oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="ada80-104">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="ada80-105">Programlı olarak, bağlama uzantısı soyut sınıfı <xref:System.ServiceModel.Channels.BindingElement>uygulayan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="ada80-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="ada80-106">Yapılandırma dosyasında, `bindingElementExtensions` bölümü bir uzantı öğesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ada80-106">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="ada80-107">Aşağıdaki örnek, yapılandırma dosyasının `add` `bindingElementExtensions` bölümüne bir bağlama uzantısı eklemek için `name` öğesini ve özniteliğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ada80-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ada80-108">Öğeye yapılandırma becerileri eklemek için, kullanıcının bir `bindingElementExtensionSection` öğesi yazması ve kaydetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ada80-108">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="ada80-109">Bunun hakkında daha fazla bilgi için <xref:System.Configuration> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="ada80-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="ada80-110">Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi özel bağlamanın bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ada80-110">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ada80-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ada80-111">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [<span data-ttu-id="ada80-112">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="ada80-112">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
