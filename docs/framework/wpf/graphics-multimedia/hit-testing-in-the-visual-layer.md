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
ms.openlocfilehash: 28ae983923c985050ac589166023e483721028d3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452623"
---
# <a name="hit-testing-in-the-visual-layer"></a>Görsel Katmanda Tıklama Testi
Bu konuda, görsel katman tarafından sağlanan isabet sınama işlevselliğine genel bir bakış sağlanır. İsabet testi desteği, bir geometri veya nokta değerinin bir <xref:System.Windows.Media.Visual>işlenmiş içeriği dahilinde olup olmadığını belirlemenizi sağlar. bu sayede, birden çok nesne seçmek için seçim dikdörtgeni gibi kullanıcı arabirimi davranışlarını uygulamanıza olanak tanır.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>İsabet testi senaryoları  
 <xref:System.Windows.UIElement> sınıfı, belirli bir koordinat değeri kullanarak bir öğeye karşı test 'e isabet etmenizi sağlayan <xref:System.Windows.UIElement.InputHitTest%2A> yöntemini sağlar. Birçok durumda <xref:System.Windows.UIElement.InputHitTest%2A> yöntemi, öğelerin isabet sınamasını uygulamak için istenen işlevselliği sağlar. Ancak, görsel katmanda isabet sınamasını uygulamanız gerekebilecek birkaç senaryo vardır.  
  
- <xref:System.Windows.UIElement> olmayan nesnelere karşı isabet testi: Bu, <xref:System.Windows.Media.DrawingVisual> veya grafik nesneleri gibi<xref:System.Windows.UIElement> olmayan nesneleri isabet ediyorsanız geçerlidir.  
  
- Geometri kullanarak isabet testi: Bu, bir noktanın koordinat değeri yerine bir geometri nesnesi kullanarak isabet etmeniz gerekiyorsa geçerlidir.  
  
- Birden çok nesneye karşı isabet testi: Bu, örtüşen nesneler gibi birden çok nesneye karşı test için isabet etmeniz gerektiğinde geçerlidir. Yalnızca ilki değil, bir geometriyi veya noktası kesişen tüm görsellerin sonuçlarını elde edebilirsiniz.  
  
- <xref:System.Windows.UIElement> isabet testi ilkesi yoksayılıyor: Bu, bir öğenin devre dışı veya görünmez olması gibi etkenlere göz önünde bulundurarak, <xref:System.Windows.UIElement> hit test ilkesini gözardı etmeniz gerektiğinde geçerlidir.  
  
