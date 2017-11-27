---
title: ".NET diğer dizeleri ayrıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="8c688-102">.NET diğer dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="8c688-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="8c688-103">Sayısal yanı sıra ve <xref:System.DateTime> dizeleri, türleri temsil eden dizeleri de ayrıştırmak <xref:System.Char>, <xref:System.Boolean>, ve <xref:System.Enum> veri türlerine.</span><span class="sxs-lookup"><span data-stu-id="8c688-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="8c688-104">Char</span><span class="sxs-lookup"><span data-stu-id="8c688-104">Char</span></span>  
 <span data-ttu-id="8c688-105">İlişkili statik parse yöntemi **Char** veri türü tek bir karakterlik Unicode değerini içeren bir dize dönüştürme için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8c688-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="8c688-106">Aşağıdaki kod örneğinde bir dize Unicode karakter ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="8c688-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="8c688-107">Boole değeri</span><span class="sxs-lookup"><span data-stu-id="8c688-107">Boolean</span></span>  
 <span data-ttu-id="8c688-108">**Boolean** veri türü içeren bir **ayrıştırma** bir Boole değeri gerçek bir temsil eden bir dize dönüştürmek için kullanabileceğiniz yöntemi **Boolean** türü.</span><span class="sxs-lookup"><span data-stu-id="8c688-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="8c688-109">Bu yöntem, büyük küçük harfe duyarlı değildir ve "True" veya "False" içeren bir dize başarıyla ayrıştıramıyor</span><span class="sxs-lookup"><span data-stu-id="8c688-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="8c688-110">**Ayrıştırma** yöntemi ile ilişkili **Boolean** türü de boşluk tarafından çevrelenen dizeleri ayrıştırma.</span><span class="sxs-lookup"><span data-stu-id="8c688-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="8c688-111">Herhangi bir dize aktarılırsa bir <xref:System.FormatException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8c688-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="8c688-112">Aşağıdaki kod örneğinde **ayrıştırma** bir dizeyi bir Boolean değerine dönüştürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="8c688-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="8c688-113">Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8c688-113">Enumeration</span></span>  
 <span data-ttu-id="8c688-114">Statik kullanabilirsiniz **ayrıştırma** yöntemi bir dize değeri için bir numaralandırma türü başlatılamadı.</span><span class="sxs-lookup"><span data-stu-id="8c688-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="8c688-115">Bu yöntem, ayrıştırma numaralandırma türü, dizesi ayrıştırılamıyor ve ayrıştırma büyük küçük harfe duyarlı olup olmadığını belirten bir isteğe bağlı mantıksal bayrak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8c688-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="8c688-116">Dize Ayrıştırma öncesinde veya (boşluk olarak da bilinir) bir veya daha fazla boş alanları tarafından izlenen virgülle ayırarak birden fazla değer içerebilir.</span><span class="sxs-lookup"><span data-stu-id="8c688-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="8c688-117">Dize birden fazla değer içeriyorsa, döndürülen nesnenin değerini bit düzeyinde OR işlemi ile birlikte tüm belirtilen değerleri değerdir.</span><span class="sxs-lookup"><span data-stu-id="8c688-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="8c688-118">Aşağıdaki örnek kullanır **ayrıştırma** bir numaralandırma değeri bir dize gösterimi dönüştürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="8c688-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="8c688-119"><xref:System.DayOfWeek> Numaralandırma başlatılır **Perşembe** bir dizeden.</span><span class="sxs-lookup"><span data-stu-id="8c688-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8c688-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8c688-120">See Also</span></span>  
 [<span data-ttu-id="8c688-121">Dizeleri ayrıştırma</span><span class="sxs-lookup"><span data-stu-id="8c688-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 [<span data-ttu-id="8c688-122">Biçimlendirme türleri</span><span class="sxs-lookup"><span data-stu-id="8c688-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 [<span data-ttu-id="8c688-123">.NET tür dönüştürme</span><span class="sxs-lookup"><span data-stu-id="8c688-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
