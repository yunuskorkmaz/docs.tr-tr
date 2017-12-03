---
title: "WCF Hata İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26dfea83400b5d601fabc5cfb52bc71a4d5e4f6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-error-handling"></a><span data-ttu-id="26ea0-102">WCF Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="26ea0-102">WCF Error Handling</span></span>
<span data-ttu-id="26ea0-103">Bir WCF uygulaması tarafından karşılaşılan hataları üç gruplardan birine ait:</span><span class="sxs-lookup"><span data-stu-id="26ea0-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1.  <span data-ttu-id="26ea0-104">İletişim hataları</span><span class="sxs-lookup"><span data-stu-id="26ea0-104">Communication Errors</span></span>  
  
2.  <span data-ttu-id="26ea0-105">Proxy/kanal hataları</span><span class="sxs-lookup"><span data-stu-id="26ea0-105">Proxy/Channel Errors</span></span>  
  
3.  <span data-ttu-id="26ea0-106">Uygulama hataları</span><span class="sxs-lookup"><span data-stu-id="26ea0-106">Application Errors</span></span>  
  
 <span data-ttu-id="26ea0-107">Ağ kullanılamıyor, istemci yanlış bir adres kullanır ya da hizmet konağı gelen iletiler için dinleme yapmıyor iletişim hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="26ea0-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="26ea0-108">Bu tür hataları istemciye döndürülen <xref:System.ServiceModel.CommunicationException> veya <xref:System.ServiceModel.CommunicationException>-türetilmiş sınıfları.</span><span class="sxs-lookup"><span data-stu-id="26ea0-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="26ea0-109">Proxy/kanal, kanal veya proxy kendisini içinde oluşan hataları hatalardır.</span><span class="sxs-lookup"><span data-stu-id="26ea0-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="26ea0-110">Bu tür hataları şunlardır: bir proxy kullanır veya bu kanal girişimi kapatıldı, istemci ile hizmet arasında bir sözleşme uyumsuzluğu var. veya istemci kimlik bilgileri hizmeti tarafından reddedilir.</span><span class="sxs-lookup"><span data-stu-id="26ea0-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="26ea0-111">Farklı türlerde bu kategorideki hataları vardır burada listelemek için çok fazla.</span><span class="sxs-lookup"><span data-stu-id="26ea0-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="26ea0-112">Bu tür hataları istemciye döndürülen-olduğu (hiçbir dönüştürme özel durum nesnelerde gerçekleştirilir).</span><span class="sxs-lookup"><span data-stu-id="26ea0-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="26ea0-113">Uygulama hataları bir hizmet işlemi yürütme sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="26ea0-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="26ea0-114">Bu tür hataların istemci olarak gönderilen <xref:System.ServiceModel.FaultException> veya <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="26ea0-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="26ea0-115">WCF'de işleme hatası, bir veya daha fazlasını tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="26ea0-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="26ea0-116">Doğrudan oluşturulan özel durum işleme.</span><span class="sxs-lookup"><span data-stu-id="26ea0-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="26ea0-117">Bu, yalnızca iletişimi ve proxy/kanal hataları için yapılır.</span><span class="sxs-lookup"><span data-stu-id="26ea0-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="26ea0-118">Hataya sözleşmeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="26ea0-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="26ea0-119">Uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi</span><span class="sxs-lookup"><span data-stu-id="26ea0-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="26ea0-120">İşleme <xref:System.ServiceModel.ServiceHost> olayları</span><span class="sxs-lookup"><span data-stu-id="26ea0-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="26ea0-121">Hataya sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="26ea0-121">Fault Contracts</span></span>  
 <span data-ttu-id="26ea0-122">Hataya sözleşmeleri izin Platform hizmet işlemi sırasında oluşabilecek hataları tanımlamanızı bağımsız şekilde.</span><span class="sxs-lookup"><span data-stu-id="26ea0-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="26ea0-123">Varsayılan olarak gelen bir hizmet işlemi içinde oluşturulan tüm özel durumları istemciye döndürülecek bir <xref:System.ServiceModel.FaultException> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="26ea0-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="26ea0-124"><xref:System.ServiceModel.FaultException> Nesne çok az bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="26ea0-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="26ea0-125">Bir arıza sözleşmesi tanımlayarak ve hata olarak döndüren istemciye gönderilen bilgiler denetleyebilirsiniz bir <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="26ea0-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="26ea0-126">[Belirtme ve sözleşme ve hizmetlerde hataları işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="26ea0-126"> [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="26ea0-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="26ea0-127">IErrorHandler</span></span>  
 <span data-ttu-id="26ea0-128"><xref:System.ServiceModel.Dispatcher.IErrorHandler> Arabirimi WCF uygulamanızın hatalarının nasıl yanıt vereceğini üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="26ea0-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="26ea0-129">İstemciye döndürülen ve günlüğe kaydetme gibi işlenirken özel hata gerçekleştirmenize olanak sağlayan hata iletisi üzerinde tam denetim verir.</span><span class="sxs-lookup"><span data-stu-id="26ea0-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<span data-ttu-id="26ea0-130"><xref:System.ServiceModel.Dispatcher.IErrorHandler> ve [üzerinden hata işleme ve bildirme denetimini genişletme](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="26ea0-130"> <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="26ea0-131">ServiceHost olayları</span><span class="sxs-lookup"><span data-stu-id="26ea0-131">ServiceHost Events</span></span>  
 <span data-ttu-id="26ea0-132"><xref:System.ServiceModel.ServiceHost> Sınıfı konakları Hizmetleri ve hataları işlemek için gerekli olabilecek çeşitli olaylarını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="26ea0-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="26ea0-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="26ea0-133">For example:</span></span>  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="26ea0-134"><xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="26ea0-134"> <xref:System.ServiceModel.ServiceHost></span></span>
