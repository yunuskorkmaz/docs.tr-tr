---
title: Visual Basic'te My Ad Alanını Genişletme
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 6da0914c9d2d4dc1220ede5d6fa9f1aa6b43426a
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775294"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic `My` ad alanını genişletme

Visual Basic `My` ad alanı, .NET Framework gücünden kolayca yararlanmanızı sağlayan özellikler ve yöntemler sunar. @No__t_0 ad alanı yaygın programlama sorunlarını basitleştirir ve genellikle zor bir görevi tek bir kod satırına azaltır. Ayrıca, `My` ad alanı tamamen genişletilebilir ve bu sayede belirli uygulama gereksinimlerine uyum sağlamak için `My` davranışını özelleştirebilir ve hiyerarşisine yeni hizmetler ekleyebilmenizi sağlayabilirsiniz. Bu konu, `My` ad alanının mevcut üyelerini nasıl özelleştireceğinizi ve kendi özel sınıflarınızın `My` ad alanına nasıl ekleneceğini anlatmaktadır.

## <a name="customizing-existing-my-namespace-members"></a>Mevcut `My` ad alanı üyelerini özelleştirme

Visual Basic `My` ad alanı, uygulamanız, bilgisayarınız ve daha fazlası hakkında sık kullanılan bilgileri gösterir. @No__t_0 ad alanındaki nesnelerin tüm listesi için bkz. [başvurum](../../language-reference/keywords/my-reference.md). @No__t_0 ad alanının mevcut üyelerini, uygulamanızın ihtiyaçlarını daha iyi eşleşecek şekilde özelleştirmeniz gerekebilir. Salt okuma olmayan `My` ad alanındaki bir nesnenin herhangi bir özelliği, özel bir değere ayarlanabilir.

Örneğin, uygulamanızı çalıştıran kullanıcı için geçerli güvenlik bağlamına erişmek üzere `My.User` nesnesini sıklıkla kullandığınızı varsayalım. Ancak şirketiniz, Şirket içindeki kullanıcılar için ek bilgi ve yetenekler sunmak üzere özel bir kullanıcı nesnesi kullanır. Bu senaryoda, aşağıdaki örnekte gösterildiği gibi `My.User.CurrentPrincipal` özelliğinin varsayılan değerini kendi özel asıl nesnenizin bir örneğiyle değiştirebilirsiniz:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

@No__t_1 nesnesinde `CurrentPrincipal` özelliğinin ayarlanması, uygulamanın çalıştırıldığı kimliği değiştirir. @No__t_0 nesnesi, yeni belirtilen kullanıcı hakkında bilgiler döndürür.
  
## <a name="adding-members-to-my-objects"></a>@No__t_0 nesnelere üye ekleme

@No__t_0 ve `My.Computer` döndürülen türler `Partial` sınıfları olarak tanımlanmıştır. Bu nedenle, `MyApplication` veya `MyComputer` adlı bir `Partial` sınıfı oluşturarak `My.Application` ve `My.Computer` nesneleri genişletebilirsiniz. Sınıf bir `Private` sınıfı olamaz. Sınıfı `My` ad alanının parçası olarak belirtirseniz, `My.Application` veya `My.Computer` nesnelerine dahil edilecek özellikler ve yöntemler ekleyebilirsiniz.

Aşağıdaki örnek, `My.Computer` nesnesine `DnsServerIPAddresses` adlı bir özellik ekler:

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>@No__t_0 ad alanına özel nesneler ekleme

@No__t_0 ad alanı birçok ortak programlama görevi için çözümler sağlasa da, `My` ad alanının ele aldığı görevlerle karşılaşabilirsiniz. Örneğin, uygulamanız kullanıcı verileri için özel dizin hizmetlerine erişebilir veya uygulamanız Visual Basic varsayılan olarak yüklenmeyen derlemeleri kullanabilir. @No__t_0 ad alanını, ortamınıza özgü ortak görevlere özel çözümler içerecek şekilde genişletebilirsiniz. @No__t_0 ad alanı, büyüyen uygulama ihtiyaçlarını karşılamak için yeni üyeler eklemek üzere kolayca genişletilebilir. Ayrıca, `My` ad alanı uzantılarınızı diğer geliştiricilere Visual Basic şablonu olarak dağıtabilirsiniz.
  
### <a name="adding-members-to-the-my-namespace"></a>@No__t_0 ad alanına üye ekleme

