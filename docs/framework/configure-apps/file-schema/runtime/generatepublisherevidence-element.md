---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 11592b055641c0fa2d2b968547dcc5aa40c94600
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541790"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="9ea1c-102">\<generatePublisherEvidence> Öğesi</span><span class="sxs-lookup"><span data-stu-id="9ea1c-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="9ea1c-103">Çalışma zamanının <xref:System.Security.Policy.Publisher> kod erişim güvenliği (CAS) için kanıt oluşturup oluşturmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="9ea1c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9ea1c-104">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ea1c-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ea1c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9ea1c-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ea1c-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ea1c-107">Attributes</span></span>  
  
|<span data-ttu-id="9ea1c-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ea1c-108">Attribute</span></span>|<span data-ttu-id="9ea1c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ea1c-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9ea1c-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="9ea1c-111">Çalışma zamanının kanıt oluşturup oluşturmadığını belirtir <xref:System.Security.Policy.Publisher> .</span><span class="sxs-lookup"><span data-stu-id="9ea1c-111">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9ea1c-112">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ea1c-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="9ea1c-113">Değer</span><span class="sxs-lookup"><span data-stu-id="9ea1c-113">Value</span></span>|<span data-ttu-id="9ea1c-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ea1c-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9ea1c-115"><xref:System.Security.Policy.Publisher>Kanıt oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-115">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="9ea1c-116"><xref:System.Security.Policy.Publisher>Kanıt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-116">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="9ea1c-117">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-117">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ea1c-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ea1c-118">Child Elements</span></span>  
 <span data-ttu-id="9ea1c-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ea1c-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ea1c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9ea1c-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ea1c-121">Element</span></span>|<span data-ttu-id="9ea1c-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ea1c-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9ea1c-123">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9ea1c-124">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ea1c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ea1c-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ea1c-126">.NET Framework 4 ve sonrasında, bu öğenin derleme yükleme süreleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-126">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="9ea1c-127">Daha fazla bilgi için [güvenlik değişikliklerinin](/previous-versions/dotnet/framework/security/security-changes)"güvenlik ilkesi basitleştirmesi" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-127">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="9ea1c-128">Ortak dil çalışma zamanı (CLR), derleme için kanıt oluşturmak üzere yükleme zamanında Authenticode imzasını doğrulamaya çalışır <xref:System.Security.Policy.Publisher> .</span><span class="sxs-lookup"><span data-stu-id="9ea1c-128">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="9ea1c-129">Ancak, varsayılan olarak çoğu uygulama <xref:System.Security.Policy.Publisher> kanıt gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-129">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="9ea1c-130">Standart CAS ilkesi öğesine bağlı değildir <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="9ea1c-130">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="9ea1c-131">Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütülmediği veya kısmi güven ortamındaki taleplerini karşılamak üzere bir sorun olduğu müddetçe, yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyetinden kaçının <xref:System.Security.Permissions.PublisherIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="9ea1c-131">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="9ea1c-132">(Kimlik izinlerinin istekleri her zaman tam güven ortamında başarılı olur.)</span><span class="sxs-lookup"><span data-stu-id="9ea1c-132">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ea1c-133">Hizmetin, `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesini kullanmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-133">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="9ea1c-134">Bu öğenin kullanılması, zaman aşımına neden olabilecek ve hizmet başlangıcını iptal eden gecikmelerden kaçınmaya da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-134">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="9ea1c-135">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="9ea1c-135">Configuration File</span></span>  
 <span data-ttu-id="9ea1c-136">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-136">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ea1c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="9ea1c-137">Example</span></span>  
 <span data-ttu-id="9ea1c-138">Aşağıdaki örnek, `<generatePublisherEvidence>` bir uygulama IÇIN CAS yayımcı ilkesi denetimini devre dışı bırakmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-138">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ea1c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ea1c-139">See also</span></span>

- [<span data-ttu-id="9ea1c-140">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9ea1c-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9ea1c-141">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9ea1c-141">Configuration File Schema</span></span>](../index.md)
