---
title: . NET'te diğer dizeleri ayrıştırma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85bb6dcdaa198b6b038cc80e1e38fa7d11123678
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43878729"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="92250-102">. NET'te diğer dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="92250-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="92250-103">Sayısal yanı sıra ve <xref:System.DateTime> dizeleri türleri temsil eden dizeleri de ayrıştırmak <xref:System.Char>, <xref:System.Boolean>, ve <xref:System.Enum> veri türlerini.</span><span class="sxs-lookup"><span data-stu-id="92250-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="92250-104">Char</span><span class="sxs-lookup"><span data-stu-id="92250-104">Char</span></span>  
 <span data-ttu-id="92250-105">İlişkili statik parse metoduna **Char** veri türü, tek bir karakter Unicode değerini içeren bir dize dönüştürmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="92250-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="92250-106">Aşağıdaki kod örneği, bir Unicode karakter bir dizeyi ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="92250-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="92250-107">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="92250-107">Boolean</span></span>  
 <span data-ttu-id="92250-108">**Boole** veri türü içeren bir **ayrıştırma** gerçek bir bir Boolean değeri temsil eden bir dize dönüştürmek için kullanabileceğiniz yöntem **Boole** türü.</span><span class="sxs-lookup"><span data-stu-id="92250-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="92250-109">Bu yöntem, büyük küçük harfe duyarlı değildir ve "True" veya "False" içeren bir dizeyi başarıyla ayrıştırmak</span><span class="sxs-lookup"><span data-stu-id="92250-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="92250-110">**Ayrıştırma** yöntemi ile ilişkili **Boole** türü de boşluk tarafından çevrilmiş dizeleri ayrıştırma.</span><span class="sxs-lookup"><span data-stu-id="92250-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="92250-111">Herhangi bir dize iletilmezse, bir <xref:System.FormatException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="92250-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="92250-112">Aşağıdaki kod örneğinde **ayrıştırma** bir dizeyi bir Boolean değerine dönüştürülmesi için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="92250-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="92250-113">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="92250-113">Enumeration</span></span>  
 <span data-ttu-id="92250-114">Statik kullanabileceğiniz **ayrıştırma** bir dize değeri için bir numaralandırma türüne başlatmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="92250-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="92250-115">Bu yöntem, ayrıştırma numaralandırma türü, ayrıştırılacak dize ve ayrıştırma büyük küçük harfe duyarlı olup olmadığını belirten isteğe bağlı bir Boole bayrağı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="92250-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="92250-116">Dize Ayrıştırma çok sayıda değer öncesinde mı (boşluk olarak da bilinir) bir veya daha fazla boş alanları tarafından izlenen, virgülle ayrılmış içerebilir.</span><span class="sxs-lookup"><span data-stu-id="92250-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="92250-117">Dize birden çok değer içeriyorsa, döndürülen nesnenin değerini bir bit düzeyinde OR işlemi ile birlikte tüm belirtilen değerleri değeridir.</span><span class="sxs-lookup"><span data-stu-id="92250-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="92250-118">Aşağıdaki örnekte **ayrıştırma** bir sabit listesi değeri dize gösterimine dönüştürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="92250-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="92250-119"><xref:System.DayOfWeek> Numaralandırması için başlatılan **Perşembe** bir dizeden.</span><span class="sxs-lookup"><span data-stu-id="92250-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="92250-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92250-120">See also</span></span>

- [<span data-ttu-id="92250-121">Dizeleri Ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="92250-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
- [<span data-ttu-id="92250-122">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="92250-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
- [<span data-ttu-id="92250-123">.NET içinde tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="92250-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
