---
description: 'Daha fazla bilgi edinin: <oidEntry> öğesi'
title: <oidEntry> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: d5fe22018377e247ffa0b6addb58cbeee7119e66
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698758"
---
# <a name="oidentry-element"></a><span data-ttu-id="e26ee-103">\<oidEntry> Öğesi</span><span class="sxs-lookup"><span data-stu-id="e26ee-103">\<oidEntry> Element</span></span>

<span data-ttu-id="e26ee-104">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="e26ee-104">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oidEntry>**

## <a name="syntax"></a><span data-ttu-id="e26ee-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e26ee-105">Syntax</span></span>  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e26ee-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e26ee-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e26ee-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e26ee-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e26ee-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e26ee-108">Attributes</span></span>  
  
|<span data-ttu-id="e26ee-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e26ee-109">Attribute</span></span>|<span data-ttu-id="e26ee-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e26ee-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e26ee-111">**ID**</span><span class="sxs-lookup"><span data-stu-id="e26ee-111">**OID**</span></span>|<span data-ttu-id="e26ee-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e26ee-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="e26ee-113">Sınıfınız tarafından uygulanan algoritmaya karşılık gelen ASN. 1 OID 'yi belirtir.</span><span class="sxs-lookup"><span data-stu-id="e26ee-113">Specifies the ASN.1 OID corresponding to the algorithm implemented by your class.</span></span>|  
|<span data-ttu-id="e26ee-114">**ada**</span><span class="sxs-lookup"><span data-stu-id="e26ee-114">**name**</span></span>|<span data-ttu-id="e26ee-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e26ee-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="e26ee-116">Etiketteki **Name** özniteliğinin değerini belirtir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e26ee-116">Specifies the value for the **name** attribute in the [\<nameEntry>](nameentry-element.md) tag.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e26ee-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e26ee-117">Child Elements</span></span>  

 <span data-ttu-id="e26ee-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="e26ee-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e26ee-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e26ee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e26ee-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="e26ee-120">Element</span></span>|<span data-ttu-id="e26ee-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e26ee-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e26ee-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e26ee-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="e26ee-123">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e26ee-123">Contains cryptography settings.</span></span>|  
|`mscorlib`|<span data-ttu-id="e26ee-124">Öğesini içerir `cryptographySettings` .</span><span class="sxs-lookup"><span data-stu-id="e26ee-124">Contains the `cryptographySettings` element.</span></span>|  
|`oidMap`|<span data-ttu-id="e26ee-125">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e26ee-125">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e26ee-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e26ee-126">Remarks</span></span>  

 <span data-ttu-id="e26ee-127">ASN. 1 nesne tanımlayıcıları bazı şifreleme biçimlerinde algoritmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="e26ee-127">ASN.1 object identifiers identify algorithms in some cryptographic formats.</span></span> <span data-ttu-id="e26ee-128">Tanımlamak istediğiniz algoritmaların nesne tanımlayıcılarını kolay adlarla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="e26ee-128">Map object identifiers to friendly names for the algorithms you want to identify.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e26ee-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="e26ee-129">Example</span></span>  

 <span data-ttu-id="e26ee-130">Aşağıdaki örnek, **\<oidEntry>** RIPEMD-160 karma algoritmasının bir nesne tanımlayıcısını, bu karma algoritmanın bir uygulamasına eşlemek için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e26ee-130">The following example shows how to use the **\<oidEntry>** element to map an object identifier for the RIPEMD-160 hash algorithm to an implementation of that hash algorithm.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e26ee-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e26ee-131">See also</span></span>

- [<span data-ttu-id="e26ee-132">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="e26ee-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e26ee-133">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="e26ee-133">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e26ee-134">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e26ee-134">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="e26ee-135">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e26ee-135">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
- [<span data-ttu-id="e26ee-136">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e26ee-136">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../map-object-identifiers-to-cryptography-algorithms.md)
