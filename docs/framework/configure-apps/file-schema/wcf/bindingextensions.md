---
title: '&lt;bindingExtensions&gt;'
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: c2b097926ac21dda6a86e1e21958e15c9b63b1c4
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148441"
---
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="a5692-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="a5692-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="a5692-103">Bu bölümde, kullanıcı tanımlı bir makineden bağlama kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="a5692-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="a5692-104">Kullanıcı tanımlı kullanılarak bu koleksiyona bağlama ekleyebileceğiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği kullanıcı tanımlı bağlama, öğenin yanı sıra `name` tanımlanan bağlama kullanıcı adı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a5692-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="a5692-105">Bağlama uzantıları bir uç nokta yapılandırması bir parçası olarak kullanmak için kullanıcı tanımlı bağlamalar oluşturma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="a5692-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="a5692-106">Programlı olarak soyut sınıf uygulayan bir tür bir bağlama uzantısı olan <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="a5692-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="a5692-107">Aşağıdaki örnekte `add` öğesi hem de `name` özniteliği bir bağlama uzantının ekleneceği `bindingElementExtensions` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="a5692-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="a5692-108">Yapılandırma yeteneklerini öğesine eklemek için yazmak ve kaydetmek kullanıcı gerekli bir `bindingSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="a5692-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="a5692-109">Bunun hakkında daha fazla bilgi için bkz. <xref:System.Configuration> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="a5692-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="a5692-110">Öğesi ve kendi yapılandırma türü tanımlandıktan sonra uzantıyı aşağıdaki örnekte gösterildiği gibi bir uç noktasının bir parçası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5692-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="a5692-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5692-111">See Also</span></span>  
 [<span data-ttu-id="a5692-112">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="a5692-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
