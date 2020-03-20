---
title: Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182761"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a><span data-ttu-id="219fb-102">Özel Etkinlik Tasarımcısında ExpressionTextBox Kullanma</span><span class="sxs-lookup"><span data-stu-id="219fb-102">Using the ExpressionTextBox in a Custom Activity Designer</span></span>
<span data-ttu-id="219fb-103">Bu örnek, özel <xref:System.Activities.Presentation.View.ExpressionTextBox> bir etkinlik tasarımcısında nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="219fb-103">This sample shows how to use the <xref:System.Activities.Presentation.View.ExpressionTextBox> in a custom activity designer.</span></span> <span data-ttu-id="219fb-104">Özel etkinlik, `MultiAssign`iki dize değişkenine iki dize değeri atar.</span><span class="sxs-lookup"><span data-stu-id="219fb-104">The custom activity, `MultiAssign`, assigns two string values to two string variables.</span></span> <span data-ttu-id="219fb-105">Bazı <xref:System.Activities.Presentation.View.ExpressionTextBox> denetimler <xref:System.Activities.InArgument>s'ye, bazıları <xref:System.Activities.OutArgument>da s'ye bağlanır.</span><span class="sxs-lookup"><span data-stu-id="219fb-105">Some <xref:System.Activities.Presentation.View.ExpressionTextBox> controls bind to <xref:System.Activities.InArgument>s and some bind to <xref:System.Activities.OutArgument>s.</span></span>

## <a name="sample-details"></a><span data-ttu-id="219fb-106">Örnek ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="219fb-106">Sample details</span></span>
 <span data-ttu-id="219fb-107">İfadeleri `ArgumentToExpressionConverter` bağımsız değişkenlere bağlarken kullanılan tür dönüştürücüdür.</span><span class="sxs-lookup"><span data-stu-id="219fb-107">The `ArgumentToExpressionConverter` is the type converter used when binding expressions to arguments.</span></span> <span data-ttu-id="219fb-108">Ayarlanmalıdır `ConverterParameter` `In` veya `Out` uygun olarak.</span><span class="sxs-lookup"><span data-stu-id="219fb-108">The `ConverterParameter` must be set to `In` or `Out` as appropriate.</span></span> <span data-ttu-id="219fb-109">`InOut`Desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="219fb-109">`InOut` is not supported.</span></span>

 <span data-ttu-id="219fb-110">`OutArgument`Öznitelik, `UseLocationExpression` ifadenin Bir L değeri ("sol değer" veya "konum değeri") ifadesi olması gerektiğini belirtmek için s üzerinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="219fb-110">The `UseLocationExpression` attribute is used on `OutArgument`s to specify that the expression should be an L-value ("left value" or "location value") expression.</span></span> <span data-ttu-id="219fb-111">Çoğu durumda, L değeri ifadesi, `OutArgument` döndürülen değişken veya bağımsız değişken adı olduğunu belirtmek için kullanılan geçerli bir Visual Basic tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="219fb-111">In most cases, an L-value expression is a valid Visual Basic identifier used to indicate that the `OutArgument` being returned is a variable or argument name.</span></span>

 <span data-ttu-id="219fb-112">Öznitelik `MaxLines` bu örnekte bir olarak `MinLines` ayarlanır ve ayarlanmaz.</span><span class="sxs-lookup"><span data-stu-id="219fb-112">The `MaxLines` attribute is set to one in this example and `MinLines` is not set.</span></span> <span data-ttu-id="219fb-113">Bu, kullanıcı <xref:System.Activities.Presentation.View.ExpressionTextBox> tarafından yazılan metin miktarına bakılmaksızın bir satırın sabit boyutu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="219fb-113">This indicates that the <xref:System.Activities.Presentation.View.ExpressionTextBox> is a fixed size of one line regardless of the amount of text typed by the user.</span></span> <span data-ttu-id="219fb-114">Kullanıcı <xref:System.Activities.Presentation.View.ExpressionTextBox> girişine uyacak şekilde büyümesine `MaxLines` izin `MinLines`vermek için, 'den büyük.</span><span class="sxs-lookup"><span data-stu-id="219fb-114">To allow the <xref:System.Activities.Presentation.View.ExpressionTextBox> to grow to fit user input, set `MaxLines` greater than `MinLines`.</span></span>

 <span data-ttu-id="219fb-115">ExpressionTextBox yalnızca bağımsız değişkenlere bağlı olabilir ve CLR özelliklerine bağlanamaz.</span><span class="sxs-lookup"><span data-stu-id="219fb-115">An ExpressionTextBox can only be bound to arguments, and cannot be bound to CLR properties.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="219fb-116">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="219fb-116">To use this sample</span></span>

1. <span data-ttu-id="219fb-117">Visual Studio 2010'u kullanarak ExpressionTextBoxSample.sln dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="219fb-117">Using Visual Studio 2010, open the ExpressionTextBoxSample.sln file.</span></span>

2. <span data-ttu-id="219fb-118">Çözümü oluşturmak için CTRL+SHIFT+B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="219fb-118">To build the solution, press CTRL+SHIFT+B.</span></span>

#### <a name="to-run-this-sample"></a><span data-ttu-id="219fb-119">Bu örneği çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="219fb-119">To run this sample</span></span>

1. <span data-ttu-id="219fb-120">Çözüme yeni bir İş Akışı Konsolu Uygulaması ekleyin.</span><span class="sxs-lookup"><span data-stu-id="219fb-120">Add a new Workflow Console Application to the solution.</span></span>

2. <span data-ttu-id="219fb-121">Yeni İş Akışı Konsolu Uygulaması projesinden **ExpressionTextBoxSample** projesine bir başvuru ekleyin.</span><span class="sxs-lookup"><span data-stu-id="219fb-121">Add a reference to the **ExpressionTextBoxSample** project from the new Workflow Console Application project.</span></span>

3. <span data-ttu-id="219fb-122">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="219fb-122">Build the solution.</span></span>

4. <span data-ttu-id="219fb-123">**MultiAssign** etkinliğini araç kutusundan sürükleyin ve iş akışına bırakın.</span><span class="sxs-lookup"><span data-stu-id="219fb-123">Drag the **MultiAssign** activity from the toolbox and drop it into the workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="219fb-124">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="219fb-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="219fb-125">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="219fb-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="219fb-126">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="219fb-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="219fb-127">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="219fb-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a><span data-ttu-id="219fb-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="219fb-128">See also</span></span>

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [<span data-ttu-id="219fb-129">İş Akışı Tasarımcısı ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="219fb-129">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
