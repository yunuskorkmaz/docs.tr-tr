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
ms.openlocfilehash: b5c1178519601d7dcb7c5b3014f413b6436746fb
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816167"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="5ff84-102">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5ff84-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="5ff84-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Varsayılan şifreleme algoritmaları ve .NET Framework ve uygun şekilde yazılmış uygulamalar kullanan algoritması uygulamalarını yapılandırmak bilgisayarda administrators sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ff84-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="5ff84-104">Örneğin, kendi uygulama şifreleme algoritması olan Kuruluş sevk edilen varsayılan uygulama yerine bu uygulamayı Windows SDK'da yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ff84-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="5ff84-105">Şifreleme kullanan yönetilen uygulamaları açıkça belirli bir uygulamaya bağlamak her zaman seçebilmenize rağmen bunlar şifreleme nesneleri şifreleme yapılandırma sistemini kullanarak oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="5ff84-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ff84-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5ff84-106">In This Section</span></span>  
 [<span data-ttu-id="5ff84-107">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="5ff84-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="5ff84-108">Bir algoritma adının bir şifreleme sınıfına harita açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ff84-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="5ff84-109">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="5ff84-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="5ff84-110">Bir şifreleme algoritması için nesne tanımlayıcısı harita açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ff84-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5ff84-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5ff84-111">Related Sections</span></span>  
 [<span data-ttu-id="5ff84-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5ff84-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="5ff84-113">Windows SDK'sı tarafından sağlanan şifreleme hizmetlerine genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ff84-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="5ff84-114">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="5ff84-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="5ff84-115">Şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="5ff84-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
