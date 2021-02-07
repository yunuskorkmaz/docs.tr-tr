---
description: 'Daha fazla bilgi edinin: <nameEntry> öğesi'
title: <nameEntry> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 0ca227a2ba17a6b1e67fb75ec91aac9194b54737
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730011"
---
# <a name="nameentry-element"></a><span data-ttu-id="4a476-103">\<nameEntry> Öğesi</span><span class="sxs-lookup"><span data-stu-id="4a476-103">\<nameEntry> Element</span></span>

<span data-ttu-id="4a476-104">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="4a476-104">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameEntry>**  
  
## <a name="syntax"></a><span data-ttu-id="4a476-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a476-105">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a476-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a476-106">Attributes and Elements</span></span>  

 <span data-ttu-id="4a476-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4a476-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a476-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4a476-108">Attributes</span></span>  
  
|<span data-ttu-id="4a476-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4a476-109">Attribute</span></span>|<span data-ttu-id="4a476-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a476-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a476-111">**ada**</span><span class="sxs-lookup"><span data-stu-id="4a476-111">**name**</span></span>|<span data-ttu-id="4a476-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4a476-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="4a476-113">Şifreleme sınıfının uyguladığı algoritmanın kolay adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a476-113">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="4a476-114">**sınıfı**</span><span class="sxs-lookup"><span data-stu-id="4a476-114">**class**</span></span>|<span data-ttu-id="4a476-115">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="4a476-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="4a476-116">Öğesindeki **Name** özniteliği için değeri belirtir [\<cryptoClass>](cryptoclass-element.md) .</span><span class="sxs-lookup"><span data-stu-id="4a476-116">Specifies the value for the **name** attribute in the [\<cryptoClass>](cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a476-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a476-117">Child Elements</span></span>  

 <span data-ttu-id="4a476-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="4a476-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a476-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4a476-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4a476-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="4a476-120">Element</span></span>|<span data-ttu-id="4a476-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4a476-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4a476-122">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="4a476-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="4a476-123">ASP.NET yapılandırma bölümünün kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a476-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a476-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a476-124">Remarks</span></span>  

 <span data-ttu-id="4a476-125">**Ad** özniteliği ad alanında bulunan soyut sınıflardan birinin adı olabilir <xref:System.Security.Cryptography> .</span><span class="sxs-lookup"><span data-stu-id="4a476-125">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="4a476-126">Bir soyut şifreleme sınıfında **Create** yöntemini çağırdığınızda, soyut sınıf adı <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="4a476-126">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="4a476-127">**CreateFromName** , **sınıf** özniteliği tarafından belirtilen türün bir örneğini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4a476-127">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="4a476-128">**Ad** özniteliği RSA gibi kısa bir addır, **CreateFromName** metodunu çağırırken bu adı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a476-128">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a476-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="4a476-129">Example</span></span>  

 <span data-ttu-id="4a476-130">Aşağıdaki örnek, **\<nameEntry>** bir şifreleme sınıfına başvurmak ve çalışma zamanını yapılandırmak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4a476-130">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="4a476-131">Daha sonra "RSA" dizesini <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemine geçirebilir ve <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodunu kullanarak bir `MyCryptoRSAClass` nesne döndürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a476-131">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a476-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a476-132">See also</span></span>

- [<span data-ttu-id="4a476-133">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="4a476-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="4a476-134">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="4a476-134">Cryptography Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4a476-135">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="4a476-135">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
- [<span data-ttu-id="4a476-136">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4a476-136">Configuring Cryptography Classes</span></span>](../../configure-cryptography-classes.md)
