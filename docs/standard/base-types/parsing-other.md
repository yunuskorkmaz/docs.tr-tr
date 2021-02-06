---
description: "Daha fazla bilgi edinin: .NET 'te diğer dizeleri ayrıştırma"
title: .NET 'teki diğer dizeleri ayrıştırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
ms.openlocfilehash: 10d8d9686c451334929471d06e4e3136fca80c68
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642727"
---
# <a name="parsing-other-strings-in-net"></a>.NET 'teki diğer dizeleri ayrıştırma

Sayısal ve dizelere ek olarak,, <xref:System.DateTime> ve türlerini temsil eden dizeleri de ayrıştırabilirsiniz <xref:System.Char> <xref:System.Boolean> <xref:System.Enum> .  
  
## <a name="char"></a>Char  

 **Char** veri türüyle ilişkili statik Parse yöntemi, tek bir karakter içeren bir dizeyi Unicode değerine dönüştürmek için yararlıdır. Aşağıdaki kod örneği bir dizeyi Unicode karakter olarak ayrıştırır.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boole  

 **Boolean** veri türü, bir Boolean değeri temsil eden bir dizeyi gerçek bir **Boolean** türüne dönüştürmek için kullanabileceğiniz bir **Parse** yöntemi içerir. Bu yöntem, büyük/küçük harfe duyarlı değildir ve "true" veya "false" içeren bir dizeyi başarıyla ayrıştırabilirler. **Boolean** türüyle ilişkili **Parse** yöntemi, boşluk ile çevrelenen dizeleri de ayrıştırabilirler. Başka bir dize geçirilirse, bir <xref:System.FormatException> oluşturulur.  
  
 Aşağıdaki kod örneği bir dizeyi Boole değerine dönüştürmek için **Parse** metodunu kullanır.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Sabit Listesi  

 Statik **Parse** yöntemini bir dize değerine bir sabit listesi türü başlatmak için kullanabilirsiniz. Bu yöntem, ayrıştırma yaptığınız numaralandırma türünü, ayrıştırılacak dizeyi ve ayrıştırmanın büyük/küçük harfe duyarlı olup olmadığını belirten isteğe bağlı bir Boolean bayrağını kabul eder. Ayrıştırıldıkları dize, bir veya daha fazla boş boşluk (boşluk da denir) tarafından öncesinde veya sonra gelen virgüllerle ayrılmış birkaç değer içerebilir. Dize birden çok değer içerdiğinde, döndürülen nesnenin değeri, bir bit düzeyinde veya işlemle birlikte belirtilen tüm değerlerin değeridir.  
  
 Aşağıdaki örnek, bir dize gösterimini bir numaralandırma değerine dönüştürmek için **Parse** metodunu kullanır. <xref:System.DayOfWeek>Sabit listesi bir dizeden **Perşembe** olarak başlatılır.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](parsing-strings.md)
- [Biçimlendirme Türleri](formatting-types.md)
- [.NET 'te tür dönüştürme](type-conversion.md)
