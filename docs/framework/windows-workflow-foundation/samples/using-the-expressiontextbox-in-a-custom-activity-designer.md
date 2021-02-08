---
description: 'Hakkında daha fazla bilgi edinin: özel bir etkinlik tasarımcısında ExpressionTextBox kullanma'
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: c333832c2f955354233371c6572f8ae27e5d8643
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787766"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="abc65-103">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="abc65-103">Using the ExpressionTextBox in a Custom Activity Designer</span></span>

<span data-ttu-id="abc65-104">Bu örnek, <xref:System.Activities.Presentation.View.ExpressionTextBox> bir özel etkinlik tasarımcısında ' nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="abc65-104">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="abc65-105">Özel etkinlik, `MultiAssign` iki dize değişkenine iki dize değeri atar.</span><span class="sxs-lookup"><span data-stu-id="abc65-105">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="abc65-106">Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> Denetimler s öğesine bağlanır <xref:System.Activities.InArgument> ve bazıları bazı <xref:System.Activities.OutArgument> öğeleri bağlar.</span><span class="sxs-lookup"><span data-stu-id="abc65-106">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="abc65-107">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="abc65-107">Sample details</span></span>

 <span data-ttu-id="abc65-108">`ArgumentToExpressionConverter`İfadeleri bağımsız değişkenlere bağlarken kullanılan tür dönüştürücüsü.</span><span class="sxs-lookup"><span data-stu-id="abc65-108">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="abc65-109">`ConverterParameter`Ya da uygun şekilde ayarlanmalıdır `In` `Out` .</span><span class="sxs-lookup"><span data-stu-id="abc65-109">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="abc65-110">`InOut` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="abc65-110">`InOut` is not supported.</span></span>

 <span data-ttu-id="abc65-111">`UseLocationExpression`Özniteliği, `OutArgument` Ifadesinin bir L-değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="abc65-111">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="abc65-112">Çoğu durumda, bir L-değer ifadesi, `OutArgument` döndürülmekte olan değişkenin bir değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="abc65-112">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="abc65-113">`MaxLines`Özniteliği bu örnekteki bir öğesine ayarlanır ve `MinLines` ayarlanmamış.</span><span class="sxs-lookup"><span data-stu-id="abc65-113">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="abc65-114">Bu, <xref:System.Activities.Presentation.View.ExpressionTextBox> Kullanıcı tarafından yazılan metin miktarına bakılmaksızın bir satırın sabit bir boyutu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abc65-114">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="abc65-115"><xref:System.Activities.Presentation.View.ExpressionTextBox>Kullanıcı girişine sığacak şekilde büyümeye izin vermek için, `MaxLines` büyüktür olarak ayarlayın `MinLines` .</span><span class="sxs-lookup"><span data-stu-id="abc65-115">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="abc65-116">ExpressionTextBox yalnızca bağımsız değişkenlere bağlanabilir ve CLR özelliklerine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="abc65-116">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="abc65-117">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="abc65-117">To use this sample</span></span>

1. <span data-ttu-id="abc65-118">Visual Studio 2010 kullanarak, ExpressionTextBoxSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="abc65-118">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="abc65-119">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="abc65-119">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="abc65-120">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="abc65-120">To run this sample</span></span>

1. <span data-ttu-id="abc65-121">Çözüme yeni bir Iş akışı konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abc65-121">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="abc65-122">Yeni Iş akışı konsol uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abc65-122">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="abc65-123">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="abc65-123">Build the solution.</span></span>

4. <span data-ttu-id="abc65-124">Araç kutusundan **MultiAssign** etkinliğini sürükleyin ve iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="abc65-124">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="abc65-125">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="abc65-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="abc65-126">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="abc65-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="abc65-127">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="abc65-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="abc65-128">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="abc65-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="abc65-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abc65-129">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="abc65-130">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="abc65-130">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
