---
description: 'Daha fazla bilgi edinin: <bypassTrustedAppStrongNames> öğesi'
title: <bypassTrustedAppStrongNames> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: d23b9efa19481027480f2a1c7dab22bc97a05e13
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719168"
---
# <a name="bypasstrustedappstrongnames-element"></a><span data-ttu-id="4579b-103">\<bypassTrustedAppStrongNames> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4579b-103">\<bypassTrustedAppStrongNames> Element</span></span>

<span data-ttu-id="4579b-104">Tam güvenle yüklenmiş olan tam güven derlemelerindeki tanımlayıcı adların doğrulanmasının atlanıp atlanmayacağını belirtir <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="4579b-104">Specifies whether to bypass the validation of strong names on full-trust assemblies that are loaded into a full-trust <xref:System.AppDomain>.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a><span data-ttu-id="4579b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4579b-105">Syntax</span></span>

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4579b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4579b-106">Attributes and Elements</span></span>

<span data-ttu-id="4579b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4579b-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="4579b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4579b-108">Attributes</span></span>

|<span data-ttu-id="4579b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4579b-109">Attribute</span></span>|<span data-ttu-id="4579b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4579b-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="4579b-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4579b-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="4579b-112">Tam güven derlemeleri için tanımlayıcı adların doğrulanmasını önleyen atlama özelliğinin etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4579b-112">Specifies whether the bypass feature that avoids validating strong names for full-trust assemblies is enabled.</span></span> <span data-ttu-id="4579b-113">Bu özellik etkinleştirildiğinde, derleme yüklendiğinde tanımlayıcı adlar doğruluk açısından doğrulanmaz.</span><span class="sxs-lookup"><span data-stu-id="4579b-113">When this feature is enabled, strong names are not validated for correctness when the assembly is loaded.</span></span> <span data-ttu-id="4579b-114">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="4579b-114">The default is `true`.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="4579b-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4579b-115">enabled Attribute</span></span>

|<span data-ttu-id="4579b-116">Değer</span><span class="sxs-lookup"><span data-stu-id="4579b-116">Value</span></span>|<span data-ttu-id="4579b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4579b-117">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="4579b-118">Derlemeler tam güvenle yüklendiğinde, tam güven derlemelerindeki tanımlayıcı ad imzaları doğrulanmaz <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="4579b-118">Strong-name signatures on full-trust assemblies are not validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="4579b-119">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="4579b-119">This is the default.</span></span>|
|`false`|<span data-ttu-id="4579b-120">Tam güven derlemelerindeki tanımlayıcı ad imzaları, derlemeler tam güvenle yüklendiğinde onaylanır <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="4579b-120">Strong-name signatures on full-trust assemblies are validated when the assemblies are loaded into a full-trust <xref:System.AppDomain>.</span></span> <span data-ttu-id="4579b-121">Tanımlayıcı ad imzası yalnızca imza doğruluğu için denetlenir; bir eşleşme için başka bir tanımlayıcı adla karşılaştırılmaz.</span><span class="sxs-lookup"><span data-stu-id="4579b-121">The strong-name signature is checked only for signature correctness; it is not compared to another strong name for a match.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4579b-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4579b-122">Child Elements</span></span>

<span data-ttu-id="4579b-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="4579b-123">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4579b-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4579b-124">Parent Elements</span></span>

|<span data-ttu-id="4579b-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="4579b-125">Element</span></span>|<span data-ttu-id="4579b-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4579b-126">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="4579b-127">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4579b-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="4579b-128">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="4579b-128">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4579b-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4579b-129">Remarks</span></span>

<span data-ttu-id="4579b-130">Tanımlayıcı adı atlama özelliği, tam güven derlemelerinin tanımlayıcı ad imzası doğrulamasının yükünü önler.</span><span class="sxs-lookup"><span data-stu-id="4579b-130">The strong-name bypass feature avoids the overhead of strong-name signature verification of full-trust assemblies.</span></span>

<span data-ttu-id="4579b-131">Atlama özelliği, bir tanımlayıcı ad ile imzalanmış ve aşağıdaki özelliklere sahip olan her derleme için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="4579b-131">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>

- <span data-ttu-id="4579b-132">Kanıt olmadan tamamen güvenilir <xref:System.Security.Policy.StrongName> (örneğin, `MyComputer` bölge kanıtları vardır).</span><span class="sxs-lookup"><span data-stu-id="4579b-132">Fully trusted without the <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>

- <span data-ttu-id="4579b-133">Tam güvenilir bir şekilde yüklendi <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="4579b-133">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="4579b-134">Özelliği altında bir konumdan yüklendi <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="4579b-134">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>

- <span data-ttu-id="4579b-135">Gecikmeli imza değildir.</span><span class="sxs-lookup"><span data-stu-id="4579b-135">Not delay-signed.</span></span>

> [!NOTE]
> <span data-ttu-id="4579b-136">Bir kayıt defteri anahtarı kullanılarak bilgisayardaki tüm uygulamalar için atlama özelliği kapatılmışsa, bu yapılandırma dosyası ayarının etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="4579b-136">If the bypass feature has been turned off for all applications on the computer by using a registry key, this configuration file setting has no effect.</span></span> <span data-ttu-id="4579b-137">Daha fazla bilgi için bkz. [nasıl yapılır: Strong-Name atlama özelliğini devre dışı bırakma](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span><span class="sxs-lookup"><span data-stu-id="4579b-137">For more information, see [How to: Disable the Strong-Name Bypass Feature](../../../../standard/assembly/disable-strong-name-bypass-feature.md).</span></span>

## <a name="example"></a><span data-ttu-id="4579b-138">Örnek</span><span class="sxs-lookup"><span data-stu-id="4579b-138">Example</span></span>

<span data-ttu-id="4579b-139">Aşağıdaki örnek, tam güven derlemelerinde tanımlayıcı ad imzasını doğrulayan davranışın nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4579b-139">The following example shows how to specify the behavior that validates the strong-name signature on full-trust assemblies.</span></span>

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="4579b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4579b-140">See also</span></span>

- [<span data-ttu-id="4579b-141">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4579b-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4579b-142">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4579b-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4579b-143">Nasıl yapılır: tanımlayıcı adı atlama özelliğini devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="4579b-143">How to: Disable the strong-name bypass feature</span></span>](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
