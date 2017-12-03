---
title: "Araç kutusu hizmeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 294c530072b2d694f9aeb54d04b36d72bb6da637
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="toolbox-service"></a><span data-ttu-id="b8c1a-102">Araç kutusu hizmeti</span><span class="sxs-lookup"><span data-stu-id="b8c1a-102">Toolbox Service</span></span>
<span data-ttu-id="b8c1a-103">Bu örnek nasıl güncelleştirileceğini gösterir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] etkinlikler araç kutusu temel iş akışı bağlamı.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="b8c1a-104">Örnek özel bir aktivite seçili olduğundan dayalı araç kutusu içeriği değiştiren bir iş akışı içerir.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b8c1a-105">Tartışma</span><span class="sxs-lookup"><span data-stu-id="b8c1a-105">Discussion</span></span>  
 <span data-ttu-id="b8c1a-106">İş akışı yazma sırasında müşteriler genellikle içeriğe duyarlı olması için araç kutusu istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="b8c1a-107">Örneğin, kullanıcının belirli bir etkinliğe akışına eklendiğinde birkaç ek etkinlikler araç kutusu gösterir emin olmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="b8c1a-108">Etkinlikler iş akışını kaldırdıysanız, araç etki alanı gereksinimlerine bağlı olarak uygun şekilde tepki vermelidir.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="b8c1a-109">Yeniden barındırılan iş akışı Tasarımcısı'nda araç kutusu denetim ve iş akışı Model değişiklikleri esas emin olabilirsiniz, araç kutusu denetiminde uygun değişiklikleri konak tetikler.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="b8c1a-110">Bununla birlikte, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], araç kutusu kullanıcı tarafından denetlenmeyen ve böylece içeriğini değiştirmek için bir arabirim için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="b8c1a-111">`IActivityToolboxService`Bu arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="b8c1a-112">API'si aşağıdaki dört yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-112">The API provides the following four methods.</span></span>  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8c1a-113">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="b8c1a-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8c1a-114">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WorkflowSimulator.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b8c1a-115">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b8c1a-116">Workflow.xaml dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="b8c1a-117">Ekleme bir **CustomActivity** Araç Kutusu'ndan bırakarak.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="b8c1a-118">Adlı bir ek araç kategorisine dikkat edin: **yeni WF kategori** ek bir etkinliği ile **atamak**.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="b8c1a-119">Şimdi işaretini **CustomActivity** başka bir etkinlik içine sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="b8c1a-120">Öğe **atamak** kategorisinde **yeni WF kategori** altında araç kutusu artık kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="b8c1a-121">Ayrıca, kategoride başka bir öğe yok olduğundan, kategori de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="b8c1a-122">Seçin **CustomActivity** yeniden ve kategori ve **atamak** etkinlik geri eklendi.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8c1a-123">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8c1a-124">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8c1a-125">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8c1a-126">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b8c1a-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
