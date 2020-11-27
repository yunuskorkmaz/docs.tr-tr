---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: dfb53096be59abd9924a024880d4125ca774d4b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267507"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="a9e3f-102">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="a9e3f-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>

<span data-ttu-id="a9e3f-103">Bu örnek, <xref:System.Activities.Presentation.View.ExpressionTextBox> bir özel etkinlik tasarımcısında ' nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="a9e3f-104">Özel etkinlik, `MultiAssign` iki dize değişkenine iki dize değeri atar.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="a9e3f-105">Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> Denetimler s öğesine bağlanır <xref:System.Activities.InArgument> ve bazıları bazı <xref:System.Activities.OutArgument> öğeleri bağlar.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="a9e3f-106">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a9e3f-106">Sample details</span></span>

 <span data-ttu-id="a9e3f-107">`ArgumentToExpressionConverter`İfadeleri bağımsız değişkenlere bağlarken kullanılan tür dönüştürücüsü.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="a9e3f-108">`ConverterParameter`Ya da uygun şekilde ayarlanmalıdır `In` `Out` .</span><span class="sxs-lookup"><span data-stu-id="a9e3f-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="a9e3f-109">`InOut` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="a9e3f-110">`UseLocationExpression`Özniteliği, `OutArgument` Ifadesinin bir L-değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="a9e3f-111">Çoğu durumda, bir L-değer ifadesi, `OutArgument` döndürülmekte olan değişkenin bir değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="a9e3f-112">`MaxLines`Özniteliği bu örnekteki bir öğesine ayarlanır ve `MinLines` ayarlanmamış.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="a9e3f-113">Bu, <xref:System.Activities.Presentation.View.ExpressionTextBox> Kullanıcı tarafından yazılan metin miktarına bakılmaksızın bir satırın sabit bir boyutu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="a9e3f-114"><xref:System.Activities.Presentation.View.ExpressionTextBox>Kullanıcı girişine sığacak şekilde büyümeye izin vermek için, `MaxLines` büyüktür olarak ayarlayın `MinLines` .</span><span class="sxs-lookup"><span data-stu-id="a9e3f-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="a9e3f-115">ExpressionTextBox yalnızca bağımsız değişkenlere bağlanabilir ve CLR özelliklerine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="a9e3f-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a9e3f-116">To use this sample</span></span>

1. <span data-ttu-id="a9e3f-117">Visual Studio 2010 kullanarak, ExpressionTextBoxSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="a9e3f-118">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="a9e3f-119">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a9e3f-119">To run this sample</span></span>

1. <span data-ttu-id="a9e3f-120">Çözüme yeni bir Iş akışı konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="a9e3f-121">Yeni Iş akışı konsol uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="a9e3f-122">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-122">Build the solution.</span></span>

4. <span data-ttu-id="a9e3f-123">Araç kutusundan **MultiAssign** etkinliğini sürükleyin ve iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9e3f-124">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9e3f-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a9e3f-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a9e3f-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9e3f-127">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="a9e3f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9e3f-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="a9e3f-129">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="a9e3f-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
