---
title: Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma
ms.date: 03/30/2017
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
ms.openlocfilehash: 63a5860bd428fd4ce7fe01d7901427c85b2d5609
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154118"
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="a33fd-102">Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a33fd-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="a33fd-103">İş akışı Hizmetleri, Windows Communication Foundation (WCF) Hizmetleri, bu nedenle, ya da kullanma seçeneği <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a33fd-103">Workflow services are Windows Communication Foundation (WCF) services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="a33fd-104">Kullanılacak serileştirici tür olmayan iş akışı yazma, hizmetleri, hizmet veya işlemi sözleşme belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a33fd-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="a33fd-105">WCF iş akışı hizmetleri oluştururken bu sözleşme kodu belirtmeyin, ancak bunlar sözleşme çıkarımı tarafından çalışma zamanında yerine oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a33fd-105">When creating WCF workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> <span data-ttu-id="a33fd-106">Sözleşme çıkarımı hakkında daha fazla bilgi için bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="a33fd-106">For more information about contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="a33fd-107">Seri hale getirici kullanarak belirtilen <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a33fd-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="a33fd-108">Bu tasarımcıda aşağıdaki çizimde gösterildiği gibi ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="a33fd-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a33fd-109">![Seri hale getirici ayarlama](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="a33fd-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="a33fd-110">Seri hale getirici aşağıdaki örnekte gösterildiği gibi kodda de ayarlanabilir,</span><span class="sxs-lookup"><span data-stu-id="a33fd-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
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
  
 <span data-ttu-id="a33fd-111">Bilinen türler, iş akışı hizmetlerinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a33fd-111">Known types can be specified on Workflow services as well.</span></span> <span data-ttu-id="a33fd-112">Bilinen türleri hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="a33fd-112">For more information about Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="a33fd-113">Bilinen türler Tasarımcısı'nda veya kod içinde belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="a33fd-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="a33fd-114">Tasarımcıda bilinen türler belirtmek için Özellikler penceresinde KnownTypes özelliğin yanındaki üç nokta düğmesini tıklayın. bir <xref:System.ServiceModel.Activities.Receive> aşağıdaki çizimde gösterildiği gibi etkinlik.</span><span class="sxs-lookup"><span data-stu-id="a33fd-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a33fd-115">![KnownTypes özelliği](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="a33fd-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="a33fd-116">Bu, arayın ve bilinen türler belirtmek olanak tanıyacak türü koleksiyonları Düzenleyicisi'ni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a33fd-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="a33fd-117">![Bilinen türleri ekleme](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="a33fd-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="a33fd-118">Tıklayın **yeni türü eklemek** bağlamak ve bilinen türlerin koleksiyonuna eklemek için açılan listeyi seçin veya bir tür için arama yapın.</span><span class="sxs-lookup"><span data-stu-id="a33fd-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="a33fd-119">Kod kullanımda bilinen türler belirtmek için <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> aşağıdaki örnekte gösterildiği gibi özelliği.</span><span class="sxs-lookup"><span data-stu-id="a33fd-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
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
