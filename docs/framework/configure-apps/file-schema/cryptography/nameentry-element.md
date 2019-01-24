---
title: '&lt;nameEntry&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a4c29db3f84570d4d5e99a1deaf8beb3145c8ea1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626946"
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="e99a5-102">&lt;nameEntry&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="e99a5-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="e99a5-103">Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="e99a5-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="e99a5-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="e99a5-104">\<configuration></span></span>  
<span data-ttu-id="e99a5-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="e99a5-105">\<mscorlib></span></span>  
<span data-ttu-id="e99a5-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="e99a5-106">\<cryptographySettings></span></span>  
<span data-ttu-id="e99a5-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="e99a5-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="e99a5-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="e99a5-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e99a5-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e99a5-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e99a5-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e99a5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e99a5-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e99a5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e99a5-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e99a5-112">Attributes</span></span>  
  
|<span data-ttu-id="e99a5-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e99a5-113">Attribute</span></span>|<span data-ttu-id="e99a5-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e99a5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e99a5-115">**Adı**</span><span class="sxs-lookup"><span data-stu-id="e99a5-115">**name**</span></span>|<span data-ttu-id="e99a5-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e99a5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e99a5-117">Şifreleme sınıfına uygulayan algoritma kolay adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="e99a5-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="e99a5-118">**class**</span><span class="sxs-lookup"><span data-stu-id="e99a5-118">**class**</span></span>|<span data-ttu-id="e99a5-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="e99a5-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="e99a5-120">Değeri belirtir **adı** özniteliğini [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="e99a5-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e99a5-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e99a5-121">Child Elements</span></span>  
 <span data-ttu-id="e99a5-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e99a5-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e99a5-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e99a5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e99a5-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="e99a5-124">Element</span></span>|<span data-ttu-id="e99a5-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e99a5-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e99a5-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="e99a5-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="e99a5-127">ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e99a5-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e99a5-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e99a5-128">Remarks</span></span>  
 <span data-ttu-id="e99a5-129">**Adı** özniteliği bulunan soyut sınıflar birinin adı olabilir <xref:System.Security.Cryptography> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="e99a5-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="e99a5-130">Çağırdığınızda **Oluştur** bir soyut bir şifreleme sınıfına yönteminde, soyut sınıf adı için geçirilir <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e99a5-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="e99a5-131">**CreateFromName** tarafından belirtilen türün bir örneğini döndürür **sınıfı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e99a5-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="e99a5-132">Varsa **adı** kısa bir ad özniteliği olan RSA gibi bu adı çağırırken kullanabilirsiniz **CreateFromName** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e99a5-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99a5-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="e99a5-133">Example</span></span>  
 <span data-ttu-id="e99a5-134">Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<nameEntry >** bir şifreleme sınıfına başvurmak için ve çalışma zamanı yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e99a5-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="e99a5-135">Ardından "RSA" dize iletebileceğiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemini <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesne.</span><span class="sxs-lookup"><span data-stu-id="e99a5-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e99a5-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e99a5-136">See also</span></span>
- [<span data-ttu-id="e99a5-137">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="e99a5-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="e99a5-138">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e99a5-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [<span data-ttu-id="e99a5-139">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e99a5-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="e99a5-140">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e99a5-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
