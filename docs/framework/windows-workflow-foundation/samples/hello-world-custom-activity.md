---
title: Merhaba Dünya özel etkinliği
ms.date: 03/30/2017
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
ms.openlocfilehash: fde745fae7470ec763b6b5030a60436a6525e3c0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856858"
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="6f2d2-102">Merhaba Dünya özel etkinliği</span><span class="sxs-lookup"><span data-stu-id="6f2d2-102">Hello World Custom Activity</span></span>
<span data-ttu-id="6f2d2-103">Bu örnek, Windows Workflow Foundation (basit bir özel etkinlik oluşturma da dahil olmak üzere WF), birkaç temel özellikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-103">This sample demonstrates several key features of Windows Workflow Foundation (WF), including how to create a simple custom activity.</span></span> <span data-ttu-id="6f2d2-104">Bu örnekte gösterilen özelliklerin bazıları C# ve kullanarak özel bir etkinlik oluşturmakta olduğunuz `in` ve `out` bağımsız değişkenleri (<xref:System.Activities.InArgument> ve <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="6f2d2-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f2d2-105">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="6f2d2-106">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6f2d2-107">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6f2d2-108">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="6f2d2-109">Kodda bir iş akışı oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f2d2-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="6f2d2-110">Bu örnekte, iki özel etkinlikler, C# kodunu kullanarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="6f2d2-111">Her iki özel etkinlikler doğrudan veya dolaylı olarak devralınacak <xref:System.Activities.Activity%601> tek bir değer.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="6f2d2-112">Genel olmayan devralan yerine genel dönüş değeri kullanmanın avantajı <xref:System.Activities.Activity> sınıfı, bazı etkinlikler olan (gibi <xref:System.Activities.Statements.Assign>) oluşan bir etkinlik bir parçası olarak kullanıldığında döndürülen değer erişebilir.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="6f2d2-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="6f2d2-113">AppendString</span></span>  
 <span data-ttu-id="6f2d2-114">Bu etkinlik devraldığı <xref:System.Activities.Activity%601>ve kullandığı bir <xref:System.Activities.Statements.Assign> birlikte iki dizeyi art arda ekler etkinlik.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="6f2d2-115">Dize önüne ekleyin</span><span class="sxs-lookup"><span data-stu-id="6f2d2-115">Prepend String</span></span>  
 <span data-ttu-id="6f2d2-116">Bu etkinlik, doğrudan devralan <xref:System.Activities.CodeActivity%601>ve benzer bir işlevsellik oluşturur `AppendString` etkinliği kod yerine önceden varolan bir etkinliğin oluşturuluyor uygulanan mantığı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="6f2d2-117">Aşağıdaki dosyalar bu projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="6f2d2-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="6f2d2-118">AppendString.cs</span></span>  
 <span data-ttu-id="6f2d2-119">Özel Etkinlik dizeleri birlikte ekler.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="6f2d2-120">Bu, bir dize alır ve "Merhaba Dünya forma çıktı olarak tam bir ileti yazan" sabit metin dizesi ile birleştirir.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="6f2d2-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="6f2d2-121">PrependString.cs</span></span>  
 <span data-ttu-id="6f2d2-122">Bu etkinliğin bir Giriş dizesinin için önceden tanımlanmış bir dize ekler.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="6f2d2-123">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="6f2d2-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="6f2d2-124">Kullanan bir iş akışı `AppendString` ve `PrependString` özel etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="6f2d2-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="6f2d2-125">Program.cs</span></span>  
 <span data-ttu-id="6f2d2-126">İş akışının çalıştığı bir programdır.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6f2d2-127">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="6f2d2-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="6f2d2-128">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], HelloWorld.sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6f2d2-129">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6f2d2-130">Çözümü çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="6f2d2-130">To run the solution, press F5.</span></span>