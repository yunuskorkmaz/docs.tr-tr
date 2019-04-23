---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: 1df4b32feda246a536183a42ac11b113bc4bb259
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768403"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="cd7a9-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="cd7a9-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="cd7a9-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="cd7a9-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd7a9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd7a9-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="cd7a9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cd7a9-105">Methods</span></span>  
 <span data-ttu-id="cd7a9-106">MsmqBindingElementBase sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cd7a9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cd7a9-107">Properties</span></span>  
 <span data-ttu-id="cd7a9-108">MsmqBindingElementBase sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cd7a9-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="cd7a9-109">customDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="cd7a9-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="cd7a9-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cd7a9-110">Data type: string</span></span>  
  
 <span data-ttu-id="cd7a9-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-112">Aktarım veya teslim başarısız olan veya süresi dolmuş olan iletileri yerleştirildiği her uygulama için geçerliliğini yitirmiş kuyruk konumunu içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="cd7a9-113">deadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="cd7a9-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="cd7a9-114">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cd7a9-114">Data type: string</span></span>  
  
 <span data-ttu-id="cd7a9-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-116">Kullanılacak geçerliliğini yitirmiş kuyruk türü belirten bir numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="cd7a9-117">dayanıklı</span><span class="sxs-lookup"><span data-stu-id="cd7a9-117">Durable</span></span>  
 <span data-ttu-id="cd7a9-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="cd7a9-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd7a9-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-120">Bu bağlama tarafından işlenen iletilerin sürekli veya geçici olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="cd7a9-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="cd7a9-121">ExactlyOnce</span></span>  
 <span data-ttu-id="cd7a9-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="cd7a9-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd7a9-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-124">Bu bağlama tarafından işlenen iletilerin tam olarak bir kez alınıp olup olmadığını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="cd7a9-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="cd7a9-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="cd7a9-126">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cd7a9-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="cd7a9-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-128">Alıcı uygulamasına iletileri teslim girişiminde yeniden deneme döngüsü sayısı.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="cd7a9-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="cd7a9-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="cd7a9-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cd7a9-130">Data type: string</span></span>  
  
 <span data-ttu-id="cd7a9-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-132">Zehirli ileti işleme için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="cd7a9-133">receiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="cd7a9-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="cd7a9-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cd7a9-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="cd7a9-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-136">Hemen yeniden deneme sayısı, uygulama kuyruktan okuyan bir ileti üzerinde çalışır.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="cd7a9-137">retryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="cd7a9-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="cd7a9-138">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="cd7a9-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="cd7a9-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-140">Anında teslim edilemeyen bir iletiyi teslim etmeye çalışırken deneme arasındaki gecikmeyi belirten bir değer dolaşır.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="cd7a9-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="cd7a9-141">TimeToLive</span></span>  
 <span data-ttu-id="cd7a9-142">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="cd7a9-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="cd7a9-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-144">Süresi dolmadan önce bu bağlama tarafından işlenen iletilerin belirten zaman aralığını kuyrukta olabilir.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="cd7a9-145">useMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="cd7a9-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="cd7a9-146">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="cd7a9-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd7a9-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-148">İletileri bu bağlama tarafından işlenen olup olmadığını gösteren bir Boole değeri izlenip izlenmemesini gerektiğini.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="cd7a9-149">useSourceJournal</span><span class="sxs-lookup"><span data-stu-id="cd7a9-149">UseSourceJournal</span></span>  
 <span data-ttu-id="cd7a9-150">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="cd7a9-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd7a9-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cd7a9-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd7a9-152">Bu bağlama tarafından işlenen iletilerin kopyalarını kaynak günlük sırasındaki depolanıp depolanmayacağını gösteren bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd7a9-153">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd7a9-153">Requirements</span></span>  
  
|<span data-ttu-id="cd7a9-154">MOF</span><span class="sxs-lookup"><span data-stu-id="cd7a9-154">MOF</span></span>|<span data-ttu-id="cd7a9-155">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cd7a9-156">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cd7a9-156">Namespace</span></span>|<span data-ttu-id="cd7a9-157">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cd7a9-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd7a9-158">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd7a9-158">See also</span></span>

- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
