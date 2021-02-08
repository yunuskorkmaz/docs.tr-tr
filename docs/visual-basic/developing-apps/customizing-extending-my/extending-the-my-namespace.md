---
description: 'Hakkında daha fazla bilgi edinin: `My` Visual Basic ad alanını genişletme'
title: Visual Basic'te My Ad Alanını Genişletme
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 896e85da14e6e8a417c93560b1d3b78a5954b769
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797971"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>`My`Visual Basic ad alanını genişletme

`My`Visual Basic ad alanı, .NET Framework gücünden kolayca yararlanmanıza olanak sağlayan özellikler ve yöntemler sunar. `My`Ad alanı yaygın programlama sorunlarını basitleştirir ve genellikle zor bir görevi tek bir kod satırına azaltır. Ayrıca, `My` bir ad alanı tamamen genişletilebilir ve bu sayede, `My` belirli uygulama gereksinimlerine uyum sağlamak için, ve hiyerarşisine yeni hizmetler ekleyebilmenizi sağlayabilirsiniz. Bu konu, ad alanının var olan üyelerini nasıl özelleştireceğinizi `My` ve kendi özel sınıflarınızın ad alanına nasıl ekleneceğini anlatmaktadır `My` .

## <a name="customizing-existing-my-namespace-members"></a>Mevcut `My` ad alanı üyelerini özelleştirme

`My`Visual Basic ad alanı, uygulamanız, bilgisayarınız ve daha fazlası hakkında sık kullanılan bilgileri gösterir. Ad alanındaki nesnelerin tüm listesi için `My` bkz. [başvurum](../../language-reference/keywords/my-reference.md). `My`Uygulamanızın ihtiyaçlarını daha iyi eşleşecek şekilde, ad alanının mevcut üyelerini özelleştirmeniz gerekebilir. Salt okuma olmayan ad alanındaki bir nesnenin herhangi bir özelliği, `My` özel bir değere ayarlanabilir.

Örneğin, `My.User` uygulamanızı çalıştıran kullanıcı için geçerli güvenlik bağlamına erişmek üzere nesnesini sıklıkla kullandığınızı varsayalım. Ancak şirketiniz, Şirket içindeki kullanıcılar için ek bilgi ve yetenekler sunmak üzere özel bir kullanıcı nesnesi kullanır. Bu senaryoda, `My.User.CurrentPrincipal` Aşağıdaki örnekte gösterildiği gibi, özelliğinin varsayılan değerini kendi özel asıl nesnenizin bir örneğiyle değiştirebilirsiniz:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

`CurrentPrincipal`Nesnedeki özelliği ayarlamak, `My.User` uygulamanın çalıştırıldığı kimliği değiştirir. `My.User`Nesne, sırasıyla, yeni belirtilen kullanıcı hakkında bilgiler döndürür.
  
## <a name="adding-members-to-my-objects"></a>Nesnelere üye ekleme `My`

Ve ' den döndürülen `My.Application` türler `My.Computer` sınıflar olarak tanımlanır `Partial` . Bu nedenle, `My.Application` `My.Computer` veya adlı bir sınıf oluşturarak ve nesnelerini genişletebilirsiniz `Partial` `MyApplication` `MyComputer` . Sınıf bir `Private` sınıf olamaz. Sınıfını ad alanının parçası olarak belirtirseniz `My` , veya nesnelerine dahil edilecek özellikler ve yöntemler ekleyebilirsiniz `My.Application` `My.Computer` .

Aşağıdaki örnek, nesnesine adlı bir özellik ekler `DnsServerIPAddresses` `My.Computer` :

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Ad alanına özel nesneler ekleme `My`

`My`Ad alanı birçok ortak programlama görevi için çözümler sağlasa da, ad alanının ele aldığı görevlerle karşılaşabilirsiniz `My` . Örneğin, uygulamanız kullanıcı verileri için özel dizin hizmetlerine erişebilir veya uygulamanız Visual Basic varsayılan olarak yüklenmeyen derlemeleri kullanabilir. Çalışma `My` alanını ortamınıza özgü ortak görevlere özel çözümler içerecek şekilde genişletebilirsiniz. `My`Ad alanı, büyüyen uygulama ihtiyaçlarını karşılamak için yeni üyeler eklemek üzere kolayca genişletilebilir. Ayrıca, `My` ad alanı uzantılarınızı diğer geliştiricilere Visual Basic şablonu olarak dağıtabilirsiniz.
  
