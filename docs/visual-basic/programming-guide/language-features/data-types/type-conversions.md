---
title: Visual Basic'de Tür Dönüştürmeleri
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: 7f1a571cda4f68222c5c03c3a8fe31c29eafd8c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647220"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="14ae8-102">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="14ae8-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="14ae8-103">Bir değeri başka bir türüne bir veri türünden değiştirme işlemi adlı *dönüştürme*.</span><span class="sxs-lookup"><span data-stu-id="14ae8-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="14ae8-104">Dönüşümler olan ya da *genişletme* veya *daraltma*ilgili türleri veri kapasiteleri bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="14ae8-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="14ae8-105">Ayrıca oldukları *örtük* veya *açık*sözdizimi kaynak koduna bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="14ae8-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14ae8-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="14ae8-106">In This Section</span></span>  
 [<span data-ttu-id="14ae8-107">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="14ae8-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="14ae8-108">Verileri hedef türü olup olmadığını tutabilir göre sınıflandırılmış dönüşümleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14ae8-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="14ae8-109">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="14ae8-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="14ae8-110">Olup Visual Basic bunları otomatik olarak gerçekleştirir göre sınıflandırılmış dönüşümleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="14ae8-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="14ae8-111">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="14ae8-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="14ae8-112">Dizeler ve sayısal arasında dönüştürme gösterilmektedir `Boolean`, veya tarih/saat değerleri.</span><span class="sxs-lookup"><span data-stu-id="14ae8-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="14ae8-113">Nasıl yapılır: Visual Basic'de başka bir tür nesneyi Dönüştür</span><span class="sxs-lookup"><span data-stu-id="14ae8-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="14ae8-114">Dönüştürülecek gösterilmiştir bir `Object` herhangi bir veri türü için değişken.</span><span class="sxs-lookup"><span data-stu-id="14ae8-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="14ae8-115">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="14ae8-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="14ae8-116">Farklı veri türleri dizilerine dönüştürme süreci adımları.</span><span class="sxs-lookup"><span data-stu-id="14ae8-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="14ae8-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="14ae8-117">Related Sections</span></span>  
 [<span data-ttu-id="14ae8-118">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="14ae8-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="14ae8-119">Visual Basic veri türleri tanıtır ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="14ae8-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="14ae8-120">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="14ae8-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 <span data-ttu-id="14ae8-121">Visual Basic tarafından sağlanan başlangıç veri türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="14ae8-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="14ae8-122">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="14ae8-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="14ae8-123">Veri türleri ile çalışırken ortaya çıkabilecek bazı yaygın sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="14ae8-123">Discusses some common problems that can arise when working with data types.</span></span>
