---
title: <cryptographySettings> Öğe
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: ec3a5a73caa901a21e22dbec7500af9153e01ef4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164144"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="10a8d-102">\<cryptographySettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="10a8d-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="10a8d-103">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="10a8d-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="10a8d-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="10a8d-104">\<configuration></span></span>  
<span data-ttu-id="10a8d-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="10a8d-105">\<mscorlib></span></span>  
<span data-ttu-id="10a8d-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="10a8d-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10a8d-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10a8d-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10a8d-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="10a8d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="10a8d-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="10a8d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10a8d-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="10a8d-110">Attributes</span></span>  
 <span data-ttu-id="10a8d-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="10a8d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="10a8d-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="10a8d-112">Child Elements</span></span>  
  
|<span data-ttu-id="10a8d-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="10a8d-113">Element</span></span>|<span data-ttu-id="10a8d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10a8d-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10a8d-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="10a8d-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="10a8d-116">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="10a8d-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="10a8d-117">\<oidMap></span><span class="sxs-lookup"><span data-stu-id="10a8d-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="10a8d-118">ASN.1 nesne tanımlayıcısını (OID) eşlemeleri için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="10a8d-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="10a8d-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="10a8d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="10a8d-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="10a8d-120">Element</span></span>|<span data-ttu-id="10a8d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10a8d-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="10a8d-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="10a8d-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="10a8d-123">İçeren `cryptographySettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="10a8d-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="10a8d-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="10a8d-124">Example</span></span>  
 <span data-ttu-id="10a8d-125">Aşağıdaki örnek nasıl kullanıldığını gösterir  **\<cryptographySettings >** şifreleme adı eşlemeleri ve OID eşlemeleri içerecek şekilde öğesi.</span><span class="sxs-lookup"><span data-stu-id="10a8d-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="10a8d-126">Bu örneği, çalışma zamanı yapılandırır. böylece <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> döndürür bir `MyHashClass` nesne ve `MyCryptoClass` sınıfı nesne tanımlayıcısı 1.3.36.2.1 eşlenir.</span><span class="sxs-lookup"><span data-stu-id="10a8d-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="10a8d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10a8d-127">See also</span></span>

- [<span data-ttu-id="10a8d-128">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="10a8d-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="10a8d-129">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="10a8d-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="10a8d-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="10a8d-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
