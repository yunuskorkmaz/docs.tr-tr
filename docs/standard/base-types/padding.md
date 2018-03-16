---
title: Padding Strings in .NET
ms.custom: 
ms.date: 03/15/2018
ms.prod: .net
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bf90c841c8fff21dd423fcd19613b5eb46a2c80c
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2018
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="ba944-102">Padding Strings in .NET</span><span class="sxs-lookup"><span data-stu-id="ba944-102">Padding Strings in .NET</span></span>

<span data-ttu-id="ba944-103">Aşağıdakilerden birini kullanmak <xref:System.String> baştaki veya sondaki belirtilen toplam uzunluğu karakterleri ile doldurulan bir özgün dize içeren yeni bir dize oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ba944-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="ba944-104">Doldurma karakteri boşluk veya belirtilen bir karakterin olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba944-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="ba944-105">Sonuç dizesini sağa hizalı ya da sola hizalı gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="ba944-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="ba944-106">Özgün dizesinin uzunluğu zaten eşit veya bundan büyük istenen toplam uzunluğu ise, doldurma yöntemleri değişmeden özgün dizeyi döndürür; Daha fazla bilgi için bkz: **döndürür** iki aşırı bölümlerini <xref:System.String.PadLeft%2A?displayProperty=nameWithType> ve <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="ba944-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="ba944-107">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="ba944-107">Method name</span></span>|<span data-ttu-id="ba944-108">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="ba944-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="ba944-109">Belirtilen bir toplam uzunluğu karakter eklenerek bir dize pads.</span><span class="sxs-lookup"><span data-stu-id="ba944-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="ba944-110">Sondaki belirtilen toplam uzunluğu karakterleri içeren bir dize pads.</span><span class="sxs-lookup"><span data-stu-id="ba944-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="ba944-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="ba944-111">PadLeft</span></span>  
 <span data-ttu-id="ba944-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Yöntemi, belirtilen toplam uzunluğu elde etmek için özgün bir dizeye başında yeterli paneli karakter birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba944-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="ba944-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Yöntemi doldurma karakteri boşluk kullanır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba944-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="ba944-114">Aşağıdaki kod örneğinde <xref:System.String.PadLeft%2A> yirmi karakterden uzun olduğundan yeni bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba944-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="ba944-115">Örnek görüntüler "`--------Hello World!`" konsoluna.</span><span class="sxs-lookup"><span data-stu-id="ba944-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="ba944-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="ba944-116">PadRight</span></span>  
 <span data-ttu-id="ba944-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Yöntemi, belirtilen toplam uzunluğu elde etmek için özgün bir dizeye sonunda yeterli paneli karakterler birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba944-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="ba944-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Yöntemi doldurma karakteri boşluk kullanır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba944-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="ba944-119">Aşağıdaki kod örneğinde <xref:System.String.PadRight%2A> yirmi karakterden uzun olduğundan yeni bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba944-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="ba944-120">Örnek görüntüler "`Hello World!--------`" konsoluna.</span><span class="sxs-lookup"><span data-stu-id="ba944-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ba944-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba944-121">See Also</span></span>  
 [<span data-ttu-id="ba944-122">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="ba944-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
