---
title: '&lt;oidEntry&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c891b5d67c7f2ef46682233ad555a1276f8e027d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606906"
---
# <a name="ltoidentrygt-element"></a><span data-ttu-id="3b5af-102">&lt;oidEntry&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="3b5af-102">&lt;oidEntry&gt; Element</span></span>
<span data-ttu-id="3b5af-103">ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.</span><span class="sxs-lookup"><span data-stu-id="3b5af-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="3b5af-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3b5af-104">\<configuration></span></span>  
<span data-ttu-id="3b5af-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="3b5af-105">\<mscorlib></span></span>  
<span data-ttu-id="3b5af-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="3b5af-106">\<cryptographySettings></span></span>  
<span data-ttu-id="3b5af-107">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="3b5af-107">\<oidMap></span></span>  
<span data-ttu-id="3b5af-108">\<oidEntry ></span><span class="sxs-lookup"><span data-stu-id="3b5af-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b5af-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b5af-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b5af-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b5af-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3b5af-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3b5af-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b5af-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3b5af-112">Attributes</span></span>  
  
|<span data-ttu-id="3b5af-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3b5af-113">Attribute</span></span>|<span data-ttu-id="3b5af-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b5af-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b5af-115">**OID**</span><span class="sxs-lookup"><span data-stu-id="3b5af-115">**OID**</span></span>|<span data-ttu-id="3b5af-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b5af-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b5af-117">Sınıfınız tarafından uygulanan algoritması karşılık gelen ASN.1 OID belirtir.</span><span class="sxs-lookup"><span data-stu-id="3b5af-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="3b5af-118">**Adı**</span><span class="sxs-lookup"><span data-stu-id="3b5af-118">**name**</span></span>|<span data-ttu-id="3b5af-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="3b5af-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="3b5af-120">Değeri belirtir **adı** özniteliğini [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) etiketi.</span><span class="sxs-lookup"><span data-stu-id="3b5af-120">Specifies the value for the **name** attribute in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b5af-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b5af-121">Child Elements</span></span>  
 <span data-ttu-id="3b5af-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="3b5af-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b5af-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3b5af-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3b5af-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="3b5af-124">Element</span></span>|<span data-ttu-id="3b5af-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b5af-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3b5af-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3b5af-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="3b5af-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3b5af-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="3b5af-128">İçeren `cryptographySettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b5af-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="3b5af-129">ASN.1 nesne tanımlayıcısını (OID) eşlemeleri için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="3b5af-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b5af-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b5af-130">Remarks</span></span>  
 <span data-ttu-id="3b5af-131">ASN.1 nesne tanımlayıcılarını şifreleme bazı biçimlerde algoritmaları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b5af-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="3b5af-132">Nesne tanımlayıcılarını tanımlamak istediğiniz algoritmalar için kolay adlar eşleyin.</span><span class="sxs-lookup"><span data-stu-id="3b5af-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b5af-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b5af-133">Example</span></span>  
 <span data-ttu-id="3b5af-134">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<oidEntry >** RIPEMD 160 karma algoritması için nesne tanımlayıcısı bu karma algoritmayı uygulaması için eşlemek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="3b5af-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b5af-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b5af-135">See also</span></span>
- [<span data-ttu-id="3b5af-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3b5af-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="3b5af-137">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3b5af-137">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="3b5af-138">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3b5af-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="3b5af-139">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3b5af-139">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [<span data-ttu-id="3b5af-140">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="3b5af-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
