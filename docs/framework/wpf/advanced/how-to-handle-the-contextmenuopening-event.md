---
title: 'Nasıl yapılır: ContextMenuOpening Olayını İşleme'
ms.date: 03/30/2017
helpviewer_keywords:
- ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
ms.openlocfilehash: ab4c4867981cd318738b7404d76f2f5932bb9059
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Nasıl yapılır: ContextMenuOpening Olayını İşleme
<xref:System.Windows.FrameworkElement.ContextMenuOpening> Olay ya da varolan bağlam menüsü önceliğini görüntülemek veya ayarlayarak görüntülenen menüsünü bastırmak için ayarlamak için bir uygulamada işlenebilir <xref:System.Windows.RoutedEventArgs.Handled%2A> özelliğine `true` olay verisi içinde. Ayar tipik nedeni <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` olay verileri menü tamamen yeni bir ile değiştirmektir <xref:System.Windows.Controls.ContextMenu> nesnesi, bazen işlemi iptal ediliyor ve yeni bir açık başlatma gerektirir. İçin işleyiciler yazarsanız <xref:System.Windows.FrameworkElement.ContextMenuOpening> olayı olmanız gerekir arasında zamanlama sorunların farkında bir <xref:System.Windows.Controls.ContextMenu> denetimi ve açma ve denetimlerin bağlam menülerini genel konumlandırma sorumlu hizmet. Bu konu, çeşitli bağlam menüsü açma senaryolarının kod tekniklerini bazıları gösterir ve zamanlama sorunu oyuna nereden geldiğini durumunu gösterir.  
  
 İşleme için birkaç senaryo vardır <xref:System.Windows.FrameworkElement.ContextMenuOpening> olay:  
  
-   Menü öğelerini görüntüleme önce ayarlama.  
  
-   Görüntü önce tüm menü değiştirme.  
  
-   Tamamen varolan herhangi bağlam menüsünü gizleme ve hiçbir bağlam menüsünü görüntüleme.  
  
## <a name="example"></a>Örnek  
  
## <a name="adjusting-the-menu-items-before-display"></a>Menü öğelerini görüntüleme önce ayarlama  
 Varolan menü öğelerini ayarlama oldukça basittir ve büyük olasılıkla en yaygın senaryodur. Eklemek veya yanıt geçerli durumu, uygulamanızda veya bağlam menüsünü burada istenen nesne üzerinde bir özelliği olarak kullanılabilir olan özel durumu bilgileri olarak bağlam menüsü seçenekleri çıkarmak için bunu yapabilirsiniz.  
  
 Sağ belirli denetim olan olayın kaynağını almak ve genel tekniktir <xref:System.Windows.FrameworkElement.ContextMenu%2A> özelliğini almaktır. Genellikle denetlemek istediğiniz <xref:System.Windows.Controls.ItemsControl.Items%2A> zaten menüde, mevcut ve ardından ekleyip yeni uygun hangi bağlam menüsü öğeleri görmek için koleksiyon <xref:System.Windows.Controls.MenuItem> maddeleri veya koleksiyondan.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Görüntü önce tüm menü değiştirme  
 Bir alternatif, tüm bağlam menüsünü değiştirmek istiyorsanız bir senaryodur. Elbette da önceki kod çeşitlemesi her öğenin varolan bir bağlam menüsündeki kaldırmak ve sıfır öğesi ile başlayan yenilerini eklemek için kullanabilirsiniz. Ancak daha sezgisel bir yaklaşım bağlam menüsünden tüm öğeleri değiştirmek için yeni bir <xref:System.Windows.Controls.ContextMenu>, öğeler ile doldurulur ve ardından <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> yeni olması denetimin özelliğini <xref:System.Windows.Controls.ContextMenu>.  
  
 Değiştirme için basit işleyici kodu aşağıdaki bir <xref:System.Windows.Controls.ContextMenu>. Özel koda başvuran `BuildMenu` onu çağrıldığı birden fazla örnek işleyiciler tarafından ayrılmış olan yöntemi.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Ancak, bu stili işleyicisinin kullanırsanız <xref:System.Windows.FrameworkElement.ContextMenuOpening>, varsa potansiyel bir zamanlama sorunu getirebilir ayarladığınız nesne <xref:System.Windows.Controls.ContextMenu> önceden var olan bir bağlam menüsü yok. Bir kullanıcı bir denetimi tıklattığında <xref:System.Windows.FrameworkElement.ContextMenuOpening> tetiklenir olsa bile varolan <xref:System.Windows.Controls.ContextMenu> boş veya null. Ancak bu durumda, her yeni <xref:System.Windows.Controls.ContextMenu> kaynak üzerinde ayarlanmış öğesi çok geç ulaşır görüntülenecek. Ayrıca, kullanıcı ikinci kez sağ olursa, ancak bu defa yeni <xref:System.Windows.Controls.ContextMenu> görüntülenirse, değer null değildir ve işleyicinizi düzgün şekilde değiştirin ve işleyici ikinci kez çalıştırıldığında menüsü görüntülenir. Bu iki olası geçici çözümler önerir:  
  
1.  Çalışabildiğinden emin olun <xref:System.Windows.FrameworkElement.ContextMenuOpening> her zaman en az bir yer tutucu denetimleri karşı çalıştırmak işleyicileri <xref:System.Windows.Controls.ContextMenu> kullanılabilir işleyici koduyla değiştirilmesini amaçladığınız. Bu durumda, önceki örnekte gösterilen işleyiciyi kullanmaya devam edebilirsiniz, ancak genellikle bir yer tutucu atamak istediğiniz <xref:System.Windows.Controls.ContextMenu> ilk biçimlendirme içinde:  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Varsayımında ilk <xref:System.Windows.Controls.ContextMenu> değeri olabilir null, bazı başlangıç mantığına göre. Denetlemede <xref:System.Windows.Controls.ContextMenu> null ya da kullanım işleyicinizi olup olmadığını denetlemek için kodunuzda bir bayrak için çalıştıran en az bir kez. Olmadığını varsayar çünkü <xref:System.Windows.Controls.ContextMenu> ilgili olarak görüntülenen işleyicinizi yapılır ve ardından ayarlar <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` olay verisi içinde. İçin <xref:System.Windows.Controls.ContextMenuService> bağlam menüsü görüntüleme için sorumlu bir `true` değerini <xref:System.Windows.RoutedEventArgs.Handled%2A> olay bağlam menüsü görüntüleme iptal / olayı birleşimi denetlemek için bir istek verileri temsil eder.  
  
 Potansiyel şüpheli bağlam menüsü gizlenen, yeni bir tane sağlamak için sonraki adım olan sonra görüntüleyin. Yeni bir, aslında aynı önceki işleyici olarak ayarlama: yeni bir derleme <xref:System.Windows.Controls.ContextMenu> ve denetim kaynağının ayarlayın <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> onunla özelliği. İlk denemesi gizlenmesi için ek bağlam menüsü görüntüleme şimdi zorlamalısınız adımdır. Görüntü zorlamak için ayarladığınız <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> özelliğine `true` işleyici içinde. İşleyicisinde bağlam menüsünü açarak başlatır çünkü bunu yaparken dikkatli olun <xref:System.Windows.FrameworkElement.ContextMenuOpening> yeniden olay. İşleyicinizi yeniden girin, sonsuz özyinelemeli olur. Her zaman denetlemek gereken bu yüzden `null` veya bir bağlam menüsü içinden açarsanız bir bayrak kullanın bir <xref:System.Windows.FrameworkElement.ContextMenuOpening> olay işleyicisi.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Varolan herhangi bağlam menüsünü gizleme ve hiçbir bağlam menüsünü görüntüleme  
 Seyrek bir menü tümüyle bastırır işleyicisi yazma son senaryodur. Bir bağlam menüsü görüntülemek için belirli bir denetim beklenmiyor varsa, bu daha yeni bir kullanıcı istediğinde menü görüntülemesi için büyük olasılıkla daha uygun yolu vardır. Ancak işleyiciyi bağlam menüsünü bastırmak ve hiçbir şey göstermek için kullanmak istediğiniz sonra işleyicinizi yalnızca ayarlamalısınız <xref:System.Windows.RoutedEventArgs.Handled%2A> için `true` olay verisi içinde. <xref:System.Windows.Controls.ContextMenuService> , Sorumlu bir bağlam menüsü görüntüleme denetimde ortaya çıkan olayın olay verilerini denetler. Olay işaretliyse <xref:System.Windows.RoutedEventArgs.Handled%2A> yol boyunca olayı başlatan bağlam menüsünün açık eylemi sonra herhangi bir yere engellenir.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [Temel Öğelere Genel Bakış](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [ContextMenu Genel Bakış](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
