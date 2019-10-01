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
ms.openlocfilehash: 45d2da22a7c3486d4c7a638e92d1f3fce6f9883c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699710"
---
# <a name="cryptonamemapping-element"></a><span data-ttu-id="3f8bf-102">\<cryptoNameMapping > öğesi</span><span class="sxs-lookup"><span data-stu-id="3f8bf-102">\<cryptoNameMapping> Element</span></span>
<span data-ttu-id="3f8bf-103">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-103">Contains mappings of classes to friendly names.</span></span>  
  
[<span data-ttu-id="3f8bf-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="3f8bf-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3f8bf-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3f8bf-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="3f8bf-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<Cryptographrivsettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="3f8bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="3f8bf-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="3f8bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoNameMapping>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f8bf-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f8bf-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f8bf-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f8bf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f8bf-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f8bf-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f8bf-111">Attributes</span></span>  
 <span data-ttu-id="3f8bf-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f8bf-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f8bf-113">Child Elements</span></span>  
  
|<span data-ttu-id="3f8bf-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f8bf-114">Element</span></span>|<span data-ttu-id="3f8bf-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f8bf-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="3f8bf-116">**@No__t-1nameEntry >** öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="3f8bf-117">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f8bf-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f8bf-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3f8bf-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f8bf-119">Element</span></span>|<span data-ttu-id="3f8bf-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f8bf-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3f8bf-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="3f8bf-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="3f8bf-123">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="3f8bf-124">@No__t-0Cryptographyısettings > öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3f8bf-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f8bf-125">Example</span></span>  
 <span data-ttu-id="3f8bf-126">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için **\<cryptoNameMapping >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="3f8bf-127">Daha sonra, "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak `MyCryptoRSAClass` nesnesini döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3f8bf-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f8bf-128">See also</span></span>

- [<span data-ttu-id="3f8bf-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3f8bf-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3f8bf-130">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3f8bf-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3f8bf-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3f8bf-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="3f8bf-132">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3f8bf-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
