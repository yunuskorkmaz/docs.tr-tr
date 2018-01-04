---
title: '&lt;bindingExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58392fc71508c3cf6ad7178396a927cf0e84c98f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingextensionsgt"></a>&lt;bindingExtensions&gt;
Bu bölümde bir makineden bağlama kullanıcı tanımlı bir kullanımını etkinleştirir veya uygulama yapılandırma dosyası. Kullanarak bu koleksiyona bağlama kullanıcı tanımlı bir ekleyebilirsiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği bağlama, kullanıcı tanımlı bir öğenin yanı sıra `name` kullanıcı adına özniteliği tanımlı bağlama.  
  
 Bağlama uzantıları kullanıcı tanımlı bağlamalar parçası olarak kullanmak için bir uç nokta yapılandırması oluşturmak kullanıcının etkinleştirir. Programlı olarak bir bağlama soyut sınıf uygulayan bir tür uzantısıdır <xref:System.ServiceModel.Channels.Binding>.  
  
 Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` özniteliği için bağlama uzantısı eklemek için `bindingElementExtensions` yapılandırma dosyasının.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingExtensions>  
           <add name="MyBinding" type="Microsoft.ServiceModel.Samples.MyBinding, MyBinding,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Yapılandırma yeteneklerini öğesine eklemek için kullanıcı yazmak ve kaydetmek gerek duyduğu bir `bindingSection` öğesi. Bunun hakkında daha fazla bilgi için bkz: <xref:System.Configuration> belgeleri.  
  
 Öğesini ve kendi yapılandırma türü tanımlandıktan sonra uzantı aşağıdaki örnekte gösterildiği gibi bir uç nokta bir parçası olarak kullanılabilir.  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağlamaları Genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
