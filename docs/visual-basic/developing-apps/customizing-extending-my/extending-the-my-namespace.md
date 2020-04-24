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
ms.openlocfilehash: 2a7b0b84061fccd9a333a68e4a19477bd19ca4ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330311"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic `My` ad alanını genişletme

Visual Basic `My` ad alanı, .NET Framework gücünden kolayca yararlanmanıza olanak sağlayan özellikler ve yöntemler sunar. `My` Ad alanı yaygın programlama sorunlarını basitleştirir ve genellikle zor bir görevi tek bir kod satırına azaltır. Ayrıca, bir `My` `My` ad alanı tamamen genişletilebilir ve bu sayede, belirli uygulama gereksinimlerine uyum sağlamak için, ve hiyerarşisine yeni hizmetler ekleyebilmenizi sağlayabilirsiniz. Bu konu, `My` ad alanının var olan üyelerini nasıl özelleştireceğinizi ve kendi özel sınıflarınızın `My` ad alanına nasıl ekleneceğini anlatmaktadır.

## <a name="customizing-existing-my-namespace-members"></a>Mevcut `My` ad alanı üyelerini özelleştirme

Visual Basic `My` ad alanı, uygulamanız, bilgisayarınız ve daha fazlası hakkında sık kullanılan bilgileri gösterir. `My` Ad alanındaki nesnelerin tüm listesi için bkz. [başvurum](../../language-reference/keywords/my-reference.md). Uygulamanızın ihtiyaçlarını daha iyi eşleşecek şekilde, `My` ad alanının mevcut üyelerini özelleştirmeniz gerekebilir. Salt okuma olmayan `My` ad alanındaki bir nesnenin herhangi bir özelliği, özel bir değere ayarlanabilir.

Örneğin, uygulamanızı çalıştıran kullanıcı için geçerli güvenlik bağlamına `My.User` erişmek üzere nesnesini sıklıkla kullandığınızı varsayalım. Ancak şirketiniz, Şirket içindeki kullanıcılar için ek bilgi ve yetenekler sunmak üzere özel bir kullanıcı nesnesi kullanır. Bu senaryoda, aşağıdaki örnekte gösterildiği gibi, `My.User.CurrentPrincipal` özelliğinin varsayılan değerini kendi özel asıl nesnenizin bir örneğiyle değiştirebilirsiniz:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

`My.User` Nesnedeki `CurrentPrincipal` özelliği ayarlamak, uygulamanın çalıştırıldığı kimliği değiştirir. `My.User` Nesne, sırasıyla, yeni belirtilen kullanıcı hakkında bilgiler döndürür.
  
## <a name="adding-members-to-my-objects"></a>`My` Nesnelere üye ekleme

Ve ' `My.Application` `My.Computer` den döndürülen türler sınıflar olarak `Partial` tanımlanır. Bu nedenle, `My.Application` veya `My.Computer` `Partial` `MyApplication` `MyComputer`adlı bir sınıf oluşturarak ve nesnelerini genişletebilirsiniz. Sınıf bir `Private` sınıf olamaz. Sınıfını `My` ad alanının parçası olarak belirtirseniz, `My.Application` veya `My.Computer` nesnelerine dahil edilecek özellikler ve yöntemler ekleyebilirsiniz.

Aşağıdaki örnek, `DnsServerIPAddresses` `My.Computer` nesnesine adlı bir özellik ekler:

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>`My` Ad alanına özel nesneler ekleme

`My` Ad alanı birçok ortak programlama görevi için çözümler sağlasa da, `My` ad alanının ele aldığı görevlerle karşılaşabilirsiniz. Örneğin, uygulamanız kullanıcı verileri için özel dizin hizmetlerine erişebilir veya uygulamanız Visual Basic varsayılan olarak yüklenmeyen derlemeleri kullanabilir. Çalışma `My` alanını ortamınıza özgü ortak görevlere özel çözümler içerecek şekilde genişletebilirsiniz. Ad `My` alanı, büyüyen uygulama ihtiyaçlarını karşılamak için yeni üyeler eklemek üzere kolayca genişletilebilir. Ayrıca, ad alanı uzantılarınızı `My` diğer geliştiricilere Visual Basic şablonu olarak dağıtabilirsiniz.
  
### <a name="adding-members-to-the-my-namespace"></a>`My` Ad alanına üye ekleme

