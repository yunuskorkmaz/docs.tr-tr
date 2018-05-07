---
title: Genel Türlere Giriş (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 892b6bfe5cf18bde91221bb8b2fa7ca7a2813870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="introduction-to-generics-c-programming-guide"></a>Genel Türlere Giriş (C# Programlama Kılavuzu)
Genel sınıflar ve yöntemler yeniden kullanılırlığı, tür güvenliği ve genel olmayan'dekiler edilemez şekilde verimliliği birleştirir. Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile en sık kullanılır. .NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel dayalı koleksiyon sınıfları içerir. Tüm uygulamalar, .NET Framework 2.0 ve daha sonra kullanmak yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi hedeflediğiniz önerilir <xref:System.Collections.ArrayList>. Daha fazla bilgi için bkz: [.NET'nda genel türler](../../../standard/generics/index.md).  
  
 Elbette, ayrıca özel genel türleri oluşturabilir ve kendi sağlamak için yöntemleri çözümleri ve tür kullanımı uyumlu ve verimli tasarım desenleri genelleştirilmiş. Aşağıdaki kod örneğinde tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterir. (Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan sınıfı.) Tür parametresi `T` burada somut bir türde normalde kullanılabilir listede depolanan öğenin türünü belirtmek için çeşitli konumlarda kullanılır. Aşağıdaki yollarla kullanılır:  
  
-   Bir yöntemin parametre türü olarak `AddHead` yöntemi.  
  
-   Dönüş türü olarak `Data` iç içe bir özellik `Node` sınıfı.  
  
-   Özel üye türü olarak `data` içinde iç içe geçmiş sınıf.  
  
 T iç içe geçmiş için kullanılabilir olduğunu unutmayın `Node` sınıfı. Zaman `GenericList<T>` somut bir türde ile örneğin olarak örneği bir `GenericList<int>`, her oluşumu `T` ile değiştirilecek `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmasını sağlar. Yalnızca tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeyi veya herhangi bir özel tür listesi oluşturmak için değiştirilmesi:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türler](../../../csharp/programming-guide/generics/index.md)
