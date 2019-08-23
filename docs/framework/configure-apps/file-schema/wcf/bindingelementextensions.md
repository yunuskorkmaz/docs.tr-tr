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
# <a name="bindingelementextensions"></a>\<bindingElementExtensions >
Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar. `add` Anahtar sözcüğünü kullanarak bu koleksiyona özel bir bağlama öğesi ekleyebilir ve öğesinin `type` özniteliğini bir bağlama öğesi uzantısına `name` ve özniteliği de özel bağlama öğesine ayarlayabilirsiniz.  
  
 Bağlama uzantıları, kullanıcının özel bağlamaların parçası olarak kullanılmak üzere Kullanıcı tanımlı bağlama öğeleri oluşturmasını sağlar. Programlı olarak, bağlama uzantısı soyut sınıfı <xref:System.ServiceModel.Channels.BindingElement>uygulayan bir türdür. Yapılandırma dosyasında, `bindingElementExtensions` bölümü bir uzantı öğesi tanımlamak için kullanılır.  
  
 Aşağıdaki örnek, yapılandırma dosyasının `add` `bindingElementExtensions` bölümüne bir bağlama uzantısı eklemek için `name` öğesini ve özniteliğini kullanır.  
  
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
  
 Öğeye yapılandırma becerileri eklemek için, kullanıcının bir `bindingElementExtensionSection` öğesi yazması ve kaydetmesi gerekir. Bunun hakkında daha fazla bilgi için <xref:System.Configuration> belgelerine bakın.  
  
 Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi özel bağlamanın bir parçası olarak kullanılabilir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>
- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
