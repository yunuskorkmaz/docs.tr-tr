---
title: "Şifreleme Sınıflarını Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 79eb9f9ef95dae24dd38fa93b137c9303815143b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="1c55a-102">Şifreleme Sınıflarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1c55a-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="1c55a-103">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Varsayılan şifreleme algoritmaları ve .NET Framework ve uygun şekilde yazılmış uygulamalar kullanmak algoritması uygulamalarını yapılandırmak bilgisayar yöneticilerinin sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c55a-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="1c55a-104">Örneğin, kendi uygulamanızda bir şifreleme algoritması, bir kuruluş bu uygulama içinde gönderilen uygulaması yerine varsayılan hale getirebilir [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c55a-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="1c55a-105">Şifreleme kullanan yönetilen uygulamalar her zaman açık olarak belirli bir uygulamaya bağlamak seçebilmenize rağmen şifre yapılandırma sistemi kullanarak şifreleme nesneleri oluşturmak önerilir.</span><span class="sxs-lookup"><span data-stu-id="1c55a-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c55a-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1c55a-106">In This Section</span></span>  
 [<span data-ttu-id="1c55a-107">Algoritma adlarını şifreleme sınıflarıyla eşleştirme</span><span class="sxs-lookup"><span data-stu-id="1c55a-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="1c55a-108">Bir şifreleme sınıf için bir algoritma adı eşlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c55a-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="1c55a-109">Nesne tanımlayıcılarını şifreleme algoritmalarıyla eşleştirme</span><span class="sxs-lookup"><span data-stu-id="1c55a-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="1c55a-110">Bir şifreleme algoritması için bir nesne tanımlayıcı eşlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c55a-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1c55a-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1c55a-111">Related Sections</span></span>  
 [<span data-ttu-id="1c55a-112">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1c55a-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="1c55a-113">Tarafından sağlanan şifreleme hizmetlerine genel bakış sağlayan [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c55a-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="1c55a-114">Şifreleme Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="1c55a-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="1c55a-115">Şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleme öğelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c55a-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
