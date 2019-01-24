---
title: Genel türlere - giriş C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: ed767ca100ee0405ce918d2d842d951f09d19e7a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646350"
---
# <a name="introduction-to-generics-c-programming-guide"></a>Genel Türlere Giriş (C# Programlama Kılavuzu)
Genel sınıflar ve yöntemler çalışmalarında, tür güvenliği ve verimlilik genel olmayan karşılıkları edilemez bir şekilde birleştirin. Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile sık kullanılır. .NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel tabanlı koleksiyon sınıflarını içerir. Tüm .NET Framework 2.0 ve daha sonra kullanmak yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi hedefleyen uygulamalar, önerilen <xref:System.Collections.ArrayList>. Daha fazla bilgi için [.NET içindeki genel türler](../../../standard/generics/index.md).  
  
 Elbette, özel, genel türler de oluşturabilirsiniz ve kendi sağlamak için yöntemleri çözümleri ve tür açısından güvenli ve verimli tasarım desenleri genelleştirilmiş. Aşağıdaki kod örneği, Tanıtım amaçlı basit bir genel bağlantılı liste sınıfı gösterir. (Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> sınıf kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan.) Tür parametresi `T` çeşitli konumlarda burada somut bir türde normalde kullanılabilir listesinde depolanan öğenin türünü belirtmek için kullanılır. Bu, aşağıdaki şekillerde kullanılır:  
  
-   Bir yöntemin parametre türü olarak `AddHead` yöntemi.  
  
-   Dönüş türü olarak `Data` iç içe özellik `Node` sınıfı.  
  
-   Özel üye türü olarak `data` içinde iç içe geçmiş sınıf.  
  
 T için iç içe geçmiş kullanılabilir olduğunu unutmayın `Node` sınıfı. Zaman `GenericList<T>` somut bir türde örneğin olarak Örneklendirilmiş bir `GenericList<int>`, her geçtiği `T` ile değiştirilecek `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmak için sınıf. Basit tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeler veya başka herhangi bir özel tür listesini oluşturmak için değiştirilmesi:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türler](../../../csharp/programming-guide/generics/index.md)
