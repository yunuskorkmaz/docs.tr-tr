---
title: .NET Framework'te Konsol Uygulamaları Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c1658f27b66d9447d191d23801eba2d659ce9c2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933893"
---
# <a name="building-console-applications-in-the-net-framework"></a>.NET Framework'te Konsol Uygulamaları Oluşturma
.NET Framework uygulamalar, <xref:System.Console?displayProperty=nameWithType> sınıftan karakterleri okumak ve konsola karakter yazmak için sınıfını kullanabilir. Konsolda bulunan veriler standart giriş akışından, konsola ait veriler standart çıkış akışına yazılır ve konsola hata verileri standart hata çıktı akışına yazılır. Uygulama başlatıldığında ve sırasıyla <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, ve <xref:System.Console.Error%2A> özellikleri olarak sunulursa, bu akışlar konsol ile otomatik olarak ilişkilendirilir.  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> Özelliğin değeri bir <xref:System.IO.TextReader?displayProperty=nameWithType> nesnedir, <xref:System.Console.Out%2A?displayProperty=nameWithType> ancak ve <xref:System.Console.Error%2A?displayProperty=nameWithType> özelliklerinin değerleri nesneler olur <xref:System.IO.TextWriter?displayProperty=nameWithType> . Bu özellikleri, konsolunu temsil eden akışlarla ilişkilendirerek, akışı giriş veya çıkış için farklı bir konuma işaret etmeniz mümkün hale getirebilirsiniz. Örneğin, <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliğini, <xref:System.Console.SetOut%2A?displayProperty=nameWithType> yöntemini bir <xref:System.IO.FileStream?displayProperty=nameWithType> by yöntemi ile kapsülleyen bir olarak ayarlayarak, çıkışı bir <xref:System.IO.StreamWriter?displayProperty=nameWithType>dosyaya yönlendirebilirsiniz. <xref:System.Console.In%2A?displayProperty=nameWithType> Ve<xref:System.Console.Out%2A?displayProperty=nameWithType> özelliklerinin aynı akışa başvurması gerekmez.  
  
> [!NOTE]
> , Visual Basic ve C# C++içindeki örnekler de dahil olmak üzere konsol uygulamaları oluşturma hakkında daha fazla bilgi için, bkz. <xref:System.Console> sınıfının belgeleri.  
  
 Konsol yoksa, Windows tabanlı bir uygulamada olduğu gibi, bilgilerin yazılacağı bir konsol olmadığından, standart çıkış akışına yazılan çıkış görünmez. Erişilemeyen bir konsola bilgi yazmak bir özel durumun oluşturulmasına neden olmaz.  
  
 Alternatif olarak, konsolunu Visual Studio kullanılarak geliştirilen Windows tabanlı bir uygulama içinde okumak ve yazmak üzere etkinleştirmek için projenin **Özellikler** iletişim kutusunu açın, **uygulama** sekmesine tıklayın ve **uygulama türünü** ayarlayın **konsol uygulamasına**.  
  
 Konsol uygulamalarında varsayılan olarak başlayan bir ileti göndericisi yok. Bu nedenle, Microsoft Win32 zamanlayıcılara yönelik konsol çağrıları başarısız olabilir.  
  
 **System. Console** sınıfında, tek tek karakterleri veya tüm satırları konsoldan okuyabilen yöntemler vardır. Diğer yöntemler, verileri ve biçim dizelerini dönüştürür ve sonra biçimli dizeleri konsola yazar. Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz. [biçimlendirme türleri](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../docs/standard/base-types/formatting-types.md)
