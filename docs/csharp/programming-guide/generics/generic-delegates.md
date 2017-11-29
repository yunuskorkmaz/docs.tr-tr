---
title: "Genel Temsilciler (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1377723f18d6dd0e984538b530acbc7aa8d52feb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-delegates-c-programming-guide"></a>Genel Temsilciler (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) kendi tür parametreleri tanımlayabilirsiniz. Kod başvurularını ne zaman gibi kapalı oluşturulan türü oluşturmak için tür bağımsız değişkeni genel temsilcisi belirtebilirsiniz genel bir sınıf örneği veya aşağıdaki örnekte gösterildiği gibi genel bir yöntemini çağırmadan:  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C# sürüm 2.0 somut yanı sıra Genel temsilci türleri için geçerlidir ve bu Basitleştirilmiş söz dizimi önceki satırla yazmanızı sağlar yöntemi Grup Dönüştürme adlı yeni bir özellik vardır:  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Genel bir sınıf içinde tanımlanan temsilcileri ve genel bir sınıf türü parametrelerine sınıfı yöntemleri yapan aynı şekilde kullanabilirsiniz.  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 Temsilci başvuran kodu içeren sınıfının tür bağımsız değişkeni aşağıdaki gibi belirtmeniz gerekir:  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Genel temsilciler gönderici bağımsız kesin türü belirtilmiş olmalıdır ve artık ve ondan dönüştürme olduğundan tipik tasarım deseni temel alınarak olayları tanımlama özellikle yararlı <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel türlere giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Genel yöntemler](../../../csharp/programming-guide/generics/generic-methods.md)  
 [Genel sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
 [Genel arabirimler](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Genel türler](~/docs/standard/generics/index.md)
