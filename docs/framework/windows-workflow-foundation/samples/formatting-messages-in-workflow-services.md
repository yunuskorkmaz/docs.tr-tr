---
title: "İş akışı hizmetleri iletilerinde biçimlendirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 726ce98f3fe11bbc3cd13d90cdae335c0741efe6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="16d70-102">İş akışı hizmetleri iletilerinde biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="16d70-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="16d70-103">Bu örnek nasıl farklı kullanıcı türleri kullanılabilir Mesajlaşma etkinlikleri (WF Hizmetleri) gösterir.</span><span class="sxs-lookup"><span data-stu-id="16d70-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="16d70-104">Örnek hizmeti bir basit gider onay hizmetidir ve üç işlemini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="16d70-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="16d70-105">`ApproveExpense`bir veri sözleşmesi türü alır ve bilinen türleri kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="16d70-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="16d70-106">İşlemi döndürür `true` veya `false` gider miktarına bağlı.</span><span class="sxs-lookup"><span data-stu-id="16d70-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="16d70-107">`ApprovePO`XmlSerializer türü alıp döndüren `true` veya `false` gider miktarına bağlı.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="16d70-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="16d70-108">Sözleşme türden bir ileti alıp döndüren `true` veya `false` satıcı onaylanan satıcılar listesinde ise veya istek (Finans departmanı herhangi bir satıcı kullanabilir) Finans departmanından geldiyse.</span><span class="sxs-lookup"><span data-stu-id="16d70-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="16d70-109">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="16d70-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="16d70-110">Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="16d70-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="16d70-111">[Çözüm temel dizin] \FormatterService\bin\debug\ oluşturulan hizmeti, ilk çalıştırma</span><span class="sxs-lookup"><span data-stu-id="16d70-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="16d70-112">İkinci olarak, [çözüm temel dizin] \FormatterClient\bin\debug oluşturulan istemci uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="16d70-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="16d70-113">İstemci, üç işlemi hizmet üzerinde çağırır ve sonuçlarını yazdırır.</span><span class="sxs-lookup"><span data-stu-id="16d70-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="16d70-114">Tamamlandığında, istemci ve hizmet çıkmak için ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="16d70-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16d70-115">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="16d70-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="16d70-116">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="16d70-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="16d70-117">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="16d70-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="16d70-118">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="16d70-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`