---
title: .NET Framework'te Konsol Uygulamaları Derleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 979989c3e1f90f3de47473aa1bd8bc5268520e57
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45647320"
---
# <a name="building-console-applications-in-the-net-framework"></a>.NET Framework'te Konsol Uygulamaları Derleme
.NET Framework uygulamalarında kullanabileceğiniz <xref:System.Console?displayProperty=nameWithType> karakterleri okumak ve konsola karakterleri yazmak için sınıf. Standart giriş akışından veri konsoldan okunan, konsola veriler standart çıkış akışına yazılır ve hata verileri konsola standart hata çıktı akışına yazılır. Uygulama başladığında ve bu olarak sunulduğunda bu akışları konsoluyla otomatik olarak ilişkili <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, ve <xref:System.Console.Error%2A> özellikleri, sırasıyla.  
  
 Değerini <xref:System.Console.In%2A?displayProperty=nameWithType> özelliği bir <xref:System.IO.TextReader?displayProperty=nameWithType> ise, nesne değerlerini <xref:System.Console.Out%2A?displayProperty=nameWithType> ve <xref:System.Console.Error%2A?displayProperty=nameWithType> özellikleri <xref:System.IO.TextWriter?displayProperty=nameWithType> nesneleri. Stream giriş veya çıkış için farklı bir konuma işaret edecek şekilde edinerek bu özellikleri konsol temsil etmeyen akışları ile ilişkilendirebilirsiniz. Bir dosyaya ayarlayarak çıkışı örneğin yönlendirebilirsiniz <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliğini bir <xref:System.IO.StreamWriter?displayProperty=nameWithType>, hangi kapsülleyen bir <xref:System.IO.FileStream?displayProperty=nameWithType> yoluyla <xref:System.Console.SetOut%2A?displayProperty=nameWithType> yöntemi. <xref:System.Console.In%2A?displayProperty=nameWithType> Ve <xref:System.Console.Out%2A?displayProperty=nameWithType> özellikleri aynı akışa başvurmak gerekli değildir.  
  
> [!NOTE]
>  Örnekler C#, Visual Basic ve C++ ' dahil olmak üzere, konsol uygulamaları oluşturma hakkında daha fazla bilgi için belgelere bakın <xref:System.Console> sınıfı.  
  
 Konsol yoksa Windows tabanlı bir uygulama olduğu gibi bilgileri yazma konsola olduğundan standart çıkış akışına yazılan çıktı görünür olmayacaktır. Erişilemez bir konsola bilgilerini yazma oluşturulması için bir özel durum neden olmaz.  
  
 Alternatif olarak, Visual Studio kullanarak geliştirilen Windows tabanlı bir uygulama içinde yazma ve okuma için konsol etkinleştirmek için projenin açın **özellikleri** iletişim kutusu, tıklayın **uygulama** sekme ve ayarlama **uygulama türü** için **konsol uygulaması**.  
  
 Konsol uygulamaları, varsayılan olarak başlayan bir ileti pompası yoksundur. Bu nedenle, Microsoft Win32 zamanlayıcılar konsol çağrıları başarısız olabilir.  
  
 **System.Console** sınıf, karakterlerin tek tek veya tüm satırları konsoldan okuyabilir yöntemleri vardır. Diğer yöntemler veri ve biçim dizeleri dönüştürmek ve ardından konsola biçimlendirilmiş dizeler yazar. Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Console?displayProperty=nameWithType>  
- [Biçimlendirme Türleri](../../docs/standard/base-types/formatting-types.md)
