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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088655"
---
# <a name="cryptoclass-element"></a><span data-ttu-id="ac37f-102">\<cryptoClass> Öğesi</span><span class="sxs-lookup"><span data-stu-id="ac37f-102">\<cryptoClass> Element</span></span>
<span data-ttu-id="ac37f-103">Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ac37f-103">Contains a cryptography class that has a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<cryptoClass>**

## <a name="syntax"></a><span data-ttu-id="ac37f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac37f-104">Syntax</span></span>  
  
```xml  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac37f-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac37f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ac37f-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ac37f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac37f-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ac37f-107">Attributes</span></span>  
  
|<span data-ttu-id="ac37f-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ac37f-108">Attribute</span></span>|<span data-ttu-id="ac37f-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac37f-109">Description</span></span>|  
|---------------|-----------------|  
|`customClassName`|<span data-ttu-id="ac37f-110">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="ac37f-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ac37f-111">Şifreleme sınıfıyla ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="ac37f-111">Contains the information for the cryptography class.</span></span> <span data-ttu-id="ac37f-112">Sınıfınız için kısa bir ad sağlamak üzere bu özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="ac37f-112">Use this attribute to provide a short name for your class.</span></span> <span data-ttu-id="ac37f-113">[Tam nitelikli tür adlarını belirtirken](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)belirtilen gereksinimleri karşılayan bir dize belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ac37f-113">You must specify a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac37f-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac37f-114">Child Elements</span></span>  
 <span data-ttu-id="ac37f-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="ac37f-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac37f-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ac37f-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ac37f-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ac37f-117">Element</span></span>|<span data-ttu-id="ac37f-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac37f-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ac37f-119">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="ac37f-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`cryptoClasses`|<span data-ttu-id="ac37f-120">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir [\<nameEntry>](nameentry-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ac37f-120">Contains a list of cryptography classes that have a mapping to a friendly name in the [\<nameEntry>](nameentry-element.md) element.</span></span>|  
|`cryptographySettings`|<span data-ttu-id="ac37f-121">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ac37f-121">Contains cryptography settings.</span></span>|  
|`cryptoNameMapping`|<span data-ttu-id="ac37f-122">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ac37f-122">Contains mappings of classes to friendly names.</span></span>|  
|`mscorlib`|<span data-ttu-id="ac37f-123">Öğesini içerir [\<cryptographySettings>](cryptographysettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="ac37f-123">Contains the [\<cryptographySettings>](cryptographysettings-element.md) element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ac37f-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac37f-124">Example</span></span>  
 <span data-ttu-id="ac37f-125">Aşağıdaki örnek, **\<cryptoClass>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ac37f-125">The following example shows how use the **\<cryptoClass>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="ac37f-126">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac37f-126">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ac37f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac37f-127">See also</span></span>

- [<span data-ttu-id="ac37f-128">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ac37f-128">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ac37f-129">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ac37f-129">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ac37f-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ac37f-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="ac37f-131">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ac37f-131">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
