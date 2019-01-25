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
ms.openlocfilehash: ef916b0950e179f6782ce8d4d6fa380fd3804aa0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577173"
---
# <a name="ltcryptonamemappinggt-element"></a><span data-ttu-id="49f72-102">&lt;cryptoNameMapping&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="49f72-102">&lt;cryptoNameMapping&gt; Element</span></span>
<span data-ttu-id="49f72-103">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="49f72-103">Contains mappings of classes to friendly names.</span></span>  
  
 <span data-ttu-id="49f72-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="49f72-104">\<configuration></span></span>  
<span data-ttu-id="49f72-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="49f72-105">\<mscorlib></span></span>  
<span data-ttu-id="49f72-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="49f72-106">\<cryptographySettings></span></span>  
<span data-ttu-id="49f72-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="49f72-107">\<cryptoNameMapping></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f72-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49f72-108">Syntax</span></span>  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49f72-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49f72-109">Attributes and Elements</span></span>  
 <span data-ttu-id="49f72-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49f72-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49f72-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49f72-111">Attributes</span></span>  
 <span data-ttu-id="49f72-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="49f72-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="49f72-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49f72-113">Child Elements</span></span>  
  
|<span data-ttu-id="49f72-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="49f72-114">Element</span></span>|<span data-ttu-id="49f72-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49f72-115">Description</span></span>|  
|-------------|-----------------|  
|`cryptoClasses`|<span data-ttu-id="49f72-116">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="49f72-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|`nameEntry`|<span data-ttu-id="49f72-117">Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="49f72-117">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49f72-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49f72-118">Parent Elements</span></span>  
  
|<span data-ttu-id="49f72-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="49f72-119">Element</span></span>|<span data-ttu-id="49f72-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49f72-120">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="49f72-121">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="49f72-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="49f72-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="49f72-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="49f72-123">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="49f72-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="49f72-124">İçeren \<cryptographySettings > öğesi.</span><span class="sxs-lookup"><span data-stu-id="49f72-124">Contains the \<cryptographySettings> element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="49f72-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="49f72-125">Example</span></span>  
 <span data-ttu-id="49f72-126">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<cryptoNameMapping >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="49f72-126">The following example shows how to use the **\<cryptoNameMapping>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="49f72-127">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="49f72-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49f72-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49f72-128">See also</span></span>
- [<span data-ttu-id="49f72-129">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="49f72-129">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="49f72-130">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="49f72-130">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="49f72-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="49f72-131">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="49f72-132">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="49f72-132">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
