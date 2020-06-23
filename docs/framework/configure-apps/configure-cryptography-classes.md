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
ms.openlocfilehash: 5d12aae31ec78f80bea7df1bb0f37ac78dc37de2
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105070"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="e8dbd-103">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e8dbd-103">Configuring Cryptography Classes</span></span>
<span data-ttu-id="e8dbd-104">Windows SDK, bilgisayar yöneticilerinin .NET Framework ve uygun şekilde yazılmış uygulamaların kullandığı varsayılan şifreleme algoritmalarını ve algoritma uygulamalarını yapılandırmalarına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-104">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="e8dbd-105">Örneğin, bir şifreleme algoritması uygulamasına sahip bir kuruluş, bu uygulamayı Windows SDK sevk edilen uygulama yerine varsayılan olarak yapabilir.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-105">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="e8dbd-106">Şifreleme kullanan yönetilen uygulamalar her zaman belirli bir uygulamaya açıkça bağlamayı seçebilse de, şifre yapılandırma sistemini kullanarak şifreleme nesneleri oluşturması önerilir.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-106">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8dbd-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e8dbd-107">In This Section</span></span>  
 [<span data-ttu-id="e8dbd-108">Algoritma Adlarını Şifreleme Sınıflarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e8dbd-108">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="e8dbd-109">Bir algoritma adının bir şifreleme sınıfına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-109">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="e8dbd-110">Nesne Tanımlayıcılarını Şifreleme Algoritmalarıyla Eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e8dbd-110">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="e8dbd-111">Bir nesne tanımlayıcısının bir şifreleme algoritmasına nasıl eşleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-111">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e8dbd-112">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e8dbd-112">Related Sections</span></span>  
 [<span data-ttu-id="e8dbd-113">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e8dbd-113">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="e8dbd-114">Windows SDK tarafından sağlanan şifreleme hizmetlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-114">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="e8dbd-115">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="e8dbd-115">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="e8dbd-116">Kolay algoritma adlarını şifreleme algoritmaları uygulayan sınıflarla eşleyen öğeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e8dbd-116">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
