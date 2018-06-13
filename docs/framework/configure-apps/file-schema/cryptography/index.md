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
manager: markl
ms.openlocfilehash: b7f41bc477f8d8095bf73859c02b7e2fc2443c14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742880"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="d94b6-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="d94b6-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="d94b6-103">Şifreleme Ayarları Şeması şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleme belirtmek öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d94b6-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="d94b6-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="d94b6-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="d94b6-106">**\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="d94b6-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="d94b6-108">**\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="d94b6-109">**\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="d94b6-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="d94b6-111">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="d94b6-112">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="d94b6-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="d94b6-113">Element</span></span>|<span data-ttu-id="d94b6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d94b6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d94b6-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="d94b6-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="d94b6-116">Bir kolay ad eşlemeye sahip şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d94b6-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="d94b6-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="d94b6-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="d94b6-118">Bir kolay ad için bir eşleme olan bir şifreleme sınıfı içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d94b6-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="d94b6-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="d94b6-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="d94b6-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="d94b6-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="d94b6-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="d94b6-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="d94b6-122">Kolay adlar sınıflarına eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d94b6-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="d94b6-123">**\<mscorlib >** öğesi için şifreleme ayarları</span><span class="sxs-lookup"><span data-stu-id="d94b6-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="d94b6-124">İçeren  **\<cryptographySettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="d94b6-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="d94b6-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="d94b6-126">Çok sayıda kolay adlar sağlamak bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="d94b6-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="d94b6-127">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="d94b6-128">ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.</span><span class="sxs-lookup"><span data-stu-id="d94b6-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="d94b6-129">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="d94b6-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="d94b6-130">ASN.1 OID eşlemeler sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="d94b6-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d94b6-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d94b6-131">See Also</span></span>  
 [<span data-ttu-id="d94b6-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="d94b6-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="d94b6-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d94b6-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
