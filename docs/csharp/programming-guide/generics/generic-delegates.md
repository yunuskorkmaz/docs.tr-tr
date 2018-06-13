---
title: Genel Temsilciler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: a9f06dcf608a83b53e894310f20810182cf6daa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332913"
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Genel Yöntemler](../../../csharp/programming-guide/generics/generic-methods.md)  
 [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)  
 [Genel Arabirimler](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [Genel Türler](~/docs/standard/generics/index.md)
