---
title: "Özel maaş örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4ace7d38a456bb9d7f5dd59776b9ae5843b7b651
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="604c4-102">Özel maaş örnek</span><span class="sxs-lookup"><span data-stu-id="604c4-102">Custom Compensation Sample</span></span>
<span data-ttu-id="604c4-103">Bu örnek nasıl kullanılacağını göstermektedir <xref:System.Activities.Statements.CompensableActivity> ve özel maaş mantığını tanımlamak üzere kendi maaş işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="604c4-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="604c4-104">Bu örnekte Modellenen Kamyon kiralama Teşkilatı senaryodur.</span><span class="sxs-lookup"><span data-stu-id="604c4-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="604c4-105">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="604c4-105">Sample Details</span></span>  
 <span data-ttu-id="604c4-106">Benzetimli adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="604c4-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="604c4-107">Kullanıcı isteklerini kiralama teklifleri için belirli bir tarih kamyon.</span><span class="sxs-lookup"><span data-stu-id="604c4-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="604c4-108">Üç kamyon şirketler kurulur ve üç tırnak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="604c4-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="604c4-109">Kullanıcı bir kamyonu teklif seçer ve sipariş için kredi kartı ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="604c4-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="604c4-110">Uygulama, diğer iki kamyon tırnak işareti iptal eder.</span><span class="sxs-lookup"><span data-stu-id="604c4-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="604c4-111">Uygulama iade iptali 10 gün olursa premium olmayan hesaplar için veya rezervasyon tarihi önce daha az bir hizmet ücret ister.</span><span class="sxs-lookup"><span data-stu-id="604c4-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="604c4-112">Uygulama Kamyon kiralama ücreti ister.</span><span class="sxs-lookup"><span data-stu-id="604c4-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="604c4-113">Uygulama rezervasyon tarihi veya müşteri ayırması iptal etmeye karar kadar hangisi önce gelirse bekler.</span><span class="sxs-lookup"><span data-stu-id="604c4-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="604c4-114">Müşteri ayırması iptal ederse <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> özel maaş mantığı göre aşağıdaki mantık çalışır:</span><span class="sxs-lookup"><span data-stu-id="604c4-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="604c4-115">Müşterinin bir premium olmayan hesabı varsa ve 10 günden kısa bir süre önce rezervasyon tarihi sonra hizmet ücreti ise hala ücretlendirilir; Aksi takdirde, uygulama hizmeti ücret para iadeleri.</span><span class="sxs-lookup"><span data-stu-id="604c4-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="604c4-116">Compensable etkinlikleri (kamyon sipariş + kamyon sipariş ücreti) kalanı ters sırada yürütülmesi dengelemek için varsayılan maaş mantığı göre çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="604c4-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="604c4-117">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="604c4-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="604c4-118">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CustomCompensation.sln çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="604c4-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="604c4-119">\WF\Basic\Compensation\CustomCompensation dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="604c4-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="604c4-120">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="604c4-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="604c4-121">Uygulamayı çalıştırmak için CTRL + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="604c4-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="604c4-122">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="604c4-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="604c4-123">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="604c4-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="604c4-124">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="604c4-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="604c4-125">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="604c4-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`