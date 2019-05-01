---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964261"
---
# <a name="appdomaininfo"></a><span data-ttu-id="9e095-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="9e095-102">AppDomainInfo</span></span>
<span data-ttu-id="9e095-103">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="9e095-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e095-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e095-104">Syntax</span></span>  
  
```csharp
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9e095-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9e095-105">Methods</span></span>  
 <span data-ttu-id="9e095-106">AppDomainInfo sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9e095-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9e095-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9e095-107">Properties</span></span>  
 <span data-ttu-id="9e095-108">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9e095-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="9e095-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="9e095-109">AppDomainId</span></span>  
 <span data-ttu-id="9e095-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9e095-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="9e095-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-112">Uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="9e095-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="9e095-113">Dil paketinde IsDefault</span><span class="sxs-lookup"><span data-stu-id="9e095-113">IsDefault</span></span>  
 <span data-ttu-id="9e095-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9e095-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e095-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-116">Appdomain varsayılan uygulama etki alanı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e095-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="9e095-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="9e095-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="9e095-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9e095-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e095-119">Erişim türü: Okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="9e095-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="9e095-120">Hatalı biçimlendirilmiş iletilerin kaydedilip kaydedilmeyeceğini belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="9e095-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="9e095-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="9e095-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="9e095-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9e095-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e095-123">Erişim türü: Okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="9e095-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="9e095-124">İletilerin hizmet düzeyinde (önce şifreleme ve taşıma ilişkili dönüşümler) izlenilmeyeceğini belirleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="9e095-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="9e095-125">Transfer</span><span class="sxs-lookup"><span data-stu-id="9e095-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="9e095-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9e095-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e095-127">Erişim türü: Okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="9e095-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="9e095-128">İletileri taşıma düzeyinde izlenip izlenilmeyeceğini belirleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="9e095-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="9e095-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="9e095-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="9e095-130">Veri türü: TraceListener dizi</span><span class="sxs-lookup"><span data-stu-id="9e095-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="9e095-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-132">Dinleme System.Wmi.MessageLogging izleme kaynağına izleme dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9e095-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9e095-133">Ad</span><span class="sxs-lookup"><span data-stu-id="9e095-133">Name</span></span>  
 <span data-ttu-id="9e095-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9e095-134">Data type: string</span></span>  
  
 <span data-ttu-id="9e095-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-136">Uygulama etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="9e095-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="9e095-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="9e095-137">PerformanceCounters</span></span>  
 <span data-ttu-id="9e095-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9e095-138">Data type: string</span></span>  
  
 <span data-ttu-id="9e095-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-140">Appdomain içinde etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="9e095-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="9e095-141">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="9e095-141">ProcessId</span></span>  
 <span data-ttu-id="9e095-142">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9e095-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="9e095-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-144">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="9e095-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="9e095-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="9e095-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="9e095-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9e095-146">Data type: string</span></span>  
  
 <span data-ttu-id="9e095-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-148">Hizmeti yapılandırma yolu.</span><span class="sxs-lookup"><span data-stu-id="9e095-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="9e095-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="9e095-149">TraceLevel</span></span>  
 <span data-ttu-id="9e095-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9e095-150">Data type: string</span></span>  
  
 <span data-ttu-id="9e095-151">Erişim türü: Okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="9e095-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="9e095-152">System.Wmi izleme kaynağına izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="9e095-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="9e095-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="9e095-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="9e095-154">Veri türü: TraceListener dizi</span><span class="sxs-lookup"><span data-stu-id="9e095-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="9e095-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9e095-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e095-156">System.ServiceModel kaynağına ait izleme dinleyicileri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="9e095-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e095-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e095-157">Requirements</span></span>  
  
|<span data-ttu-id="9e095-158">MOF</span><span class="sxs-lookup"><span data-stu-id="9e095-158">MOF</span></span>|<span data-ttu-id="9e095-159">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9e095-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9e095-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9e095-160">Namespace</span></span>|<span data-ttu-id="9e095-161">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9e095-161">Defined in root\ServiceModel</span></span>|
