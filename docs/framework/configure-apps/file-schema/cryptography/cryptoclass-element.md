---
title: <cryptoClass> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: c8076fba1ebae693aa5e4c80e822b9ae840ff1c5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664331"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="ec0c8-102">\<cryptoClass > öğesi</span><span class="sxs-lookup"><span data-stu-id="ec0c8-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="ec0c8-103">NameEntry > öğesinde kolay bir ad [ \<](nameentry-element.md) ile eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="ec0c8-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="ec0c8-104">\<configuration></span></span>  
<span data-ttu-id="ec0c8-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="ec0c8-105">\<mscorlib></span></span>  
<span data-ttu-id="ec0c8-106">\<Cryptographyısettings ></span><span class="sxs-lookup"><span data-stu-id="ec0c8-106">\<cryptographySettings></span></span>  
<span data-ttu-id="ec0c8-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="ec0c8-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="ec0c8-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="ec0c8-108">\<cryptoClasses></span></span>  
<span data-ttu-id="ec0c8-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="ec0c8-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec0c8-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ec0c8-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec0c8-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec0c8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="ec0c8-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec0c8-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ec0c8-113">Attributes</span></span>  
  
|<span data-ttu-id="ec0c8-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ec0c8-114">Attribute</span></span>|<span data-ttu-id="ec0c8-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec0c8-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="ec0c8-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="ec0c8-117">Şifreleme sınıfıyla ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="ec0c8-118">Sınıfınız için kısa bir ad sağlamak üzere bu özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="ec0c8-119">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ec0c8-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec0c8-120">Child Elements</span></span>  
 <span data-ttu-id="ec0c8-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec0c8-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ec0c8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ec0c8-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="ec0c8-123">Element</span></span>|<span data-ttu-id="ec0c8-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ec0c8-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ec0c8-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="ec0c8-126">NameEntry > öğesinde kolay bir ada [ \<](nameentry-element.md) eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ec0c8-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ec0c8-128">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ec0c8-129">Cryptographrivsettings > öğesini içerir. [ \<](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="ec0c8-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ec0c8-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec0c8-130">Example</span></span>  
 <span data-ttu-id="ec0c8-131">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için  **\<CryptoClass >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ec0c8-132">Daha sonra "RSA" <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> dizesini yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec0c8-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec0c8-133">See also</span></span>

- [<span data-ttu-id="ec0c8-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="ec0c8-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ec0c8-135">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ec0c8-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ec0c8-136">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ec0c8-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="ec0c8-137">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ec0c8-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
