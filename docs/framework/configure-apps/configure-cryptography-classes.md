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
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927769"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="a2907-102">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a2907-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="a2907-103">Windows SDK, bilgisayar yöneticilerinin .NET Framework ve uygun şekilde yazılmış uygulamaların kullandığı varsayılan şifreleme algoritmalarını ve algoritma uygulamalarını yapılandırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a2907-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="a2907-104">Örneğin, bir şifreleme algoritması uygulamasına sahip bir kuruluş, bu uygulamayı Windows SDK sevk edilen uygulama yerine varsayılan olarak yapabilir.</span><span class="sxs-lookup"><span data-stu-id="a2907-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="a2907-105">Şifreleme kullanan yönetilen uygulamalar her zaman belirli bir uygulamaya açıkça bağlamayı seçebilse de, şifre yapılandırma sistemini kullanarak şifreleme nesneleri oluşturması önerilir.</span><span class="sxs-lookup"><span data-stu-id="a2907-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2907-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a2907-106">In This Section</span></span>  
 [<span data-ttu-id="a2907-107">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="a2907-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="a2907-108">Bir algoritma adının bir şifreleme sınıfına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2907-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="a2907-109">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleme</span><span class="sxs-lookup"><span data-stu-id="a2907-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="a2907-110">Bir nesne tanımlayıcısının bir şifreleme algoritmasına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2907-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2907-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a2907-111">Related Sections</span></span>  
 [<span data-ttu-id="a2907-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a2907-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="a2907-113">Windows SDK tarafından sağlanan şifreleme hizmetlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2907-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="a2907-114">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="a2907-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="a2907-115">Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="a2907-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
