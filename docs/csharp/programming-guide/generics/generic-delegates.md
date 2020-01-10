---
title: Genel Temsilciler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712227"
---
# <a name="generic-delegates-c-programming-guide"></a>Genel Temsilciler (C# Programlama Kılavuzu)
Bir [temsilci](../../language-reference/builtin-types/reference-types.md) kendi tür parametrelerini tanımlayabilir. Genel temsilciye başvuran kod, aşağıdaki örnekte gösterildiği gibi, bir genel sınıf örneği oluşturulurken veya genel bir yöntemi çağırırken olduğu gibi kapalı bir oluşturulmuş tür oluşturmak için tür bağımsız değişkenini belirtebilir:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C#sürüm 2,0 ' de, somut ve genel temsilci türleri için geçerli olan Yöntem grubu dönüştürmesi adlı yeni bir özellik vardır ve bu Basitleştirilmiş söz dizimi ile önceki satırı yazmanızı sağlar:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Genel bir sınıf içinde tanımlanan temsilciler, sınıf yöntemlerinin olduğu şekilde genel sınıf türü parametrelerini kullanabilir.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Temsilciye başvuran kodun, kapsayan sınıfın tür bağımsız değişkenini aşağıdaki gibi belirtmesi gerekir:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Genel Temsilciler, genellikle gönderen bağımsız değişkeni kesin bir şekilde türlenebilir ve <xref:System.Object>'ye ve bu tür bir ve bundan sonra yayınlanmamalı.  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Yöntemler](./generic-methods.md)
- [Genel Sınıflar](./generic-classes.md)
- [Genel Arabirimler](./generic-interfaces.md)
- [Temsilciler](../delegates/index.md)
- [Genel Türler](../../../standard/generics/index.md)
