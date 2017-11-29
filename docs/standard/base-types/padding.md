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
# <a name="padding-strings-in-net"></a>.NET dizeleri doldurma
Aşağıdakilerden birini kullanmak <xref:System.String> baştaki veya sondaki belirtilen toplam uzunluğu karakterleri ile doldurulan bir özgün dize içeren yeni bir dize oluşturmak için yöntem. Doldurma karakteri boşluk ya da belirtilen bir karakterin olabilir ve bunun sonucunda da sağa hizalı sola hizalı veya bozulmuş olabilir.  
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Belirtilen bir toplam uzunluğu karakter eklenerek bir dize pads.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Sondaki belirtilen toplam uzunluğu karakterleri içeren bir dize pads.|  
  
## <a name="padleft"></a>PadLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> Yöntemi, belirtilen toplam uzunluğu elde etmek için özgün bir dizeye başında yeterli paneli karakter birleştirerek yeni bir dize oluşturur. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Yöntemi doldurma karakteri boşluk kullanır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize olanak sağlar.  
  
 Aşağıdaki kod örneğinde <xref:System.String.PadLeft%2A> yirmi karakterden uzun olduğundan yeni bir dize oluşturmak için yöntemi. Örnek görüntüler "`--------Hello World!`" konsoluna.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> Yöntemi, belirtilen toplam uzunluğu elde etmek için özgün bir dizeye sonunda yeterli paneli karakterler birleştirerek yeni bir dize oluşturur. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Yöntemi doldurma karakteri boşluk kullanır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize olanak sağlar.  
  
 Aşağıdaki kod örneğinde <xref:System.String.PadRight%2A> yirmi karakterden uzun olduğundan yeni bir dize oluşturmak için yöntemi. Örnek görüntüler "`Hello World!--------`" konsoluna.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel dize işlemleri](../../../docs/standard/base-types/basic-string-operations.md)
