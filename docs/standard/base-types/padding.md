---
title: .NET 'teki dizeleri doldurma
description: .NET 'teki dizelerin nasıl gösterileceğini öğrenin. Belirtilen toplam uzunluğu elde etmek için baştaki veya sondaki karakterler eklemek üzere String. der Left ve String. asma sağ yöntemlerini kullanın.
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 5bf7023a3429e932a44ad0a0bd3409012f77cbf9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594536"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="fe6c6-104">.NET 'teki dizeleri doldurma</span><span class="sxs-lookup"><span data-stu-id="fe6c6-104">Padding Strings in .NET</span></span>

<span data-ttu-id="fe6c6-105"><xref:System.String>Belirtilen toplam uzunluğa baştaki veya sondaki karakterlerle doldurulan bir özgün dizeden oluşan yeni bir dize oluşturmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-105">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="fe6c6-106">Doldurma karakteri bir boşluk veya belirtilen karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-106">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="fe6c6-107">Elde edilen dize, sağa hizalı veya sola hizalı olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-107">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="fe6c6-108">Özgün dizenin uzunluğu, istenen toplam uzunluğa zaten eşitse veya daha büyükse, doldurma yöntemleri özgün dizeyi değiştirilmemiş şekilde döndürür; daha fazla bilgi için, ve yöntemlerinin iki aşırı yüklemesinin bölümlerini **döndürür** <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe6c6-108">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="fe6c6-109">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="fe6c6-109">Method name</span></span>|<span data-ttu-id="fe6c6-110">Kullanım</span><span class="sxs-lookup"><span data-stu-id="fe6c6-110">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="fe6c6-111">Baştaki karakterlerle belirtilen toplam uzunluğa sahip bir dizeyi defterler.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-111">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="fe6c6-112">Sondaki karakterlerle bir dizeyi belirtilen toplam uzunluğa göre defterler.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-112">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="fe6c6-113">Asma sol</span><span class="sxs-lookup"><span data-stu-id="fe6c6-113">PadLeft</span></span>  
 <span data-ttu-id="fe6c6-114"><xref:System.String.PadLeft%2A?displayProperty=nameWithType>Yöntemi, belirli bir toplam uzunluğu elde etmek için, bir özgün dizeye yeterince önde gelen doldurma karakteri birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-114">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="fe6c6-115"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>Yöntemi, doldurma karakteri olarak boşluk kullanır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakterinizi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-115">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="fe6c6-116">Aşağıdaki kod örneği, <xref:System.String.PadLeft%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-116">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="fe6c6-117">Örnek, konsola " `--------Hello World!` " görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-117">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="fe6c6-118">Asma sağ</span><span class="sxs-lookup"><span data-stu-id="fe6c6-118">PadRight</span></span>  
 <span data-ttu-id="fe6c6-119"><xref:System.String.PadRight%2A?displayProperty=nameWithType>Yöntemi, belirli bir toplam uzunluğa ulaşmak için bir özgün dizeye yeterli sayıda sondaki doldurma karakteri birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-119">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="fe6c6-120"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>Yöntemi, doldurma karakteri olarak boşluk kullanır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakterinizi belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-120">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="fe6c6-121">Aşağıdaki kod örneği, <xref:System.String.PadRight%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-121">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="fe6c6-122">Örnek, konsola " `Hello World!--------` " görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-122">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fe6c6-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe6c6-123">See also</span></span>

- [<span data-ttu-id="fe6c6-124">Temel dize Işlemleri</span><span class="sxs-lookup"><span data-stu-id="fe6c6-124">Basic String Operations</span></span>](basic-string-operations.md)
