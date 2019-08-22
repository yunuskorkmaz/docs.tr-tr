---
title: <cryptographySettings> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: 572a5856c9f92f105e727df1ecd8eb2e0a92fc09
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664276"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="91612-102">\<Cryptographyısettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="91612-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="91612-103">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="91612-103">Contains cryptography settings.</span></span>  
  
 <span data-ttu-id="91612-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="91612-104">\<configuration></span></span>  
<span data-ttu-id="91612-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="91612-105">\<mscorlib></span></span>  
<span data-ttu-id="91612-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="91612-106">\<cryptographySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91612-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91612-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91612-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="91612-108">Attributes and Elements</span></span>  
 <span data-ttu-id="91612-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="91612-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91612-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="91612-110">Attributes</span></span>  
 <span data-ttu-id="91612-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="91612-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91612-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="91612-112">Child Elements</span></span>  
  
|<span data-ttu-id="91612-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="91612-113">Element</span></span>|<span data-ttu-id="91612-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91612-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91612-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="91612-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="91612-116">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="91612-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="91612-117">\<Oıdmap ></span><span class="sxs-lookup"><span data-stu-id="91612-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="91612-118">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="91612-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91612-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="91612-119">Parent Elements</span></span>  
  
|<span data-ttu-id="91612-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="91612-120">Element</span></span>|<span data-ttu-id="91612-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91612-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="91612-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="91612-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="91612-123">`cryptographySettings` Öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="91612-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="91612-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="91612-124">Example</span></span>  
 <span data-ttu-id="91612-125">Aşağıdaki örnek, şifreleme adı eşlemelerini ve OID eşlemelerini içermek için  **\<cryptographısettings >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91612-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="91612-126">Bu örnek, çalışma zamanını bir <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> `MyHashClass` nesne döndüren ve `MyCryptoClass` sınıfı 1.3.36.2.1 nesne tanımlayıcısına eşlenecek şekilde yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="91612-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91612-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91612-127">See also</span></span>

- [<span data-ttu-id="91612-128">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="91612-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="91612-129">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="91612-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="91612-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="91612-130">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
