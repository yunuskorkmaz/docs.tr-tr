---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 48d26bfa9074fd605e3545579f0bdc2744dfc7d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267870"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="1a0d9-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="1a0d9-102">MsmqBindingElementBase</span></span>

<span data-ttu-id="1a0d9-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="1a0d9-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0d9-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a0d9-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1a0d9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1a0d9-105">Methods</span></span>  

 <span data-ttu-id="1a0d9-106">MsmqBindingElementBase sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1a0d9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1a0d9-107">Properties</span></span>  

 <span data-ttu-id="1a0d9-108">MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1a0d9-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="1a0d9-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="1a0d9-109">CustomDeadLetterQueue</span></span>  

 <span data-ttu-id="1a0d9-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1a0d9-110">Data type: string</span></span>  
  
 <span data-ttu-id="1a0d9-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-112">Bu, zaman aşımına uğradı veya başarısız aktarım ya da teslimi olan iletilerin yerleştirildiği her uygulama için atılacak ileti sırasının konumunu içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="1a0d9-113">Özelliğinde</span><span class="sxs-lookup"><span data-stu-id="1a0d9-113">DeadLetterQueue</span></span>  

 <span data-ttu-id="1a0d9-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1a0d9-114">Data type: string</span></span>  
  
 <span data-ttu-id="1a0d9-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-116">Kullanılacak atılacak ileti sırasının türünü gösteren bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="1a0d9-117">Dayanıklı</span><span class="sxs-lookup"><span data-stu-id="1a0d9-117">Durable</span></span>  

 <span data-ttu-id="1a0d9-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1a0d9-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1a0d9-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-120">Bu bağlama tarafından işlenen iletilerin dayanıklı veya geçici olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="1a0d9-121">ExactlyOnce</span><span class="sxs-lookup"><span data-stu-id="1a0d9-121">ExactlyOnce</span></span>  

 <span data-ttu-id="1a0d9-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1a0d9-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1a0d9-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-124">Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp alınmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="1a0d9-125">Maxretrydöngüleri</span><span class="sxs-lookup"><span data-stu-id="1a0d9-125">MaxRetryCycles</span></span>  

 <span data-ttu-id="1a0d9-126">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="1a0d9-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="1a0d9-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-128">İleti alma uygulamasına iletileri teslim girişiminde bulunan en fazla yeniden deneme döngüsü sayısı.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="1a0d9-129">ReceiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="1a0d9-129">ReceiveErrorHandling</span></span>  

 <span data-ttu-id="1a0d9-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1a0d9-130">Data type: string</span></span>  
  
 <span data-ttu-id="1a0d9-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-132">Zarar iletisi işleme ayarları.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="1a0d9-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="1a0d9-133">ReceiveRetryCount</span></span>  

 <span data-ttu-id="1a0d9-134">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="1a0d9-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="1a0d9-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-136">Uygulama sırasından okunan bir ileti üzerinde anında yeniden deneme girişimlerinin en fazla sayısı.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="1a0d9-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="1a0d9-137">RetryCycleDelay</span></span>  

 <span data-ttu-id="1a0d9-138">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="1a0d9-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="1a0d9-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-140">Anında teslim edilmemiş bir iletiyi teslim etmeye çalışırken deneme döngüleri arasındaki gecikme süresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="1a0d9-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="1a0d9-141">TimeToLive</span></span>  

 <span data-ttu-id="1a0d9-142">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="1a0d9-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="1a0d9-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-144">Bu bağlama tarafından işlenen iletilerin, süresi dolmadan önce kuyrukta ne kadar süre içinde kalabileceğini belirten zaman aralığı.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="1a0d9-145">UseMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="1a0d9-145">UseMsmqTracing</span></span>  

 <span data-ttu-id="1a0d9-146">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1a0d9-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="1a0d9-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-148">Bu bağlama tarafından işlenen iletilerin izlenip izlenmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="1a0d9-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="1a0d9-149">UseSourceJournal</span></span>  

 <span data-ttu-id="1a0d9-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1a0d9-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="1a0d9-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1a0d9-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1a0d9-152">Bu bağlama tarafından işlenen iletilerin kopyalarının kaynak günlük kuyruğunda depolanması gerekip gerekmediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0d9-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a0d9-153">Requirements</span></span>  
  
|<span data-ttu-id="1a0d9-154">MOF</span><span class="sxs-lookup"><span data-stu-id="1a0d9-154">MOF</span></span>|<span data-ttu-id="1a0d9-155">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1a0d9-156">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1a0d9-156">Namespace</span></span>|<span data-ttu-id="1a0d9-157">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="1a0d9-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a0d9-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a0d9-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
