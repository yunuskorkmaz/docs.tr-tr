---
title: WCF Hata İşleme
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: d70edacd2447fbe0b0b6db42b93f699ce7c17003
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306293"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="faf5c-102">WCF Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="faf5c-102">WCF Error Handling</span></span>
<span data-ttu-id="faf5c-103">WCF uygulaması tarafından karşılaşılan hataları üç gruplardan birine ait:</span><span class="sxs-lookup"><span data-stu-id="faf5c-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="faf5c-104">İletişim hataları</span><span class="sxs-lookup"><span data-stu-id="faf5c-104">Communication Errors</span></span>  
  
2. <span data-ttu-id="faf5c-105">Proxy/kanal hataları</span><span class="sxs-lookup"><span data-stu-id="faf5c-105">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="faf5c-106">Uygulama hataları</span><span class="sxs-lookup"><span data-stu-id="faf5c-106">Application Errors</span></span>  
  
 <span data-ttu-id="faf5c-107">İletişim hataları ağ kullanılamıyor, istemci yanlış bir adresi kullanır veya hizmet ana bilgisayarı gelen iletiler için dinleme yapmıyor ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="faf5c-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="faf5c-108">Bu tür hatalar istemciye döndürülür <xref:System.ServiceModel.CommunicationException> veya <xref:System.ServiceModel.CommunicationException>-türetilmiş sınıflar.</span><span class="sxs-lookup"><span data-stu-id="faf5c-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="faf5c-109">Proxy/kanal, kanal veya proxy kendisi içinde oluşan hataları hatalardır.</span><span class="sxs-lookup"><span data-stu-id="faf5c-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="faf5c-110">Bu tür hatalar vardır: bir ara sunucu kullanmak veya, kanal çalışılıyor kapatıldı, hizmet ve istemci arasında bir anlaşma uyumsuzluğu var. veya istemci kimlik bilgileri hizmet tarafından reddedilir.</span><span class="sxs-lookup"><span data-stu-id="faf5c-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="faf5c-111">Farklı türlerde bu kategoriye giren hataları vardır. burada listelemek için çok fazla.</span><span class="sxs-lookup"><span data-stu-id="faf5c-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="faf5c-112">Bu tür hatalar istemciye döndürülür-olduğu (hiçbir dönüştürme yapılmadı, özel durum nesnelerinde gerçekleştirilir).</span><span class="sxs-lookup"><span data-stu-id="faf5c-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="faf5c-113">Bir hizmet işlemi yürütülürken uygulama hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="faf5c-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="faf5c-114">Bu tür hatalar istemciye gönderilen <xref:System.ServiceModel.FaultException> veya <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="faf5c-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="faf5c-115">WCF'de işleme hata, bir veya daha fazlasını tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="faf5c-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
-   <span data-ttu-id="faf5c-116">Doğrudan özel durum işleme.</span><span class="sxs-lookup"><span data-stu-id="faf5c-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="faf5c-117">Bu yalnızca iletişimi ve proxy/kanal hataları için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="faf5c-117">This is only done for communication and proxy/channel errors.</span></span>  
  
-   <span data-ttu-id="faf5c-118">Hata sözleşmeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="faf5c-118">Using fault contracts</span></span>  
  
-   <span data-ttu-id="faf5c-119">Uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi</span><span class="sxs-lookup"><span data-stu-id="faf5c-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
-   <span data-ttu-id="faf5c-120">İşleme <xref:System.ServiceModel.ServiceHost> olayları</span><span class="sxs-lookup"><span data-stu-id="faf5c-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="faf5c-121">Hata sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="faf5c-121">Fault Contracts</span></span>  
 <span data-ttu-id="faf5c-122">Hata sözleşmelerine izin vermek, Platform hizmeti işlemi sırasında oluşabilecek hataları tanımlamak bağımsız bir şekilde.</span><span class="sxs-lookup"><span data-stu-id="faf5c-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="faf5c-123">Varsayılan olarak, gelen bir hizmet işlemi içinde oluşturulan tüm özel durumlar istemciye döndürülecek bir <xref:System.ServiceModel.FaultException> nesne.</span><span class="sxs-lookup"><span data-stu-id="faf5c-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="faf5c-124"><xref:System.ServiceModel.FaultException> Nesne çok az bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="faf5c-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="faf5c-125">Hatalı sözleşme tanımlayarak ve hata olarak döndüren istemciye gönderilen bilgiler denetleyebilirsiniz bir <xref:System.ServiceModel.FaultException%601>.</span><span class="sxs-lookup"><span data-stu-id="faf5c-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="faf5c-126">Daha fazla bilgi için [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="faf5c-126">For more information, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="faf5c-127">Ierrorhandler</span><span class="sxs-lookup"><span data-stu-id="faf5c-127">IErrorHandler</span></span>  
 <span data-ttu-id="faf5c-128"><xref:System.ServiceModel.Dispatcher.IErrorHandler> Arabirim WCF uygulamanızı hatalara nasıl yanıt vereceğini üzerinde daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="faf5c-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="faf5c-129">Özel Hata günlük kaydı gibi işlem yapmanıza olanak tanır ve istemciye döndürülen hata iletisi üzerinde tam denetim verir.</span><span class="sxs-lookup"><span data-stu-id="faf5c-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="faf5c-130">Hakkında daha fazla bilgi için <xref:System.ServiceModel.Dispatcher.IErrorHandler> ve [genişletme denetiminin üzerine hata işleme ve Raporlama](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="faf5c-130">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="faf5c-131">ServiceHost Events</span><span class="sxs-lookup"><span data-stu-id="faf5c-131">ServiceHost Events</span></span>  
 <span data-ttu-id="faf5c-132"><xref:System.ServiceModel.ServiceHost> Sınıfı konakları Hizmetleri ve hataları işleme için gerekli olabilecek çeşitli olayları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="faf5c-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="faf5c-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="faf5c-133">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="faf5c-134">Daha fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="faf5c-134">For more information, see</span></span> <xref:System.ServiceModel.ServiceHost>
