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
ms.openlocfilehash: 00b04cc2175f4bb4cc0b74602cd3c26f4a4e342f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184463"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="415d4-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="415d4-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="415d4-103">Şifreleme Ayarları Şeması kolay algoritma adlarını şifreleme algoritmalarını uygulayan sınıflar için eşleme belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="415d4-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="415d4-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="415d4-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="415d4-105">**\<mscorlib>**</span><span class="sxs-lookup"><span data-stu-id="415d4-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="415d4-106">**\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="415d4-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="415d4-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="415d4-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="415d4-108">**\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="415d4-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="415d4-109">**\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="415d4-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="415d4-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="415d4-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="415d4-111">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="415d4-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="415d4-112">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="415d4-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="415d4-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="415d4-113">Element</span></span>|<span data-ttu-id="415d4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="415d4-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="415d4-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="415d4-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="415d4-116">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="415d4-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="415d4-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="415d4-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="415d4-118">İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="415d4-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="415d4-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="415d4-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="415d4-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="415d4-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="415d4-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="415d4-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="415d4-122">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="415d4-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="415d4-123">**\<mscorlib >** öğesi için şifreleme ayarları</span><span class="sxs-lookup"><span data-stu-id="415d4-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="415d4-124">İçeren  **\<cryptographySettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="415d4-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="415d4-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="415d4-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="415d4-126">Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="415d4-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="415d4-127">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="415d4-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="415d4-128">ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.</span><span class="sxs-lookup"><span data-stu-id="415d4-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="415d4-129">**\<oidMap>**</span><span class="sxs-lookup"><span data-stu-id="415d4-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="415d4-130">ASN.1 OID eşlemeleri için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="415d4-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="415d4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="415d4-131">See also</span></span>

- [<span data-ttu-id="415d4-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="415d4-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="415d4-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="415d4-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
