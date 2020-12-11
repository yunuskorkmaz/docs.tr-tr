---
title: Finally-C# programlama kılavuzunu kullanarak Temizleme kodunu yürütme
description: "' Finally ' ifadesini kullanarak Temizleme kodunu yürütmeyi öğrenin. Finally deyimleri, tüm gerekli nesne temizleme işleminin hemen gerçekleşmesini güvence altına aldığından emin olur."
ms.date: 12/09/2020
helpviewer_keywords:
- try/finally blocks [C#]
- exceptions [C#], try/finally block
- exception handling [C#], try/finally block
ms.assetid: 1b1e5aef-3f32-4a88-9d39-b5fffb33bdaf
ms.openlocfilehash: e9b5d3086488d3f7e3c0709317d6fafd15c439e8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110188"
---
# <a name="how-to-execute-cleanup-code-using-finally-c-programming-guide"></a>Finally kullanarak temizleme kodu yürütme (C# Programlama Kılavuzu)

Bir `finally` deyimin amacı, genellikle özel bir durum oluşsa bile, genellikle dış kaynakları tutan nesneler olan nesnelerin gerekli temizleme işleminin hemen gerçekleşmemesini sağlamaktır. Bu tür temizliğin bir örneği, <xref:System.IO.Stream.Close%2A> <xref:System.IO.FileStream> nesnenin ortak dil çalışma zamanı tarafından çöp toplanmasını beklemek yerine, aşağıdaki gibi, hemen sonrasında çağrılır:

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="NoCleanup":::

## <a name="example"></a>Örnek

Önceki kodu bir ifadeye dönüştürmek için `try-catch-finally` , temizleme kodu, çalışma kodundan aşağıdaki gibi ayrılır.

:::code language="csharp" source="snippets/exceptions/Program.cs" ID="WithCleanup":::

Bir özel durum, çağrıdan önce blok içinde herhangi bir zamanda olabileceği `try` `OpenWrite()` veya `OpenWrite()` çağrının kendisi başarısız olabileceği için, kapatmayı denediğinde dosyanın açık olduğunu garanti etmedik. `finally`Blok, <xref:System.IO.FileStream> `null` yöntemi çağırmadan önce nesnenin olmadığından emin olmak için bir denetim ekler <xref:System.IO.Stream.Close%2A> . Denetim olmadan, `null` `finally` blok kendi kendine fırlatabilir <xref:System.NullReferenceException> , ancak mümkünse özel durumların atma `finally` yapılabilmelidir.

Veritabanı bağlantısı, bir blokta kapanmakta olan başka bir adaydır `finally` . Bir veritabanı sunucusuyla izin verilen bağlantı sayısı bazen sınırlı olduğundan, veritabanı bağlantılarını mümkün olduğunca hızlı bir şekilde kapatmanız gerekir. Bağlantınızı kapatabilmeniz için önce bir özel durum oluşturulursa, `finally` blok kullanmak çöp toplama için beklerken daha iyidir.

## <a name="see-also"></a>Ayrıca bkz.

- [using Deyimi](../../language-reference/keywords/using-statement.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
