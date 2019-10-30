---
title: <bindingExtensions>
ms.date: 03/30/2017
ms.assetid: 8373f94d-d095-486f-8f1e-4ac2f72b58c7
ms.openlocfilehash: bd6aeb32e0994bceb9e56bcb1c6267f4cb64a5a4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039140"
---
# <a name="bindingextensions"></a><span data-ttu-id="16b7b-101">\<bindingExtensions ></span><span class="sxs-lookup"><span data-stu-id="16b7b-101">\<bindingExtensions></span></span>

<span data-ttu-id="16b7b-102">Bu bölüm, bir makineden ya da uygulama yapılandırma dosyasından Kullanıcı tanımlı bağlamanın kullanımını sunar.</span><span class="sxs-lookup"><span data-stu-id="16b7b-102">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="16b7b-103">`add` anahtar sözcüğünü kullanarak bu koleksiyona Kullanıcı tanımlı bir bağlama ekleyebilirsiniz ve öğenin `type` özniteliğini Kullanıcı tanımlı bağlamaya, `name` özniteliğini de Kullanıcı tanımlı bağlama adına ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="16b7b-103">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>

<span data-ttu-id="16b7b-104">Bağlama uzantıları, kullanıcının bir uç nokta yapılandırması olarak kullanılmak üzere Kullanıcı tanımlı bağlamalar oluşturmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="16b7b-104">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="16b7b-105">Programlı olarak, bağlama uzantısı <xref:System.ServiceModel.Channels.Binding>soyut sınıfı uygulayan bir türdür.</span><span class="sxs-lookup"><span data-stu-id="16b7b-105">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>

<span data-ttu-id="16b7b-106">Aşağıdaki örnek, yapılandırma dosyasının `bindingExtensions` bölümüne bir bağlama uzantısı eklemek için `add` öğesini ve `name` özniteliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="16b7b-106">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingExtensions` section of the configuration file:</span></span>

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

<span data-ttu-id="16b7b-107">Öğeye yapılandırma becerileri eklemek için, kullanıcının bir `bindingSection` öğesi yazması ve kaydetmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="16b7b-107">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="16b7b-108">Bunun hakkında daha fazla bilgi için <xref:System.Configuration> belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="16b7b-108">For more information on this, see the <xref:System.Configuration> documentation.</span></span>

<span data-ttu-id="16b7b-109">Öğesi ve yapılandırma türü tanımlandıktan sonra uzantı, aşağıdaki örnekte gösterildiği gibi bir uç noktanın parçası olarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="16b7b-109">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example:</span></span>

```xml
<services>
  <service name="MyService">
    <endpoint address="myAddress"
              binding="MyBinding" />
  </service>
</services>
```

## <a name="see-also"></a><span data-ttu-id="16b7b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16b7b-110">See also</span></span>

- [<span data-ttu-id="16b7b-111">Bağlamaları Genişletme</span><span class="sxs-lookup"><span data-stu-id="16b7b-111">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
