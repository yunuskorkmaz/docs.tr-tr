---
title: Şifreleme Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088001"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="7b9cf-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="7b9cf-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="7b9cf-103">Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
<span data-ttu-id="7b9cf-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7b9cf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7b9cf-105">&nbsp;&nbsp;[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>\
<span data-ttu-id="7b9cf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Cryptographyısettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>\
<span data-ttu-id="7b9cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>\
<span data-ttu-id="7b9cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>\
<span data-ttu-id="7b9cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>\
<span data-ttu-id="7b9cf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>\
<span data-ttu-id="7b9cf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oıdmap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>\
<span data-ttu-id="7b9cf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oıdentry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9cf-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>

|<span data-ttu-id="7b9cf-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="7b9cf-113">Element</span></span>|<span data-ttu-id="7b9cf-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b9cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b9cf-115">**cryptoClasses\<** ></span><span class="sxs-lookup"><span data-stu-id="7b9cf-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="7b9cf-116">**\<nameEntry >** öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="7b9cf-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="7b9cf-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="7b9cf-118">**\<nameEntry >** öğesinde kolay bir ad ile eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="7b9cf-119"> **\<Cryptographi settings**></span><span class="sxs-lookup"><span data-stu-id="7b9cf-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="7b9cf-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="7b9cf-121">**cryptoNameMapping>\<** </span><span class="sxs-lookup"><span data-stu-id="7b9cf-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="7b9cf-122">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="7b9cf-123">şifreleme ayarları için **mscorlib > öğesi\<** </span><span class="sxs-lookup"><span data-stu-id="7b9cf-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="7b9cf-124">**\<Cryptographyısettings >** öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="7b9cf-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="7b9cf-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="7b9cf-126">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="7b9cf-127"> **\<Oıdentry >** </span><span class="sxs-lookup"><span data-stu-id="7b9cf-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="7b9cf-128">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="7b9cf-129"> **\<Oıdmap >** </span><span class="sxs-lookup"><span data-stu-id="7b9cf-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="7b9cf-130">Sınıflara ASN. 1 OID eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b9cf-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b9cf-131">See also</span></span>

- [<span data-ttu-id="7b9cf-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="7b9cf-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7b9cf-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="7b9cf-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
