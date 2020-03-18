---
title: Nasıl nihayet kullanarak temizleme kodu yürütmek için - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705281"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Son olarak kullanarak temizleme kodu nasıl çalıştırılatır (C# Programlama Kılavuzu)
Bir `finally` deyimin amacı, genellikle dış kaynak tutan nesnelerin gerekli şekilde temizlenmesinin, bir özel durum atılsa bile hemen gerçekleşmesini sağlamaktır. Bu tür bir temizleme <xref:System.IO.Stream.Close%2A> örneği, <xref:System.IO.FileStream> nesnenin ortak dil çalışma zamanı tarafından toplanan çöp olmasını beklemek yerine kullanımdan hemen sonra aşağıdaki gibi çağrı yapmaktır:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Örnek  
 Önceki kodu bir `try-catch-finally` deyime dönüştürmek için, temizleme kodu aşağıdaki gibi çalışma kodundan ayrılır.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Aramadan önce `try` blok içinde herhangi bir zamanda bir `OpenWrite()` özel durum oluşabileceğinden veya aramanın kendisi başarısız olabileceğinden, kapatmaya çalıştığımızda dosyanın açık olduğu garanti edilmez. `OpenWrite()` Blok, `finally` <xref:System.IO.FileStream> <xref:System.IO.Stream.Close%2A> yöntemi çağırmadan önce nesnenin `null` olmadığından emin olmak için bir denetim ekler. `null` Kontrol olmadan, `finally` blok kendi <xref:System.NullReferenceException>atabilir, ancak mümkünse bloklarda `finally` özel durumlar atma kaçınılmalıdır.  
  
 Veritabanı bağlantısı, bir blokta kapatılması `finally` için iyi bir adaydır. Veritabanı sunucusuna izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca çabuk kapatmanız gerekir. Bağlantınızı kapatmadan önce bir özel durum atılırsa, bu, bloğu kullanmanın `finally` çöp toplamayı beklemekten daha iyi olduğu başka bir durumdur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
- [Özel Durum Taşıma](./exception-handling.md)
- [Ekstresi'ni kullanma](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
