---
title: ".NET Framework'te Temel Dize İşlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1ee53343a68a2c2169baefaebc68a817159d0313
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="0dc3f-102">.NET temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="0dc3f-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="0dc3f-103">Uygulamalar genellikle kullanıcı girişini temel alarak iletileri oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="0dc3f-104">Örneğin, yeni oturum açmış olan bir kullanıcı kullanıcı adını içeren özelleştirilmiş bir karşılama yanıtlamak Web siteleri için seyrek değil.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="0dc3f-105">Çeşitli yöntemlerin <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfları dinamik olarak, kullanıcı arabiriminde görüntülenecek özel dizeleri oluşturmak izin verir.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="0dc3f-106">Bu yöntemler bir dizi bayt dizileri yeni dizeler oluşturma, dize değerleri karşılaştırma ve varolan dizeleri değiştirme gibi temel dize işlemleri gerçekleştirmenize yardımcı.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0dc3f-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0dc3f-107">In This Section</span></span>  
 [<span data-ttu-id="0dc3f-108">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0dc3f-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="0dc3f-109">Nesneleri dizelere dönüştürme ve dizeleri birleştirmek için temel yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="0dc3f-110">Karakterleri Kırpma ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="0dc3f-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="0dc3f-111">Kırpma veya bir dizedeki karakterleri Kaldır açıklar.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="0dc3f-112">Dizeleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="0dc3f-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="0dc3f-113">Karakter veya boş alanları bir dizeye nasıl ekleneceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="0dc3f-114">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="0dc3f-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="0dc3f-115">İki veya daha fazla içeriğini karşılaştırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="0dc3f-116">Büyük/Küçük Harf Değiştirme</span><span class="sxs-lookup"><span data-stu-id="0dc3f-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="0dc3f-117">Bir dize karakterlerine durumunun değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="0dc3f-118">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="0dc3f-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="0dc3f-119">İle dinamik dize nesneleri oluşturup değiştirmesi açıklar <xref:System.Text.StringBuilder> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="0dc3f-120">Nasıl yapılır: Temel Dize İşlemeleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="0dc3f-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="0dc3f-121">Temel dize işlemleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0dc3f-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0dc3f-122">Related Sections</span></span>  
 [<span data-ttu-id="0dc3f-123">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0dc3f-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="0dc3f-124">Bir tür başka bir türüne dönüştürün açıklar.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="0dc3f-125">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="0dc3f-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="0dc3f-126">Biçim dizeleri biçim belirticilerini kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="0dc3f-126">Describes how to format strings using format specifiers.</span></span>