@No__t_0 diğer ad alanı gibi bir ad alanı olduğundan, yalnızca bir modül ekleyerek ve `My` `Namespace` belirterek en üst düzey özellikler ekleyebilirsiniz. Aşağıdaki örnekte gösterildiği gibi `HideModuleName` özniteliğiyle modüle not ekleyin. @No__t_0 öznitelik, IntelliSense 'in, `My` ad alanının üyelerini görüntülediğinde modül adını görüntülememesini sağlar.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

@No__t_0 ad alanına üye eklemek için, gerekli özellikleri modüle ekleyin. @No__t_0 ad alanına eklenen her özellik için, türün özel özelliği tarafından döndürülen tür olduğu `ThreadSafeObjectProvider(Of T)` türünde bir özel alan ekleyin. Bu alan, `GetInstance` metodu çağırarak özelliği tarafından döndürülecek iş parçacığı güvenli nesne örnekleri oluşturmak için kullanılır. Sonuç olarak, genişletilmiş özelliğe erişen her iş parçacığı döndürülen türün kendi örneğini alır. Aşağıdaki örnek `My` ad alanına `SampleExtension` türündeki `SampleExtension` adlı bir özellik ekler:

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Özel `My` nesnelerine olaylar ekleme

@No__t_3 ad alanındaki `MyApplication` parçalı sınıfını genişleterek özel `My` nesnelerinizin olaylarını açığa çıkarmak için `My.Application` nesnesini kullanabilirsiniz. Windows tabanlı projelerde, **Çözüm Gezgini**' de projeniz Için **projem** düğümüne çift tıklayabilirsiniz. Visual Basic **projesi tasarımcısında** **uygulama** sekmesine tıklayın ve ardından **uygulama olaylarını görüntüle** düğmesine tıklayın. *ApplicationEvents. vb* adlı yeni bir dosya oluşturulacaktır. @No__t_0 sınıfını genişletmek için aşağıdaki kodu içerir:

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

@No__t_1 sınıfına özel olay işleyicileri ekleyerek, özel `My` nesneleriniz için olay işleyicileri ekleyebilirsiniz. Özel olaylar, bir olay işleyicisi eklendiğinde, kaldırıldığında veya olay oluşturulduğunda yürütülecek kodu eklemenize olanak sağlar. Özel bir olay için `AddHandler` kodunun yalnızca, olayı işlemek için bir kullanıcı tarafından kod eklenirse çalıştığını unutmayın. Örneğin, önceki bölümdeki `SampleExtension` nesnesinin için özel olay işleyicisi eklemek istediğiniz bir `Load` olayına sahip olduğunu düşünün. Aşağıdaki kod örneği, `My.SampleExtension.Load` olayı gerçekleştiğinde çağrılacak `SampleExtensionLoad` adlı özel bir olay işleyicisini gösterir. Yeni `My.SampleExtensionLoad` olayını işlemek için kod eklendiğinde, bu özel olay kodunun `AddHandler` kısmı yürütülür. @No__t_0 yöntemi, `My.SampleExtensionLoad` olayını işleyen bir olay işleyicisinin örneğini göstermek için kod örneğine dahil edilir. *ApplicationEvents. vb* dosyasını düzenlediğinizde, kod Düzenleyicisi 'nin üzerindeki sol aşağı açılan listede yer alan **uygulama olayları** seçeneğini belirlediğinizde `SampleExtensionLoad` olayın kullanılabilir olacağını unutmayın.

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Tasarım yönergeleri

@No__t_0 ad alanına uzantı geliştirirken, uzantı bileşenlerinizin Bakım maliyetlerini en aza indirmeye yardımcı olması için aşağıdaki yönergeleri kullanın:

