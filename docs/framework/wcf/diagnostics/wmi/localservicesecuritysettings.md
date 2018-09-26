---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
ms.openlocfilehash: c79eb11fcc1973a3ef25a78afb8b141443d865c3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47156954"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="f0629-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f0629-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="f0629-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="f0629-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0629-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0629-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="f0629-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0629-105">Methods</span></span>  
 <span data-ttu-id="f0629-106">LocalServiceSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f0629-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f0629-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f0629-107">Properties</span></span>  
 <span data-ttu-id="f0629-108">LocalServiceSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f0629-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="f0629-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="f0629-109">DetectReplays</span></span>  
 <span data-ttu-id="f0629-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f0629-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0629-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-112">Kanal yeniden yürütme saldırıları algılandı ve otomatik olarak ele belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0629-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="f0629-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="f0629-113">InactivityTimeout</span></span>  
 <span data-ttu-id="f0629-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-116">Hizmetin desteklediği güvenlik oturumu bekleyen maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0629-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="f0629-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="f0629-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="f0629-118">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-120">Tüm yeni güvenlik tanımlama bilgilerine verilen ömür süresini belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="f0629-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="f0629-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="f0629-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="f0629-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f0629-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0629-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-124">Önbelleğe alınabilecek tanımlama bilgileri maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0629-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="f0629-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="f0629-125">MaxClockSkew</span></span>  
 <span data-ttu-id="f0629-126">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-128">İki iletişim kuran tarafların sistem saatleri arasındaki en uzun süre farkını belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="f0629-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="f0629-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="f0629-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="f0629-130">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f0629-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0629-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-132">Bekleyen hizmet bağlantıları maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0629-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="f0629-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="f0629-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="f0629-134">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f0629-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0629-135">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-136">Aynı anda etkin olabilen güvenlik anlaşmaları sayısını.</span><span class="sxs-lookup"><span data-stu-id="f0629-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="f0629-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="f0629-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="f0629-138">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-139">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-140">Sunucu ve istemci arasındaki güvenlik anlaşması aşaması için süre üst sınırını belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="f0629-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="f0629-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="f0629-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="f0629-142">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f0629-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0629-143">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-144">WS-Reliable Mesajlaşma kullanan bağlantı aktarım hatasından sonra yeniden bağlanmaya olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0629-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="f0629-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="f0629-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="f0629-146">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f0629-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0629-147">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-148">Yeniden yürütme algılaması için önbelleğe alınan nonce sayısını.</span><span class="sxs-lookup"><span data-stu-id="f0629-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="f0629-149">ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="f0629-149">ReplayWindow</span></span>  
 <span data-ttu-id="f0629-150">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-151">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-152">Tek tek ileti nonce öğelerinin geçerli kalacağı süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="f0629-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="f0629-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="f0629-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="f0629-154">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-155">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-156">Sonra ve Başlatıcı anahtarı için güvenlik oturumu yeniler süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="f0629-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="f0629-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="f0629-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="f0629-158">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-159">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-160">Zaman aralığını belirten bir TimeSpan anahtar yenilemesi sırasında önceki oturum anahtarının gelen iletileri geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="f0629-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="f0629-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="f0629-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="f0629-162">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="f0629-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="f0629-163">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0629-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0629-164">Zaman damgası geçerli olduğu süreyi belirten bir TimeSpan.</span><span class="sxs-lookup"><span data-stu-id="f0629-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0629-165">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0629-165">Requirements</span></span>  
  
|<span data-ttu-id="f0629-166">MOF</span><span class="sxs-lookup"><span data-stu-id="f0629-166">MOF</span></span>|<span data-ttu-id="f0629-167">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f0629-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f0629-168">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f0629-168">Namespace</span></span>|<span data-ttu-id="f0629-169">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f0629-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0629-170">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0629-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
