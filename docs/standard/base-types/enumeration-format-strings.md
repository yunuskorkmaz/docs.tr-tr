---
title: Numaralandırma biçimi dizeleri - .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4f2a8fc10d2aad6b2d43bf128697e86aa73c411
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644688"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="58e31-102">Numaralandırma biçimi dizeleri</span><span class="sxs-lookup"><span data-stu-id="58e31-102">Enumeration format strings</span></span>

<span data-ttu-id="58e31-103">Kullanabileceğiniz <xref:System.Enum.ToString%2A?displayProperty=nameWithType> sayısal, onaltılık veya dize değerini bir numaralandırma üyesine temsil eden yeni bir dize nesnesi oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58e31-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="58e31-104">Bu yöntem biçimlendirme dizeleri döndürülmesini istediğiniz değeri belirtmek için numaralandırma alır.</span><span class="sxs-lookup"><span data-stu-id="58e31-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="58e31-105">Aşağıdaki bölümlerde, sabit listesi biçimlendirme dizeleri ve bunların dönüş değerleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="58e31-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="58e31-106">Bu biçim tanımlayıcıları büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="58e31-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="58e31-107">G veya g</span><span class="sxs-lookup"><span data-stu-id="58e31-107">G or g</span></span>

<span data-ttu-id="58e31-108">Dize değeri olarak sabit listesi girişi görüntüler, mümkünse ve aksi takdirde geçerli örneğin tamsayı değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="58e31-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="58e31-109">Sabit listesi ile tanımlanmışsa **bayrakları** virgüllerle ayrılmış şekilde öznitelik kümesi, geçerli her girişin değerleri birleştirilmiş birlikte bir dize.</span><span class="sxs-lookup"><span data-stu-id="58e31-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="58e31-110">Varsa **bayrakları** özniteliği ayarlanmadı, sayısal bir giriş olarak geçersiz bir değer görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="58e31-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="58e31-111">Aşağıdaki örnekte, G biçim belirticisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="58e31-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="58e31-112">F veya f</span><span class="sxs-lookup"><span data-stu-id="58e31-112">F or f</span></span>

<span data-ttu-id="58e31-113">Sabit listesi girişi mümkünse bir dize değeri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="58e31-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="58e31-114">Değeri, listedeki girişleri toplamı olarak tamamen görüntülenebilen varsa (bile **bayrakları** özniteliği mevcut değil), virgülle ayrılmış geçerli her girişin dize değerleri birlikte bitiştirilir.</span><span class="sxs-lookup"><span data-stu-id="58e31-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="58e31-115">Ardından değeri tamamen göre sabit listesi girişi belirlenemiyorsa değeri tamsayı biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="58e31-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="58e31-116">Aşağıdaki örnek, F biçim belirticisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="58e31-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="58e31-117">D veya d</span><span class="sxs-lookup"><span data-stu-id="58e31-117">D or d</span></span>

<span data-ttu-id="58e31-118">Sabit listesi Giriş bir tamsayı değeri mümkün olan en kısa gösteriminde olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="58e31-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="58e31-119">Aşağıdaki örnek, D biçim belirticisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="58e31-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="58e31-120">X ya da x</span><span class="sxs-lookup"><span data-stu-id="58e31-120">X or x</span></span>

<span data-ttu-id="58e31-121">Sabit listesi girişi bir onaltılık değer görüntüler.</span><span class="sxs-lookup"><span data-stu-id="58e31-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="58e31-122">Değer, değer en az sekiz basamak uzunluğunda olduğundan emin olmak için gerekirse sayının önüne gösterilir.</span><span class="sxs-lookup"><span data-stu-id="58e31-122">The value is represented with leading zeros as necessary, to ensure that the value is a minimum eight digits in length.</span></span> <span data-ttu-id="58e31-123">Aşağıdaki örnek X biçim belirticisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="58e31-123">The following example illustrates the X format specifier.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="58e31-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="58e31-124">Example</span></span>

<span data-ttu-id="58e31-125">Aşağıdaki örnek adlı bir sabit listesi tanımlar `Colors` üç girişlerini oluşur: `Red`, `Blue`, ve `Green`.</span><span class="sxs-lookup"><span data-stu-id="58e31-125">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="58e31-126">Numaralandırma tanımlandıktan sonra bir örneğini aşağıdaki şekilde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="58e31-126">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="58e31-127">`Color.ToString(System.String)` Yöntemi daha sonra geçirilen biçim belirticisi bağlı olarak farklı şekillerde numaralandırma değeri görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="58e31-127">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="58e31-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58e31-128">See also</span></span>

- [<span data-ttu-id="58e31-129">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="58e31-129">Formatting Types</span></span>](formatting-types.md)
