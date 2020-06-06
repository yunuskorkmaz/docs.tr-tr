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
ms.openlocfilehash: 4564cf59e3b6cfbdcd9dca06cd0f966d524834de
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088544"
---
# <a name="oidentry-element"></a><span data-ttu-id="d7763-102">\<oidEntry> Öğesi</span><span class="sxs-lookup"><span data-stu-id="d7763-102">\<oidEntry> Element</span></span>
<span data-ttu-id="d7763-103">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="d7763-103">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="d7763-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7763-104">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7763-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7763-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d7763-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7763-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7763-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d7763-107">Attributes</span></span>  
  
|<span data-ttu-id="d7763-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d7763-108">Attribute</span></span>|<span data-ttu-id="d7763-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7763-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7763-110">**ID**</span><span class="sxs-lookup"><span data-stu-id="d7763-110">**OID**</span></span>|<span data-ttu-id="d7763-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d7763-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="d7763-112">Sınıfınız tarafından uygulanan algoritmaya karşılık gelen ASN. 1 OID 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7763-112">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="d7763-113">**ada**</span><span class="sxs-lookup"><span data-stu-id="d7763-113">**name**</span></span>|<span data-ttu-id="d7763-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="d7763-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d7763-115">Etiketteki **Name** özniteliğinin değerini belirtir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d7763-115">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7763-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7763-116">Child Elements</span></span>  
 <span data-ttu-id="d7763-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7763-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7763-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7763-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d7763-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7763-119">Element</span></span>|<span data-ttu-id="d7763-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7763-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d7763-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="d7763-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="d7763-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d7763-122">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="d7763-123">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="d7763-123">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="d7763-124">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7763-124">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7763-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d7763-125">Remarks</span></span>  
 <span data-ttu-id="d7763-126">ASN. 1 nesne tanımlayıcıları bazı şifreleme biçimlerinde algoritmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="d7763-126">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="d7763-127">Tanımlamak istediğiniz algoritmaların nesne tanımlayıcılarını kolay adlarla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="d7763-127">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7763-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="d7763-128">Example</span></span>  
 <span data-ttu-id="d7763-129">Aşağıdaki örnek, **\<oidEntry>** RIPEMD-160 karma algoritmasının bir nesne tanımlayıcısını, bu karma algoritmanın bir uygulamasına eşlemek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7763-129">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d7763-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7763-130">See also</span></span>

- [<span data-ttu-id="d7763-131">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="d7763-131">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d7763-132">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d7763-132">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d7763-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d7763-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="d7763-134">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d7763-134">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="d7763-135">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="d7763-135">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
