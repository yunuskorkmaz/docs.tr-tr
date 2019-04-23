---
title: 'Nasıl yapılır: ContextMenuOpening Olayını İşleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: 65a1e34d5b078c49bf59c2d9787812940c9a7494
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340405"
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Nasıl yapılır: ContextMenuOpening Olayını İşleme
<xref:System.Windows.FrameworkElement.ContextMenuOpening> Olay ya da bir var olan bağlam menüsü önceki görüntülemek veya ayarlayarak görüntülenen menüyü bastırmak için ayarlamak için bir uygulama işlenebilir <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliğini `true` içinde olay verileri. Ayar tipik nedeni <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` olay menü tamamen yeni ile değiştirilecek verilerdir <xref:System.Windows.Controls.ContextMenu> işlemi iptal ediliyor ve yeni bir açık başlatma bazen gerektiren, nesne. İçin işleyiciler yazarsanız <xref:System.Windows.FrameworkElement.ContextMenuOpening> olay olmanız gerekir zamanlama sorunları arasında farkında bir <xref:System.Windows.Controls.ContextMenu> denetimi ve açma ve genel denetimlerin bağlam menülerini konumlandırma sorumlu hizmeti. Bu konuda çeşitli bağlam menüsü açma senaryoları için kod yöntemlerden bazıları gösterilmektedir ve burada zamanlama sorunu devreye bir durumu gösterir.  
  
 İşleme için birkaç senaryo mevcuttur <xref:System.Windows.FrameworkElement.ContextMenuOpening> olay:  
  
-   Görüntü önce menü öğelerini ayarlanıyor.  
  
-   Önce görünen tüm menü değiştiriliyor.  
  
-   Tamamen var olan herhangi bir bağlam menüsü gizleme ve hiçbir bağlam menüsünü görüntüleme.  
  
## <a name="example"></a>Örnek  
  
## <a name="adjusting-the-menu-items-before-display"></a>Menü öğelerini görünen önce ayarlama  
 Mevcut menü öğelerini ayarlama oldukça basittir ve büyük olasılıkla en yaygın senaryodur. Eklemek veya bağlam menüsü seçenekleri geçerli durumu bilgileri, uygulamanızda veya bağlam menüsünü burada istenen nesne üzerinde bir özelliği olarak kullanılabilir özel durum bilgilerini yanıt olarak çıkarmak için bunu yapabilirsiniz.  
  
 Tıklanan belirli denetim olan, olay kaynağını almak ve genel tekniktir <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliğini. Genellikle kontrol etmek istediğiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> zaten mevcut ve ardından ekleyip yeni uygun hangi bağlam menüsü öğeleri görmek için koleksiyon <xref:System.Windows.Controls.MenuItem> öğeleri için veya koleksiyon.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Önce görünen tüm menü değiştirme  
 Bir alternatif, tüm bağlam menüsünü değiştirmek istiyorsanız senaryodur. Elbette da önceki kod çeşitlemesi her var olan bir bağlam menüsü öğesini kaldırın ve sıfır öğe ile başlayan yenilerini eklemek için kullanabilirsiniz. Ancak daha sezgisel bir yaklaşım bağlam menüsünden tüm öğeleri değiştirmek için yeni bir <xref:System.Windows.Controls.ContextMenu>öğeleriyle doldurun ve ardından <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> yeni olacak şekilde bir denetimin özellik <xref:System.Windows.Controls.ContextMenu>.  
  
 Değiştirme için basit bir işleyici kodu verilmiştir bir <xref:System.Windows.Controls.ContextMenu>. Bir özel koda başvuran `BuildMenu` olduğu çağrıldığı için birden fazla örnek işleyiciler tarafından ayrılmış olan yöntem.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Ancak, bu stil işleyicisinin kullanırsanız <xref:System.Windows.FrameworkElement.ContextMenuOpening>, potansiyel olarak, bir zamanlama sorunu getirebilir ayarladığınız nesne <xref:System.Windows.Controls.ContextMenu> önceden var olan bir bağlam menüsü sahip değil. Bir kullanıcının bir denetimi tıklattığında <xref:System.Windows.FrameworkElement.ContextMenuOpening> tetiklenir olsanız bile var olan <xref:System.Windows.Controls.ContextMenu> boş veya null. Ancak bu durumda, her yeni <xref:System.Windows.Controls.ContextMenu> kaynağında ayarladığınız öğesi ulaşan çok geç görüntülenecek. Ayrıca, kullanıcı ikinci kez sağ tıkladığınızda, bu sefer yeni <xref:System.Windows.Controls.ContextMenu> göründüğünde, null değeri değildir ve işleyicinizi düzgün şekilde değiştirin ve işleyici ikinci kez çalıştırıldığında menüsünü görüntüleme. Bu, iki olası geçici çözümler önerir:  
  
1. Çalışabildiğinden emin olun <xref:System.Windows.FrameworkElement.ContextMenuOpening> her zaman en az bir yer tutucu denetimleri karşı çalıştırma işleyicileri <xref:System.Windows.Controls.ContextMenu> kullanılabilir işleyici kodu değiştirilmesi amaçladığınız. Bu durumda, önceki örnekte gösterilen işleyiciyi kullanmaya devam edebilirsiniz, ancak genellikle bir yer tutucu atamak istediğiniz <xref:System.Windows.Controls.ContextMenu> ilk biçimlendirme içinde:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2. Varsayımında ilk <xref:System.Windows.Controls.ContextMenu> değeri olabilir null, bazı başlangıç mantığına göre. Denetlemede <xref:System.Windows.Controls.ContextMenu> null ya da kodunuzda işleyicinizi olup olmadığını denetlemek için bir bayrak kullanın çalıştıran en az bir kez. Olduğunu varsaydığından <xref:System.Windows.Controls.ContextMenu> ilgili olarak görüntülenen işleyicinizi yapılır ve ardından ayarlar <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` içinde olay verileri. İçin <xref:System.Windows.Controls.ContextMenuService> bağlam menüsü görüntüleme için sorumlu bir `true` değerini <xref:System.Windows.RoutedEventArgs.Handled%2A> olay iptal et bağlam menüsü görüntüleme / olayı birleşimi denetlemek için bir istek verileri temsil eder.  
  
 Şüpheli bağlam menüsü gizlenen, sonraki adım olan yeni bir tane sağlamayı bunu görüntüleyebilir. İçin yeni bir temel olarak aynı olup önceki işleyici: yeni bir yapı <xref:System.Windows.Controls.ContextMenu> ve denetim kaynağının <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> onunla özelliği. Ek bir adım bağlam menüsü görüntülenmesini artık zorlamalısınız yapılan ilk girişim gizlenen olmasıdır. Görüntülemeye zorla için ayarlamanız <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> özelliğini `true` işleyici içinde. Bağlam menüsünü açarak işleyicisinde ortaya çıkardığı için bunu yaparken dikkatli olun <xref:System.Windows.FrameworkElement.ContextMenuOpening> yeniden olay. İşleyicinize sonsuz özyinelemeli dönüşür. Her zaman denetlemek gereken bu yüzden `null` veya bağlam menüsünü içinden açarsanız bir bayrağını kullanın. bir <xref:System.Windows.FrameworkElement.ContextMenuOpening> olay işleyicisi.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Var olan herhangi bir bağlam menüsü gizleme ve hiçbir bağlam menüsü görüntüleme  
 Bir menüyü tümüyle bastıran bir işleyicisi yazma son senaryosu, sıra dışı. Bir bağlam menüsünü görüntülemek için belirli bir denetim olmaması gerekiyorsa bu değerden yalnızca bir kullanıcı istediğinde menü görüntülemesi için büyük olasılıkla daha uygun bir yolu vardır. Ancak işleyici bağlam menüsü bastırmak ve hiçbir şey göstermek için kullanmak istediğiniz sonra işleyicinizi yalnızca ayarlamalısınız <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` içinde olay verileri. <xref:System.Windows.Controls.ContextMenuService> Bağlam menüsü görüntüleme denetimde tetiklenen olayı olay verilerini denetler sorumlu olan. Olay işaretliyse <xref:System.Windows.RoutedEventArgs.Handled%2A> herhangi bir yol boyunca olayı başlatan bağlam menüsünün açık eylemi ardından bastırılır.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](~/samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ContextMenu>
- <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>
- [Temel Öğelere Genel Bakış](base-elements-overview.md)
- [ContextMenu Genel Bakış](../controls/contextmenu-overview.md)
