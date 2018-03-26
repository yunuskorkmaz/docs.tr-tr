---
title: Değişken ve bağımsız değişkeni izleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c0857830b52b2f71df5d81f4bd232b62b894da63
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="b58ff-102">Değişken ve bağımsız değişkeni izleme</span><span class="sxs-lookup"><span data-stu-id="b58ff-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="b58ff-103">Bir iş akışının yürütülmesini izlerken, genellikle veri ayıklamak kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="b58ff-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="b58ff-104">Bu, bir izleme kayıt post yürütme erişirken ek bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="b58ff-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="b58ff-105">İçinde [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], herhangi bir görünür değişkeni veya herhangi bir etkinlik izleme kullanarak bir iş akışı kapsamında bağımsız değişkeni ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b58ff-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="b58ff-106">İzleme profilleri veri ayıklamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b58ff-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="b58ff-107">Değişkenleri ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="b58ff-107">Variables and Arguments</span></span>  
 <span data-ttu-id="b58ff-108">Bir etkinlik bir ActivityStateRecord yayar, değişkenler ve bağımsız değişkenler ayıklanır.</span><span class="sxs-lookup"><span data-stu-id="b58ff-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="b58ff-109">Yalnızca etkinliğin kapsamında ise bir ayıklama için kullanılabilir bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="b58ff-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="b58ff-110">İçinde bir etkinlik ayıklanacak bir değişken, aşağıdaki şekilde belirlenir:</span><span class="sxs-lookup"><span data-stu-id="b58ff-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="b58ff-111">Bir değişken değişken adıyla belirtilirse, izlenmekte olan geçerli etkinlik ve üst etkinliklerde değişkeni İzleme arar.</span><span class="sxs-lookup"><span data-stu-id="b58ff-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="b58ff-112">Değişken geçerli etkinlik kapsamını ve üst kapsam aranır.</span><span class="sxs-lookup"><span data-stu-id="b58ff-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="b58ff-113">Ayıklanacak değişkenleri adını kullanarak belirtilirse = "\*", izlenmekte olan geçerli etkinliği tüm değişkenler ayıklandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="b58ff-113">If variables to be extracted are specified by using name="\*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="b58ff-114">Bu durumda değişkenleri, kapsamındaki ancak etkinlikler değil ayıklanır üst tanımlı.</span><span class="sxs-lookup"><span data-stu-id="b58ff-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="b58ff-115">Bağımsız değişkenler çıkarılırken, ayıklanan bağımsız değişkenleri etkinliğin durumuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b58ff-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="b58ff-116">Bir etkinlik durumunu olduğunda Executing, ardından yalnızca `InArguments` ayıklama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b58ff-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="b58ff-117">Tüm diğer etkinlik için durumu (kapalı, Faulted, iptal edildi), tüm bağımsız değişkenler, InArguments ve OutArguments, ayıklama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b58ff-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="b58ff-118">Aşağıdaki örnek, değişkenler ve bağımsız değişkenler ayıklar bir etkinlik durumu sorgu gösterir, etkinliğin `Closed` izleme kaydı yayılan.</span><span class="sxs-lookup"><span data-stu-id="b58ff-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="b58ff-119">Değişkenleri ve bağımsız değişkenler ayıklanan yalnızca bir <xref:System.Activities.Tracking.ActivityStateRecord> ve bu nedenle bir izleme içinde abone olduğunuz kullanarak profil <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="b58ff-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
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
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="b58ff-120">Değişkenleri ve bağımsız değişkenler depolanan bilgileri koruma</span><span class="sxs-lookup"><span data-stu-id="b58ff-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="b58ff-121">İzlenen değişken veya değişken WF çalışma zamanı tarafından görünür hale varsayılan olarak açıktır.</span><span class="sxs-lookup"><span data-stu-id="b58ff-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="b58ff-122">Bir iş akışı Geliştirici aşağıdaki adımları uygulayarak erişilmesini koruyabilir:</span><span class="sxs-lookup"><span data-stu-id="b58ff-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="b58ff-123">Bir değişkenin değeri olarak şifreleyin.</span><span class="sxs-lookup"><span data-stu-id="b58ff-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="b58ff-124">Bir değişken veya değişken ayıklama önlemek için bir izleme profili yazma denetler.</span><span class="sxs-lookup"><span data-stu-id="b58ff-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="b58ff-125">Özel İzleme katılımcıları WF kod emin olmak için değişkenleri veya bağımsız değişkenler depolanan hassas bilgilerin açığa çıkarmıyor.</span><span class="sxs-lookup"><span data-stu-id="b58ff-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58ff-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b58ff-126">See Also</span></span>  
 [<span data-ttu-id="b58ff-127">Windows Server App Fabric izleme</span><span class="sxs-lookup"><span data-stu-id="b58ff-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="b58ff-128">App Fabric ile uygulamaları izleme</span><span class="sxs-lookup"><span data-stu-id="b58ff-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
