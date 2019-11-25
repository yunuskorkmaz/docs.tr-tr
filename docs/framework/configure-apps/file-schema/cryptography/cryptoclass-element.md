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
ms.openlocfilehash: 4872fbd6fa043902e8c69f158bee5d0c915ec83a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088655"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="6b5b4-102">\<cryptoClass > öğesi</span><span class="sxs-lookup"><span data-stu-id="6b5b4-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="6b5b4-103">[\<nameEntry >](nameentry-element.md) öğesinde kolay bir ad ile eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

<span data-ttu-id="6b5b4-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6b5b4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b5b4-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6b5b4-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="6b5b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Cryptographyısettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b5b4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="6b5b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b5b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="6b5b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b5b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="6b5b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="6b5b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6b5b4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b5b4-110">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b5b4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b5b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6b5b4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b5b4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6b5b4-113">Attributes</span></span>  
  
|<span data-ttu-id="6b5b4-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="6b5b4-114">Attribute</span></span>|<span data-ttu-id="6b5b4-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b5b4-115">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="6b5b4-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="6b5b4-117">Şifreleme sınıfıyla ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-117">Contains the information for the cryptography class.</span></span> <span data-ttu-id="6b5b4-118">Sınıfınız için kısa bir ad sağlamak üzere bu özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-118">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="6b5b4-119">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-119">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b5b4-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b5b4-120">Child Elements</span></span>  
 <span data-ttu-id="6b5b4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b5b4-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6b5b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="6b5b4-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="6b5b4-123">Element</span></span>|<span data-ttu-id="6b5b4-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b5b4-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6b5b4-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="6b5b4-126">[\<nameEntry >](nameentry-element.md) öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-126">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="6b5b4-127">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-127">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="6b5b4-128">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-128">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="6b5b4-129">[\<Cryptographyısettings >](cryptographysettings-element.md) öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-129">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6b5b4-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="6b5b4-130">Example</span></span>  
 <span data-ttu-id="6b5b4-131">Aşağıdaki örnek, bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için **\<cryptoClass >** öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-131">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="6b5b4-132">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve bir `MyCryptoRSAClass` nesnesi döndürmek için <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-132">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b5b4-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b5b4-133">See also</span></span>

- [<span data-ttu-id="6b5b4-134">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="6b5b4-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6b5b4-135">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6b5b4-135">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6b5b4-136">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6b5b4-136">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="6b5b4-137">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6b5b4-137">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
