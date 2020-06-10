---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 5076f3d377a656cb96909cf8df01591dc6ab72b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597547"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="120c4-102">Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="120c4-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="120c4-103">Workflow Services Windows Communication Foundation (WCF) hizmetlerdir ve bu nedenle, <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya ' i kullanma seçeneğine sahiptir <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="120c4-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="120c4-104">İş akışı olmayan hizmetleri yazarken, hizmet veya işlem sözleşmesinde kullanılacak seri hale getirici türü belirtilir.</span><span class="sxs-lookup"><span data-stu-id="120c4-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="120c4-105">WCF iş akışı hizmetleri oluşturulurken bu sözleşmeleri kodda belirtmezsiniz, ancak bunun yerine sözleşme çıkarımı tarafından çalışma zamanında oluşturulmazlar.</span><span class="sxs-lookup"><span data-stu-id="120c4-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="120c4-106">Sözleşme çıkarımı hakkında daha fazla bilgi için bkz. [Iş akışında sözleşmeleri kullanma](using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="120c4-106">For more information about contract inference, see  [Using Contracts in Workflow](using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="120c4-107">Seri hale getirici, özelliği kullanılarak belirtilir <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> .</span><span class="sxs-lookup"><span data-stu-id="120c4-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="120c4-108">Bu, aşağıdaki çizimde gösterildiği gibi tasarımcıda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="120c4-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Özellikler penceresinde SerializerOption özelliği ayarlanıyor.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="120c4-110">Seri hale getirici, aşağıdaki örnekte gösterildiği gibi kodda de ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="120c4-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```csharp  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
  <span data-ttu-id="120c4-111">Bilinen türler, Iş akışı hizmetlerinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="120c4-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="120c4-112">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="120c4-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="120c4-113">Bilinen türler tasarımcıda veya kodda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="120c4-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="120c4-114">Tasarımcıda bilinen türleri belirtmek için, aşağıdaki çizimde gösterildiği gibi bir etkinliğin **Özellikler penceresinde** KnownTypes özelliğinin yanındaki üç nokta düğmesine tıklayın <xref:System.ServiceModel.Activities.Receive> .</span><span class="sxs-lookup"><span data-stu-id="120c4-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![KnownTypes özelliği iletişim kutusunun ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="120c4-116">Bu, bilinen türleri aramanızı ve belirtmenizi sağlayan tür koleksiyonları düzenleyicisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="120c4-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Tür koleksiyonları düzenleyicisinin ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="120c4-118">Bilinen türler koleksiyonuna eklemek üzere bir tür seçmek veya aramak için **yeni tür Ekle** bağlantısına tıklayın ve açılan eklentiyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="120c4-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="120c4-119">Kodda bilinen türleri belirtmek için, <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> Aşağıdaki örnekte gösterildiği gibi özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="120c4-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```csharp
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
            approveExpense.KnownTypes.Add(typeof(Travel));  
            approveExpense.KnownTypes.Add(typeof(Meal));  
```
