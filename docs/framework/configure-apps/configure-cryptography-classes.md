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
ms.openlocfilehash: 77f26405792ac782f2a04e174e8165a09b7f22f6
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567338"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="94394-102">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="94394-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="94394-103">Windows SDK, bilgisayar yöneticilerinin .NET Framework ve uygun şekilde yazılmış uygulamaların kullandığı varsayılan şifreleme algoritmalarını ve algoritma uygulamalarını yapılandırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="94394-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="94394-104">Örneğin, bir şifreleme algoritması uygulamasına sahip bir kuruluş, bu uygulamayı Windows SDK sevk edilen uygulama yerine varsayılan olarak yapabilir.</span><span class="sxs-lookup"><span data-stu-id="94394-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="94394-105">Şifreleme kullanan yönetilen uygulamalar her zaman belirli bir uygulamaya açıkça bağlamayı seçebilse de, şifre yapılandırma sistemini kullanarak şifreleme nesneleri oluşturması önerilir.</span><span class="sxs-lookup"><span data-stu-id="94394-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94394-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="94394-106">In This Section</span></span>  
 [<span data-ttu-id="94394-107">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="94394-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="94394-108">Bir algoritma adının bir şifreleme sınıfına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="94394-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="94394-109">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="94394-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="94394-110">Bir nesne tanımlayıcısının bir şifreleme algoritmasına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="94394-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94394-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="94394-111">Related Sections</span></span>  
 [<span data-ttu-id="94394-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="94394-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="94394-113">Windows SDK tarafından sağlanan şifreleme hizmetlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="94394-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="94394-114">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="94394-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="94394-115">Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="94394-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
