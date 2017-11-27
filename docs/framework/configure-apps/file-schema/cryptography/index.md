---
title: "Şifreleme Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c7d1e193236528c96e8253668c742883090ae188
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="ef94f-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="ef94f-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="ef94f-103">Şifreleme Ayarları Şeması şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleme belirtmek öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ef94f-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
 [<span data-ttu-id="ef94f-104">**\<Yapılandırma >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-104">**\<configuration>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="ef94f-105">**\<mscorlib >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-105">**\<mscorlib>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [<span data-ttu-id="ef94f-106">**\<cryptographySettings >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-106">**\<cryptographySettings>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [<span data-ttu-id="ef94f-107">**\<cryptoNameMapping >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-107">**\<cryptoNameMapping>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [<span data-ttu-id="ef94f-108">**\<cryptoClasses >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-108">**\<cryptoClasses>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [<span data-ttu-id="ef94f-109">**\<cryptoClass >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-109">**\<cryptoClass>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [<span data-ttu-id="ef94f-110">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-110">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [<span data-ttu-id="ef94f-111">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-111">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [<span data-ttu-id="ef94f-112">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-112">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|<span data-ttu-id="ef94f-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="ef94f-113">Element</span></span>|<span data-ttu-id="ef94f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef94f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef94f-115">**\<cryptoClasses**></span><span class="sxs-lookup"><span data-stu-id="ef94f-115">**\<cryptoClasses**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|<span data-ttu-id="ef94f-116">Bir kolay ad eşlemeye sahip şifreleme sınıflarını listesini içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ef94f-116">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="ef94f-117">**\<cryptoClass**></span><span class="sxs-lookup"><span data-stu-id="ef94f-117">**\<cryptoClass**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|<span data-ttu-id="ef94f-118">Bir kolay ad için bir eşleme olan bir şifreleme sınıfı içeren  **\<nameEntry >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ef94f-118">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[<span data-ttu-id="ef94f-119">**\<cryptographySettings**></span><span class="sxs-lookup"><span data-stu-id="ef94f-119">**\<cryptographySettings**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|<span data-ttu-id="ef94f-120">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="ef94f-120">Contains cryptography settings.</span></span>|  
|[<span data-ttu-id="ef94f-121">**\<cryptoNameMapping**></span><span class="sxs-lookup"><span data-stu-id="ef94f-121">**\<cryptoNameMapping**></span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|<span data-ttu-id="ef94f-122">Kolay adlar sınıflarına eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="ef94f-122">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="ef94f-123">**\<mscorlib >** öğesi için şifreleme ayarları</span><span class="sxs-lookup"><span data-stu-id="ef94f-123">**\<mscorlib>** element for cryptography settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="ef94f-124">İçeren  **\<cryptographySettings >** öğesi.</span><span class="sxs-lookup"><span data-stu-id="ef94f-124">Contains the **\<cryptographySettings>** element.</span></span>|  
|[<span data-ttu-id="ef94f-125">**\<nameEntry >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-125">**\<nameEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|<span data-ttu-id="ef94f-126">Çok sayıda kolay adlar sağlamak bir sınıf sağlar ve kolay algoritma adı için bir sınıf adı eşler.</span><span class="sxs-lookup"><span data-stu-id="ef94f-126">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[<span data-ttu-id="ef94f-127">**\<oidEntry >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-127">**\<oidEntry>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|<span data-ttu-id="ef94f-128">ASN.1 nesne tanımlayıcısı (OID) için bir kolay ad eşler.</span><span class="sxs-lookup"><span data-stu-id="ef94f-128">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[<span data-ttu-id="ef94f-129">**\<oidMap >**</span><span class="sxs-lookup"><span data-stu-id="ef94f-129">**\<oidMap>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|<span data-ttu-id="ef94f-130">ASN.1 OID eşlemeler sınıflar içerir.</span><span class="sxs-lookup"><span data-stu-id="ef94f-130">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef94f-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ef94f-131">See Also</span></span>  
 [<span data-ttu-id="ef94f-132">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="ef94f-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="ef94f-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="ef94f-133">Cryptographic Services</span></span>](../../../../../docs/standard/security/cryptographic-services.md)
