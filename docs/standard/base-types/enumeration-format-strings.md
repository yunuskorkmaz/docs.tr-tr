---
title: Sabit listesi biçim dizeleri
description: .NET 'teki Enum. ToString yöntemini kullanarak numaralandırma biçim dizeleri oluşturun. Numaralandırma üyelerinin sayısal, onaltılık veya dize değerlerini biçimlendirin.
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
ms.openlocfilehash: 825357cf4a56132dae0870972d316eff89b0c94f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583433"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="71f68-104">Sabit listesi biçim dizeleri</span><span class="sxs-lookup"><span data-stu-id="71f68-104">Enumeration format strings</span></span>

<span data-ttu-id="71f68-105"><xref:System.Enum.ToString%2A?displayProperty=nameWithType>Bir numaralandırma üyesinin sayısal, onaltılı veya dize değerini temsil eden yeni bir String nesnesi oluşturmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="71f68-105">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="71f68-106">Bu yöntem, döndürülmek istediğiniz değeri belirtmek için sabit listesi biçimlendirme dizelerinden birini alır.</span><span class="sxs-lookup"><span data-stu-id="71f68-106">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="71f68-107">Aşağıdaki bölümlerde sabit listesi biçimlendirme dizeleri ve döndürdüğü değerler listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="71f68-107">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="71f68-108">Bu biçim belirticileri büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="71f68-108">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="71f68-109">G veya g</span><span class="sxs-lookup"><span data-stu-id="71f68-109">G or g</span></span>

<span data-ttu-id="71f68-110">Sabit Listesi girişini, mümkünse bir dize değeri olarak görüntüler ve aksi takdirde geçerli örneğin tamsayı değerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="71f68-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="71f68-111">Numaralandırma, **Flags** özniteliği kümesiyle tanımlanmışsa, her bir geçerli girdinin dize değerleri, virgülle ayırarak birlikte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="71f68-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="71f68-112">**Flags** özniteliği ayarlanmamışsa, geçersiz bir değer sayısal giriş olarak görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="71f68-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="71f68-113">Aşağıdaki örnekte, G Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71f68-113">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="71f68-114">F veya f</span><span class="sxs-lookup"><span data-stu-id="71f68-114">F or f</span></span>

<span data-ttu-id="71f68-115">Mümkünse, numaralandırma girişini bir dize değeri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="71f68-115">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="71f68-116">Değer, Numaralandırmadaki girişlerin toplamı olarak tamamen görüntülenebilse ( **Flags** özniteliği mevcut olmasa bile), her bir geçerli girdinin dize değerleri, virgülle ayırarak birlikte birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="71f68-116">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="71f68-117">Değer, numaralandırma girişleriyle tamamen tespit edilemez, değer tamsayı değeri olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="71f68-117">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="71f68-118">Aşağıdaki örnekte, F Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71f68-118">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="71f68-119">D veya d</span><span class="sxs-lookup"><span data-stu-id="71f68-119">D or d</span></span>

<span data-ttu-id="71f68-120">Numaralandırma girişini mümkün olan en kısa temsilde tamsayı değeri olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="71f68-120">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="71f68-121">Aşağıdaki örnekte D Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71f68-121">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="71f68-122">X veya x</span><span class="sxs-lookup"><span data-stu-id="71f68-122">X or x</span></span>

<span data-ttu-id="71f68-123">Sabit Listesi girişini onaltılık bir değer olarak görüntüler.</span><span class="sxs-lookup"><span data-stu-id="71f68-123">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="71f68-124">Sonuç dizesinin, numaralandırma türünün [temel alınan sayısal türündeki](xref:System.Enum.GetUnderlyingType%2A)her bayt için iki karakteri olduğundan emin olmak için, değer önde gelen sıfır ile temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="71f68-124">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="71f68-125">Aşağıdaki örnekte X Biçim belirleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="71f68-125">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="71f68-126">Örnekte, hem hem de ' nin temel türü <xref:System.ConsoleColor> <xref:System.IO.FileAttributes> <xref:System.Int32> ya da 8 karakterlik sonuç dizesi üreten 32 bitlik (veya 4 baytlık) tamsayı.</span><span class="sxs-lookup"><span data-stu-id="71f68-126">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="71f68-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="71f68-127">Example</span></span>

<span data-ttu-id="71f68-128">Aşağıdaki örnek üç girdilerden oluşan adlı bir numaralandırma tanımlar `Colors` : `Red` , `Blue` , ve `Green` .</span><span class="sxs-lookup"><span data-stu-id="71f68-128">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="71f68-129">Sabit Listesi tanımlandıktan sonra bir örnek aşağıdaki şekilde bildirilebilirler.</span><span class="sxs-lookup"><span data-stu-id="71f68-129">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="71f68-130">`Color.ToString(System.String)`Daha sonra yöntemi, kendisine geçirilen biçim belirticisine bağlı olarak, numaralandırma değerini farklı yollarla göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71f68-130">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="71f68-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f68-131">See also</span></span>

- [<span data-ttu-id="71f68-132">Biçimlendirme Türleri</span><span class="sxs-lookup"><span data-stu-id="71f68-132">Formatting Types</span></span>](formatting-types.md)
