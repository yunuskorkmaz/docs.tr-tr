---
title: Görsel Katmanda Tıklama Testi
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit testing functionality [WPF]
- visual layer [WPF], hit testing functionality
ms.assetid: b1a64b61-14be-4d75-b89a-5c67bebb2c7b
ms.openlocfilehash: d4d304353e91147c57297dcc4525759ff1474b4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186411"
---
# <a name="hit-testing-in-the-visual-layer"></a>Görsel Katmanda Tıklama Testi
Bu konu, görsel katman tarafından sağlanan isabet testi işlevselliği genel bir bakış sağlar. Hit test desteği, bir geometri nin veya nokta değerinin, birden <xref:System.Windows.Media.Visual>çok nesne seçmek için seçim dikdörtgeni gibi kullanıcı arabirimi davranışı uygulamanıza olanak tanıyan bir geometrinin veya nokta değerinin işlenmiş içeriğinde olup olmadığını belirlemenize olanak tanır.  

<a name="hit_testing_scenarios"></a>
## <a name="hit-testing-scenarios"></a>Hit Test Senaryoları  
 Sınıf, <xref:System.Windows.UIElement> belirli <xref:System.Windows.UIElement.InputHitTest%2A> bir koordinat değerini kullanarak bir öğeye karşı test vurmak için izin veren yöntemi sağlar. Çoğu durumda, <xref:System.Windows.UIElement.InputHitTest%2A> yöntem öğelerin isabet testi uygulamak için istenen işlevselliği sağlar. Ancak, görsel katmanda isabet testi uygulamanız gerekebileceği birkaç senaryo vardır.  
  
- <xref:System.Windows.UIElement> Nesne olmayanlara karşı vur testi: Bu, nesne olmayan<xref:System.Windows.UIElement> nesneleri <xref:System.Windows.Media.DrawingVisual> veya grafik nesneleri test isabet varsa geçerlidir.  
  
- Bir geometri kullanarak vurma testi: Bu, bir noktanın koordinat değeri yerine bir geometri nesnesi kullanarak test ehit gerekiyorsa geçerlidir.  
  
- Birden çok nesneye karşı vur testi: Bu, çakışan nesneler gibi birden çok nesneye karşı test tuşuna basmanız gerektiğinde geçerlidir. Sadece ilki değil, bir geometri veya noktayla kesişen tüm görseller için sonuç alabilirsiniz.  
  
- Isabet <xref:System.Windows.UIElement> testi ilkesini yok sayma: Bu, <xref:System.Windows.UIElement> bir öğenin devre dışı bırakılmış veya görünmez olup olmadığı gibi faktörleri dikkate alan isabet testi ilkesini yoksaymanız gerektiğinde geçerlidir.  
  
> [!NOTE]
> Görsel katmanda isabet testini gösteren tam bir kod örneği için, [Win32 İnteroperation Sample ile](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting) [DrawingVisuals Örnek](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) ve Hit Test kullanarak Hit Testi'ne bakın.  
  
