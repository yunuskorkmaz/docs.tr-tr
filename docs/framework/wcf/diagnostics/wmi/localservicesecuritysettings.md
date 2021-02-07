---
description: ': LocalServiceSecuritySettings hakkında daha fazla bilgi edinin'
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: f7220e8253c6ab218414c1be7ed90e5d593b4692
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743947"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="7918c-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="7918c-103">LocalServiceSecuritySettings</span></span>

<span data-ttu-id="7918c-104">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="7918c-104">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7918c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7918c-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7918c-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7918c-106">Methods</span></span>  

 <span data-ttu-id="7918c-107">LocalServiceSecuritySettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7918c-107">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7918c-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7918c-108">Properties</span></span>  

 <span data-ttu-id="7918c-109">LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7918c-109">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="7918c-110">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="7918c-110">DetectReplays</span></span>  

 <span data-ttu-id="7918c-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7918c-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="7918c-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-113">Kanala karşı yeniden yürütme saldırılarının algılanıp algılanmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7918c-113">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="7918c-114">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="7918c-114">InactivityTimeout</span></span>  

 <span data-ttu-id="7918c-115">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-117">Hizmetin desteklediği en fazla beklemedeki güvenlik oturumu sayısı.</span><span class="sxs-lookup"><span data-stu-id="7918c-117">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="7918c-118">Issuedtarif ıelifetime</span><span class="sxs-lookup"><span data-stu-id="7918c-118">IssuedCookieLifetime</span></span>  

 <span data-ttu-id="7918c-119">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-121">Tüm yeni güvenlik tanımlama bilgilerine verilen yaşam süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-121">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="7918c-122">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="7918c-122">MaxCachedCookies</span></span>  

 <span data-ttu-id="7918c-123">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="7918c-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="7918c-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-125">Önbelleğe alınabilecek tanımlama bilgisi sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="7918c-125">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="7918c-126">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="7918c-126">MaxClockSkew</span></span>  

 <span data-ttu-id="7918c-127">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-127">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-129">İki iletişim kuran tarafın sistem saatleri arasındaki en uzun süre farkını belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-129">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="7918c-130">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="7918c-130">MaxPendingSessions</span></span>  

 <span data-ttu-id="7918c-131">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="7918c-131">Data type: sint32</span></span>  
  
 <span data-ttu-id="7918c-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-133">Hizmette bekleyen en fazla bağlantı sayısı.</span><span class="sxs-lookup"><span data-stu-id="7918c-133">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="7918c-134">Maxstatefulanlaşmaları</span><span class="sxs-lookup"><span data-stu-id="7918c-134">MaxStatefulNegotiations</span></span>  

 <span data-ttu-id="7918c-135">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="7918c-135">Data type: sint32</span></span>  
  
 <span data-ttu-id="7918c-136">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-136">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-137">Aynı anda etkin olabilen güvenlik anlaşmaları sayısı.</span><span class="sxs-lookup"><span data-stu-id="7918c-137">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="7918c-138">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="7918c-138">NegotiationTimeout</span></span>  

 <span data-ttu-id="7918c-139">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-139">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-140">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-140">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-141">Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için en uzun süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-141">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="7918c-142">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="7918c-142">ReconnectTransportOnFailure</span></span>  

 <span data-ttu-id="7918c-143">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7918c-143">Data type: boolean</span></span>  
  
 <span data-ttu-id="7918c-144">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-144">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-145">WS-Reliable mesajlaşma kullanan bağlantıların aktarım arızasından sonra yeniden bağlanmaya çalışıp çalışmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="7918c-145">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="7918c-146">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="7918c-146">ReplayCacheSize</span></span>  

 <span data-ttu-id="7918c-147">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="7918c-147">Data type: sint32</span></span>  
  
 <span data-ttu-id="7918c-148">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-148">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-149">Yeniden yürütme algılaması için kullanılan önbelleğe alınmış nonce sayısı.</span><span class="sxs-lookup"><span data-stu-id="7918c-149">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="7918c-150">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="7918c-150">ReplayWindow</span></span>  

 <span data-ttu-id="7918c-151">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-151">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-152">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-152">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-153">Tek tek ileti nonce öğelerinin geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-153">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="7918c-154">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="7918c-154">SessionKeyRenewalInterval</span></span>  

 <span data-ttu-id="7918c-155">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-155">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-156">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-156">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-157">Başlatanın güvenlik oturumu için anahtarı yenileme süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-157">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="7918c-158">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="7918c-158">SessionKeyRolloverInterval</span></span>  

 <span data-ttu-id="7918c-159">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-159">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-160">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-160">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-161">Anahtar yenileme sırasında gelen iletilerde önceki oturum anahtarının geçerli olduğu zaman aralığını belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-161">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="7918c-162">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="7918c-162">TimestampValidityDuration</span></span>  

 <span data-ttu-id="7918c-163">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="7918c-163">Data type: datetime</span></span>  
  
 <span data-ttu-id="7918c-164">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7918c-164">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7918c-165">Zaman damgasının geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="7918c-165">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7918c-166">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7918c-166">Requirements</span></span>  
  
|<span data-ttu-id="7918c-167">MOF</span><span class="sxs-lookup"><span data-stu-id="7918c-167">MOF</span></span>|<span data-ttu-id="7918c-168">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7918c-168">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7918c-169">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7918c-169">Namespace</span></span>|<span data-ttu-id="7918c-170">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="7918c-170">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7918c-171">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7918c-171">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
