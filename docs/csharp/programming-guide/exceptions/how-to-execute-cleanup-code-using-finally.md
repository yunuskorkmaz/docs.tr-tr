---
title: Son C# programlama kılavuzunu kullanarak Temizleme kodunu yürütme
ms.date: 07/20/2015
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: d1ba761e64053d656ad4cd004133fc455a57c6f6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705281"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Son kullanılan temizleme kodunu yürütme (C# Programlama Kılavuzu)
Bir `finally` ifadesinin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır. Bu tür bir temizlik örneği, nesnenin ortak dil çalışma zamanı tarafından atık olarak toplanmasını beklemek yerine, bir <xref:System.IO.FileStream> hemen sonrasında <xref:System.IO.Stream.Close%2A>, aşağıdaki gibi çağırıyor:  
  
 [!code-csharp[csProgGuideExceptions#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#16)]  
  
## <a name="example"></a>Örnek  
 Önceki kodu bir `try-catch-finally` ifadesine dönüştürmek için, temizleme kodu aşağıdaki gibi çalışma kodundan ayrılır.  
  
 [!code-csharp[csProgGuideExceptions#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#17)]  
  
 `OpenWrite()` çağrısından önce `try` bloğunda herhangi bir zamanda bir özel durum gerçekleşebildiğinden veya `OpenWrite()` çağrısı başarısız olursa, kapatmayı denediğinde dosyanın açık olduğu garanti edilmez. `finally` bloğu, <xref:System.IO.Stream.Close%2A> yöntemini çağırmadan önce <xref:System.IO.FileStream> nesnesinin `null` olmadığından emin olmak için bir denetim ekler. `null` denetimi olmadan `finally` bloğu kendi <xref:System.NullReferenceException>oluşturabilir, ancak mümkünse `finally` bloklardaki özel durumların oluşturulması kaçınılmalıdır.  
  
 Veritabanı bağlantısı, `finally` bloğunda kapanmakta olan başka bir adaydır. Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir. Bağlantınızı kapatabilmeniz için önce bir özel durum oluşturulursa, bu, `finally` bloğunun kullanımı çöp toplama işleminin daha iyi olduğu bir durumdur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel Durum İşleme](./exception-handling.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
