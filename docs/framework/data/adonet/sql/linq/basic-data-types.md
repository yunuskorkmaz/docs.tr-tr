---
title: "Temel veri türleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9249a98c8a6c60d51039b6348a41c4f5805865f0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="basic-data-types"></a><span data-ttu-id="b022d-102">Temel veri türleri</span><span class="sxs-lookup"><span data-stu-id="b022d-102">Basic Data Types</span></span>
<span data-ttu-id="b022d-103">Transact-SQL önce LINQ to SQL sorguları Çevir çünkü bunlar Microsoft SQL Server üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b022d-103">Because LINQ to SQL queries translate to Transact-SQL before they are executed on the Microsoft SQL Server.</span></span> <span data-ttu-id="b022d-104">LINQ-SQL temel veri türleri için SQL Server mu aynı yerleşik işlevlerinin çoğunu destekler.</span><span class="sxs-lookup"><span data-stu-id="b022d-104">LINQ to SQL supports much of the same built-in functionality that SQL Server does for basic data types.</span></span>  
  
## <a name="casting"></a><span data-ttu-id="b022d-105">Atama</span><span class="sxs-lookup"><span data-stu-id="b022d-105">Casting</span></span>  
 <span data-ttu-id="b022d-106">SQL Server içinde benzer geçerli bir dönüştürme ise açık veya kapalı atamaları bir hedef CLR türü bir kaynaktan CLR türü etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b022d-106">Implicit or explicit casts are enabled from a source CLR type to a target CLR type if there is a similar valid conversion within SQL Server.</span></span> <span data-ttu-id="b022d-107">CLR atama hakkında daha fazla bilgi için bkz: [CType işlevi](~/docs/visual-basic/language-reference/functions/ctype-function.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ve [olarak](~/docs/csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="b022d-107">For more information about CLR casting, see [CType Function](~/docs/visual-basic/language-reference/functions/ctype-function.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) and [as](~/docs/csharp/language-reference/keywords/as.md).</span></span> <span data-ttu-id="b022d-108">Dönüştürme işleminden sonra atamaları doğal olarak hedef türe eşleme diğer CLR ifadeleri davranışını eşleşecek şekilde bir CLR ifadesi üzerinde gerçekleştirilen işlemler davranışını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b022d-108">After conversion, casts change the behavior of operations performed on a CLR expression to match the behavior of other CLR expressions that naturally map to the destination type.</span></span> <span data-ttu-id="b022d-109">Atamalar da devralma eşleme bağlamında çevrilebilir.</span><span class="sxs-lookup"><span data-stu-id="b022d-109">Casts are also translatable in the context of inheritance mapping.</span></span> <span data-ttu-id="b022d-110">Böylece alt özgü verilerine erişilebilir nesneler için daha özel varlık türlerinde çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b022d-110">Objects can be cast to more specific entity subtypes so that their subtype-specific data can be accessed.</span></span>  
  
## <a name="equality-operators"></a><span data-ttu-id="b022d-111">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="b022d-111">Equality Operators</span></span>  
 <span data-ttu-id="b022d-112">LINQ-SQL, SQL sorguları için LINQ içinde temel veri türleri hakkında aşağıdaki eşitlik işleçleri destekler:</span><span class="sxs-lookup"><span data-stu-id="b022d-112">LINQ to SQL supports the following equality operators on basic data types inside LINQ to SQL queries:</span></span>  
  
-   <span data-ttu-id="b022d-113">Eşit ve eşitsizlik işleci: eşitlik ve eşitsizlik işleçleri için sayısal desteklenir <xref:System.Boolean>, <xref:System.DateTime>, ve <xref:System.TimeSpan> türleri.</span><span class="sxs-lookup"><span data-stu-id="b022d-113">Equal and Inequality Operator: Equality and inequality operators are supported for numeric <xref:System.Boolean>, <xref:System.DateTime>, and <xref:System.TimeSpan> types.</span></span> <span data-ttu-id="b022d-114">Hakkında daha fazla bilgi için [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] işleçleri `=` ve `<>`, bkz: [Karşılaştırma işleçleri](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="b022d-114">For more about [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] operators `=` and `<>`, see [Comparison Operators](~/docs/visual-basic/language-reference/operators/comparison-operators.md).</span></span> <span data-ttu-id="b022d-115">C# Karşılaştırma işleçleri hakkında daha fazla bilgi için `==` ve `!=`, bkz: [== işleci](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) ve [! = işleci](~/docs/csharp/language-reference/operators/not-equal-operator.md)sırasıyla</span><span class="sxs-lookup"><span data-stu-id="b022d-115">For more information about C# comparison operators `==` and `!=`, see [== Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) and [!= Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md), respectively</span></span>  
  
-   <span data-ttu-id="b022d-116">Is işleci: `IS` işleci devralma eşleme kullanıldığında, desteklenen bir çeviri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="b022d-116">Is operator: The `IS` operator has a supported translation when inheritance mapping is being used.</span></span> <span data-ttu-id="b022d-117">Bu doğrudan ayrıştırıcı sütunun sınama yerine bir nesne belirli bir varlık türü ve ayrıştırıcı sütunun bir denetim için çevrilen olup olmadığını belirlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b022d-117">It can be used instead of directly testing the discriminator column to determine whether an object is of a specific entity type, and is translated to a check on the discriminator column.</span></span> <span data-ttu-id="b022d-118">Visual Basic ve C# işleçleri hakkında daha fazla bilgi için bkz: [Is işlecini](~/docs/visual-basic/language-reference/operators/is-operator.md) ve [olan](~/docs/csharp/language-reference/keywords/is.md).</span><span class="sxs-lookup"><span data-stu-id="b022d-118">For more information about the Visual Basic and C# Is operators, see [Is Operator](~/docs/visual-basic/language-reference/operators/is-operator.md) and [is](~/docs/csharp/language-reference/keywords/is.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b022d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b022d-119">See Also</span></span>  
 [<span data-ttu-id="b022d-120">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="b022d-120">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="b022d-121">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b022d-121">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
