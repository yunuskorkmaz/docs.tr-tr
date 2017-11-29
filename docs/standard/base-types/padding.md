---
title: .NET dizeleri doldurma
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
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="d2074-102">.NET dizeleri doldurma</span><span class="sxs-lookup"><span data-stu-id="d2074-102">Padding Strings in .NET</span></span>
<span data-ttu-id="d2074-103">Aşağıdakilerden birini kullanmak <xref:System.String> baştaki veya sondaki belirtilen toplam uzunluğu karakterleri ile doldurulan bir özgün dize içeren yeni bir dize oluşturmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d2074-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="d2074-104">Doldurma karakteri boşluk ya da belirtilen bir karakterin olabilir ve bunun sonucunda da sağa hizalı sola hizalı veya bozulmuş olabilir.</span><span class="sxs-lookup"><span data-stu-id="d2074-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="d2074-105">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="d2074-105">Method name</span></span>|<span data-ttu-id="d2074-106">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="d2074-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="d2074-107">Belirtilen bir toplam uzunluğu karakter eklenerek bir dize pads.</span><span class="sxs-lookup"><span data-stu-id="d2074-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="d2074-108">Sondaki belirtilen toplam uzunluğu karakterleri içeren bir dize pads.</span><span class="sxs-lookup"><span data-stu-id="d2074-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="d2074-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="d2074-109">PadLeft</span></span>  
 <span data-ttu-id="d2074-110"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Yöntemi, belirtilen toplam uzunluğu elde etmek için özgün bir dizeye başında yeterli paneli karakter birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2074-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d2074-111"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Yöntemi doldurma karakteri boşluk kullanır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2074-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d2074-112">Aşağıdaki kod örneğinde <xref:System.String.PadLeft%2A> yirmi karakterden uzun olduğundan yeni bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2074-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d2074-113">Örnek görüntüler "`--------Hello World!`" konsoluna.</span><span class="sxs-lookup"><span data-stu-id="d2074-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="d2074-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="d2074-114">PadRight</span></span>  
 <span data-ttu-id="d2074-115"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Yöntemi, belirtilen toplam uzunluğu elde etmek için özgün bir dizeye sonunda yeterli paneli karakterler birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d2074-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d2074-116"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Yöntemi doldurma karakteri boşluk kullanır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d2074-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d2074-117">Aşağıdaki kod örneğinde <xref:System.String.PadRight%2A> yirmi karakterden uzun olduğundan yeni bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d2074-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d2074-118">Örnek görüntüler "`Hello World!--------`" konsoluna.</span><span class="sxs-lookup"><span data-stu-id="d2074-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d2074-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2074-119">See Also</span></span>  
 [<span data-ttu-id="d2074-120">Temel dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="d2074-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
