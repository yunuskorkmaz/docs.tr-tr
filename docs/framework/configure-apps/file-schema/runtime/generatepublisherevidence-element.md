---
title: '&lt;generatePublisherEvidence&gt; öğesi'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33d4c023b7a649fd2aa3d9d52a90bb7111c59743
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683040"
---
# <a name="ltgeneratepublisherevidencegt-element"></a><span data-ttu-id="b8974-102">&lt;generatePublisherEvidence&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="b8974-102">&lt;generatePublisherEvidence&gt; Element</span></span>
<span data-ttu-id="b8974-103">Çalışma zamanı oluşturup oluşturmayacağını belirtir <xref:System.Security.Policy.Publisher> kod erişimi güvenliği (CAS) için kanıt.</span><span class="sxs-lookup"><span data-stu-id="b8974-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
 <span data-ttu-id="b8974-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="b8974-104">\<configuration></span></span>  
<span data-ttu-id="b8974-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="b8974-105">\<runtime></span></span>  
<span data-ttu-id="b8974-106">\<generatePublisherEvidence ></span><span class="sxs-lookup"><span data-stu-id="b8974-106">\<generatePublisherEvidence></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8974-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8974-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8974-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8974-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b8974-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b8974-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8974-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b8974-110">Attributes</span></span>  
  
|<span data-ttu-id="b8974-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8974-111">Attribute</span></span>|<span data-ttu-id="b8974-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8974-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b8974-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="b8974-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b8974-114">Çalışma zamanı oluşturup oluşturmayacağını belirtir <xref:System.Security.Policy.Publisher> kanıt.</span><span class="sxs-lookup"><span data-stu-id="b8974-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b8974-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="b8974-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="b8974-116">Değer</span><span class="sxs-lookup"><span data-stu-id="b8974-116">Value</span></span>|<span data-ttu-id="b8974-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8974-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b8974-118">Oluşturmaz <xref:System.Security.Policy.Publisher> kanıt.</span><span class="sxs-lookup"><span data-stu-id="b8974-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="b8974-119">Oluşturur <xref:System.Security.Policy.Publisher> kanıt.</span><span class="sxs-lookup"><span data-stu-id="b8974-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="b8974-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="b8974-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8974-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8974-121">Child Elements</span></span>  
 <span data-ttu-id="b8974-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="b8974-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8974-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b8974-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b8974-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="b8974-124">Element</span></span>|<span data-ttu-id="b8974-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8974-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b8974-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="b8974-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b8974-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="b8974-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8974-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8974-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8974-129">İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] ve daha sonra bu öğe üzerinde derleme yükleme süreleri etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b8974-129">In the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="b8974-130">Daha fazla bilgi için bkz: "Güvenlik ilkesi basitleştirme" bölümünde [güvenlik değişiklikleri](../../../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="b8974-130">For more information, see the "Security Policy Simplification" section in [Security Changes](../../../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="b8974-131">Ortak dil çalışma zamanı (CLR) oluşturmak için yükleme zamanında Authenticode imzasını dener <xref:System.Security.Policy.Publisher> için bütünleştirilmiş kanıt.</span><span class="sxs-lookup"><span data-stu-id="b8974-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="b8974-132">Bununla birlikte, varsayılan olarak, çoğu uygulama gerekmeyen <xref:System.Security.Policy.Publisher> kanıt.</span><span class="sxs-lookup"><span data-stu-id="b8974-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="b8974-133">Standart CAS ilkesini değil Bel <xref:System.Security.Policy.PublisherMembershipCondition>.</span><span class="sxs-lookup"><span data-stu-id="b8974-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="b8974-134">Uygulamanız özel CAS ilkesi olan bir bilgisayarda yürütür ya da talepleri karşılamak planladığı sürece yayımcı imzası doğrulanarak ile gereksiz başlangıç maliyeti kaçınmalısınız <xref:System.Security.Permissions.PublisherIdentityPermission> kısmi güven ortamında.</span><span class="sxs-lookup"><span data-stu-id="b8974-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="b8974-135">(Her zaman talepleri kimlik izinleri için tam güven ortamında başarılı.)</span><span class="sxs-lookup"><span data-stu-id="b8974-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8974-136">Kullanım Hizmetleri öneririz `<generatePublisherEvidence>` başlangıç performansını artırmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8974-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="b8974-137">Bu öğe kullanarak da bir zaman aşımı ve hizmetin başlatılması iptaline neden olabilecek gecikmeleri önlemek yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b8974-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b8974-138">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="b8974-138">Configuration File</span></span>  
 <span data-ttu-id="b8974-139">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8974-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8974-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8974-140">Example</span></span>  
 <span data-ttu-id="b8974-141">Aşağıdaki örnek nasıl kullanılacağını gösterir `<generatePublisherEvidence>` CAS bir uygulama için yayımcı ilkesi denetlemeyi devre dışı bırakmak için öğesi.</span><span class="sxs-lookup"><span data-stu-id="b8974-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8974-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8974-142">See also</span></span>
- [<span data-ttu-id="b8974-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="b8974-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="b8974-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="b8974-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
