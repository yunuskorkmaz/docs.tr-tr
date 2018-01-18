---
title: "Null semantiği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a97017ae-d634-4cf3-bbaf-054a528fd683
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8d32f73c8c2095c23ec164ad40fd1ab27ef1153a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="null-semantics"></a><span data-ttu-id="d586d-102">Null semantiği</span><span class="sxs-lookup"><span data-stu-id="d586d-102">Null Semantics</span></span>
<span data-ttu-id="d586d-103">Aşağıdaki tabloda, çeşitli bölümlerine bağlantılar sağlanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri nerede `null` (`Nothing` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) sorunları ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d586d-103">The following table provides links to various parts of the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] documentation where `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) issues are discussed.</span></span>  
  
|<span data-ttu-id="d586d-104">Konu</span><span class="sxs-lookup"><span data-stu-id="d586d-104">Topic</span></span>|<span data-ttu-id="d586d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d586d-105">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d586d-106">SQL-CLR Tür Uyumsuzlukları</span><span class="sxs-lookup"><span data-stu-id="d586d-106">SQL-CLR Type Mismatches</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mismatches.md)|<span data-ttu-id="d586d-107">Üç durumlu SQL Boolean iki durumlu ortak dil çalışma zamanı (CLR) karşı tartışması bu konuda "Null semantiği" kısmında bulunur <xref:System.Boolean>, sabit `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ve `null` (C#) ve benzer diğer sorunları.</span><span class="sxs-lookup"><span data-stu-id="d586d-107">The "Null Semantics" section of this topic includes discussion of the three-state SQL Boolean versus the two-state common language runtime (CLR) <xref:System.Boolean>, the literal `Nothing` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and `null` (C#), and other similar issues.</span></span>|  
|[<span data-ttu-id="d586d-108">Standart Sorgu İşleci Çevirisi</span><span class="sxs-lookup"><span data-stu-id="d586d-108">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)|<span data-ttu-id="d586d-109">Bu konunun "Null semantiği" bölümüne null karşılaştırma semantiği açıklar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d586d-109">The "Null Semantics" section of this topic describes null comparison semantics in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|  
|[<span data-ttu-id="d586d-110">System.String Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="d586d-110">System.String Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/system-string-methods.md)|<span data-ttu-id="d586d-111">Bu konunun "Farklar gelen .NET" bölümüne 0'dan döndürmek nasıl açıklar <xref:System.String.LastIndexOf%2A> dizesi null veya bulunan konumu 0 olduğu anlamına gelebilir.</span><span class="sxs-lookup"><span data-stu-id="d586d-111">The "Differences from .NET" section of this topic describes how a return of 0 from <xref:System.String.LastIndexOf%2A> might mean either that the string is null or that the found position is 0.</span></span>|  
|[<span data-ttu-id="d586d-112">Sayısal Dizideki Değerlerin Toplamını Hesaplama</span><span class="sxs-lookup"><span data-stu-id="d586d-112">Compute the Sum of Values in a Numeric Sequence</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/compute-the-sum-of-values-in-a-numeric-sequence.md)|<span data-ttu-id="d586d-113">Açıklar nasıl <xref:System.Linq.Enumerable.Sum%2A> işleci hesaplar için `null` (`Nothing` içinde [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) yerine boş bir dizi veya yalnızca null içeren bir dizi için 0.</span><span class="sxs-lookup"><span data-stu-id="d586d-113">Describes how the <xref:System.Linq.Enumerable.Sum%2A> operator evaluates to `null` (`Nothing` in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) instead of 0 for a sequence that contains only nulls or for an empty sequence.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d586d-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d586d-114">See Also</span></span>  
 [<span data-ttu-id="d586d-115">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d586d-115">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
