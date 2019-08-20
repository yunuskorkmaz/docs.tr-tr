---
title: 'Nasıl yapılır: Son C# programlama kılavuzunu kullanarak temizlik kodu yürütme'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e6adbb864b0450cdd1dbfcc56abdbad2034c5c7a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590252"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Nasıl yapılır: Son kullanılan temizleme kodunu yürütme (C# Programlama Kılavuzu)
Bir `finally` deyimin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır. Bu tür temizliğin bir örneği, <xref:System.IO.Stream.Close%2A> nesnenin ortak <xref:System.IO.FileStream> dil çalışma zamanı tarafından çöp toplanmasını beklemek yerine, aşağıdaki gibi, hemen sonrasında çağrılır:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Örnek  
 Önceki kodu bir `try-catch-finally` ifadeye dönüştürmek için, temizleme kodu, çalışma kodundan aşağıdaki gibi ayrılır.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Bir özel durum, `try` `OpenWrite()` çağrıdan önce blok içinde herhangi bir zamanda olabileceği veya `OpenWrite()` çağrının kendisi başarısız olabileceği için, kapatmayı denediğinde dosyanın açık olduğu garanti edilmez. Blok, <xref:System.IO.Stream.Close%2A> yöntemi çağırmadan önce <xref:System.IO.FileStream> nesnenin olmadığından `null` emin olmak için bir denetim ekler. `finally` Denetim olmadan, <xref:System.NullReferenceException>blok kendi kendine oluşturabilir, ancak mümkünse özel durumların `finally` atma işlemi mümkünse kaçınılmalıdır. `finally` `null`  
  
 Veritabanı bağlantısı, bir `finally` blokta kapanmakta olan başka bir adaydır. Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir. Bağlantınızı kapatabilmeniz için önce bir özel durum oluşursa, bu, `finally` bloğu kullanmanın çöp toplama beklerken daha iyi bir durumdur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
