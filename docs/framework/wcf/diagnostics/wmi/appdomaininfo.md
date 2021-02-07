---
description: 'Daha fazla bilgi edinin: AppDomainInfo'
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 1e527f2a25c48a3bf35d974e3ac192d937a8a86e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757975"
---
# <a name="appdomaininfo"></a><span data-ttu-id="ef94d-103">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="ef94d-103">AppDomainInfo</span></span>

<span data-ttu-id="ef94d-104">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="ef94d-104">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef94d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef94d-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ef94d-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ef94d-106">Methods</span></span>  

 <span data-ttu-id="ef94d-107">AppDomainInfo sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ef94d-107">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef94d-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ef94d-108">Properties</span></span>  

 <span data-ttu-id="ef94d-109">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ef94d-109">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="ef94d-110">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="ef94d-110">AppDomainId</span></span>  

 <span data-ttu-id="ef94d-111">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="ef94d-111">Data type: sint32</span></span>  
  
 <span data-ttu-id="ef94d-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-113">AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="ef94d-113">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="ef94d-114">IsDefault</span><span class="sxs-lookup"><span data-stu-id="ef94d-114">IsDefault</span></span>  

 <span data-ttu-id="ef94d-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef94d-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef94d-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-117">AppDomain 'in varsayılan AppDomain olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef94d-117">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="ef94d-118">Günlüğe kaydetme Iletileri</span><span class="sxs-lookup"><span data-stu-id="ef94d-118">LogMalformedMessages</span></span>  

 <span data-ttu-id="ef94d-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef94d-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef94d-120">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ef94d-120">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ef94d-121">Hatalı biçimlendirilmiş iletilerin günlüğe kaydedilip kaydedilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ef94d-121">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="ef94d-122">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="ef94d-122">LogMessagesAtServiceLevel</span></span>  

 <span data-ttu-id="ef94d-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef94d-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef94d-124">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ef94d-124">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ef94d-125">İletilerin hizmet düzeyinde izlenip izlenmeyeceğini belirten bir değer (şifreleme ve aktarımlarla ilgili dönüşümlerden önce).</span><span class="sxs-lookup"><span data-stu-id="ef94d-125">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="ef94d-126">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="ef94d-126">LogMessagesAtTransportLevel</span></span>  

 <span data-ttu-id="ef94d-127">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef94d-127">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef94d-128">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ef94d-128">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ef94d-129">İletilerin Aktarım düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="ef94d-129">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="ef94d-130">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="ef94d-130">MessageLoggingTraceListeners</span></span>  

 <span data-ttu-id="ef94d-131">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="ef94d-131">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="ef94d-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-133">System. WMI. MessageLogging izleme kaynağını dinleyen koleksiyon izleme dinleyicileri.</span><span class="sxs-lookup"><span data-stu-id="ef94d-133">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ef94d-134">Name</span><span class="sxs-lookup"><span data-stu-id="ef94d-134">Name</span></span>  

 <span data-ttu-id="ef94d-135">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef94d-135">Data type: string</span></span>  
  
 <span data-ttu-id="ef94d-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-137">AppDomain 'in adı.</span><span class="sxs-lookup"><span data-stu-id="ef94d-137">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="ef94d-138">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="ef94d-138">PerformanceCounters</span></span>  

 <span data-ttu-id="ef94d-139">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef94d-139">Data type: string</span></span>  
  
 <span data-ttu-id="ef94d-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-141">AppDomain içindeki etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="ef94d-141">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="ef94d-142">Işlem</span><span class="sxs-lookup"><span data-stu-id="ef94d-142">ProcessId</span></span>  

 <span data-ttu-id="ef94d-143">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="ef94d-143">Data type: sint32</span></span>  
  
 <span data-ttu-id="ef94d-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-145">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="ef94d-145">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="ef94d-146">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="ef94d-146">ServiceConfigPath</span></span>  

 <span data-ttu-id="ef94d-147">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef94d-147">Data type: string</span></span>  
  
 <span data-ttu-id="ef94d-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-149">Hizmetin yapılandırmasının yolu.</span><span class="sxs-lookup"><span data-stu-id="ef94d-149">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="ef94d-150">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="ef94d-150">TraceLevel</span></span>  

 <span data-ttu-id="ef94d-151">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef94d-151">Data type: string</span></span>  
  
 <span data-ttu-id="ef94d-152">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="ef94d-152">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="ef94d-153">System. WMI izleme kaynağının izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="ef94d-153">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="ef94d-154">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="ef94d-154">ServiceModelTraceListeners</span></span>  

 <span data-ttu-id="ef94d-155">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="ef94d-155">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="ef94d-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef94d-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef94d-157">System. ServiceModel izleme kaynağından gelen bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ef94d-157">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef94d-158">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef94d-158">Requirements</span></span>  
  
|<span data-ttu-id="ef94d-159">MOF</span><span class="sxs-lookup"><span data-stu-id="ef94d-159">MOF</span></span>|<span data-ttu-id="ef94d-160">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef94d-160">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef94d-161">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ef94d-161">Namespace</span></span>|<span data-ttu-id="ef94d-162">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="ef94d-162">Defined in root\ServiceModel</span></span>|
