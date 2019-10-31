---
title: .NET 'teki dizeleri doldurma
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127618"
---
# <a name="padding-strings-in-net"></a>.NET 'teki dizeleri doldurma

Belirtilen toplam uzunluğa baştaki veya sondaki karakterlerle doldurulan bir özgün dizeden oluşan yeni bir dize oluşturmak için aşağıdaki <xref:System.String> yöntemlerinden birini kullanın. Doldurma karakteri bir boşluk veya belirtilen karakter olabilir. Elde edilen dize, sağa hizalı veya sola hizalı olarak görünür. Özgün dizenin uzunluğu, istenen toplam uzunluğa zaten eşitse veya daha büyükse, doldurma yöntemleri özgün dizeyi değiştirilmemiş şekilde döndürür; daha fazla bilgi için, <xref:System.String.PadLeft%2A?displayProperty=nameWithType> ve <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemlerinin iki aşırı yüklemesinin **geri dönüş** bölümlerine bakın.
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Baştaki karakterlerle belirtilen toplam uzunluğa sahip bir dizeyi defterler.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Sondaki karakterlerle bir dizeyi belirtilen toplam uzunluğa göre defterler.|  
  
## <a name="padleft"></a>Asma sol  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> yöntemi, belirtilen toplam uzunluğu elde etmek için, bir özgün dizeye yeterince önde gelen doldurma karakteri birleştirerek yeni bir dize oluşturur. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> yöntemi, doldurma karakteri olarak boşluk kullanır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakterinizi belirtmenizi sağlar.  
  
 Aşağıdaki kod örneği, yirmi karakter uzunluğunda yeni bir dize oluşturmak için <xref:System.String.PadLeft%2A> yöntemini kullanır. Örnek, konsola "`--------Hello World!`" görüntüler.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>Asma sağ  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemi, belirtilen toplam uzunluğu elde etmek için bir özgün dizeye yeterli sayıda izleyen doldurma karakteri birleştirerek yeni bir dize oluşturur. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> yöntemi, doldurma karakteri olarak boşluk kullanır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakterinizi belirtmenizi sağlar.  
  
 Aşağıdaki kod örneği, yirmi karakter uzunluğunda yeni bir dize oluşturmak için <xref:System.String.PadRight%2A> yöntemini kullanır. Örnek, konsola "`Hello World!--------`" görüntüler.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
