---
title: "Temel etkinlik oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 047948552471b33af8690b526db7c416e87f897a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-activity-composition"></a><span data-ttu-id="d447f-102">Temel etkinlik oluşturma</span><span class="sxs-lookup"><span data-stu-id="d447f-102">Basic Activity Composition</span></span>
<span data-ttu-id="d447f-103">Bu örnek özel etkinlikler ve daha fazla özel etkinlikler oluşturmak için sistem tarafından sağlanan etkinlikleri oluşturmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d447f-103">This sample demonstrates how to compose custom activities and system-provided activities to build more custom activities.</span></span>  
  
 <span data-ttu-id="d447f-104">Anket etkinliğini kullanarak iş akışı bir soru listesi ile anket zamanlar ve alınan yanıtların çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d447f-104">The workflow using the Survey activity schedules the Survey with a list of questions, and then outputs the responses received.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="d447f-105">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="d447f-105">Sample Details</span></span>  
 <span data-ttu-id="d447f-106">Bu örnek, üç özel etkinlikler kullanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d447f-106">This sample uses three custom activities.</span></span> <span data-ttu-id="d447f-107">`ReadLine`Basit bir olan <xref:System.Activities.NativeActivity> \<dize > oluşturan bir <xref:System.Activities.Bookmark> zamanlanmış ve ardından ayarlar `Return` <xref:System.Activities.OutArgument%601> hangi değerine <xref:System.Activities.Bookmark> sürdürülür.</span><span class="sxs-lookup"><span data-stu-id="d447f-107">`ReadLine` is a simple <xref:System.Activities.NativeActivity>\<string> that creates a <xref:System.Activities.Bookmark> when scheduled, and then sets the `Return`<xref:System.Activities.OutArgument%601> to the value with which the <xref:System.Activities.Bookmark> is resumed.</span></span> <span data-ttu-id="d447f-108">`Prompt`olan bir <xref:System.Activities.Activity%601> \<dize > alan bir <xref:System.Activities.InArgument%601>< dize\> adlı `Text` ve kullanıcıların yanıt olarak döndürür `Result` <xref:System.Activities.OutArgument%601> \<dize >.</span><span class="sxs-lookup"><span data-stu-id="d447f-108">`Prompt` is an <xref:System.Activities.Activity%601>\<string> that takes an <xref:System.Activities.InArgument%601><string\> named `Text` and returns the users response in the `Result`<xref:System.Activities.OutArgument%601>\<string>.</span></span> <span data-ttu-id="d447f-109">`Prompt` Aktivitesi kullanır <xref:System.Activities.Statements.Sequence> ve <xref:System.Activities.Statements.WriteLine> sevk .NET Framework'ün bir parçası olarak ve ayrıca özel bir araya getirir etkinlikleri `ReadLine` kullanıcı girişi alma etkinliği.</span><span class="sxs-lookup"><span data-stu-id="d447f-109">The `Prompt` activity uses the <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.WriteLine> activities that ship as part of the .NET Framework, and also incorporates the custom `ReadLine` activity for getting user input.</span></span> <span data-ttu-id="d447f-110">Son özel etkinliği `Survey` etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d447f-110">The last custom activity is the `Survey` activity.</span></span> <span data-ttu-id="d447f-111">Bu bir <xref:System.Activities.Activity>< ICollection\<dize >>.</span><span class="sxs-lookup"><span data-stu-id="d447f-111">It is an <xref:System.Activities.Activity><ICollection\<string>>.</span></span>  <span data-ttu-id="d447f-112">Bu etkinliği alır bir <xref:System.Activities.InArgument%601>< IEnumerable < dize\>> adlı `Questions` ve doldurur `Result` out yanıtlarla bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="d447f-112">This activity takes an <xref:System.Activities.InArgument%601><IEnumerable<string\>> named `Questions` and populates the `Result` out argument with the responses.</span></span> <span data-ttu-id="d447f-113">`Survey` Aktivitesi kullanır <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> ve <xref:System.Activities.Statements.AddToCollection%601> .NET Framework ve uygular `Prompt` anket sorular sormak ve yanıtları almak için etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d447f-113">The `Survey` activity uses <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.AddToCollection%601> from the .NET Framework and employs the `Prompt` activity for asking the survey questions and getting responses.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d447f-114">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="d447f-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d447f-115">Açık **BasicActivityComposition.sln** örnek çözümde [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d447f-115">Open the **BasicActivityComposition.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="d447f-116">Derleme ve çözümü çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d447f-116">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d447f-117">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d447f-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d447f-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d447f-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d447f-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d447f-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d447f-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d447f-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`