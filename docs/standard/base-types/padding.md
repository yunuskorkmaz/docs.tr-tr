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
# <a name="padding-strings-in-net"></a>.NET'te Dolgu Dizeleri

Belirli bir toplam <xref:System.String> uzunluğa giden veya izleyen karakterlerle dolgulu özgün bir dizeden oluşan yeni bir dize oluşturmak için aşağıdaki yöntemlerden birini kullanın. Dolgu karakteri bir boşluk veya belirli bir karakter olabilir. Elde edilen dize sağ hizalanmış veya sol ayarı gibi görünür. Özgün dizenin uzunluğu zaten istenen toplam uzunluğa eşit veya daha büyükse, dolgu yöntemleri özgün dizeyi değiştirmeden döndürer; daha fazla bilgi **Returns** için, iki aşırı yüklemeve <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemin İade bölümlerine bakın.
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Belirli bir toplam uzunluğa önde gelen karakterleri içeren bir dize yidizer.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Belirli bir toplam uzunluğa kadar karakterleri takip eden bir dize pads.|  
  
## <a name="padleft"></a>Padleft  
 Yöntem, <xref:System.String.PadLeft%2A?displayProperty=nameWithType> belirli bir toplam uzunluğa ulaşmak için özgün bir dize için yeterli öncü pad karakterleri concatenating yeni bir dize oluşturur. Yöntem <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> dolgu karakteri olarak beyaz boşluk <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> kullanır ve yöntem kendi dolgu karakteri belirtmenizi sağlar.  
  
 Aşağıdaki kod örneği, <xref:System.String.PadLeft%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemi kullanır. Örnek konsola`--------Hello World!`" " " gösterir.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>Padright  
 Yöntem, <xref:System.String.PadRight%2A?displayProperty=nameWithType> belirli bir toplam uzunluğa ulaşmak için özgün bir dize için yeterli izleme pad karakterleri concatenating yeni bir dize oluşturur. Yöntem <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> dolgu karakteri olarak beyaz boşluk <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> kullanır ve yöntem kendi dolgu karakteri belirtmenizi sağlar.  
  
 Aşağıdaki kod örneği, <xref:System.String.PadRight%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemi kullanır. Örnek konsola`Hello World!--------`" " " gösterir.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
