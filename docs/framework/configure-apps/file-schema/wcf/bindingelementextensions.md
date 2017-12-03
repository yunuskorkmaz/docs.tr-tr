---
title: '&lt;bindingElementExtensions&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fdc7c68ff7e672a5adf044bbe0200563772a58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbindingelementextensionsgt"></a>&lt;bindingElementExtensions&gt;
Bu bölümde özel bağlama öğesi bir makineden kullanımını etkinleştirir veya uygulama yapılandırma dosyası. Özel bağlama öğesi kullanarak bu koleksiyona eklemek `add` anahtar sözcüğü ve ayarı `type` bağlama öğesi uzantısı öğesinin özniteliği yanı sıra `name` özniteliği için özel bağlama öğesi.  
  
 Özel bağlamalar bir parçası olarak kullanmak için kullanıcı tanımlı bağlama öğeleri oluşturmak kullanıcı bağlama uzantıları sağlar. Programlı olarak bir bağlama soyut sınıf uygulayan bir tür uzantısıdır <xref:System.ServiceModel.Channels.BindingElement>. Yapılandırma dosyasında `bindingElementExtensions` bölümü, bir uzantı öğesi tanımlamak için kullanılır.  
  
 Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` özniteliği için bağlama uzantısı eklemek için `bindingElementExtensions` yapılandırma dosyasının.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <bindingElementExtensions>  
           <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportSection, UdpTransport,  
                Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </bindingElementExtensions>  
    </extensions>  
</system.serviceModel>  
```  
  
 Yapılandırma yeteneklerini öğesine eklemek için kullanıcı yazmak ve kaydetmek gerek duyduğu bir `bindingElementExtensionSection` öğesi. Bunun hakkında daha fazla bilgi için bkz: <xref:System.Configuration> belgeleri.  
  
 Öğesini ve kendi yapılandırma türü tanımlandıktan sonra uzantı aşağıdaki örnekte gösterildiği gibi özel bağlama bir parçası olarak kullanılabilir.  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)
