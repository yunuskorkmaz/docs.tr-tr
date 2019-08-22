---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caec297f8d0f6febad5cf46adb0a2658960c6bb1
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663668"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="d91cc-102">\<generatePublisherEvidence > öğesi</span><span class="sxs-lookup"><span data-stu-id="d91cc-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="d91cc-103">Çalışma zamanının kod erişim güvenliği <xref:System.Security.Policy.Publisher> (CAS) için kanıt oluşturup oluşturmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d91cc-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="d91cc-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d91cc-104">\<configuration></span></span>  
<span data-ttu-id="d91cc-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d91cc-105">\<runtime></span></span>  
<span data-ttu-id="d91cc-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="d91cc-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d91cc-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d91cc-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d91cc-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d91cc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d91cc-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d91cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d91cc-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d91cc-110">Attributes</span></span>  
  
|<span data-ttu-id="d91cc-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d91cc-111">Attribute</span></span>|<span data-ttu-id="d91cc-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d91cc-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d91cc-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d91cc-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d91cc-114">Çalışma zamanının kanıt oluşturup oluşturmadığını <xref:System.Security.Policy.Publisher> belirtir.</span><span class="sxs-lookup"><span data-stu-id="d91cc-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d91cc-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d91cc-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="d91cc-116">Değer</span><span class="sxs-lookup"><span data-stu-id="d91cc-116">Value</span></span>|<span data-ttu-id="d91cc-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d91cc-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="d91cc-118">Kanıt oluşturmaz <xref:System.Security.Policy.Publisher> .</span><span class="sxs-lookup"><span data-stu-id="d91cc-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="d91cc-119">Kanıt <xref:System.Security.Policy.Publisher> oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d91cc-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="d91cc-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d91cc-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d91cc-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d91cc-121">Child Elements</span></span>  
 <span data-ttu-id="d91cc-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="d91cc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d91cc-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d91cc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d91cc-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="d91cc-124">Element</span></span>|<span data-ttu-id="d91cc-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d91cc-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d91cc-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d91cc-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d91cc-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d91cc-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d91cc-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d91cc-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d91cc-129">.NET Framework 4 ve sonrasında, bu öğenin derleme yükleme süreleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d91cc-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="d91cc-130">Daha fazla bilgi için [güvenlik değişikliklerinin](../../../security/security-changes.md)"güvenlik ilkesi basitleştirmesi" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d91cc-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../security/security-changes.md).</span></span>  
  
 <span data-ttu-id="d91cc-131">Ortak dil çalışma zamanı (CLR), derleme için kanıt oluşturmak <xref:System.Security.Policy.Publisher> üzere yükleme zamanında Authenticode imzasını doğrulamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="d91cc-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="d91cc-132">Ancak, varsayılan olarak çoğu uygulama <xref:System.Security.Policy.Publisher> kanıt gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="d91cc-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="d91cc-133">Standart CAS ilkesi öğesine bağlı değildir <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="d91cc-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="d91cc-134">Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütülmediği veya kısmi güven ortamındaki taleplerini <xref:System.Security.Permissions.PublisherIdentityPermission> karşılamak üzere bir sorun olduğu müddetçe, yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyetinden kaçının.</span><span class="sxs-lookup"><span data-stu-id="d91cc-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="d91cc-135">(Kimlik izinlerinin istekleri her zaman tam güven ortamında başarılı olur.)</span><span class="sxs-lookup"><span data-stu-id="d91cc-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d91cc-136">Hizmetin, `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesini kullanmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="d91cc-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="d91cc-137">Bu öğenin kullanılması, zaman aşımına neden olabilecek ve hizmet başlangıcını iptal eden gecikmelerden kaçınmaya da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d91cc-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d91cc-138">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="d91cc-138">Configuration File</span></span>  
 <span data-ttu-id="d91cc-139">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d91cc-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d91cc-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="d91cc-140">Example</span></span>  
 <span data-ttu-id="d91cc-141">Aşağıdaki örnek, bir uygulama için CAS yayımcı `<generatePublisherEvidence>` ilkesi denetimini devre dışı bırakmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d91cc-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d91cc-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d91cc-142">See also</span></span>

- [<span data-ttu-id="d91cc-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d91cc-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d91cc-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d91cc-144">Configuration File Schema</span></span>](../index.md)
