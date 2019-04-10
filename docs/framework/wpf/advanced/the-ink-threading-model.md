---
title: Mürekkep İş Parçacığı Modeli
ms.date: 03/30/2017
helpviewer_keywords:
- application user interface thread [WPF]
- stylus plug-in
- ink threading model [WPF]
- ink [WPF], rendering
- pen thread [WPF]
- threading model [WPF]
- rendering ink [WPF]
- dynamic rendering thread [WPF]
- ink collection plug-in
- plug-ins [WPF], for ink
ms.assetid: c85fcad1-cb50-4431-847c-ac4145a35c89
ms.openlocfilehash: 80e7ef202c46a23069766512cf4e67bb21a49564
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335328"
---
# <a name="the-ink-threading-model"></a>Mürekkep İş Parçacığı Modeli
Tablet PC üzerinde mürekkep avantajları, çok yazma gibi normal Kalem ve kağıt hissettiği biridir.  Bunu gerçekleştirmek için tablet kalem, fare yapar ve kullanıcı yazdıkça mürekkebi işler daha çok daha yüksek bir hızda girdi verilerini toplar.  Uygulamanın kullanıcı arabirimini (UI) iş parçacığı engellenmiş olur çünkü Kalem verileri ve işleme mürekkebi toplama için yeterli değil.  Bunu çözmek için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama kullanıcı mürekkep yazdığında iki ek iş parçacığı kullanır.  
  
 Aşağıdaki listede yer toplama ve dijital mürekkebi işleme iş parçacıkları açıklanmaktadır:  
  
-   Kalem iş parçacığı - kaleminden giriş alan bir iş parçacığı.  (Gerçekte, bu iş parçacığı havuzu bağlıdır, ancak bu konu için bir kalem iş parçacığı olarak gösterir.)  
  
-   Uygulama kullanıcı arabirimi iş parçacığı - uygulama kullanıcı arabirimi denetimleri iş parçacığı.  
  
-   Dinamik işlenen iş parçacığı - kullanıcı mürekkebi işler iş parçacığı vuruşu çizer. Dinamik işlenen iş parçacığı penceresi Presentation Foundation'da belirtildiği gibi uygulamanın diğer kullanıcı Arabirimi öğelerini işler iş parçacığı farklıdır [iş parçacığı modeli](threading-model.md).  
  
 Uygulamanın kullandığı mürekkep modeli aynı olup <xref:System.Windows.Controls.InkCanvas> veya gösterilene benzer bir özel denetim [mürekkep giriş denetimi oluşturma](creating-an-ink-input-control.md).  İş parçacığı oluşturma açısından bu konuda ele alınmaktadır ancak <xref:System.Windows.Controls.InkCanvas>, özel bir denetim oluşturduğunuzda, aynı kavramlar geçerlidir.  
  
