---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: bfac07d64cd5e30c3475d4e269c16597905ea829
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045348"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="a56a0-102">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="a56a0-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="a56a0-103">Bu örnek, <xref:System.Activities.Presentation.View.ExpressionTextBox> bir özel etkinlik tasarımcısında ' nin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a56a0-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="a56a0-104">Özel etkinlik `MultiAssign`, iki dize değişkenine iki dize değeri atar.</span><span class="sxs-lookup"><span data-stu-id="a56a0-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="a56a0-105">Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> <xref:System.Activities.InArgument> denetimler<xref:System.Activities.OutArgument>s öğesine bağlanır ve bazıları bazı öğeleri bağlar.</span><span class="sxs-lookup"><span data-stu-id="a56a0-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="a56a0-106">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a56a0-106">Sample details</span></span>
 <span data-ttu-id="a56a0-107">`ArgumentToExpressionConverter` İfadeleri bağımsız değişkenlere bağlarken kullanılan tür dönüştürücüsü.</span><span class="sxs-lookup"><span data-stu-id="a56a0-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="a56a0-108">`ConverterParameter` Ya`Out`da uygun şekilde ayarlanmalıdır. `In`</span><span class="sxs-lookup"><span data-stu-id="a56a0-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="a56a0-109">`InOut`desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a56a0-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="a56a0-110">Özniteliği, ifadesinin bir L `OutArgument`-değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için kullanılır. `UseLocationExpression`</span><span class="sxs-lookup"><span data-stu-id="a56a0-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="a56a0-111">Çoğu durumda, bir L-değer ifadesi, `OutArgument` döndürülmekte olan değişkenin bir değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a56a0-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="a56a0-112">Özniteliği bu örnekteki bir öğesine ayarlanır ve `MinLines` ayarlanmamış. `MaxLines`</span><span class="sxs-lookup"><span data-stu-id="a56a0-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="a56a0-113">Bu, <xref:System.Activities.Presentation.View.ExpressionTextBox> Kullanıcı tarafından yazılan metin miktarına bakılmaksızın bir satırın sabit bir boyutu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a56a0-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="a56a0-114">Kullanıcı girişine sığacak <xref:System.Activities.Presentation.View.ExpressionTextBox> şekilde büyümeye izin vermek için, büyüktür `MaxLines` `MinLines`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a56a0-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="a56a0-115">ExpressionTextBox yalnızca bağımsız değişkenlere bağlanabilir ve CLR özelliklerine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="a56a0-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="a56a0-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="a56a0-116">To use this sample</span></span>

1. <span data-ttu-id="a56a0-117">Visual Studio 2010 kullanarak, ExpressionTextBoxSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="a56a0-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="a56a0-118">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="a56a0-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="a56a0-119">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a56a0-119">To run this sample</span></span>

1. <span data-ttu-id="a56a0-120">Çözüme yeni bir Iş akışı konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a56a0-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="a56a0-121">Yeni Iş akışı konsol uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a56a0-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="a56a0-122">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a56a0-122">Build the solution.</span></span>

4. <span data-ttu-id="a56a0-123">Araç kutusundan **MultiAssign** etkinliğini sürükleyin ve iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="a56a0-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a56a0-124">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a56a0-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a56a0-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a56a0-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="a56a0-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="a56a0-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a56a0-127">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a56a0-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="a56a0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a56a0-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="a56a0-129">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="a56a0-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
