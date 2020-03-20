---
title: Ekli Olaylara Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141568"
---
# <a name="attached-events-overview"></a>Ekli Olaylara Genel Bakış

Genişletilebilir Uygulama Biçimlendirme Dili (XAML), bir dil bileşeni ve *ekli olay*olarak adlandırılan olay türünü tanımlar. Ekli bir olay kavramı, olayı gerçekten tanımlayan veya devralan bir öğeyerine rasgele bir öğeye belirli bir olay için işleyici eklemenize olanak tanır. Bu durumda, ne nesneyi potansiyel olarak olay yükselterek ne de hedef işleme örneği tanımlar veya başka bir olay "sahibi".  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Önkoşullar  
 Bu [konu, Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md) ve [XAML Genel Bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md)okuduğunuz varsayar.  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>Ekli Olay Sözdizimi  
 Ekli olaylar, ekli olay kullanımını desteklemek için bir XAML sözdizimi ve destek kodu tarafından kullanılması gereken bir kodlama deseni vardır.  
  
 XAML sözdiziminde, eklenen olay sadece olay adı ile değil, sahip olduğu tür artı olay adı ile bir nokta (.) ile ayrılmış olarak belirtilir. Olay adı kendi türüadı ile nitelikli olduğundan, ekli olay sözdizimi herhangi bir ekli olay anlık olabilir herhangi bir öğeye eklenmesine izin verir.  
  
 Örneğin, özel `NeedsCleaning` bir bağlı olay için işleyici eklemek için XAML sözdizimi aşağıdaverilmiştir:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Önek `aqua:` dikkat edin; ekteki olay özel eşlenmiş xmlns gelen özel bir olay olduğundan önek bu durumda gereklidir.  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>WPF Ekli Olayları Nasıl Uygular?

