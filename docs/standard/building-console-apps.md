---
title: .NET Framework'te Konsol Uygulamaları Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: 1ec65795a7f3d706b2878dd8a8397ae42b61ce7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132859"
---
# <a name="building-console-applications-in-the-net-framework"></a>.NET Framework'te Konsol Uygulamaları Oluşturma
.NET Framework uygulamalar, içindeki karakterleri okumak ve konsola karakter yazmak için <xref:System.Console?displayProperty=nameWithType> sınıfını kullanabilir. Konsolda bulunan veriler standart giriş akışından, konsola ait veriler standart çıkış akışına yazılır ve konsola hata verileri standart hata çıktı akışına yazılır. Uygulama başlatıldığında ve sırasıyla <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>ve <xref:System.Console.Error%2A> özellikleri olarak sunulursa, bu akışlar konsolla otomatik olarak ilişkilendirilir.  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> özelliğinin değeri bir <xref:System.IO.TextReader?displayProperty=nameWithType> nesnesidir, ancak <xref:System.Console.Out%2A?displayProperty=nameWithType> ve <xref:System.Console.Error%2A?displayProperty=nameWithType> özelliklerinin değerleri <xref:System.IO.TextWriter?displayProperty=nameWithType> nesnelerdir. Bu özellikleri, konsolunu temsil eden akışlarla ilişkilendirerek, akışı giriş veya çıkış için farklı bir konuma işaret etmeniz mümkün hale getirebilirsiniz. Örneğin, <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliğini <xref:System.Console.SetOut%2A?displayProperty=nameWithType> yöntemi aracılığıyla bir <xref:System.IO.FileStream?displayProperty=nameWithType> kapsülleyen bir <xref:System.IO.StreamWriter?displayProperty=nameWithType>ayarlayarak çıktıyı bir dosyaya yönlendirebilirsiniz. <xref:System.Console.In%2A?displayProperty=nameWithType> ve <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliklerinin aynı akışa başvurması gerekmez.  
  
> [!NOTE]
> , Visual Basic ve C# C++içindeki örnekler de dahil olmak üzere konsol uygulamaları oluşturma hakkında daha fazla bilgi için <xref:System.Console> sınıfına yönelik belgelere bakın.  
  
 Konsol yoksa, Windows tabanlı bir uygulamada olduğu gibi, bilgilerin yazılacağı bir konsol olmadığından, standart çıkış akışına yazılan çıkış görünmez. Erişilemeyen bir konsola bilgi yazmak bir özel durumun oluşturulmasına neden olmaz.  
  
 Alternatif olarak, konsolunu Visual Studio kullanılarak geliştirilen Windows tabanlı bir uygulama içinde okumak ve yazmak üzere etkinleştirmek için projenin **Özellikler** iletişim kutusunu açın, **uygulama** sekmesine tıklayın ve **uygulama türünü** ayarlayın **konsol uygulamasına**.  
  
 Konsol uygulamalarında varsayılan olarak başlayan bir ileti göndericisi yok. Bu nedenle, Microsoft Win32 zamanlayıcılara yönelik konsol çağrıları başarısız olabilir.  
  
 **System. Console** sınıfında, tek tek karakterleri veya tüm satırları konsoldan okuyabilen yöntemler vardır. Diğer yöntemler, verileri ve biçim dizelerini dönüştürür ve sonra biçimli dizeleri konsola yazar. Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../docs/standard/base-types/formatting-types.md)
