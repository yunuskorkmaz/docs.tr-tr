---
title: "Temel XAML yalnızca hizmeti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c106feb0-0245-43b5-aefe-93ce0e4d38eb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 004a37682b855135998ef4620e673421f769326d
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="basic-xaml-only-service"></a><span data-ttu-id="5996c-102">Temel XAML yalnızca hizmeti</span><span class="sxs-lookup"><span data-stu-id="5996c-102">Basic XAML only Service</span></span>
<span data-ttu-id="5996c-103">Bu örnek bir XAML yalnızca hizmetin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5996c-103">This sample demonstrates how to create a XAML only service.</span></span> <span data-ttu-id="5996c-104">Senaryo bir araba ilgili sorunları tanılama hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="5996c-104">The scenario is a diagnostics service for car-related problems.</span></span> <span data-ttu-id="5996c-105">Hizmet, istemci bir dizi sorunu tanılamak için soru soran bir iş akışı olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5996c-105">The service is implemented as a workflow that asks the client a series of questions to diagnose the problem.</span></span> <span data-ttu-id="5996c-106">İki tür hizmet tanılama sorunları vardır (car başlatamaz veya çalışmıyor koşullandırma hava).</span><span class="sxs-lookup"><span data-stu-id="5996c-106">There are two types of issues the service can diagnose (car does not start or air conditioning not working).</span></span> <span data-ttu-id="5996c-107">İş Akışı Tasarımcısı'ndan istek/yanıt şablon üç Basit Hizmet işlemleri kullanıma sunmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="5996c-107">The workflow uses Request/Reply template from the designer to expose three simple service operations.</span></span> <span data-ttu-id="5996c-108">IIS'de bir sanal dizin oluşturarak IIS'de barındırılan hizmet ve service1.xamlx ve Web.config dosyalarında sanal dizine kopyalama, derlenmiş kod gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5996c-108">The service is hosted in IIS by creating a virtual directory in IIS and copying the service1.xamlx and Web.config files into the virtual directory, no compiled code is required.</span></span> <span data-ttu-id="5996c-109">Varsayılan olarak bu örnek otomatik olarak gerekli dosyaların WCF ve WF örnekleri için kurulum yönergeleri izlediğinizde oluşturulan sanal dizine kopyalar: [Windows Communication Foundation örnekleriiçinkerelikKurulumprosedürü](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) Visual Studio 2010'da yapılandırıldığında.</span><span class="sxs-lookup"><span data-stu-id="5996c-109">By default this sample will automatically copy the needed files into the virtual directory created when you follow the setup instructions for the WCF and WF samples: [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) when built in Visual Studio 2010.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5996c-110">Bu örneği kullanmak için</span><span class="sxs-lookup"><span data-stu-id="5996c-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="5996c-111">Proje çözümde yük [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] ve projeyi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5996c-111">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="5996c-112">[Çözüm temel dizin] \Client\bin\debug oluşturulan istemci uygulaması çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5996c-112">Run the Client application generated in [solution base directory]\Client\bin\debug.</span></span>  
  
3.  <span data-ttu-id="5996c-113">Uygulama Seçenekleri yazdırır bir seçenek seçer.</span><span class="sxs-lookup"><span data-stu-id="5996c-113">The application prints out options, selects an option.</span></span> <span data-ttu-id="5996c-114">Yanıt Evet veya Hayır bunları uygulama bazı sorular sorar (E/H anahtarları kullanarak).</span><span class="sxs-lookup"><span data-stu-id="5996c-114">The application then asks some questions, answer them yes or no (using Y/N keys).</span></span> <span data-ttu-id="5996c-115">Hizmet tamamlandığında sorunlarını tanılama, uygulama tanılama yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5996c-115">When the service is done diagnosing the issues, the application prints out a diagnosis.</span></span>  
  
4.  <span data-ttu-id="5996c-116">Uygulama geri seçenekleri gider.</span><span class="sxs-lookup"><span data-stu-id="5996c-116">The application goes back to the options.</span></span> <span data-ttu-id="5996c-117">Başka bir sorunu tanılamak ya da uygulamadan çıkın.</span><span class="sxs-lookup"><span data-stu-id="5996c-117">You can diagnose another problem or exit the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5996c-118">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="5996c-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5996c-119">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5996c-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5996c-120">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5996c-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5996c-121">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5996c-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLService`