---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 34ba198de33ae4aa1882d13f74bd2d538999a0c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919785"
---
# <a name="bindingextensions"></a>\<bindingExtensions >
Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından Kullanıcı tanımlı bağlamanın kullanımını sunar. `add` Anahtar sözcüğünü kullanarak bu koleksiyona Kullanıcı tanımlı bir bağlama ekleyebilir ve öğesinin `type` `name` özniteliğini Kullanıcı tanımlı bağlama adına ve özniteliğini Kullanıcı tanımlı bağlamanın adına ayarlayarak ekleyebilirsiniz.  
  
 Bağlama uzantıları, kullanıcının bir uç nokta yapılandırması olarak kullanılmak üzere Kullanıcı tanımlı bağlamalar oluşturmasını sağlar. Programlı olarak, bağlama uzantısı soyut sınıfı <xref:System.ServiceModel.Channels.Binding>uygulayan bir türdür.  
  
 Aşağıdaki örnek, yapılandırma dosyasının `add` `bindingElementExtensions` bölümüne bir bağlama uzantısı eklemek için `name` öğesini ve özniteliğini kullanır.  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
      <add name="MyBinding"
           type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </bindingExtensions>
  </extensions>
</system.serviceModel>
```  
  
 Öğeye yapılandırma becerileri eklemek için, kullanıcının bir `bindingSection` öğesi yazması ve kaydetmesi gerekir. Bunun hakkında daha fazla bilgi için <xref:System.Configuration> belgelerine bakın.  
  
 Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi bir uç noktanın parçası olarak kullanılabilir.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağlamaları Genişletme](../../../wcf/extending/extending-bindings.md)
