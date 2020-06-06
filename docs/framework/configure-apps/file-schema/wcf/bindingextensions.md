---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73039140"
---
# \<bindingExtensions>

Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından Kullanıcı tanımlı bağlamanın kullanımını sunar. Anahtar sözcüğünü kullanarak bu koleksiyona Kullanıcı tanımlı bir bağlama ekleyebilir `add` ve öğesinin özniteliğini Kullanıcı tanımlı bağlama adına ve `type` özniteliğini Kullanıcı tanımlı bağlamanın adına ayarlayarak ekleyebilirsiniz `name` .

Bağlama uzantıları, kullanıcının bir uç nokta yapılandırması olarak kullanılmak üzere Kullanıcı tanımlı bağlamalar oluşturmasını sağlar. Programlı olarak, bağlama uzantısı soyut sınıfı uygulayan bir türdür <xref:System.ServiceModel.Channels.Binding> .

Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne bir bağlama uzantısı eklemek için öğesini ve özniteliğini kullanır `bindingExtensions` :

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

Öğeye yapılandırma becerileri eklemek için, kullanıcının bir öğesi yazması ve kaydetmesi gerekir `bindingSection` . Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .

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
