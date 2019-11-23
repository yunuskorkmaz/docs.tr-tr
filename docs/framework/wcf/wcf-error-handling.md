---
title: WCF Hata İşleme
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 7e5c65da3fa13a3640c7a6948f1284d0c6ffdfc4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319941"
---
# <a name="wcf-error-handling"></a><span data-ttu-id="2a2d3-102">WCF Hata İşleme</span><span class="sxs-lookup"><span data-stu-id="2a2d3-102">WCF Error Handling</span></span>
<span data-ttu-id="2a2d3-103">Bir WCF uygulaması tarafından karşılaşılan hatalar üç gruptan birine aittir:</span><span class="sxs-lookup"><span data-stu-id="2a2d3-103">The errors encountered by a WCF application belong to one of three groups:</span></span>  
  
1. <span data-ttu-id="2a2d3-104">İletişim hataları</span><span class="sxs-lookup"><span data-stu-id="2a2d3-104">Communication Errors</span></span>  
  
2. <span data-ttu-id="2a2d3-105">Ara sunucu/kanal hataları</span><span class="sxs-lookup"><span data-stu-id="2a2d3-105">Proxy/Channel Errors</span></span>  
  
3. <span data-ttu-id="2a2d3-106">Uygulama hataları</span><span class="sxs-lookup"><span data-stu-id="2a2d3-106">Application Errors</span></span>  
  
 <span data-ttu-id="2a2d3-107">İletişim hataları, bir ağ kullanılamadığında, bir istemci yanlış bir adres kullandığında veya hizmet ana bilgisayarı gelen iletileri dinlemediğinde oluşur.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-107">Communication errors occur when a network is unavailable, a client uses an incorrect address, or the service host is not listening for incoming messages.</span></span> <span data-ttu-id="2a2d3-108">Bu tür hatalar istemciye <xref:System.ServiceModel.CommunicationException> veya <xref:System.ServiceModel.CommunicationException>türetilmiş sınıflar olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-108">Errors of this type are returned to the client as <xref:System.ServiceModel.CommunicationException> or <xref:System.ServiceModel.CommunicationException>-derived classes.</span></span>  
  
 <span data-ttu-id="2a2d3-109">Ara sunucu/kanal hataları, kanal veya proxy içinde oluşan hatalardır.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-109">Proxy/Channel errors are errors that occur within the channel or proxy itself.</span></span> <span data-ttu-id="2a2d3-110">Bu tür hatalar şunlardır: kapatılmış bir proxy veya kanal kullanılmaya çalışılıyor, istemci ile hizmet arasında bir anlaşma uyumsuzluğu var veya istemcinin kimlik bilgileri hizmet tarafından reddedildi.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-110">Errors of this type include: attempting to use a proxy or channel that has been closed, a contract mismatch exists between the client and service, or the client’s credentials are rejected by the service.</span></span> <span data-ttu-id="2a2d3-111">Bu kategoride çok fazla sayıda farklı hata türü var, burada listelemek için çok fazla.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-111">There are many different types of errors in this category, too many to list here.</span></span> <span data-ttu-id="2a2d3-112">Bu tür hatalar istemciye olduğu gibi döndürülür (özel durum nesnelerinde hiçbir dönüşüm gerçekleştirilmez).</span><span class="sxs-lookup"><span data-stu-id="2a2d3-112">Errors of this type are returned to the client as-is (no transformation is performed on the exception objects).</span></span>  
  
 <span data-ttu-id="2a2d3-113">Uygulama hataları, bir hizmet işleminin yürütülmesi sırasında oluşur.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-113">Application errors occur during the execution of a service operation.</span></span> <span data-ttu-id="2a2d3-114">Bu tür hatalar istemciye <xref:System.ServiceModel.FaultException> veya <xref:System.ServiceModel.FaultException%601>olarak gönderilir.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-114">Errors of this kind are sent to the client as <xref:System.ServiceModel.FaultException> or <xref:System.ServiceModel.FaultException%601>.</span></span>  
  
 <span data-ttu-id="2a2d3-115">WCF 'de hata işleme, aşağıdakilerden biri veya birkaçı tarafından gerçekleştirilir:</span><span class="sxs-lookup"><span data-stu-id="2a2d3-115">Error handling in WCF is performed by one or more of the following:</span></span>  
  
