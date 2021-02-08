---
description: 'Hakkında daha fazla bilgi edinin: MsmqBindingElementBase'
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 3aa5ec2343d73798f1cf5e3c7d4b5a8282f97ac9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803184"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="5d8ed-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="5d8ed-103">MsmqBindingElementBase</span></span>

<span data-ttu-id="5d8ed-104">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="5d8ed-104">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d8ed-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d8ed-105">Syntax</span></span>  
  
```csharp  
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
  
## <a name="methods"></a><span data-ttu-id="5d8ed-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5d8ed-106">Methods</span></span>  

 <span data-ttu-id="5d8ed-107">MsmqBindingElementBase sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-107">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5d8ed-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5d8ed-108">Properties</span></span>  

 <span data-ttu-id="5d8ed-109">MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5d8ed-109">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="5d8ed-110">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="5d8ed-110">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="5d8ed-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5d8ed-111">Data type: string</span></span>  
  
 <span data-ttu-id="5d8ed-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-113">Bu, zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği her uygulama için atılacak ileti sırasının konumunu içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-113">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="5d8ed-114">Özelliğinde</span><span class="sxs-lookup"><span data-stu-id="5d8ed-114">DeadLetterQueue</span></span>  

 <span data-ttu-id="5d8ed-115">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5d8ed-115">Data type: string</span></span>  
  
 <span data-ttu-id="5d8ed-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-117">Kullanılacak atılacak ileti sırasının türünü gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-117">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="5d8ed-118">Dayanıklı</span><span class="sxs-lookup"><span data-stu-id="5d8ed-118">Durable</span></span>  

 <span data-ttu-id="5d8ed-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="5d8ed-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d8ed-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-121">Bu bağlama tarafından işlenen iletilerin dayanıklı veya geçici olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-121">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="5d8ed-122">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="5d8ed-122">ExactlyOnce</span></span>  

 <span data-ttu-id="5d8ed-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="5d8ed-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d8ed-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-125">Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp alınmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-125">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="5d8ed-126">Maxretrydöngüleri</span><span class="sxs-lookup"><span data-stu-id="5d8ed-126">MaxRetryCycles</span></span>  

 <span data-ttu-id="5d8ed-127">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="5d8ed-127">Data type: sint32</span></span>  
  
 <span data-ttu-id="5d8ed-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-129">İleti alma uygulamasına iletileri teslim girişiminde bulunan en fazla yeniden deneme döngüsü sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-129">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="5d8ed-130">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="5d8ed-130">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="5d8ed-131">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5d8ed-131">Data type: string</span></span>  
  
 <span data-ttu-id="5d8ed-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-133">Zarar iletisi işleme ayarları.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-133">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="5d8ed-134">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="5d8ed-134">ReceiveRetryCount</span></span>  

 <span data-ttu-id="5d8ed-135">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="5d8ed-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="5d8ed-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-137">Uygulama sırasından okunan bir ileti üzerinde anında yeniden deneme girişimlerinin en fazla sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-137">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="5d8ed-138">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="5d8ed-138">RetryCycleDelay</span></span>  

 <span data-ttu-id="5d8ed-139">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="5d8ed-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="5d8ed-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-141">Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken deneme döngüleri arasındaki gecikme süresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-141">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="5d8ed-142">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="5d8ed-142">TimeToLive</span></span>  

 <span data-ttu-id="5d8ed-143">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="5d8ed-143">Data type: datetime</span></span>  
  
 <span data-ttu-id="5d8ed-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-145">Bu bağlama tarafından işlenen iletilerin, süresi dolmadan önce kuyrukta ne kadar süre içinde kalabileceğini belirten zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-145">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="5d8ed-146">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="5d8ed-146">UseMsmqTracing</span></span>  

 <span data-ttu-id="5d8ed-147">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="5d8ed-147">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d8ed-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-149">Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-149">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="5d8ed-150">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="5d8ed-150">UseSourceJournal</span></span>  

 <span data-ttu-id="5d8ed-151">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="5d8ed-151">Data type: boolean</span></span>  
  
 <span data-ttu-id="5d8ed-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="5d8ed-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5d8ed-153">Bu bağlama tarafından işlenen iletilerin kopyalarının kaynak günlük kuyruğunda depolanması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-153">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d8ed-154">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d8ed-154">Requirements</span></span>  
  
|<span data-ttu-id="5d8ed-155">MOF</span><span class="sxs-lookup"><span data-stu-id="5d8ed-155">MOF</span></span>|<span data-ttu-id="5d8ed-156">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-156">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5d8ed-157">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5d8ed-157">Namespace</span></span>|<span data-ttu-id="5d8ed-158">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="5d8ed-158">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5d8ed-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-159">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
