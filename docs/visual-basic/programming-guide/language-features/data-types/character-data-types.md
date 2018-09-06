---
title: Karakter Veri Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 3b031c6e3dc04637128f95ca8e922d3298981287
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863209"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="8537b-102">Karakter Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8537b-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="8537b-103">Visual Basic sağlar *karakter veri türleri* yazdırılabilir ve görüntülenebilen karakterler ile dağıtılacak.</span><span class="sxs-lookup"><span data-stu-id="8537b-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="8537b-104">Her ikisi de Unicode karakterleriyle işlem sırasında `Char` tek bir karakter tutarken `String` sonsuz sayıda karakter içeriyor.</span><span class="sxs-lookup"><span data-stu-id="8537b-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="8537b-105">Visual Basic veri türleri yan yana karşılaştırmasını gösteren bir tablo için bkz [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="8537b-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="8537b-106">Char türü</span><span class="sxs-lookup"><span data-stu-id="8537b-106">Char Type</span></span>  
 <span data-ttu-id="8537b-107">`Char` Veri türü olan tek bir iki baytlık (16-bit) Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="8537b-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="8537b-108">Bir değişken her zaman tam olarak bir karakter içermiyorsa, olarak bildirin `Char`.</span><span class="sxs-lookup"><span data-stu-id="8537b-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="8537b-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8537b-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="8537b-110">Olası her değeri bir `Char` veya `String` değişken bir *kod noktası*, veya Unicode karakter kümesindeki karakter kodu.</span><span class="sxs-lookup"><span data-stu-id="8537b-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="8537b-111">Temel ASCII karakter kümesi, çeşitli diğer alfabedeki harfleri, vurgular, para birimi sembolleri, kesirli, aksanlar ve semboller matematiksel ve teknik Unicode karakterler içerir.</span><span class="sxs-lookup"><span data-stu-id="8537b-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8537b-112">Kod noktaları için DFFF (55296 55551 ondalık üzerinden) aracılığıyla D800 yedekleri Unicode karakter kümesi *vekil çiftleri*, iki 16-bit değerleri temsil eden tek bir kod noktası gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8537b-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="8537b-113">A `Char` değişkeni, bir yedek çifti tutun olamaz ve bir `String` böyle bir çift tutmak için iki konum kullanır.</span><span class="sxs-lookup"><span data-stu-id="8537b-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="8537b-114">Daha fazla bilgi için [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="8537b-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="8537b-115">Dize türü</span><span class="sxs-lookup"><span data-stu-id="8537b-115">String Type</span></span>  
 <span data-ttu-id="8537b-116">`String` Veri türü olan bir dizi iki baytlık (16-bit) sıfır veya daha fazla Unicode karakteri.</span><span class="sxs-lookup"><span data-stu-id="8537b-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="8537b-117">Bir değişken sonsuz sayıda karakter içeriyorsa olarak bildirin `String`.</span><span class="sxs-lookup"><span data-stu-id="8537b-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="8537b-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8537b-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="8537b-119">Daha fazla bilgi için [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="8537b-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8537b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8537b-120">See Also</span></span>  
 [<span data-ttu-id="8537b-121">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8537b-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="8537b-122">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8537b-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="8537b-123">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="8537b-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="8537b-124">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="8537b-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="8537b-125">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="8537b-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="8537b-126">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="8537b-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="8537b-127">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="8537b-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
