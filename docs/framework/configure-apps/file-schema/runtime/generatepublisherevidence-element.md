---
description: 'Daha fazla bilgi edinin: <generatePublisherEvidence> öğesi'
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: 2a949b52abe5ec10872d2cade49a0556063b2018
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754530"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="55268-103">\<generatePublisherEvidence> Öğesi</span><span class="sxs-lookup"><span data-stu-id="55268-103">\<generatePublisherEvidence> Element</span></span>

<span data-ttu-id="55268-104">Çalışma zamanının <xref:System.Security.Policy.Publisher> kod erişim güvenliği (CAS) için kanıt oluşturup oluşturmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55268-104">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**  
  
## <a name="syntax"></a><span data-ttu-id="55268-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="55268-105">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55268-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55268-106">Attributes and Elements</span></span>  

 <span data-ttu-id="55268-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55268-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55268-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55268-108">Attributes</span></span>  
  
|<span data-ttu-id="55268-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55268-109">Attribute</span></span>|<span data-ttu-id="55268-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55268-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55268-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55268-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="55268-112">Çalışma zamanının kanıt oluşturup oluşturmadığını belirtir <xref:System.Security.Policy.Publisher> .</span><span class="sxs-lookup"><span data-stu-id="55268-112">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55268-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55268-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="55268-114">Değer</span><span class="sxs-lookup"><span data-stu-id="55268-114">Value</span></span>|<span data-ttu-id="55268-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55268-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55268-116"><xref:System.Security.Policy.Publisher>Kanıt oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="55268-116">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="55268-117"><xref:System.Security.Policy.Publisher>Kanıt oluşturur.</span><span class="sxs-lookup"><span data-stu-id="55268-117">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="55268-118">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="55268-118">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55268-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55268-119">Child Elements</span></span>  

 <span data-ttu-id="55268-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="55268-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55268-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55268-121">Parent Elements</span></span>  
  
|<span data-ttu-id="55268-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="55268-122">Element</span></span>|<span data-ttu-id="55268-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55268-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55268-124">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="55268-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55268-125">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="55268-125">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55268-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55268-126">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55268-127">.NET Framework 4 ve sonrasında, bu öğenin derleme yükleme süreleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="55268-127">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="55268-128">Daha fazla bilgi için [güvenlik değişikliklerinin](/previous-versions/dotnet/framework/security/security-changes)"güvenlik ilkesi basitleştirmesi" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="55268-128">For more information, see the "Security Policy Simplification" section in [Security Changes](/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="55268-129">Ortak dil çalışma zamanı (CLR), derleme için kanıt oluşturmak üzere yükleme zamanında Authenticode imzasını doğrulamaya çalışır <xref:System.Security.Policy.Publisher> .</span><span class="sxs-lookup"><span data-stu-id="55268-129">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="55268-130">Ancak, varsayılan olarak çoğu uygulama <xref:System.Security.Policy.Publisher> kanıt gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="55268-130">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="55268-131">Standart CAS ilkesi öğesine bağlı değildir <xref:System.Security.Policy.PublisherMembershipCondition> .</span><span class="sxs-lookup"><span data-stu-id="55268-131">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="55268-132">Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütülmediği veya kısmi güven ortamındaki taleplerini karşılamak üzere bir sorun olduğu müddetçe, yayımcı imzasını doğrulama ile ilişkili gereksiz başlangıç maliyetinden kaçının <xref:System.Security.Permissions.PublisherIdentityPermission> .</span><span class="sxs-lookup"><span data-stu-id="55268-132">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="55268-133">(Kimlik izinlerinin istekleri her zaman tam güven ortamında başarılı olur.)</span><span class="sxs-lookup"><span data-stu-id="55268-133">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55268-134">Hizmetin, `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesini kullanmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="55268-134">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="55268-135">Bu öğenin kullanılması, zaman aşımına neden olabilecek ve hizmet başlangıcını iptal eden gecikmelerden kaçınmaya da yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="55268-135">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="55268-136">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="55268-136">Configuration File</span></span>  

 <span data-ttu-id="55268-137">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55268-137">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55268-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="55268-138">Example</span></span>  

 <span data-ttu-id="55268-139">Aşağıdaki örnek, `<generatePublisherEvidence>` bir uygulama IÇIN CAS yayımcı ilkesi denetimini devre dışı bırakmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55268-139">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55268-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55268-140">See also</span></span>

- [<span data-ttu-id="55268-141">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="55268-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55268-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="55268-142">Configuration File Schema</span></span>](../index.md)