## <a name="threading-overview"></a>İş parçacığına genel bakış  
 Bir kullanıcı bir fırça çizdiğinde iş parçacığı modeli Aşağıdaki diyagramda gösterilmektedir:  
  
 ![Fırça darbesi çizerken iş parçacığı modeli. ](./media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1. Kullanıcı vuruş çizerken gerçekleşen eylemleri  
  
    1.  Kullanıcı bir fırça çizdiğinde, ekran kalemi noktaları kalem iş parçacığı üzerinde vardır.  Ekran kalemi de dahil olmak üzere eklentileri <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, ekran kalemi noktaları kalem iş parçacığı üzerinde kabul eder ve önce bunları değiştirmeniz şansınız <xref:System.Windows.Controls.InkCanvas> bunları alır.  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Dinamik işlenen iş parçacığı ekran kalemi noktalarında işler. Bu ve önceki adımla aynı anda gerçekleşir.  
  
    3.  <xref:System.Windows.Controls.InkCanvas> UI iş parçacığı üzerinde ekran kalemi noktalarını alır.  
  
2. Kullanıcı vuruş sona erdikten sonra gerçekleşen eylemleri  
  
    1.  Kullanıcı vuruşu çizim tamamlandığında <xref:System.Windows.Controls.InkCanvas> oluşturur bir <xref:System.Windows.Ink.Stroke> ekler ve nesne <xref:System.Windows.Controls.InkPresenter>, statik olarak işleyen.  
  
    2.  UI iş parçacığı uyarılar <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vuruş statik olarak işlenen, böylece <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> visual gösterimine stroke'un kaldırır.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Mürekkep toplama ve ekran kalemi eklentileri  
 Her <xref:System.Windows.UIElement> sahip bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Nesneler <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> almak ve kalem iş parçacığı ekran kalemi noktalarında değiştirebilirsiniz. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Nesnelerini alma içindeki sıralarına göre ekran kalemi noktaları <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 Aşağıdaki diyagramda kuramsal durumu gösterir burada <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonunu bir <xref:System.Windows.UIElement> içerir `stylusPlugin1`, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, ve `stylusPlugin2`bu sırası.  
  
 ![Ekran kalemi eklentileri sırasını çıkışı etkiler. ](./media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 Önceki diyagramda, aşağıdaki davranış gerçekleşir:  
  
1. `StylusPlugin1` x değerleri değiştirir ve y.  
  
2. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> değişiklik kalemi noktalarını alır ve bunları dinamik işlenen iş parçacığı üzerinde işler.  
  
3. `StylusPlugin2` değişiklik kalemi noktalarını alır ve daha fazla x değerlerini değiştirir ve y.  
  
4. Uygulama ekran kalemi noktaları toplar ve kullanıcı vuruş tamamlandığında vuruş statik olarak işler.  
  
 Varsayın `stylusPlugin1` dikdörtgen ekran kalemi noktaları sınırlar ve `stylusPlugin2` ekran kalemi noktalarını sağa çevirir.  Önceki senaryoda <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> kısıtlı ekran kalemi noktaları, ancak ekran kalemi noktalarını alır.  Kullanıcı vuruş çizdiğinde vuruş dikdörtgenin sınırları içinde oluşturulur, ancak kullanıcı kalemi kaldırıncaya kadar çevrilemeyen vuruş görünmez.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Ekran kalemi UI iş parçacığında eklentisi ile işlemlerini gerçekleştirme  
 Doğru isabet sınaması kalem iş parçacığı üzerinde gerçekleştirilemiyor çünkü bazı öğeleri diğer öğeler için amaçlanan iğne girişi zaman zaman alabilir. Giriş yönlendirildiğinden doğru bir işlem gerçekleştirmeden önce emin olmanız gerekir, abone olma ve işlemde gerçekleştirmek <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, veya <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> yöntemi. Bu yöntemler, uygulama iş parçacığının doğru isabet sınaması gerçekleştirildikten sonra çağrılır. Bu yöntemlerin abone olmak için çağrı <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> yöntemi yönteminde kalem iş parçacığı üzerinde oluşur.  
  
 Aşağıdaki diyagramda kalem iş parçacığı ve kullanıcı Arabirimi iş parçacığı ekran kalemi olaylarını göre arasındaki ilişkiyi gösterir bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![Mürekkep iş parçacığı oluşturma modelleri &#40;kullanıcı Arabirimi ve Kalem&#41;](./media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Mürekkebi işleme  
 Kullanıcı bir fırça çizer gibi <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> mürekkep "UI iş parçacığı meşgul olduğunda bile kaleminden flow" görünmesi için ayrı bir iş parçacığında mürekkebi işler.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Ekran kalemi noktaları toplayan bir görsel ağaç dinamik işlenen iş parçacığı üzerinde oluşturur.  Kullanıcı vuruş tamamlandığında <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> uygulama ileri işleme geçiş yaptığında uyarılmayı sorar.  Uygulama ileri işleme geçişi tamamlandıktan sonra <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> , görsel ağacı temizler.  Aşağıdaki diyagram bu işlemi göstermektedir.  
  
 ![Mürekkep iş parçacığı diyagram](./media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1. Kullanıcı vuruş başlar.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Görsel ağaç oluşturur.  
  
2. Kullanıcı vuruşu çiziyor.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Görsel ağaç oluşturur.  
  
3. Kullanıcı vuruşu sonlandırır.  
  
    1.  <xref:System.Windows.Controls.InkPresenter> Vuruş görsel ağacına ekler.  
  
    2.  Medya tümleştirme katmanı (MIL) vuruşları statik olarak işler.  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Görselleri temizler.
