---
title: <enforceFIPSPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 0d6dd291a24928487a040c0427f058dee80bf836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117380"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="bd786-102">\<enforceFIPSPolicy > öğesi</span><span class="sxs-lookup"><span data-stu-id="bd786-102">\<enforceFIPSPolicy> Element</span></span>
<span data-ttu-id="bd786-103">Şifreleme algoritmalarının Federal bilgi Işleme standartları (FIPS) ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlayamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd786-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
<span data-ttu-id="bd786-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bd786-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bd786-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="bd786-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="bd786-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<enforceFIPSPolicy >**</span><span class="sxs-lookup"><span data-stu-id="bd786-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd786-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd786-107">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd786-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd786-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bd786-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bd786-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd786-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bd786-110">Attributes</span></span>  
  
|<span data-ttu-id="bd786-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd786-111">Attribute</span></span>|<span data-ttu-id="bd786-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd786-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd786-113">etkinletir</span><span class="sxs-lookup"><span data-stu-id="bd786-113">enabled</span></span>|<span data-ttu-id="bd786-114">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="bd786-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="bd786-115">Şifreleme algoritmalarının FIPS ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlamasının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bd786-115">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="bd786-116">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bd786-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="bd786-117">Değer</span><span class="sxs-lookup"><span data-stu-id="bd786-117">Value</span></span>|<span data-ttu-id="bd786-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd786-118">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="bd786-119">Bilgisayarınız, şifreleme algoritmalarının FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırıldıysa, bu gereksinim zorlanır.</span><span class="sxs-lookup"><span data-stu-id="bd786-119">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="bd786-120">Bir sınıf FIPS ile uyumlu olmayan bir algoritma uygularsa, bu sınıf için oluşturucular veya `Create` yöntemleri, bu bilgisayarda çalıştıklarında özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd786-120">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="bd786-121">Bu varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="bd786-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="bd786-122">Uygulama tarafından kullanılan şifreleme algoritmalarının, bilgisayar yapılandırmasına bakılmaksızın FIPS ile uyumlu olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bd786-122">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd786-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd786-123">Child Elements</span></span>  
 <span data-ttu-id="bd786-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="bd786-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd786-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bd786-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bd786-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="bd786-126">Element</span></span>|<span data-ttu-id="bd786-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd786-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="bd786-128">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="bd786-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="bd786-129">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="bd786-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd786-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bd786-130">Remarks</span></span>  
 <span data-ttu-id="bd786-131">2,0 .NET Framework başlayarak, şifreleme algoritmaları uygulayan sınıfların oluşturulması bilgisayarın yapılandırmasıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="bd786-131">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="bd786-132">Bilgisayar algoritmaların FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırıldıysa ve bir sınıf FIPS ile uyumlu olmayan bir algoritma uygularsa, bu sınıfın bir örneğini oluşturma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd786-132">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="bd786-133">Oluşturucular <xref:System.InvalidOperationException> bir özel durum oluşturur ve `Create` Yöntemler bir iç <xref:System.InvalidOperationException> özel durumuyla <xref:System.Reflection.TargetInvocationException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd786-133">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="bd786-134">Uygulamanız, yapılandırmaları FIPS ile uyumluluk gerektiren bilgisayarlarda çalışıyorsa ve uygulamanız FIPS ile uyumlu olmayan bir algoritma kullanıyorsa, ortak dil çalışma zamanını (CLR) engellemek için yapılandırma dosyanızda bu öğeyi kullanabilirsiniz FIPS uyumluluğunu zorunlu tutma.</span><span class="sxs-lookup"><span data-stu-id="bd786-134">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="bd786-135">Bu öğe .NET Framework 2,0 hizmet paketi 1 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="bd786-135">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd786-136">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd786-136">Example</span></span>  
 <span data-ttu-id="bd786-137">Aşağıdaki örnek, CLR 'nin FIPS uyumluluğunu zorlemesini nasıl önleyegösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd786-137">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bd786-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd786-138">See also</span></span>

- [<span data-ttu-id="bd786-139">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bd786-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bd786-140">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="bd786-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="bd786-141">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="bd786-141">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
