---
title: <generatePublisherEvidence> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
ms.openlocfilehash: c2ba4a7244b7849e28eac38fb34a2cdd0d1f1048
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645352"
---
# <a name="generatepublisherevidence-element"></a><span data-ttu-id="55158-102">\<PublisherEvidence> Öğesi'ni oluşturur</span><span class="sxs-lookup"><span data-stu-id="55158-102">\<generatePublisherEvidence> Element</span></span>
<span data-ttu-id="55158-103">Çalışma zamanının kod erişim <xref:System.Security.Policy.Publisher> güvenliği (CAS) için kanıt oluşturup oluşturmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55158-103">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence for code access security (CAS).</span></span>  
  
<span data-ttu-id="55158-104">[**\<yapılandırma>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55158-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55158-105">&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="55158-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="55158-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<PublisherEvidence>**</span><span class="sxs-lookup"><span data-stu-id="55158-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<generatePublisherEvidence>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55158-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55158-107">Syntax</span></span>  
  
```xml  
<generatePublisherEvidence
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55158-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55158-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55158-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55158-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55158-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55158-110">Attributes</span></span>  
  
|<span data-ttu-id="55158-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55158-111">Attribute</span></span>|<span data-ttu-id="55158-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55158-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55158-113">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="55158-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="55158-114">Çalışma zamanının kanıt oluşturup <xref:System.Security.Policy.Publisher> oluşturmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="55158-114">Specifies whether the runtime creates <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55158-115">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="55158-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="55158-116">Değer</span><span class="sxs-lookup"><span data-stu-id="55158-116">Value</span></span>|<span data-ttu-id="55158-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55158-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="55158-118">Kanıt yaratmaz. <xref:System.Security.Policy.Publisher></span><span class="sxs-lookup"><span data-stu-id="55158-118">Does not create <xref:System.Security.Policy.Publisher> evidence.</span></span>|  
|`true`|<span data-ttu-id="55158-119">Kanıt <xref:System.Security.Policy.Publisher> yaratır.</span><span class="sxs-lookup"><span data-stu-id="55158-119">Creates <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="55158-120">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="55158-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55158-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55158-121">Child Elements</span></span>  
 <span data-ttu-id="55158-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="55158-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55158-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55158-123">Parent Elements</span></span>  
  
|<span data-ttu-id="55158-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="55158-124">Element</span></span>|<span data-ttu-id="55158-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55158-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55158-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="55158-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55158-127">Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="55158-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55158-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55158-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55158-129">.NET Framework 4 ve sonraki durumlarda, bu öğenin montaj yük süreleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="55158-129">In the .NET Framework 4 and later, this element has no effect on assembly load times.</span></span> <span data-ttu-id="55158-130">Daha fazla bilgi için, [Güvenlik Değişiklikleri'ndeki](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes)"Güvenlik İlkesi Basitleştirme" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="55158-130">For more information, see the "Security Policy Simplification" section in [Security Changes](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).</span></span>  
  
 <span data-ttu-id="55158-131">Ortak dil çalışma süresi (CLR), derleme için kanıt oluşturmak <xref:System.Security.Policy.Publisher> için yük zamanında Authenticode imzasını doğrulamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="55158-131">The common language runtime (CLR) tries to verify the Authenticode signature at load time to create <xref:System.Security.Policy.Publisher> evidence for the assembly.</span></span> <span data-ttu-id="55158-132">Ancak, varsayılan olarak, çoğu uygulamakanıt gerekmez. <xref:System.Security.Policy.Publisher></span><span class="sxs-lookup"><span data-stu-id="55158-132">However, by default, most applications do not need <xref:System.Security.Policy.Publisher> evidence.</span></span> <span data-ttu-id="55158-133">Standart CAS <xref:System.Security.Policy.PublisherMembershipCondition>ilkesi, ..</span><span class="sxs-lookup"><span data-stu-id="55158-133">Standard CAS policy does not rely on the <xref:System.Security.Policy.PublisherMembershipCondition>.</span></span> <span data-ttu-id="55158-134">Uygulamanız özel CAS ilkesine sahip bir bilgisayarda yürütülmedikçe veya kısmi güven ortamında taleplerini <xref:System.Security.Permissions.PublisherIdentityPermission> karşılamayı amaçlamıyorsa, yayımcı imzasını doğrulamayla ilişkili gereksiz başlangıç maliyetinden kaçınmalısınız.</span><span class="sxs-lookup"><span data-stu-id="55158-134">You should avoid the unnecessary startup cost associated with verifying the publisher signature unless your application executes on a computer with custom CAS policy, or is intending to satisfy demands for <xref:System.Security.Permissions.PublisherIdentityPermission> in a partial-trust environment.</span></span> <span data-ttu-id="55158-135">(Kimlik izinleri talepleri her zaman tam güven ortamında başarılı olur.)</span><span class="sxs-lookup"><span data-stu-id="55158-135">(Demands for identity permissions always succeed in a full-trust environment.)</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55158-136">Hizmetlerin başlangıç performansını `<generatePublisherEvidence>` artırmak için öğeyi kullanmasını öneririz.</span><span class="sxs-lookup"><span data-stu-id="55158-136">We recommend that services use the `<generatePublisherEvidence>` element to improve startup performance.</span></span>  <span data-ttu-id="55158-137">Bu öğeyi kullanmak, zaman ayarı ve hizmet başlatmanın iptaline neden olabilecek gecikmeleri önlemeye de yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="55158-137">Using this element can also help avoid delays that can cause a time-out and the cancellation of the service startup.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="55158-138">Yapılandırma Dosyası</span><span class="sxs-lookup"><span data-stu-id="55158-138">Configuration File</span></span>  
 <span data-ttu-id="55158-139">Bu öğe yalnızca uygulama yapılandırma dosyasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="55158-139">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55158-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="55158-140">Example</span></span>  
 <span data-ttu-id="55158-141">Aşağıdaki örnek, bir uygulama `<generatePublisherEvidence>` için CAS yayımcı ilkesini denetlemeyi devre dışı betmek için öğenin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="55158-141">The following example shows how to use the `<generatePublisherEvidence>` element to disable checking for CAS publisher policy for an application.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55158-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55158-142">See also</span></span>

- [<span data-ttu-id="55158-143">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="55158-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="55158-144">Yapılandırma Dosya Şema</span><span class="sxs-lookup"><span data-stu-id="55158-144">Configuration File Schema</span></span>](../index.md)
