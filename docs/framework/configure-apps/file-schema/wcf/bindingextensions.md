---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: 6eed4e8c549bccb06d8d425b084554a2ec7a1183
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272767"
---
# <a name="bindingextensions"></a>\<bindingExtensions >
Bu bölümde, kullanıcı tanımlı bir makineden bağlama kullanımını etkinleştirir veya uygulama yapılandırma dosyası. Kullanıcı tanımlı kullanılarak bu koleksiyona bağlama ekleyebileceğiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği kullanıcı tanımlı bağlama, öğenin yanı sıra `name` tanımlanan bağlama kullanıcı adı özniteliği.  
  
 Bağlama uzantıları bir uç nokta yapılandırması bir parçası olarak kullanmak için kullanıcı tanımlı bağlamalar oluşturma olanağı sunar. Programlı olarak soyut sınıf uygulayan bir tür bir bağlama uzantısı olan <xref:System.ServiceModel.Channels.Binding>.  
  
 Aşağıdaki örnekte `add` öğesi hem de `name` özniteliği bir bağlama uzantının ekleneceği `bindingElementExtensions` yapılandırma dosyasının.  
  
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
  
 Yapılandırma yeteneklerini öğesine eklemek için yazmak ve kaydetmek kullanıcı gerekli bir `bindingSection` öğesi. Bunun hakkında daha fazla bilgi için bkz. <xref:System.Configuration> belgeleri.  
  
 Öğesi ve kendi yapılandırma türü tanımlandıktan sonra uzantıyı aşağıdaki örnekte gösterildiği gibi bir uç noktasının bir parçası kullanılabilir.  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