`My` Diğer ad alanı gibi bir ad alanı olduğu için, yalnızca bir modül ekleyerek ve ' ı belirterek `Namespace` en üst düzey özellikler ekleyebilirsiniz `My`. Aşağıdaki örnekte gösterildiği gibi, `HideModuleName` bu özniteliğe modüle not ekleyin. `HideModuleName` Özniteliği, `My` ad alanının üyelerini görüntülediğinde IntelliSense 'in modül adını görüntülememesini sağlar.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

`My` Ad alanına üye eklemek için modüle gereken özellikleri ekleyin. `My` Ad alanına eklenen her bir özellik için türünde `ThreadSafeObjectProvider(Of T)`bir özel alan ekleyin, burada türün özel özelliği tarafından döndürülen türdür. Bu alan, `GetInstance` yöntemi çağırarak özelliği tarafından döndürülecek iş parçacığı güvenli nesne örnekleri oluşturmak için kullanılır. Sonuç olarak, genişletilmiş özelliğe erişen her iş parçacığı döndürülen türün kendi örneğini alır. Aşağıdaki örnek, `SampleExtension` `SampleExtension` `My` ad alanına türünde olan adlı bir özelliği ekler:

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Özel `My` nesnelere olaylar ekleme

Ad alanındaki `MyApplication` kısmi sınıfı `My.Application` genişleterek özel `My` nesnelerinizin olaylarını göstermek için nesnesini kullanabilirsiniz. `My` Windows tabanlı projelerde, **Çözüm Gezgini**' de projeniz Için **projem** düğümüne çift tıklayabilirsiniz. Visual Basic **projesi tasarımcısında** **uygulama** sekmesine tıklayın ve ardından **uygulama olaylarını görüntüle** düğmesine tıklayın. *ApplicationEvents. vb* adlı yeni bir dosya oluşturulacaktır. `MyApplication` Sınıfı genişletmek için aşağıdaki kodu içerir:

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Sınıfına özel olay işleyicileri ekleyerek özel `My` nesneleriniz için olay işleyicileri ekleyebilirsiniz. `MyApplication` Özel olaylar, bir olay işleyicisi eklendiğinde, kaldırıldığında veya olay oluşturulduğunda yürütülecek kodu eklemenize olanak sağlar. Özel bir olay `AddHandler` için kodun yalnızca olay işlemek için bir kullanıcı tarafından bir kod eklendiyse çalıştığını unutmayın. Örneğin, önceki bölümdeki `SampleExtension` nesnenin için özel olay işleyicisi eklemek istediğiniz bir `Load` olay olduğunu düşünün. Aşağıdaki kod örneğinde, `SampleExtensionLoad` `My.SampleExtension.Load` olay gerçekleştiğinde çağrılacak adlı özel bir olay işleyicisi gösterilmektedir. Yeni `My.SampleExtensionLoad` olayı işlemek için kod eklendiğinde, bu özel olay kodunun `AddHandler` bölümü yürütülür. `MyApplication_SampleExtensionLoad` Yöntemi, `My.SampleExtensionLoad` olayı işleyen bir olay işleyicisinin örneğini göstermek için kod örneğine dahil edilir. `SampleExtensionLoad` *ApplicationEvents. vb* dosyasını düzenlediğinizde, kod düzenleyicisinin üzerindeki sol aşağı açılan listede yer alan **uygulama olayları** seçeneğini belirlediğinizde olayın kullanılabilir olacağını unutmayın.

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Tasarım yönergeleri

`My` Ad alanına uzantı geliştirirken, uzantı bileşenlerinizin Bakım maliyetlerini en aza indirmeye yardımcı olması için aşağıdaki yönergeleri kullanın:

