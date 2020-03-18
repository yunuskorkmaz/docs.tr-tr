---
title: .NET'te Temel Dize İşlemleri
description: Dizelerüzerinde gerçekleştirebileceğiniz temel işlemler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132920"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="de4d8-103">.NET'te Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="de4d8-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="de4d8-104">Uygulamalar genellikle kullanıcı girişine dayalı iletiler oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="de4d8-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="de4d8-105">Örneğin, Web sitelerinin yeni oturum açmış bir kullanıcıya kullanıcının adını içeren özel bir karşılamayla yanıt vermesi sık rastlanan bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="de4d8-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="de4d8-106"><xref:System.String?displayProperty=nameWithType> Ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflardaki çeşitli yöntemler, kullanıcı arabiriminizde görüntülenecek özel dizeleri dinamik olarak oluşturmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="de4d8-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="de4d8-107">Bu yöntemler, bayt dizilerinden yeni dizeler oluşturma, dizelerin değerlerini karşılaştırma ve varolan dizeleri değiştirme gibi bir dizi temel dize işlemi gerçekleştirmenize de yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="de4d8-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="de4d8-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="de4d8-108">In This Section</span></span>  
 [<span data-ttu-id="de4d8-109">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="de4d8-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="de4d8-110">Nesneleri dizeleri dönüştürmenin ve dizeleri birleştirmenin temel yollarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="de4d8-111">Karakterleri Kırpma ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="de4d8-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="de4d8-112">Dizedeki karakterlerin nasıl kırpılabildiğini veya kaldırılabildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="de4d8-113">Dizeleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="de4d8-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="de4d8-114">Karakterleri veya boş alanları bir dize ye nasıl ekinize edineceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="de4d8-115">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="de4d8-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="de4d8-116">İki veya daha fazla dize içeriğini nasıl karşılaştırın açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="de4d8-117">Büyük/Küçük Harf Değiştirme</span><span class="sxs-lookup"><span data-stu-id="de4d8-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="de4d8-118">Dize içindeki karakterlerin durumununasıl değiştireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="de4d8-119">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="de4d8-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="de4d8-120"><xref:System.Text.StringBuilder> Sınıfla birlikte dinamik dize nesnelerinin nasıl oluşturulup değiştirilebildiğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="de4d8-121">Nasıl yapılır: Temel Dize İşlemeleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="de4d8-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="de4d8-122">Temel dize işlemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de4d8-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="de4d8-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="de4d8-123">Related Sections</span></span>  
 [<span data-ttu-id="de4d8-124">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="de4d8-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="de4d8-125">Bir türü başka bir türe dönüştürme yi açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="de4d8-126">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="de4d8-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="de4d8-127">Biçim belirteçlerini kullanarak dizeleri nasıl biçimlendireceklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de4d8-127">Describes how to format strings using format specifiers.</span></span>