### <a name="adding-members-to-the-my-namespace"></a>Ad alanına üye ekleme `My`

`My`Diğer ad alanı gibi bir ad alanı olduğu için, yalnızca bir modül ekleyerek ve ' ı belirterek en üst düzey özellikler ekleyebilirsiniz `Namespace` `My` . `HideModuleName`Aşağıdaki örnekte gösterildiği gibi, bu özniteliğe modüle not ekleyin. `HideModuleName`Özniteliği, ad alanının üyelerini görüntülediğinde IntelliSense 'in modül adını görüntülememesini sağlar `My` .

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Ad alanına üye eklemek için `My` modüle gereken özellikleri ekleyin. Ad alanına eklenen her bir özellik için `My` türünde bir özel alan ekleyin, `ThreadSafeObjectProvider(Of T)` burada türün özel özelliği tarafından döndürülen türdür. Bu alan, yöntemi çağırarak özelliği tarafından döndürülecek iş parçacığı güvenli nesne örnekleri oluşturmak için kullanılır `GetInstance` . Sonuç olarak, genişletilmiş özelliğe erişen her iş parçacığı döndürülen türün kendi örneğini alır. Aşağıdaki örnek, `SampleExtension` ad alanına türünde olan adlı bir özelliği ekler `SampleExtension` `My` :

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Özel nesnelere olaylar ekleme `My`

`My.Application` `My` `MyApplication` Ad alanındaki kısmi sınıfı genişleterek özel nesnelerinizin olaylarını göstermek için nesnesini kullanabilirsiniz `My` . Windows tabanlı projelerde, **Çözüm Gezgini**' de projeniz Için **projem** düğümüne çift tıklayabilirsiniz. Visual Basic **projesi tasarımcısında** **uygulama** sekmesine tıklayın ve ardından **uygulama olaylarını görüntüle** düğmesine tıklayın. *ApplicationEvents. vb* adlı yeni bir dosya oluşturulacaktır. Sınıfı genişletmek için aşağıdaki kodu içerir `MyApplication` :

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

`My`Sınıfına özel olay işleyicileri ekleyerek özel nesneleriniz için olay işleyicileri ekleyebilirsiniz `MyApplication` . Özel olaylar, bir olay işleyicisi eklendiğinde, kaldırıldığında veya olay oluşturulduğunda yürütülecek kodu eklemenize olanak sağlar. `AddHandler`Özel bir olay için kodun yalnızca olay işlemek için bir kullanıcı tarafından bir kod eklendiyse çalıştığını unutmayın. Örneğin, `SampleExtension` önceki bölümdeki nesnenin `Load` için özel olay işleyicisi eklemek istediğiniz bir olay olduğunu düşünün. Aşağıdaki kod örneğinde, `SampleExtensionLoad` olay gerçekleştiğinde çağrılacak adlı özel bir olay işleyicisi gösterilmektedir `My.SampleExtension.Load` . Yeni olayı işlemek için kod eklendiğinde `My.SampleExtensionLoad` , `AddHandler` Bu özel olay kodunun bölümü yürütülür. `MyApplication_SampleExtensionLoad`Yöntemi, olayı işleyen bir olay işleyicisinin örneğini göstermek için kod örneğine dahil edilir `My.SampleExtensionLoad` . `SampleExtensionLoad` *ApplicationEvents. vb* dosyasını düzenlediğinizde, kod düzenleyicisinin üzerindeki sol aşağı açılan listede yer alan **uygulama olayları** seçeneğini belirlediğinizde olayın kullanılabilir olacağını unutmayın.

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Tasarım yönergeleri

`My`Ad alanına uzantı geliştirirken, uzantı bileşenlerinizin Bakım maliyetlerini en aza indirmeye yardımcı olması için aşağıdaki yönergeleri kullanın:

