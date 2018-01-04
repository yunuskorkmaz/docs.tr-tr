---
title: "&lt;cryptographySettings&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 73a4f362be1612658e6911b7e7ea7a6c3e670e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptographysettingsgt-element"></a><span data-ttu-id="20fb4-102">&lt;cryptographySettings&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="20fb4-102">&lt;cryptographySettings&gt; Element</span></span>
<span data-ttu-id="20fb4-103">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="20fb4-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="20fb4-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="20fb4-104">\<configuration></span></span>  
<span data-ttu-id="20fb4-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="20fb4-105">\<mscorlib></span></span>  
<span data-ttu-id="20fb4-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="20fb4-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fb4-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20fb4-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20fb4-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="20fb4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="20fb4-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="20fb4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20fb4-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="20fb4-110">Attributes</span></span>  
 <span data-ttu-id="20fb4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="20fb4-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="20fb4-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="20fb4-112">Child Elements</span></span>  
  
|<span data-ttu-id="20fb4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="20fb4-113">Element</span></span>|<span data-ttu-id="20fb4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20fb4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20fb4-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="20fb4-115">\<cryptoNameMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="20fb4-116">Kolay adlar sınıflarına eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="20fb4-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="20fb4-117">\<oidMap ></span><span class="sxs-lookup"><span data-stu-id="20fb4-117">\<oidMap></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="20fb4-118">ASN.1 nesne tanımlayıcısı (OID) eşlemeleri sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="20fb4-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="20fb4-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="20fb4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="20fb4-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="20fb4-120">Element</span></span>|<span data-ttu-id="20fb4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="20fb4-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="20fb4-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="20fb4-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="20fb4-123">İçeren `cryptographySettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="20fb4-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="20fb4-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="20fb4-124">Example</span></span>  
 <span data-ttu-id="20fb4-125">Aşağıdaki örnekte nasıl kullanıldığını gösterir  **\<cryptographySettings >** şifreleme adı eşlemeleri ve OID eşlemelerini içeren öğe.</span><span class="sxs-lookup"><span data-stu-id="20fb4-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="20fb4-126">Bu örnek çalışma zamanı yapılandırır böylece <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> döndürür bir `MyHashClass` nesne ve `MyCryptoClass` sınıfının nesne tanımlayıcısı 1.3.36.2.1 eşlenir.</span><span class="sxs-lookup"><span data-stu-id="20fb4-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20fb4-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20fb4-127">See Also</span></span>  
 [<span data-ttu-id="20fb4-128">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="20fb4-128">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="20fb4-129">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="20fb4-129">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="20fb4-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="20fb4-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
