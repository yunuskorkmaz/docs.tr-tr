---
title: .NET'te Dolgu Dizeleri
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
ms.openlocfilehash: 2cf114296005456f354d286aa2804fa8a95160dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127618"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="7df15-102">.NET'te Dolgu Dizeleri</span><span class="sxs-lookup"><span data-stu-id="7df15-102">Padding Strings in .NET</span></span>

<span data-ttu-id="7df15-103">Belirli bir toplam <xref:System.String> uzunluğa giden veya izleyen karakterlerle dolgulu özgün bir dizeden oluşan yeni bir dize oluşturmak için aşağıdaki yöntemlerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7df15-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="7df15-104">Dolgu karakteri bir boşluk veya belirli bir karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="7df15-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="7df15-105">Elde edilen dize sağ hizalanmış veya sol ayarı gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="7df15-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="7df15-106">Özgün dizenin uzunluğu zaten istenen toplam uzunluğa eşit veya daha büyükse, dolgu yöntemleri özgün dizeyi değiştirmeden döndürer; daha fazla bilgi **Returns** için, iki aşırı yüklemeve <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemin İade bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="7df15-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="7df15-107">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="7df15-107">Method name</span></span>|<span data-ttu-id="7df15-108">Kullanım</span><span class="sxs-lookup"><span data-stu-id="7df15-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="7df15-109">Belirli bir toplam uzunluğa önde gelen karakterleri içeren bir dize yidizer.</span><span class="sxs-lookup"><span data-stu-id="7df15-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="7df15-110">Belirli bir toplam uzunluğa kadar karakterleri takip eden bir dize pads.</span><span class="sxs-lookup"><span data-stu-id="7df15-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="7df15-111">Padleft</span><span class="sxs-lookup"><span data-stu-id="7df15-111">PadLeft</span></span>  
 <span data-ttu-id="7df15-112">Yöntem, <xref:System.String.PadLeft%2A?displayProperty=nameWithType> belirli bir toplam uzunluğa ulaşmak için özgün bir dize için yeterli öncü pad karakterleri concatenating yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df15-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="7df15-113">Yöntem <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> dolgu karakteri olarak beyaz boşluk <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> kullanır ve yöntem kendi dolgu karakteri belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7df15-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="7df15-114">Aşağıdaki kod örneği, <xref:System.String.PadLeft%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7df15-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="7df15-115">Örnek konsola`--------Hello World!`" " " gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df15-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="7df15-116">Padright</span><span class="sxs-lookup"><span data-stu-id="7df15-116">PadRight</span></span>  
 <span data-ttu-id="7df15-117">Yöntem, <xref:System.String.PadRight%2A?displayProperty=nameWithType> belirli bir toplam uzunluğa ulaşmak için özgün bir dize için yeterli izleme pad karakterleri concatenating yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7df15-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="7df15-118">Yöntem <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> dolgu karakteri olarak beyaz boşluk <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> kullanır ve yöntem kendi dolgu karakteri belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7df15-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="7df15-119">Aşağıdaki kod örneği, <xref:System.String.PadRight%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7df15-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="7df15-120">Örnek konsola`Hello World!--------`" " " gösterir.</span><span class="sxs-lookup"><span data-stu-id="7df15-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7df15-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7df15-121">See also</span></span>

- [<span data-ttu-id="7df15-122">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="7df15-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
