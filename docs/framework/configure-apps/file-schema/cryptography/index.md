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
ms.openlocfilehash: a7964d01905be4e3dd6e8149e5533e9a2cfd9a71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927626"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="fd148-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="fd148-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="fd148-103">Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fd148-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="fd148-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="fd148-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="fd148-105"> **\<mscorlib >** </span><span class="sxs-lookup"><span data-stu-id="fd148-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="fd148-106"> **\<Cryptographyısettings >** </span><span class="sxs-lookup"><span data-stu-id="fd148-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="fd148-107"> **\<cryptoNameMapping >** </span><span class="sxs-lookup"><span data-stu-id="fd148-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="fd148-108"> **\<cryptoClasses >** </span><span class="sxs-lookup"><span data-stu-id="fd148-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="fd148-109"> **\<cryptoClass >** </span><span class="sxs-lookup"><span data-stu-id="fd148-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="fd148-110"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="fd148-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="fd148-111"> **\<Oıdmap >** </span><span class="sxs-lookup"><span data-stu-id="fd148-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="fd148-112"> **\<Oıdentry >** </span><span class="sxs-lookup"><span data-stu-id="fd148-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="fd148-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="fd148-113">Element</span></span>|<span data-ttu-id="fd148-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd148-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd148-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="fd148-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="fd148-116">NameEntry > öğesinde kolay bir ada  **\<** eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="fd148-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="fd148-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="fd148-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="fd148-118">NameEntry > öğesinde kolay bir ad  **\<** ile eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="fd148-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="fd148-119"> **\<Cryptographrivsettings**></span><span class="sxs-lookup"><span data-stu-id="fd148-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="fd148-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="fd148-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="fd148-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="fd148-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="fd148-122">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fd148-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="fd148-123">şifreleme ayarları için mscorlib > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="fd148-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="fd148-124">Cryptographrivsettings > öğesini içerir.  **\<**</span><span class="sxs-lookup"><span data-stu-id="fd148-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="fd148-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="fd148-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="fd148-126">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="fd148-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="fd148-127"> **\<Oıdentry >** </span><span class="sxs-lookup"><span data-stu-id="fd148-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="fd148-128">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="fd148-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="fd148-129"> **\<Oıdmap >** </span><span class="sxs-lookup"><span data-stu-id="fd148-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="fd148-130">Sınıflara ASN. 1 OID eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="fd148-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd148-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd148-131">See also</span></span>

- [<span data-ttu-id="fd148-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="fd148-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fd148-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="fd148-133">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
