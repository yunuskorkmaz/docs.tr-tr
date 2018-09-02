---
title: Bookmarks2
ms.date: 03/30/2017
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
ms.openlocfilehash: 6bcc4e27566b9c8553e0792558c281a6b1f1caf4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387395"
---
# <a name="bookmarks"></a><span data-ttu-id="4407e-102">Yer işaretleri</span><span class="sxs-lookup"><span data-stu-id="4407e-102">Bookmarks</span></span>
<span data-ttu-id="4407e-103">Bu örnek, dış girdi almak için bir yer işareti oluşturur ve özel bir etkinlik yazma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4407e-103">This sample demonstrates how to write a custom activity that creates a bookmark to receive external input.</span></span> <span data-ttu-id="4407e-104">Örnek ayrıca özel etkinlik bir iş akışında kullanır ve bulma ve çalışan bir iş akışı örneğiyle ilişkili yer işaretleri sürdürme gösterir bir temel bir konsol uygulaması içerir.</span><span class="sxs-lookup"><span data-stu-id="4407e-104">The sample also includes a basic console application that uses the custom activity in a workflow and shows how to discover and resume bookmarks associated with a running workflow instance.</span></span> <span data-ttu-id="4407e-105">Yer işaretleri hakkında daha fazla bilgi için bkz. [yer işaretleri](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="4407e-105">For more information about bookmarks, see [Bookmarks](../../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4407e-106">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4407e-106">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4407e-107">Bookmarks.sln örnek çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4407e-107">Open the Bookmarks.sln sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="4407e-108">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="4407e-108">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4407e-109">Örneği çalıştırmak için CTRLl + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="4407e-109">To run the sample, press CTRLl + F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4407e-110">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="4407e-110">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4407e-111">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="4407e-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4407e-112">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4407e-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4407e-113">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="4407e-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`