---
title: .NET'te Diğer Dizeleri Ayrışdırma
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127567"
---
# <a name="parsing-other-strings-in-net"></a>.NET'te Diğer Dizeleri Ayrışdırma
Sayısal <xref:System.DateTime> ve dizeleri ek olarak, aynı zamanda <xref:System.Char>türleri temsil dizeleri <xref:System.Boolean>ayrıştını , ve <xref:System.Enum> veri türleri içine.  
  
## <a name="char"></a>Char  
 **Char** veri türüyle ilişkili statik ayrıştırma yöntemi, tek bir karakter içeren bir dizeyi Unicode değerine dönüştürmek için yararlıdır. Aşağıdaki kod örneği, bir dizeyi Unicode karakterine benzeter.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boole  
 Boolean veri türü, **Boolean** değerini temsil eden bir dizeyi gerçek **boolean** türüne dönüştürmek için kullanabileceğiniz bir **Ayrışdır** yöntemi içerir. Bu yöntem büyük/küçük harf duyarlı değildir ve "True" veya "False" içeren bir dizeyi başarıyla ayrıştırabilir. **Boolean** türüyle ilişkili **Ayrıştırıcı** yöntemi, beyaz boşluklarla çevrili dizeleri de ayrıştırabilir. Başka bir dize geçilirse, bir <xref:System.FormatException> atılır.  
  
 Aşağıdaki kod örneği, bir dizeyi Boolean değerine dönüştürmek için **Ayrışma** yöntemini kullanır.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Sabit Listesi  
 Bir dizinin değerine numaralandırma türünü başlatmak için statik **Ayrışma** yöntemini kullanabilirsiniz. Bu yöntem, ayrıştırdığınız numaralandırma türünü, ayrıştırmak için dize ve ayrıştırma durumda duyarlı olup olmadığını belirten isteğe bağlı Boolean bayrağı kabul eder. Ayrıştırdığınız dize, virgülle ayrılmış birkaç değer içerebilir ve bu değerler bir veya daha fazla boş boşluk (beyaz boşluk olarak da adlandırılır) tarafından önce veya ardından gelebilir. Dize birden çok değer içeriyorsa, döndürülen nesnenin değeri, bitwise OR işlemiyle birlikte tüm belirtilen değerlerin değeridir.  
  
 Aşağıdaki örnek, dize gösterimini numaralandırma değerine dönüştürmek için **Parse** yöntemini kullanır. Numaralandırma <xref:System.DayOfWeek> bir dize **perşembeye** başharfle.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)
- [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)
- [.NET'te Tür Dönüştürme](../../../docs/standard/base-types/type-conversion.md)
