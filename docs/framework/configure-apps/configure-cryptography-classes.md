---
title: Şifreleme Sınıflarını Yapılandırma
description: Bilgisayar yöneticilerinin .NET ve uygulamaların kullandığı varsayılan şifreleme algoritmalarını ve algoritma uygulamalarını nasıl yapılandırabileceğini anlayın.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5262dfca914fd5306297ea9535bcef3d2088d107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165214"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="d752e-103">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d752e-103">Configuring Cryptography Classes</span></span>

<span data-ttu-id="d752e-104">Windows SDK, bilgisayar yöneticilerinin .NET Framework ve uygun şekilde yazılmış uygulamaların kullandığı varsayılan şifreleme algoritmalarını ve algoritma uygulamalarını yapılandırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d752e-104">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="d752e-105">Örneğin, bir şifreleme algoritması uygulamasına sahip bir kuruluş, bu uygulamayı Windows SDK sevk edilen uygulama yerine varsayılan olarak yapabilir.</span><span class="sxs-lookup"><span data-stu-id="d752e-105">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="d752e-106">Şifreleme kullanan yönetilen uygulamalar her zaman belirli bir uygulamaya açıkça bağlamayı seçebilse de, şifre yapılandırma sistemini kullanarak şifreleme nesneleri oluşturması önerilir.</span><span class="sxs-lookup"><span data-stu-id="d752e-106">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d752e-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d752e-107">In This Section</span></span>  

 [<span data-ttu-id="d752e-108">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="d752e-108">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="d752e-109">Bir algoritma adının bir şifreleme sınıfına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d752e-109">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="d752e-110">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="d752e-110">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="d752e-111">Bir nesne tanımlayıcısının bir şifreleme algoritmasına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d752e-111">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d752e-112">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d752e-112">Related Sections</span></span>  

 [<span data-ttu-id="d752e-113">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d752e-113">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="d752e-114">Windows SDK tarafından sağlanan şifreleme hizmetlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="d752e-114">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="d752e-115">Şifreleme ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="d752e-115">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="d752e-116">Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d752e-116">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
