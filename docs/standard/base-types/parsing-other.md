---
title: .NET'te Diğer Dizeleri Ayrışdırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127567"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="e4389-102">.NET'te Diğer Dizeleri Ayrışdırma</span><span class="sxs-lookup"><span data-stu-id="e4389-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="e4389-103">Sayısal <xref:System.DateTime> ve dizeleri ek olarak, aynı zamanda <xref:System.Char>türleri temsil dizeleri <xref:System.Boolean>ayrıştını , ve <xref:System.Enum> veri türleri içine.</span><span class="sxs-lookup"><span data-stu-id="e4389-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="e4389-104">Char</span><span class="sxs-lookup"><span data-stu-id="e4389-104">Char</span></span>  
 <span data-ttu-id="e4389-105">**Char** veri türüyle ilişkili statik ayrıştırma yöntemi, tek bir karakter içeren bir dizeyi Unicode değerine dönüştürmek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4389-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="e4389-106">Aşağıdaki kod örneği, bir dizeyi Unicode karakterine benzeter.</span><span class="sxs-lookup"><span data-stu-id="e4389-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="e4389-107">Boole</span><span class="sxs-lookup"><span data-stu-id="e4389-107">Boolean</span></span>  
 <span data-ttu-id="e4389-108">Boolean veri türü, **Boolean** değerini temsil eden bir dizeyi gerçek **boolean** türüne dönüştürmek için kullanabileceğiniz bir **Ayrışdır** yöntemi içerir.</span><span class="sxs-lookup"><span data-stu-id="e4389-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="e4389-109">Bu yöntem büyük/küçük harf duyarlı değildir ve "True" veya "False" içeren bir dizeyi başarıyla ayrıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="e4389-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="e4389-110">**Boolean** türüyle ilişkili **Ayrıştırıcı** yöntemi, beyaz boşluklarla çevrili dizeleri de ayrıştırabilir.</span><span class="sxs-lookup"><span data-stu-id="e4389-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="e4389-111">Başka bir dize geçilirse, bir <xref:System.FormatException> atılır.</span><span class="sxs-lookup"><span data-stu-id="e4389-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="e4389-112">Aşağıdaki kod örneği, bir dizeyi Boolean değerine dönüştürmek için **Ayrışma** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4389-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="e4389-113">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e4389-113">Enumeration</span></span>  
 <span data-ttu-id="e4389-114">Bir dizinin değerine numaralandırma türünü başlatmak için statik **Ayrışma** yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e4389-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="e4389-115">Bu yöntem, ayrıştırdığınız numaralandırma türünü, ayrıştırmak için dize ve ayrıştırma durumda duyarlı olup olmadığını belirten isteğe bağlı Boolean bayrağı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="e4389-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="e4389-116">Ayrıştırdığınız dize, virgülle ayrılmış birkaç değer içerebilir ve bu değerler bir veya daha fazla boş boşluk (beyaz boşluk olarak da adlandırılır) tarafından önce veya ardından gelebilir.</span><span class="sxs-lookup"><span data-stu-id="e4389-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="e4389-117">Dize birden çok değer içeriyorsa, döndürülen nesnenin değeri, bitwise OR işlemiyle birlikte tüm belirtilen değerlerin değeridir.</span><span class="sxs-lookup"><span data-stu-id="e4389-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="e4389-118">Aşağıdaki örnek, dize gösterimini numaralandırma değerine dönüştürmek için **Parse** yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e4389-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="e4389-119">Numaralandırma <xref:System.DayOfWeek> bir dize **perşembeye** başharfle.</span><span class="sxs-lookup"><span data-stu-id="e4389-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e4389-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4389-120">See also</span></span>

- [<span data-ttu-id="e4389-121">Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="e4389-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)
- [<span data-ttu-id="e4389-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="e4389-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
- [<span data-ttu-id="e4389-123">.NET'te Tür Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="e4389-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
