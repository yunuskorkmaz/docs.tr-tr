---
title: '&lt;bindingElementExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: bb597fc0-c947-451c-afda-bf23d42f4f4d
ms.openlocfilehash: a93474a4f86fac2a6b211652e3ddc86901cf197f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747755"
---
# <a name="ltbindingelementextensionsgt"></a><span data-ttu-id="5679c-102">&lt;bindingElementExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="5679c-102">&lt;bindingElementExtensions&gt;</span></span>
<span data-ttu-id="5679c-103">Bu bölümde özel bağlama öğesi bir makineden kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="5679c-103">This section enables the use of a custom binding element from a machine or application configuration file.</span></span> <span data-ttu-id="5679c-104">Özel bağlama öğesi kullanarak bu koleksiyona eklemek `add` anahtar sözcüğü ve ayarı `type` bağlama öğesi uzantısı öğesinin özniteliği yanı sıra `name` özniteliği için özel bağlama öğesi.</span><span class="sxs-lookup"><span data-stu-id="5679c-104">You can add a custom binding element to this collection by using the `add` keyword, and setting the `type` attribute of the element to a binding element extension, as well as the `name` attribute to the custom binding element.</span></span>  
  
 <span data-ttu-id="5679c-105">Özel bağlamalar bir parçası olarak kullanmak için kullanıcı tanımlı bağlama öğeleri oluşturmak kullanıcı bağlama uzantıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5679c-105">Binding extensions enable the user to create user-defined binding elements for use as part of custom bindings.</span></span> <span data-ttu-id="5679c-106">Programlı olarak bir bağlama soyut sınıf uygulayan bir tür uzantısıdır <xref:System.ServiceModel.Channels.BindingElement>.</span><span class="sxs-lookup"><span data-stu-id="5679c-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.BindingElement>.</span></span> <span data-ttu-id="5679c-107">Yapılandırma dosyasında `bindingElementExtensions` bölümü, bir uzantı öğesi tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5679c-107">In the configuration file, the `bindingElementExtensions` section is used to define an extension element.</span></span>  
  
 <span data-ttu-id="5679c-108">Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` özniteliği için bağlama uzantısı eklemek için `bindingElementExtensions` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="5679c-108">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="5679c-109">Yapılandırma yeteneklerini öğesine eklemek için kullanıcı yazmak ve kaydetmek gerek duyduğu bir `bindingElementExtensionSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="5679c-109">To add configuration abilities to the element, the user needs to write and register a `bindingElementExtensionSection` element.</span></span> <span data-ttu-id="5679c-110">Bunun hakkında daha fazla bilgi için bkz: <xref:System.Configuration> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="5679c-110">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="5679c-111">Öğesini ve kendi yapılandırma türü tanımlandıktan sonra uzantı aşağıdaki örnekte gösterildiği gibi özel bağlama bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5679c-111">After the element and its configuration type are defined, the extension can be used as part of a custom binding as shown in the following example.</span></span>  
  
```xml  
<customBinding>  
     <binding name="test2">  
         <udpTransport />  
         <binaryMessageEncoding maxReadPoolSize="211" maxWritePoolSize="2132"  
             maxSessionSize="3141" />  
         </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5679c-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5679c-112">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>  
 [<span data-ttu-id="5679c-113">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="5679c-113">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
