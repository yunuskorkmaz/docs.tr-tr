---
title: '&lt;cryptoNameMapping&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ad1611701dca48244f3b2a93ecc3ea86363081ed
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170515"
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="ab9a1-102">&lt;cryptoNameMapping&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="ab9a1-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="ab9a1-103">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="ab9a1-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="ab9a1-104">\<configuration></span></span>  
<span data-ttu-id="ab9a1-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="ab9a1-105">\<mscorlib></span></span>  
<span data-ttu-id="ab9a1-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="ab9a1-106">\<cryptographySettings></span></span>  
<span data-ttu-id="ab9a1-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="ab9a1-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9a1-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab9a1-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab9a1-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab9a1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab9a1-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab9a1-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab9a1-111">Attributes</span></span>  
 <span data-ttu-id="ab9a1-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ab9a1-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab9a1-113">Child Elements</span></span>  
  
|<span data-ttu-id="ab9a1-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab9a1-114">Element</span></span>|<span data-ttu-id="ab9a1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab9a1-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="ab9a1-116">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="ab9a1-117">Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab9a1-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab9a1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ab9a1-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab9a1-119">Element</span></span>|<span data-ttu-id="ab9a1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab9a1-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ab9a1-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ab9a1-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ab9a1-123">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ab9a1-124">İçeren \<cryptographySettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ab9a1-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="ab9a1-125">Example</span></span>  
 <span data-ttu-id="ab9a1-126">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<cryptoNameMapping >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ab9a1-127">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ab9a1-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab9a1-128">See Also</span></span>  
 [<span data-ttu-id="ab9a1-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ab9a1-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ab9a1-130">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ab9a1-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="ab9a1-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ab9a1-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="ab9a1-132">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ab9a1-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
