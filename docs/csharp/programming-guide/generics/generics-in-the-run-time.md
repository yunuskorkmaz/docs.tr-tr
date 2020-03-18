---
title: Çalışma Süresindeki Jenerikler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: a53a21d3028e588f5c4d5ce7bf35fad8d3720a08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75702993"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
Genel bir tür veya yöntem Microsoft ara dili (MSIL) içine derlendiğinde, tür parametrelerine sahip olarak tanımlayan meta veriler içerir. Genel bir tür için MSIL'in nasıl kullanılacağı, sağlanan tür parametresinin bir değer türü veya başvuru türü olup olmadığına bağlı olarak değişir.  
  
 Genel bir tür ilk parametre olarak bir değer türü ile inşa edildiğinde, çalışma zamanı, msil'deki uygun konumlarda verilen parametre veya parametrelerle özel leştirilmiş bir genel yazı oluşturur. Özelleştirilmiş genel türleri, parametre olarak kullanılan her benzersiz değer türü için bir kez oluşturulur.  
  
 Örneğin, program kodunuzu tamsayılardan oluşan bir yığın olarak ilan ettiğini varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 Bu noktada, çalışma zamanı, <xref:System.Collections.Generic.Stack%601> tamsayı yada parametresi için uygun şekilde değiştirilen sınıfın özel leştirilmiş bir sürümünü oluşturur. Şimdi, program kodunuz bir tamsayı yığını kullandığında, çalışma zamanı oluşturulan <xref:System.Collections.Generic.Stack%601> özel sınıfı yeniden kullanır. Aşağıdaki örnekte, bir tamsayı yığınının iki örneği oluşturulur ve kodun `Stack<int>` tek bir örneğini paylaşırlar:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Ancak, parametresi olarak kullanıcı <xref:System.Collections.Generic.Stack%601> `long` tanımlı yapı gibi farklı bir değer türüne sahip başka bir sınıfın kodunuzdaki başka bir noktada oluşturulduğunu varsayalım. Sonuç olarak, çalışma zamanı genel türün başka bir sürümünü `long` oluşturur ve MSIL'deki uygun konumlardaki bir sürümün yerine geçer. Her özel genel sınıf yerel olarak değer türünü içerdiğinden dönüşümler artık gerekli değildir.  
  
 Genel ler başvuru türleri için biraz farklı çalışır. Genel bir tür herhangi bir başvuru türüyle ilk kez oluşturuldurda, çalışma zamanı, MSIL'deki parametrelerin yerine nesne başvuruları içeren özel leştirilmiş bir genel yazı oluşturur. Daha sonra, yapılandırılan bir tür, parametresi olarak bir başvuru türüyle anlık olarak anında ne zaman olursa olsun, çalışma zamanı genel türün önceden oluşturulmuş özel sürümünü yeniden kullanır. Tüm başvurular aynı boyutta olduğundan bu mümkündür.  
  
 Örneğin, bir `Customer` sınıf ve sınıf `Order` olmak üzere iki başvuru türünüz olduğunu ve `Customer` ayrıca bir tür yığını oluşturduğunuzu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 Bu noktada, çalışma zamanı, verileri depolamak <xref:System.Collections.Generic.Stack%601> yerine daha sonra doldurulacak nesne başvurularını depolayan sınıfın özelleştirilmiş bir sürümünü oluşturur. Bir sonraki kod satırının, adı geçen `Order`başka bir başvuru türü yığını oluşturduğunu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Değer türlerinin aksine, <xref:System.Collections.Generic.Stack%601> `Order` sınıfın başka bir özel sürümü türü için oluşturulmaz. Bunun yerine, <xref:System.Collections.Generic.Stack%601> sınıfın özelleştirilmiş sürümünün bir örneği `orders` oluşturulur ve değişken buna başvurmak üzere ayarlanır. Daha sonra bir `Customer` tür yığını oluşturmak için bir kod satırı yla karşılaştığınızı varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Türü kullanılarak oluşturulan <xref:System.Collections.Generic.Stack%601> sınıfın önceki kullanımında olduğu gibi, özelleştirilmiş <xref:System.Collections.Generic.Stack%601> sınıfın başka bir örneği oluşturulur. `Order` Burada bulunan işaretçiler, bir `Customer` tür boyutunda bir bellek alanına başvurmak üzere ayarlanmış. Başvuru türlerinin sayısı programdan programa çılgınca değişebildiği için, jeneriklerin C# uygulaması, başvuru türlerinin genel sınıfları için derleyici tarafından oluşturulan özel sınıf sayısını bire indirerek kod miktarını büyük ölçüde azaltır.  
  
 Ayrıca, genel bir C# sınıfı bir değer türü veya başvuru türü parametresi kullanılarak anında olduğunda, yansıma çalışma zamanında sorgulayabilir ve hem gerçek türü hem de türü parametresi tespit edilebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Türler](../../../standard/generics/index.md)
