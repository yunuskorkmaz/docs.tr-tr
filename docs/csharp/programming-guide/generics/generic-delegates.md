---
title: Genel Temsilciler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712227"
---
# <a name="generic-delegates-c-programming-guide"></a>Genel Temsilciler (C# Programlama Kılavuzu)
Bir [temsilci](../../language-reference/builtin-types/reference-types.md) kendi türü parametrelerini tanımlayabilir. Genel temsilciye başvuran kod, aşağıdaki örnekte gösterildiği gibi, genel bir sınıfı anlık olarak veya genel bir yöntem ararken olduğu gibi kapalı oluşturulmuş bir tür oluşturmak için tür bağımsız değişkenini belirtebilir:  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 C# sürüm 2.0, genel temsilci türlerinin yanı sıra somut olarak da geçerli olan yöntem grubu dönüştürme adı verilen yeni bir özelliğe sahiptir ve bu basitleştirilmiş sözdizimiyle önceki satırı yazmanızı sağlar:  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 Genel bir sınıf içinde tanımlanan temsilciler, genel sınıf türü parametrelerini sınıf yöntemleriyle aynı şekilde kullanabilir.  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 Temsilciye başvuran kod, aşağıdaki gibi, içeren sınıfın tür bağımsız değişkenini belirtmelidir:  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 Genel temsilciler, gönderen bağımsız değişkeni güçlü bir şekilde yazılabilir ve artık .'a ve'den <xref:System.Object>atılmak zorunda olmadığından, olayları tipik tasarım desenine göre tanımlamada özellikle yararlıdır.  
  
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
