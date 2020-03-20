---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: f894f2e044e35bb278f975ef2385a6b22a8bea49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185340"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="0c3dc-102">Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0c3dc-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="0c3dc-103">İş akışı hizmetleri Windows Communication Foundation (WCF) hizmetleridir ve <xref:System.Runtime.Serialization.DataContractSerializer> bu nedenle (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="0c3dc-104">İş akışı olmayan hizmetler yazarken kullanılacak serileştirici türü hizmet veya işletme sözleşmesinde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="0c3dc-105">WCF iş akışı hizmetleri oluştururken bu sözleşmeleri kod olarak belirtmezsiniz, daha çok sözleşme çıkarımı yla çalışma zamanında oluşturulurlar.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="0c3dc-106">Sözleşme çıkarımı hakkında daha fazla bilgi için [bkz.](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="0c3dc-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="0c3dc-107">Serileştirici <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="0c3dc-108">Bu, aşağıdaki resimde gösterildiği gibi tasarımcıda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![Özellikler Penceresinde SerializerOption özelliğini ayarlama.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="0c3dc-110">Serileştirici, aşağıdaki örnekte gösterildiği gibi kod olarak da ayarlanabilir,</span><span class="sxs-lookup"><span data-stu-id="0c3dc-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="0c3dc-111">Bilinen türler İş Akışı hizmetlerinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="0c3dc-112">Bilinen Türler hakkında daha fazla bilgi için [bkz.](data-contract-known-types.md)</span><span class="sxs-lookup"><span data-stu-id="0c3dc-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="0c3dc-113">Bilinen türler tasarımcıda veya kodda belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="0c3dc-114">Tasarımcıda bilinen türleri belirtmek için, aşağıdaki resimde gösterildiği gibi bir <xref:System.ServiceModel.Activities.Receive> etkinlik için Özellikler **Penceresinde** bilinen türleri özelliğinin yanındaki elips düğmesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>
  
 ![KnownTypes özellik iletişim kutusunun ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="0c3dc-116">Bu, bilinen türleri aramanızı ve belirtmenizi sağlayan Tür Koleksiyonları Düzenleyicisi'ni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Type Collections Düzenleyicisinin ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="0c3dc-118">Yeni **tür ekle** bağlantısını tıklatın ve bilinen türler koleksiyonuna eklemek için bir tür seçmek veya aramak için açılır açılır'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="0c3dc-119">Kodda bilinen türleri belirtmek <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> için aşağıdaki örnekte gösterildiği gibi özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c3dc-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