WPF'de, ekli olaylar bir <xref:System.Windows.RoutedEvent> alan tarafından desteklenen ve yükseltildikten sonra ağaç üzerinden yönlendirilir. Genellikle, ekli olayın kaynağı (olayı yükselten nesne) bir sistem veya hizmet kaynağıdır ve olayı yükselten kodu çalıştıran nesne bu nedenle öğe ağacının doğrudan bir parçası değildir.  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>Ekli Olaylar için Senaryolar  
 WPF'de, statik <xref:System.Windows.Input.Mouse> sınıfın veya <xref:System.Windows.Controls.Validation> sınıfın etkinleştirdiği olaylar gibi hizmet düzeyi soyutlamanın olduğu belirli özellik alanlarında ekli olaylar bulunur. Hizmetle etkileşimde bulunan veya hizmeti kullanan sınıflar, olayı ekteki olay sözdiziminde kullanabilir veya sınıfın hizmetin yeteneklerini nasıl tümleştirdiğinin bir parçası olan yönlendirilmiş bir olay olarak ekli olayı yüzeyden ayırmayı seçebilir.  
  
 WPF bir dizi bağlı olayı tanımlasa da, bağlı olayı doğrudan kullanacağınız veya işleyeceğiniz senaryolar çok sınırlıdır. Genellikle, ekli olay mimari bir amaca hizmet eder, ancak daha sonra bağlı olmayan (CLR olay "sarıcı" ile desteklenen) yönlendirilmiş olay iletilir.  
  
 Örneğin, xaml veya <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> kod ya ekli olay <xref:System.Windows.UIElement> sözdizimi ile ilgili yerine bu <xref:System.Windows.UIElement.MouseDown> <xref:System.Windows.UIElement> kullanarak herhangi bir temel ekli olay daha kolay işlenebilir. Bağlı olay, giriş aygıtlarının gelecekteki genişlemesine izin verdiği için mimaride bir amaca hizmet eder. Varsayımsal aygıtın yalnızca fare girişini simüle etmek için yükseltmesi <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> gerekir <xref:System.Windows.Input.Mouse> ve bunu yapmak için türetin gerekmez. Ancak, bu senaryo olayların kod işleme içerir ve ekli olayın XAML işleme bu senaryo ile ilgili değildir.  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>WPF'de Ekli Bir Olayı İşleme  
 Ekli bir olayı işleme işlemi ve yazacağınız işleyici kodu, temelde yönlendirilmiş bir olay için aynıdır.  
  
 Genel olarak, WPF ekli bir olay, WPF yönlendirilmiş bir olaydan çok farklı değildir. Farklar, olayın nasıl kaynağı olduğu ve bir sınıf tarafından üye olarak nasıl ortaya çıkarılan (xaml işleyicisi sözdizimini de etkilediği) dir.  
  
 Ancak, daha önce belirtildiği gibi, mevcut WPF ekli olaylar özellikle WPF işlemek için tasarlanmamıştır. Daha sık, olayın amacı, bileşik bir öğenin bir durumu birleştirmedeki bir üst öğeye bildirmesini sağlamaktır, bu durumda olay genellikle kodolarak yükseltilir ve aynı zamanda ilgili üst sınıftasınıf işlemeye dayanır. <xref:System.Windows.Controls.Primitives.Selector> Örneğin, a içindeki öğelerin, <xref:System.Windows.Controls.Primitives.Selector.Selected> <xref:System.Windows.Controls.Primitives.Selector> sınıf tarafından işlenen ve daha sonra sınıf tarafından <xref:System.Windows.Controls.Primitives.Selector> potansiyel olarak farklı bir yönlendirilmiş olaya <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>dönüştürülen ekli olayı yükseltmesi beklenir. Yönlendirilen olaylar ve sınıf işleme hakkında daha fazla bilgi için, [Yönlendirilen Olayları İşlenirken İşaretleme ve Sınıf İşleme'ye](marking-routed-events-as-handled-and-class-handling.md)bakın.  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>Kendi Ekli Etkinliklerinizi Yönlendirilmiş Olaylar Olarak Tanımlama  
 Ortak WPF taban sınıflarından türeyen iseniz, sınıfınızda belirli desen yöntemlerini ekleyerek ve temel sınıflarda zaten mevcut olan yardımcı program yöntemlerini kullanarak kendi ekli etkinliklerinizi uygulayabilirsiniz.  
  
 Desen aşağıdaki gibidir:  
  
- İki parametre ile __*EventName*Işleyicisi ekle__ yöntemi. İlk parametre, olay işleyicisinin eklendiği örnektir. İkinci parametre, eklenecek olay işleyicisidir. Yöntem olmalı `public` ve `static`, hiçbir iade değeri ile.  
  
- İki parametreile __*EventName*Işleyicisi kaldır'__ yöntemi. İlk parametre, olay işleyicisinin kaldırıldığı örnektir. İkinci parametre kaldırılacak olay işleyicisidir. Yöntem olmalı `public` ve `static`, hiçbir iade değeri ile.  
  
 __*EventName*İşleyicisi Ekle__ erişimyöntemi, bir öğe üzerinde eklenen olay işleyicisi öznitelikleri bildirildiğinde XAML işlemini kolaylaştırır. __*EventName*İşleyicisi Ekle__ ve __Olay Adı*İşleyicisini*Kaldır__ yöntemleri de ekli olay için olay işleyicisi deposuna kod erişimi sağlar.  
  
 Herhangi bir XAML okuyucu uygulaması destekleyici dil ve mimaride temel olayları tanımlamak için farklı şemaları olabilir, çünkü bu genel desen henüz bir çerçevede pratik uygulama için yeterince hassas değildir. Bu, WPF'nin yönlendirilen olaylar olarak ekli olayları uygulama nedenlerinden biridir; bir olay için kullanılacak tanımlayıcı (<xref:System.Windows.RoutedEvent>) zaten WPF olay sistemi tarafından tanımlanır. Ayrıca, bir olayı yönlendirme, ekli bir olayın XAML dil düzeyi kavramıüzerinde doğal bir uygulama uzantısıdır.  
  
 WPF ekli bir olay için <xref:System.Windows.UIElement.AddHandler%2A> __*EventName*İşleyicisi__ ekle uygulaması, yönlendirilen olayı ve işleyiciyi bağımsız değişken olarak çağırmaktan oluşur.  
  
 Bu uygulama stratejisi ve genel olarak yönlendirilmiş olay sistemi, <xref:System.Windows.UIElement> yalnızca <xref:System.Windows.ContentElement> bu sınıfların uygulamaları olduğundan, <xref:System.Windows.UIElement.AddHandler%2A> ekli olayların işlenmesini türemiş sınıflarla veya türetilmiş sınıflarla kısıtlar.  
  
 Örneğin, aşağıdaki kod, bağlı `NeedsCleaning` olayı yönlendirilmiş bir `Aquarium`olay olarak bildirme ye ait WPF ekli olay stratejisini kullanarak, sahip sınıfındaki ekteki olayı tanımlar.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Ekli olay tanımlayıcı alanını oluşturmak için kullanılan yöntemin aslında <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>bağlı olmayan bir yönlendirilmiş olayı kaydetmek için kullanılan yöntemle aynı olduğunu unutmayın. Ekli olaylar ve yönlendirilmiş olayların tümü merkezi bir dahili mağazaya kaydedilir. Bu olay deposu [uygulaması, Yönlendirilmiş Olaylara Genel Bakış'ta](routed-events-overview.md)tartışılan "arabirim olarak olaylar" kavramsal dikkate alınmasını sağlar.  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>WPF Ekli Etkinlik Yükseltme  
 Genellikle kodunuzdan wpf tanımlı bağlı olayları yükseltmeniz gerekmez. Bu olaylar genel "hizmet" kavramsal modelini <xref:System.Windows.Input.InputManager> izler ve bu tür hizmet sınıfları olayların yükseltilmesinden sorumludur.  
  
 Ancak, bağlı olayları temel alan WPF modeline dayalı özel bir bağlı <xref:System.Windows.RoutedEvent>olay tanımlıyorsanız, <xref:System.Windows.UIElement.RaiseEvent%2A> ekli bir olayı <xref:System.Windows.UIElement> herhangi <xref:System.Windows.ContentElement>birinden veya. Yönlendirilen bir olayı yükseltmek (ekli veya bağlı değil) öğe ağacında belirli bir öğeyi olay kaynağı olarak bildirmenizi gerektirir; bu kaynak <xref:System.Windows.UIElement.RaiseEvent%2A> arayan olarak bildirilir. Ağaçtaki kaynağın hangi öğe olarak raporlandığı belirlendir, hizmetinsorumluluğundadır  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gönderilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Ayrıntılı XAML Sözdizimi](xaml-syntax-in-detail.md)
- [WPF için XAML ve Özel Sınıflar](xaml-and-custom-classes-for-wpf.md)
