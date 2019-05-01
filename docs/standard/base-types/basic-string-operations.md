---
title: .NET içinde temel dize işlemleri
description: Dizeleri gerçekleştirebileceğiniz temel işlemleri hakkında bilgi edinin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
author: rpetrusha
ms.author: ronpet
ms.custom: seadec18
ms.openlocfilehash: 8621e79ad6e305f3859dc269965ecd216081f695
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936818"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="fda18-103">.NET içinde temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="fda18-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="fda18-104">Uygulamalar genellikle kullanıcılar için kullanıcı girişini temel alarak iletileri oluşturarak yanıt.</span><span class="sxs-lookup"><span data-stu-id="fda18-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="fda18-105">Örneğin, yeni oturum açan bir kullanıcı kullanıcı adını içeren özelleştirilmiş bir Karşılama ile yanıt vermek Web siteleri için sık karşılaşılan bir durum değil.</span><span class="sxs-lookup"><span data-stu-id="fda18-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="fda18-106">Çeşitli yöntemlerin <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfları, kullanıcı arabiriminde görüntülenecek özel dizeleri dinamik olarak oluşturmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fda18-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="fda18-107">Bu yöntemler bir dizi bayt dizilerden yeni dizeler oluşturma, değerleri dize karşılaştırma ve mevcut dizeleri değiştirme gibi temel dize işlemleri gerçekleştirmenize yardımcı.</span><span class="sxs-lookup"><span data-stu-id="fda18-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fda18-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fda18-108">In This Section</span></span>  
 [<span data-ttu-id="fda18-109">Yeni Dizeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fda18-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="fda18-110">Nesneleri dizeleri dönüştürmek için ve dizeleri birleştirmek için temel yolu anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fda18-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="fda18-111">Karakterleri Kırpma ve Kaldırma</span><span class="sxs-lookup"><span data-stu-id="fda18-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="fda18-112">Bir dizedeki karakterleri kaldırın veya Trim açıklar.</span><span class="sxs-lookup"><span data-stu-id="fda18-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="fda18-113">Dizeleri Doldurma</span><span class="sxs-lookup"><span data-stu-id="fda18-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="fda18-114">Karakterler veya boşluk boş bir dizeye nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fda18-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="fda18-115">Dizeleri Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="fda18-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="fda18-116">İki veya daha fazla dizeleri içeriğini karşılaştırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="fda18-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="fda18-117">Büyük/Küçük Harf Değiştirme</span><span class="sxs-lookup"><span data-stu-id="fda18-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="fda18-118">Bir dizedeki karakterlerin değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="fda18-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="fda18-119">StringBuilder Sınıfını Kullanma</span><span class="sxs-lookup"><span data-stu-id="fda18-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="fda18-120">İle dinamik dize nesneleri oluşturup değiştirmesi açıklar <xref:System.Text.StringBuilder> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="fda18-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="fda18-121">Nasıl yapılır: Temel dize işlemeleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="fda18-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="fda18-122">Temel dize işlemleri kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fda18-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fda18-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="fda18-123">Related Sections</span></span>  
 [<span data-ttu-id="fda18-124">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fda18-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="fda18-125">Bir tür başka bir türe dönüştürmenize olanak açıklar.</span><span class="sxs-lookup"><span data-stu-id="fda18-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="fda18-126">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="fda18-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="fda18-127">Biçim belirticilerini kullanarak dizelerinin nasıl biçimlendirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="fda18-127">Describes how to format strings using format specifiers.</span></span>
