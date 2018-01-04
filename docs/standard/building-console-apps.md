---
title: ".NET Framework'te Konsol Uygulamaları Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8bcfa7d8a55cd2754965430db7ea6d2351892658
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="building-console-applications-in-the-net-framework"></a>.NET Framework'te Konsol Uygulamaları Derleme
.NET Framework uygulamalarında kullanma <xref:System.Console?displayProperty=nameWithType> karakterlerinden okumak ve konsola karakterleri yazmak için sınıf. Konsolundan veri standart giriş akışından okuma, verileri konsola standart çıktı akışına yazılır ve hata verileri konsola standart hata çıktı akışına yazılır. Konsol ile uygulama başlar ve bu olarak sunulduğunda bu akışları otomatik olarak ilişkilendirilir <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, ve <xref:System.Console.Error%2A> özellikleri, sırasıyla.  
  
 Değeri <xref:System.Console.In%2A?displayProperty=nameWithType> özelliği bir <xref:System.IO.TextReader?displayProperty=nameWithType> , ancak nesne değerlerini <xref:System.Console.Out%2A?displayProperty=nameWithType> ve <xref:System.Console.Error%2A?displayProperty=nameWithType> özellikleri <xref:System.IO.TextWriter?displayProperty=nameWithType> nesneleri. Bu özellikleri akış girişi veya çıkışı için farklı bir konum işaret edecek şekilde edinerek konsol temsil etmeyen akışları ile ilişkilendirebilirsiniz. Bir dosyaya ayarlayarak çıkışı örneğin yönlendirebilirsiniz <xref:System.Console.Out%2A?displayProperty=nameWithType> özelliğine bir <xref:System.IO.StreamWriter?displayProperty=nameWithType>, hangi yalıtan bir <xref:System.IO.FileStream?displayProperty=nameWithType> yoluyla <xref:System.Console.SetOut%2A?displayProperty=nameWithType> yöntemi. <xref:System.Console.In%2A?displayProperty=nameWithType> Ve <xref:System.Console.Out%2A?displayProperty=nameWithType> özellikleri aynı akışa başvurmak gerek yoktur.  
  
> [!NOTE]
>  Örnekler C#, Visual Basic ve C++ da dahil olmak üzere, konsol uygulamaları oluşturma hakkında daha fazla bilgi için belgelere bakın <xref:System.Console> sınıfı.  
  
 Konsol yoksa Windows tabanlı bir uygulama olduğu gibi bilgileri yazma konsola olduğundan standart çıkış akışına yazılan çıktı görünür olmaz. Bilgi erişilemeyen bir konsola yazma oluşturulması için bir özel duruma neden olmaz.  
  
 Alternatif olarak, okuma ve Visual Studio kullanılarak geliştirilen Windows tabanlı bir uygulama içinde yazma Konsolu etkinleştirmek için projenin açın **özellikleri** iletişim kutusu, tıklatın **uygulama** sekme ve ayarlayın **uygulama türü** için **konsol uygulaması**.  
  
 Konsol uygulamaları varsayılan olarak başlatılır bir ileti Pompalama yoksundur. Bu nedenle, Microsoft Win32 zamanlayıcılar konsol çağrılar başarısız olabilir.  
  
 **System.Console** sınıfı karakterleri tek tek veya tüm satırları konsoldan okuyabilir yöntemleri vardır. Diğer yöntemleri veri ve biçim dizelerini dönüştürmek ve ardından biçimlendirilmiş dizeler konsola yazma. Biçimlendirme dizeleri hakkında daha fazla bilgi için bkz: [biçimlendirme türleri](../../docs/standard/base-types/formatting-types.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Console?displayProperty=nameWithType>  
 [Biçimlendirme Türleri](../../docs/standard/base-types/formatting-types.md)
