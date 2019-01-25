---
title: . NET'te diğer dizeleri ayrıştırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf8a7b090b7a54328101478aed7edbbc5efd79ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603631"
---
# <a name="parsing-other-strings-in-net"></a>. NET'te diğer dizeleri ayrıştırma
Sayısal yanı sıra ve <xref:System.DateTime> dizeleri türleri temsil eden dizeleri de ayrıştırmak <xref:System.Char>, <xref:System.Boolean>, ve <xref:System.Enum> veri türlerini.  
  
## <a name="char"></a>Char  
 İlişkili statik parse metoduna **Char** veri türü, tek bir karakter Unicode değerini içeren bir dize dönüştürmek için kullanışlıdır. Aşağıdaki kod örneği, bir Unicode karakter bir dizeyi ayrıştırır.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boole değeri  
 **Boole** veri türü içeren bir **ayrıştırma** gerçek bir bir Boolean değeri temsil eden bir dize dönüştürmek için kullanabileceğiniz yöntem **Boole** türü. Bu yöntem, büyük küçük harfe duyarlı değildir ve "True" veya "False" içeren bir dizeyi başarıyla ayrıştırmak **Ayrıştırma** yöntemi ile ilişkili **Boole** türü de boşluk tarafından çevrilmiş dizeleri ayrıştırma. Herhangi bir dize iletilmezse, bir <xref:System.FormatException> oluşturulur.  
  
 Aşağıdaki kod örneğinde **ayrıştırma** bir dizeyi bir Boolean değerine dönüştürülmesi için yöntemi.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Sabit Listesi  
 Statik kullanabileceğiniz **ayrıştırma** bir dize değeri için bir numaralandırma türüne başlatmak için yöntemi. Bu yöntem, ayrıştırma numaralandırma türü, ayrıştırılacak dize ve ayrıştırma büyük küçük harfe duyarlı olup olmadığını belirten isteğe bağlı bir Boole bayrağı kabul eder. Dize Ayrıştırma çok sayıda değer öncesinde mı (boşluk olarak da bilinir) bir veya daha fazla boş alanları tarafından izlenen, virgülle ayrılmış içerebilir. Dize birden çok değer içeriyorsa, döndürülen nesnenin değerini bir bit düzeyinde OR işlemi ile birlikte tüm belirtilen değerleri değeridir.  
  
 Aşağıdaki örnekte **ayrıştırma** bir sabit listesi değeri dize gösterimine dönüştürmek için yöntemi. <xref:System.DayOfWeek> Numaralandırması için başlatılan **Perşembe** bir dizeden.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [.NET içinde tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
