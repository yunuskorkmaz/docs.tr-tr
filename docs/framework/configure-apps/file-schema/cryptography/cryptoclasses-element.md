---
title: <cryptoClasses> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 7a03729f075645a230c660ff4c6469e0f5f3a51e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674785"
---
# <a name="cryptoclasses-element"></a><span data-ttu-id="220bc-102">\<cryptoClasses > öğesi</span><span class="sxs-lookup"><span data-stu-id="220bc-102">\<cryptoClasses> Element</span></span>
<span data-ttu-id="220bc-103">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="220bc-103">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="220bc-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="220bc-104">\<configuration></span></span>  
<span data-ttu-id="220bc-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="220bc-105">\<mscorlib></span></span>  
<span data-ttu-id="220bc-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="220bc-106">\<cryptographySettings></span></span>  
<span data-ttu-id="220bc-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="220bc-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="220bc-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="220bc-108">\<cryptoClasses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="220bc-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="220bc-109">Syntax</span></span>  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="220bc-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="220bc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="220bc-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="220bc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="220bc-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="220bc-112">Attributes</span></span>  
 <span data-ttu-id="220bc-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="220bc-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="220bc-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="220bc-114">Child Elements</span></span>  
  
|<span data-ttu-id="220bc-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="220bc-115">Element</span></span>|<span data-ttu-id="220bc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="220bc-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="220bc-117">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="220bc-117">\<cryptoClass></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="220bc-118">İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="220bc-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="220bc-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="220bc-119">Parent Elements</span></span>  
  
|<span data-ttu-id="220bc-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="220bc-120">Element</span></span>|<span data-ttu-id="220bc-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="220bc-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="220bc-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="220bc-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="220bc-123">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="220bc-123">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="220bc-124">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="220bc-124">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="220bc-125">İçeren `cryptographySettings` öğesi.</span><span class="sxs-lookup"><span data-stu-id="220bc-125">Contains the `cryptographySettings` element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="220bc-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="220bc-126">Example</span></span>  
 <span data-ttu-id="220bc-127">Aşağıdaki örnek nasıl kullanıldığını gösterir  **\<cryptoClass >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="220bc-127">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="220bc-128">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="220bc-128">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="220bc-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="220bc-129">See also</span></span>

- <xref:System.Security.Cryptography>
- [<span data-ttu-id="220bc-130">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="220bc-130">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="220bc-131">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="220bc-131">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="220bc-132">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="220bc-132">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="220bc-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span><span class="sxs-lookup"><span data-stu-id="220bc-133">System.Security.Cryptography.CryptoConfig.CreateFromName</span></span>](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [<span data-ttu-id="220bc-134">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="220bc-134">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
