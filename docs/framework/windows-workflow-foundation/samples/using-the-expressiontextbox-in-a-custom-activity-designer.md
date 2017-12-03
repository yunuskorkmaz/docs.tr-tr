---
title: "Özel Etkinlik Tasarımcısı'nda ExpressionTextBox kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 85fe8dcbd0ef5e774ab81ed167ff937ec2e09d83
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="de057-102">Özel Etkinlik Tasarımcısı'nda ExpressionTextBox kullanma</span><span class="sxs-lookup"><span data-stu-id="de057-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="de057-103">Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Activities.Presentation.View.ExpressionTextBox> özel etkinlik Tasarımcısı'nda.</span><span class="sxs-lookup"><span data-stu-id="de057-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="de057-104">Özel Etkinlik `MultiAssign`, iki dize değişkenleri iki dize değeri atar.</span><span class="sxs-lookup"><span data-stu-id="de057-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="de057-105">Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimleri bağlamak için <xref:System.Activities.InArgument>s ve bazı bağlamak için <xref:System.Activities.OutArgument>s.</span><span class="sxs-lookup"><span data-stu-id="de057-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="de057-106">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="de057-106">Sample details</span></span>  
 <span data-ttu-id="de057-107">`ArgumentToExpressionConverter` İfadeleri bağımsız değişkenleri bağlanırken kullanılan türü dönüştürücü.</span><span class="sxs-lookup"><span data-stu-id="de057-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="de057-108">`ConverterParameter` Ayarlanmalıdır `In` veya `Out` uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="de057-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="de057-109">`InOut`desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="de057-109">`InOut` is not supported.</span></span>  
  
 <span data-ttu-id="de057-110">`UseLocationExpression` Özniteliği kullanılır `OutArgument`s ifade L-değeri ("sol value" veya "konum değeri") ifade gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="de057-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="de057-111">Çoğu durumda, L-değeri ifade belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcı olan `OutArgument` döndürülen bir değişken veya değişken adı değil.</span><span class="sxs-lookup"><span data-stu-id="de057-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>  
  
 <span data-ttu-id="de057-112">`MaxLines` Özniteliği olarak ayarlanmış bir Bu örnekte ve `MinLines` ayarlı değil.</span><span class="sxs-lookup"><span data-stu-id="de057-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="de057-113">Bu belirten <xref:System.Activities.Presentation.View.ExpressionTextBox> kullanıcı tarafından yazılan metin bakılmaksızın tek bir çizgi sabit bir boyuta sahiptir.</span><span class="sxs-lookup"><span data-stu-id="de057-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="de057-114">İzin vermek için <xref:System.Activities.Presentation.View.ExpressionTextBox> kullanıcı girişi uyacak şekilde büyümesine olanak ayarlamak `MaxLines` büyük `MinLines`.</span><span class="sxs-lookup"><span data-stu-id="de057-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>  
  
 <span data-ttu-id="de057-115">Bir ExpressionTextBox bağımsız değişken yalnızca bağlanabilir ve CLR özelliklerine bağlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="de057-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="de057-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="de057-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="de057-117">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ExpressionTextBoxSample.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="de057-117">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ExpressionTextBoxSample.sln file.</span></span>  
  
2.  <span data-ttu-id="de057-118">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="de057-118">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="de057-119">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="de057-119">To run this sample</span></span>  
  
1.  <span data-ttu-id="de057-120">Yeni bir iş akışı konsol uygulaması çözüme ekleyin.</span><span class="sxs-lookup"><span data-stu-id="de057-120">Add a new Workflow Console Application to the solution.</span></span>  
  
2.  <span data-ttu-id="de057-121">Bir başvuru ekleyin **ExpressionTextBoxSample** yeni bir iş akışı konsol uygulama projesi projeden.</span><span class="sxs-lookup"><span data-stu-id="de057-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>  
  
3.  <span data-ttu-id="de057-122">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="de057-122">Build the solution.</span></span>  
  
4.  <span data-ttu-id="de057-123">Sürükleme **MultiAssign** araç etkinliğinden ve iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="de057-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="de057-124">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="de057-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="de057-125">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="de057-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="de057-126">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="de057-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="de057-127">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="de057-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="de057-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de057-128">See Also</span></span>  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>  
 [<span data-ttu-id="de057-129">İş Akışı Tasarımcısı ile uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="de057-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
