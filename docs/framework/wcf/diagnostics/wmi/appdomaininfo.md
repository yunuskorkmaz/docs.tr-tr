---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50170230"
---
# <a name="appdomaininfo"></a><span data-ttu-id="1b718-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="1b718-102">AppDomainInfo</span></span>
<span data-ttu-id="1b718-103">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="1b718-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b718-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b718-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1b718-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b718-105">Methods</span></span>  
 <span data-ttu-id="1b718-106">AppDomainInfo sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1b718-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1b718-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1b718-107">Properties</span></span>  
 <span data-ttu-id="1b718-108">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1b718-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="1b718-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="1b718-109">AppDomainId</span></span>  
 <span data-ttu-id="1b718-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="1b718-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="1b718-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-112">Uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b718-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="1b718-113">Dil paketinde IsDefault</span><span class="sxs-lookup"><span data-stu-id="1b718-113">IsDefault</span></span>  
 <span data-ttu-id="1b718-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1b718-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="1b718-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-116">Appdomain varsayılan uygulama etki alanı olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b718-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="1b718-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="1b718-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="1b718-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1b718-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1b718-119">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="1b718-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="1b718-120">Hatalı biçimlendirilmiş iletilerin kaydedilip kaydedilmeyeceğini belirten bir değeri.</span><span class="sxs-lookup"><span data-stu-id="1b718-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="1b718-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="1b718-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="1b718-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1b718-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1b718-123">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="1b718-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="1b718-124">İletilerin hizmet düzeyinde (önce şifreleme ve taşıma ilişkili dönüşümler) izlenilmeyeceğini belirleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="1b718-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="1b718-125">Transfer</span><span class="sxs-lookup"><span data-stu-id="1b718-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="1b718-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="1b718-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="1b718-127">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="1b718-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="1b718-128">İletileri taşıma düzeyinde izlenip izlenilmeyeceğini belirleyen bir değer.</span><span class="sxs-lookup"><span data-stu-id="1b718-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="1b718-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="1b718-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="1b718-130">Veri türü: TraceListener dizi</span><span class="sxs-lookup"><span data-stu-id="1b718-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="1b718-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-132">Dinleme System.Wmi.MessageLogging izleme kaynağına izleme dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1b718-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="1b718-133">Ad</span><span class="sxs-lookup"><span data-stu-id="1b718-133">Name</span></span>  
 <span data-ttu-id="1b718-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1b718-134">Data type: string</span></span>  
  
 <span data-ttu-id="1b718-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-136">Uygulama etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="1b718-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="1b718-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="1b718-137">PerformanceCounters</span></span>  
 <span data-ttu-id="1b718-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1b718-138">Data type: string</span></span>  
  
 <span data-ttu-id="1b718-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-140">Appdomain içinde etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="1b718-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="1b718-141">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="1b718-141">ProcessId</span></span>  
 <span data-ttu-id="1b718-142">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="1b718-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="1b718-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-144">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b718-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="1b718-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="1b718-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="1b718-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1b718-146">Data type: string</span></span>  
  
 <span data-ttu-id="1b718-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-148">Hizmeti yapılandırma yolu.</span><span class="sxs-lookup"><span data-stu-id="1b718-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="1b718-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="1b718-149">TraceLevel</span></span>  
 <span data-ttu-id="1b718-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1b718-150">Data type: string</span></span>  
  
 <span data-ttu-id="1b718-151">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="1b718-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="1b718-152">System.Wmi izleme kaynağına izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="1b718-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="1b718-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="1b718-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="1b718-154">Veri türü: TraceListener dizi</span><span class="sxs-lookup"><span data-stu-id="1b718-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="1b718-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="1b718-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b718-156">System.ServiceModel kaynağına ait izleme dinleyicileri koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="1b718-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b718-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b718-157">Requirements</span></span>  
  
|<span data-ttu-id="1b718-158">MOF</span><span class="sxs-lookup"><span data-stu-id="1b718-158">MOF</span></span>|<span data-ttu-id="1b718-159">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1b718-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1b718-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1b718-160">Namespace</span></span>|<span data-ttu-id="1b718-161">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1b718-161">Defined in root\ServiceModel</span></span>|
