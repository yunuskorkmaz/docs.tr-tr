---
title: COM birlikte çalışma programlamada dizinli özellikleri kullanma-C# Programlama Kılavuzu
description: Dizine alınmış özelliklerin, bu C# örneğinde, parametreleri olan COM özelliklerinin hangi şekilde geliştirileceğini nasıl artıracağınızı öğrenin.
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: abd785864bd79d455024cb4501c76a21b349aa91
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303016"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>COM birlikte çalışma programlamada Dizin oluşturulmuş özellikleri kullanma (C# Programlama Kılavuzu)
*Dizinli Özellikler* , C# programlamasında PARAMETRELERI olan com özelliklerinin hangi şekilde tüketildiğini geliştirir. Dizinli özellikler, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/builtin-types/reference-types.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi Visual C# ' deki diğer özelliklerle birlikte çalışır.  
  
 C# ' nin önceki sürümlerinde yöntemlere yalnızca `get` yöntemin parametresi yoksa ve `set` yöntemi bir ve yalnızca bir değer parametresi yoksa özellikler olarak erişilebilir. Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor. Örneğin, Excel özelliğinin, <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> `get` Aralık adı için bir parametre gerektiren bir erişimcisi vardır. Geçmişte, `Range` özelliği doğrudan erişemediği için, `get_Range` Aşağıdaki örnekte gösterildiği gibi yöntemini kullanmanız gerekiyordu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Önceki örnek ayrıca, öğesini atlamanızı sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır `Type.Missing` .  
  
 Benzer şekilde `Value` <xref:Microsoft.Office.Interop.Excel.Range> , C# 3,0 ve önceki bir nesnenin özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir. Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar. Diğer, özelliğinin değerini sağlar `Value` . Aşağıdaki örneklerde bu teknikler gösterilmektedir. Her ikisi de a1 hücresinin değerini olarak ayarlayın `Name` .
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Kendinizinkini dizinli Özellikler oluşturamazsınız. Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir örnek gösterir. Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md).
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [dinamik](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](./how-to-access-office-onterop-objects.md)
- [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)
