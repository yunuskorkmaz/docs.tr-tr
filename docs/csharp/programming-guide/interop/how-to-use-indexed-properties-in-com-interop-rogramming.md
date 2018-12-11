---
title: 'Nasıl Yapılır: Özellikleri - COM birlikte çalışma programlamada dizin oluşturulmuş kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 58b3b2646fec0284dc3e04c152b183ce05e05932
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245382"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>Nasıl Yapılır: Özellikleri COM birlikte çalışma programlamada dizin oluşturulmuş kullanma (C# Programlama Kılavuzu)
*Dizin oluşturulmuş özellikleri* parametrelere sahip özellikler COM kullandığı şeklini geliştirmek C# programlama. Diğer özellikler Visual C#, birlikte çalışma özellikleri gibi dizine [adlandırılmış ve isteğe bağlı bağımsız değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), yeni bir tür ([dinamik](../../../csharp/language-reference/keywords/dynamic.md)), ve [gömülü tür bilgileri](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md), Microsoft Office programlama geliştirin.  
  
 Önceki sürümlerde, C#, yöntemler yalnızca şu durumlarda özellikler erişilebilir `get` yönteminin parametresiz vardır ve `set` yöntemi yalnızca tek değer parametresi vardır. Ancak, tüm COM özellikleri bu kısıtlamaları karşılayın. Örneğin, Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> özelliğine sahip bir `get` aralığın adı için bir parametre gerektiren erişimcisi. Geçmişte, olmayan erişim çünkü `Range` özelliği doğrudan tablonuz kullanılacak `get_Range` yöntemi yerine, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Dizinli Özellikler, bunun yerine aşağıdaki yazma olanak sağlar:  
  
 [!code-csharp[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  Ayrıca önceki örneğin kullandığı [isteğe bağlı bağımsız değişkenlere](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) atlamak sağlayan bir özellik `Type.Missing`.  
  
 Benzer şekilde değerini ayarlamak için `Value` özelliği bir <xref:Microsoft.Office.Interop.Excel.Range> nesne Visual C# 2008 ve önceki sürümlerinde, iki bağımsız değişkeni gereklidir. Bir aralık değeri türünü belirten isteğe bağlı parametresi için bağımsız değişken sağlar. Diğer değeri sağlayan `Value` özelliği. Aşağıdaki örnekler, bu teknikleri gösterir. Her ikisi de A1 hücresine değerini `Name`.
  
 [!code-csharp[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Dizinli Özellikler, bunun yerine aşağıdaki kodu yazmak etkinleştirin.  
  
 [!code-csharp[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Dizinli Özellikler kendi oluşturulamıyor. Özelliği, yalnızca mevcut Dizinlenmiş özelliklerin tüketimini destekler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam bir örnek gösterir. Office API'si erişen bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-csharp[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Adlandırılmış ve İsteğe Bağlı Bağımsız Değişkenler](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
- [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
- [Tür dinamiği kullanma](../../../csharp/programming-guide/types/using-type-dynamic.md)  
- [Nasıl yapılır: Office Programlamada adlandırılmış ve isteğe bağlı bağımsız değişkenleri kullanma](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)  
- [Nasıl yapılır: Visual kullanarak Office birlikte çalışma nesnelerine erişim C# özellikleri](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
- [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
