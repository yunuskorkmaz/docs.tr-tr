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
ms.openlocfilehash: da78140806ab8dbe7b7cb5e321e82755774ff25d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103824"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="8403f-102">\<cryptoClass > öğesi</span><span class="sxs-lookup"><span data-stu-id="8403f-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="8403f-103">İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8403f-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>  
  
 <span data-ttu-id="8403f-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="8403f-104">\<configuration></span></span>  
<span data-ttu-id="8403f-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="8403f-105">\<mscorlib></span></span>  
<span data-ttu-id="8403f-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="8403f-106">\<cryptographySettings></span></span>  
<span data-ttu-id="8403f-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="8403f-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="8403f-108">\<cryptoClasses ></span><span class="sxs-lookup"><span data-stu-id="8403f-108">\<cryptoClasses></span></span>  
<span data-ttu-id="8403f-109">\<cryptoClass ></span><span class="sxs-lookup"><span data-stu-id="8403f-109">\<cryptoClass></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8403f-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8403f-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8403f-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8403f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8403f-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8403f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8403f-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8403f-113">Attributes</span></span>  
  
|<span data-ttu-id="8403f-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8403f-114">Attribute</span></span>|<span data-ttu-id="8403f-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8403f-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="8403f-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="8403f-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="8403f-117">Şifreleme sınıfı için bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="8403f-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="8403f-118">Bu öznitelik, sınıfınız için kısa bir ad vermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8403f-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="8403f-119">Belirtilen gereksinimleri karşılayan bir dize belirtmelisiniz [belirtme tam olarak nitelenmiş tür adlarını](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="8403f-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8403f-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8403f-120">Child Elements</span></span>  
 <span data-ttu-id="8403f-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="8403f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8403f-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8403f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8403f-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="8403f-123">Element</span></span>|<span data-ttu-id="8403f-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8403f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8403f-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="8403f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="8403f-126">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8403f-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="8403f-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8403f-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="8403f-128">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8403f-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="8403f-129">İçeren [ \<cryptographySettings >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="8403f-129">Contains the [\<cryptographySettings>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8403f-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8403f-130">Example</span></span>  
 <span data-ttu-id="8403f-131">Aşağıdaki örnek nasıl kullanıldığını gösterir  **\<cryptoClass >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="8403f-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="8403f-132">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="8403f-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8403f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8403f-133">See also</span></span>

- [<span data-ttu-id="8403f-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="8403f-134">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="8403f-135">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="8403f-135">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="8403f-136">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="8403f-136">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="8403f-137">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8403f-137">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
