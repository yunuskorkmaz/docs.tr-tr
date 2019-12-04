---
title: XAML’den Yükleme
ms.date: 03/30/2017
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
ms.openlocfilehash: c46c9020f07731d3d833332d77fd46a162ccb6dc
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715959"
---
# <a name="load-from-xaml"></a><span data-ttu-id="f31a0-102">XAML’den Yükleme</span><span class="sxs-lookup"><span data-stu-id="f31a0-102">Load From XAML</span></span>
<span data-ttu-id="f31a0-103">Bu örnek, XamlBuildTask aracını çalıştırmak zorunda kalmadan bir XAML iş akışını dinamik olarak yüklemeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f31a0-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="f31a0-104">Bunun yerine, örnek <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f31a0-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="f31a0-105">Örnek, <xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfını kullanarak XAML iş akışlarını yükleyen ve bunları yürüten bir Windows Presentation Foundation (WPF) istemci uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f31a0-105">The sample is a Windows Presentation Foundation (WPF) client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="f31a0-106"><xref:System.Activities.XamlIntegration.ActivityXamlServices> sınıfı kullanılarak yüklendikten sonra yürütülebilecek bir <xref:System.Activities.DynamicActivity%601> döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f31a0-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="f31a0-107">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="f31a0-107">To use this sample</span></span>

1. <span data-ttu-id="f31a0-108">Visual Studio 2010 kullanarak LoadFromXAML. sln çözüm dosyasını açın.</span><span class="sxs-lookup"><span data-stu-id="f31a0-108">Using Visual Studio 2010, open the LoadFromXAML.sln solution file.</span></span>

2. <span data-ttu-id="f31a0-109">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f31a0-109">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="f31a0-110">Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="f31a0-110">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f31a0-111">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="f31a0-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f31a0-112">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="f31a0-112">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f31a0-113">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="f31a0-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f31a0-114">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="f31a0-114">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`
