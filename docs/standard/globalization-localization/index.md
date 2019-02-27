---
title: .NET uygulamaları Genelleştirme ve yerelleştirme
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
  - 'international applications [.NET]'
  - 'globalization [.NET], encoding'
  - global applications
  - internationalization
  - world-ready applications
  - 'application development [.NET], globalization'
  - multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
author: rpetrusha
ms.author: ronpet
---
# <a name="globalizing-and-localizing-net-applications"></a>.NET uygulamaları Genelleştirme ve yerelleştirme

Bir veya daha fazla dile yerelleştirilebilen bir uygulama da dahil olmak üzere bir dünya çapında kullanılmaya hazır uygulama geliştirmek, üç adımdan oluşur: genelleştirme, yerelleştirme gözden geçirme ve Yerelleştirme.

[Genelleştirme](globalization.md)

Bu adım kültür ve dil açısından nötr olan ve tüm kullanıcılar için yerelleştirilmiş kullanıcı arabirimleri ve bölgesel verileri destekleyen bir uygulamanın tasarlanması ve kodlanmasını içerir. Tasarım yapma ve kültüre özgü varsayımlara dayalı olmayan kararları programlama ile ilgilidir. Global uygulamalar yerelleştirilmez, ancak daha sonra bir veya birden çok dile görece kolay yerelleştirilebilecek şekilde tasarlanır ve yazılırlar.

[Yerelleştirilebilirlik gözden geçirmesi](localizability-review.md)

Bu adım, bir uygulamanın kod ve tasarımının, kolayca yerelleştirilebilir olmasını sağlamak ve yerelleştirme için olası engelleri tanımlamak üzere gözden geçirilmesi ve uygulamanın yürütülebilir kodunun kaynaklarından ayrı olduğunun doğrulanması ile ilgilidir. Genelleştirme aşaması etkili olduysa, yerelleştirme incelemesi, genelleştirme sırasında yapılan tasarım ve kodlama seçimlerini onaylar. Yerelleştirilebilirlik aşaması, bir uygulamanın kaynak kodunu yerelleştirme aşamasında değiştirmek zorunda kalmamanızı sağlayacak şekilde geri kalan sorunları tanımlayabilir.

[Yerelleştirme](localization.md)

Bu adım özel kültürler veya bölgeler için bir uygulamanın özelleştirilmesini içerir. Genelleştirme ve yerelleştirme adımları doğru olarak gerçekleştirilmişse, yerelleştirme, öncelikli olarak kullanıcı arabirimini çevirmeyi içerir.

Aşağıdaki üç adımı izlemenin iki avantajı vardır:

-   Bu, ABD gibi tek bir kültürü desteklemek için tasarlanan bir uygulama yükseltmek zorunda kalmanızı İngilizce, ek kültürleri desteklemek üzere kullanılır.

-   Daha kararlı ve daha az hatası olan yerelleştirilmiş uygulamalar olarak sonuçlanır.

.NET, dünya çapında kullanılmaya hazır ve yerelleştirilmiş uygulamalar geliştirme için kapsamlı destek sağlar. Özellikle, birçok üyeleri .NET sınıf kitaplığı genelleştirmeye yardım eder geçerli kullanıcının kültür veya belirtilen bir kültürün kurallarını yansıtan değerlerini döndürerek yazın. Ayrıca, .NET, bir uygulamayı yerelleştirme işlemini kolaylaştıran uydu derlemelerini destekler.

Ek bilgi için bkz: [Genelleştirme belgeleri](/globalization/).

## <a name="in-this-section"></a>Bu bölümde

[Genelleştirme](globalization.md)

Nötr kültüre ve nötr dile sahip bir uygulama tasarlamayı ve kodlamayı da içeren, dünya çapında kullanılmaya hazır uygulama bir oluşturmanın ilk aşamasını açıklar.

[Yerelleştirilebilirlik gözden geçirmesi](localizability-review.md)

Yerelleştirmede potansiyel bariyerler tanımlamayı da içeren yerelleştirilmiş uygulama oluşturmanın ikinci aşamasını açıklar.

[Yerelleştirme](localization.md)

Özel bölgeler ve kültürler için bir uygulamanın kullanıcı arabirimini özelleştirmeyi içeren yerelleştirilmiş bir uygulama oluşturmanın son adımını açıklar.

[Kültüre duyarsız dize işlemleri](culture-insensitive-string-operations.md)

.NET yöntemleri ve kültüre duyarlı sınıfları kullanmayı açıklar varsayılan olarak kültüre duyarlı olmayan sonuçlar elde edilir.

[Dünya çapında kullanılmaya hazır uygulamalar geliştirmek için en iyi yöntemler](best-practices-for-developing-world-ready-apps.md)

Genelleştirme, yerelleştirme ve dünya çapında kullanılmaya hazır ASP.NET uygulamaları geliştirmek için izlenebilecek en iyi uygulamaları açıklar.

## <a name="reference"></a>Başvuru

- <xref:System.Globalization?displayProperty=nameWithType> Namespace

   Bu ad alanındaki, dil, ülke/bölge, kullanılan takvimler, tarihler için biçim desenleri, para birimi, sayılar ve dizeler için sıralama düzeni gibi kültürle ilişkili bilgileri tanımlayan sınıflar içerir

- <xref:System.Resources> Namespace

   Kaynaklar oluşturmak, düzenlemek ve kullanmak için sınıflar sağlar.

- <xref:System.Text> Namespace

   ASCII, ANSI, Unicode ve diğer karakter kodlamalarını temsil eden sınıfları içerir.

- [Resgen.exe (Kaynak Dosya Oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)

   .txt dosyalarını ve XML tabanlı kaynak biçimi (.resx) dosyalarını ortak dil çalışma zamanı ikili .resources dosyalarına dönüştürmek için Resgen.exe öğesinin nasıl kullanılacağını açıklar.

- [Winres.exe (Windows Forms Kaynak Düzenleyici)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md)

   Windows Forms formlarını yerelleştirmek için Winres.exe yürütme dosyasının nasıl kullanılacağını açıklar.
