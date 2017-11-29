---
title: "Mürekkep İş Parçacığı Modeli"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: efbd05f88b962363e3b866fbf914f6d3a37823cc
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="the-ink-threading-model"></a>Mürekkep İş Parçacığı Modeli
Tablet PC mürekkep avantajları, çok yazmak gibi bir normal Kalem ve kağıt hissi olduğunu biridir.  Bunu başarmak için tablet kalem fare yapar ve kullanıcının yazmasına mürekkep işler daha çok daha yüksek bir hızda giriş verilerini toplar.  Engellenmiş duruma olduğundan uygulamanın kullanıcı arabirimini (UI) iş parçacığı kalem verisi ve mürekkep işleme toplanması için yeterli değil.  Bunu çözmek için bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama kullanıcı mürekkep yazdığında iki ek iş parçacığı kullanır.  
  
 Aşağıdaki listede, toplama ve dijital mürekkep işleme katılmak iş parçacıklarını açıklar:  
  
-   Kalem iş parçacığı - kaleminden giriş alan iş parçacığı.  (Gerçekte, bu iş parçacığı havuzu bağlıdır, ancak bu konu için kalem iş parçacığı olarak gösterir.)  
  
-   Uygulama kullanıcı arabirimi iş parçacığı - uygulamanın kullanıcı arabirimi denetimlerini iş parçacığı.  
  
