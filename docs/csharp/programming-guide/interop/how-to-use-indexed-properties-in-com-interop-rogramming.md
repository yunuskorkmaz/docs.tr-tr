---
title: COM interop programlamada dizinlenmiş özellikler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712071"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>COM interop programlamada dizinlenmiş özellikler nasıl kullanılır (C# Programlama Kılavuzu)
*Dizinlenmiş özellikler,* parametreleri olan COM özelliklerinin C# programlamada nasıl tüketildiğini geliştirir. Dizine eklenmiş özellikler, Microsoft Office programlamasını geliştirmek için Visual C#'daki [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür[(dinamik)](../../language-reference/builtin-types/reference-types.md)ve [katıştılı tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi diğer özelliklerle birlikte çalışır.  
  
 C#'ın önceki sürümlerinde, yöntemlere yalnızca `get` yöntemin parametreleri `set` yoksa ve yöntemin tek ve tek bir değer parametresi varsa özellik olarak erişilebilir. Ancak, tüm COM özellikleri bu kısıtlamaları karşılamaz. Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliği, `get` aralığın adı için bir parametre gerektiren bir erişime sahiptir. Geçmişte, `Range` özelliğe doğrudan erişemediğiniz için, aşağıdaki örnekte gösterildiği gibi `get_Range` yöntemi kullanmanız gerekiyordu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Dizinlenmiş özellikler yerine aşağıdakileri yazmanızı sağlar:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Önceki örnekte, atlayabilmenizi sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliği de `Type.Missing`kullanır.  
  
 Benzer şekilde C# 3.0 <xref:Microsoft.Office.Interop.Excel.Range> ve daha önce bir nesnenin `Value` özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir. Bir aralık değeri türünü belirten isteğe bağlı bir parametre için bir bağımsız değişken sağlar. Diğeri `Value` mülkün değerini sağlar. Aşağıdaki örneklerde bu teknikler gösterilmektedir. Her ikisi de A1 hücresinin değerini `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Dizinlenmiş özellikler yerine aşağıdaki kodu yazmanızı sağlar.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Kendi dizinlenmiş özellikleri oluşturamazsınız. Özellik yalnızca varolan dizinlenmiş özelliklerin tüketimini destekler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod tam bir örnek gösterir. Office API'sine erişen bir projeyi nasıl ayarladığınız hakkında daha fazla bilgi için [C# özelliklerini kullanarak Office interop nesnelerine nasıl erişilir'e](./how-to-access-office-onterop-objects.md)bakın.
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [Dinamik](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Office programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](./how-to-access-office-onterop-objects.md)
- [Walkthrough: Office Programlama](./walkthrough-office-programming.md)
