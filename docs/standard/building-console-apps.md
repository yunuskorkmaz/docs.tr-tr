---
title: .NET 'te konsol uygulamaları oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, creating console applications
- application development [.NET], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: b9c38e1311379037695879565b33ade29c6bf632
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687554"
---
# <a name="console-apps-in-net"></a>.NET 'teki konsol uygulamaları

.NET uygulamaları, <xref:System.Console?displayProperty=nameWithType> sınıftan karakter okumak ve konsola karakter yazmak için sınıfını kullanabilir. Konsolda bulunan veriler standart giriş akışından, konsola ait veriler standart çıkış akışına yazılır ve konsola hata verileri standart hata çıktı akışına yazılır. Uygulama başlatıldığında ve <xref:System.Console.In%2A> sırasıyla,, ve özellikleri olarak sunulursa, bu akışlar konsol ile otomatik olarak ilişkilendirilir <xref:System.Console.Out%2A> <xref:System.Console.Error%2A> .

<xref:System.Console.In%2A?displayProperty=nameWithType>Özelliğin değeri bir <xref:System.IO.TextReader?displayProperty=nameWithType> nesnedir, ancak <xref:System.Console.Out%2A?displayProperty=nameWithType> ve <xref:System.Console.Error%2A?displayProperty=nameWithType> özelliklerinin değerleri <xref:System.IO.TextWriter?displayProperty=nameWithType> nesneler olur. Bu özellikleri, konsolunu temsil eden akışlarla ilişkilendirerek, akışı giriş veya çıkış için farklı bir konuma işaret etmeniz mümkün hale getirebilirsiniz. Örneğin, <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliğini, <xref:System.IO.StreamWriter?displayProperty=nameWithType> yöntemini bir <xref:System.IO.FileStream?displayProperty=nameWithType> by yöntemi ile kapsülleyen bir olarak ayarlayarak, çıkışı bir dosyaya yönlendirebilirsiniz <xref:System.Console.SetOut%2A?displayProperty=nameWithType> . <xref:System.Console.In%2A?displayProperty=nameWithType>Ve <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliklerinin aynı akışa başvurması gerekmez.

> [!NOTE]
> C#, Visual Basic ve C++ örnekleri de dahil olmak üzere konsol uygulamaları oluşturma hakkında daha fazla bilgi için, bkz <xref:System.Console> . sınıf belgeleri.

Konsol yoksa, örneğin, Windows Forms bir uygulamada, bilgilerin yazılacağı bir konsol olmadığından, standart çıkış akışına yazılan çıkış görünür olmayacaktır. Erişilemeyen bir konsola bilgi yazmak bir özel durumun oluşturulmasına neden olmaz. (Örneğin, Visual Studio 'Nun proje özelliği sayfalarında) uygulama türünü **konsol uygulaması** olarak değiştirebilirsiniz.

**System. Console** sınıfında, tek tek karakterleri veya tüm satırları konsoldan okuyabilen yöntemler vardır. Diğer yöntemler, verileri ve biçim dizelerini dönüştürür ve sonra biçimli dizeleri konsola yazar. Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](base-types/formatting-types.md).

> [!TIP]
> Konsol uygulamalarında varsayılan olarak başlayan bir ileti göndericisi yok. Bu nedenle, Microsoft Win32 zamanlayıcılara yönelik konsol çağrıları başarısız olabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console?displayProperty=nameWithType>
- [Biçimlendirme Türleri](base-types/formatting-types.md)
