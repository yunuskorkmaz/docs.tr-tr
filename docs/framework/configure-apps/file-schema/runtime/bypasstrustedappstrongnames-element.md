---
title: <bypassTrustedAppStrongNames> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739089"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="29bb9-102">\<bypassTrustedAppStrongNames> Öğesi</span><span class="sxs-lookup"><span data-stu-id="29bb9-102">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="29bb9-103">Tam güvenle yüklenmiş olan tam güven derlemelerindeki tanımlayıcı adların doğrulanmasının atlanıp atlanmayacağını belirtir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="29bb9-103">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="29bb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29bb9-104">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="29bb9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="29bb9-105">Attributes and Elements</span></span>

<span data-ttu-id="29bb9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="29bb9-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="29bb9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="29bb9-107">Attributes</span></span>

|<span data-ttu-id="29bb9-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29bb9-108">Attribute</span></span>|<span data-ttu-id="29bb9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29bb9-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="29bb9-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="29bb9-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="29bb9-111">Tam güven derlemeleri için tanımlayıcı adların doğrulanmasını önleyen atlama özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29bb9-111">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="29bb9-112">Bu özellik etkinleştirildiğinde, derleme yüklendiğinde tanımlayıcı adlar doğruluk açısından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="29bb9-112">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="29bb9-113">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="29bb9-113">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="29bb9-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="29bb9-114">enabled Attribute</span></span>

|<span data-ttu-id="29bb9-115">Değer</span><span class="sxs-lookup"><span data-stu-id="29bb9-115">Value</span></span>|<span data-ttu-id="29bb9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29bb9-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="29bb9-117">Derlemeler tam güvenle yüklendiğinde, tam güven derlemelerindeki tanımlayıcı ad imzaları doğrulanmaz <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="29bb9-117">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="29bb9-118">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="29bb9-118">This is the default.</span></span>|
|`false`|<span data-ttu-id="29bb9-119">Tam güven derlemelerindeki tanımlayıcı ad imzaları, derlemeler tam güvenle yüklendiğinde onaylanır <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="29bb9-119">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="29bb9-120">Tanımlayıcı ad imzası yalnızca imza doğruluğu için denetlenir; bir eşleşme için başka bir tanımlayıcı adla karşılaştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="29bb9-120">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="29bb9-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="29bb9-121">Child Elements</span></span>

<span data-ttu-id="29bb9-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="29bb9-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="29bb9-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="29bb9-123">Parent Elements</span></span>

|<span data-ttu-id="29bb9-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="29bb9-124">Element</span></span>|<span data-ttu-id="29bb9-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29bb9-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="29bb9-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="29bb9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="29bb9-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="29bb9-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="29bb9-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29bb9-128">Remarks</span></span>

<span data-ttu-id="29bb9-129">Tanımlayıcı adı atlama özelliği, tam güven derlemelerinin tanımlayıcı ad imzası doğrulamasının yükünü önler.</span><span class="sxs-lookup"><span data-stu-id="29bb9-129">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="29bb9-130">Atlama özelliği, bir tanımlayıcı ad ile imzalanmış ve aşağıdaki özelliklere sahip olan her derleme için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="29bb9-130">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="29bb9-131">Kanıt olmadan tamamen güvenilir <xref:System.Security.Policy.StrongName> (örneğin, `MyComputer` bölge kanıtları vardır).</span><span class="sxs-lookup"><span data-stu-id="29bb9-131">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="29bb9-132">Tam güvenilir bir şekilde yüklendi <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="29bb9-132">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="29bb9-133">Özelliği altında bir konumdan yüklendi <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="29bb9-133">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="29bb9-134">Gecikmeli imza değildir.</span><span class="sxs-lookup"><span data-stu-id="29bb9-134">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="29bb9-135">Bir kayıt defteri anahtarı kullanılarak bilgisayardaki tüm uygulamalar için atlama özelliği kapatılmışsa, bu yapılandırma dosyası ayarının etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="29bb9-135">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="29bb9-136">Daha fazla bilgi için bkz. [nasıl yapılır: güçlü adı atlama özelliğini devre dışı bırakma](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="29bb9-136">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="29bb9-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="29bb9-137">Example</span></span>

<span data-ttu-id="29bb9-138">Aşağıdaki örnek, tam güven derlemelerinde tanımlayıcı ad imzasını doğrulayan davranışın nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29bb9-138">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="29bb9-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29bb9-139">See also</span></span>

- [<span data-ttu-id="29bb9-140">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="29bb9-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="29bb9-141">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="29bb9-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="29bb9-142">Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="29bb9-142">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
