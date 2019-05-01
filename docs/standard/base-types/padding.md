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
# <a name="padding-strings-in-net"></a>. NET'te dizeleri doldurma

Aşağıdakilerden birini kullanın <xref:System.String> baştaki veya sondaki karakterler belirtilen toplam uzunluğu sıfır özgün bir dize içeren yeni bir dize oluşturmak için yöntemleri. Doldurma karakteri boşluk veya belirtilen bir karakter olabilir. Sonuç dizesi sağa veya sola hizalanmış gibi görünür. Orijinal dizenin uzunluğu, zaten istenen toplam uzunluğundan büyük veya eşit ise, doldurma yöntemleri değişmeden orijinal dizeyi döndürür; Daha fazla bilgi için **döndürür** bölümlerde iki aşırı yüklemelerinden birini <xref:System.String.PadLeft%2A?displayProperty=nameWithType> ve <xref:System.String.PadRight%2A?displayProperty=nameWithType> yöntemleri.
  
|Yöntem adı|Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|Bir dize için belirtilen bir toplam uzunluğu baştaki ile sıfır ekleyerek doldurur.|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|Bir dize sondaki karakterler belirtilen toplam uzunluğu olan sıfır ekleyerek doldurur.|  
  
## <a name="padleft"></a>padLeft  
 <xref:System.String.PadLeft%2A?displayProperty=nameWithType> Yöntemi, özgün dizeye belirtilen toplam uzunluğu elde etmek için yeterli sayıda önde gelen paneli karakter birleştirerek yeni bir dize oluşturur. <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Boşluk doldurma karakteri kullanmaktadır ve <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize imkan tanır.  
  
 Aşağıdaki kod örneğinde <xref:System.String.PadLeft%2A> yirmi karakterden uzun yeni bir dize oluşturmak için yöntemi. Örnek görüntüler "`--------Hello World!`" konsola.  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a>PadRight  
 <xref:System.String.PadRight%2A?displayProperty=nameWithType> Yöntemi, özgün dizeye belirtilen toplam uzunluğu elde etmek için yeterli sonunda paneli karakterler birleştirerek yeni bir dize oluşturur. <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Boşluk doldurma karakteri kullanmaktadır ve <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> yöntemi kendi doldurma karakteri belirtmenize imkan tanır.  
  
 Aşağıdaki kod örneğinde <xref:System.String.PadRight%2A> yirmi karakterden uzun yeni bir dize oluşturmak için yöntemi. Örnek görüntüler "`Hello World!--------`" konsola.  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel Dize İşlemleri](../../../docs/standard/base-types/basic-string-operations.md)
