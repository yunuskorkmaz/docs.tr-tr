---
title: "Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b290-a2ee-4c3c-90ea-d0a7665096ae
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78f963f61c7ec67d6104a90c047ce78b0470568a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-serialization-in-a-workflow-service"></a><span data-ttu-id="fe59e-102">Bir İş Akışı Hizmetinde Seri Hale Getirmeyi Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fe59e-102">Configuring Serialization in a Workflow Service</span></span>
<span data-ttu-id="fe59e-103">İş akışı Hizmetleri [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri ve bu nedenle olması ya da kullanma seçeneğini <xref:System.Runtime.Serialization.DataContractSerializer> (varsayılan) veya <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fe59e-103">Workflow services are [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services and so have the option of using either the <xref:System.Runtime.Serialization.DataContractSerializer> (the default) or the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="fe59e-104">Kullanılacak serileştirici tür olmayan iş akışı yazma, hizmetleri hizmet veya işlemi sözleşmenin belirtilir.</span><span class="sxs-lookup"><span data-stu-id="fe59e-104">When writing non-workflow services the type of serializer to use is specified on the service or operation contract.</span></span> <span data-ttu-id="fe59e-105">Oluştururken [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yok belirttiğiniz bu iş akışı hizmetleri kod sözleşmeleri, ancak bunlar sözleşme çıkarım tarafından çalışma zamanında yerine oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="fe59e-105">When creating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] workflow services you don’t specify these contracts in code, but rather they are generated at runtime by contract inference.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fe59e-106">Sözleşme çıkarım, bkz: [iş akışında sözleşmeleri kullanma](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="fe59e-106"> contract inference, see  [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  <span data-ttu-id="fe59e-107">Seri hale getirici kullanarak belirtilen <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fe59e-107">The serializer is specified using the <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> property.</span></span> <span data-ttu-id="fe59e-108">Bu tasarımcıda aşağıdaki çizimde gösterildiği gibi ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe59e-108">This can be set in the designer as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fe59e-109">![Seri hale getirici ayarı](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span><span class="sxs-lookup"><span data-stu-id="fe59e-109">![Setting the serializer](../../../../docs/framework/wcf/feature-details/media/settingserialzier.png "SettingSerialzier")</span></span>  
  
 <span data-ttu-id="fe59e-110">Seri hale getirici aşağıdaki örnekte gösterildiği gibi kodunda da ayarlanabilir,</span><span class="sxs-lookup"><span data-stu-id="fe59e-110">The serializer can also be set in code as shown in the following example,</span></span>  
  
```  
Receive approveExpense = new Receive  
            {  
                OperationName = "ApproveExpense",  
                CanCreateInstance = true,  
                ServiceContractName = "FinanceService",  
                SerializerOption = SerializerOption.DataContractSerializer,  
                Content = ReceiveContent.Create(new OutArgument<Expense>(expense))  
            };  
```  
  
 <span data-ttu-id="fe59e-111">Bilinen türler iş akışı hizmetleri üzerinde de belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe59e-111">Known types can be specified on Workflow services as well.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fe59e-112">Türlerini görmek bilinen [veri sözleşmesi bilinen türleri](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe59e-112"> Known Types see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="fe59e-113">Bilinen türler Tasarımcısı'nda veya kod belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="fe59e-113">Known types can be specified in the designer or in code.</span></span> <span data-ttu-id="fe59e-114">Bilinen türler Tasarımcısı'nda belirtmek için için Özellikler penceresini KnownTypes özelliğinde yanındaki üç nokta düğmesini tıklatın bir <xref:System.ServiceModel.Activities.Receive> aşağıdaki çizimde gösterildiği gibi etkinlik.</span><span class="sxs-lookup"><span data-stu-id="fe59e-114">To specify known types in the designer, click the ellipsis button next to the KnownTypes property in the properties window for a <xref:System.ServiceModel.Activities.Receive> activity as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="fe59e-115">![KnownTypes özelliği](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span><span class="sxs-lookup"><span data-stu-id="fe59e-115">![KnownTypes property](../../../../docs/framework/wcf/feature-details/media/knowntypes.png "KnownTypes")</span></span>  
  
 <span data-ttu-id="fe59e-116">Bu, aramak ve bilinen türleri belirtmenize olanak sağlayacak türü koleksiyon Düzenleyicisi'ni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe59e-116">This will display the Type Collections Editor that will allow you to search for and specify known types.</span></span>  
  
 <span data-ttu-id="fe59e-117">![Bilinen türleri ekleme](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span><span class="sxs-lookup"><span data-stu-id="fe59e-117">![Adding Known Types](../../../../docs/framework/wcf/feature-details/media/typecollectionseditor.gif "TypeCollectionsEditor")</span></span>  
  
 <span data-ttu-id="fe59e-118">Tıklatın **yeni türü eklemek** bağlantı ve bilinen türleri koleksiyona eklemek için seçin ya da arama türü için aşağı açılan kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe59e-118">Click the **Add new type** link and use the drop down to select or search for a type to add to the known types collection.</span></span> <span data-ttu-id="fe59e-119">Bilinen türler kodu kullanımda belirtmek için <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> aşağıdaki örnekte gösterildiği gibi özelliği.</span><span class="sxs-lookup"><span data-stu-id="fe59e-119">To specify known types in code use the <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> property as shown in the following example.</span></span>  
  
```  
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
  
 <span data-ttu-id="fe59e-120">Bkz: seri hale getirme iş akışı hizmeti için yapılandırma gösteren tam bir kod örneğini görmek için [iş akışı hizmetleri iletilerinde biçimlendirme](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="fe59e-120">To see a complete code example showing how to configure serialization for a workflow service see [Formatting messages in Workflow Services](../../../../docs/framework/windows-workflow-foundation/samples/formatting-messages-in-workflow-services.md).</span></span>
