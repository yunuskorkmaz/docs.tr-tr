---
description: 'Daha fazla bilgi edinin: şifreleme ayarları şeması'
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
ms.openlocfilehash: a7b3c020ed760aba24c9faf020281b7ad4bf3af7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730089"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="6a8cf-103">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6a8cf-103">Cryptography Settings Schema</span></span>

<span data-ttu-id="6a8cf-104">Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-104">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="6a8cf-105">Öğe</span><span class="sxs-lookup"><span data-stu-id="6a8cf-105">Element</span></span>|<span data-ttu-id="6a8cf-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a8cf-106">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="6a8cf-107">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="6a8cf-107">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="6a8cf-108">Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="6a8cf-108">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="6a8cf-109">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-109">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="6a8cf-110">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-110">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="6a8cf-111">**\<mscorlib>** şifreleme ayarları için öğesi</span><span class="sxs-lookup"><span data-stu-id="6a8cf-111">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="6a8cf-112">Öğesini içerir **\<cryptographySettings>** .</span><span class="sxs-lookup"><span data-stu-id="6a8cf-112">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="6a8cf-113">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-113">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="6a8cf-114">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-114">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="6a8cf-115">Sınıflara ASN. 1 OID eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-115">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6a8cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a8cf-116">See also</span></span>

- [<span data-ttu-id="6a8cf-117">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="6a8cf-117">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6a8cf-118">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6a8cf-118">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
