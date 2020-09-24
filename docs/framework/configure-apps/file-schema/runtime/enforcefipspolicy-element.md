---
title: <enforceFIPSPolicy> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
ms.openlocfilehash: 864a371d4ad10585e672452ad85cc09d4b684068
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158844"
---
# <a name="enforcefipspolicy-element"></a><span data-ttu-id="763b1-102">\<enforceFIPSPolicy> Öğesi</span><span class="sxs-lookup"><span data-stu-id="763b1-102">\<enforceFIPSPolicy> Element</span></span>

<span data-ttu-id="763b1-103">Şifreleme algoritmalarının Federal bilgi Işleme standartları (FIPS) ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlayamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="763b1-103">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<enforceFIPSPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="763b1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="763b1-104">Syntax</span></span>  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="763b1-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="763b1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="763b1-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="763b1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="763b1-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="763b1-107">Attributes</span></span>  
  
|<span data-ttu-id="763b1-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="763b1-108">Attribute</span></span>|<span data-ttu-id="763b1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="763b1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="763b1-110">enabled</span><span class="sxs-lookup"><span data-stu-id="763b1-110">enabled</span></span>|<span data-ttu-id="763b1-111">Gerekli öznitelik.</span><span class="sxs-lookup"><span data-stu-id="763b1-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="763b1-112">Şifreleme algoritmalarının FIPS ile uyumlu olması gereken bir bilgisayar yapılandırma gereksinimini zorlamasının etkinleştirilip etkinleştirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="763b1-112">Specifies whether to enable the enforcement of a computer configuration requirement that cryptographic algorithms must be compliant with FIPS.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="763b1-113">etkin Öznitelik</span><span class="sxs-lookup"><span data-stu-id="763b1-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="763b1-114">Değer</span><span class="sxs-lookup"><span data-stu-id="763b1-114">Value</span></span>|<span data-ttu-id="763b1-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="763b1-115">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="763b1-116">Bilgisayarınız, şifreleme algoritmalarının FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırıldıysa, bu gereksinim zorlanır.</span><span class="sxs-lookup"><span data-stu-id="763b1-116">If your computer is configured to require cryptographic algorithms to be FIPS compliant, that requirement is enforced.</span></span> <span data-ttu-id="763b1-117">Bir sınıf FIPS ile uyumlu olmayan bir algoritma uygularsa, `Create` Bu sınıfa yönelik oluşturucular veya Yöntemler, bu bilgisayarda çalıştırıldığında özel durumlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="763b1-117">If a class implements an algorithm that is not compliant with FIPS, the constructors or `Create` methods for that class throw exceptions when they are run on that computer.</span></span> <span data-ttu-id="763b1-118">Bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="763b1-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="763b1-119">Uygulama tarafından kullanılan şifreleme algoritmalarının, bilgisayar yapılandırmasına bakılmaksızın FIPS ile uyumlu olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="763b1-119">Cryptographic algorithms that are used by the application are not required to be compliant with FIPS, regardless of computer configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="763b1-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="763b1-120">Child Elements</span></span>  

 <span data-ttu-id="763b1-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="763b1-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="763b1-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="763b1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="763b1-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="763b1-123">Element</span></span>|<span data-ttu-id="763b1-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="763b1-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="763b1-125">Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.</span><span class="sxs-lookup"><span data-stu-id="763b1-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="763b1-126">Derleme bağlama ve atık toplama hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="763b1-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="763b1-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="763b1-127">Remarks</span></span>  

 <span data-ttu-id="763b1-128">2,0 .NET Framework başlayarak, şifreleme algoritmaları uygulayan sınıfların oluşturulması bilgisayarın yapılandırmasıyla denetlenir.</span><span class="sxs-lookup"><span data-stu-id="763b1-128">Starting with the .NET Framework 2.0, the creation of classes that implement cryptographic algorithms is controlled by the configuration of the computer.</span></span> <span data-ttu-id="763b1-129">Bilgisayar algoritmaların FIPS ile uyumlu olmasını gerektirecek şekilde yapılandırıldıysa ve bir sınıf FIPS ile uyumlu olmayan bir algoritma uygularsa, bu sınıfın bir örneğini oluşturma girişimi bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="763b1-129">If the computer is configured to require algorithms to be compliant with FIPS, and a class implements an algorithm that is not compliant with FIPS, any attempt to create an instance of that class throws an exception.</span></span> <span data-ttu-id="763b1-130">Oluşturucular bir özel durum oluşturur <xref:System.InvalidOperationException> ve `Create` Yöntemler <xref:System.Reflection.TargetInvocationException> iç özel durum ile özel durum oluşturur <xref:System.InvalidOperationException> .</span><span class="sxs-lookup"><span data-stu-id="763b1-130">Constructors throw an <xref:System.InvalidOperationException> exception, and `Create` methods throw a <xref:System.Reflection.TargetInvocationException> exception with an inner <xref:System.InvalidOperationException> exception.</span></span>  
  
 <span data-ttu-id="763b1-131">Uygulamanız, yapılandırmaları FIPS ile uyumlu olması gereken bilgisayarlarda çalışıyorsa ve uygulamanız FIPS ile uyumlu olmayan bir algoritma kullanıyorsa, ortak dil çalışma zamanının (CLR) FIPS uyumluluğunu zorlemesini engellemek için bu öğeyi yapılandırma dosyanızda kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="763b1-131">If your application runs on computers whose configurations require compliance with FIPS, and your application uses an algorithm that is not compliant with FIPS, you can use this element in your configuration file to prevent the common language runtime (CLR) from enforcing FIPS compliance.</span></span> <span data-ttu-id="763b1-132">Bu öğe .NET Framework 2,0 hizmet paketi 1 ' de tanıtılmıştı.</span><span class="sxs-lookup"><span data-stu-id="763b1-132">This element was introduced in the .NET Framework 2.0 Service Pack 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="763b1-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="763b1-133">Example</span></span>  

 <span data-ttu-id="763b1-134">Aşağıdaki örnek, CLR 'nin FIPS uyumluluğunu zorlemesini nasıl önleyegösterdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="763b1-134">The following example shows how to prevent the CLR from enforcing FIPS compliance.</span></span>  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="763b1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="763b1-135">See also</span></span>

- [<span data-ttu-id="763b1-136">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="763b1-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="763b1-137">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="763b1-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="763b1-138">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="763b1-138">Cryptography Model</span></span>](../../../../standard/security/cryptography-model.md)
