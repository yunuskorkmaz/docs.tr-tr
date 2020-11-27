---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: eecf2b0bf459fd14236c550e393149553183b3ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267929"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="08a60-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="08a60-102">LocalServiceSecuritySettings</span></span>

<span data-ttu-id="08a60-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="08a60-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08a60-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="08a60-104">Syntax</span></span>  
  
```csharp
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="08a60-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="08a60-105">Methods</span></span>  

 <span data-ttu-id="08a60-106">LocalServiceSecuritySettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="08a60-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="08a60-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="08a60-107">Properties</span></span>  

 <span data-ttu-id="08a60-108">LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="08a60-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="08a60-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="08a60-109">DetectReplays</span></span>  

 <span data-ttu-id="08a60-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="08a60-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="08a60-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-112">Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="08a60-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="08a60-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="08a60-113">InactivityTimeout</span></span>  

 <span data-ttu-id="08a60-114">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-116">Hizmetin desteklediği en fazla beklemedeki güvenlik oturumu sayısı.</span><span class="sxs-lookup"><span data-stu-id="08a60-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="08a60-117">Issuedtarif ıelifetime</span><span class="sxs-lookup"><span data-stu-id="08a60-117">IssuedCookieLifetime</span></span>  

 <span data-ttu-id="08a60-118">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-120">Tüm yeni güvenlik tanımlama bilgilerine verilen yaşam süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="08a60-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="08a60-121">MaxCachedCookies</span></span>  

 <span data-ttu-id="08a60-122">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="08a60-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="08a60-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-124">Önbelleğe alınabilecek tanımlama bilgisi sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="08a60-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="08a60-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="08a60-125">MaxClockSkew</span></span>  

 <span data-ttu-id="08a60-126">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-128">İki iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="08a60-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="08a60-129">MaxPendingSessions</span></span>  

 <span data-ttu-id="08a60-130">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="08a60-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="08a60-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-132">Hizmette bekleyen en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="08a60-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="08a60-133">Maxstatefulanlaşmaları</span><span class="sxs-lookup"><span data-stu-id="08a60-133">MaxStatefulNegotiations</span></span>  

 <span data-ttu-id="08a60-134">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="08a60-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="08a60-135">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-136">Aynı anda etkin olabilen güvenlik anlaşmaları sayısı.</span><span class="sxs-lookup"><span data-stu-id="08a60-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="08a60-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="08a60-137">NegotiationTimeout</span></span>  

 <span data-ttu-id="08a60-138">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-139">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-140">Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için en uzun süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="08a60-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="08a60-141">ReconnectTransportOnFailure</span></span>  

 <span data-ttu-id="08a60-142">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="08a60-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="08a60-143">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-144">WS-Reliable mesajlaşma kullanan bağlantıların aktarım arızasından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="08a60-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="08a60-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="08a60-145">ReplayCacheSize</span></span>  

 <span data-ttu-id="08a60-146">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="08a60-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="08a60-147">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-148">Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısı.</span><span class="sxs-lookup"><span data-stu-id="08a60-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="08a60-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="08a60-149">ReplayWindow</span></span>  

 <span data-ttu-id="08a60-150">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-151">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-152">Tek tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="08a60-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="08a60-153">SessionKeyRenewalInterval</span></span>  

 <span data-ttu-id="08a60-154">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-155">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-156">Başlatanın güvenlik oturumu için anahtarı yenileme süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="08a60-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="08a60-157">SessionKeyRolloverInterval</span></span>  

 <span data-ttu-id="08a60-158">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-159">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-160">Anahtar yenileme sırasında gelen iletilerde önceki oturum anahtarının geçerli olduğu zaman aralığını belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="08a60-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="08a60-161">TimestampValidityDuration</span></span>  

 <span data-ttu-id="08a60-162">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="08a60-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="08a60-163">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="08a60-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="08a60-164">Zaman damgasının geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="08a60-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08a60-165">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08a60-165">Requirements</span></span>  
  
|<span data-ttu-id="08a60-166">MOF</span><span class="sxs-lookup"><span data-stu-id="08a60-166">MOF</span></span>|<span data-ttu-id="08a60-167">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="08a60-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="08a60-168">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="08a60-168">Namespace</span></span>|<span data-ttu-id="08a60-169">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="08a60-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="08a60-170">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08a60-170">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
