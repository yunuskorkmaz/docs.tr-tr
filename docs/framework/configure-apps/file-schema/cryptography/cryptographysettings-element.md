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
ms.openlocfilehash: 96a8c9accc56274b5cc13dc2a871165857b3a2d9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699818"
---
# <a name="cryptographysettings-element"></a><span data-ttu-id="cb996-102">\<Cryptographyısettings > öğesi</span><span class="sxs-lookup"><span data-stu-id="cb996-102">\<cryptographySettings> Element</span></span>
<span data-ttu-id="cb996-103">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cb996-103">Contains cryptography settings.</span></span>  
  
[<span data-ttu-id="cb996-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="cb996-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cb996-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cb996-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="cb996-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<Cryptographrivsettings >**</span><span class="sxs-lookup"><span data-stu-id="cb996-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptographySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb996-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb996-107">Syntax</span></span>  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb996-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb996-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cb996-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb996-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb996-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb996-110">Attributes</span></span>  
 <span data-ttu-id="cb996-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb996-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cb996-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb996-112">Child Elements</span></span>  
  
|<span data-ttu-id="cb996-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb996-113">Element</span></span>|<span data-ttu-id="cb996-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb996-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb996-115">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="cb996-115">\<cryptoNameMapping></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="cb996-116">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb996-116">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="cb996-117">\<Oıdmap ></span><span class="sxs-lookup"><span data-stu-id="cb996-117">\<oidMap></span></span>](oidmap-element.md)|<span data-ttu-id="cb996-118">Sınıflara ASN. 1 nesne tanımlayıcısı (OID) eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cb996-118">Contains ASN.1 object identifier (OID) mappings to classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cb996-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb996-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cb996-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb996-120">Element</span></span>|<span data-ttu-id="cb996-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb996-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="cb996-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="cb996-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`mscorlib`|<span data-ttu-id="cb996-123">@No__t-0 öğesi içerir.</span><span class="sxs-lookup"><span data-stu-id="cb996-123">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb996-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb996-124">Example</span></span>  
 <span data-ttu-id="cb996-125">Aşağıdaki örnek, **\<Cryptographyısettings >** öğesinin şifreleme adı EŞLEMELERINI ve OID eşlemelerini nasıl kullandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb996-125">The following example shows how use the **\<cryptographySettings>** element to contain cryptography name mappings and OID mappings.</span></span> <span data-ttu-id="cb996-126">Bu örnek, <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> `MyHashClass` nesnesi ve `MyCryptoClass` sınıfı 1.3.36.2.1 nesne tanımlayıcısına eşlenecek şekilde çalışma zamanını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="cb996-126">This example configures the runtime so that <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> returns a `MyHashClass` object and the `MyCryptoClass` class maps to the object identifier 1.3.36.2.1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb996-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb996-127">See also</span></span>

- [<span data-ttu-id="cb996-128">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="cb996-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cb996-129">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cb996-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cb996-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cb996-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
