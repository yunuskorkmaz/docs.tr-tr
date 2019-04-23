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
ms.openlocfilehash: 6c39d9a1e3da9cccb2f027e9597a6f2272d187ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179146"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="a6910-102">\<bypassTrustedAppStrongNames > öğesi</span><span class="sxs-lookup"><span data-stu-id="a6910-102">\<bypassTrustedAppStrongNames> Element</span></span>
<span data-ttu-id="a6910-103">Tanımlayıcı adları üzerinde tam güvene yüklenen derlemeleri tam güven doğrulama atlanıp atlanmayacağını belirtir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a6910-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>  
  
 <span data-ttu-id="a6910-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="a6910-104">\<configuration></span></span>  
<span data-ttu-id="a6910-105">\<çalışma zamanı ></span><span class="sxs-lookup"><span data-stu-id="a6910-105">\<runtime></span></span>  
<span data-ttu-id="a6910-106">\<bypassTrustedAppStrongNames></span><span class="sxs-lookup"><span data-stu-id="a6910-106">\<bypassTrustedAppStrongNames></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6910-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6910-107">Syntax</span></span>  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6910-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6910-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6910-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a6910-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6910-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a6910-110">Attributes</span></span>  
  
|<span data-ttu-id="a6910-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6910-111">Attribute</span></span>|<span data-ttu-id="a6910-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6910-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a6910-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="a6910-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="a6910-114">Tam güven derlemeleri için tanımlayıcı adlar doğrulama önler atlama özelliğini etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a6910-114">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="a6910-115">Bu özellik etkinleştirildiğinde, bir derleme yüklendiğinde güçlü adlar doğruluğu doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="a6910-115">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="a6910-116">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="a6910-116">The default is `true`.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a6910-117">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a6910-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="a6910-118">Değer</span><span class="sxs-lookup"><span data-stu-id="a6910-118">Value</span></span>|<span data-ttu-id="a6910-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6910-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="a6910-120">Tanımlayıcı ad imzaları tam güven derlemeleri derlemeleri tam güven içinde yüklü olduğunda doğrulanmaz <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a6910-120">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="a6910-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="a6910-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="a6910-122">Tam güven derlemeleri tanımlayıcı ad imzaları, derlemeleri tam güven içinde yüklü olduğunda doğrulanır <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a6910-122">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="a6910-123">Tanımlayıcı ad imzası yalnızca imza doğruluğu denetlenir; bir eşleşme için başka bir güçlü ad için karşılaştırılması değil.</span><span class="sxs-lookup"><span data-stu-id="a6910-123">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6910-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6910-124">Child Elements</span></span>  
 <span data-ttu-id="a6910-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="a6910-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6910-126">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a6910-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a6910-127">Öğe</span><span class="sxs-lookup"><span data-stu-id="a6910-127">Element</span></span>|<span data-ttu-id="a6910-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6910-128">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6910-129">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="a6910-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a6910-130">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="a6910-130">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6910-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6910-131">Remarks</span></span>  
 <span data-ttu-id="a6910-132">Tanımlayıcı adlı atlama özelliği, tam güven derleme tanımlayıcı ad imzası doğrulama yükünü ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="a6910-132">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>  
  
 <span data-ttu-id="a6910-133">Atlama özelliği, güçlü bir adla imzalanır ve aşağıdaki özelliklere sahip herhangi bir derleme için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a6910-133">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="a6910-134">Olmadan tam olarak güvenilen <xref:System.Security.Policy.StrongName> kanıt (örneğin, `MyComputer` kanıt bölge).</span><span class="sxs-lookup"><span data-stu-id="a6910-134">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="a6910-135">Tam olarak güvenilen yüklenen <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a6910-135">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="a6910-136">Bir konumdan yüklenen <xref:System.AppDomainSetup.ApplicationBase%2A> , söz konusu özellik <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a6910-136">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="a6910-137">Gecikmeli imzalanmış değil.</span><span class="sxs-lookup"><span data-stu-id="a6910-137">Not delay-signed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6910-138">Atlama özelliği bilgisayarda tüm uygulamalar için bir kayıt defteri anahtarını kullanarak devre dışı bırakıldıysa, bu yapılandırma dosyası ayarı bir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a6910-138">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="a6910-139">Daha fazla bilgi için [nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="a6910-139">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6910-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6910-140">Example</span></span>  
 <span data-ttu-id="a6910-141">Aşağıdaki örnek, tam güven derlemeleri üzerinde tanımlayıcı ad imzası doğrulama davranışını belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a6910-141">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6910-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6910-142">See also</span></span>

- [<span data-ttu-id="a6910-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a6910-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="a6910-144">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="a6910-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="a6910-145">Nasıl yapılır: Tanımlayıcı adlı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="a6910-145">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
