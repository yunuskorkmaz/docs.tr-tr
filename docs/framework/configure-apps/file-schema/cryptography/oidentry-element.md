---
title: <oidEntry> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 013994e36c4c63410a753967cbac92c38783ae62
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659585"
---
# <a name="oidentry-element"></a><span data-ttu-id="f6bf3-102">\<Oıdentry > öğesi</span><span class="sxs-lookup"><span data-stu-id="f6bf3-102">\<oidEntry> Element</span></span>
<span data-ttu-id="f6bf3-103">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
 <span data-ttu-id="f6bf3-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="f6bf3-104">\<configuration></span></span>  
<span data-ttu-id="f6bf3-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="f6bf3-105">\<mscorlib></span></span>  
<span data-ttu-id="f6bf3-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="f6bf3-106">\<cryptographySettings></span></span>  
<span data-ttu-id="f6bf3-107">\<Oıdmap ></span><span class="sxs-lookup"><span data-stu-id="f6bf3-107">\<oidMap></span></span>  
<span data-ttu-id="f6bf3-108">\<Oıdentry ></span><span class="sxs-lookup"><span data-stu-id="f6bf3-108">\<oidEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6bf3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f6bf3-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6bf3-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6bf3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f6bf3-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6bf3-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f6bf3-112">Attributes</span></span>  
  
|<span data-ttu-id="f6bf3-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f6bf3-113">Attribute</span></span>|<span data-ttu-id="f6bf3-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6bf3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6bf3-115">**ID**</span><span class="sxs-lookup"><span data-stu-id="f6bf3-115">**OID**</span></span>|<span data-ttu-id="f6bf3-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="f6bf3-117">Sınıfınız tarafından uygulanan algoritmaya karşılık gelen ASN. 1 OID 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="f6bf3-118">**name**</span><span class="sxs-lookup"><span data-stu-id="f6bf3-118">**name**</span></span>|<span data-ttu-id="f6bf3-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="f6bf3-120">NameEntry > etiketinde **ad** özniteliğinin [değerini belirtir. \<](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6bf3-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6bf3-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6bf3-121">Child Elements</span></span>  
 <span data-ttu-id="f6bf3-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6bf3-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f6bf3-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f6bf3-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f6bf3-124">Element</span></span>|<span data-ttu-id="f6bf3-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6bf3-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f6bf3-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="f6bf3-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="f6bf3-128">`cryptographySettings` Öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="f6bf3-129">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6bf3-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6bf3-130">Remarks</span></span>  
 <span data-ttu-id="f6bf3-131">ASN. 1 nesne tanımlayıcıları bazı şifreleme biçimlerinde algoritmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="f6bf3-132">Tanımlamak istediğiniz algoritmaların nesne tanımlayıcılarını kolay adlarla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6bf3-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6bf3-133">Example</span></span>  
 <span data-ttu-id="f6bf3-134">Aşağıdaki örnek, RIPEMD-160 karma algoritması için bir nesne tanımlayıcısını bu karma algoritmanın bir uygulamasına eşlemek için  **\<oıdentry >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6bf3-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6bf3-135">See also</span></span>

- [<span data-ttu-id="f6bf3-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="f6bf3-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f6bf3-137">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="f6bf3-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f6bf3-138">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f6bf3-138">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="f6bf3-139">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f6bf3-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="f6bf3-140">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="f6bf3-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
