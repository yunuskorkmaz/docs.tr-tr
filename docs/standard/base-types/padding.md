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
# <a name="padding-strings-in-net"></a>.NET 'teki dizeleri doldurma

<xref:System.String>Belirtilen toplam uzunluğa baştaki veya sondaki karakterlerle doldurulan bir özgün dizeden oluşan yeni bir dize oluşturmak için aşağıdaki yöntemlerden birini kullanın. Doldurma karakteri bir boşluk veya belirtilen karakter olabilir. Elde edilen dize, sağa hizalı veya sola hizalı olarak görünür. Özgün dizenin uzunluğu, istenen toplam uzunluğa zaten eşitse veya daha büyükse, doldurma yöntemleri özgün dizeyi değiştirilmemiş şekilde döndürür; daha fazla bilgi için, ve yöntemlerinin iki aşırı yüklemesinin bölümlerini **döndürür** <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> .
  
|Yöntem adı|Kullanım|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Baştaki karakterlerle belirtilen toplam uzunluğa sahip bir dizeyi defterler.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Sondaki karakterlerle bir dizeyi belirtilen toplam uzunluğa göre defterler.|  
  
## <a name="padleft"></a>Asma sol  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType>Yöntemi, belirli bir toplam uzunluğu elde etmek için, bir özgün dizeye yeterince önde gelen doldurma karakteri birleştirerek yeni bir dize oluşturur. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>Yöntemi, doldurma karakteri olarak boşluk kullanır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakterinizi belirtmenizi sağlar.  
  
 Aşağıdaki kod örneği, <xref:System.String.PadLeft%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemini kullanır. Örnek, konsola " `--------Hello World!` " görüntüler.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>Asma sağ  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType>Yöntemi, belirli bir toplam uzunluğa ulaşmak için bir özgün dizeye yeterli sayıda sondaki doldurma karakteri birleştirerek yeni bir dize oluşturur. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>Yöntemi, doldurma karakteri olarak boşluk kullanır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakterinizi belirtmenizi sağlar.  
  
 Aşağıdaki kod örneği, <xref:System.String.PadRight%2A> yirmi karakter uzunluğunda yeni bir dize oluşturmak için yöntemini kullanır. Örnek, konsola " `Hello World!--------` " görüntüler.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel dize Işlemleri](basic-string-operations.md)
