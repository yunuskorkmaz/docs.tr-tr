---
description: 'Daha fazla bilgi edinin: <cryptoClass> öğesi'
title: <cryptoClass> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass
helpviewer_keywords:
- cryptoClass element
- <cryptoClass> element
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
ms.openlocfilehash: 503a079ea78a71a11e4c750a629cf67c9244a25d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698946"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="9f4cf-103">\<cryptoClass> Öğesi</span><span class="sxs-lookup"><span data-stu-id="9f4cf-103">\<cryptoClass> Element</span></span>

<span data-ttu-id="9f4cf-104">Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9f4cf-104">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="9f4cf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9f4cf-105">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f4cf-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f4cf-106">Attributes and Elements</span></span>  

 <span data-ttu-id="9f4cf-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f4cf-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9f4cf-108">Attributes</span></span>  
  
|<span data-ttu-id="9f4cf-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9f4cf-109">Attribute</span></span>|<span data-ttu-id="9f4cf-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f4cf-110">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="9f4cf-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="9f4cf-112">Şifreleme sınıfıyla ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-112">Contains the information for the cryptography class.</span></span> <span data-ttu-id="9f4cf-113">Sınıfınız için kısa bir ad sağlamak üzere bu özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-113">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="9f4cf-114">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-114">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f4cf-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f4cf-115">Child Elements</span></span>  

 <span data-ttu-id="9f4cf-116">Yok.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f4cf-117">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9f4cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9f4cf-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="9f4cf-118">Element</span></span>|<span data-ttu-id="9f4cf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f4cf-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9f4cf-120">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="9f4cf-121">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9f4cf-121">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="9f4cf-122">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-122">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="9f4cf-123">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-123">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="9f4cf-124">Öğesini içerir [\<cryptographySettings>](cryptographysettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="9f4cf-124">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9f4cf-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f4cf-125">Example</span></span>  

 <span data-ttu-id="9f4cf-126">Aşağıdaki örnek, **\<cryptoClass>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-126">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="9f4cf-127">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-127">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f4cf-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f4cf-128">See also</span></span>

- [<span data-ttu-id="9f4cf-129">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="9f4cf-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="9f4cf-130">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="9f4cf-130">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9f4cf-131">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="9f4cf-131">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="9f4cf-132">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="9f4cf-132">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
