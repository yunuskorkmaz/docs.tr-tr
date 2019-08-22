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
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664290"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="cbaa0-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="cbaa0-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="cbaa0-103">Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="cbaa0-104"> **\<Yapılandırma >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-104">**\<configuration>**</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="cbaa0-105"> **\<mscorlib >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-105">**\<mscorlib>**</span></span>](mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="cbaa0-106"> **\<Cryptographyısettings >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-106">**\<cryptographySettings>**</span></span>](cryptographysettings-element.md)  
  
 [<span data-ttu-id="cbaa0-107"> **\<cryptoNameMapping >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-107">**\<cryptoNameMapping>**</span></span>](cryptonamemapping-element.md)  
  
 [<span data-ttu-id="cbaa0-108"> **\<cryptoClasses >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-108">**\<cryptoClasses>**</span></span>](cryptoclasses-element.md)  
  
 [<span data-ttu-id="cbaa0-109"> **\<cryptoClass >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-109">**\<cryptoClass>**</span></span>](cryptoclass-element.md)  
  
 [<span data-ttu-id="cbaa0-110"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-110">**\<nameEntry>**</span></span>](nameentry-element.md)  
  
 [<span data-ttu-id="cbaa0-111"> **\<Oıdmap >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-111">**\<oidMap>**</span></span>](oidmap-element.md)  
  
 [<span data-ttu-id="cbaa0-112"> **\<Oıdentry >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-112">**\<oidEntry>**</span></span>](oidentry-element.md)  
  
|<span data-ttu-id="cbaa0-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="cbaa0-113">Element</span></span>|<span data-ttu-id="cbaa0-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbaa0-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cbaa0-115"> **\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="cbaa0-115">**\<cryptoClasses**></span></span>](cryptoclasses-element.md)|<span data-ttu-id="cbaa0-116">NameEntry > öğesinde kolay bir ada  **\<** eşleme olan şifreleme sınıflarının bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="cbaa0-117"> **\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="cbaa0-117">**\<cryptoClass**></span></span>](cryptoclass-element.md)|<span data-ttu-id="cbaa0-118">NameEntry > öğesinde kolay bir ad  **\<** ile eşleşen bir şifreleme sınıfı içerir.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="cbaa0-119"> **\<Cryptographrivsettings**></span><span class="sxs-lookup"><span data-stu-id="cbaa0-119">**\<cryptographySettings**></span></span>](cryptographysettings-element.md)|<span data-ttu-id="cbaa0-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="cbaa0-121"> **\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="cbaa0-121">**\<cryptoNameMapping**></span></span>](cryptonamemapping-element.md)|<span data-ttu-id="cbaa0-122">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="cbaa0-123">şifreleme ayarları için mscorlib > öğesi  **\<** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-123">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="cbaa0-124">Cryptographrivsettings > öğesini içerir.  **\<**</span><span class="sxs-lookup"><span data-stu-id="cbaa0-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="cbaa0-125"> **\<nameEntry >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-125">**\<nameEntry>**</span></span>](nameentry-element.md)|<span data-ttu-id="cbaa0-126">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="cbaa0-127"> **\<Oıdentry >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-127">**\<oidEntry>**</span></span>](oidentry-element.md)|<span data-ttu-id="cbaa0-128">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="cbaa0-129"> **\<Oıdmap >** </span><span class="sxs-lookup"><span data-stu-id="cbaa0-129">**\<oidMap>**</span></span>](oidmap-element.md)|<span data-ttu-id="cbaa0-130">Sınıflara ASN. 1 OID eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cbaa0-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-131">See also</span></span>

- [<span data-ttu-id="cbaa0-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="cbaa0-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="cbaa0-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cbaa0-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
