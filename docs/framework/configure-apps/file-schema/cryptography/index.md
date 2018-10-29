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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9bf94c28522d42e1a763726469cf9b1a03ccd86e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196758"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="bb436-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="bb436-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="bb436-103">Şifreleme Ayarları Şeması kolay algoritma adlarını şifreleme algoritmalarını uygulayan sınıflar için eşleme belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bb436-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="bb436-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="bb436-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="bb436-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="bb436-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="bb436-106">**\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="bb436-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="bb436-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="bb436-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="bb436-108">**\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="bb436-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="bb436-109">**\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="bb436-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="bb436-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="bb436-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="bb436-111">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="bb436-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="bb436-112">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="bb436-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="bb436-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="bb436-113">Element</span></span>|<span data-ttu-id="bb436-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb436-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb436-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="bb436-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="bb436-116">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="bb436-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="bb436-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="bb436-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="bb436-118">İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="bb436-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="bb436-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="bb436-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="bb436-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="bb436-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="bb436-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="bb436-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="bb436-122">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bb436-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="bb436-123">**\<mscorlib >** öğesi için şifreleme ayarları</span><span class="sxs-lookup"><span data-stu-id="bb436-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="bb436-124">İçeren  **\<cryptographySettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="bb436-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="bb436-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="bb436-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="bb436-126">Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="bb436-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="bb436-127">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="bb436-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="bb436-128">ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.</span><span class="sxs-lookup"><span data-stu-id="bb436-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="bb436-129">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="bb436-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="bb436-130">ASN.1 OID eşlemeleri için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="bb436-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb436-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bb436-131">See Also</span></span>  
- [<span data-ttu-id="bb436-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="bb436-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="bb436-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="bb436-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
