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
ms.openlocfilehash: 71d2edac1dd9a84c9d3c92049d2494c7c5bd54b0
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028229"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="011c7-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="011c7-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="011c7-103">Şifreleme Ayarları Şeması kolay algoritma adlarını şifreleme algoritmalarını uygulayan sınıflar için eşleme belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="011c7-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="011c7-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="011c7-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="011c7-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="011c7-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="011c7-106">**\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="011c7-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="011c7-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="011c7-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="011c7-108">**\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="011c7-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="011c7-109">**\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="011c7-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="011c7-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="011c7-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="011c7-111">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="011c7-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="011c7-112">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="011c7-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="011c7-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="011c7-113">Element</span></span>|<span data-ttu-id="011c7-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="011c7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="011c7-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="011c7-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="011c7-116">Bir eşleme için bir kolay ad şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="011c7-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="011c7-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="011c7-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="011c7-118">İçin bir kolay ad eşlemesi var. bir şifreleme sınıfına içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="011c7-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="011c7-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="011c7-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="011c7-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="011c7-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="011c7-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="011c7-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="011c7-122">Sınıf için kolay adlar eşlemeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="011c7-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="011c7-123">**\<mscorlib >** öğesi için şifreleme ayarları</span><span class="sxs-lookup"><span data-stu-id="011c7-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="011c7-124">İçeren  **\<cryptographySettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="011c7-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="011c7-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="011c7-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="011c7-126">Çok sayıda kolay adlara sahip bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="011c7-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="011c7-127">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="011c7-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="011c7-128">ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.</span><span class="sxs-lookup"><span data-stu-id="011c7-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="011c7-129">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="011c7-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="011c7-130">ASN.1 OID eşlemeleri için sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="011c7-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="011c7-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="011c7-131">See Also</span></span>  
 [<span data-ttu-id="011c7-132">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="011c7-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="011c7-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="011c7-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
