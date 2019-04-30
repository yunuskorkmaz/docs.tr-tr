---
title: Açık arabirim uygulaması - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 75b031773f8ac34b04f68ec01b12cd9263413bc3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680083"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)
Varsa bir [sınıfı](../../../csharp/language-reference/keywords/class.md) üyenin sınıf üzerinde uygulama, bu üye, geliştirdikleri kullanılacak iki arabirim neden olmaz ve aynı imzaya sahip bir üye içeren iki arabirimlerini uygular. Aşağıdaki örnekte, tüm çağrıları `Paint` aynı yöntemini çağırır.  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 İki [arabirimi](../../../csharp/language-reference/keywords/interface.md) üyeleri aynı işlev gerçekleştirmez, ancak bu birini veya her ikisini arabirimler yanlış bir uygulanmasına neden olabilir. Arabirim üyesini açık olarak uygulanması mümkün — bir sınıf üyesinin oluşturma yalnızca arabirimi aracılığıyla çağrılır ve bu arabirim için özgüdür. Bu sınıf üyesinin adını arabirimi ve nokta ile adlandırma tarafından gerçekleştirilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 Sınıf üyesi `IControl.Paint` aracılığıyla yalnızca kullanılabilir `IControl` arabirimi ve `ISurface.Paint` aracılığıyla yalnızca kullanılabilir `ISurface`. Her iki yöntem uygulamaları ayrıdır ve hiçbiri doğrudan sınıfta kullanılabilir. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 Açık uygulama, iki arabirim üyeleri aynı adlı bir özelliği ve yöntemi gibi farklı yeri bildirin durumları çözümlemek için de kullanılır:  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 İki arabirim uygulamak için açık uygulama P özellik veya yöntemin P için veya her ikisi de bir derleyici hatası önlemek bir sınıf vardır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Arabirimler](../../../csharp/programming-guide/interfaces/index.md)
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
