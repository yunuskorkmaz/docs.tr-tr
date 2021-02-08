---
description: 'Daha fazla bilgi edinin: <enforceFIPSPolicy> öğesi'
title: <enforceFIPSPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: d445570db634867a15b6d97d4e20186bd0641c2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787077"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="befcc-103">\<enforceFIPSPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="befcc-103">\<enforceFIPSPolicy> Element</span></span>

<span data-ttu-id="befcc-104">Şifreleme algoritmalarının Federal bilgi Işleme standartları (FIPS) ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlayamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="befcc-104">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="befcc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="befcc-105">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="befcc-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="befcc-106">Attributes and Elements</span></span>  

 <span data-ttu-id="befcc-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="befcc-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="befcc-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="befcc-108">Attributes</span></span>  
  
|<span data-ttu-id="befcc-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="befcc-109">Attribute</span></span>|<span data-ttu-id="befcc-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="befcc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="befcc-111">enabled</span><span class="sxs-lookup"><span data-stu-id="befcc-111">enabled</span></span>|<span data-ttu-id="befcc-112">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="befcc-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="befcc-113">Şifreleme algoritmalarının FIPS ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlamasının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="befcc-113">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="befcc-114">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="befcc-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="befcc-115">Değer</span><span class="sxs-lookup"><span data-stu-id="befcc-115">Value</span></span>|<span data-ttu-id="befcc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="befcc-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="befcc-117">Bilgisayarınız, şifreleme algoritmalarının FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırıldıysa, bu gereksinim zorlanır.</span><span class="sxs-lookup"><span data-stu-id="befcc-117">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="befcc-118">Bir sınıf FIPS ile uyumlu olmayan bir algoritma uygularsa, `Create` Bu sınıfa yönelik oluşturucular veya Yöntemler, bu bilgisayarda çalıştırıldığında özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="befcc-118">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="befcc-119">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="befcc-119">This is the default.</span></span>|  
|`false`|<span data-ttu-id="befcc-120">Uygulama tarafından kullanılan şifreleme algoritmalarının, bilgisayar yapılandırmasına bakılmaksızın FIPS ile uyumlu olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="befcc-120">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="befcc-121">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="befcc-121">Child Elements</span></span>  

 <span data-ttu-id="befcc-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="befcc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="befcc-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="befcc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="befcc-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="befcc-124">Element</span></span>|<span data-ttu-id="befcc-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="befcc-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="befcc-126">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="befcc-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="befcc-127">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="befcc-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="befcc-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="befcc-128">Remarks</span></span>  

 <span data-ttu-id="befcc-129">2,0 .NET Framework başlayarak, şifreleme algoritmaları uygulayan sınıfların oluşturulması bilgisayarın yapılandırmasıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="befcc-129">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="befcc-130">Bilgisayar algoritmaların FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırıldıysa ve bir sınıf FIPS ile uyumlu olmayan bir algoritma uygularsa, bu sınıfın bir örneğini oluşturma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="befcc-130">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="befcc-131">Oluşturucular bir özel durum oluşturur <xref:System.InvalidOperationException> ve `Create` Yöntemler <xref:System.Reflection.TargetInvocationException> iç özel durum ile özel durum oluşturur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="befcc-131">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="befcc-132">Uygulamanız, yapılandırmaları FIPS ile uyumlu olması gereken bilgisayarlarda çalışıyorsa ve uygulamanız FIPS ile uyumlu olmayan bir algoritma kullanıyorsa, ortak dil çalışma zamanının (CLR) FIPS uyumluluğunu zorlemesini engellemek için bu öğeyi yapılandırma dosyanızda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="befcc-132">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="befcc-133">Bu öğe .NET Framework 2,0 hizmet paketi 1 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="befcc-133">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="befcc-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="befcc-134">Example</span></span>  

 <span data-ttu-id="befcc-135">Aşağıdaki örnek, CLR 'nin FIPS uyumluluğunu zorlemesini nasıl önleyegösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="befcc-135">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="befcc-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="befcc-136">See also</span></span>

- [<span data-ttu-id="befcc-137">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="befcc-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="befcc-138">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="befcc-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="befcc-139">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="befcc-139">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
