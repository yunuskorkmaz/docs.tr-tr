---
title: ".NET Framework Uygulamalarını Genelleştirme ve Yerelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- international applications [.NET Framework]
- globalization [.NET Framework], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET Framework], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 63f0e001280773c55f18f0604ca93986acbb9674
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2018
---
# <a name="globalizing-and-localizing-net-framework-applications"></a>.NET Framework Uygulamalarını Genelleştirme ve Yerelleştirme
Geliştirme bir [dünya çapında kullanılmaya hazır uygulama](http://msdn.microsoft.com/goglobal/bb978433.aspx), bir veya daha fazla dillere yerelleştirilmiş bir uygulama da dahil olmak üzere, üç adımdan oluşur: yerelleştirilebilirlik gözden geçirin Genelleştirme ve Yerelleştirme.  
  
 [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)  
 Bu adım kültür ve dil açısından nötr olan ve tüm kullanıcılar için yerelleştirilmiş kullanıcı arabirimleri ve bölgesel verileri destekleyen bir uygulamanın tasarlanması ve kodlanmasını içerir. Tasarım yapma ve kültüre özgü varsayımlara dayalı olmayan kararları programlama ile ilgilidir. Global uygulamalar yerelleştirilmez, ancak daha sonra bir veya birden çok dile görece kolay yerelleştirilebilecek şekilde tasarlanır ve yazılırlar.  
  
 [Yerelleştirilebilirlik Gözden Geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md)  
 Bu adım, bir uygulamanın kod ve tasarımının, kolayca yerelleştirilebilir olmasını sağlamak ve yerelleştirme için olası engelleri tanımlamak üzere gözden geçirilmesi ve uygulamanın yürütülebilir kodunun kaynaklarından ayrı olduğunun doğrulanması ile ilgilidir. Genelleştirme aşaması etkili olduysa, yerelleştirme incelemesi, genelleştirme sırasında yapılan tasarım ve kodlama seçimlerini onaylar. Yerelleştirilebilirlik aşaması, bir uygulamanın kaynak kodunu yerelleştirme aşamasında değiştirmek zorunda kalmamanızı sağlayacak şekilde geri kalan sorunları tanımlayabilir.  
  
 [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md)  
 Bu adım özel kültürler veya bölgeler için bir uygulamanın özelleştirilmesini içerir. Genelleştirme ve yerelleştirme adımları doğru olarak gerçekleştirilmişse, yerelleştirme, öncelikli olarak kullanıcı arabirimini çevirmeyi içerir.  
  
 Aşağıdaki üç adımı izlemenin iki avantajı vardır:  
  
-   ABD gibi tek bir kültür desteklemek üzere tasarlanmış bir uygulama yükseltmek zorunda kalmaktan serbest bırakma İngilizce, ek kültürler desteklemek için kullanılır.  
  
-   Daha kararlı ve daha az hatası olan yerelleştirilmiş uygulamalar olarak sonuçlanır.  
  
 .NET Framework, dünya çapında kullanılmaya hazır ve yerelleştirilmiş uygulamalar geliştirme için kapsamlı destek sağlar. Özellikle, .NET Framework sınıf kitaplığındaki birçok üye türü, geçerli kullanıcının kültür veya belirli bir kültürü yansıtan değerlerini döndürerek genelleştirmeye yardım eder. Ayrıca, .NET Framework, bir uygulamayı yerelleştirme işlemini kolaylaştıran uydu derlemelerini destekler.  
  
 Ek bilgi için bkz: [Genelleştirme belgelerine](/globalization/).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Genelleştirme](../../../docs/standard/globalization-localization/globalization.md)  
 Nötr kültüre ve nötr dile sahip bir uygulama tasarlamayı ve kodlamayı da içeren, dünya çapında kullanılmaya hazır uygulama bir oluşturmanın ilk aşamasını açıklar.  
  
 [Yerelleştirilebilirlik Gözden Geçirmesi](../../../docs/standard/globalization-localization/localizability-review.md)  
 Yerelleştirmede potansiyel bariyerler tanımlamayı da içeren yerelleştirilmiş uygulama oluşturmanın ikinci aşamasını açıklar.  
  
 [Yerelleştirme](../../../docs/standard/globalization-localization/localization.md)  
 Özel bölgeler ve kültürler için bir uygulamanın kullanıcı arabirimini özelleştirmeyi içeren yerelleştirilmiş bir uygulama oluşturmanın son adımını açıklar.  
  
 [Kültüre Duyarsız Dize İşlemleri](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Kültür duyarlı olmayan sonuçlar elde etmek için varsayılan olarak kültüre duyarlı olan .NET Framework yöntemlerinin ve sınıflarının nasıl kullanılacağını açıklar.  
  
 [Dünya Çapında Kullanılmaya Hazır Uygulamalar Geliştirmek için En İyi Yöntemler](../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md)  
 Genelleştirme, yerelleştirme ve dünya çapında kullanılmaya hazır ASP.NET uygulamaları geliştirmek için izlenebilecek en iyi uygulamaları açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Globalization?displayProperty=nameWithType>ad alanı  
 Bu ad alanındaki, dil, ülke/bölge, kullanılan takvimler, tarihler için biçim desenleri, para birimi, sayılar ve dizeler için sıralama düzeni gibi kültürle ilişkili bilgileri tanımlayan sınıflar içerir  
  
 <xref:System.Resources>ad alanı  
 Kaynaklar oluşturmak, düzenlemek ve kullanmak için sınıflar sağlar.  
  
 <xref:System.Text>ad alanı  
 ASCII, ANSI, Unicode ve diğer karakter kodlamalarını temsil eden sınıfları içerir.  
  
 [Resgen.exe (Kaynak Dosya Oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)  
 .txt dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürmek için Resgen.exe öğesinin nasıl kullanılacağını açıklar.  
  
 [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)  
 Windows Forms formlarını yerelleştirmek için Winres.exe yürütme dosyasının nasıl kullanılacağını açıklar.
