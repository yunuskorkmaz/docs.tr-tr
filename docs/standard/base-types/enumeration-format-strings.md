---
title: Sabit listesi biçim dizeleri
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
ms.openlocfilehash: c32fd9d59f61b6befe94ff9eb85b0c39ce926adb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348260"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="6aa0a-102">Sabit listesi biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="6aa0a-102">Enumeration format strings</span></span>

<span data-ttu-id="6aa0a-103">Bir numaralandırma üyesinin sayısal, onaltılı veya dize değerini temsil eden yeni bir String nesnesi oluşturmak için <xref:System.Enum.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="6aa0a-104">Bu yöntem, döndürülmek istediğiniz değeri belirtmek için sabit listesi biçimlendirme dizelerinden birini alır.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="6aa0a-105">Aşağıdaki bölümlerde sabit listesi biçimlendirme dizeleri ve döndürdüğü değerler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-105">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="6aa0a-106">Bu biçim belirticileri büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-106">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="6aa0a-107">G veya g</span><span class="sxs-lookup"><span data-stu-id="6aa0a-107">G or g</span></span>

<span data-ttu-id="6aa0a-108">Sabit Listesi girişini, mümkünse bir dize değeri olarak görüntüler ve aksi takdirde geçerli örneğin tamsayı değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-108">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="6aa0a-109">Numaralandırma, **Flags** özniteliği kümesiyle tanımlanmışsa, her bir geçerli girdinin dize değerleri, virgülle ayırarak birlikte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-109">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="6aa0a-110">**Flags** özniteliği ayarlanmamışsa, geçersiz bir değer sayısal giriş olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-110">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="6aa0a-111">Aşağıdaki örnekte, G Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-111">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="6aa0a-112">F veya f</span><span class="sxs-lookup"><span data-stu-id="6aa0a-112">F or f</span></span>

<span data-ttu-id="6aa0a-113">Mümkünse, numaralandırma girişini bir dize değeri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-113">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="6aa0a-114">Değer, Numaralandırmadaki girişlerin toplamı olarak tamamen görüntülenebilse ( **Flags** özniteliği mevcut olmasa bile), her bir geçerli girdinin dize değerleri, virgülle ayırarak birlikte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-114">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="6aa0a-115">Değer, numaralandırma girişleriyle tamamen tespit edilemez, değer tamsayı değeri olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-115">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="6aa0a-116">Aşağıdaki örnekte, F Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-116">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="6aa0a-117">D veya d</span><span class="sxs-lookup"><span data-stu-id="6aa0a-117">D or d</span></span>

<span data-ttu-id="6aa0a-118">Numaralandırma girişini mümkün olan en kısa temsilde tamsayı değeri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-118">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="6aa0a-119">Aşağıdaki örnekte D Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-119">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="6aa0a-120">X veya x</span><span class="sxs-lookup"><span data-stu-id="6aa0a-120">X or x</span></span>

<span data-ttu-id="6aa0a-121">Sabit Listesi girişini onaltılık bir değer olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-121">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="6aa0a-122">Sonuç dizesinin, numaralandırma türünün [temel alınan sayısal türündeki](xref:System.Enum.GetUnderlyingType%2A)her bayt için iki karakteri olduğundan emin olmak için, değer önde gelen sıfır ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-122">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="6aa0a-123">Aşağıdaki örnekte X Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-123">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="6aa0a-124">Örnekte, hem <xref:System.ConsoleColor> hem de <xref:System.IO.FileAttributes> temel alınan türü <xref:System.Int32>ya da 8 karakterlik bir sonuç dizesi üreten 32 bitlik (veya 4 baytlık) bir tamsayıdır.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-124">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]      
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="6aa0a-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="6aa0a-125">Example</span></span>

<span data-ttu-id="6aa0a-126">Aşağıdaki örnek üç girdilerden oluşan `Colors` adlı bir sabit listesi tanımlar: `Red`, `Blue`ve `Green`.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-126">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="6aa0a-127">Sabit Listesi tanımlandıktan sonra bir örnek aşağıdaki şekilde bildirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-127">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="6aa0a-128">`Color.ToString(System.String)` yöntemi, kendisine geçirilen biçim belirticisine bağlı olarak, numaralandırma değerini farklı yollarla göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-128">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="6aa0a-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aa0a-129">See also</span></span>

- [<span data-ttu-id="6aa0a-130">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="6aa0a-130">Formatting Types</span></span>](formatting-types.md)
