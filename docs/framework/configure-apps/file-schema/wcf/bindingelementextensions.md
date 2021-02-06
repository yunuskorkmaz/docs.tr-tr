---
description: 'Hakkında daha fazla bilgi edinin: <bindingElementExtensions>'
title: <bindingElementExtensions>
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: 4c1b4b924906b1a6dc143588a057129ca5ce8f40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639425"
---
# \<bindingElementExtensions>

Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından özel bağlama öğesinin kullanımını sunar. Anahtar sözcüğünü kullanarak bu koleksiyona özel bir bağlama öğesi ekleyebilir `add` ve `type` öğesinin özniteliğini bir bağlama öğesi uzantısına ve `name` özniteliği de özel bağlama öğesine ayarlayabilirsiniz.  
  
 Bağlama uzantıları, kullanıcının özel bağlamaların parçası olarak kullanılmak üzere Kullanıcı tanımlı bağlama öğeleri oluşturmasını sağlar. Programlı olarak, bağlama uzantısı soyut sınıfı uygulayan bir türdür <xref:System.ServiceModel.Channels.BindingElement> . Yapılandırma dosyasında, `bindingElementExtensions` bölümü bir uzantı öğesi tanımlamak için kullanılır.  
  
 Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne bir bağlama uzantısı eklemek için öğesini ve özniteliğini kullanır `bindingElementExtensions` .  
  
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
  
 Öğeye yapılandırma becerileri eklemek için, kullanıcının bir öğesi yazması ve kaydetmesi gerekir `bindingElementExtensionSection` . Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .  
  
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
