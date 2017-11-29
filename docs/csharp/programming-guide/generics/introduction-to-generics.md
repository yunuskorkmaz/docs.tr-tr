---
title: "Genel Türlere Giriş (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ec4fe9cc9fe7bf868fcc8afe4dc4e4234241e352
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-generics-c-programming-guide"></a>Genel Türlere Giriş (C# Programlama Kılavuzu)
Genel sınıflar ve yöntemler yeniden kullanılırlığı, tür güvenliği ve genel olmayan'dekiler edilemez şekilde verimliliği birleştirir. Genel türler, koleksiyonlar ve bunlar üzerinde çalışan yöntemleri ile en sık kullanılır. .NET Framework sınıf kitaplığı 2.0 sürümünü sağlayan yeni bir ad alanı <xref:System.Collections.Generic>, birkaç yeni genel dayalı koleksiyon sınıfları içerir. Tüm uygulamalar hedef önerilir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 2.0 ve daha sonra yeni genel koleksiyon sınıfları yerine eski genel olmayan ortaklarınıza gibi kullandığınız <xref:System.Collections.ArrayList>. Daha fazla bilgi için bkz: [.NET Framework Sınıf Kitaplığı'nda genel türler](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md).  
  
 Elbette, ayrıca özel genel türleri oluşturabilir ve kendi sağlamak için yöntemleri çözümleri ve tür kullanımı uyumlu ve verimli tasarım desenleri genelleştirilmiş. Aşağıdaki kod örneğinde tanıtım amacıyla basit bir genel bağlantılı liste sınıfı gösterir. (Çoğu durumda, kullanmanız gereken <xref:System.Collections.Generic.List%601> kendi oluşturmak yerine .NET Framework sınıf kitaplığı tarafından sağlanan sınıfı.) Tür parametresi `T` burada somut bir türde normalde kullanılabilir listede depolanan öğenin türünü belirtmek için çeşitli konumlarda kullanılır. Aşağıdaki yollarla kullanılır:  
  
-   Bir yöntemin parametre türü olarak `AddHead` yöntemi.  
  
-   Genel yöntem dönüş türü olarak `GetNext` ve `Data` iç içe bir özellik `Node` sınıfı.  
  
-   Özel üye verileri iç içe geçmiş sınıf türü.  
  
 T iç içe geçmiş için kullanılabilir olduğunu unutmayın `Node` sınıfı. Zaman `GenericList<T>` somut bir türde ile örneğin olarak örneği bir `GenericList<int>`, her oluşumu `T` ile değiştirilecek `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 Aşağıdaki kod örneği, istemci kodu Genel nasıl kullandığını gösterir `GenericList<T>` tamsayı listesi oluşturmasını sağlar. Yalnızca tür bağımsız değişkeni değiştirerek aşağıdaki kodu kolayca dizeyi veya herhangi bir özel tür listesi oluşturmak için değiştirilmesi:  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel türler](../../../csharp/programming-guide/generics/index.md)
