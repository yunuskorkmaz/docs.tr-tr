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
ms.openlocfilehash: 22d9d0def302b870de6f3e5ca4c142758b21314c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591839"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic'te My Ad Alanını Genişletme
`My` Visual Basic'de ad alanı özellikleri ve .NET Framework'ün güç kolayca yararlanmak sağlayan yöntemler sunar. `My` Ad alanı tek satırlık bir kod için genellikle zor bir görev azaltma genel programlama sorunlarını basitleştirir. Ayrıca, `My` davranışını özelleştirebilirsiniz böylece ad alanı tam olarak Genişletilebilir `My` ve belirli bir uygulama gereksinimlerine uyarlamak için hiyerarşi için yeni hizmetler ekleyin. Bu konuda her ikisi de ele alınmıştır varolan üyeleri özelleştirmek nasıl `My` ad alanı ve kendi özel sınıfları ekleme `My` ad alanı.  
  
 **Konu içerikleri**  
  
-   [My Namespace üyelerini varolan özelleştirme](#customizing)  
  
-   [My nesneleri üye ekleme](#addingtoobjects)  
  
-   [Özel nesne eklemeyi My Namespace](#addingcustom)  
  
-   [Üye ekleme My Namespace](#addingtonamespace)  
  
-   [My nesneleri özel olaylar ekleme](#addingevents)  
  
-   [Tasarım yönergeleri](#design)  
  
-   [Sınıf kitaplıkları için tasarlama My](#designing)  
  
-   [Paketleme ve uzantıları dağıtma](#packaging)  
  
##  <a name="customizing"></a> My Namespace üyelerini varolan özelleştirme  
 `My` Sık kullanılan uygulamanız, bilgisayarınızı ve daha fazlasını hakkında bilgi ad alanında Visual Basic açığa çıkarır. İçindeki nesneler tam bir listesi için `My` ad alanı, bkz: [My başvuru](../../../visual-basic/language-reference/keywords/my-reference.md). Var olan üyelerine özelleştirmeniz gerekebilir `My` ad alanı bunlar daha iyi, uygulamanızın gereksinimlerine uyan. Bir nesnenin herhangi bir özelliği `My` salt okunur olmayan ad alanı, özel bir değere ayarlanabilir.  
  
 Örneğin, sık kullandığınız varsayılmıştır `My.User` uygulamanızı çalıştıran kullanıcının geçerli güvenlik bağlamı erişmek için nesne. Ancak, şirket ek bilgi ve şirket içindeki kullanıcıları için özellikleri kullanıma sunmak için bir özel kullanıcı nesnesi kullanır. Bu senaryoda, varsayılan değerini değiştirebilir `My.User.CurrentPrincipal` aşağıdaki örnekte gösterildiği gibi kendi özel asıl nesne örneği özelliğiyle.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 Ayarı `CurrentPrincipal` özellikte `My.User` nesne değişiklikleri uygulamanın altında çalışacağı kimliği. `My.User` Nesnesi, buna karşılık, yeni belirtilen kullanıcı hakkındaki bilgileri döndürür.  
  
##  <a name="addingtoobjects"></a> My nesneleri üye ekleme  
 Döndürülen türleri `My.Application` ve `My.Computer` olarak tanımlanan `Partial` sınıfları. Bu nedenle, genişletebilirsiniz `My.Application` ve `My.Computer` oluşturarak nesneleri bir `Partial` adlı sınıf `MyApplication` veya `MyComputer`. Sınıf olamaz bir `Private` sınıfı. Sınıfının bir parçası olarak belirtirseniz, `My` ad alanı, özellikleri ve yöntemleri ile eklenecek ekleyebilirsiniz `My.Application` veya `My.Computer` nesneleri.  
  
 Örneğin, aşağıdaki örnekte adlı bir özellik ekler `DnsServerIPAddresses` için `My.Computer` nesnesi.  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> Özel nesne eklemeyi My Namespace  
 Ancak `My` ad alanı, çok sayıda genel programlama görevleri için çözümleri sağlar, görevleri karşılaşabilirsiniz, `My` ad alanı adresi değil. Örneğin, uygulamanız için kullanıcı verilerini özel dizin hizmetleri erişebilir ya da uygulamanızı Visual Basic ile varsayılan olarak yüklenmez derlemeleri kullanabilir. Genişletebilirsiniz `My` ortamınıza özgü ortak görevler için özel çözümler içerecek şekilde ad alanı. `My` Ad alanı kolayca uzatabilirsiniz büyüyen uygulama gereksinimlerini karşılamak için yeni üye eklemek için. Ayrıca, dağıtma, `My` diğer geliştiriciler Visual Basic şablon olarak ad alanı uzantıları.  
  
###  <a name="addingtonamespace"></a> Üye ekleme My Namespace  
 Çünkü `My` bir ad alanı diğer ad gibi üst düzey özellikleri için yalnızca bir modül ekleme ve belirterek ekleyebileceğiniz bir `Namespace` , `My`. Modülüyle açıklama `HideModuleName` özniteliği aşağıdaki örnekte gösterildiği gibi. `HideModuleName` Özniteliği sağlar üyelerini görüntülediğinde IntelliSense modül adı görüntülemez `My` ad alanı.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Üye eklemek için `My` ad alanı, modülü gerektiği gibi özellikler ekleyin. Eklenen her bir özellik için `My` ad alanı, türünde bir özel alan eklemek `ThreadSafeObjectProvider(Of T)`, burada türü özel özellik tarafından döndürülen tür. Bu alan çağırarak özelliği tarafından döndürülecek iş parçacığı açısından güvenli nesne örneklerini oluşturmak için kullanılan `GetInstance` yöntemi. Sonuç olarak, genişletilmiş özellik erişen her bir iş parçacığı döndürülen tür örneğini alır. Aşağıdaki örnek, adında bir özellik ekler `SampleExtension` türü olan `SampleExtension` için `My` ad alanı:  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> My nesneleri özel olaylar ekleme  
 Kullanabileceğiniz `My.Application` özel olaylar oluşturmak için nesne `My` genişletme nesneleri `MyApplication` kısmi sınıfında `My` ad alanı. Windows tabanlı projelerde çift tıklayarak **My proje** düğümünde projenizde için **Çözüm Gezgini**. Visual Basic'te **Proje Tasarımcısı**, tıklatın `Application` sekmesini ve ardından `View Application Events` düğmesi. ApplicationEvents.vb adlı yeni bir dosya oluşturulur. Genişletmek için aşağıdaki kodu içeren `MyApplication` sınıfı.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Olay işleyicileri için özel ekleyebilirsiniz `My` için özel olay işleyicileri ekleme nesneleri `MyApplication` sınıfı. Özel olaylar, olay işleyici eklenmiş, kaldırılmış veya olay tetiklenir yürütecek kodu eklemenize olanak tanır. Unutmayın `AddHandler` yalnızca kod olayını işlemek için bir kullanıcı tarafından eklenmişse özel bir olay çalıştırmaları için kod. Örneğin, göz önünde bulundurun `SampleExtension` önceki bölümdeki nesnesi bir `Load` özel bir olay işleyicisi için eklemek istediğiniz olay. Aşağıdaki kod örneğinde adlı özel bir olay işleyicisi gösterir `SampleExtensionLoad` , olacaktır olduğunda çağrılan `My.SampleExtension.Load` olayı oluşur. Yeni işlemek için kod eklendiğinde `My.SampleExtensionLoad` olayı `AddHandler` bu özel olay kod parçası gerçekleştirilir. `MyApplication_SampleExtensionLoad` Yöntemi işleyen olay işleyicisi örneği göstermek için aşağıdaki kod örneğinde dahil `My.SampleExtensionLoad` olay. Unutmayın `SampleExtensionLoad` olay kullanılabilir seçtiğinizde **My uygulama olayları** sol aşağı açılan listede Yukarıdaki kod ApplicationEvents.vb dosyayı düzenlerken Düzenleyicisi seçeneği.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> Tasarım yönergeleri  
 Uzantıları geliştirirken `My` ad alanı, uzantısı bileşenlerinizi bakım maliyetlerini en aza indirmek için aşağıdaki kılavuzları kullanın.  
  
-   **Yalnızca uzantı mantığı içerir.** Dahil mantığı `My` ad uzantısı, yalnızca gerekli işlevselliği kullanıma sunmak için gereken kodu içermelidir `My` ad alanı. Uzantınızı kullanıcı projelerde kaynak kodu olarak yer alacağı için uzantı bileşeni güncelleştirme yüksek bakım maliyet oluşturur ve mümkünse kaçınılmalıdır.  
  
-   **Proje varsayımlar en aza indirin.** Uzantılarınızın, oluşturduğunuzda `My` ad alanı, başvurular, proje düzeyi Imports ya da belirli derleyici ayarları varsayın değil (örneğin, `Option Strict` kapalı). Bunun yerine, bağımlılıkları en aza indirmek ve tüm tür başvuruları kullanarak tam olarak nitelemek `Global` anahtar sözcüğü. Ayrıca, uzantısı ile derlendiğinden emin olun `Option Strict` uzantısı'nda hataları en aza indirmek için üzerinde.  
  
-   **Uzantı kodu yalıtma.** Tek bir dosyada kodu yerleştirme uzantınızın Visual Studio öğe şablonu kolayca dağıtılabilir yapar. Daha fazla bilgi için "Paketleme ve dağıtma uzantılarını" bölümüne bakın. Tüm yerleştirme `My` ad alanı uzantı kodu tek bir dosyada veya bir proje ayrı bir klasörde ayrıca bulmalarına yardımcı olacak `My` ad alanı uzantı.  
  
##  <a name="designing"></a> Sınıf kitaplıkları için tasarlama My  
 Çoğu nesne modelleri ile olduğu gibi bazı tasarım desenleri iş iyi `My` ad alanı ve diğerleri yapın. Bir uzantısı tasarlarken `My` ad alanı, aşağıdaki ilkeleri göz önünde bulundurun:  
  
-   **Durum bilgisiz yöntemleri.** Yöntemleri `My` ad alanı, belirli bir görev için eksiksiz bir çözüm temin etmelidir. Yönteme geçirilen parametre değerlerini belirli bir görevi tamamlamak için gereken tüm giriş sağlamak emin olun. Kaynakları açık bağlantıları gibi önceki durumuna dayanan yöntemleri oluşturmamaya özen gösterin.  
  
-   **Genel örnekleri.** Tutulur yalnızca durum `My` projeye genel ad alanıdır. Örneğin, `My.Application.Info` uygulama genelinde paylaşılan durumu yalıtır.  
  
-   **Basit parametre türleri.** Karmaşık parametre türleri kaçınarak şeyler basit tutun. Bunun yerine, ya da giriş herhangi bir parametre alan yöntemleri oluşturun veya dizeler, ilkel türler vb. gibi basit giriş türleri alın.  
  
-   **Fabrika yöntemleri.** Bazı türleri örneği oluşturmak mutlaka zordur. Uzantıları olarak Fabrika yöntemleri sağlayan `My` ad alanı, daha kolay bulmak ve bu kategoriye türleri kullanmasına olanak tanır. İyi çalışan bir Üreteç yöntemi örneği `My.Computer.FileSystem.OpenTextFileReader`. .NET Framework birkaç akış türü vardır. Metin dosyaları özellikle belirterek `OpenTextFileReader` kullanmak için hangi akışın anlamasına yardımcı olur.  
  
 Bu yönergeleri sınıf kitaplıkları için genel tasarım ilkeleri engellemek değil. Bunun yerine, Visual Basic kullanan geliştiriciler için optimize önerileri oldukları ve `My` ad alanı. Genel tasarım ilkeleri sınıf kitaplıkları oluşturmak için bkz: [Framework tasarım yönergeleri](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a> Paketleme ve uzantıları dağıtma  
 Dahil edebileceğiniz `My` Visual Studio Proje şablonu veya ad alanı uzantıları uzantılarınızın paketini ve Visual Studio öğe şablon olarak dağıtın. Paketi, `My` ad alanı uzantılarını Visual Studio öğe şablon olarak Visual Basic tarafından sağlanan ek özelliklerinden alabilir. Bu özellikler, belirli bir derleme bir projeye başvuruda bulunan bir uzantısı dahil etkinleştirmek veya açık olarak eklenecek kullanıcıları etkinleştirmek, `My` kullanarak ad alanı uzantı **My Extensions** Visual Basic sayfası Proje Tasarımcısı.  
  
 Nasıl dağıtılacağı hakkında ayrıntılı bilgi için `My` ad alanı uzantılarını görmek [paketleme ve dağıtma özel My Extensions](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My Uzantılarını Paketleme ve Dağıtma](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)  
 [Visual Basic Uygulama Modelini Genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [My Extensions sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)  
 [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
