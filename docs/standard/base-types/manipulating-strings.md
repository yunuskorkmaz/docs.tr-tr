---
title: ".NET Framework'te Dizeleri Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], manipulating
- manipulating strings
ms.assetid: d4568ff3-9f83-4549-acd8-47aec2194ac0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b1db77672928ebf4a03b69b4bef1af80f04124b5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="manipulating-strings-in-net"></a><span data-ttu-id="d0b9e-102">.NET dizeleri düzenleme</span><span class="sxs-lookup"><span data-stu-id="d0b9e-102">Manipulating Strings in .NET</span></span>
<span data-ttu-id="d0b9e-103">.NET verimli bir şekilde oluşturmak, karşılaştırın ve dizeleri değiştirmek etkinleştirmeniz yanı sıra büyük miktarlarda metin ve veri aramak, kaldırmak ve metin kalıplarını değiştirmek için hızla ayrıştırma yordamları kapsamlı bir kümesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-103">.NET provides an extensive set of routines that enable you to efficiently create, compare, and modify strings as well as rapidly parse large amounts of text and data to search for, remove, and replace text patterns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0b9e-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d0b9e-104">In This Section</span></span>  
 [<span data-ttu-id="d0b9e-105">Dizeleri Kullanmak için En İyi Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="d0b9e-105">Best Practices for Using Strings</span></span>](../../../docs/standard/base-types/best-practices-strings.md)  
 <span data-ttu-id="d0b9e-106">Dize sıralama, karşılaştırma ve .NET büyük/küçük harf yöntemleri inceler ve dize işleme yöntemi seçme önerileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-106">Examines string-sorting, comparison, and casing methods in .NET, and provides recommendations for selecting a string-handling method .</span></span>  
  
 [<span data-ttu-id="d0b9e-107">.NET normal ifadeler</span><span class="sxs-lookup"><span data-stu-id="d0b9e-107">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="d0b9e-108">Dil öğeleri, normal ifade davranışı ve örnekler dahil .NET normal ifadeler hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-108">Provides detailed information about .NET regular expressions, including language elements, regular expression behavior, and examples.</span></span>  
  
 [<span data-ttu-id="d0b9e-109">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d0b9e-109">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 <span data-ttu-id="d0b9e-110">Tarafından sağlanan dize işlemleri açıklanır <xref:System.String?displayProperty=nameWithType> ve <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfları, bayt dizileri yeni dizeler oluşturma, dize değerleri karşılaştırma ve varolan dizeleri değiştirme gibi.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-110">Describes string operations provided by the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes, including creating new strings from arrays of bytes, comparing string values, and modifying existing strings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0b9e-111">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d0b9e-111">Related Sections</span></span>  
 [<span data-ttu-id="d0b9e-112">.NET içinde Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d0b9e-112">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="d0b9e-113">.NET kullanarak türlerine dönüştürmek için kullanılan kuralları ve teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-113">Explains the techniques and rules used to convert types using .NET.</span></span>  
  
 [<span data-ttu-id="d0b9e-114">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="d0b9e-114">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="d0b9e-115">Biçimlendirme uygulamak için temel sınıf kitaplığı kullanma, sayısal türler biçimlendirme, dize türleri biçimlendirme ve belirli bir kültür için biçimlendirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-115">Provides how to use the base class library to implement formatting, how to format numeric types, how to format string types, and how to format for a specific culture.</span></span>  
  
 [<span data-ttu-id="d0b9e-116">Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="d0b9e-116">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 <span data-ttu-id="d0b9e-117">Nesneleri bu nesnelerin dizesi ifadeleri tarafından tanımlanan değerlerle başlatmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-117">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="d0b9e-118">Ayrıştırma, biçimlendirme ters bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="d0b9e-118">Parsing is the inverse operation of formatting.</span></span>
