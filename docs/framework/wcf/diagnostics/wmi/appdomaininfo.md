---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="09fdb-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="09fdb-102">AppDomainInfo</span></span>
<span data-ttu-id="09fdb-103">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="09fdb-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09fdb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="09fdb-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="09fdb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="09fdb-105">Methods</span></span>  
 <span data-ttu-id="09fdb-106">AppDomainInfo sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="09fdb-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="09fdb-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="09fdb-107">Properties</span></span>  
 <span data-ttu-id="09fdb-108">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="09fdb-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="09fdb-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="09fdb-109">AppDomainId</span></span>  
 <span data-ttu-id="09fdb-110">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="09fdb-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="09fdb-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-112">Appdomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="09fdb-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="09fdb-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="09fdb-113">IsDefault</span></span>  
 <span data-ttu-id="09fdb-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="09fdb-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="09fdb-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-116">Appdomain varsayılan appdomain olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="09fdb-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="09fdb-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="09fdb-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="09fdb-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="09fdb-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="09fdb-119">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="09fdb-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="09fdb-120">Hatalı biçimlendirilmiş iletileri günlüğe olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="09fdb-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="09fdb-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="09fdb-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="09fdb-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="09fdb-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="09fdb-123">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="09fdb-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="09fdb-124">İletiler (şifreleme ve taşımayla ilgili Dönüşümlerde önce) hizmet düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="09fdb-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="09fdb-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="09fdb-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="09fdb-126">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="09fdb-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="09fdb-127">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="09fdb-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="09fdb-128">İletileri aktarım düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="09fdb-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="09fdb-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="09fdb-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="09fdb-130">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="09fdb-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="09fdb-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-132">System.Wmi.MessageLogging izleme kaynağını dinleyen izleme dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="09fdb-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="09fdb-133">Ad</span><span class="sxs-lookup"><span data-stu-id="09fdb-133">Name</span></span>  
 <span data-ttu-id="09fdb-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09fdb-134">Data type: string</span></span>  
  
 <span data-ttu-id="09fdb-135">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-136">Uygulama etki alanı adı.</span><span class="sxs-lookup"><span data-stu-id="09fdb-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="09fdb-137">performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="09fdb-137">PerformanceCounters</span></span>  
 <span data-ttu-id="09fdb-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09fdb-138">Data type: string</span></span>  
  
 <span data-ttu-id="09fdb-139">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-140">Appdomain'deki etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="09fdb-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="09fdb-141">İşlem kimliği</span><span class="sxs-lookup"><span data-stu-id="09fdb-141">ProcessId</span></span>  
 <span data-ttu-id="09fdb-142">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="09fdb-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="09fdb-143">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-144">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="09fdb-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="09fdb-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="09fdb-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="09fdb-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09fdb-146">Data type: string</span></span>  
  
 <span data-ttu-id="09fdb-147">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-148">Hizmet yapılandırma yolu.</span><span class="sxs-lookup"><span data-stu-id="09fdb-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="09fdb-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="09fdb-149">TraceLevel</span></span>  
 <span data-ttu-id="09fdb-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="09fdb-150">Data type: string</span></span>  
  
 <span data-ttu-id="09fdb-151">Erişim türüne: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="09fdb-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="09fdb-152">System.Wmi izleme kaynağına izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="09fdb-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="09fdb-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="09fdb-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="09fdb-154">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="09fdb-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="09fdb-155">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="09fdb-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="09fdb-156">System.ServiceModel izleme kaynağından dinleyicileri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="09fdb-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09fdb-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09fdb-157">Requirements</span></span>  
  
|<span data-ttu-id="09fdb-158">MOF</span><span class="sxs-lookup"><span data-stu-id="09fdb-158">MOF</span></span>|<span data-ttu-id="09fdb-159">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="09fdb-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="09fdb-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="09fdb-160">Namespace</span></span>|<span data-ttu-id="09fdb-161">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="09fdb-161">Defined in root\ServiceModel</span></span>|
