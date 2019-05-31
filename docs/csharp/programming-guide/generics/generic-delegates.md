---
title: Genel temsilciler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: ff19b3d71858552158a8ae5d0ab362a86dc98e65
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423502"
---
# <a name="generic-delegates-c-programming-guide"></a>Genel Temsilciler (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) kendi tür parametreleri tanımlayabilirsiniz. Kod başvurularını Genel temsilci kapalı bir oluşturulmuş tür, gibi ne zaman oluşturulacağını tür bağımsız değişkeni belirtebilirsiniz genel bir sınıf örnekleme veya aşağıdaki örnekte gösterildiği gibi bir genel yöntem çağırma:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C# sürüm 2.0 somut yanı sıra Genel temsilci türleri için geçerlidir ve önceki satıra bu Basitleştirilmiş söz dizimi yazmanızı sağlar yöntem grubu dönüştürme adlı yeni bir özellik vardır:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Temsilciler genel bir sınıf içinde tanımlanan genel sınıf türündeki parametrelere sınıfı yöntemleri yapan aynı şekilde kullanabilirsiniz.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Temsilci başvurduğu kod şu şekilde içerilen sınıfının, tür bağımsız değişkeni belirtmeniz gerekir:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Genel temsilciler olayları gönderen bağımsız değişken türü kesin belirlenmiş ve ondan dönüştürme artık sahip olduğundan, normal tasarım deseni temel alınarak tanımlarken kullanışlı <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/index.md)
- [Genel Yöntemler](../../../csharp/programming-guide/generics/generic-methods.md)
- [Genel Sınıflar](../../../csharp/programming-guide/generics/generic-classes.md)
- [Genel Arabirimler](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
- [Genel Türler](~/docs/standard/generics/index.md)
