---
title: Değişken ve bağımsız değişken izleme
ms.date: 03/30/2017
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
ms.openlocfilehash: 4e59a6838d93a57302f0c894445ab9da5d4252ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625217"
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="de6af-102">Değişken ve bağımsız değişken izleme</span><span class="sxs-lookup"><span data-stu-id="de6af-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="de6af-103">Bir iş akışı yürütülmesini izlerken, genellikle verileri ayıklamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="de6af-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="de6af-104">Bu izleme kayıt sonrası yürütme erişirken ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="de6af-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="de6af-105">İçinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], herhangi bir görünür bir değişken veya bağımsız değişken izleme kullanarak iş akışı herhangi bir etkinliği kapsamında ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de6af-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="de6af-106">İzleme profilleri verileri ayıklamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="de6af-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="de6af-107">Değişkenler ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="de6af-107">Variables and Arguments</span></span>  
 <span data-ttu-id="de6af-108">Bir etkinlik bir ActivityStateRecord içerilip değişkenleri ve bağımsız değişkenler ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="de6af-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="de6af-109">Yalnızca etkinlik kapsamında olduğunda, bir değişken için ayıklama kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de6af-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="de6af-110">Bir etkinlik içinde ayıklanacak bir değişken, aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="de6af-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="de6af-111">Bir değişken değişken adıyla belirtilirse, izlenmekte olan geçerli etkinliği içinde ve üst etkinliklerde değişkeni İzleme arar.</span><span class="sxs-lookup"><span data-stu-id="de6af-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="de6af-112">Değişken, geçerli etkinlik kapsamda ve üst kapsam aranır.</span><span class="sxs-lookup"><span data-stu-id="de6af-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="de6af-113">Ayıklanacak değişkenleri adıyla belirtilmişse = "\*", geçerli etkinliği izlenmekte olan tüm değişkenler ayıklandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="de6af-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="de6af-114">Bu durumda değişkenleri, kapsamındaki ancak etkinlikleri ayıklanmadı üst öğede tanımlı.</span><span class="sxs-lookup"><span data-stu-id="de6af-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="de6af-115">Bağımsız değişkenler ayıklanırken, ayıklanan bağımsız değişkenleri etkinliğin durumuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="de6af-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="de6af-116">Bir etkinlik durumunu olduğunda Executing, ardından yalnızca `InArguments` ayıklama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de6af-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="de6af-117">Herhangi diğer etkinlik için durumu (kapalı, hatalı, iptal edildi), tüm bağımsız değişkenler, InArguments hem OutArguments, ayıklama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de6af-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="de6af-118">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgusu gösterir, etkinliğin `Closed` izleme kaydını yayılan.</span><span class="sxs-lookup"><span data-stu-id="de6af-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="de6af-119">Değişkenler ve bağımsız değişkenler ayıklanan yalnızca bir <xref:System.Activities.Tracking.ActivityStateRecord> ve bu nedenle içinde bir izleme abone olduğunuz kullanarak profil <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="de6af-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="de6af-120">Değişkenler ve bağımsız değişkenler içinde depolanan bilgi koruma</span><span class="sxs-lookup"><span data-stu-id="de6af-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="de6af-121">Varsayılan WF çalışma zamanı tarafından görünür hale izlenen bir değişken veya bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="de6af-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="de6af-122">Bir iş akışı Geliştirici aşağıdaki adımları izleyerek erişmesini koruyabilir:</span><span class="sxs-lookup"><span data-stu-id="de6af-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="de6af-123">Bir değişkenin değeri olarak şifreleyin.</span><span class="sxs-lookup"><span data-stu-id="de6af-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="de6af-124">Bir değişkenin veya bağımsız değişken ayıklama önlemek için bir izleme profili yazma denetimi.</span><span class="sxs-lookup"><span data-stu-id="de6af-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="de6af-125">Özel İzleme katılımcıları WF kod emin olmak için değişken veya bağımsız değişkenleri depolanan hassas bilgileri açıklamaz.</span><span class="sxs-lookup"><span data-stu-id="de6af-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de6af-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de6af-126">See also</span></span>
- [<span data-ttu-id="de6af-127">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="de6af-127">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="de6af-128">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="de6af-128">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
