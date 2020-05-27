---
title: .NET uygulamalarını genelleştirmek ve yerelleştirme
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: c5c601d18d92d9b57781bc8a09f26f0bc3a9216a
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842016"
---
# <a name="globalizing-and-localizing-net-applications"></a>.NET uygulamalarını genelleştirmek ve yerelleştirme

Bir veya daha fazla dilde yerelleştirilebilecek bir uygulama da dahil olmak üzere dünya çapında kullanılabilir bir uygulama geliştirme, üç adımdan oluşur: Genelleştirme, Yerelleştirilebilirlik incelemesi ve yerelleştirme.

[Genelleştirme](globalization.md)

Bu adım kültür ve dil açısından nötr olan ve tüm kullanıcılar için yerelleştirilmiş kullanıcı arabirimleri ve bölgesel verileri destekleyen bir uygulamanın tasarlanması ve kodlanmasını içerir. Tasarım yapma ve kültüre özgü varsayımlara dayalı olmayan kararları programlama ile ilgilidir. Global uygulamalar yerelleştirilmez, ancak daha sonra bir veya birden çok dile görece kolay yerelleştirilebilecek şekilde tasarlanır ve yazılırlar.

[Yerelleştirilebilirlik incelemesi](localizability-review.md)

Bu adım, bir uygulamanın kod ve tasarımının, kolayca yerelleştirilebilir olmasını sağlamak ve yerelleştirme için olası engelleri tanımlamak üzere gözden geçirilmesi ve uygulamanın yürütülebilir kodunun kaynaklarından ayrı olduğunun doğrulanması ile ilgilidir. Genelleştirme aşaması etkili olduysa, yerelleştirme incelemesi, genelleştirme sırasında yapılan tasarım ve kodlama seçimlerini onaylar. Yerelleştirilebilirlik aşaması, bir uygulamanın kaynak kodunu yerelleştirme aşamasında değiştirmek zorunda kalmamanızı sağlayacak şekilde geri kalan sorunları tanımlayabilir.

[Localization (Yerelleştirme)](localization.md)

Bu adım özel kültürler veya bölgeler için bir uygulamanın özelleştirilmesini içerir. Genelleştirme ve yerelleştirme adımları doğru olarak gerçekleştirilmişse, yerelleştirme, öncelikli olarak kullanıcı arabirimini çevirmeyi içerir.

Aşağıdaki üç adımı izlemenin iki avantajı vardır:

- ABD İngilizcesi gibi tek bir kültürü desteklemek için tasarlanmış bir uygulamayı ek kültürleri desteklemek üzere yükseltmek zorunda kalmanızı önler.

- Daha kararlı ve daha az hatası olan yerelleştirilmiş uygulamalar olarak sonuçlanır.

.NET, dünya çapında ve yerelleştirilmiş uygulamaların geliştirilmesi için kapsamlı destek sağlar. Özellikle, .NET sınıf kitaplığındaki birçok üye türü, geçerli kullanıcının kültürünün veya belirtilen kültürün kurallarını yansıtan değerler döndürerek Genelleştirme 'ye yardımcı olur. Ayrıca, .NET, bir uygulamayı yerelleştirme işlemini kolaylaştıran uydu derlemelerini destekler.

Daha fazla bilgi için bkz. [Genelleştirme belgeleri](/globalization/).

## <a name="in-this-section"></a>Bu bölümde

[Genelleştirme](globalization.md)

Nötr kültüre ve nötr dile sahip bir uygulama tasarlamayı ve kodlamayı da içeren, dünya çapında kullanılmaya hazır uygulama bir oluşturmanın ilk aşamasını açıklar.

[.NET Genelleştirme ve ıCU](globalization-icu.md)

.NET Genelleştirme 'nin [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)nasıl kullandığını açıklar.

[Yerelleştirilebilirlik incelemesi](localizability-review.md)

Yerelleştirmede potansiyel bariyerler tanımlamayı da içeren yerelleştirilmiş uygulama oluşturmanın ikinci aşamasını açıklar.

[Localization (Yerelleştirme)](localization.md)

Özel bölgeler ve kültürler için bir uygulamanın kullanıcı arabirimini özelleştirmeyi içeren yerelleştirilmiş bir uygulama oluşturmanın son adımını açıklar.

[Kültüre duyarsız dize işlemleri](culture-insensitive-string-operations.md)

Kültüre duyarsız sonuçlar elde etmek için varsayılan olarak kültüre duyarlı olan .NET yöntemlerinin ve sınıflarının nasıl kullanılacağını açıklar.

[Dünya çapında kullanmaya yönelik uygulamalar geliştirmek için en iyi uygulamalar](best-practices-for-developing-world-ready-apps.md)

Genelleştirme, yerelleştirme ve dünya çapında kullanılmaya hazır ASP.NET uygulamaları geliştirmek için izlenebilecek en iyi uygulamaları açıklar.

## <a name="reference"></a>Başvuru

- <xref:System.Globalization?displayProperty=nameWithType>uzayına

   Bu ad alanındaki, dil, ülke/bölge, kullanılan takvimler, tarihler için biçim desenleri, para birimi, sayılar ve dizeler için sıralama düzeni gibi kültürle ilişkili bilgileri tanımlayan sınıflar içerir

- <xref:System.Resources>uzayına

   Kaynaklar oluşturmak, düzenlemek ve kullanmak için sınıflar sağlar.

- <xref:System.Text>uzayına

   ASCII, ANSI, Unicode ve diğer karakter kodlamalarını temsil eden sınıfları içerir.

- [Resgen. exe (kaynak dosya Oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   .txt dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürmek için Resgen.exe öğesinin nasıl kullanılacağını açıklar.

- [Winres. exe (Windows Forms Kaynak Düzenleyicisi)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   Windows Forms formlarını yerelleştirmek için Winres.exe yürütme dosyasının nasıl kullanılacağını açıklar.
