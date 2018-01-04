---
title: "&lt;cryptoNameMapping&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b0ddd8368b84ec1b218f2c48fddd898f83fc71fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="5e935-102">&lt;cryptoNameMapping&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="5e935-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="5e935-103">Kolay adlar sınıflarına eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5e935-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="5e935-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="5e935-104">\<configuration></span></span>  
<span data-ttu-id="5e935-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="5e935-105">\<mscorlib></span></span>  
<span data-ttu-id="5e935-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="5e935-106">\<cryptographySettings></span></span>  
<span data-ttu-id="5e935-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="5e935-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e935-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e935-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e935-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e935-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e935-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e935-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e935-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e935-111">Attributes</span></span>  
 <span data-ttu-id="5e935-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e935-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5e935-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e935-113">Child Elements</span></span>  
  
|<span data-ttu-id="5e935-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e935-114">Element</span></span>|<span data-ttu-id="5e935-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e935-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="5e935-116">Bir kolay ad eşlemeye sahip şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="5e935-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="5e935-117">Çok sayıda kolay adlar sağlamak bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="5e935-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e935-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e935-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5e935-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e935-119">Element</span></span>|<span data-ttu-id="5e935-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e935-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5e935-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="5e935-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="5e935-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5e935-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="5e935-123">Kolay adlar sınıflarına eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5e935-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="5e935-124">İçeren \<cryptographySettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="5e935-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5e935-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e935-125">Example</span></span>  
 <span data-ttu-id="5e935-126">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<cryptoNameMapping >** öğesi bir şifreleme sınıf başvurusu ve çalışma zamanı yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="5e935-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="5e935-127">Ardından "RSA" dizesi geçirebilirsiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemi ve kullanım <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5e935-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5e935-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e935-128">See Also</span></span>  
 [<span data-ttu-id="5e935-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="5e935-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="5e935-130">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5e935-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="5e935-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5e935-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="5e935-132">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5e935-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
