---
title: "&lt;nameEntry&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 507c71b5c13deeb7c1a81b6a4dd9604c3bd919f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnameentrygt-element"></a><span data-ttu-id="434fa-102">&lt;nameEntry&gt; öğesi</span><span class="sxs-lookup"><span data-stu-id="434fa-102">&lt;nameEntry&gt; Element</span></span>
<span data-ttu-id="434fa-103">Çok sayıda kolay adlar sağlamak bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="434fa-103">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>  
  
 <span data-ttu-id="434fa-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="434fa-104">\<configuration></span></span>  
<span data-ttu-id="434fa-105">\<mscorlib ></span><span class="sxs-lookup"><span data-stu-id="434fa-105">\<mscorlib></span></span>  
<span data-ttu-id="434fa-106">\<cryptographySettings ></span><span class="sxs-lookup"><span data-stu-id="434fa-106">\<cryptographySettings></span></span>  
<span data-ttu-id="434fa-107">\<cryptoNameMapping ></span><span class="sxs-lookup"><span data-stu-id="434fa-107">\<cryptoNameMapping></span></span>  
<span data-ttu-id="434fa-108">\<nameEntry ></span><span class="sxs-lookup"><span data-stu-id="434fa-108">\<nameEntry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="434fa-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="434fa-109">Syntax</span></span>  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="434fa-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="434fa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="434fa-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="434fa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="434fa-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="434fa-112">Attributes</span></span>  
  
|<span data-ttu-id="434fa-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="434fa-113">Attribute</span></span>|<span data-ttu-id="434fa-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="434fa-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="434fa-115">**adı**</span><span class="sxs-lookup"><span data-stu-id="434fa-115">**name**</span></span>|<span data-ttu-id="434fa-116">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="434fa-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="434fa-117">Şifreleme sınıfı uygulayan algoritması kolay adı belirtir.</span><span class="sxs-lookup"><span data-stu-id="434fa-117">Specifies the friendly name of the algorithm that the cryptography class implements.</span></span>|  
|<span data-ttu-id="434fa-118">**sınıfı**</span><span class="sxs-lookup"><span data-stu-id="434fa-118">**class**</span></span>|<span data-ttu-id="434fa-119">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="434fa-119">Required attribute.</span></span><br /><br /> <span data-ttu-id="434fa-120">Değerini belirtir **adı** özniteliğini [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) öğesi.</span><span class="sxs-lookup"><span data-stu-id="434fa-120">Specifies the value for the **name** attribute in the [\<cryptoClass>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="434fa-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="434fa-121">Child Elements</span></span>  
 <span data-ttu-id="434fa-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="434fa-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="434fa-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="434fa-123">Parent Elements</span></span>  
  
|<span data-ttu-id="434fa-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="434fa-124">Element</span></span>|<span data-ttu-id="434fa-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="434fa-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="434fa-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="434fa-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.web`|<span data-ttu-id="434fa-127">ASP.NET yapılandırma bölümü için kök öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="434fa-127">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="434fa-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="434fa-128">Remarks</span></span>  
 <span data-ttu-id="434fa-129">**Adı** özniteliği bulunan soyut sınıflar birinin adını olabilir <xref:System.Security.Cryptography> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="434fa-129">The **name** attribute can be the name of one of the abstract classes found in the <xref:System.Security.Cryptography> namespace.</span></span> <span data-ttu-id="434fa-130">Çağırdığınızda **oluşturma** yöntemi bir soyut şifreleme sınıf üzerinde soyut sınıf adı için geçirilir <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="434fa-130">When you call the **Create** method on an abstract cryptography class, the abstract class name is passed to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> method.</span></span> <span data-ttu-id="434fa-131">**CreateFromName** tarafından gösterilen türünün bir örneği döndürür **sınıfı** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="434fa-131">**CreateFromName** returns an instance of the type indicated by the **class** attribute.</span></span> <span data-ttu-id="434fa-132">Varsa **adı** özniteliktir kısa bir ad RSA gibi bu adı çağrılırken kullanabilirsiniz **CreateFromName** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="434fa-132">If the **name** attribute is a short name, such as RSA, you can use that name when calling the **CreateFromName** method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="434fa-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="434fa-133">Example</span></span>  
 <span data-ttu-id="434fa-134">Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<nameEntry >** öğesi bir şifreleme sınıf başvurusu ve çalışma zamanı yapılandırmak için.</span><span class="sxs-lookup"><span data-stu-id="434fa-134">The following example shows how to use the **\<nameEntry>** element to reference a cryptography class and to configure the runtime.</span></span> <span data-ttu-id="434fa-135">Ardından "RSA" dizesi geçirebilirsiniz <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> yöntemi ve kullanım <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> döndürülecek yöntemi bir `MyCryptoRSAClass` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="434fa-135">You can then pass the string "RSA" to the <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> method and use the <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> method to return a `MyCryptoRSAClass` object.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="434fa-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="434fa-136">See Also</span></span>  
 [<span data-ttu-id="434fa-137">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="434fa-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="434fa-138">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="434fa-138">Cryptography Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [<span data-ttu-id="434fa-139">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="434fa-139">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)  
 [<span data-ttu-id="434fa-140">Şifreleme sınıflarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="434fa-140">Configuring Cryptography Classes</span></span>](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
