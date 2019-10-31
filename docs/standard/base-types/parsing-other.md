---
title: .NET 'teki diğer dizeleri ayrıştırma
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
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127567"
---
# <a name="parsing-other-strings-in-net"></a>.NET 'teki diğer dizeleri ayrıştırma
Sayısal ve <xref:System.DateTime> dizelerine ek olarak, <xref:System.Char>, <xref:System.Boolean>ve <xref:System.Enum> türlerini temsil eden dizeleri veri türlerine de ayrıştırabilirsiniz.  
  
## <a name="char"></a>Char  
 **Char** veri türüyle ilişkili statik Parse yöntemi, tek bir karakter içeren bir dizeyi Unicode değerine dönüştürmek için yararlıdır. Aşağıdaki kod örneği bir dizeyi Unicode karakter olarak ayrıştırır.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boole değeri  
 **Boolean** veri türü, bir Boolean değeri temsil eden bir dizeyi gerçek bir **Boolean** türüne dönüştürmek için kullanabileceğiniz bir **Parse** yöntemi içerir. Bu yöntem, büyük/küçük harfe duyarlı değildir ve "true" veya "false" içeren bir dizeyi başarıyla ayrıştırabilirler. **Boolean** türüyle ilişkili **Parse** yöntemi, boşluk ile çevrelenen dizeleri de ayrıştırabilirler. Başka bir dize geçmişse, bir <xref:System.FormatException> oluşturulur.  
  
 Aşağıdaki kod örneği bir dizeyi Boole değerine dönüştürmek için **Parse** metodunu kullanır.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Sabit Listesi  
 Statik **Parse** yöntemini bir dize değerine bir sabit listesi türü başlatmak için kullanabilirsiniz. Bu yöntem, ayrıştırma yaptığınız numaralandırma türünü, ayrıştırılacak dizeyi ve ayrıştırmanın büyük/küçük harfe duyarlı olup olmadığını belirten isteğe bağlı bir Boolean bayrağını kabul eder. Ayrıştırıldıkları dize, bir veya daha fazla boş boşluk (boşluk da denir) tarafından öncesinde veya sonra gelen virgüllerle ayrılmış birkaç değer içerebilir. Dize birden çok değer içerdiğinde, döndürülen nesnenin değeri, bir bit düzeyinde veya işlemle birlikte belirtilen tüm değerlerin değeridir.  
  
 Aşağıdaki örnek, bir dize gösterimini bir numaralandırma değerine dönüştürmek için **Parse** metodunu kullanır. <xref:System.DayOfWeek> numaralandırması bir dizeden **Perşembe** olarak başlatılır.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [.NET 'te tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
