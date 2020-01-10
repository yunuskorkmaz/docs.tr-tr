---
title: COM birlikte çalışma programlama- C# programlama kılavuzunda dizinli özellikleri kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712071"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>COM birlikte çalışma programlamada Dizin oluşturulmuş özellikleri kullanma (C# Programlama Kılavuzu)
*Dizinli Özellikler* , programlama içinde C# parametreleri olan com özelliklerinin hangi şekilde tüketildiğini geliştirir. Dizinli Özellikler C#, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/builtin-types/reference-types.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi görseldeki diğer özelliklerle birlikte çalışır.  
  
 Önceki sürümlerinde C#, yöntemler yalnızca `get` yönteminin parametresi yoksa ve `set` yöntemi bir ve yalnızca bir değer parametresi içeriyorsa özellikler olarak erişilebilir. Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor. Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğinin, Aralık adı için bir parametre gerektiren bir `get` erişimcisi vardır. Geçmişte, `Range` özelliğine doğrudan erişemediği için, aşağıdaki örnekte gösterildiği gibi, bunun yerine `get_Range` yöntemini kullanmanız gerekiyordu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Önceki örnek ayrıca, `Type.Missing`atlamanızı sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır.  
  
 Benzer şekilde, C# 3,0 ve önceki sürümlerde bir <xref:Microsoft.Office.Interop.Excel.Range> nesnesinin `Value` özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir. Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar. Diğeri `Value` özelliği için değer sağlar. Aşağıdaki örneklerde bu teknikler gösterilmektedir. Her ikisi de a1 hücresinin değerini `Name`olarak ayarlayın.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Kendinizinkini dizinli Özellikler oluşturamazsınız. Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir örnek gösterir. Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [özellikleri kullanarak C# Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md).
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Özellikleri kullanarak C# Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md)
- [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)
