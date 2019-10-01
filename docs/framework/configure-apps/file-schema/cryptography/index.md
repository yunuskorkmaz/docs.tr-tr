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
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699810"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="3bae7-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="3bae7-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="3bae7-103">Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[<span data-ttu-id="3bae7-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="3bae7-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3bae7-105">&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-105">&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)</span></span>  
<span data-ttu-id="3bae7-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<Cryptographrivsettings >** ](cryptographysettings-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)</span></span>  
<span data-ttu-id="3bae7-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)</span></span>  
<span data-ttu-id="3bae7-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)</span></span>  
<span data-ttu-id="3bae7-109">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)</span></span>  
<span data-ttu-id="3bae7-110">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)</span></span>  
<span data-ttu-id="3bae7-111">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<Oıdmap >** ](oidmap-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)</span></span>  
<span data-ttu-id="3bae7-112">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<Oıdentry >** ](oidentry-element.md)</span><span class="sxs-lookup"><span data-stu-id="3bae7-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)</span></span>  
  
|<span data-ttu-id="3bae7-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="3bae7-113">Element</span></span>|<span data-ttu-id="3bae7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3bae7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3bae7-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="3bae7-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="3bae7-116">**@No__t-1nameEntry >** öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="3bae7-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="3bae7-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="3bae7-118">**@No__t-1nameEntry >** öğesinde kolay bir adla eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="3bae7-119"> **\<Cryptographrivsettings**></span><span class="sxs-lookup"><span data-stu-id="3bae7-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="3bae7-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="3bae7-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="3bae7-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="3bae7-122">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="3bae7-123">şifreleme ayarları için **\<mscorlib >** öğesi</span><span class="sxs-lookup"><span data-stu-id="3bae7-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="3bae7-124">**@No__t-1Cryptographyısettings >** öğesini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="3bae7-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="3bae7-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="3bae7-126">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3bae7-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="3bae7-127"> **\<Oıdentry >** </span><span class="sxs-lookup"><span data-stu-id="3bae7-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="3bae7-128">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="3bae7-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="3bae7-129"> **\<Oıdmap >** </span><span class="sxs-lookup"><span data-stu-id="3bae7-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="3bae7-130">Sınıflara ASN. 1 OID eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bae7-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3bae7-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bae7-131">See also</span></span>

- [<span data-ttu-id="3bae7-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="3bae7-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3bae7-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="3bae7-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
