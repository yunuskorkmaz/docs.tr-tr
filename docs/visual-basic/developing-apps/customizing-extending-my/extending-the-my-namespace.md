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
ms.openlocfilehash: fafeb6cd47ebab5dd8f197b27d1aee9d7573e6ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717742"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic'te My Ad Alanını Genişletme
`My` Visual Basic'de ad alanı özellikleri ve kolayca .NET Framework'ün gücünden yararlanmak sağlayan yöntemler sunar. `My` Ad alanı genellikle zor bir görev için tek bir kod satırının azaltma ortak programlama sorunlarını basitleştirir. Ayrıca, `My` davranışını özelleştirebilmeniz için ad alanı tam olarak Genişletilebilir `My` ve belirli bir uygulama gereksinimlerine uyum sağlamak için hiyerarşi için yeni hizmet ekleyin. Her ikisi de bu konu açıklar nasıl özelleştirileceğini mevcut üyeleri `My` ad alanı ve kendi özel sınıflar için ekleme `My` ad alanı.  
  
 **Konu içerikleri**  
  
-   [My Namespace üyeleri varolan özelleştirme](#customizing)  
  
-   [My nesnelere üye ekleme](#addingtoobjects)  
  
-   [Özel nesne eklemeyi My Namespace](#addingcustom)  
  
-   [Üye ekleme My Namespace](#addingtonamespace)  
  
-   [Nesnelerim özel olaylar ekleme](#addingevents)  
  
-   [Tasarım yönergeleri](#design)  
  
-   [Sınıf kitaplıkları için tasarlama My](#designing)  
  
-   [Paketleme ve hata ayıklama uzantıları](#packaging)  
  
##  <a name="customizing"></a> My Namespace üyeleri varolan özelleştirme  
 `My` Ad alanında Visual Basic kullanıma sunan sık kullanılan uygulamanız, bilgisayarınız ve daha fazla bilgi. Nesnelerin tam listesi için `My` ad bkz [My başvuru](../../../visual-basic/language-reference/keywords/my-reference.md). Mevcut üyeleri özelleştirmeniz gerekebilir `My` ad alanı, daha iyi eşleşecek uygulamanızın ihtiyaçlarını. Bir nesnenin herhangi bir özelliği `My` salt okunur olmayan ad alanı, özel bir değere ayarlanabilir.  
  
 Örneğin, sık kullandığınız varsayılmıştır `My.User` uygulamanızı çalıştıran kullanıcının geçerli güvenlik bağlamına erişmek için nesne. Ancak şirketiniz özel kullanıcı nesnesindeki ek bilgi ve şirket içindeki kullanıcıları kapasitesini kullanıma sunmak için kullanır. Bu senaryoda, varsayılan değeri değiştirin `My.User.CurrentPrincipal` özelliğiyle aşağıdaki örnekte gösterildiği gibi kendi özel asıl nesne örneği.  
  
 [!code-vb[VbVbcnExtendingMy#1](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_1.vb)]  
  
 Ayarı `CurrentPrincipal` özelliği `My.User` nesne, uygulamanın çalıştığı kimliği değiştirir. `My.User` Nesne, sırayla yeni belirtilen kullanıcı ile ilgili bilgi döndürür.  
  
##  <a name="addingtoobjects"></a> My nesnelere üye ekleme  
 Öğesinden döndürülen türleri `My.Application` ve `My.Computer` olarak tanımlanan `Partial` sınıfları. Bu nedenle, genişletebileceğiniz `My.Application` ve `My.Computer` oluşturarak nesneleri bir `Partial` adlı sınıfı `MyApplication` veya `MyComputer`. Sınıf olamaz bir `Private` sınıfı. Sınıf kapsamında belirtirseniz `My` ad alanı, özellikleri ve yöntemleri ile dahil edilecek ekleyebilirsiniz `My.Application` veya `My.Computer` nesneleri.  
  
 Örneğin, aşağıdaki örnekte adlı bir özellik ekler `DnsServerIPAddresses` için `My.Computer` nesne.  
  
 [!code-vb[VbVbcnExtendingMy#2](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_2.vb)]  
  
##  <a name="addingcustom"></a> Özel nesne eklemeyi My Namespace  
 Ancak `My` ad alanı, birçok genel programlama görevleri için çözümler sağlar, görevleri karşılaşabilirsiniz, `My` ad alanı adresi değil. Örneğin, uygulamanızın kullanıcı verileri için özel dizin hizmetleri erişebilir veya Visual Basic ile varsayılan olarak yüklü olmayan bütünleştirilmiş kodları uygulamanızın kullanabilir. Genişletebileceğiniz `My` ortamınıza özgü ortak görevler için özel çözümler dahil etmek için ad alanı. `My` Ad alanı kolayca uzatabilirsiniz büyüyen uygulama ihtiyaçlarınızı karşılamak için yeni üyeler eklemek için. Ayrıca, dağıtabilirsiniz, `My` Visual Basic şablonu olarak diğer geliştiriciler için ad alanı uzantıları.  
  
###  <a name="addingtonamespace"></a> Üye ekleme My Namespace  
 Çünkü `My` bir ad alanı diğer herhangi bir ad gibi üst düzey özellikleri için yalnızca bir modül ekleme ve belirterek ekleyebileceğiniz bir `Namespace` , `My`. Modülü ile Açıklama `HideModuleName` özniteliği aşağıdaki örnekte gösterildiği gibi. `HideModuleName` Öznitelik sağlar üyelerinin görüntülediğinde IntelliSense modül adı görüntülenmez `My` ad alanı.  
  
 [!code-vb[VbVbcnExtendingMy#3](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_3.vb)]  
  
 Üye ekleme `My` ad modülü gerektiği gibi özellikleri ekleyin. Eklenen her bir özellik için `My` ad alanı, türü özel bir alan eklemek `ThreadSafeObjectProvider(Of T)`, burada türü, özel bir özellik tarafından döndürülen türdür. Bu alan çağırarak özelliği tarafından döndürülen için iş parçacığı açısından güvenli nesne örnekleri oluşturmak için kullanılan `GetInstance` yöntemi. Sonuç olarak, genişletilmiş özellik erişen her bir iş parçacığı kendi örneğini döndürülen türü alır. Aşağıdaki örnekte adlı bir özellik ekler `SampleExtension` türü olan `SampleExtension` için `My` ad alanı:  
  
 [!code-vb[VbVbcnExtendingMy#4](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_4.vb)]  
  
##  <a name="addingevents"></a> Nesnelerim özel olaylar ekleme  
 Kullanabileceğiniz `My.Application` için özel olaylar oluşturmak için nesne `My` genişleterek nesneleri `MyApplication` kısmi class içinde `My` ad alanı. Windows tabanlı projeler için çift tıklayabilirsiniz **Projem** düğümünde projeniz için **Çözüm Gezgini**. Visual Basic'te **Proje Tasarımcısı**, tıklayın `Application` sekmesine ve ardından `View Application Events` düğmesi. ApplicationEvents.vb adlı yeni bir dosya oluşturulur. Genişletmek için aşağıdaki kodu içeren `MyApplication` sınıfı.  
  
 [!code-vb[VbVbcnExtendingMy#5](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_5.vb)]  
  
 Olay işleyicileri için özel ekleyebilirsiniz `My` özel olay işleyicileri nesneleri `MyApplication` sınıfı. Özel olaylar, olay tetiklenir ya da bir olay işleyicisi eklenir, kaldırılır, yürütülen kod eklemenize olanak tanır. Unutmayın `AddHandler` kodu yalnızca bir kullanıcı tarafından olayı işlemek için kod eklediyseniz, özel olay çalıştırır. Örneğin, göz önünde bulundurun `SampleExtension` nesnesinin ise önceki bölümden bir `Load` bir özel olay işleyicisi eklemek istediğiniz olay. Aşağıdaki kod örneğinde adlı bir özel olay işleyicisi gösterir `SampleExtensionLoad` olacak ne zaman çağrılır `My.SampleExtension.Load` olayı oluşur. Yeni işlemek için kod eklendiğinde `My.SampleExtensionLoad` olay `AddHandler` bölümü bu özel olay kod yürütülür. `MyApplication_SampleExtensionLoad` Yöntemi işleyen bir olay işleyicisi örneği göstermek için aşağıdaki kod örneğinde dahil `My.SampleExtensionLoad` olay. Unutmayın `SampleExtensionLoad` seçtiğinizde olay kullanılabilir olacak **My uygulama olayları** seçeneği sol aşağı açılan listesinde yukarıda kod ApplicationEvents.vb dosyası düzenlenirken Düzenleyici.  
  
 [!code-vb[VbVbcnExtendingMy#6](../../../visual-basic/developing-apps/customizing-extending-my/codesnippet/VisualBasic/extending-the-my-namespace_6.vb)]  
  
##  <a name="design"></a> Tasarım yönergeleri  
 Uzantıları geliştirirken `My` ad alanı uzantısı bileşenlerinizi bakım maliyetlerini en aza indirmek için aşağıdaki yönergeleri kullanın.  
  
-   **Uzantı mantığı içerir.** Dahil olan mantıksal `My` ad alanı uzantısı, gerekli işlevleri kullanıma sunmak için gereken kodu içermelidir `My` ad alanı. Uzantınızı kullanıcı projelerinde kod kaynağı olarak yer alacağı için uzantı bileşeninin yüksek bakım maliyeti doğurur ve mümkün olduğunda kaçınılmalıdır.  
  
-   **Proje varsayımlar en aza indirin.** Oluşturduğunuzda, uzantıları `My` ad alanı, bir dizi başvuruları, proje düzeyi Imports veya belirli bir derleyici ayarları varsaymayın (örneğin, `Option Strict` kapalı). Bunun yerine, bağımlılıkları en aza indirmek ve kullanarak tüm tür başvurularını tam olarak nitelemek `Global` anahtar sözcüğü. Ayrıca, uzantı ile derlendiğinden emin olmak `Option Strict` uzantı hataları en aza indirmek için üzerinde.  
  
-   **Uzantı kodu yalıtın.** Tek bir dosyada kod yerleştirme uzantınızın Visual Studio öğe şablonu kolayca dağıtılabilir hale getirir. Daha fazla bilgi için bu konunun ilerleyen bölümlerinde "Paketleme ve dağıtma uzantıları" konusuna bakın. Tüm yerleştirme `My` ad alanı uzantı kodu tek bir dosyada veya ayrı bir klasörde bir proje de bulmalarına yardımcı olacak `My` ad alanı uzantısı.  
  
##  <a name="designing"></a> Sınıf kitaplıkları için tasarlama My  
 Çoğu nesne modelleri ile olduğu gibi bazı tasarım desenleri çalışmak iyi `My` ad alanı ve diğerleri yapın. Bir uzantı tasarlarken `My` ad alanı, aşağıdaki ilkeleri göz önünde bulundurun:  
  
-   **Durum bilgisi olmayan yöntemler.** Yöntemleri `My` ad alanı, belirli bir görev için eksiksiz bir çözüm sağlamalıdır. Yönteme geçirilen parametre değerleri belirli bir görevi tamamlamak için gereken tüm girişler sağladığından emin olun. Açık kaynak bağlantıları gibi önceki durum kullanan yöntemleri oluşturmaktan kaçının.  
  
-   **Genel örnekleri.** Tutulur yalnızca durumu `My` projeye genel ad alanı. Örneğin, `My.Application.Info` uygulama genelinde paylaşılan durum kapsüller.  
  
-   **Basit parametre türleri.** Karmaşık bir parametre türleri önleyerek basit bir anlatım gözetildiği. Bunun yerine, giriş parametresi yok ya da ele yöntemleri oluşturun veya dizeleri, ilkel türler vb. gibi basit giriş türlerini alır.  
  
-   **Fabrika yöntemleri.** Bazı türleri oluşturmak mutlaka zordur. Uzantıları olarak Fabrika yöntemleri sağlayan `My` ad alanı daha kolay bulmak ve bu kategoriye giren türleri kullanmasına olanak sağlar. İyi bir Üreteç yöntemi örneğidir `My.Computer.FileSystem.OpenTextFileReader`. .NET Framework'te bulunan çeşitli akış türü vardır. Özellikle, metin dosyaları belirterek `OpenTextFileReader` kullanıcının kullanmak için hangi akışını anlamanıza yardımcı olur.  
  
 Bu yönergeler, sınıf kitaplıkları için genel bir tasarım ilkeleri kullanımını değil. Bunun yerine, Visual Basic kullanan geliştiriciler için optimize edilmiş önerileri olduklarını ve `My` ad alanı. Genel tasarım ilkeleri sınıf kitaplıkları oluşturmak için bkz: [çerçeve tasarım yönergeleri](../../../standard/design-guidelines/index.md).  
  
##  <a name="packaging"></a> Paketleme ve hata ayıklama uzantıları  
 Ekleyebileceğiniz `My` ad alanı uzantıları Visual Studio Proje şablonu ya da uzantılarınızı paketleyebilir ve bunları Visual Studio öğesi şablon olarak dağıtabilirsiniz. Paketi, `My` ad alanı uzantıları Visual Studio öğe şablonu olarak Visual Basic tarafından sağlanan ek özelliklerden faydalanabilirsiniz. Bu özellikler, belirli bir derleme bir projeye başvuruda bulunduğunda, bir uzantı eklemeyi etkinleştirmek ya da açık olarak eklemek kullanıcıların, `My` kullanarak ad alanı uzantısı **My uzantılarını** sayfanın Visual Basic Proje Tasarımcısı.  
  
 Nasıl dağıtılacağı hakkındaki ayrıntılar için `My` ad alanı uzantılarını görmek [paketleme ve dağıtma özel My uzantılarını](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [My Uzantılarını Paketleme ve Dağıtma](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)
- [Visual Basic Uygulama Modelini Genişletme](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [My Özelliklerinde Hangi Nesnelerin Kullanılabilir Olduğunu Özelleştirme](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [My Extensions Sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
