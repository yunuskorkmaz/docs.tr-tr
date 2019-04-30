---
title: <enforceFIPSPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1aa958e15449949a1b7ca740198fff71295b2ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704975"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="41ee0-102">\<Enforcefıpspolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="41ee0-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="41ee0-103">Şifreleme algoritmaları Federal Bilgi işleme standartları (FIPS ile) uyması gereken bir bilgisayar yapılandırma gereksinimini zorlanıp zorlanmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="41ee0-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
 <span data-ttu-id="41ee0-104">\<Yapılandırma > öğesi</span><span class="sxs-lookup"><span data-stu-id="41ee0-104">\<configuration> Element</span></span>  
<span data-ttu-id="41ee0-105">\<çalışma zamanı > öğesi</span><span class="sxs-lookup"><span data-stu-id="41ee0-105">\<runtime> Element</span></span>  
<span data-ttu-id="41ee0-106">\<Enforcefıpspolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="41ee0-106">\<enforceFIPSPolicy> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ee0-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41ee0-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41ee0-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="41ee0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="41ee0-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="41ee0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41ee0-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="41ee0-110">Attributes</span></span>  
  
|<span data-ttu-id="41ee0-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41ee0-111">Attribute</span></span>|<span data-ttu-id="41ee0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41ee0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41ee0-113">Etkin</span><span class="sxs-lookup"><span data-stu-id="41ee0-113">enabled</span></span>|<span data-ttu-id="41ee0-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="41ee0-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="41ee0-115">Şifreleme algoritması FIPS ile uyumlu bir bilgisayar yapılandırma gereksinimini uygulanması etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="41ee0-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="41ee0-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="41ee0-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="41ee0-117">Değer</span><span class="sxs-lookup"><span data-stu-id="41ee0-117">Value</span></span>|<span data-ttu-id="41ee0-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41ee0-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="41ee0-119">Bilgisayarınız, şifreleme algoritmaları FIPS uyumlu olmasını gerektirecek şekilde yapılandırılmışsa, bu gereksinimi zorunlu tutulur.</span><span class="sxs-lookup"><span data-stu-id="41ee0-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="41ee0-120">Bir sınıf oluşturucuları FIPS ile uyumlu değil bir algoritma uyguluyorsa veya `Create` yöntemleri o sınıf için o bilgisayarda çalıştırdığınızda özel durum throw.</span><span class="sxs-lookup"><span data-stu-id="41ee0-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="41ee0-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="41ee0-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="41ee0-122">Uygulama tarafından kullanılan şifreleme algoritmaları, bilgisayar yapılandırması ne olursa olsun, FIPS uyumlu olmasını gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="41ee0-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41ee0-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="41ee0-123">Child Elements</span></span>  
 <span data-ttu-id="41ee0-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="41ee0-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41ee0-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="41ee0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="41ee0-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="41ee0-126">Element</span></span>|<span data-ttu-id="41ee0-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="41ee0-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="41ee0-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="41ee0-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="41ee0-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="41ee0-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41ee0-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41ee0-130">Remarks</span></span>  
 <span data-ttu-id="41ee0-131">Şifreleme algoritmalarını uygulayan sınıflar oluşturma, .NET Framework 2.0 ile başlayarak, bilgisayar yapılandırması tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="41ee0-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="41ee0-132">Bilgisayar algoritmaları FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırılmış ve bir sınıf FIPS ile uyumlu değil bir algoritma uygular, bu sınıfın bir örneğini oluşturmak için her türlü girişim, özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="41ee0-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="41ee0-133">Throw oluşturucular bir <xref:System.InvalidOperationException> özel durumu ve `Create` yöntemleri throw bir <xref:System.Reflection.TargetInvocationException> özel durumla bir iç <xref:System.InvalidOperationException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="41ee0-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="41ee0-134">FIPS uyumluluğu olan yapılandırmalar gerektirir bilgisayarlarda uygulamanızın çalıştığı ve uygulamanızı FIPS ile uyumlu değil bir algoritma kullanır, bu öğe yapılandırma dosyanızda gelen ortak dil çalışma zamanı (CLR) önlemek için kullanabilirsiniz FIPS uyumluluğunu zorlama.</span><span class="sxs-lookup"><span data-stu-id="41ee0-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="41ee0-135">Bu öğe de sunulan [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41ee0-135">This element was introduced in the [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="41ee0-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="41ee0-136">Example</span></span>  
 <span data-ttu-id="41ee0-137">Aşağıdaki örnek, FIPS uyumluluğu zorlama gelen CLR önlemek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="41ee0-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="41ee0-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="41ee0-138">See also</span></span>

- [<span data-ttu-id="41ee0-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="41ee0-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="41ee0-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="41ee0-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="41ee0-141">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="41ee0-141">Cryptography Model</span></span>](../../../../../docs/standard/security/cryptography-model.md)