<a name="hit_testing_support"></a>
## <a name="hit-testing-support"></a>Hit Test Desteği  
 Sınıftaki <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> <xref:System.Windows.Media.VisualTreeHelper> yöntemlerin amacı, bir geometri veya nokta koordinat değeri, denetim veya grafik öğesi gibi belirli bir nesnenin işlenen içeriği içinde olup olmadığını belirlemektir. Örneğin, bir nesnenin sınırlayıcı dikdörtgeni içindeki fare tıklamasının dairenin geometrisine düşüp düşmediğini belirlemek için isabet testi kullanabilirsiniz. Ayrıca, kendi özel isabet testi hesaplamalarınızı gerçekleştirmek için isabet testinin varsayılan uygulamasını geçersiz kılmayı da seçebilirsiniz.  
  
 Aşağıdaki resimde dikdörtgen olmayan bir nesnenin bölgesi ile sınırlayıcı dikdörtgeni arasındaki ilişki gösterilmektedir.  
  
 ![Geçerli isabet testi bölgesinin diyagramı](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Geçerli isabet testi bölgesinin diyagramı  
  
<a name="hit_testing_and_z-order"></a>
## <a name="hit-testing-and-z-order"></a>Hit Test ve Z-Order  
 Görsel [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] katman, yalnızca en üstteki nesneye değil, bir nokta veya geometri altındaki tüm nesnelere karşı isabet testini destekler. Sonuçlar z sırasına göre döndürülür. Ancak, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yönteme parametre olarak geçtiğiniz görsel nesne, işgöremezliğin hangi bölümünün test edileceğini belirler. Tüm görsel ağaca veya herhangi bir bölümüne karşı test vurabilirsiniz.  
  
 Aşağıdaki resimde, daire nesnesi hem kare hem de üçgen nesnelerin üstündedir. Yalnızca z-sıra değeri en üstte olan görsel nesneyi test etmekle ilgileniyorsanız, ilk öğeden <xref:System.Windows.Media.HitTestResultBehavior.Stop> sonra <xref:System.Windows.Media.HitTestResultCallback> isabet testi geçişini durdurmak için görsel isabet testi numaralandırmasını ayarlayabilirsiniz.  
  
 ![Görsel bir ağacın z&#45;sırası diyagramı](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Görsel bir ağacın z sırası diyagramı  
  
 Tüm görsel nesneleri belirli bir nokta veya geometri altında sayısallandırmak <xref:System.Windows.Media.HitTestResultCallback>istiyorsanız, 'den dön. <xref:System.Windows.Media.HitTestResultBehavior.Continue> Bu, tamamen gizlenmiş olsalar bile, diğer nesnelerin altında olan görsel nesneler için test tuşuna basabileceğiniz anlamına gelir. Daha fazla bilgi için "Hit Test Sonuçları Geri Aramasını Kullanma" bölümündeki örnek koda bakın.  
  
> [!NOTE]
> Saydam olan görsel bir nesne de test isabet olabilir.  
  
<a name="using_default_hit_testing"></a>
## <a name="using-default-hit-testing"></a>Varsayılan Isabet Testini Kullanma  
 Görsel bir nesne ve karşı sınamak için bir nokta <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> koordinat değeri belirtmek için yöntemi kullanarak, bir nokta görsel bir nesnenin geometrisi içinde olup olmadığını belirleyebilirsiniz. Görsel nesne parametresi, isabet testi araması için görsel ağaçtaki başlangıç noktasını tanımlar. Geometrisi koordinatı içeren görsel ağaçta görsel bir nesne bulunursa, <xref:System.Windows.Media.HitTestResult.VisualHit%2A> <xref:System.Windows.Media.HitTestResult> nesnenin özelliğine ayarlanır. Daha <xref:System.Windows.Media.HitTestResult> sonra <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemden döndürülür. Nokta görsel alt ağaç ile içermiyorsa test <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> isabet, döndürür. `null`  
  
> [!NOTE]
> Varsayılan isabet testi her zaman z sırasına göre en üstteki nesneyi döndürür. Tüm görsel nesneleri tanımlamak için, kısmen veya tamamen gizlenmiş olanlar bile, bir isabet testi sonucu geri arama kullanın.  
  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> Yöntemiçin nokta parametresi olarak geçtiğiniz koordinat değeri, test ettiğiniz görsel nesnenin koordinat alanına göre olmalıdır. Örneğin, ebeveynin koordinat alanında (100, 100) tanımlanan görsel nesneler içinde yse, (0, 0) ile bir alt güngörsel teste basmak, ebeveynin koordinat uzağındaki (100, 100) hit sınırlamaya eşdeğerdir.  
  
 Aşağıdaki kod, isabet testi için kullanılan olayları <xref:System.Windows.UIElement> yakalamak için kullanılan bir nesne için fare olay işleyicilerinin nasıl ayarlanır olduğunu gösterir.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Görsel Ağaç Hit Testini Nasıl Etkiler?  
 Görsel ağaçtaki başlangıç noktası, nesnelerin isabet testi numaralandırması sırasında hangi nesnelerin döndürülderken döndürülderken belirler. Teste vurmak istediğiniz birden çok nesne varsa, görsel ağaçta başlangıç noktası olarak kullanılan görsel nesne, ilgi çeken tüm nesnelerin ortak atası olmalıdır. Örneğin, aşağıdaki diyagramda hem düğme öğesini hem de görsel çizimi test etmek istiyorsanız, görsel ağaçtaki başlangıç noktasını her ikisinin de ortak atasına ayarlamanız gerekir. Bu durumda, tuval öğesi hem düğme öğesinin hem de görsel çizimin ortak atasıdır.  
  
 ![Görsel ağaç hiyerarşisi diyagramı](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Görsel ağaç hiyerarşisi diyagramı  
  
> [!NOTE]
> Özellik, <xref:System.Windows.UIElement.IsHitTestVisible%2A> türetilmiş bir <xref:System.Windows.UIElement>nesnenin, işlenen içeriğinin bir bölümünden isabet testi sonucu olarak döndürülebileceğini bildiren bir değer alır veya ayarlar. Bu, isabet testinde hangi görsel nesnelerin yer aldığını belirlemek için görsel ağacı seçerek değiştirmenize olanak tanır.  
  
<a name="using_a_hit_test_result_callback"></a>
## <a name="using-a-hit-test-result-callback"></a>Hit Test Sonucu Geri Arama Kullanma  
 Geometrisi belirli bir koordinat değeri içeren görsel bir ağaçtaki tüm görsel nesneleri sayısalatabilirsiniz. Bu, diğer görsel nesneler tarafından kısmen veya tamamen gizlenmiş olabilecek tüm görsel nesneleri, hatta tüm görsel nesneleri tanımlamanızı sağlar. Görsel bir ağaçtaki görsel nesneleri sayısallandırmak <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> için, isabet testi geri arama işleviyle yöntemi kullanın. Belirttiğiniz koordinat değeri görsel bir nesnede bulunduğunda, isabet testi geri arama işlevi sistem tarafından çağrılır.  
  
 Hit test sonuçları numaralandırma sırasında, görsel ağacı değiştiren herhangi bir işlem yapmamalısınız. Bir nesnenin geçilirken görsel ağaçtan eklenmesi veya çıkarılması öngörülemeyen davranışlara neden olabilir. <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> Yöntem döndükten sonra görsel ağacı güvenle değiştirebilirsiniz. Hit test sonuçları numaralandırması sırasında <xref:System.Collections.ArrayList>değerleri depolamak için bir veri yapısı sağlamak isteyebilirsiniz.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 Isabet testi geri arama yöntemi, görsel ağaçtaki belirli bir görsel nesne üzerinde isabet testi tanımlandığında gerçekleştirdiğiniz eylemleri tanımlar. Eylemleri gerçekleştirdikten sonra, diğer <xref:System.Windows.Media.HitTestResultBehavior> görsel nesnelerin numaralandırmasına devam edip etmeyeceğini belirleyen bir değer döndürün.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> Isabet eden görsel nesnelerin numaralandırma sırası z-sırasına göredir. En üstteki z-sıra düzeyindeki görsel nesne numaralandırılmış ilk nesnedir. Numaralandırılmış diğer görsel nesneler z-sıra düzeyi azalır. Bu numaralandırma sırası görsellerin işleme sırasına karşılık gelir.  
  
 Görsel nesnelerin numaralandırmasını, isabet testi geri arama işlevinde istediğiniz zaman döndürerek <xref:System.Windows.Media.HitTestResultBehavior.Stop>durdurabilirsiniz.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>
## <a name="using-a-hit-test-filter-callback"></a>Hit Test Filtresi Geri Arama Kullanma  
 Isabet testi sonuçlarına geçirilen nesneleri kısıtlamak için isteğe bağlı isabet testi filtresi kullanabilirsiniz. Bu, isabet test sonuçlarınızda işlemekle ilgilenmediğiniz görsel ağacın bölümlerini yoksaymanızı sağlar. Isabet testi filtresi uygulamak için, bir isabet testi filtresi geri arama işlevi tanımlar ve <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi aradığınızda bir parametre değeri olarak geçersiniz.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 İsteğe bağlı isabet testi filtresi geri arama işlevini sağlamak `null` istemiyorsanız, yöntem <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> için parametresi olarak bir değer geçirin.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![Isabet testi filtresi kullanarak görsel bir ağacı budama](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Görsel bir ağacı budama  
  
 Hit test filtresi geri arama işlevi, işlenen içeriği belirttiğiniz koordinatları içeren tüm görselleri ayarlamanızı sağlar. Ancak, isabet test sonuçları geri arama işleviişleme ilgilenmiyor görsel ağacın belirli dalları yoksaymak isteyebilirsiniz. Isabet testi filtresi geri arama işlevinin geri dönüş değeri, görsel nesnelerin numaralandırmasının ne tür bir eylem alması gerektiğini belirler. Örneğin, değeri döndürünürseniz, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>geçerli görsel nesneyi ve onun çocuklarını isabet testi sonuçları numaralandırmasından kaldırabilirsiniz. Bu, isabet testi sonuçları geri arama işlevinin bu nesneleri numaralandırmasında görmeyeceğim anlamına gelir. Nesnelerin görsel ağacı budama isabet test sonuçları numaralandırma geçiş sırasında işlem miktarını azaltır. Aşağıdaki kod örneğinde, filtre etiketleri ve onların torunlarını atlar ve hit diğer her şeyi sınar.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> Hit test filtresi geri arama bazen hit test sonuçları geri arama çağrılmadığını durumlarda çağrılır.  
  
<a name="overriding_default_hit_testing"></a>
## <a name="overriding-default-hit-testing"></a>Varsayılan Isabet Testini Geçersiz Kılma  
 <xref:System.Windows.Media.Visual.HitTestCore%2A> Yöntemi geçersiz kılarak görsel bir nesnenin varsayılan isabet testi desteğini geçersiz kılabilirsiniz. Bu, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi çağırdığınızda, geçersiz kılınan uygulamanın <xref:System.Windows.Media.Visual.HitTestCore%2A> çağrılması anlamına gelir. Bir isabet testi görsel nesnenin sınırlayıcı dikdörtgen içine düştüğünde, koordinat görsel nesnenin işlenen içeriğinin dışına düşse bile, geçersiz kılınan yönteme denir.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Hem sınırlayan dikdörtgen hem de görsel bir nesnenin işlenen içeriğine karşı test vurmak istediğiniz zamanlar olabilir. Geçersiz kılınan `PointHitTestParameters` <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemdeki parametre değerini temel yönteme <xref:System.Windows.Media.Visual.HitTestCore%2A>parametre olarak kullanarak, görsel nesnenin sınırlayan dikdörtgeninin çarpmasına dayalı eylemleri gerçekleştirebilir ve ardından görsel nesnenin işlenen içeriğine karşı ikinci bir isabet testi gerçekleştirebilirsiniz.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Çizim Görselleri Örnek Kullanarak Test Hit](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Win32 İnterİşleme Örneği ile Vur Testi](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Görselde Tıklama Testi Geometrisi](how-to-hit-test-geometry-in-a-visual.md)
- [Win32 Konak Kapsayıcısı Kullanan Tıklama Testi](how-to-hit-test-using-a-win32-host-container.md)
