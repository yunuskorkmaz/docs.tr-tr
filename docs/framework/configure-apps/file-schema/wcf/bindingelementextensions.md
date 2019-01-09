---
title: '&lt;bindingElementExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: ee67df95de715f0b21250bbf5739f84b4945d719
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151455"
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="c5025-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="c5025-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="c5025-103">Bu bölümde bir makineden özel bağlama öğesinin kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="c5025-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="c5025-104">Özel bağlama öğesini kullanarak bu koleksiyona ekleyebilirsiniz `add` anahtar sözcüğü ve ayarı `type` bir bağlama öğesi uzantısı için bir öğenin özniteliği hem de `name` özniteliği için özel bir bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5025-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="c5025-105">Bağlama uzantıları, özel bağlamalar bir parçası olarak kullanmak için kullanıcı tanımlı bağlama öğeleri oluşturmak kullanıcının etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="c5025-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="c5025-106">Programlı olarak soyut sınıf uygulayan bir tür bir bağlama uzantısı olan <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c5025-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="c5025-107">Yapılandırma dosyasında `bindingElementExtensions` bölümü, bir uzantı öğesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5025-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="c5025-108">Aşağıdaki örnekte `add` öğesi hem de `name` özniteliği bir bağlama uzantının ekleneceği `bindingElementExtensions` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="c5025-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="c5025-109">Yapılandırma yeteneklerini öğesine eklemek için yazmak ve kaydetmek kullanıcı gerekli bir `bindingElementExtensionSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c5025-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="c5025-110">Bunun hakkında daha fazla bilgi için bkz. <xref:System.Configuration> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="c5025-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="c5025-111">Öğesi ve kendi yapılandırma türü tanımlandıktan sonra uzantıyı aşağıdaki örnekte gösterildiği gibi özel bir bağlama bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5025-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5025-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5025-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="c5025-113">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="c5025-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
