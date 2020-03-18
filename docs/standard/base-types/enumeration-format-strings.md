---
title: Numaralandırma biçimi dizeleri
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
ms.openlocfilehash: da7634758f5c4319fa18612d216682dc141318fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155964"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="5268c-102">Numaralandırma biçimi dizeleri</span><span class="sxs-lookup"><span data-stu-id="5268c-102">Enumeration format strings</span></span>

<span data-ttu-id="5268c-103"><xref:System.Enum.ToString%2A?displayProperty=nameWithType> Metod, numaralandırma üyesinin sayısal, hexadecimal veya dize değerini temsil eden yeni bir dize nesnesi oluşturmak için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5268c-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="5268c-104">Bu yöntem, döndürülen istediğiniz değeri belirtmek için numaralandırma biçimlendirme dizeleri biri alır.</span><span class="sxs-lookup"><span data-stu-id="5268c-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="5268c-105">Aşağıdaki bölümlerde numaralandırma biçimlendirme dizeleri ve döndükleri değerleri listele.</span><span class="sxs-lookup"><span data-stu-id="5268c-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="5268c-106">Bu biçim belirteciler büyük/küçük harf duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="5268c-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="5268c-107">G veya g</span><span class="sxs-lookup"><span data-stu-id="5268c-107">G or g</span></span>

<span data-ttu-id="5268c-108">Numaralandırma girişini mümkünse bir dize değeri olarak görüntüler ve aksi takdirde geçerli örneğin tamsayı değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5268c-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="5268c-109">Numaralandırma **Bayraklar** öznitelik kümesi ile tanımlanırsa, her geçerli girişin dize değerleri biraraya getirilmiş ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="5268c-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="5268c-110">**Bayraklar** özniteliği ayarlanmazsa, geçersiz bir değer sayısal giriş olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5268c-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="5268c-111">Aşağıdaki örnekte G biçimi belirtimi gösteriş.</span><span class="sxs-lookup"><span data-stu-id="5268c-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="5268c-112">F veya f</span><span class="sxs-lookup"><span data-stu-id="5268c-112">F or f</span></span>

<span data-ttu-id="5268c-113">Numaralandırma girişini mümkünse bir dize değeri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5268c-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="5268c-114">Değer, numaralandırmadaki girişlerin toplamı olarak tamamen görüntülenebilirse **(Bayraköz** özniteliği olmasa bile), her geçerli girişin dize değerleri biraraya getirilmiş ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="5268c-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="5268c-115">Değer numaralandırma girişleri tarafından tamamen belirlenemiyorsa, değer tamsayı değeri olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5268c-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="5268c-116">Aşağıdaki örnekte F biçimi belirtimi gösteriş.</span><span class="sxs-lookup"><span data-stu-id="5268c-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="5268c-117">D veya d</span><span class="sxs-lookup"><span data-stu-id="5268c-117">D or d</span></span>

<span data-ttu-id="5268c-118">Numaralandırma girişini mümkün olan en kısa gösterimde bir tümseci değeri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5268c-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="5268c-119">Aşağıdaki örnekte D biçimi belirtimi gösteriş.</span><span class="sxs-lookup"><span data-stu-id="5268c-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="5268c-120">X veya x</span><span class="sxs-lookup"><span data-stu-id="5268c-120">X or x</span></span>

<span data-ttu-id="5268c-121">Numaralandırma girişini hexadecimal değer olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5268c-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="5268c-122">Değer, sonuç dizesinin numaralandırma türünün [temel sayısal türündeki](xref:System.Enum.GetUnderlyingType%2A)her bir bayt için iki karaktere sahip olduğundan emin olmak için gerektiğinde önde gelen sıfırlarla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="5268c-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="5268c-123">Aşağıdaki örnek, X biçimi belirticisini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5268c-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="5268c-124">Örnekte, her ikisinin <xref:System.ConsoleColor> de <xref:System.IO.FileAttributes> <xref:System.Int32>altında yatan türü veya 8 karakterlik bir sonuç dizesi üreten 32 bit (veya 4 bayt) tamsayı dır.</span><span class="sxs-lookup"><span data-stu-id="5268c-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="5268c-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5268c-125">Example</span></span>

<span data-ttu-id="5268c-126">Aşağıdaki örnek, üç girişten oluşan `Colors` numaralandırma yı `Red`tanımlar: `Blue` `Green`, , ve .</span><span class="sxs-lookup"><span data-stu-id="5268c-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="5268c-127">Numaralandırma tanımlandıktan sonra, bir örnek aşağıdaki şekilde bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5268c-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="5268c-128">Yöntem `Color.ToString(System.String)` daha sonra, numaralandırma değerini, ona aktarılan biçim belirticiye bağlı olarak farklı şekillerde görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5268c-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="5268c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5268c-129">See also</span></span>

- [<span data-ttu-id="5268c-130">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="5268c-130">Formatting Types</span></span>](formatting-types.md)
