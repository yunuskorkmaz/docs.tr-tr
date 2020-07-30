---
title: Finally-C# programlama kılavuzunu kullanarak Temizleme kodunu yürütme
description: "' Finally ' ifadesini kullanarak Temizleme kodunu yürütmeyi öğrenin. Finally deyimleri, tüm gerekli nesne temizleme işleminin hemen gerçekleşmesini güvence altına aldığından emin olur."
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: 148c1f9fba67659a07c667bb15619d6f3f7c3b2f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302028"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Finally kullanarak temizleme kodu yürütme (C# Programlama Kılavuzu)
Bir `finally` deyimin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır. Bu tür temizliğin bir örneği, <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> nesnenin ortak dil çalışma zamanı tarafından çöp toplanmasını beklemek yerine, aşağıdaki gibi, hemen sonrasında çağrılır:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Örnek  
 Önceki kodu bir ifadeye dönüştürmek için `try-catch-finally` , temizleme kodu, çalışma kodundan aşağıdaki gibi ayrılır.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 Bir özel durum, çağrıdan önce blok içinde herhangi bir zamanda olabileceği `try` `OpenWrite()` veya `OpenWrite()` çağrının kendisi başarısız olabileceği için, kapatmayı denediğinde dosyanın açık olduğu garanti edilmez. `finally`Blok, <xref:System.IO.FileStream> `null` yöntemi çağırmadan önce nesnenin olmadığından emin olmak için bir denetim ekler <xref:System.IO.Stream.Close%2A> . Denetim olmadan, `null` `finally` blok kendi kendine oluşturabilir <xref:System.NullReferenceException> , ancak mümkünse özel durumların atma `finally` işlemi mümkünse kaçınılmalıdır.  
  
 Veritabanı bağlantısı, bir blokta kapanmakta olan başka bir adaydır `finally` . Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir. Bağlantınızı kapatabilmeniz için önce bir özel durum oluşursa, bu, `finally` bloğu kullanmanın çöp toplama beklerken daha iyi bir durumdur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel durumlar ve özel durum Işleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
