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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132859"
---
# <a name="building-console-applications-in-the-net-framework"></a>.NET Framework'te Konsol Uygulamaları Oluşturma
.NET Framework'deki uygulamalar, <xref:System.Console?displayProperty=nameWithType> konsoldaki karakterleri okumak ve karakterleri yazmak için sınıfı kullanabilir. Konsoldan gelen veriler standart giriş akışından okunur, konsola veri standart çıkış akışına yazılır ve konsoldaki hata verileri standart hata çıktı akışına yazılır. Bu akışlar, uygulama başladığında konsolla otomatik olarak ilişkilendirilir <xref:System.Console.In%2A> <xref:System.Console.Out%2A>ve <xref:System.Console.Error%2A> sırasıyla , ve özellikler olarak sunulur.  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> <xref:System.IO.TextReader?displayProperty=nameWithType> Özelliğin değeri bir nesnedir, oysa ve <xref:System.Console.Out%2A?displayProperty=nameWithType> <xref:System.Console.Error%2A?displayProperty=nameWithType> özelliklerin <xref:System.IO.TextWriter?displayProperty=nameWithType> değerleri nesnelerdir. Bu özellikleri konsolu temsil etmeyen akışlarla ilişkilendirerek akışı giriş veya çıktı için farklı bir konuma getirmenizi sağlayabilirsiniz. Örneğin, <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliği yöntem yoluyla bir <xref:System.IO.StreamWriter?displayProperty=nameWithType> <xref:System.IO.FileStream?displayProperty=nameWithType> kapsülleyen bir dosyaya ayarlayarak çıktıyı bir dosyaya <xref:System.Console.SetOut%2A?displayProperty=nameWithType> yönlendirebilirsiniz. <xref:System.Console.In%2A?displayProperty=nameWithType> Ve <xref:System.Console.Out%2A?displayProperty=nameWithType> özellikleri aynı akış akışın başvurması gerekmez.  
  
> [!NOTE]
> C#, Visual Basic ve C++'daki örnekler de dahil olmak üzere konsol uygulamaları <xref:System.Console> oluşturma hakkında daha fazla bilgi için sınıf için belgelere bakın.  
  
 Konsol yoksa, Windows tabanlı bir uygulamada olduğu gibi, bilgileri yazacak konsol olmadığından, standart çıktı akışına yazılan çıktı görünmez. Erişilemeyen bir konsola bilgi yazmak bir özel durum olarak yükseltilmesine neden olmaz.  
  
 Alternatif olarak, Visual Studio kullanılarak geliştirilen Windows tabanlı bir uygulama içinde okuma ve yazma konsolu etkinleştirmek için, projenin **Özellikleri** iletişim kutusunu açın, **Uygulama** sekmesini tıklatın ve **Uygulama türünü** **Konsol Uygulaması'na**ayarlayın.  
  
 Konsol uygulamaları varsayılan olarak başlayan bir ileti pompası yoksun. Bu nedenle, Microsoft Win32 zamanlayıcılarına konsol çağrıları başarısız olabilir.  
  
 **System.Console** sınıfı, konsoldaki karakterleri veya satırların tamamını tek tek okuyabilen yöntemlere sahiptir. Diğer yöntemler veri ve biçim dizeleri dönüştürmek ve sonra konsola biçimlendirilmiş dizeleri yazın. Dizeleri biçimlendirme hakkında daha fazla bilgi için [biçimlendirme Türleri'ne](../../docs/standard/base-types/formatting-types.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console?displayProperty=nameWithType>
- [Biçimlendirme Türleri](../../docs/standard/base-types/formatting-types.md)
