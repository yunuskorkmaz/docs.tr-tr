---
title: . NET'te dizeleri doldurma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f58e1c3a9e42f48ecc219a2db1649051f9ca20b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811546"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="775fd-102">. NET'te dizeleri doldurma</span><span class="sxs-lookup"><span data-stu-id="775fd-102">Padding Strings in .NET</span></span>

<span data-ttu-id="775fd-103">Aşağıdakilerden birini kullanın <xref:System.String> baştaki veya sondaki karakterler belirtilen toplam uzunluğu sıfır özgün bir dize içeren yeni bir dize oluşturmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="775fd-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="775fd-104">Doldurma karakteri boşluk veya belirtilen bir karakter olabilir.</span><span class="sxs-lookup"><span data-stu-id="775fd-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="775fd-105">Sonuç dizesi sağa veya sola hizalanmış gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="775fd-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="775fd-106">Orijinal dizenin uzunluğu, zaten istenen toplam uzunluğundan büyük veya eşit ise, doldurma yöntemleri değişmeden orijinal dizeyi döndürür; Daha fazla bilgi için **döndürür** bölümlerde iki aşırı yüklemelerinden birini <xref:System.String.PadLeft%2A?displayProperty=nameWithType> ve <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="775fd-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="775fd-107">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="775fd-107">Method name</span></span>|<span data-ttu-id="775fd-108">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="775fd-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="775fd-109">Bir dize için belirtilen bir toplam uzunluğu baştaki ile sıfır ekleyerek doldurur.</span><span class="sxs-lookup"><span data-stu-id="775fd-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="775fd-110">Bir dize sondaki karakterler belirtilen toplam uzunluğu olan sıfır ekleyerek doldurur.</span><span class="sxs-lookup"><span data-stu-id="775fd-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="775fd-111">padLeft</span><span class="sxs-lookup"><span data-stu-id="775fd-111">PadLeft</span></span>  
 <span data-ttu-id="775fd-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Yöntemi, özgün dizeye belirtilen toplam uzunluğu elde etmek için yeterli sayıda önde gelen paneli karakter birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="775fd-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="775fd-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Boşluk doldurma karakteri kullanmaktadır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="775fd-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="775fd-114">Aşağıdaki kod örneğinde <xref:System.String.PadLeft%2A> yirmi karakterden uzun yeni bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="775fd-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="775fd-115">Örnek görüntüler "`--------Hello World!`" konsola.</span><span class="sxs-lookup"><span data-stu-id="775fd-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="775fd-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="775fd-116">PadRight</span></span>  
 <span data-ttu-id="775fd-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Yöntemi, özgün dizeye belirtilen toplam uzunluğu elde etmek için yeterli sonunda paneli karakterler birleştirerek yeni bir dize oluşturur.</span><span class="sxs-lookup"><span data-stu-id="775fd-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="775fd-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Boşluk doldurma karakteri kullanmaktadır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="775fd-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="775fd-119">Aşağıdaki kod örneğinde <xref:System.String.PadRight%2A> yirmi karakterden uzun yeni bir dize oluşturmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="775fd-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="775fd-120">Örnek görüntüler "`Hello World!--------`" konsola.</span><span class="sxs-lookup"><span data-stu-id="775fd-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="775fd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="775fd-121">See also</span></span>

- [<span data-ttu-id="775fd-122">Temel Dize İşlemleri</span><span class="sxs-lookup"><span data-stu-id="775fd-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
