---
title: "Visual Basic'de Tür Dönüştürmeleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b46d813b4fcadd975d87b235e9f3350a365949fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="300fa-102">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="300fa-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="300fa-103">Bir değeri başka bir türüne bir veri türünden değiştirme işlemi adlı *dönüştürme*.</span><span class="sxs-lookup"><span data-stu-id="300fa-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="300fa-104">Dönüşümler olan ya da *genişletme* veya *daraltma*ilgili türleri veri kapasiteleri bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="300fa-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="300fa-105">Ayrıca oldukları *örtük* veya *açık*sözdizimi kaynak koduna bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="300fa-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="300fa-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="300fa-106">In This Section</span></span>  
 [<span data-ttu-id="300fa-107">Genişletme ve daraltma dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="300fa-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="300fa-108">Verileri hedef türü olup olmadığını tutabilir göre sınıflandırılmış dönüşümleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="300fa-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="300fa-109">Örtük ve açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="300fa-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="300fa-110">Tarafından mı yoksa sınıflandırılmış dönüşümleri anlatılmaktadır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] otomatik olarak gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="300fa-110">Discusses conversions classified by whether [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] performs them automatically.</span></span>  
  
 [<span data-ttu-id="300fa-111">Dizeler ve diğer türleri arasında dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="300fa-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="300fa-112">Dizeler ve sayısal arasında dönüştürme gösterilmektedir `Boolean`, veya tarih/saat değerleri.</span><span class="sxs-lookup"><span data-stu-id="300fa-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="300fa-113">Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür</span><span class="sxs-lookup"><span data-stu-id="300fa-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="300fa-114">Dönüştürülecek gösterilmiştir bir `Object` herhangi bir veri türü için değişken.</span><span class="sxs-lookup"><span data-stu-id="300fa-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="300fa-115">Dizi dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="300fa-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="300fa-116">Farklı veri türleri dizilerine dönüştürme süreci adımları.</span><span class="sxs-lookup"><span data-stu-id="300fa-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="300fa-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="300fa-117">Related Sections</span></span>  
 [<span data-ttu-id="300fa-118">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="300fa-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="300fa-119">Tanıtır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] veri türlerini ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="300fa-119">Introduces the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="300fa-120">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="300fa-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="300fa-121">Tarafından sağlanan başlangıç veri türleri listeler [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="300fa-121">Lists the elementary data types supplied by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 [<span data-ttu-id="300fa-122">Veri türleri sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="300fa-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="300fa-123">Veri türleri ile çalışırken ortaya çıkabilecek bazı yaygın sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="300fa-123">Discusses some common problems that can arise when working with data types.</span></span>
