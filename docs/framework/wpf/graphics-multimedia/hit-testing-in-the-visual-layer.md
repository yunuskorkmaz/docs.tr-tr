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
ms.openlocfilehash: 0cb8d0656765e5bc2c2a54ef5f282a67d8579f20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762467"
---
# <a name="hit-testing-in-the-visual-layer"></a>Görsel Katmanda Tıklama Testi
Bu konu, isabet testi işlevi görsel katman tarafından sağlanan genel bir bakış sağlar. İsabet sınaması desteği sayesinde geometri veya nokta değerinin işlenmiş içeriği içinde olup olmadığını belirlemek bir <xref:System.Windows.Media.Visual>, birden çok nesne seçmek için seçim dikdörtgeninin gibi kullanıcı arabirimi davranışı uygulamak etmenize imkan sağlar.  

<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>İsabet sınaması senaryoları  
 <xref:System.Windows.UIElement> Sağlar sınıfını <xref:System.Windows.UIElement.InputHitTest%2A> isabet sınaması bir belirtilen koordinat değeri kullanarak bir öğe olanak tanıyan yöntemi. Çoğu durumda, <xref:System.Windows.UIElement.InputHitTest%2A> yöntemi uygulamak için isabet sınaması öğeleri istenen işlevselliği sağlar. Ancak, görsel katmanda isabet sınaması uygulamak gerekebilir çeşitli senaryolar vardır.  
  
- İsabet sınaması olmayan<xref:System.Windows.UIElement> nesneler: Test olmayan isabet durumunda geçerlidir<xref:System.Windows.UIElement> gibi nesneleri <xref:System.Windows.Media.DrawingVisual> veya grafik nesneleri.  
  
- İsabet sınaması bir geometri kullanarak: İsabet sınaması bir noktanın koordinat değeri yerine geometri nesnesi gerekiyorsa bu geçerlidir.  
  
- Birden çok nesne için isabet sınaması: İsabet testi nesneleri çakışan gibi birden çok nesneyi karşı gerektiğinde bu geçerlidir. Geometri veya noktası, yalnızca ilki kesişen tüm görseller için sonuçlar alabilirsiniz.  
  
- Yoksayma <xref:System.Windows.UIElement> isabet sınaması İlkesi: Yok saymak gerektiğinde bu geçerlidir <xref:System.Windows.UIElement> isabet sınaması bir öğe devre dışı olup olmadığını veya görünmez gibi Etkenler dikkate alan ilkesi.  
  