- **Yalnızca uzantı mantığını dahil edin.** `My`Ad alanı uzantısına dahil edilen mantık yalnızca ad alanında gerekli işlevselliği göstermek için gereken kodu içermelidir `My` . Uzantınızın, kaynak kodu olarak Kullanıcı projelerinde yer alacağı için, uzantı bileşeninin güncelleştirilmesi yüksek bir bakım maliyeti doğurur ve mümkünse bu kaçınılmalıdır.
- **Proje varsayımlarını en aza indirin.** Ad alanı uzantılarınızı oluşturduğunuzda `My` , bir dizi başvuru, proje düzeyi içeri aktarma veya belirli derleyici ayarları (örneğin, kapalı) olarak kabul edilmez `Option Strict` . Bunun yerine, bağımlılıkları en aza indirin ve anahtar sözcüğünü kullanarak tüm tür başvurularını tam olarak nitelendirin `Global` . Ayrıca, uzantının, `Option Strict` uzantıdaki hataları en aza indirmek için üzerinde ile derlendiğinden emin olun.
- **Uzantı kodunu yalıtın.** Kodun tek bir dosyaya yerleştirilmesi, uzantınızı Visual Studio öğe şablonu olarak kolayca dağıtılabilir hale getirir. Daha fazla bilgi için bu konunun devamındaki "uzantıları paketleme ve dağıtma" bölümüne bakın. Tüm `My` ad alanı uzantı kodunun tek bir dosyaya veya bir projedeki ayrı bir klasöre yerleştirilmesi, kullanıcıların `My` ad alanı uzantısını bulmalarına de yardımcı olur.

## <a name="designing-class-libraries-for-my"></a>İçin sınıf kitaplıkları tasarlama `My`

Çoğu nesne modelinde olduğu gibi, bazı tasarım desenleri `My` ad alanında iyi çalışır ve diğerleri değildir. `My`Ad alanına uzantı tasarlarken aşağıdaki ilkeleri göz önünde bulundurun:

- **Durum bilgisi olmayan yöntemler.** `My`Ad alanındaki Yöntemler, belirli bir göreve yönelik kapsamlı bir çözüm sağlamalıdır. Yöntemine geçirilen parametre değerlerinin, belirli görevi tamamlaması için gereken tüm girişleri sağlamasına emin olun. Kaynaklara yönelik açık bağlantılar gibi önceki duruma dayanan yöntemler oluşturmaktan kaçının.
- **Genel örnekler.** Ad alanında tutulan tek durum, `My` proje için geneldir. Örneğin, `My.Application.Info` uygulama genelinde paylaşılan durumu kapsüller.
- **Basit parametre türleri.** Karmaşık parametre türlerini önleyerek şeyleri basit tutun. Bunun yerine, hiçbir parametre girişi olmayan veya dizeler, ilkel türler gibi basit giriş türleri alan yöntemler oluşturun.
- **Fabrika yöntemleri.** Bazı türlerin örneklendirilecek kadar zor olması gerekebilir. Ad alanına uzantı olarak fabrika yöntemlerinin sağlanması, `My` Bu kategoriye giren türleri daha kolay keşfetmenizi ve kullanmanızı sağlar. İyi bir şekilde çalışacak fabrika yöntemine bir örnektir `My.Computer.FileSystem.OpenTextFileReader` . .NET Framework çeşitli akış türleri mevcuttur. Metin dosyalarını özellikle belirterek, `OpenTextFileReader` kullanıcının hangi akışın kullanılacağını anlamasına yardımcı olur.

Bu yönergeler, sınıf kitaplıkları için genel tasarım ilkelerini ön olarak etkilemez. Bunun yerine, Visual Basic ve ad alanını kullanan geliştiriciler için en iyi duruma getirilmiş önerilerdir `My` . Sınıf kitaplıkları oluşturmaya yönelik genel tasarım ilkeleri için bkz. [Framework tasarım yönergeleri](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Uzantıları paketleme ve dağıtma

`My`Ad alanı uzantılarını bir Visual Studio proje şablonuna dahil edebilir veya uzantılarınızı paketleyebilir ve bunları Visual Studio öğe şablonu olarak dağıtabilirsiniz. `My`Ad alanı uzantılarınızı Visual Studio öğe şablonu olarak paketleyerek, Visual Basic tarafından sunulan ek özelliklerden yararlanabilirsiniz. Bu yetenekler, bir proje belirli bir derlemeye başvurduğunda bir uzantı eklemenize olanak sağlar veya `My` Visual Basic proje Tasarımcısı ' nın **My uzantıları** sayfasını kullanarak, kullanıcıların ad alanı uzantınızı açıkça eklemesini sağlar.

Ad alanı uzantılarının nasıl dağıtılacağı hakkında daha fazla bilgi için `My` bkz. [özel uzantılarımı paketleme ve dağıtma](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [My Uzantılarını Paketleme ve Dağıtma](packaging-and-deploying-custom-my-extensions.md)
- [Visual Basic Uygulama Modelini Genişletme](extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Kısmi](../../language-reference/modifiers/partial.md)
