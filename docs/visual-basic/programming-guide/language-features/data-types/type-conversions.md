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
ms.openlocfilehash: 026b2a250abfac0782feb0946bc50a94f504f7ed
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800670"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="c0352-102">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="c0352-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="c0352-103">Değeri bir veri türünden başka bir türe değiştirme işleminin adlı *dönüştürme*.</span><span class="sxs-lookup"><span data-stu-id="c0352-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="c0352-104">Dönüştürmeleri değerleri *genişletme* veya *daraltma*türleri dahil veri kapasiteleri bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="c0352-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="c0352-105">Ayrıca bunlar *örtük* veya *açık*kaynak kodunda sözdizimi bağlı olarak.</span><span class="sxs-lookup"><span data-stu-id="c0352-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0352-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c0352-106">In This Section</span></span>  
 [<span data-ttu-id="c0352-107">Genişletme ve Daraltma Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="c0352-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="c0352-108">Dönüştürmeler verileri hedef türü olup olmadığını tutabilir tarafından sınıflandırılan açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0352-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="c0352-109">Örtük ve Açık Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c0352-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="c0352-110">Dönüştürmeleri olup Visual Basic bunları otomatik olarak gerçekleştirir tarafından sınıflandırılan açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c0352-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="c0352-111">Dizeler ve Diğer Türler Arasında Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c0352-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="c0352-112">Dizeler ve sayısal arasında dönüştürme gösterilmektedir `Boolean`, veya tarih/saat değerleri.</span><span class="sxs-lookup"><span data-stu-id="c0352-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="c0352-113">Nasıl yapılır: bir nesneyi Visual Basic'de başka bir türe dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c0352-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="c0352-114">Nasıl dönüştürüleceğini gösterir bir `Object` değişkenini herhangi bir veri türü.</span><span class="sxs-lookup"><span data-stu-id="c0352-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="c0352-115">Dizi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c0352-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="c0352-116">Farklı veri türlerinin dizileri arasında dönüştürme işleminde adımları.</span><span class="sxs-lookup"><span data-stu-id="c0352-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0352-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c0352-117">Related Sections</span></span>  
 [<span data-ttu-id="c0352-118">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c0352-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="c0352-119">Visual Basic veri türlerini tanıtır ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c0352-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="c0352-120">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="c0352-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="c0352-121">Visual Basic tarafından sağlanan başlangıç veri türleri listeler.</span><span class="sxs-lookup"><span data-stu-id="c0352-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="c0352-122">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="c0352-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="c0352-123">Veri türleri ile çalışırken ortaya çıkabilecek bazı yaygın sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0352-123">Discusses some common problems that can arise when working with data types.</span></span>
