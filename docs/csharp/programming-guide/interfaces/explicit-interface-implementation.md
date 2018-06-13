---
title: Açık Arabirim Uygulaması (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 7494f7d6a3897d56419f9d3aa96668fd9dab5f35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331597"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)
Varsa bir [sınıfı](../../../csharp/language-reference/keywords/class.md) bu üye sınıfını uygulama bu üye olarak kendi uygulaması kullanmak her iki arabirimde neden olmaz üyesi aynı imzayla içeren iki arabirimlerini uygular. Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemini çağırma.  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 İki [arabirimi](../../../csharp/language-reference/keywords/interface.md) üyeleri aynı işlevi gerçekleştirmez, ancak bu birini veya her ikisini arabirimler yanlış uygulaması için yol açabilir. Arabirim üyesini açıkça uygulama mümkündür — bir sınıf üyesi oluşturmayı yalnızca arabirimi aracılığıyla çağrılır ve bu arabirim için özeldir. Bu sınıf üyesi süre ve arabirim adı ile adlandırma tarafından gerçekleştirilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 Sınıf üyesi `IControl.Paint` aracılığıyla yalnızca kullanılabilir `IControl` arabirimi ve `ISurface.Paint` aracılığıyla yalnızca kullanılabilir `ISurface`. Her iki yöntem uygulamalarını ayrıdır ve ikisi sınıfında doğrudan kullanılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 Açık uygulama burada iki arabirim aynı adlı bir özellik ve yöntemi gibi farklı üyeleri bildirme durumları çözümlemek için de kullanılır:  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 Her iki arabirimde uygulamak için bir sınıf derleyici hatası önlemek için açık uygulama P özelliği veya yöntemi P için veya her ikisini de kullanması gerekir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
