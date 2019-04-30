---
title: Dönüşüm işleçleri - kullanma C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
- implicit conversion operators [C#]
- explicit conversion operators [C#]
ms.assetid: caf36e89-c6c0-4b87-9f9e-85780a45c9a4
ms.openlocfilehash: 888339661ba1cb2e0b702f284d9f27b3217e74c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678445"
---
# <a name="using-conversion-operators-c-programming-guide"></a><span data-ttu-id="9f008-102">Dönüşüm İşleçleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="9f008-102">Using Conversion Operators (C# Programming Guide)</span></span>
<span data-ttu-id="9f008-103">Kullanımı daha kolay olan `implicit` dönüştürme operatörlerini veya kodu okuyan herkese bir türü dönüştürdüğünüzü açıkça gösteren `explicit` dönüştürme operatörlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9f008-103">You can use `implicit` conversion operators, which are easier to use, or `explicit` conversion operators, which clearly indicate to anyone reading the code that you're converting a type.</span></span> <span data-ttu-id="9f008-104">Bu konuda, her iki dönüştürme operatörü türü gösterilir.</span><span class="sxs-lookup"><span data-stu-id="9f008-104">This topic demonstrates both types of conversion operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f008-105">Basit tür dönüştürmeleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [nasıl yapılır: Byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), veya <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="9f008-105">For information about simple type conversions, see [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md), or <xref:System.Convert>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f008-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f008-106">Example</span></span>  
 <span data-ttu-id="9f008-107">Bu bir açık bir dönüştürme operatörü örneğidir.</span><span class="sxs-lookup"><span data-stu-id="9f008-107">This is an example of an explicit conversion operator.</span></span> <span data-ttu-id="9f008-108">Bu operatör, <xref:System.Byte> türünden `Digit` isimli değer türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9f008-108">This operator converts from the type <xref:System.Byte> to a value type called `Digit`.</span></span> <span data-ttu-id="9f008-109">Tüm baytlar bir basamak değerine dönüştürülemediğinden, dönüştürme açıktır; yani `Main` yönteminde gösterildiği gibi bir yayın kullanılması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9f008-109">Because not all bytes can be converted to a digit, the conversion is explicit, meaning that a cast must be used, as shown in the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideStatements#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#11)]  
  
## <a name="example"></a><span data-ttu-id="9f008-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="9f008-110">Example</span></span>  
 <span data-ttu-id="9f008-111">Bu örnek, önceki örnekte yapılanı geri alan bir dönüştürme aracı tanımlayarak kapalı bir dönüştürme aracı gösterir: `Digit` olarak adlandırılan bir değer sınıfını <xref:System.Byte> integral türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9f008-111">This example demonstrates an implicit conversion operator by defining a conversion operator that undoes what the previous example did: it converts from a value class called `Digit` to the integral <xref:System.Byte> type.</span></span> <span data-ttu-id="9f008-112">Herhangi bir rakam bir <xref:System.Byte>'a dönüştürülebilir olduğundan, kullanıcıların dönüştürme hakkında açık olmaya zorlamaya gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f008-112">Because any digit can be converted to a <xref:System.Byte>, there's no need to force users to be explicit about the conversion.</span></span>  
  
 [!code-csharp[csProgGuideStatements#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#12)]  
  
## <a name="see-also"></a><span data-ttu-id="9f008-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f008-113">See also</span></span>

- [<span data-ttu-id="9f008-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9f008-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="9f008-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9f008-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9f008-116">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9f008-116">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
- [<span data-ttu-id="9f008-117">is</span><span class="sxs-lookup"><span data-stu-id="9f008-117">is</span></span>](../../../csharp/language-reference/keywords/is.md)
