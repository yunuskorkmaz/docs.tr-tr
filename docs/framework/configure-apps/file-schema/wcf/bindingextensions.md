---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: ed55701e45d8580e37cf4776de6b9c5241e0548c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113041"
---
# <a name="bindingextensions"></a><span data-ttu-id="46f1d-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="46f1d-101">\<bindingExtensions></span></span>
<span data-ttu-id="46f1d-102">Bu bölümde, kullanıcı tanımlı bir makineden bağlama kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="46f1d-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="46f1d-103">Kullanıcı tanımlı kullanılarak bu koleksiyona bağlama ekleyebileceğiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği kullanıcı tanımlı bağlama, öğenin yanı sıra `name` tanımlanan bağlama kullanıcı adı özniteliği.</span><span class="sxs-lookup"><span data-stu-id="46f1d-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="46f1d-104">Bağlama uzantıları bir uç nokta yapılandırması bir parçası olarak kullanmak için kullanıcı tanımlı bağlamalar oluşturma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="46f1d-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="46f1d-105">Programlı olarak soyut sınıf uygulayan bir tür bir bağlama uzantısı olan <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="46f1d-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="46f1d-106">Aşağıdaki örnekte `add` öğesi hem de `name` özniteliği bir bağlama uzantının ekleneceği `bindingElementExtensions` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="46f1d-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="46f1d-107">Yapılandırma yeteneklerini öğesine eklemek için yazmak ve kaydetmek kullanıcı gerekli bir `bindingSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="46f1d-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="46f1d-108">Bunun hakkında daha fazla bilgi için bkz. <xref:System.Configuration> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="46f1d-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="46f1d-109">Öğesi ve kendi yapılandırma türü tanımlandıktan sonra uzantıyı aşağıdaki örnekte gösterildiği gibi bir uç noktasının bir parçası kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46f1d-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="46f1d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46f1d-110">See also</span></span>

- [<span data-ttu-id="46f1d-111">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="46f1d-111">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
