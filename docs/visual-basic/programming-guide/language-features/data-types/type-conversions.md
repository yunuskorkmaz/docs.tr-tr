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
ms.openlocfilehash: ee8700ea757cee9c20e2598de029f54ae33a7114
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090163"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="372cf-102">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="372cf-102">Type Conversions in Visual Basic</span></span>

<span data-ttu-id="372cf-103">Bir değeri bir veri türünden başka bir türe değiştirme işlemi *dönüştürme*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="372cf-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="372cf-104">Dönüşümler, dahil edilen türlerin veri kapasiteye bağlı olarak, *genişletme* veya *daraltma*.</span><span class="sxs-lookup"><span data-stu-id="372cf-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="372cf-105">Bunlar ayrıca, kaynak kodundaki sözdizimine bağlı olarak *örtük* veya *açıktır*.</span><span class="sxs-lookup"><span data-stu-id="372cf-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="372cf-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="372cf-106">In This Section</span></span>  

 [<span data-ttu-id="372cf-107">Genişletme ve Daraltma Dönüşümleri</span><span class="sxs-lookup"><span data-stu-id="372cf-107">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)  
 <span data-ttu-id="372cf-108">Hedef türün verileri tutabilir olup olmadığı sınıflandırılan dönüştürmeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="372cf-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="372cf-109">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="372cf-109">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)  
 <span data-ttu-id="372cf-110">Visual Basic otomatik olarak gerçekleştirip gerçekleştirmediğini sınıflandırılan dönüştürmeleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="372cf-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="372cf-111">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="372cf-111">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="372cf-112">Dizeler ve sayısal, `Boolean` ya da tarih/saat değerleri arasında dönüştürme gösterir.</span><span class="sxs-lookup"><span data-stu-id="372cf-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="372cf-113">Nasıl yapılır: Visual Basic'te Bir Nesneyi Başka Bir Türe Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="372cf-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="372cf-114">Bir `Object` değişkenin diğer veri türlerine nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="372cf-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="372cf-115">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="372cf-115">Array Conversions</span></span>](array-conversions.md)  
 <span data-ttu-id="372cf-116">Farklı veri türlerinin dizileri arasında dönüştürme işleminde size adım adım.</span><span class="sxs-lookup"><span data-stu-id="372cf-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="372cf-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="372cf-117">Related Sections</span></span>  

 [<span data-ttu-id="372cf-118">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="372cf-118">Data Types</span></span>](index.md)  
 <span data-ttu-id="372cf-119">Visual Basic veri türlerini tanıtır ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="372cf-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="372cf-120">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="372cf-120">Data Types</span></span>](../../../language-reference/data-types/index.md)  
 <span data-ttu-id="372cf-121">Visual Basic tarafından sağlanan elemensel veri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="372cf-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="372cf-122">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="372cf-122">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)  
 <span data-ttu-id="372cf-123">Veri türleriyle çalışırken ortaya çıkabilecek bazı yaygın sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="372cf-123">Discusses some common problems that can arise when working with data types.</span></span>
