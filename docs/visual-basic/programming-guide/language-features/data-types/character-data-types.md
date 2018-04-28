---
title: Karakter Veri Türleri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afd368c00444f136c6d69b02a733c82f0c8eafe0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="e2db6-102">Karakter Veri Türleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2db6-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="e2db6-103">Visual Basic sağlar *karakter veri türleri* yazdırılabilir ve görüntülenebilecek karakterlerle dağıtılacak.</span><span class="sxs-lookup"><span data-stu-id="e2db6-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="e2db6-104">Her ikisi de Unicode karakterlerle ilgilidir sırada `Char` tek bir karakter tutarken `String` sonsuz sayıda karakter içeriyor.</span><span class="sxs-lookup"><span data-stu-id="e2db6-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="e2db6-105">Visual Basic veri türleri yan yana karşılaştırmasını görüntüler bir tablo için bkz: [veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="e2db6-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="e2db6-106">Char türü</span><span class="sxs-lookup"><span data-stu-id="e2db6-106">Char Type</span></span>  
 <span data-ttu-id="e2db6-107">`Char` Veri türü olan tek bir iki baytlık (16-bit) Unicode karakter.</span><span class="sxs-lookup"><span data-stu-id="e2db6-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="e2db6-108">Bir değişken her zaman tam olarak bir karakter depoluyorsa olarak bildirme `Char`.</span><span class="sxs-lookup"><span data-stu-id="e2db6-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="e2db6-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e2db6-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="e2db6-110">Olası her değerin bir `Char` veya `String` değişkeni, bir *kod noktası*, veya karakter kodu, Unicode karakter kümesi.</span><span class="sxs-lookup"><span data-stu-id="e2db6-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="e2db6-111">Unicode karakterler temel ASCII karakter kümesi, çeşitli diğer alfabedeki harfleri, vurgular, para birimi simgeleri, kesirler, Vurgu ve matematiksel ve teknik simgeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e2db6-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2db6-112">Kod noktaları için DFFF (55296 55551 ondalık aracılığıyla) aracılığıyla D800 yedekleri Unicode karakter kümesi *vekil çiftleri*, tek bir kod noktası göstermek için iki 16 bit değerleri gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e2db6-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="e2db6-113">A `Char` değişkeni, bir yedek çifti tutun olamaz ve `String` böyle bir çifti tutmak için iki konum kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2db6-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="e2db6-114">Daha fazla bilgi için bkz: [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e2db6-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="e2db6-115">Dize türü</span><span class="sxs-lookup"><span data-stu-id="e2db6-115">String Type</span></span>  
 <span data-ttu-id="e2db6-116">`String` Veri türü olan sıfır veya daha fazla iki baytlık (16-bit) Unicode karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="e2db6-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="e2db6-117">Bir değişken sonsuz sayıda karakter içeriyorsa olarak bildirme `String`.</span><span class="sxs-lookup"><span data-stu-id="e2db6-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="e2db6-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e2db6-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="e2db6-119">Daha fazla bilgi için bkz: [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e2db6-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2db6-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2db6-120">See Also</span></span>  
 [<span data-ttu-id="e2db6-121">Başlangıç Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="e2db6-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="e2db6-122">Bileşik Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="e2db6-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="e2db6-123">Visual Basic'de genel türler</span><span class="sxs-lookup"><span data-stu-id="e2db6-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="e2db6-124">Değer Türleri ve Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="e2db6-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="e2db6-125">Visual Basic'de tür dönüştürmeleri</span><span class="sxs-lookup"><span data-stu-id="e2db6-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="e2db6-126">Veri Türü Sorunlarını Giderme</span><span class="sxs-lookup"><span data-stu-id="e2db6-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="e2db6-127">Tür Karakterleri</span><span class="sxs-lookup"><span data-stu-id="e2db6-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
