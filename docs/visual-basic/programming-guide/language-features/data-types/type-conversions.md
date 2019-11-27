---
title: Tür Dönüştürmeleri
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
ms.openlocfilehash: fbf0c9877cf9a9b4364c8c058c61e847ad7bf049
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348717"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="0d54b-102">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="0d54b-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="0d54b-103">Bir değeri bir veri türünden başka bir türe değiştirme işlemi *dönüştürme*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="0d54b-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="0d54b-104">Dönüşümler, dahil edilen türlerin veri kapasiteye bağlı olarak, *genişletme* veya *daraltma*.</span><span class="sxs-lookup"><span data-stu-id="0d54b-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="0d54b-105">Bunlar ayrıca, kaynak kodundaki sözdizimine bağlı olarak *örtük* veya *açıktır*.</span><span class="sxs-lookup"><span data-stu-id="0d54b-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d54b-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="0d54b-106">In This Section</span></span>  
 [<span data-ttu-id="0d54b-107">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="0d54b-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="0d54b-108">Hedef türün verileri tutabilir olup olmadığı sınıflandırılan dönüştürmeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d54b-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="0d54b-109">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0d54b-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="0d54b-110">Visual Basic otomatik olarak gerçekleştirip gerçekleştirmediğini sınıflandırılan dönüştürmeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d54b-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="0d54b-111">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0d54b-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="0d54b-112">Dizeler ve sayısal, `Boolean`veya tarih/saat değerleri arasında dönüştürme gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d54b-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="0d54b-113">Nasıl yapılır: Visual Basic bir nesneyi başka bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="0d54b-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="0d54b-114">Bir `Object` değişkeninin diğer veri türlerine nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d54b-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="0d54b-115">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="0d54b-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="0d54b-116">Farklı veri türlerinin dizileri arasında dönüştürme işleminde size adım adım.</span><span class="sxs-lookup"><span data-stu-id="0d54b-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d54b-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0d54b-117">Related Sections</span></span>  
 [<span data-ttu-id="0d54b-118">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0d54b-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="0d54b-119">Visual Basic veri türlerini tanıtır ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d54b-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="0d54b-120">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="0d54b-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="0d54b-121">Visual Basic tarafından sağlanan elemensel veri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="0d54b-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="0d54b-122">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="0d54b-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="0d54b-123">Veri türleriyle çalışırken ortaya çıkabilecek bazı yaygın sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="0d54b-123">Discusses some common problems that can arise when working with data types.</span></span>
