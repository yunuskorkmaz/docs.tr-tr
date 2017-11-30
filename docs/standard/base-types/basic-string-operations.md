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
ms.openlocfilehash: f241b99f97cad081a65fd8654169e444a1b588cb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="71599-102">.NET temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="71599-102">Basic String Operations in .NET</span></span>
<span data-ttu-id="71599-103">Uygulamalar genellikle kullanıcı girişini temel alarak iletileri oluşturarak kullanıcılara yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="71599-103">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="71599-104">Örneğin, yeni oturum açmış olan bir kullanıcı kullanıcı adını içeren özelleştirilmiş bir karşılama yanıtlamak Web siteleri için seyrek değil.</span><span class="sxs-lookup"><span data-stu-id="71599-104">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="71599-105">Çeşitli yöntemlerin <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfları dinamik olarak, kullanıcı arabiriminde görüntülenecek özel dizeleri oluşturmak izin verir.</span><span class="sxs-lookup"><span data-stu-id="71599-105">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="71599-106">Bu yöntemler bir dizi bayt dizileri yeni dizeler oluşturma, dize değerleri karşılaştırma ve varolan dizeleri değiştirme gibi temel dize işlemleri gerçekleştirmenize yardımcı.</span><span class="sxs-lookup"><span data-stu-id="71599-106">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71599-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="71599-107">In This Section</span></span>  
 [<span data-ttu-id="71599-108">Yeni dizeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="71599-108">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="71599-109">Nesneleri dizelere dönüştürme ve dizeleri birleştirmek için temel yolları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71599-109">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="71599-110">Karakterleri kırpma ve kaldırma</span><span class="sxs-lookup"><span data-stu-id="71599-110">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="71599-111">Kırpma veya bir dizedeki karakterleri Kaldır açıklar.</span><span class="sxs-lookup"><span data-stu-id="71599-111">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="71599-112">Dizeleri doldurma</span><span class="sxs-lookup"><span data-stu-id="71599-112">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="71599-113">Karakter veya boş alanları bir dizeye nasıl ekleneceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="71599-113">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="71599-114">Dizeleri karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="71599-114">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="71599-115">İki veya daha fazla içeriğini karşılaştırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="71599-115">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="71599-116">Durum değiştirme</span><span class="sxs-lookup"><span data-stu-id="71599-116">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="71599-117">Bir dize karakterlerine durumunun değiştirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="71599-117">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="71599-118">StringBuilder sınıfını kullanma</span><span class="sxs-lookup"><span data-stu-id="71599-118">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="71599-119">İle dinamik dize nesneleri oluşturup değiştirmesi açıklar <xref:System.Text.StringBuilder> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="71599-119">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="71599-120">Nasıl yapılır: temel dize işlemeleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="71599-120">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="71599-121">Temel dize işlemleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="71599-121">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="71599-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="71599-122">Related Sections</span></span>  
 [<span data-ttu-id="71599-123">.NET tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="71599-123">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="71599-124">Bir tür başka bir türüne dönüştürün açıklar.</span><span class="sxs-lookup"><span data-stu-id="71599-124">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="71599-125">Biçimlendirme türleri</span><span class="sxs-lookup"><span data-stu-id="71599-125">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="71599-126">Biçim dizeleri biçim belirticilerini kullanma açıklar.</span><span class="sxs-lookup"><span data-stu-id="71599-126">Describes how to format strings using format specifiers.</span></span>
