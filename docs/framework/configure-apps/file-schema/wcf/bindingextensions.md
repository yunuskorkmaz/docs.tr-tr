---
description: 'Hakkında daha fazla bilgi edinin: <bindingExtensions>'
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: e568c7dd2da509709e5c85d3181d1808b1c636df
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639412"
---
# \<bindingExtensions>

<span data-ttu-id="8d3c9-102">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından Kullanıcı tanımlı bağlamanın kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="8d3c9-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="8d3c9-103">Anahtar sözcüğünü kullanarak bu koleksiyona Kullanıcı tanımlı bir bağlama ekleyebilir `add` ve öğesinin özniteliğini Kullanıcı tanımlı bağlama adına ve `type` özniteliğini Kullanıcı tanımlı bağlamanın adına ayarlayarak ekleyebilirsiniz `name` .</span><span class="sxs-lookup"><span data-stu-id="8d3c9-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="8d3c9-104">Bağlama uzantıları, kullanıcının bir uç nokta yapılandırması olarak kullanılmak üzere Kullanıcı tanımlı bağlamalar oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d3c9-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="8d3c9-105">Programlı olarak, bağlama uzantısı soyut sınıfı uygulayan bir türdür <xref:System.ServiceModel.Channels.Binding> .</span><span class="sxs-lookup"><span data-stu-id="8d3c9-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="8d3c9-106">Aşağıdaki örnek, `add` `name` yapılandırma dosyasının bölümüne bir bağlama uzantısı eklemek için öğesini ve özniteliğini kullanır `bindingExtensions` :</span><span class="sxs-lookup"><span data-stu-id="8d3c9-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

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

<span data-ttu-id="8d3c9-107">Öğeye yapılandırma becerileri eklemek için, kullanıcının bir öğesi yazması ve kaydetmesi gerekir `bindingSection` .</span><span class="sxs-lookup"><span data-stu-id="8d3c9-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="8d3c9-108">Bunun hakkında daha fazla bilgi için belgelerine bakın <xref:System.Configuration> .</span><span class="sxs-lookup"><span data-stu-id="8d3c9-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="8d3c9-109">Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi bir uç noktanın parçası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="8d3c9-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="8d3c9-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d3c9-110">See also</span></span>

- [<span data-ttu-id="8d3c9-111">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="8d3c9-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
