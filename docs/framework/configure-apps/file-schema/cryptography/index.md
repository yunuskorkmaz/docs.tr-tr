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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088001"
---
# <a name="cryptography-settings-schema"></a><span data-ttu-id="eddce-102">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="eddce-102">Cryptography Settings Schema</span></span>
<span data-ttu-id="eddce-103">Şifreleme ayarları şeması, kolay algoritma adlarının şifreleme algoritmaları uygulayan sınıflara nasıl eşlendiğini belirten öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="eddce-103">The cryptography settings schema contains elements that specify how to map friendly algorithm names to classes that implement cryptography algorithms.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|<span data-ttu-id="eddce-104">Öğe</span><span class="sxs-lookup"><span data-stu-id="eddce-104">Element</span></span>|<span data-ttu-id="eddce-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="eddce-105">Description</span></span>|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|<span data-ttu-id="eddce-106">Öğesinde kolay bir ada eşleme olan şifreleme sınıflarının bir listesini içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="eddce-106">Contains a list of cryptography classes that have a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptoClass**>](cryptoclass-element.md)|<span data-ttu-id="eddce-107">Öğesinde bir kolay ad ile eşleşen bir şifreleme sınıfı içerir **\<nameEntry>** .</span><span class="sxs-lookup"><span data-stu-id="eddce-107">Contains a cryptography class that has a mapping to a friendly name in the **\<nameEntry>** element.</span></span>|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|<span data-ttu-id="eddce-108">Şifreleme ayarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="eddce-108">Contains cryptography settings.</span></span>|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|<span data-ttu-id="eddce-109">Kolay adlarla sınıfların eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="eddce-109">Contains mappings of classes to friendly names.</span></span>|  
|[<span data-ttu-id="eddce-110">**\<mscorlib>** şifreleme ayarları için öğesi</span><span class="sxs-lookup"><span data-stu-id="eddce-110">**\<mscorlib>** element for cryptography settings</span></span>](mscorlib-element-for-cryptography-settings.md)|<span data-ttu-id="eddce-111">Öğesini içerir **\<cryptographySettings>** .</span><span class="sxs-lookup"><span data-stu-id="eddce-111">Contains the **\<cryptographySettings>** element.</span></span>|  
|[**\<nameEntry>**](nameentry-element.md)|<span data-ttu-id="eddce-112">Bir sınıf adını kolay bir algoritma adıyla eşleştirir, bu da bir sınıfın birçok kolay adına sahip olmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eddce-112">Maps a class name to a friendly algorithm name, which allows one class to have many friendly names.</span></span>|  
|[**\<oidEntry>**](oidentry-element.md)|<span data-ttu-id="eddce-113">Bir ASN. 1 nesne tanımlayıcısını (OID) kolay bir ada eşler.</span><span class="sxs-lookup"><span data-stu-id="eddce-113">Maps an ASN.1 object identifier (OID) to a friendly name.</span></span>|  
|[**\<oidMap>**](oidmap-element.md)|<span data-ttu-id="eddce-114">Sınıflara ASN. 1 OID eşlemelerini içerir.</span><span class="sxs-lookup"><span data-stu-id="eddce-114">Contains ASN.1 OID mappings to classes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eddce-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eddce-115">See also</span></span>

- [<span data-ttu-id="eddce-116">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="eddce-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="eddce-117">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="eddce-117">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)
