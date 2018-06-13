---
title: .NET diğer dizeleri ayrıştırma
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
ms.openlocfilehash: 7becf993db866e24381fe9013c82d74dd91ee9a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568036"
---
# <a name="parsing-other-strings-in-net"></a>.NET diğer dizeleri ayrıştırma
Sayısal yanı sıra ve <xref:System.DateTime> dizeleri, türleri temsil eden dizeleri de ayrıştırmak <xref:System.Char>, <xref:System.Boolean>, ve <xref:System.Enum> veri türlerine.  
  
## <a name="char"></a>Char  
 İlişkili statik parse yöntemi **Char** veri türü tek bir karakterlik Unicode değerini içeren bir dize dönüştürme için yararlıdır. Aşağıdaki kod örneğinde bir dize Unicode karakter ayrıştırır.  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a>Boole değeri  
 **Boolean** veri türü içeren bir **ayrıştırma** bir Boole değeri gerçek bir temsil eden bir dize dönüştürmek için kullanabileceğiniz yöntemi **Boolean** türü. Bu yöntem, büyük küçük harfe duyarlı değildir ve "True" veya "False" içeren bir dize başarıyla ayrıştıramıyor **Ayrıştırma** yöntemi ile ilişkili **Boolean** türü de boşluk tarafından çevrelenen dizeleri ayrıştırma. Herhangi bir dize aktarılırsa bir <xref:System.FormatException> oluşturulur.  
  
 Aşağıdaki kod örneğinde **ayrıştırma** bir dizeyi bir Boolean değerine dönüştürmek için yöntem.  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a>Sabit Listesi  
 Statik kullanabilirsiniz **ayrıştırma** yöntemi bir dize değeri için bir numaralandırma türü başlatılamadı. Bu yöntem, ayrıştırma numaralandırma türü, dizesi ayrıştırılamıyor ve ayrıştırma büyük küçük harfe duyarlı olup olmadığını belirten bir isteğe bağlı mantıksal bayrak kabul eder. Dize Ayrıştırma öncesinde veya (boşluk olarak da bilinir) bir veya daha fazla boş alanları tarafından izlenen virgülle ayırarak birden fazla değer içerebilir. Dize birden fazla değer içeriyorsa, döndürülen nesnenin değerini bit düzeyinde OR işlemi ile birlikte tüm belirtilen değerleri değerdir.  
  
 Aşağıdaki örnek kullanır **ayrıştırma** bir numaralandırma değeri bir dize gösterimi dönüştürmek için yöntem. <xref:System.DayOfWeek> Numaralandırma başlatılır **Perşembe** bir dizeden.  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Dizeleri Ayrıştırma](../../../docs/standard/base-types/parsing-strings.md)  
 [Biçimlendirme Türleri](../../../docs/standard/base-types/formatting-types.md)  
 [.NET tür dönüştürme](../../../docs/standard/base-types/type-conversion.md)