> [!NOTE]
>  Görsel katmanda test isabet gösteren tam bir kod örneği için bkz: [isabet sınaması örneği kullanarak Test isabet](https://go.microsoft.com/fwlink/?LinkID=159994) ve [Win32 birlikte çalışması örnek ile isabet sınaması](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>İsabet sınaması desteği  
 Amacı <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemleri <xref:System.Windows.Media.VisualTreeHelper> sınıfı, geometri veya nokta bir koordinat değeri işlenen içeriğinin bir denetim veya grafik öğesi gibi belirli bir nesne içinde olup olmadığını belirlemek için. Örneğin, bir nesnenin sınırlayıcı dikdörtgeni içinde bir fare tıklaması geometrisini bir daire içinde olup olmadığını belirlemek için isabet sınaması kullanabilirsiniz. Varsayılan uygulama, kendi özel isabet sınaması hesaplamalar gerçekleştirmek için isabet testi geçersiz kılmayı seçebilirsiniz.  
  
 Aşağıdaki çizim bir dikdörtgen olmayan nesnenin bölge ve onun sınırlayıcı dikdörtgeni arasındaki ilişkiyi gösterir.  
  
 ![Geçerli isabet sınaması bölge diyagramı](./media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Geçerli isabet sınaması bölge diyagramı  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>İsabet sınaması ve Z düzeni  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Görsel katman destekleyen bir nokta veya geometri, yalnızca en üstteki nesnesini altındaki tüm nesneleri için isabet sınaması. Sonuçları z düzeninde döndürülür. Ancak, parametre olarak geçen görsel nesne <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi hangi bölümünün belirler, isabet görsel ağacını test. İsabet sınaması görsel ağacın tamamı ya da bunu.  
  
 Aşağıdaki çizimde, kare ve üçgen nesneler üzerinde daire nesnedir. Yalnızca en üst z düzenini değeri olan visual nesne ilgileniyorsanız, döndürülecek görsel isabet sınaması sabit ayarlayabilirsiniz <xref:System.Windows.Media.HitTestResultBehavior.Stop> gelen <xref:System.Windows.Media.HitTestResultCallback> isabet sınaması geçişi ilk öğeden sonra durdurmak için.  
  
 ![Z diyagramı&#45;görsel ağacı sırasını](./media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Z düzenini görsel ağacın diyagramı  
  
 Tüm görsel nesneler belirli bir nokta veya geometri altında listeleme istiyorsanız, iade <xref:System.Windows.Media.HitTestResultBehavior.Continue> gelen <xref:System.Windows.Media.HitTestResultCallback>. Bu tamamen engellediği bile test diğer nesneler, görsel nesneler için isabet anlamına gelir. Örnek kod ' % s'bölümünde "Kullanarak bir isabet sınaması geri aramalarını" daha fazla bilgi için bkz.  
  
> [!NOTE]
>  Saydam bir görsel nesneyi de ulaşmasını test edin.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Varsayılan olarak kullanan tıklama testi  
 Bir noktayı kullanarak görsel bir nesnenin geometrisini içinde olup olmadığını belirleyebilir <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> görsel bir nesne ve bir nokta koordine karşı test etmek için bir değer belirtmek için yöntemi. Görsel ağaç isabet sınaması arama için başlangıç noktası visual nesne parametresi tanımlar. Bir görsel nesneyi geometrisi koordinat içeren görsel ağaçta bulunursa ayarlanmış <xref:System.Windows.Media.HitTestResult.VisualHit%2A> özelliği bir <xref:System.Windows.Media.HitTestResult> nesne. <xref:System.Windows.Media.HitTestResult> Öğesinden sonra döndürülen <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi. Eğer isabet sınaması, görsel alt ağacı noktası bulunmuyorsa <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> döndürür `null`.  
  
> [!NOTE]
>  Varsayılan isabet sınaması her zaman z düzeninde en üstteki nesnesini döndürür. Kısmen veya tamamen görünmeyebilir, bu da tüm visual nesneleri tanımlamak için isabet testi sonucu olan bir geri çağırma kullanın.  
  
 Nokta parametresi için geçirdiğiniz koordinat değeri <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> koordinat isabet sınaması bir görsel nesneyi göreli olarak yöntemi vardır. İç içe gibi görsel nesneler tanımlanmaz (100, 100) üst öğenin koordinat alanda ardından isabet sınaması alt (0, 0) isabet sınaması sırasında eşdeğerdir (100, 100), üst öğenin koordinat.  
  
 Aşağıdaki kod, fare olay işleyicilerini ayarlama işlemi gösterilmektedir bir <xref:System.Windows.UIElement> için kullanılan olaylarını yakalamak için kullanılan nesne isabet sınaması.  
  
 [!code-csharp[HitTestingOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Görsel ağacı nasıl etkilediğini tıklama testi  
 Hangi nesnelerin nesneleri isabet sınaması numaralandırma sırasında döndürülür görsel ağaç başlangıç noktasını belirler. İsabet sınaması istediğiniz birden fazla nesneniz varsa, ilgilendiğiniz tüm nesnelerin ortak üst görsel ağaç başlangıç noktası olarak kullanılan visual nesne olmalıdır. Örneğin, düğme öğesi test etme ve aşağıdaki diyagramda görsel çizimi isabet ilginizi, başlangıç noktası görsel ağaçta üst aynı hem ayarlamak gerekir. Bu durumda, tuval düğme öğesi hem görsel çizim ortak üst öğedir.  
  
 ![Bir görsel ağacı hiyerarşi diyagramı](./media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Bir görsel ağacı hiyerarşi diyagramı  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Özelliği alır veya ayarlar bildiren bir değer olup olmadığını bir <xref:System.Windows.UIElement>-türetilmiş nesne büyük olasılıkla döndürülmesi tıklama testi sonucu olarak, işlenen içeriğinin bazı kısımlarından. Bu, hangi görsel nesneler bir isabet testi katılan belirlemek için görsel ağacı seçerek değiştirmeyi sağlar.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>İsabet testi sonucu olan bir geri arama kullanma  
 Tüm görsel nesneler geometrisi belirtilen koordinat değeri içeren bir görsel ağaç sıralayabilirsiniz. Bu, tüm görsel nesneleri tanımlamak için diğer görsel nesneler tarafından kısmen veya tamamen görünmeyebilir da sağlar. Bir görsel ağacı kullanımda görsel nesneler numaralandırılamadı <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi ile bir isabet sınaması geri çağırma işlevi. İsabet sınaması geri çağırma işlevi, belirttiğiniz koordinat değeri görsel bir nesnede bulunan sistem tarafından çağrılır.  
  
 Sonuçları numaralandırma sırasında isabet testi, görsel ağacı değiştiren herhangi bir işlem gerçekleştirmemelisiniz. Ekleme veya bu denetlenirken bir nesne görsel ağaç'tan kaldırma beklenmeyen davranışlara neden olabilir. Sonra görsel ağacı güvenli bir şekilde değiştirebilirsiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi döndürür. Bir veri yapısı gibi sağlamak isteyebilirsiniz bir <xref:System.Collections.ArrayList>isabet testi sonuçlarını numaralandırma sırasında değerlerini depolamak için.  
  
 [!code-csharp[HitTestingOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 İsabet sınaması geri çağırma yöntemi, belirli bir görsel nesneyi görsel ağaç'üzerinde bir isabet sınaması tanımlandığında gerçekleştirdiğiniz eylemleri tanımlar. Eylemleri gerçekleştirdikten sonra dönüş bir <xref:System.Windows.Media.HitTestResultBehavior> herhangi bir görsel nesneler listelenmeye devam edilip edilmeyeceğini belirleyen bir değer.  
  
 [!code-csharp[HitTestingOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Z sırasına göre İsabet görsel nesnelerinin numaralandırması sırasıdır. Görsel nesneyi z düzenini en üst düzeyinde numaralandırılan ilk nesnedir. Numaralandırılan diğer görsel nesneler daha alt z düzenini düzeyindedir. Bu sabit listesi sırası için işleme sırası görsellerin karşılık gelir.  
  
 Görsel nesneler sabit listesi isabet sınaması geri çağırma işlevi herhangi bir zamanda döndürerek durdurabilirsiniz <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>Bir isabet sınaması filtre geri araması kullanma  
 İsabet testi sonuçları geçirilen nesneleri kısıtlamak için isteğe bağlı bir isabet sınaması bir filtre kullanabilirsiniz. Bu, isabet testi sonuçlarınızı işlemede ilgilendiğiniz değil görsel ağacı parçalarını yok saymasını sağlar. Bir isabet sınaması filtre uygulamak için bir isabet sınaması filtre geri çağırma işlevi tanımlayın ve çağırdığınızda parametre değeri olarak geçirin. <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi.  
  
 [!code-csharp[HitTestingOverview#104](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 İsteğe bağlı bir isabet sınaması filtre geri çağırma işlevi sağlamak istemiyorsanız, başarılı bir `null` için parametre olarak değer <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi.  
  
 [!code-csharp[HitTestingOverview#105](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![İsabet testi filtresini kullanarak görsel ağacı temizleme](./media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Görsel ağacı temizleme  
  
 İsabet testi filtre geri çağırma işlevi işlenmiş içeriği belirttiğiniz koordinatları içeren tüm Görsellere sıralamanızı sağlar. Ancak, bazı dalların, isabet test sonuçları geri çağırma işlevinizde işlemede ilgilendiğiniz değil görsel ağacı yoksay isteyebilirsiniz. İsabet testi filtre geri çağırma işlevi dönüş değeri, ne tür görsel nesneler numaralandırmasını eylemi gerçekleştirmesi gerektiğini belirler. Örneğin, dönüş değeri, <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, geçerli visual nesne ve alt öğelerindeki isabet testi sonuçları numaralandırmasından kaldırabilirsiniz. Bu, isabet test sonuçları geri çağırma işlevine bu nesneler, listedeki görmeyeceğiniz anlamına gelir. Görsel ağacı nesnelerin temizleme isabet testi sonuçlarını numaralandırma geçişi sırasında işleme miktarını azaltır. Aşağıdaki kod örneğinde, filtre etiketleri ve bunların alt öğeleri atlar ve diğer her şey isabet testleri.  
  
 [!code-csharp[HitTestingOverview#106](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  İsabet testi filtre geri araması bazen burada isabet sınaması geri aramalarını çağrılmaz durumlarda çağrılır.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Varsayılan geçersiz kılma tıklama testi  
 Görsel bir nesnenin varsayılan isabet sınama desteğini geçersiz kılarak geçersiz kılın <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemi. Bunun anlamı çağırdığınızda <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi, geçersiz kılınan uygulamanıza <xref:System.Windows.Media.Visual.HitTestCore%2A> çağrılır. İsabet sınaması görsel nesnenin sınırlayıcı dikdörtgenini içinde düştüğünde görsel nesne dışında işlenmiş içeriği koordinat olsa bile, geçersiz kılınan yöntemi çağrılır.  
  
 [!code-csharp[HitTestingOverview#107](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 İsabet sınaması dikdörtgen hem bir görsel nesneyi işlenmiş içeriği istediğiniz zaman zamanlar olabilir. Kullanarak `PointHitTestParameters` parametre değeri, geçersiz kılınan <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemi temel yöntemin parametre olarak <xref:System.Windows.Media.Visual.HitTestCore%2A>, görsel bir nesnenin sınırlayıcı dikdörtgenini isabet üzerinde temel eylemleri gerçekleştirin ve sonra ikinci bir isabet sınaması gerçekleştirin görsel nesnesinin içerik çizilir.  
  
 [!code-csharp[HitTestingOverview#108](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- <xref:System.Windows.Media.HitTestResult>
- <xref:System.Windows.Media.HitTestResultCallback>
- <xref:System.Windows.Media.HitTestFilterCallback>
- <xref:System.Windows.UIElement.IsHitTestVisible%2A>
- [İsabet sınaması örneği kullanan tıklama testi](https://go.microsoft.com/fwlink/?LinkID=159994)
- [İsabet testi ile Win32 birlikte çalışabilirlik örneği](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Görselde Tıklama Testi Geometrisi](how-to-hit-test-geometry-in-a-visual.md)
- [Win32 Konak Kapsayıcısı Kullanan Tıklama Testi](how-to-hit-test-using-a-win32-host-container.md)
