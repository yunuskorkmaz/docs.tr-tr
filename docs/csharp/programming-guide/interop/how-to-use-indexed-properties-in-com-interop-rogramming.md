---
title: 'Nasıl yapılır: COM birlikte çalışma programlama- C# programlama kılavuzunda dizinli özellikleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: f1be14ad7ddb6973cc89f10c1735ba2ebce13f97
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971657"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Nasıl yapılır: COM birlikte çalışma programlamada dizinli özellikleri kullanma (C# Programlama Kılavuzu)
*Dizinli Özellikler* , programlama içinde C# parametreleri olan com özelliklerinin hangi şekilde tüketildiğini geliştirir. Dizinli Özellikler C#, Microsoft Office programlamayı geliştirmek için [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../language-reference/keywords/dynamic.md)) ve [katıştırılmış tür bilgileri](../../../standard/assembly/embed-types-visual-studio.md)gibi görseldeki diğer özelliklerle birlikte çalışır.  
  
 Önceki sürümlerinde C#yöntemlere yalnızca `get` yöntemin parametresi `set` yoksa ve yöntemi bir ve yalnızca bir değer parametresi varsa özellikler olarak erişilebilir. Ancak, tüm COM özellikleri bu kısıtlamaları karşılamıyor. Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğinin, Aralık adı için `get` bir parametre gerektiren bir erişimcisi vardır. Geçmişte, `Range` özelliği doğrudan erişemediği için, aşağıdaki örnekte gösterildiği gibi `get_Range` yöntemini kullanmanız gerekiyordu.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 Dizini oluşturulmuş Özellikler bunun yerine aşağıdakini yazmanızı sağlar:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> Önceki örnek ayrıca, öğesini atlamanızı `Type.Missing`sağlayan [isteğe bağlı bağımsız değişkenler](../classes-and-structs/named-and-optional-arguments.md) özelliğini de kullanır.  
  
 Benzer şekilde, `Value` C# 3,0 ve önceki bir <xref:Microsoft.Office.Interop.Excel.Range> nesnenin özelliğinin değerini ayarlamak için iki bağımsız değişken gereklidir. Bir, Aralık değerinin türünü belirten isteğe bağlı bir parametre için bağımsız değişken sağlar. Diğer, `Value` özelliğinin değerini sağlar. Aşağıdaki örneklerde bu teknikler gösterilmektedir. Her ikisi de a1 hücresinin değerini olarak `Name`ayarlayın.
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 Dizini oluşturulmuş Özellikler bunun yerine aşağıdaki kodu yazmanızı sağlar.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 Kendinizinkini dizinli Özellikler oluşturamazsınız. Özelliği yalnızca var olan dizinli özelliklerin kullanımını destekler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, bir örnek gösterir. Office API 'sine erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Visual C# özelliklerini](./how-to-access-office-onterop-objects.md)kullanarak Office birlikte çalışma nesnelerine erişin.  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/keywords/dynamic.md)
- [Tür dinamiği kullanma](../types/using-type-dynamic.md)
- [Nasıl yapılır: Office Programlamada adlandırılmış ve Isteğe bağlı bağımsız değişkenleri kullanma](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişin](./how-to-access-office-onterop-objects.md)
- [İzlenecek yol: Office programlama](./walkthrough-office-programming.md)
