---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 0e0f03a30aa8e8679cf849aa75948e0bc2314fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857506"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="d53a6-102">Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d53a6-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="d53a6-103">İş akışı Hizmetleri, Windows Communication Foundation (WCF) Hizmetleri, bu nedenle, ya da kullanma seçeneği <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d53a6-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d53a6-104">Kullanılacak serileştirici tür olmayan iş akışı yazma, hizmetleri, hizmet veya işlemi sözleşme belirtilir.</span><span class="sxs-lookup"><span data-stu-id="d53a6-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="d53a6-105">WCF iş akışı hizmetleri oluştururken bu sözleşme kodu belirtmeyin, ancak bunlar sözleşme çıkarımı tarafından çalışma zamanında yerine oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d53a6-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="d53a6-106">Sözleşme çıkarımı hakkında daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="d53a6-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="d53a6-107">Seri hale getirici kullanarak belirtilen <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d53a6-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="d53a6-108">Bu tasarımcıda aşağıdaki çizimde gösterildiği gibi ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d53a6-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 ![SerializerOption özelliği, Özellikler penceresinde ayarlanıyor.](./media/configuring-serialization-in-a-workflow-service/setting-serializer-property.png)  
  
 <span data-ttu-id="d53a6-110">Seri hale getirici aşağıdaki örnekte gösterildiği gibi kodda de ayarlanabilir,</span><span class="sxs-lookup"><span data-stu-id="d53a6-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
  <span data-ttu-id="d53a6-111">Bilinen türler, iş akışı hizmetlerinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d53a6-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="d53a6-112">Bilinen türleri hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="d53a6-112">For more information about Known Types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="d53a6-113">Bilinen türler Tasarımcısı'nda veya kod içinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="d53a6-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="d53a6-114">Tasarımcıda bilinen türler belirtmek için KnownTypes özelliğin yanındaki üç nokta düğmesine tıklayın. **Özellikler penceresi** için bir <xref:System.ServiceModel.Activities.Receive> aşağıdaki çizimde gösterildiği gibi etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d53a6-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the **Properties Window** for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>   
  
 ![KnownTypes özellik iletişim kutusunun ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/known-types-properties.png)  
  
 <span data-ttu-id="d53a6-116">Bu, aramak ve bilinen türlerini belirtmek izin veren türü koleksiyonları Düzenleyici görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d53a6-116">This displays the Type Collections Editor that allows you to search for and specify known types.</span></span>  
  
 ![Tür Koleksiyonu Düzenleyicisi ekran görüntüsü.](./media/configuring-serialization-in-a-workflow-service/type-collection-editor.gif)  
  
 <span data-ttu-id="d53a6-118">Tıklayın **yeni türü eklemek** bağlamak ve bilinen türlerin koleksiyonuna eklemek için açılan listeyi seçin veya bir tür için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="d53a6-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="d53a6-119">Kod kullanımda bilinen türler belirtmek için <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> aşağıdaki örnekte gösterildiği gibi özelliği.</span><span class="sxs-lookup"><span data-stu-id="d53a6-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
