---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 009596ee8fd7218a07487183d932e91dad07797c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="8f9d7-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="8f9d7-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="8f9d7-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="8f9d7-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f9d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f9d7-104">Syntax</span></span>  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8f9d7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8f9d7-105">Methods</span></span>  
 <span data-ttu-id="8f9d7-106">MsmqBindingElementBase sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8f9d7-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8f9d7-107">Properties</span></span>  
 <span data-ttu-id="8f9d7-108">MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8f9d7-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="8f9d7-109">customDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="8f9d7-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="8f9d7-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8f9d7-110">Data type: string</span></span>  
  
 <span data-ttu-id="8f9d7-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-112">Süresi dolan veya aktarımı veya teslim başarısız olmuş iletileri yerleştirildiği her uygulama için sahipsiz sıra konumunu içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="8f9d7-113">deadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="8f9d7-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="8f9d7-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8f9d7-114">Data type: string</span></span>  
  
 <span data-ttu-id="8f9d7-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-116">Kullanılacak sahipsiz sıra türünü gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="8f9d7-117">dayanıklı</span><span class="sxs-lookup"><span data-stu-id="8f9d7-117">Durable</span></span>  
 <span data-ttu-id="8f9d7-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8f9d7-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="8f9d7-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-120">Bu bağlama tarafından işlenen iletilerin kalıcı veya geçici olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="8f9d7-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="8f9d7-121">ExactlyOnce</span></span>  
 <span data-ttu-id="8f9d7-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8f9d7-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8f9d7-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-124">Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınan olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="8f9d7-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="8f9d7-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="8f9d7-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8f9d7-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="8f9d7-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-128">İletileri teslim alma işlemini yapan uygulamanın için denemek için yeniden deneme döngüsü sayısı.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="8f9d7-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="8f9d7-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="8f9d7-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="8f9d7-130">Data type: string</span></span>  
  
 <span data-ttu-id="8f9d7-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-132">Zehirli ileti işleme yönelik ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="8f9d7-133">receiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="8f9d7-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="8f9d7-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="8f9d7-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="8f9d7-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-136">Hemen yeniden deneme sayısı uygulama sırasından okunan bir ileti üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="8f9d7-137">retryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="8f9d7-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="8f9d7-138">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8f9d7-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="8f9d7-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-140">Yeniden deneme arasındaki gecikme süresini belirten bir değer hemen teslim edilemeyen bir ileti teslim çalışılırken geçiş yapar.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="8f9d7-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="8f9d7-141">TimeToLive</span></span>  
 <span data-ttu-id="8f9d7-142">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="8f9d7-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="8f9d7-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-144">Süresi dolmadan önce bu bağlama tarafından işlenen ne kadar süreyle iletileri gösterir zaman aralığını sırada olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="8f9d7-145">useMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="8f9d7-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="8f9d7-146">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8f9d7-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="8f9d7-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-148">Bu bağlama tarafından işlenen iletileri olup olmadığını gösteren bir Boole değeri izlenen.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="8f9d7-149">useSourceJournal</span><span class="sxs-lookup"><span data-stu-id="8f9d7-149">UseSourceJournal</span></span>  
 <span data-ttu-id="8f9d7-150">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="8f9d7-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="8f9d7-151">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="8f9d7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f9d7-152">Bu bağlama tarafından işlenen iletilerin kopyalarını kaynak günlük sırasındaki depolanması gerekip gerekmediğini gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f9d7-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f9d7-153">Requirements</span></span>  
  
|<span data-ttu-id="8f9d7-154">MOF</span><span class="sxs-lookup"><span data-stu-id="8f9d7-154">MOF</span></span>|<span data-ttu-id="8f9d7-155">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8f9d7-156">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="8f9d7-156">Namespace</span></span>|<span data-ttu-id="8f9d7-157">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8f9d7-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f9d7-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f9d7-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
