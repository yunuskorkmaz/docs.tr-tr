---
title: Karakter Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 33dd4c62776ae8c5ec0ce0a6d0858a7ed0d047fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401998"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="277e8-102">Karakter Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="277e8-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="277e8-103">Visual Basic, yazdırılabilir ve görüntülenebilen karakterlerle uğraşmak için *karakter veri türleri* sağlar.</span><span class="sxs-lookup"><span data-stu-id="277e8-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="277e8-104">Her ikisi de Unicode karakterlerle ilgilenir, `Char` ancak `String` sonsuz sayıda karakter içeren tek bir karakter tutar.</span><span class="sxs-lookup"><span data-stu-id="277e8-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="277e8-105">Visual Basic veri türlerinin yan yana karşılaştırmasını görüntüleyen bir tablo için bkz. [veri türleri](../../../language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="277e8-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="277e8-106">Karakter türü</span><span class="sxs-lookup"><span data-stu-id="277e8-106">Char Type</span></span>  
 <span data-ttu-id="277e8-107">`Char`Veri türü, tek bir iki baytlık (16 bit) Unicode karakterdir.</span><span class="sxs-lookup"><span data-stu-id="277e8-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="277e8-108">Bir değişken her zaman tam olarak bir karakter depoluyorsa, olarak bildirin `Char` .</span><span class="sxs-lookup"><span data-stu-id="277e8-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="277e8-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="277e8-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="277e8-110">Bir veya değişkenindeki olası her bir değer, `Char` `String` Unicode karakter kümesindeki bir *kod noktasıdır*veya karakter kodudur.</span><span class="sxs-lookup"><span data-stu-id="277e8-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="277e8-111">Unicode karakterler temel ASCII karakter kümesini, diğer diğer alfabe harflerini, vurguları, para birimi sembollerini, kesirleri, vurguları ve matematik ve teknik sembolleri içerir.</span><span class="sxs-lookup"><span data-stu-id="277e8-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="277e8-112">Unicode karakter kümesi, D800-DFFF (55296 ile 55551 ondalık) ile birlikte, tek bir kod noktasını temsil etmek için 2 16-bit değerleri gerektiren *yedek çiftleri*için bu kod noktalarını ayırır.</span><span class="sxs-lookup"><span data-stu-id="277e8-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="277e8-113">Bir `Char` değişken bir vekil çifti tutamaz ve `String` Bu tür bir çift tutmak için iki konum kullanır.</span><span class="sxs-lookup"><span data-stu-id="277e8-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="277e8-114">Daha fazla bilgi için bkz. [char veri türü](../../../language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="277e8-114">For more information, see [Char Data Type](../../../language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="277e8-115">Dize türü</span><span class="sxs-lookup"><span data-stu-id="277e8-115">String Type</span></span>  
 <span data-ttu-id="277e8-116">`String`Veri türü sıfır veya daha fazla iki baytlık (16 bit) Unicode karakterden oluşan bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="277e8-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="277e8-117">Bir değişken belirsiz sayıda karakter içeriyorsa, olarak bildirin `String` .</span><span class="sxs-lookup"><span data-stu-id="277e8-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="277e8-118">Örnek:</span><span class="sxs-lookup"><span data-stu-id="277e8-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="277e8-119">Daha fazla bilgi için bkz. [dize veri türü](../../../language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="277e8-119">For more information, see [String Data Type](../../../language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="277e8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="277e8-120">See also</span></span>

- [<span data-ttu-id="277e8-121">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="277e8-121">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="277e8-122">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="277e8-122">Composite Data Types</span></span>](composite-data-types.md)
- [<span data-ttu-id="277e8-123">Visual Basic genel türler</span><span class="sxs-lookup"><span data-stu-id="277e8-123">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="277e8-124">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="277e8-124">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="277e8-125">Visual Basic'de Tür Dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="277e8-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="277e8-126">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="277e8-126">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="277e8-127">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="277e8-127">Type Characters</span></span>](type-characters.md)
