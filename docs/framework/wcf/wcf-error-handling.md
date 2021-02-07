---
description: 'Daha fazla bilgi edinin: WCF hata Işleme'
title: WCF Hata İşleme
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 57f2c5078e0f73ff57eec79041cb7a2b2d42b498
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668181"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="6f051-103">WCF Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="6f051-103">WCF Error Handling</span></span>

<span data-ttu-id="6f051-104">Bir WCF uygulaması tarafından karşılaşılan hatalar üç gruptan birine aittir:</span><span class="sxs-lookup"><span data-stu-id="6f051-104">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="6f051-105">İletişim hataları</span><span class="sxs-lookup"><span data-stu-id="6f051-105">Communication Errors</span></span>  
  
2. <span data-ttu-id="6f051-106">Ara sunucu/kanal hataları</span><span class="sxs-lookup"><span data-stu-id="6f051-106">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="6f051-107">Uygulama hataları</span><span class="sxs-lookup"><span data-stu-id="6f051-107">Application Errors</span></span>  
  
 <span data-ttu-id="6f051-108">İletişim hataları, bir ağ kullanılamadığında, bir istemci yanlış bir adres kullandığında veya hizmet ana bilgisayarı gelen iletileri dinlemediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f051-108">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="6f051-109">Bu tür hatalar istemciye <xref:System.ServiceModel.CommunicationException> ya da <xref:System.ServiceModel.CommunicationException> türetilmiş sınıflar olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6f051-109">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="6f051-110">Ara sunucu/kanal hataları, kanal veya proxy içinde oluşan hatalardır.</span><span class="sxs-lookup"><span data-stu-id="6f051-110">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="6f051-111">Bu tür hatalar şunlardır: kapatılmış bir proxy veya kanal kullanılmaya çalışılıyor, istemci ile hizmet arasında bir anlaşma uyumsuzluğu var veya istemcinin kimlik bilgileri hizmet tarafından reddedildi.</span><span class="sxs-lookup"><span data-stu-id="6f051-111">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="6f051-112">Bu kategoride çok fazla sayıda farklı hata türü var, burada listelemek için çok fazla.</span><span class="sxs-lookup"><span data-stu-id="6f051-112">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="6f051-113">Bu tür hatalar istemciye olduğu gibi döndürülür (özel durum nesnelerinde hiçbir dönüşüm gerçekleştirilmez).</span><span class="sxs-lookup"><span data-stu-id="6f051-113">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="6f051-114">Uygulama hataları, bir hizmet işleminin yürütülmesi sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="6f051-114">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="6f051-115">Bu tür hatalar istemciye veya olarak gönderilir <xref:System.ServiceModel.FaultException> <xref:System.ServiceModel.FaultException%601> .</span><span class="sxs-lookup"><span data-stu-id="6f051-115">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="6f051-116">WCF 'de hata işleme, aşağıdakilerden biri veya birkaçı tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="6f051-116">Error handling in WCF is performed by one or more of the following:</span></span>  
  
- <span data-ttu-id="6f051-117">Oluşturulan özel durumu doğrudan işleme.</span><span class="sxs-lookup"><span data-stu-id="6f051-117">Directly handling the exception thrown.</span></span> <span data-ttu-id="6f051-118">Bu yalnızca iletişim ve proxy/kanal hataları için yapılır.</span><span class="sxs-lookup"><span data-stu-id="6f051-118">This is only done for communication and proxy/channel errors.</span></span>  
  
- <span data-ttu-id="6f051-119">Hata sözleşmelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6f051-119">Using fault contracts</span></span>  
  
- <span data-ttu-id="6f051-120">Arabirimi uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler></span><span class="sxs-lookup"><span data-stu-id="6f051-120">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
- <span data-ttu-id="6f051-121"><xref:System.ServiceModel.ServiceHost>Olayları işleme</span><span class="sxs-lookup"><span data-stu-id="6f051-121">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="6f051-122">Hata sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="6f051-122">Fault Contracts</span></span>  

 <span data-ttu-id="6f051-123">Hata sözleşmeleri, hizmet işlemi sırasında platformdan bağımsız bir şekilde oluşabilecek hataları tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f051-123">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="6f051-124">Varsayılan olarak, bir hizmet işlemi içinden oluşturulan tüm özel durumlar istemciye bir nesne olarak döndürülür <xref:System.ServiceModel.FaultException> .</span><span class="sxs-lookup"><span data-stu-id="6f051-124">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="6f051-125"><xref:System.ServiceModel.FaultException>Nesne çok az bilgi içerecektir.</span><span class="sxs-lookup"><span data-stu-id="6f051-125">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="6f051-126">Bir hata sözleşmesi tanımlayarak ve hatayı bir olarak döndürerek istemciye gönderilen bilgileri kontrol edebilirsiniz <xref:System.ServiceModel.FaultException%601> .</span><span class="sxs-lookup"><span data-stu-id="6f051-126">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="6f051-127">Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="6f051-127">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="6f051-128">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="6f051-128">IErrorHandler</span></span>  

 <span data-ttu-id="6f051-129"><xref:System.ServiceModel.Dispatcher.IErrorHandler>Arabirim, WCF uygulamanızın hatalara nasıl yanıt vereceğini daha fazla kontrol etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f051-129">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="6f051-130">İstemciye döndürülen hata iletisi üzerinde tam denetim sağlar ve günlüğe kaydetme gibi özel hata işleme gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6f051-130">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="6f051-131"><xref:System.ServiceModel.Dispatcher.IErrorHandler> [Hata Işleme ve raporlama üzerinde denetim](./samples/extending-control-over-error-handling-and-reporting.md) hakkında daha fazla bilgi için</span><span class="sxs-lookup"><span data-stu-id="6f051-131">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](./samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="6f051-132">ServiceHost olayları</span><span class="sxs-lookup"><span data-stu-id="6f051-132">ServiceHost Events</span></span>  

 <span data-ttu-id="6f051-133"><xref:System.ServiceModel.ServiceHost>Sınıfı Hizmetleri barındırır ve hataları işlemek için gerekebilecek birkaç olayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6f051-133">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="6f051-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6f051-134">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="6f051-135">Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6f051-135">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
