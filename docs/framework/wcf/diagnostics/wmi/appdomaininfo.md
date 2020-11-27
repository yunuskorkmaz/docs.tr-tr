---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: c5c44f4d8f6d93443802d5e1950c4d850976c5b6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291134"
---
# <a name="appdomaininfo"></a><span data-ttu-id="f18eb-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="f18eb-102">AppDomainInfo</span></span>

<span data-ttu-id="f18eb-103">Uygulama etki alanı bilgileri</span><span class="sxs-lookup"><span data-stu-id="f18eb-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18eb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f18eb-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f18eb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f18eb-105">Methods</span></span>  

 <span data-ttu-id="f18eb-106">AppDomainInfo sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f18eb-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f18eb-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f18eb-107">Properties</span></span>  

 <span data-ttu-id="f18eb-108">AppDomainInfo sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f18eb-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="f18eb-109">AppDomainID</span><span class="sxs-lookup"><span data-stu-id="f18eb-109">AppDomainId</span></span>  

 <span data-ttu-id="f18eb-110">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f18eb-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f18eb-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-112">AppDomain kimliği.</span><span class="sxs-lookup"><span data-stu-id="f18eb-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="f18eb-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="f18eb-113">IsDefault</span></span>  

 <span data-ttu-id="f18eb-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f18eb-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f18eb-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-116">AppDomain 'in varsayılan AppDomain olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f18eb-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="f18eb-117">Günlüğe kaydetme Iletileri</span><span class="sxs-lookup"><span data-stu-id="f18eb-117">LogMalformedMessages</span></span>  

 <span data-ttu-id="f18eb-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f18eb-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f18eb-119">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f18eb-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f18eb-120">Hatalı biçimlendirilmiş iletilerin günlüğe kaydedilip kaydedilmeyeceğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f18eb-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="f18eb-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="f18eb-121">LogMessagesAtServiceLevel</span></span>  

 <span data-ttu-id="f18eb-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f18eb-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f18eb-123">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f18eb-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f18eb-124">İletilerin hizmet düzeyinde izlenip izlenmeyeceğini belirten bir değer (şifreleme ve aktarımlarla ilgili dönüşümlerden önce).</span><span class="sxs-lookup"><span data-stu-id="f18eb-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="f18eb-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="f18eb-125">LogMessagesAtTransportLevel</span></span>  

 <span data-ttu-id="f18eb-126">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f18eb-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="f18eb-127">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f18eb-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f18eb-128">İletilerin Aktarım düzeyinde izlenip izlenmediğini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="f18eb-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="f18eb-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="f18eb-129">MessageLoggingTraceListeners</span></span>  

 <span data-ttu-id="f18eb-130">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="f18eb-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="f18eb-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-132">System. WMI. MessageLogging izleme kaynağını dinleyen koleksiyon izleme dinleyicileri.</span><span class="sxs-lookup"><span data-stu-id="f18eb-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f18eb-133">Adı</span><span class="sxs-lookup"><span data-stu-id="f18eb-133">Name</span></span>  

 <span data-ttu-id="f18eb-134">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f18eb-134">Data type: string</span></span>  
  
 <span data-ttu-id="f18eb-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-136">AppDomain 'in adı.</span><span class="sxs-lookup"><span data-stu-id="f18eb-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="f18eb-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="f18eb-137">PerformanceCounters</span></span>  

 <span data-ttu-id="f18eb-138">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f18eb-138">Data type: string</span></span>  
  
 <span data-ttu-id="f18eb-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-140">AppDomain içindeki etkin performans sayaçlarının kapsamı.</span><span class="sxs-lookup"><span data-stu-id="f18eb-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="f18eb-141">Işlem</span><span class="sxs-lookup"><span data-stu-id="f18eb-141">ProcessId</span></span>  

 <span data-ttu-id="f18eb-142">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f18eb-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="f18eb-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-144">İşlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="f18eb-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="f18eb-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="f18eb-145">ServiceConfigPath</span></span>  

 <span data-ttu-id="f18eb-146">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f18eb-146">Data type: string</span></span>  
  
 <span data-ttu-id="f18eb-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-148">Hizmetin yapılandırmasının yolu.</span><span class="sxs-lookup"><span data-stu-id="f18eb-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="f18eb-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="f18eb-149">TraceLevel</span></span>  

 <span data-ttu-id="f18eb-150">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f18eb-150">Data type: string</span></span>  
  
 <span data-ttu-id="f18eb-151">Erişim türü: okuma/yazma</span><span class="sxs-lookup"><span data-stu-id="f18eb-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="f18eb-152">System. WMI izleme kaynağının izleme düzeyi.</span><span class="sxs-lookup"><span data-stu-id="f18eb-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="f18eb-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="f18eb-153">ServiceModelTraceListeners</span></span>  

 <span data-ttu-id="f18eb-154">Veri türü: TraceListener dizisi</span><span class="sxs-lookup"><span data-stu-id="f18eb-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="f18eb-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f18eb-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f18eb-156">System. ServiceModel izleme kaynağından gelen bir dinleyici koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f18eb-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f18eb-157">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f18eb-157">Requirements</span></span>  
  
|<span data-ttu-id="f18eb-158">MOF</span><span class="sxs-lookup"><span data-stu-id="f18eb-158">MOF</span></span>|<span data-ttu-id="f18eb-159">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f18eb-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f18eb-160">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f18eb-160">Namespace</span></span>|<span data-ttu-id="f18eb-161">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="f18eb-161">Defined in root\ServiceModel</span></span>|
