---
title: 'Nasıl yapılır: COM birlikte çalışma programlama- C# programlama kılavuzunda dizinli özellikleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 0d4e85646a1e7f8c4ee9a73fbf7bf5a01b10b14b
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423216"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Nasıl yapılır: COM Birlikte Çalışma Programlamada Dizin Oluşturulmuş Özellikleri Kullanma (C# Programlama Kılavuzu)
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
 Aşağıdaki kod, bir örnek gösterir. Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişme](./how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/builtin-types/reference-types.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Nasıl yapılır: Office Programlamada Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenleri Kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Nasıl yapılır: Visual C# Özelliklerini Kullanarak Office Birlikte Çalışma Nesnelerine Erişim](./how-to-access-office-onterop-objects.md)
- [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)
