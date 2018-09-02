---
title: Araç kutusu hizmeti
ms.date: 03/30/2017
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
ms.openlocfilehash: 0b21f10c763f3f82591f947eb4cc48cf90f4ac79
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406468"
---
# <a name="toolbox-service"></a><span data-ttu-id="b9021-102">Araç kutusu hizmeti</span><span class="sxs-lookup"><span data-stu-id="b9021-102">Toolbox Service</span></span>
<span data-ttu-id="b9021-103">Bu örnek nasıl güncelleştirilebileceğini gösterir [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] etkinlikler araç kutusu temel iş akışı bağlama.</span><span class="sxs-lookup"><span data-stu-id="b9021-103">This sample demonstrates how to update the [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] Toolbox activities based on the context of the workflow.</span></span> <span data-ttu-id="b9021-104">Özel bir etkinlik seçili olduğundan bağlı olarak toolbox içeriklerin değiştiren bir iş akışı örneği içerir.</span><span class="sxs-lookup"><span data-stu-id="b9021-104">The sample contains a workflow that changes the toolbox contents based on whether a custom activity is selected.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b9021-105">Tartışma</span><span class="sxs-lookup"><span data-stu-id="b9021-105">Discussion</span></span>  
 <span data-ttu-id="b9021-106">İş akışı yazma sırasında müşteriler genellikle bir bağlama duyarlı olacak şekilde kendi araç kutusu istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b9021-106">During workflow authoring, customers generally want their Toolbox to be context sensitive.</span></span> <span data-ttu-id="b9021-107">Örneğin, kullanıcı iş akışını belirli bir etkinlik eklendiğinde birkaç ek etkinlikler araç kutusunu göstermesini sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b9021-107">For example, the user may want to ensure that the Toolbox shows a few additional activities when a specific activity is added to the workflow.</span></span> <span data-ttu-id="b9021-108">Etkinlikleri akışından kaldırılırsa, araç uygun etki alanı gereksinimlerine göre tepki.</span><span class="sxs-lookup"><span data-stu-id="b9021-108">If the activities are removed from the workflow, the toolbox should react appropriately based on the domain requirements.</span></span>  
  
 <span data-ttu-id="b9021-109">Yeniden barındırılan iş akışı tasarımcısında, araç kutusu denetim ve iş akışı modeli değişikliklere dayalı işaretlenmesini sağlayabilir, araç kutusu denetimi uygun değişiklikleri ana tetikler.</span><span class="sxs-lookup"><span data-stu-id="b9021-109">In a re-hosted workflow designer, you control the Toolbox control and can ensure that based on the Model changes in the workflow, the host triggers appropriate changes in the Toolbox control.</span></span> <span data-ttu-id="b9021-110">Bununla birlikte, [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], araç çubuğu kullanıcı tarafından denetlenen ve bu nedenle bir arabirim içeriğini değiştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b9021-110">However, in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], the toolbox is not controlled by the user and thus an interface is required to modify its contents.</span></span> <span data-ttu-id="b9021-111">`IActivityToolboxService` Bu arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="b9021-111">`IActivityToolboxService` is that interface.</span></span>  
  
 <span data-ttu-id="b9021-112">API'si aşağıdaki dört yöntemi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9021-112">The API provides the following four methods.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b9021-113">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="b9021-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b9021-114">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], WorkflowSimulator.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b9021-114">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the WorkflowSimulator.sln solution file.</span></span>  
  
2.  <span data-ttu-id="b9021-115">CTRL + SHIFT + B tuşlarına basarak çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b9021-115">Build the solution by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b9021-116">Workflow.xaml dosyası açın.</span><span class="sxs-lookup"><span data-stu-id="b9021-116">Open the Workflow.xaml file.</span></span>  
  
4.  <span data-ttu-id="b9021-117">Ekleme bir **CustomActivity** bunu araç kutusundan sürükleyip bırakarak.</span><span class="sxs-lookup"><span data-stu-id="b9021-117">Add a **CustomActivity** by dragging and dropping it from the toolbox.</span></span> <span data-ttu-id="b9021-118">Bir ek araç kutusu kategorisi adlı dikkat edin: **yeni WF kategori** ek bir etkinlikle **atama**.</span><span class="sxs-lookup"><span data-stu-id="b9021-118">Notice that an additional Toolbox category called: **New WF Category** with an additional activity **Assign**.</span></span>  
  
5.  <span data-ttu-id="b9021-119">Artık seçimini kaldırın **CustomActivity** başka bir etkinlik içine sürükleyerek.</span><span class="sxs-lookup"><span data-stu-id="b9021-119">Now unselect the **CustomActivity** by dragging another activity into it.</span></span>  
  
6.  <span data-ttu-id="b9021-120">Öğe **atama** kategorisinde **yeni WF kategori** araç kutusu altında artık kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b9021-120">The item **Assign** in the category **New WF Category** under Toolbox is now removed.</span></span> <span data-ttu-id="b9021-121">Ayrıca, kategorisinde başka bir öğe yok olduğundan, kategori de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="b9021-121">Also, because there are no more items left in the category, the category is removed as well.</span></span>  
  
7.  <span data-ttu-id="b9021-122">Seçin **CustomActivity** yeniden ve kategori ve **atama** etkinlik yeniden eklenir.</span><span class="sxs-lookup"><span data-stu-id="b9021-122">Select the **CustomActivity** again and the category and **Assign** activity is added back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9021-123">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="b9021-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b9021-124">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b9021-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b9021-125">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="b9021-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9021-126">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b9021-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`
