---
title: <bypassTrustedAppStrongNames> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92873277b4b25e4c1c5981628187078ac7cb5704
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920895"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="d9435-102">\<bypassTrustedAppStrongNames > öğesi</span><span class="sxs-lookup"><span data-stu-id="d9435-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="d9435-103">Tam güvenle <xref:System.AppDomain>yüklenmiş olan tam güven derlemelerindeki tanımlayıcı adların doğrulanmasının atlanıp atlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9435-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="d9435-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d9435-104">\<configuration></span></span>  
<span data-ttu-id="d9435-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="d9435-105">\<runtime></span></span>  
<span data-ttu-id="d9435-106">\<bypassTrustedAppStrongNames ></span><span class="sxs-lookup"><span data-stu-id="d9435-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9435-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9435-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9435-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9435-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d9435-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9435-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9435-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d9435-110">Attributes</span></span>  
  
|<span data-ttu-id="d9435-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9435-111">Attribute</span></span>|<span data-ttu-id="d9435-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9435-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="d9435-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d9435-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d9435-114">Tam güven derlemeleri için tanımlayıcı adların doğrulanmasını önleyen atlama özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d9435-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="d9435-115">Bu özellik etkinleştirildiğinde, derleme yüklendiğinde tanımlayıcı adlar doğruluk açısından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d9435-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="d9435-116">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="d9435-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d9435-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d9435-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="d9435-118">Değer</span><span class="sxs-lookup"><span data-stu-id="d9435-118">Value</span></span>|<span data-ttu-id="d9435-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9435-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="d9435-120">Derlemeler tam güvenle <xref:System.AppDomain>yüklendiğinde, tam güven derlemelerindeki tanımlayıcı ad imzaları doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="d9435-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="d9435-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d9435-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="d9435-122">Tam güven derlemelerindeki tanımlayıcı ad imzaları, derlemeler tam güvenle <xref:System.AppDomain>yüklendiğinde onaylanır.</span><span class="sxs-lookup"><span data-stu-id="d9435-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="d9435-123">Tanımlayıcı ad imzası yalnızca imza doğruluğu için denetlenir; bir eşleşme için başka bir tanımlayıcı adla karşılaştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="d9435-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9435-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9435-124">Child Elements</span></span>  
 <span data-ttu-id="d9435-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="d9435-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9435-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d9435-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d9435-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="d9435-127">Element</span></span>|<span data-ttu-id="d9435-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9435-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d9435-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d9435-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d9435-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="d9435-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9435-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9435-131">Remarks</span></span>  
 <span data-ttu-id="d9435-132">Tanımlayıcı adı atlama özelliği, tam güven derlemelerinin tanımlayıcı ad imzası doğrulamasının yükünü önler.</span><span class="sxs-lookup"><span data-stu-id="d9435-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="d9435-133">Atlama özelliği, bir tanımlayıcı ad ile imzalanmış ve aşağıdaki özelliklere sahip olan her derleme için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="d9435-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
- <span data-ttu-id="d9435-134"><xref:System.Security.Policy.StrongName> Kanıt olmadan tamamen güvenilir (örneğin, bölge kanıtları `MyComputer` vardır).</span><span class="sxs-lookup"><span data-stu-id="d9435-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
- <span data-ttu-id="d9435-135">Tam güvenilir <xref:System.AppDomain>bir şekilde yüklendi.</span><span class="sxs-lookup"><span data-stu-id="d9435-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="d9435-136"><xref:System.AppDomainSetup.ApplicationBase%2A> Özelliği altında<xref:System.AppDomain>bir konumdan yüklendi.</span><span class="sxs-lookup"><span data-stu-id="d9435-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
- <span data-ttu-id="d9435-137">Gecikmeli imza değildir.</span><span class="sxs-lookup"><span data-stu-id="d9435-137">Not delay-signed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9435-138">Bir kayıt defteri anahtarı kullanılarak bilgisayardaki tüm uygulamalar için atlama özelliği kapatılmışsa, bu yapılandırma dosyası ayarının etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d9435-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="d9435-139">Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adı atlama özelliğini](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d9435-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9435-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9435-140">Example</span></span>  
 <span data-ttu-id="d9435-141">Aşağıdaki örnek, tam güven derlemelerinde tanımlayıcı ad imzasını doğrulayan davranışın nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d9435-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9435-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9435-142">See also</span></span>

- [<span data-ttu-id="d9435-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d9435-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d9435-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d9435-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d9435-145">Nasıl yapılır: Tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="d9435-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../app-domains/how-to-disable-the-strong-name-bypass-feature.md)
