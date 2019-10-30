---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039140"
---
# <a name="bindingextensions"></a>\<bindingExtensions >

Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından Kullanıcı tanımlı bağlamanın kullanımını sunar. `add` anahtar sözcüğünü kullanarak bu koleksiyona Kullanıcı tanımlı bir bağlama ekleyebilirsiniz ve öğenin `type` özniteliğini Kullanıcı tanımlı bağlamaya, `name` özniteliğini de Kullanıcı tanımlı bağlama adına ayarlayabilirsiniz.

Bağlama uzantıları, kullanıcının bir uç nokta yapılandırması olarak kullanılmak üzere Kullanıcı tanımlı bağlamalar oluşturmasını sağlar. Programlı olarak, bağlama uzantısı <xref:System.ServiceModel.Channels.Binding>soyut sınıfı uygulayan bir türdür.

Aşağıdaki örnek, yapılandırma dosyasının `bindingExtensions` bölümüne bir bağlama uzantısı eklemek için `add` öğesini ve `name` özniteliğini kullanır:

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

Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi bir uç noktanın parçası olarak kullanılabilir:

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
