---
description: 'Daha fazla bilgi edinin: karakter veri türleri (Visual Basic)'
title: Karakter Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 2197c0210cb0c2287baff9856889334f5f95bd4d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466399"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="b5ad4-103">Karakter Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5ad4-103">Character Data Types (Visual Basic)</span></span>

<span data-ttu-id="b5ad4-104">Visual Basic, yazdırılabilir ve görüntülenebilen karakterlerle uğraşmak için *karakter veri türleri* sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-104">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="b5ad4-105">Her ikisi de Unicode karakterlerle ilgilenir, `Char` ancak `String` sonsuz sayıda karakter içeren tek bir karakter tutar.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-105">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="b5ad4-106">Visual Basic veri türlerinin yan yana karşılaştırmasını görüntüleyen bir tablo için bkz. [veri türleri](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5ad4-106">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="b5ad4-107">Karakter türü</span><span class="sxs-lookup"><span data-stu-id="b5ad4-107">Char Type</span></span>  

 <span data-ttu-id="b5ad4-108">`Char`Veri türü, tek bir iki baytlık (16 bit) Unicode karakterdir.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-108">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="b5ad4-109">Bir değişken her zaman tam olarak bir karakter depoluyorsa, olarak bildirin `Char` .</span><span class="sxs-lookup"><span data-stu-id="b5ad4-109">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="b5ad4-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5ad4-110">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="b5ad4-111">Bir veya değişkenindeki olası her bir değer, `Char` `String` Unicode karakter kümesindeki bir *kod noktasıdır* veya karakter kodudur.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-111">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="b5ad4-112">Unicode karakterler temel ASCII karakter kümesini, diğer diğer alfabe harflerini, vurguları, para birimi sembollerini, kesirleri, vurguları ve matematik ve teknik sembolleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-112">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b5ad4-113">Unicode karakter kümesi, D800-DFFF (55296 ile 55551 ondalık) ile birlikte, tek bir kod noktasını temsil etmek için 2 16-bit değerleri gerektiren *yedek çiftleri* için bu kod noktalarını ayırır.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-113">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="b5ad4-114">Bir `Char` değişken bir vekil çifti tutamaz ve `String` Bu tür bir çift tutmak için iki konum kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-114">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="b5ad4-115">Daha fazla bilgi için bkz. [char veri türü](../../../language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b5ad4-115">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="b5ad4-116">Dize türü</span><span class="sxs-lookup"><span data-stu-id="b5ad4-116">String Type</span></span>  

 <span data-ttu-id="b5ad4-117">`String`Veri türü sıfır veya daha fazla iki baytlık (16 bit) Unicode karakterden oluşan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-117">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="b5ad4-118">Bir değişken belirsiz sayıda karakter içeriyorsa, olarak bildirin `String` .</span><span class="sxs-lookup"><span data-stu-id="b5ad4-118">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="b5ad4-119">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="b5ad4-119">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="b5ad4-120">Daha fazla bilgi için bkz. [dize veri türü](../../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b5ad4-120">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ad4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5ad4-121">See also</span></span>

- [<span data-ttu-id="b5ad4-122">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b5ad4-122">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="b5ad4-123">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b5ad4-123">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="b5ad4-124">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="b5ad4-124">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="b5ad4-125">Değer türleri ve başvuru türleri</span><span class="sxs-lookup"><span data-stu-id="b5ad4-125">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="b5ad4-126">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="b5ad4-126">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="b5ad4-127">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="b5ad4-127">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="b5ad4-128">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="b5ad4-128">Type Characters</span></span>](type-characters.md)
