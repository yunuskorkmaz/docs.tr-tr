---
title: .NET 'te temel dize Işlemleri
description: Dizeler üzerinde gerçekleştirebileceğiniz temel işlemler hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132920"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="d6c80-103">.NET 'te temel dize Işlemleri</span><span class="sxs-lookup"><span data-stu-id="d6c80-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="d6c80-104">Uygulamalar genellikle kullanıcı girişine göre iletiler oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="d6c80-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="d6c80-105">Örneğin, Web siteleri, kullanıcının adını içeren özelleştirilmiş bir selamlama ile yeni bir oturum açan kullanıcıya yanıt verebilmesi için sık görülen bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="d6c80-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="d6c80-106"><xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıflarında çeşitli yöntemler, Kullanıcı arabiriminizdeki görüntüleme için özel dizeleri dinamik olarak oluşturmanız sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="d6c80-107">Bu yöntemler Ayrıca bayt dizelerinden yeni dizeler oluşturma, dizelerin değerlerini karşılaştırma ve mevcut dizeleri değiştirme gibi birçok temel dize işlemi gerçekleştirmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d6c80-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6c80-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d6c80-108">In This Section</span></span>  
 [<span data-ttu-id="d6c80-109">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d6c80-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="d6c80-110">Nesneleri dizelere dönüştürmenin ve dizeleri birleştirmenin temel yollarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="d6c80-111">Karakterleri Kırpma ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="d6c80-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="d6c80-112">Bir dizedeki karakterlerin nasıl kırpılacağını veya kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="d6c80-113">Dizeleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="d6c80-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="d6c80-114">Bir dizeye karakterlerin veya boş boşlukların nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="d6c80-115">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="d6c80-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="d6c80-116">İki veya daha fazla dizenin içeriğini karşılaştırmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="d6c80-117">Büyük/Küçük Harf Değiştirme</span><span class="sxs-lookup"><span data-stu-id="d6c80-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="d6c80-118">Bir dize içindeki karakterlerin durum durumunun nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="d6c80-119">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="d6c80-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="d6c80-120"><xref:System.Text.StringBuilder> sınıfıyla dinamik dize nesnelerinin nasıl oluşturulduğunu ve değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="d6c80-121">Nasıl yapılır: Temel Dize İşlemeleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d6c80-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="d6c80-122">Temel dize işlemlerinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6c80-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d6c80-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d6c80-123">Related Sections</span></span>  
 [<span data-ttu-id="d6c80-124">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d6c80-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="d6c80-125">Bir türün başka bir türe nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="d6c80-126">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="d6c80-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="d6c80-127">Biçim belirticilerini kullanarak dizelerin nasıl biçimlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d6c80-127">Describes how to format strings using format specifiers.</span></span>
