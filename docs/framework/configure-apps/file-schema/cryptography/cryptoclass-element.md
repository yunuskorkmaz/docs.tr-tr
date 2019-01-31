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
ms.openlocfilehash: 161c9212600a417a97fa5a4e0edeac02db0f17a1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287540"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="af470-102">\<cryptoClass > öğesi</span><span class="sxs-lookup"><span data-stu-id="af470-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="af470-103">İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="af470-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="af470-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="af470-104">\<configuration></span></span>  
<span data-ttu-id="af470-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="af470-105">\<mscorlib></span></span>  
<span data-ttu-id="af470-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="af470-106">\<cryptographySettings></span></span>  
<span data-ttu-id="af470-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="af470-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="af470-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="af470-108">\<cryptoClasses></span></span>  
<span data-ttu-id="af470-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="af470-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af470-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af470-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af470-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="af470-111">Attributes and Elements</span></span>  
 <span data-ttu-id="af470-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af470-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af470-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="af470-113">Attributes</span></span>  
  
|<span data-ttu-id="af470-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="af470-114">Attribute</span></span>|<span data-ttu-id="af470-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af470-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="af470-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="af470-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="af470-117">Şifreleme sınıfı için bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="af470-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="af470-118">Bu öznitelik, sınıfınız için kısa bir ad vermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="af470-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="af470-119">Belirtilen gereksinimleri karşılayan bir dize belirtmelisiniz [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="af470-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af470-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="af470-120">Child Elements</span></span>  
 <span data-ttu-id="af470-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="af470-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af470-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="af470-122">Parent Elements</span></span>  
  
|<span data-ttu-id="af470-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="af470-123">Element</span></span>|<span data-ttu-id="af470-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af470-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="af470-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="af470-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="af470-126">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="af470-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="af470-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="af470-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="af470-128">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="af470-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="af470-129">İçeren [ \<cryptographySettings >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="af470-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="af470-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="af470-130">Example</span></span>  
 <span data-ttu-id="af470-131">Aşağıdaki örnek nasıl kullanıldığını gösterir  **\<cryptoClass >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="af470-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="af470-132">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="af470-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af470-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af470-133">See also</span></span>
- [<span data-ttu-id="af470-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="af470-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="af470-135">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="af470-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="af470-136">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="af470-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="af470-137">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="af470-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
