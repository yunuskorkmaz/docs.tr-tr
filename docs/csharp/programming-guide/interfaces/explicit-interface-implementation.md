---
title: Açık arabirim uygulama- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 498c45ff1c5837f5dcb0d4a80d0e3bb249abd694
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589223"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Açık Arabirim Uygulaması (C# Programlama Kılavuzu)
Bir [sınıf](../../language-reference/keywords/class.md) , aynı imzaya sahip bir üye içeren iki arabirim uygularsa, bu üyeyi sınıfında uygulamak, her iki arabirimin de uygulama olarak bu üyeyi kullanmasına neden olur. Aşağıdaki örnekte, tüm çağrıları aynı yöntemi çağırmak için `Paint` çağırır.  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 İki [arabirim](../../language-reference/keywords/interface.md) üyesi aynı işlevi gerçekleştirmez, ancak bu, arabirimlerin bir veya her ikisinin yanlış bir uygulamasına neden olabilir. Yalnızca arabirim aracılığıyla çağrılan ve bu arabirime özgü olan bir sınıf üyesi oluşturarak, bir arabirim üyesini açıkça uygulamak mümkündür. Bu, sınıf üyesini arabirim adı ve nokta ile adlandırarak yapılır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 Sınıf üyesi `IControl.Paint` yalnızca `IControl` arabirim aracılığıyla kullanılabilir ve `ISurface.Paint` yalnızca ile `ISurface`kullanılabilir. Her iki yöntem uygulaması ayrı değildir ve doğrudan sınıfta kullanılamaz. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 Açık uygulama, her biri bir özellik ve bir yöntem gibi aynı ada sahip farklı Üyeler bildiren iki arabirimin da bulunduğu durumları çözümlemek için de kullanılır:  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 Her iki arabirimi de uygulamak için bir sınıf, derleyici hatasından kaçınmak için P ya da Yöntem P ya da her ikisi için açık uygulamayı kullanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](../classes-and-structs/index.md)
- [Arabirimler](./index.md)
- [Devralma](../classes-and-structs/inheritance.md)
