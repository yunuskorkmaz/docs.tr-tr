---
title: implicit (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 70379136fd4b14403eac919ac15590250b17b416
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135607"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="ed844-102">implicit (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ed844-102">implicit (C# Reference)</span></span>

<span data-ttu-id="ed844-103">`implicit` Anahtar sözcüğü, bir kullanıcı tanımlı örtük tür dönüştürme işleci bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ed844-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="ed844-104">Dönüştürme veri kaybına neden olmayan garanti, kullanıcı tanımlı bir tür ve başka bir türü arasında örtülü dönüştürmeler etkinleştirmek için bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ed844-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>

## <a name="example"></a><span data-ttu-id="ed844-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ed844-105">Example</span></span>

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

<span data-ttu-id="ed844-106">Örtük dönüştürmeleri gereksiz atamalar ortadan kaldırarak, kaynak kodunun okunabilirliğini artırabilir.</span><span class="sxs-lookup"><span data-stu-id="ed844-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="ed844-107">Ancak, örtük dönüştürmelerin açıkça bir türden diğerine dönüştürme yapmak programcılar gerektirmediğinden, bakım beklenmeyen sonuçları engellemek için izlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ed844-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="ed844-108">Genel olarak, örtük dönüşüm işleçleri, hiçbir zaman özel durumlar ve Programcı tanıma güvenli bir şekilde kullanılabilir böylece hiçbir zaman bilgileri kaybedersiniz.</span><span class="sxs-lookup"><span data-stu-id="ed844-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="ed844-109">Bir dönüştürme işleci bu ölçütlerin karşılayamazsanız işaretlenmelidir `explicit`.</span><span class="sxs-lookup"><span data-stu-id="ed844-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="ed844-110">Daha fazla bilgi için [dönüştürme işleçleri kullanarak](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ed844-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ed844-111">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ed844-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ed844-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed844-112">See also</span></span>

- [<span data-ttu-id="ed844-113">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ed844-113">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="ed844-114">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ed844-114">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="ed844-115">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ed844-115">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="ed844-116">explicit</span><span class="sxs-lookup"><span data-stu-id="ed844-116">explicit</span></span>](explicit.md)  
- [<span data-ttu-id="ed844-117">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ed844-117">operator (C# Reference)</span></span>](operator.md)  
- [<span data-ttu-id="ed844-118">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="ed844-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
