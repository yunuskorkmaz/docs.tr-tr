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
ms.openlocfilehash: eed2a4d06906d2928be62aed20a75484c3eea946
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699764"
---
# <a name="oidentry-element"></a><span data-ttu-id="6e0a2-102">\<Oıdentry > öğesi</span><span class="sxs-lookup"><span data-stu-id="6e0a2-102">\<oidEntry> Element</span></span>
<span data-ttu-id="6e0a2-103">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  
  
[<span data-ttu-id="6e0a2-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="6e0a2-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="6e0a2-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6e0a2-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="6e0a2-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<Cryptographrivsettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e0a2-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="6e0a2-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<Oıdmap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="6e0a2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="6e0a2-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 **\<Oıdentry >**</span><span class="sxs-lookup"><span data-stu-id="6e0a2-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e0a2-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e0a2-109">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e0a2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e0a2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e0a2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e0a2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e0a2-112">Attributes</span></span>  
  
|<span data-ttu-id="6e0a2-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6e0a2-113">Attribute</span></span>|<span data-ttu-id="6e0a2-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e0a2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6e0a2-115">**ID**</span><span class="sxs-lookup"><span data-stu-id="6e0a2-115">**OID**</span></span>|<span data-ttu-id="6e0a2-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e0a2-117">Sınıfınız tarafından uygulanan algoritmaya karşılık gelen ASN. 1 OID 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-117">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="6e0a2-118">**ada**</span><span class="sxs-lookup"><span data-stu-id="6e0a2-118">**name**</span></span>|<span data-ttu-id="6e0a2-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="6e0a2-120">[@No__t-2nameEntry >](nameentry-element.md) etiketindeki **ad** özniteliğinin değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-120">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e0a2-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e0a2-121">Child Elements</span></span>  
 <span data-ttu-id="6e0a2-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e0a2-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e0a2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6e0a2-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e0a2-124">Element</span></span>|<span data-ttu-id="6e0a2-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e0a2-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6e0a2-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6e0a2-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-127">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="6e0a2-128">@No__t-0 öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-128">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="6e0a2-129">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-129">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e0a2-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e0a2-130">Remarks</span></span>  
 <span data-ttu-id="6e0a2-131">ASN. 1 nesne tanımlayıcıları bazı şifreleme biçimlerinde algoritmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-131">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="6e0a2-132">Tanımlamak istediğiniz algoritmaların nesne tanımlayıcılarını kolay adlarla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-132">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e0a2-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e0a2-133">Example</span></span>  
 <span data-ttu-id="6e0a2-134">Aşağıdaki örnek, RIPEMD-160 karma algoritması için bir nesne tanımlayıcısını bu karma algoritmanın bir uygulamasına eşlemek için **\<Oıdentry >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-134">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e0a2-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e0a2-135">See also</span></span>

- [<span data-ttu-id="6e0a2-136">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="6e0a2-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6e0a2-137">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6e0a2-137">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6e0a2-138">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6e0a2-138">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6e0a2-139">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6e0a2-139">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="6e0a2-140">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="6e0a2-140">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