- **Yalnızca uzantı mantığını dahil edin.** `My` Ad alanı uzantısına dahil edilen mantık yalnızca `My` ad alanında gerekli işlevselliği göstermek için gereken kodu içermelidir. Uzantınızın, kaynak kodu olarak Kullanıcı projelerinde yer alacağı için, uzantı bileşeninin güncelleştirilmesi yüksek bir bakım maliyeti doğurur ve mümkünse bu kaçınılmalıdır.
- **Proje varsayımlarını en aza indirin.** `My` Ad alanı uzantılarınızı oluşturduğunuzda, bir dizi başvuru, proje düzeyi içeri aktarma veya belirli derleyici ayarları (örneğin, `Option Strict` kapalı) olarak kabul edilmez. Bunun yerine, bağımlılıkları en aza indirin ve `Global` anahtar sözcüğünü kullanarak tüm tür başvurularını tam olarak nitelendirin. Ayrıca, uzantının, uzantıdaki hataları en aza `Option Strict` indirmek için üzerinde ile derlendiğinden emin olun.
- **Uzantı kodunu yalıtın.** Kodun tek bir dosyaya yerleştirilmesi, uzantınızı Visual Studio öğe şablonu olarak kolayca dağıtılabilir hale getirir. Daha fazla bilgi için bu konunun devamındaki "uzantıları paketleme ve dağıtma" bölümüne bakın. Tüm `My` ad alanı uzantı kodunun tek bir dosyaya veya bir projedeki ayrı bir klasöre yerleştirilmesi, kullanıcıların `My` ad alanı uzantısını bulmalarına de yardımcı olur.

## <a name="designing-class-libraries-for-my"></a>İçin sınıf kitaplıkları tasarlama`My`

Çoğu nesne modelinde olduğu gibi, bazı tasarım desenleri `My` ad alanında iyi çalışır ve diğerleri değildir. `My` Ad alanına uzantı tasarlarken aşağıdaki ilkeleri göz önünde bulundurun:

- **Durum bilgisi olmayan yöntemler.** Ad alanındaki Yöntemler `My` , belirli bir göreve yönelik kapsamlı bir çözüm sağlamalıdır. Yöntemine geçirilen parametre değerlerinin, belirli görevi tamamlaması için gereken tüm girişleri sağlamasına emin olun. Kaynaklara yönelik açık bağlantılar gibi önceki duruma dayanan yöntemler oluşturmaktan kaçının.
- **Genel örnekler.** `My` Ad alanında tutulan tek durum, proje için geneldir. Örneğin, `My.Application.Info` uygulama genelinde paylaşılan durumu kapsüller.
- **Basit parametre türleri.** Karmaşık parametre türlerini önleyerek şeyleri basit tutun. Bunun yerine, hiçbir parametre girişi olmayan veya dizeler, ilkel türler gibi basit giriş türleri alan yöntemler oluşturun.
- **Fabrika yöntemleri.** Bazı türlerin örneklendirilecek kadar zor olması gerekebilir. Ad alanına uzantı olarak fabrika yöntemlerinin sağlanması `My` , bu kategoriye giren türleri daha kolay keşfetmenizi ve kullanmanızı sağlar. İyi bir şekilde çalışacak fabrika yöntemine bir örnektir `My.Computer.FileSystem.OpenTextFileReader`. .NET Framework çeşitli akış türleri mevcuttur. Metin dosyalarını özellikle belirterek, kullanıcının hangi `OpenTextFileReader` akışın kullanılacağını anlamasına yardımcı olur.

Bu yönergeler, sınıf kitaplıkları için genel tasarım ilkelerini ön olarak etkilemez. Bunun yerine, Visual Basic ve `My` ad alanını kullanan geliştiriciler için en iyi duruma getirilmiş önerilerdir. Sınıf kitaplıkları oluşturmaya yönelik genel tasarım ilkeleri için bkz. [Framework tasarım yönergeleri](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Uzantıları paketleme ve dağıtma

Ad alanı uzantılarını `My` bir Visual Studio proje şablonuna dahil edebilir veya uzantılarınızı paketleyebilir ve bunları Visual Studio öğe şablonu olarak dağıtabilirsiniz. Ad alanı uzantılarınızı `My` Visual Studio öğe şablonu olarak paketleyerek, Visual Basic tarafından sunulan ek özelliklerden yararlanabilirsiniz. Bu yetenekler, bir proje belirli bir derlemeye başvurduğunda bir uzantı eklemenize olanak sağlar veya Visual Basic proje Tasarımcısı ' nın **My uzantıları** sayfasını `My` kullanarak, kullanıcıların ad alanı uzantınızı açıkça eklemesini sağlar.

Ad alanı uzantılarının nasıl dağıtılacağı `My` hakkında daha fazla bilgi için bkz. [özel uzantılarımı paketleme ve dağıtma](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [My Extensions'ı Paketleme ve Dağıtma](packaging-and-deploying-custom-my-extensions.md)
- [Visual Basic Uygulama Modelini Genişletme](extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Kısmi](../../language-reference/modifiers/partial.md)
