---
title: Özel Dengeleme örnek
ms.date: 03/30/2017
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
ms.openlocfilehash: ac141a48f87f5b14f6b528f7b3ceb7fdddeaf2d2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503725"
---
# <a name="custom-compensation-sample"></a><span data-ttu-id="76d19-102">Özel Dengeleme örnek</span><span class="sxs-lookup"><span data-stu-id="76d19-102">Custom Compensation Sample</span></span>
<span data-ttu-id="76d19-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.CompensableActivity> ve özel telafi mantığı tanımlamak için kendi maaş işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="76d19-103">This sample shows how to use <xref:System.Activities.Statements.CompensableActivity> and its compensation handler to define custom compensation logic.</span></span> <span data-ttu-id="76d19-104">Bu örnekte modellenmiş bir Kamyon kiralama kurumu senaryodur.</span><span class="sxs-lookup"><span data-stu-id="76d19-104">The scenario modeled in this sample is a Truck Rental Agency.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="76d19-105">Örnek Ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="76d19-105">Sample Details</span></span>  
 <span data-ttu-id="76d19-106">Benzetimli adımlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="76d19-106">The steps simulated are:</span></span>  
  
1.  <span data-ttu-id="76d19-107">Kullanıcı isteklerinin kiralama teklifleri için belirli bir tarihten kamyon.</span><span class="sxs-lookup"><span data-stu-id="76d19-107">The user requests truck rental quotes for a given date.</span></span>  
  
2.  <span data-ttu-id="76d19-108">Üç kamyon şirketin iletişim kurulur ve üç tırnak sağlanır.</span><span class="sxs-lookup"><span data-stu-id="76d19-108">Three truck companies are contacted and the three quotes are provided.</span></span>  
  
3.  <span data-ttu-id="76d19-109">Kullanıcı, tek bir kamyon teklif seçer ve sıralamak için kredi kartı ile devam eder.</span><span class="sxs-lookup"><span data-stu-id="76d19-109">The user selects one truck quote and proceeds to order by credit card.</span></span>  
  
4.  <span data-ttu-id="76d19-110">Uygulama, diğer iki kamyon tırnak iptal eder.</span><span class="sxs-lookup"><span data-stu-id="76d19-110">The application cancels the other two truck quotes.</span></span>  
  
5.  <span data-ttu-id="76d19-111">Uygulamayı iptal 10 gün olursa premium olmayan hesaplar için iade olmayan veya ayırma tarihten önce hizmet için ücret.</span><span class="sxs-lookup"><span data-stu-id="76d19-111">The application charges a service fee that is non-refundable for non-premium accounts if cancelation happens 10 days or less prior to the reservation date.</span></span>  
  
6.  <span data-ttu-id="76d19-112">Uygulama Kamyon kiralama ücret.</span><span class="sxs-lookup"><span data-stu-id="76d19-112">The application charges the truck rental fee.</span></span>  
  
7.  <span data-ttu-id="76d19-113">Uygulama, rezervasyon tarihi veya ayırmayı iptal etmek müşteri karar kadar hangisi önce gelirse bekler.</span><span class="sxs-lookup"><span data-stu-id="76d19-113">The application waits until the reservation date or until the customer decided to cancel the reservation, whichever comes first.</span></span>  
  
8.  <span data-ttu-id="76d19-114">Müşteri ayırmayı iptal ederse <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> özel telafi mantığının göre aşağıdaki mantık çalıştırır:</span><span class="sxs-lookup"><span data-stu-id="76d19-114">If the customer cancels the reservation, the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> custom compensation logic runs according to the following logic:</span></span>  
  
    1.  <span data-ttu-id="76d19-115">Müşteri, bir premium olmayan hesabına sahiptir ve 10 günden önce rezervasyon tarihi ve ardından hizmet ücretinin ise hala ücretlendirilir; Aksi takdirde uygulama, hizmet ücretinin mahsup işlemleri.</span><span class="sxs-lookup"><span data-stu-id="76d19-115">If the customer has a non-premium account and it is less than 10 days prior to the reservation date, then the service fee is still charged; otherwise, the application refunds the service fee.</span></span>  
  
    2.  <span data-ttu-id="76d19-116">Rest (kamyon sipariş + kamyon siparişi masrafı) compensable etkinliklerinin ters sırada yürütülmesini dengelemek için varsayılan telafi mantığı göre çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="76d19-116">The rest of the compensable activities (truck order + truck order fee) are run according to the default compensation logic, which is to compensate in reverse order of execution.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="76d19-117">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="76d19-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="76d19-118">Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], CustomCompensation.sln çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="76d19-118">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the CustomCompensation.sln solution.</span></span> <span data-ttu-id="76d19-119">Bunu \WF\Basic\Compensation\CustomCompensation dizininde bulunur.</span><span class="sxs-lookup"><span data-stu-id="76d19-119">It is located in the \WF\Basic\Compensation\CustomCompensation directory.</span></span>  
  
2.  <span data-ttu-id="76d19-120">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="76d19-120">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="76d19-121">Uygulamayı çalıştırmak için CTRL + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="76d19-121">Press CTRL + F5 to run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="76d19-122">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="76d19-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="76d19-123">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="76d19-123">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="76d19-124">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="76d19-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="76d19-125">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="76d19-125">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`