- **Yalnızca uzantı mantığını dahil edin.** @No__t_0 ad alanı uzantısına dahil edilen mantık yalnızca `My` ad alanında gerekli işlevselliği göstermek için gereken kodu içermelidir. Uzantınızın, kaynak kodu olarak Kullanıcı projelerinde yer alacağı için, uzantı bileşeninin güncelleştirilmesi yüksek bir bakım maliyeti doğurur ve mümkünse bu kaçınılmalıdır.
- **Proje varsayımlarını en aza indirin.** @No__t_0 ad alanı uzantılarınızı oluşturduğunuzda, bir dizi başvuru, proje düzeyi içeri aktarma veya belirli derleyici ayarları (örneğin, `Option Strict` kapalı) kullanmayın. Bunun yerine, bağımlılıkları en aza indirin ve tüm tür başvurularını `Global` anahtar sözcüğünü kullanarak tam olarak nitelendirin. Ayrıca, uzantının, uzantıdaki hataları en aza indirmek için `Option Strict` ile derlendiğinden emin olun.
- **Uzantı kodunu yalıtın.** Kodun tek bir dosyaya yerleştirilmesi, uzantınızı Visual Studio öğe şablonu olarak kolayca dağıtılabilir hale getirir. Daha fazla bilgi için bu konunun devamındaki "uzantıları paketleme ve dağıtma" bölümüne bakın. Tüm `My` ad alanı uzantı kodunun tek bir dosyaya veya bir projedeki ayrı bir klasöre yerleştirilmesi, kullanıcıların `My` ad alanı uzantısını bulmalarına de yardımcı olur.

## <a name="designing-class-libraries-for-my"></a>@No__t_0 için sınıf kitaplıkları tasarlama

Çoğu nesne modelinde olduğu gibi, bazı tasarım desenleri `My` ad alanında iyi çalışır ve diğerleri değildir. @No__t_0 ad alanına uzantı tasarlarken aşağıdaki ilkeleri göz önünde bulundurun:

- **Durum bilgisi olmayan yöntemler.** @No__t_0 ad alanındaki Yöntemler, belirli bir göreve yönelik kapsamlı bir çözüm sağlamalıdır. Yöntemine geçirilen parametre değerlerinin, belirli görevi tamamlaması için gereken tüm girişleri sağlamasına emin olun. Kaynaklara yönelik açık bağlantılar gibi önceki duruma dayanan yöntemler oluşturmaktan kaçının.
- **Genel örnekler.** @No__t_0 ad alanında tutulan tek durum, proje için geneldir. Örneğin, `My.Application.Info` uygulama genelinde paylaşılan durumu kapsüller.
- **Basit parametre türleri.** Karmaşık parametre türlerini önleyerek şeyleri basit tutun. Bunun yerine, hiçbir parametre girişi olmayan veya dizeler, ilkel türler gibi basit giriş türleri alan yöntemler oluşturun.
- **Fabrika yöntemleri.** Bazı türlerin örneklendirilecek kadar zor olması gerekebilir. @No__t_0 ad alanına uzantı olarak fabrika yöntemlerinin sağlanması, bu kategoriye giren türleri daha kolay keşfetmenizi ve kullanmanızı sağlar. İyi çalışma `My.Computer.FileSystem.OpenTextFileReader` fabrika yöntemine bir örnek. .NET Framework çeşitli akış türleri mevcuttur. Metin dosyalarını özellikle belirterek, `OpenTextFileReader` kullanıcının hangi akışın kullanılacağını anlamasına yardımcı olur.

Bu yönergeler, sınıf kitaplıkları için genel tasarım ilkelerini ön olarak etkilemez. Bunun yerine, Visual Basic ve `My` ad alanını kullanan geliştiriciler için en iyi duruma getirilmiş önerilerdir. Sınıf kitaplıkları oluşturmaya yönelik genel tasarım ilkeleri için bkz. [Framework tasarım yönergeleri](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Uzantıları paketleme ve dağıtma

@No__t_0 ad alanı uzantılarını bir Visual Studio proje şablonuna dahil edebilir veya uzantılarınızı paketleyebilir ve bunları Visual Studio öğe şablonu olarak dağıtabilirsiniz. @No__t_0 ad alanı uzantılarınızı Visual Studio öğe şablonu olarak paketleyerek, Visual Basic tarafından sunulan ek özelliklerden yararlanabilirsiniz. Bu yetenekler, bir proje belirli bir derlemeye başvurduğunda bir uzantı eklemenize olanak sağlar veya kullanıcıların `My` ad alanı uzantınızı Visual Basic proje Tasarımcısı ' nın **uzantılarım** sayfasını kullanarak açıkça eklemesini sağlar.

@No__t_0 ad alanı uzantılarının nasıl dağıtılacağı hakkında ayrıntılar için bkz. [özel uzantılarımı paketleme ve dağıtma](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [My Uzantılarını Paketleme ve Dağıtma](packaging-and-deploying-custom-my-extensions.md)
- [Visual Basic Uygulama Modelini Genişletme](extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../language-reference/modifiers/partial.md)
