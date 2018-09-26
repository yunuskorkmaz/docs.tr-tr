---
title: Şifreleme Sınıflarını Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b9153b4525063d6c52e22d754d68ffa42e914d00
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196960"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="0da90-102">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0da90-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="0da90-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Varsayılan şifreleme algoritmaları ve .NET Framework ve uygun şekilde yazılmış uygulamalar kullanan algoritması uygulamalarını yapılandırmak bilgisayarda administrators sağlar.</span><span class="sxs-lookup"><span data-stu-id="0da90-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="0da90-104">Örneğin, kendi uygulama şifreleme algoritması olan Kuruluş bu uygulamayı içinde sevk uygulaması yerine varsayılan yapabilirsiniz [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0da90-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="0da90-105">Şifreleme kullanan yönetilen uygulamaları açıkça belirli bir uygulamaya bağlamak her zaman seçebilmenize rağmen bunlar şifreleme nesneleri şifreleme yapılandırma sistemini kullanarak oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="0da90-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0da90-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0da90-106">In This Section</span></span>  
 [<span data-ttu-id="0da90-107">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="0da90-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="0da90-108">Bir algoritma adının bir şifreleme sınıfına harita açıklar.</span><span class="sxs-lookup"><span data-stu-id="0da90-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="0da90-109">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="0da90-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="0da90-110">Bir şifreleme algoritması için nesne tanımlayıcısı harita açıklar.</span><span class="sxs-lookup"><span data-stu-id="0da90-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0da90-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0da90-111">Related Sections</span></span>  
 [<span data-ttu-id="0da90-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0da90-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="0da90-113">Tarafından sağlanan şifreleme hizmetlerine genel bakış sağlar [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0da90-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="0da90-114">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="0da90-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="0da90-115">Şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0da90-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