-   Dinamik işleme iş parçacığı - kullanıcı mürekkep işleyen iş parçacığından vuruş çizer. Dinamik işleme iş parçacığı penceresi Presentation Foundation'da belirtildiği gibi uygulama için diğer UI öğelerini işleyen iş parçacığından farklıdır [iş parçacığı modeline](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
 Uygulama kullanıp kullanmadığını içindekine modeli aynıdır <xref:System.Windows.Controls.InkCanvas> veya gösterilene benzer bir özel denetim [mürekkep giriş denetimi oluşturma](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  İş parçacığı açısından, bu konuda ele almasına rağmen <xref:System.Windows.Controls.InkCanvas>, özel bir denetim oluşturduğunuzda aynı kavramlar uygulanır.  
  
## <a name="threading-overview"></a>Genel Bakış iş parçacığı oluşturma  
 Aşağıdaki diyagramda bir kullanıcı vuruş çizerken iş parçacığı modelini gösterir:  
  
 ![Vuruş çizerken iş parçacığı modeli. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-drawingink.png "InkThreading_DrawingInk")  
  
1.  Kullanıcı vuruş çizerken oluşan eylemler  
  
    1.  Kullanıcı vuruş çizerken, kalem noktalarını kalem iş parçacığında geldikçe.  Kalem dahil olmak üzere eklentileri, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, kalem iş parçacığı kalem noktalarında kabul etmek ve daha önce değiştirme şansına sahip <xref:System.Windows.Controls.InkCanvas> bunları alır.  
  
    2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Dinamik işleme iş parçacığı kalem noktalarında işler. Bu ve önceki adımla aynı anda gerçekleşir.  
  
    3.  <xref:System.Windows.Controls.InkCanvas> Kullanıcı Arabirimi iş parçacığı kalem noktalarında alır.  
  
2.  Kullanıcı vuruşun sona erdikten sonra gerçekleşen Eylemler  
  
    1.  Kullanıcı vuruş çizmeyi tamamlandığında <xref:System.Windows.Controls.InkCanvas> oluşturur bir <xref:System.Windows.Ink.Stroke> nesne ve ona ekler <xref:System.Windows.Controls.InkPresenter>, statik olarak işleyen.  
  
    2.  Kullanıcı Arabirimi iş parçacığı uyarıları <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vuruşun statik olarak işlenen, böylece <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vuruşun görsel gösterimini kaldırır.  
  
## <a name="ink-collection-and-stylus-plug-ins"></a>Mürekkep koleksiyonu ve Kalem eklentiler  
 Her <xref:System.Windows.UIElement> sahip bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Nesnelerini <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> almak ve kalem iş parçacığı kalem noktalarında değiştirebilirsiniz. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Nesneleri içindeki sıralarına göre kalem noktalarını alma <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>.  
  
 Aşağıdaki diyagramda kuramsal durumu gösterir nerede <xref:System.Windows.UIElement.StylusPlugIns%2A> koleksiyonu bir <xref:System.Windows.UIElement> içeren `stylusPlugin1`, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, ve `stylusPlugin2`bu sırası.  
  
 ![Kalem eklentileri sırasını çıkışı etkiler. ] (../../../../docs/framework/wpf/advanced/media/inkthreading-pluginorder.png "InkThreading_PluginOrder")  
  
 Önceki diyagramda aşağıdaki davranış gerçekleşir:  
  
1.  `StylusPlugin1`x değerlerini değiştirir ve y.  
  
2.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>Değiştirilen kalem noktalarını alır ve bunları dinamik işleme iş parçacığında işler.  
  
3.  `StylusPlugin2`Değiştirilen kalem noktalarını alır ve daha fazla x değerlerini değiştirir ve y.  
  
4.  Uygulama kalem noktalarını toplar ve Kullanıcı vuruşu tamamlandığında Vuruşun statik olarak işler.  
  
 Varsayın `stylusPlugin1` kalem noktalarını dikdörtgen kısıtlar ve `stylusPlugin2` kalem noktalarını sağa çevirir.  Önceki senaryoda <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> kısıtlı kalem noktalarını ancak değil çevrilmiş kalem noktalarını alır.  Kullanıcı vuruşun çizer vuruşun dikdörtgen sınırları içinde işlenir ancak vuruşun kullanıcı kalem kaldırır kadar çevrilmesi gibi görünmüyor.  
  
### <a name="performing-operations-with-a-stylus-plug-in-on-the-ui-thread"></a>Kullanıcı Arabirimi iş parçacığı üzerinde eklenti kalem ile işlemlerini gerçekleştirme  
 Doğru isabet sınaması kalem iş parçacığı üzerinde gerçekleştirilemediğinden, bazı öğeler bazen diğer öğeler için amaçlanan kalem giriş alabilirsiniz. Giriş doğru olarak yönlendirildiğinden bir işlem gerçekleştirmeden önce emin olmak gerekiyorsa, abone olun ve işlemi gerçekleştirmek <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusDownProcessed%2A>, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusMoveProcessed%2A>, veya <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn.OnStylusUpProcessed%2A> yöntemi. Bu yöntemler, doğru isabet sınaması gerçekleştirildikten sonra uygulama iş parçacığı tarafından çağrılır. Bu yöntemlere abone olmak için arama <xref:System.Windows.Input.StylusPlugIns.RawStylusInput.NotifyWhenProcessed%2A> kalem iş parçacığında oluşan yönteminde yöntemi.  
  
 Aşağıdaki diyagramda kalem iş parçacığı ve kullanıcı Arabirimi iş parçacığı kalem olaylarını göre arasındaki ilişkiyi göstermektedir bir <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>.  
  
 ![İş parçacığı oluşturma modelleri &#40;mürekkep; Kullanıcı Arabirimi ve Kalem &#41; ] (../../../../docs/framework/wpf/advanced/media/inkthreading-plugincallbacks.png "InkThreading_PluginCallbacks")  
  
## <a name="rendering-ink"></a>Mürekkep işleme  
 Kullanıcı bir vuruş çizer gibi <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> mürekkep akış"kullanıcı Arabirimi iş parçacığı meşgul olduğunda bile kalem" görünmesi için ayrı bir iş parçacığı üzerinde mürekkep işler.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Kalem noktalarını topladığı gibi bir görsel ağaç dinamik işleme iş parçacığında oluşturur.  Kullanıcı vuruşu tamamlandığında <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> uygulama sonraki işleme geçiş yaptığında uyarılmayı sorar.  Uygulama sonraki işleme geçişini tamamlandıktan sonra <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> kendi görsel ağacı temizler.  Aşağıdaki diyagram bu işlemi gösterilmektedir.  
  
 ![Diyagram iş parçacığı oluşturma mürekkep](../../../../docs/framework/wpf/advanced/media/inkthreading-visualtree.png "InkThreading_VisualTree")  
  
1.  Kullanıcı vuruşun başlar.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Görsel ağaç oluşturur.  
  
2.  Kullanıcı vuruş çizmeyi.  
  
    1.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Görsel ağaç oluşturur.  
  
3.  Kullanıcı vuruşu sonlandırır.  
  
    1.  <xref:System.Windows.Controls.InkPresenter> Vuruşu görsel ağacına ekler.  
  
    2.  Ortam tümleştirme katmanı (MIL) statik olarak vuruşları işler.  
  
    3.  <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Görselleri temizler.
