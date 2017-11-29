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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c02af972ad52119af07da404a61fd3afc0facbeb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltbindingextensionsgt"></a><span data-ttu-id="e97a1-102">&lt;bindingExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="e97a1-102">&lt;bindingExtensions&gt;</span></span>
<span data-ttu-id="e97a1-103">Bu bölümde bir makineden bağlama kullanıcı tanımlı bir kullanımını etkinleştirir veya uygulama yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="e97a1-103">This section enables the use of a user defined binding from a machine or application configuration file.</span></span> <span data-ttu-id="e97a1-104">Kullanarak bu koleksiyona bağlama kullanıcı tanımlı bir ekleyebilirsiniz `add` anahtar sözcüğü ve ayarı `type` özniteliği bağlama, kullanıcı tanımlı bir öğenin yanı sıra `name` kullanıcı adına özniteliği tanımlı bağlama.</span><span class="sxs-lookup"><span data-stu-id="e97a1-104">You can add a user defined binding to this collection by using the `add` keyword, and setting the `type` attribute of the element to a user defined binding, as well as the `name` attribute to the name of the user defined binding.</span></span>  
  
 <span data-ttu-id="e97a1-105">Bağlama uzantıları kullanıcı tanımlı bağlamalar parçası olarak kullanmak için bir uç nokta yapılandırması oluşturmak kullanıcının etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e97a1-105">Binding extensions enable the user to create user-defined bindings for use as part an endpoint configuration.</span></span> <span data-ttu-id="e97a1-106">Programlı olarak bir bağlama soyut sınıf uygulayan bir tür uzantısıdır <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="e97a1-106">Programmatically, a binding extension is a type that implements the abstract class <xref:System.ServiceModel.Channels.Binding>.</span></span>  
  
 <span data-ttu-id="e97a1-107">Aşağıdaki örnek kullanır `add` öğenin yanı sıra `name` özniteliği için bağlama uzantısı eklemek için `bindingElementExtensions` yapılandırma dosyasının.</span><span class="sxs-lookup"><span data-stu-id="e97a1-107">The following example uses the `add` element, as well as the `name` attribute to add a binding extension to the `bindingElementExtensions` section of the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="e97a1-108">Yapılandırma yeteneklerini öğesine eklemek için kullanıcı yazmak ve kaydetmek gerek duyduğu bir `bindingSection` öğesi.</span><span class="sxs-lookup"><span data-stu-id="e97a1-108">To add configuration abilities to the element, the user needs to write and register a `bindingSection` element.</span></span> <span data-ttu-id="e97a1-109">Bunun hakkında daha fazla bilgi için bkz: <xref:System.Configuration> belgeleri.</span><span class="sxs-lookup"><span data-stu-id="e97a1-109">For more information on this, see the <xref:System.Configuration> documentation.</span></span>  
  
 <span data-ttu-id="e97a1-110">Öğesini ve kendi yapılandırma türü tanımlandıktan sonra uzantı aşağıdaki örnekte gösterildiği gibi bir uç nokta bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e97a1-110">After the element and its configuration type are defined, the extension can be used as part of an endpoint as shown in the following example.</span></span>  
  
```xml  
<services>  
    <service name="MyService">  
        <endpoint address="myAddress" binding="MyBinding" />  
    </service>  
</services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e97a1-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e97a1-111">See Also</span></span>  
 [<span data-ttu-id="e97a1-112">Bağlamaları genişletme</span><span class="sxs-lookup"><span data-stu-id="e97a1-112">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
