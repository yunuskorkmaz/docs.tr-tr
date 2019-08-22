---
title: <cryptoNameMapping> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: c2652ac73c1d55f09a1f8511603003dc6d7291f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659636"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="edeb0-102">\<cryptoNameMapping > öğesi</span><span class="sxs-lookup"><span data-stu-id="edeb0-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="edeb0-103">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="edeb0-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="edeb0-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="edeb0-104">\<configuration></span></span>  
<span data-ttu-id="edeb0-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="edeb0-105">\<mscorlib></span></span>  
<span data-ttu-id="edeb0-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="edeb0-106">\<cryptographySettings></span></span>  
<span data-ttu-id="edeb0-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="edeb0-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edeb0-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edeb0-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edeb0-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="edeb0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="edeb0-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="edeb0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edeb0-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="edeb0-111">Attributes</span></span>  
 <span data-ttu-id="edeb0-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="edeb0-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="edeb0-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="edeb0-113">Child Elements</span></span>  
  
|<span data-ttu-id="edeb0-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="edeb0-114">Element</span></span>|<span data-ttu-id="edeb0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edeb0-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="edeb0-116">NameEntry > öğesinde kolay bir ada  **\<** eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="edeb0-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="edeb0-117">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="edeb0-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="edeb0-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="edeb0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="edeb0-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="edeb0-119">Element</span></span>|<span data-ttu-id="edeb0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="edeb0-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="edeb0-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="edeb0-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="edeb0-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="edeb0-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="edeb0-123">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="edeb0-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="edeb0-124">\<Cryptographrivsettings > öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="edeb0-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="edeb0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="edeb0-125">Example</span></span>  
 <span data-ttu-id="edeb0-126">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için  **\<cryptoNameMapping >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="edeb0-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="edeb0-127">Daha sonra "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> dizesini yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="edeb0-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edeb0-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edeb0-128">See also</span></span>

- [<span data-ttu-id="edeb0-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="edeb0-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="edeb0-130">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="edeb0-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="edeb0-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="edeb0-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="edeb0-132">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="edeb0-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
