---
description: "Daha fazla bilgi edinin: XAML 'Den yükleme"
title: XAML’den Yükleme
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: fd0eca487c0245c7bfa46ca80c06f2adfa577353
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99742036"
---
# <a name="load-from-xaml"></a><span data-ttu-id="25bcc-103">XAML’den Yükleme</span><span class="sxs-lookup"><span data-stu-id="25bcc-103">Load From XAML</span></span>

<span data-ttu-id="25bcc-104">Bu örnek, XamlBuildTask aracını çalıştırmak zorunda kalmadan bir XAML iş akışını dinamik olarak yüklemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="25bcc-104">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="25bcc-105">Bunun yerine, örnek yöntemini çağırır <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> .</span><span class="sxs-lookup"><span data-stu-id="25bcc-105">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="25bcc-106">Örnek, sınıfını kullanarak XAML iş akışlarını yükleyen ve bunları yürüten bir Windows Presentation Foundation (WPF) istemci uygulamasıdır <xref:System.Activities.XamlIntegration.ActivityXamlServices> .</span><span class="sxs-lookup"><span data-stu-id="25bcc-106">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="25bcc-107">Sınıfı kullanılarak yüklendikten sonra <xref:System.Activities.XamlIntegration.ActivityXamlServices> <xref:System.Activities.DynamicActivity%601> yürütülebilecek bir döndürülür.</span><span class="sxs-lookup"><span data-stu-id="25bcc-107">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="25bcc-108">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="25bcc-108">To use this sample</span></span>

1. <span data-ttu-id="25bcc-109">Visual Studio 2010 kullanarak LoadFromXAML. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="25bcc-109">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="25bcc-110">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="25bcc-110">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="25bcc-111">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="25bcc-111">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25bcc-112">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="25bcc-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="25bcc-113">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="25bcc-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="25bcc-114">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="25bcc-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25bcc-115">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="25bcc-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
