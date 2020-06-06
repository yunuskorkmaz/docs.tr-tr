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

<span data-ttu-id="00e54-101">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından Kullanıcı tanımlı bağlamanın kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="00e54-101">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="00e54-102">Anahtar sözcüğünü kullanarak bu koleksiyona Kullanıcı tanımlı bir bağlama ekleyebilir `add` ve öğesinin özniteliğini Kullanıcı tanımlı bağlama adına ve `type` özniteliğini Kullanıcı tanımlı bağlamanın adına ayarlayarak ekleyebilirsiniz `name` .</span><span class="sxs-lookup"><span data-stu-id="00e54-102">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="00e54-103">Bağlama uzantıları, kullanıcının bir uç nokta yapılandırması olarak kullanılmak üzere Kullanıcı tanımlı bağlamalar oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="00e54-103">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="00e54-104">Programlı olarak, bağlama uzantısı soyut sınıfı uygulayan bir türdür <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="00e54-104">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="00e54-105">Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne bir bağlama uzantısı eklemek için öğesini ve özniteliğini kullanır `bindingExtensions` :</span><span class="sxs-lookup"><span data-stu-id="00e54-105">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

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

<span data-ttu-id="00e54-106">Öğeye yapılandırma becerileri eklemek için, kullanıcının bir öğesi yazması ve kaydetmesi gerekir `bindingSection` .</span><span class="sxs-lookup"><span data-stu-id="00e54-106">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="00e54-107">Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="00e54-107">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="00e54-108">Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi bir uç noktanın parçası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="00e54-108">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="00e54-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00e54-109">See also</span></span>

- [<span data-ttu-id="00e54-110">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="00e54-110">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
