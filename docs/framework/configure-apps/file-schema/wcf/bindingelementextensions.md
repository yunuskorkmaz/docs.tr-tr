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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b12752980e43944bb73f8adfde04bfb2d4dadf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="2b7b8-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="2b7b8-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="2b7b8-103">Bu bölümde özel bağlama öğesi bir makineden kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="2b7b8-104">Özel bağlama öğesi kullanarak bu koleksiyona eklemek `add` anahtar sözcüğü ve ayarı `type` bağlama öğesi uzantısı öğesinin özniteliği yanı sıra `name` özniteliği için özel bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="2b7b8-105">Özel bağlamalar bir parçası olarak kullanmak için kullanıcı tanımlı bağlama öğeleri oluşturmak kullanıcı bağlama uzantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="2b7b8-106">Programlı olarak bir bağlama soyut sınıf uygulayan bir tür uzantısıdır <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="2b7b8-107">Yapılandırma dosyasında `bindingElementExtensions` bölümü, bir uzantı öğesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="2b7b8-108">Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` özniteliği için bağlama uzantısı eklemek için `bindingElementExtensions` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="2b7b8-109">Yapılandırma yeteneklerini öğesine eklemek için kullanıcı yazmak ve kaydetmek gerek duyduğu bir `bindingElementExtensionSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="2b7b8-110">Bunun hakkında daha fazla bilgi için bkz: <xref:System.Configuration> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="2b7b8-111">Öğesini ve kendi yapılandırma türü tanımlandıktan sonra uzantı aşağıdaki örnekte gösterildiği gibi özel bağlama bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b7b8-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b7b8-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="2b7b8-113">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="2b7b8-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
