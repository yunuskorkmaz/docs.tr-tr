---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6b581b42c882c12425a17b9a518f8957ca10898a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715544"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="b0836-102">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="b0836-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="b0836-103">Bu örnek, <xref:System.Activities.Presentation.View.ExpressionTextBox> özel bir etkinlik tasarımcısında nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0836-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="b0836-104">`MultiAssign`özel etkinlik iki dize değişkenine iki dize değeri atar.</span><span class="sxs-lookup"><span data-stu-id="b0836-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="b0836-105">Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimleri <xref:System.Activities.InArgument>s 'ye bağlanır ve bazı <xref:System.Activities.OutArgument>s öğesine bağlanır.</span><span class="sxs-lookup"><span data-stu-id="b0836-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="b0836-106">Örnek Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b0836-106">Sample details</span></span>
 <span data-ttu-id="b0836-107">`ArgumentToExpressionConverter`, ifadeleri bağımsız değişkenlere bağlarken kullanılan tür dönüştürücütür.</span><span class="sxs-lookup"><span data-stu-id="b0836-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="b0836-108">`ConverterParameter` `In` veya `Out` uygun şekilde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0836-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="b0836-109">`InOut` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b0836-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="b0836-110">`UseLocationExpression` özniteliği, ifadenin bir L-değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için `OutArgument`s üzerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b0836-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="b0836-111">Çoğu durumda, bir L-değer ifadesi, döndürülmekte olan `OutArgument` bir değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcıdır.</span><span class="sxs-lookup"><span data-stu-id="b0836-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="b0836-112">`MaxLines` özniteliği bu örnekte bir olarak ayarlanır ve `MinLines` ayarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="b0836-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="b0836-113">Bu, <xref:System.Activities.Presentation.View.ExpressionTextBox>, Kullanıcı tarafından yazılan metin miktarına bakılmaksızın, bir satırın sabit bir boyutu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0836-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="b0836-114"><xref:System.Activities.Presentation.View.ExpressionTextBox>, kullanıcı girişine sığacak şekilde büyümeye izin vermek için, `MinLines`daha büyük `MaxLines` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b0836-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="b0836-115">ExpressionTextBox yalnızca bağımsız değişkenlere bağlanabilir ve CLR özelliklerine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="b0836-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="b0836-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="b0836-116">To use this sample</span></span>

1. <span data-ttu-id="b0836-117">Visual Studio 2010 kullanarak, ExpressionTextBoxSample. sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="b0836-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="b0836-118">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="b0836-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="b0836-119">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="b0836-119">To run this sample</span></span>

1. <span data-ttu-id="b0836-120">Çözüme yeni bir Iş akışı konsol uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b0836-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="b0836-121">Yeni Iş akışı konsol uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b0836-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="b0836-122">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b0836-122">Build the solution.</span></span>

4. <span data-ttu-id="b0836-123">Araç kutusundan **MultiAssign** etkinliğini sürükleyin ve iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="b0836-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0836-124">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b0836-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b0836-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="b0836-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b0836-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="b0836-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b0836-127">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="b0836-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="b0836-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0836-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="b0836-129">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="b0836-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