> [!NOTE]
> Görsel katmandaki isabet sınamasını gösteren bir kod örneği için, bkz. [Drawinggörseller örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) ve [Win32 birlikte çalışabilirlik örneği ile isabet testi](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>İsabet testi desteği  
 <xref:System.Windows.Media.VisualTreeHelper> sınıfındaki <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemlerinin amacı, bir geometri veya nokta koordinat değerinin bir denetim veya grafik öğesi gibi belirli bir nesnenin işlenmiş içeriği içinde olup olmadığını belirlemektir. Örneğin, bir nesnenin sınırlayıcı dikdörtgeninin içindeki bir fare tıklaması bir dairenin geometrisi dahilinde olup olmadığını anlamak için isabet sınamasını kullanabilirsiniz. Ayrıca, kendi özel isabet testi hesaplamalarınızı gerçekleştirmek için isabet sınamasının varsayılan uygulamasını geçersiz kılmayı da tercih edebilirsiniz.  
  
 Aşağıdaki çizimde, dikdörtgen olmayan bir nesnenin bölgesi ve onun sınırlayıcı dikdörtgeni arasındaki ilişki gösterilmektedir.  
  
 ![Geçerli isabet testi bölgesinin diyagramı](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Geçerli isabet testi bölgesinin diyagramı  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>İsabet testi ve Z düzeni  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] görsel katmanı yalnızca en üstteki nesnenin değil, bir nokta veya geometri altındaki tüm nesneler için isabet sınamasını destekler. Sonuçlar z düzeninde döndürülür. Ancak, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemine parametre olarak geçirdiğiniz görsel nesne, görsel ağacın hangi bölümünü isabet testi olacak şekilde belirler. Test için görsel ağacın tamamına veya herhangi bir bölümüne kadar isabet edebilirsiniz.  
  
 Aşağıdaki çizimde, Circle nesnesi hem Square hem de Triangle nesnelerinin üstünde yer alır. Yalnızca z sırası değeri en fazla olan görsel nesne isabet testi ile ilgileniyorsanız, ilk öğeden sonra gelen isabet testi geçişini durdurmak için, görsel isabet testi numaralandırmayı <xref:System.Windows.Media.HitTestResultCallback> <xref:System.Windows.Media.HitTestResultBehavior.Stop> döndürecek şekilde ayarlayabilirsiniz.  
  
 ![Görsel ağacın z&#45;sırasının diyagramı](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Görsel ağacın z düzeni diyagramı  
  
 Belirli bir nokta veya geometri altındaki tüm görsel nesneleri numaralandırmak istiyorsanız <xref:System.Windows.Media.HitTestResultCallback><xref:System.Windows.Media.HitTestResultBehavior.Continue> döndürün. Bu, tamamen görünmez olsalar bile diğer nesnelerin altında bulunan görsel nesneler için isabet testi yapabilirsiniz. Daha fazla bilgi için "Isabet Test Sonuçları geri çağırma kullanma" bölümündeki örnek koda bakın.  
  
> [!NOTE]
> Saydam bir görsel nesne Ayrıca isabet testi de alabilir.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Varsayılan Isabet sınamasını kullanma  
 Bir noktanın görsel nesne geometrisi dahilinde olup olmadığını, bir görsel nesne ve test edilecek bir nokta koordinat değeri belirtmek için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodunu kullanarak tanımlayabilirsiniz. Görsel nesne parametresi, isabet testi araması için görsel ağaçtaki başlangıç noktasını tanımlar. Görsel ağaçta geometrisi koordinat içeren bir görsel nesne bulunursa, bir <xref:System.Windows.Media.HitTestResult> nesnesinin <xref:System.Windows.Media.HitTestResult.VisualHit%2A> özelliğine ayarlanır. <xref:System.Windows.Media.HitTestResult> sonra <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yönteminden döndürülür. Nokta, isabet testi yaptığınız görsel alt ağaçta yer alıyorsa, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> `null`döndürür.  
  
> [!NOTE]
> Varsayılan isabet testi her zaman z düzeninde en üstteki nesneyi döndürür. Kısmen veya tamamen görünmez olsalar bile tüm görsel nesneleri tanımlamak için bir isabet testi sonucu geri çağırması kullanın.  
  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi için Point parametresi olarak geçirdiğiniz koordinat değeri, isabet testi yaptığınız görsel nesnenin koordinat alanına göre olmalıdır. Örneğin, üst öğe koordinat alanında (100, 100) içinde tanımlanmış iç içe görsel nesneleriniz varsa, (0, 0) konumundaki bir alt görsel için isabet testi, üst öğenin koordinat alanında (100, 100) ile eşdeğerdir.  
  
 Aşağıdaki kod, isabet testi için kullanılan olayları yakalamak için kullanılan bir <xref:System.Windows.UIElement> nesnesi için fare olay işleyicilerini ayarlamayı gösterir.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Görsel ağaç Isabet sınamasını nasıl etkiler  
 Görsel ağaçtaki başlangıç noktası, nesnelerin isabet testi numaralandırması sırasında hangi nesnelerin döndürüleceğini belirler. Test etmek istediğiniz birden çok nesneniz varsa, görsel ağaçtaki başlangıç noktası olarak kullanılan görsel nesne, tüm ilgilendiğiniz nesnelerin ortak üst öğesi olmalıdır. Örneğin, aşağıdaki diyagramda hem düğme öğesi hem de çizim görseli isabet testi ile ilgileniyorsanız, görsel ağaçtaki başlangıç noktasını her ikisinin de ortak üst öğesine ayarlamanız gerekir. Bu durumda, tuval öğesi hem düğme öğesinin hem de çizim görselin ortak üst öğesidir.  
  
 ![Görsel ağaç hiyerarşisinin diyagramı](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Görsel ağaç hiyerarşisinin diyagramı  
  
> [!NOTE]
> <xref:System.Windows.UIElement.IsHitTestVisible%2A> özelliği, <xref:System.Windows.UIElement>türetilmiş bir nesnenin, işlenen içeriğinin bir bölümünden bir isabet testi sonucu olarak döndürülüp döndürülmeyeceğini bildiren bir değer alır veya ayarlar. Bu, bir isabet testinde hangi görsel nesnelerin dahil olduğunu belirleyebilmek için görsel ağacı seçmeli olarak değiştirmenize olanak sağlar.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>Isabet testi sonucu geri çağırma kullanma  
 Geometrisi, belirtilen koordinat değeri içeren bir görsel ağaçtaki tüm görsel nesneleri numaralandırabilirsiniz. Bu, diğer görsel nesneler tarafından kısmen veya tamamen görünmeyebilir bile tüm görsel nesneleri tanımlamanızı sağlar. Görsel ağaçtaki görsel nesneleri numaralandırmak için, bir isabet testi geri çağırma işleviyle birlikte <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi kullanın. Belirttiğiniz koordinat değeri görsel bir nesne içine dahil edildiğinde, isabet testi geri çağırma işlevi sistem tarafından çağırılır.  
  
 İsabet testi sonuçları numaralandırması sırasında, görsel ağacı değiştiren herhangi bir işlem gerçekleştirmemelisiniz. Bir nesne, çapraz aktarılırken görsel ağaca eklendiğinde veya kaldırıldığında öngörülemeyen davranışlara neden olabilir. <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi döndüğünde görsel ağacı güvenle değiştirebilirsiniz. İsabet test sonuçları numaralandırması sırasında değerleri depolamak için <xref:System.Collections.ArrayList>gibi bir veri yapısı sağlamak isteyebilirsiniz.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 İsabet testi geri çağırma yöntemi, görsel ağaçtaki belirli bir görsel nesne üzerinde bir isabet testi tanımlandığında gerçekleştirdiğiniz eylemleri tanımlar. Eylemleri gerçekleştirdikten sonra, diğer görsel nesnelerin numaralandırılmasına devam edilip edilmeyeceğini belirleyen <xref:System.Windows.Media.HitTestResultBehavior> bir değer döndürür.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
> İsabet görsel nesnelerinin numaralandırılma sırası z düzeninde olur. En üstteki z sırası düzeyindeki görsel nesne, numaralandırılan ilk nesnedir. Numaralandırılmış diğer görsel nesneler, sırasıyla z sırası düzeyindedir. Bu numaralandırma sırası görsellerin işleme sırasına karşılık gelir.  
  
 <xref:System.Windows.Media.HitTestResultBehavior.Stop>döndürerek, isabet testi geri arama işlevinde istediğiniz zaman görsel nesne numaralandırmayı durdurabilirsiniz.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Isabet testi filtresi geri çağırma kullanma  
 İsabet testi sonuçlarına geçirilen nesneleri kısıtlamak için isteğe bağlı bir isabet testi filtresi kullanabilirsiniz. Bu, isabet testi sonuçlarınızda işleme ilgilenmediğiniz görsel ağacın parçalarını yoksaymasına olanak tanır. Bir isabet testi filtresi uygulamak için, bir isabet testi filtresi geri çağırma işlevini tanımlar ve <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemini çağırdığınızda bir parametre değeri olarak geçitirsiniz.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 İsteğe bağlı isabet testi filtresi geri çağırma işlevini sağlamak istemiyorsanız, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi için parametresi olarak bir `null` değeri geçirin.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![İsabet testi filtresi kullanarak görsel ağacı ayıklama](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Görsel ağacı ayıklama  
  
 İsabet testi filtresi geri çağırma işlevi, işlenmiş içeriği belirttiğiniz koordinatları içeren tüm görseller arasında listeleme yapmanıza olanak sağlar. Ancak, isabet test sonuçları geri arama işlevinizde işlemeyle ilgilenmediğiniz görsel ağacın belirli dallarını yok saymanız gerekebilir. İsabet testi filtresi geri arama işlevinin dönüş değeri, görsel nesnelerin numaralandırılmasından ne tür bir eylemin yapılacağını belirler. Örneğin, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>değeri döndürürsanız, geçerli görsel nesneyi ve alt öğelerini isabet test sonuçları numaralandırmasından kaldırabilirsiniz. Bu, isabet testi sonuçları geri çağırma işlevinin Numaralandırmadaki bu nesneleri görmeyeceği anlamına gelir. Nesnelerin görsel ağacını ayıklama, isabet testi sonuçları numaralandırma geçişi sırasında işlem miktarını azaltır. Aşağıdaki kod örneğinde, filtre etiketleri ve bunların alt öğelerini atlar ve diğer her şey için isabet testi yapın.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
> İsabet testi filtresi geri çağırması bazen isabet test sonuçları geri çağrısının çağrılmaması durumunda çağrılabilir.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Varsayılan Isabet sınamasını geçersiz kılma  
 <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemini geçersiz kılarak bir görsel nesnenin varsayılan isabet testi desteğini geçersiz kılabilirsiniz. Bu, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemini çağırdığınızda geçersiz kılınan <xref:System.Windows.Media.Visual.HitTestCore%2A> uygulamanızın çağrıldığı anlamına gelir. Geçersiz kılınan yönteminiz, koordinat görsel nesnenin işlenmiş içeriğinin dışında olsa bile, bir isabet testi görsel nesnenin sınırlayıcı dikdörtgeni içinde yer alıyorsa çağrılır.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 Hem sınırlayıcı dikdörtgende hem de bir görsel nesnenin işlenmiş içeriğine karşı test etmek istediğiniz zamanlar olabilir. Geçersiz kılınamayan <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemdeki `PointHitTestParameters` parametre değerini temel yöntem <xref:System.Windows.Media.Visual.HitTestCore%2A>parametre olarak kullanarak, bir görsel nesnenin sınırlayıcı dikdörtgeninin bir vurmasına dayalı olarak eylemler gerçekleştirebilir ve ardından görsel nesnenin işlenmiş içeriğine karşı ikinci bir isabet testi yapabilirsiniz.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [Drawinggörselleri kullanarak isabet testi örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual)
- [Win32 birlikte çalışabilirlik örneğiyle isabet testi örneği](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Görselde Tıklama Testi Geometrisi](how-to-hit-test-geometry-in-a-visual.md)
- [Win32 Konak Kapsayıcısı Kullanan Tıklama Testi](how-to-hit-test-using-a-win32-host-container.md)
