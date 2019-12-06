---
title: Değişken ve Bağımsız Değişken İzleme
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: c5d3fe6626c22184edd83de6aedad8589ab2ef35
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837551"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="7b551-102">Değişken ve Bağımsız Değişken İzleme</span><span class="sxs-lookup"><span data-stu-id="7b551-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="7b551-103">Bir iş akışının yürütülmesi izlenirken, verileri ayıklamak genellikle yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="7b551-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="7b551-104">Bu, bir izleme kaydına erişirken yürütme sonrası ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="7b551-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="7b551-105">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]' de, izleme kullanarak bir iş akışındaki herhangi bir etkinliğin kapsamındaki görünür herhangi bir değişkeni veya bağımsız değişkeni ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b551-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="7b551-106">İzleme profilleri, verileri ayıklamayı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7b551-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="7b551-107">Değişkenler ve Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="7b551-107">Variables and Arguments</span></span>  
 <span data-ttu-id="7b551-108">Bir etkinlik bir ActivityStateRecord yayar olduğunda değişkenler ve bağımsız değişkenler ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="7b551-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="7b551-109">Değişken, yalnızca etkinliğin kapsamı içindeyse, ayıklama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b551-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="7b551-110">Bir etkinlik içinde Ayıklanacak bir değişken aşağıdaki şekilde belirtilir:</span><span class="sxs-lookup"><span data-stu-id="7b551-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
- <span data-ttu-id="7b551-111">Değişken adıyla bir değişken belirtilmişse, izleme geçerli etkinliğin içinde ve üst etkinliklerdeki değişkeni arar.</span><span class="sxs-lookup"><span data-stu-id="7b551-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="7b551-112">Değişken geçerli etkinlik kapsamında ve üst kapsamda aranır.</span><span class="sxs-lookup"><span data-stu-id="7b551-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
- <span data-ttu-id="7b551-113">Ayıklanacak değişkenler Name = "\*" kullanılarak belirtilmişse, izlenen geçerli etkinliğin içindeki tüm değişkenler ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="7b551-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="7b551-114">Bu durumda, kapsamdaki ancak üst etkinliklerde tanımlanan değişkenler ayıklanmaz.</span><span class="sxs-lookup"><span data-stu-id="7b551-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="7b551-115">Bağımsız değişkenler ayıklanırken, ayıklanan bağımsız değişkenler etkinliğin durumuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7b551-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="7b551-116">Bir etkinliğin durumu yürütüldüğü zaman, ayıklama için yalnızca `InArguments` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b551-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="7b551-117">Diğer etkinlik durumları (kapalı, hatalı, Iptal edildi) için, tüm bağımsız değişkenler, hem InArguments hem de OutArguments, ayıklama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7b551-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="7b551-118">Aşağıdaki örnek, etkinliğin `Closed` izleme kaydı yayıldığınızda değişkenleri ve bağımsız değişkenleri çıkaran bir etkinlik durumu sorgusu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b551-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="7b551-119">Değişkenler ve bağımsız değişkenler yalnızca bir <xref:System.Activities.Tracking.ActivityStateRecord> ayıklanıp <xref:System.Activities.Tracking.ActivityStateQuery>kullanılarak bir izleme profili içinde abone olunmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="7b551-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="7b551-120">Değişkenler ve bağımsız değişkenler Içinde depolanan bilgileri koruma</span><span class="sxs-lookup"><span data-stu-id="7b551-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="7b551-121">İzlenen bir değişken veya bağımsız değişken varsayılan olarak WF çalışma zamanı tarafından görünür hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="7b551-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="7b551-122">Bir iş akışı geliştiricisi, aşağıdaki adımları uygulayarak bu BT 'nin erişmesini koruyabilir:</span><span class="sxs-lookup"><span data-stu-id="7b551-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1. <span data-ttu-id="7b551-123">Bir değişkenin değerini şifreleyin.</span><span class="sxs-lookup"><span data-stu-id="7b551-123">Encrypt the value of a variable.</span></span>  
  
2. <span data-ttu-id="7b551-124">Bir değişkenin veya bağımsız değişkenin ayıklanmasını engellemek için bir izleme profili yazmayı denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b551-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3. <span data-ttu-id="7b551-125">Özel izleme katılımcıları için, WF kodunun değişkenlerde veya bağımsız değişkenlerde depolanan hassas bilgileri açıklamadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="7b551-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b551-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b551-126">See also</span></span>

- <span data-ttu-id="7b551-127">[Windows Server App Fabric Izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7b551-127">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="7b551-128">[App Fabric ile uygulamaları izleme](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7b551-128">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