- <span data-ttu-id="2a2d3-116">Oluşturulan özel durumu doğrudan işleme.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-116">Directly handling the exception thrown.</span></span> <span data-ttu-id="2a2d3-117">Bu yalnızca iletişim ve proxy/kanal hataları için yapılır.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-117">This is only done for communication and proxy/channel errors.</span></span>  
  
- <span data-ttu-id="2a2d3-118">Hata sözleşmelerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2a2d3-118">Using fault contracts</span></span>  
  
- <span data-ttu-id="2a2d3-119"><xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimini uygulama</span><span class="sxs-lookup"><span data-stu-id="2a2d3-119">Implementing the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface</span></span>  
  
- <span data-ttu-id="2a2d3-120"><xref:System.ServiceModel.ServiceHost> olaylarını işleme</span><span class="sxs-lookup"><span data-stu-id="2a2d3-120">Handling <xref:System.ServiceModel.ServiceHost> events</span></span>  
  
## <a name="fault-contracts"></a><span data-ttu-id="2a2d3-121">Hata sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="2a2d3-121">Fault Contracts</span></span>  
 <span data-ttu-id="2a2d3-122">Hata sözleşmeleri, hizmet işlemi sırasında platformdan bağımsız bir şekilde oluşabilecek hataları tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-122">Fault contracts allow you to define the errors that can occur during service operation in a platform independent way.</span></span> <span data-ttu-id="2a2d3-123">Varsayılan olarak, bir hizmet işlemi içinden oluşturulan tüm özel durumlar istemciye <xref:System.ServiceModel.FaultException> nesnesi olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-123">By default all exceptions thrown from within a service operation will be returned to the client as a <xref:System.ServiceModel.FaultException> object.</span></span> <span data-ttu-id="2a2d3-124"><xref:System.ServiceModel.FaultException> nesnesi çok az bilgi içerecektir.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-124">The <xref:System.ServiceModel.FaultException> object will contain very little information.</span></span> <span data-ttu-id="2a2d3-125">Bir hata sözleşmesi tanımlayarak ve hatayı <xref:System.ServiceModel.FaultException%601>olarak döndürerek istemciye gönderilen bilgileri denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-125">You can control the information sent to the client by defining a fault contract and returning the error as a <xref:System.ServiceModel.FaultException%601>.</span></span> <span data-ttu-id="2a2d3-126">Daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="2a2d3-126">For more information, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="ierrorhandler"></a><span data-ttu-id="2a2d3-127">IErrorHandler</span><span class="sxs-lookup"><span data-stu-id="2a2d3-127">IErrorHandler</span></span>  
 <span data-ttu-id="2a2d3-128"><xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi, WCF uygulamanızın hatalara nasıl yanıt vereceğini öğrenmek için daha fazla denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-128">The <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface allows you more control over how your WCF application responds to errors.</span></span>  <span data-ttu-id="2a2d3-129">İstemciye döndürülen hata iletisi üzerinde tam denetim sağlar ve günlüğe kaydetme gibi özel hata işleme gerçekleştirmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-129">It gives you full control over the fault message that is returned to the client and allows you to perform custom error processing such as logging.</span></span>  <span data-ttu-id="2a2d3-130"><xref:System.ServiceModel.Dispatcher.IErrorHandler> ve [hata işleme ve raporlama üzerinde denetim genişletme](./samples/extending-control-over-error-handling-and-reporting.md) hakkında daha fazla bilgi için</span><span class="sxs-lookup"><span data-stu-id="2a2d3-130">For more information about <xref:System.ServiceModel.Dispatcher.IErrorHandler> and [Extending Control Over Error Handling and Reporting](./samples/extending-control-over-error-handling-and-reporting.md)</span></span>  
  
## <a name="servicehost-events"></a><span data-ttu-id="2a2d3-131">ServiceHost olayları</span><span class="sxs-lookup"><span data-stu-id="2a2d3-131">ServiceHost Events</span></span>  
 <span data-ttu-id="2a2d3-132"><xref:System.ServiceModel.ServiceHost> sınıfı Hizmetleri barındırır ve hataları işlemek için gerekebilecek birkaç olayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2a2d3-132">The <xref:System.ServiceModel.ServiceHost> class hosts services and defines several events that may be needed for handling errors.</span></span> <span data-ttu-id="2a2d3-133">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a2d3-133">For example:</span></span>  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 <span data-ttu-id="2a2d3-134">Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceHost></span><span class="sxs-lookup"><span data-stu-id="2a2d3-134">For more information, see <xref:System.ServiceModel.ServiceHost></span></span>
