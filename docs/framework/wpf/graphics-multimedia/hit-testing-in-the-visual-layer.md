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
ms.openlocfilehash: 60da11af51722e86a61c5e3298fafba2221f000b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558115"
---
# <a name="hit-testing-in-the-visual-layer"></a>Görsel Katmanda Tıklama Testi
Bu konu görsel katman tarafından sağlanan isabet sınama işlevselliğine genel bir bakış sağlar. İsabet testi desteği sağlar, geometri veya nokta değerinin işlenmiş içeriği içinde olup olmadığını belirlemek bir <xref:System.Windows.Media.Visual>, birden çok nesne seçmek için seçim dikdörtgeninin gibi kullanıcı arabirimi davranışı uygulamak olanak sağlar.  
  
 
  
<a name="hit_testing_scenarios"></a>   
## <a name="hit-testing-scenarios"></a>İsabet sınaması senaryoları  
 <xref:System.Windows.UIElement> SAX <xref:System.Windows.UIElement.InputHitTest%2A> isabet koordinat değeri verilen kullanarak bir öğe sınaması olanak tanıyan yöntemi. Çoğu durumda, <xref:System.Windows.UIElement.InputHitTest%2A> yöntemi uygulama öğelerin isabet sınamalarının istenen işlevselliği sağlar. Ancak, görsel katmanda isabet testi uygulamak gerekebilir birkaç senaryo vardır.  
  
-   İsabet testi olmayan karşı<xref:System.Windows.UIElement> nesneleri: Test olmayan isabet durumunda geçerlidir<xref:System.Windows.UIElement> gibi nesneleri <xref:System.Windows.Media.DrawingVisual> veya grafik nesneleri.  
  
-   Geometri kullanılarak isabet sınaması: bir noktanın koordinat değeri yerine geometri nesnesi kullanan isabet testi gerekiyorsa bu geçerlidir.  
  
-   Birden çok nesne için isabet sınaması: isabet nesneleri çakışan gibi birden çok nesne sınaması gerektiğinde bu geçerlidir. Geometri veya nokta, yalnızca ilki kesen tüm görsel öğeler için sonuçlar alabilirsiniz.  
  
-   Yoksayılıyor <xref:System.Windows.UIElement> isabet ilke sınama: yoksay gerektiğinde bu geçerlidir <xref:System.Windows.UIElement> isabet gibi Etkenler olup bir öğenin devre dışı veya görünmez dikkate alır ilkeyi test etme.  
  
> [!NOTE]
>  Tam kod gösteren örnek İsabet görsel katmanda sınaması için bkz: [Test kullanarak isabet sınaması örneği isabet](http://go.microsoft.com/fwlink/?LinkID=159994) ve [isabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="hit_testing_support"></a>   
## <a name="hit-testing-support"></a>İsabet sınaması desteği  
 Amacı <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemleri <xref:System.Windows.Media.VisualTreeHelper> sınıftır geometri veya nokta koordinat değeri bir denetim ya da grafik öğesinin gibi belirli bir nesne işlenmiş içeriğinin içinde olup olmadığını belirlemek için. Örneğin, bir nesnenin sınırlayıcı dikdörtgenin içindeki fare tıklatma bir daire geometrisi içinde olup olmadığını belirlemek için isabet testi kullanabilirsiniz. Kendi özel isabet testi hesaplamalar için isabet sınama varsayılan uygulama geçersiz kılmak seçebilirsiniz.  
  
 Aşağıdaki çizimde bir dikdörtgen olmayan nesnenin bölgesi ve sınırlayıcı dikdörtgenini arasındaki ilişkiyi gösterir.  
  
 ![Geçerli isabet testi bölgesinin diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-1.png "wcpsdk_mmgraphics_visuals_hittest_1")  
Geçerli isabet testi bölgesinin diyagramı  
  
<a name="hit_testing_and_z-order"></a>   
## <a name="hit-testing-and-z-order"></a>İsabet testi ve Z düzeni  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Görsel katmanı destekleyen bir nokta veya geometri, yalnızca en üstteki nesne altındaki tüm nesneleri için vuruş sınaması. Sonuçlar z-sırası döndürülür. Ancak, parametre olarak geçirmek görsel nesne <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi hangi bölümünün belirler temas eder görsel ağaç test edin. Görsel ağacın tamamı veya bir bölümünün sınaması ziyaret.  
  
 Aşağıdaki çizimde, kare ve üçgen nesneler üzerinde daire nesnesidir. Yalnızca z düzeni değeri olan en üstteki visual nesne ilgileniyorsanız, döndürülecek visual isabet testi numaralandırması ayarlayabilirsiniz <xref:System.Windows.Media.HitTestResultBehavior.Stop> gelen <xref:System.Windows.Media.HitTestResultCallback> ilk öğeden sonra isabet testi geçişi durdurmak için.  
  
 ![Z diyagramı&#45;görsel ağaç sırasını](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-hittest-2.png "wcpsdk_mmgraphics_visuals_hittest_2")  
Görsel ağacın z düzeni diyagramı  
  
 Belirli bir nokta veya geometri altındaki tüm görsel nesneleri listeleme istiyorsanız, dönüş <xref:System.Windows.Media.HitTestResultBehavior.Continue> gelen <xref:System.Windows.Media.HitTestResultCallback>. Bu, tamamen yapılabileceği olsa bile diğer nesnelerin altında olan görsel nesneler için test isabet anlamına gelir. Daha fazla bilgi için "Kullanarak bir isabet testi sonuçları geri çağırma" bölümündeki örnek koduna bakın.  
  
> [!NOTE]
>  Saydam görsel bir nesne de isabet test edin.  
  
<a name="using_default_hit_testing"></a>   
## <a name="using-default-hit-testing"></a>Varsayılan isabet sınaması kullanma  
 Kullanarak bir noktası görsel bir nesne geometrisi içinde olup olmadığını tespit edebilirsiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi görsel bir nesne ve noktası koordine karşı test etmek için değer belirtin. Görsel nesne değişkeni görsel ağaç isabet testi arama için başlangıç noktası tanımlar. Görsel bir nesne, geometrisi koordinatını içeren görsel ağaçta bulunursa, ayarlanır <xref:System.Windows.Media.HitTestResult.VisualHit%2A> özelliği bir <xref:System.Windows.Media.HitTestResult> nesnesi. <xref:System.Windows.Media.HitTestResult> Öğesinden sonra döndürülen <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi. Noktası isabet testi, görsel alt ağaç bulunmuyorsa <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> döndürür `null`.  
  
> [!NOTE]
>  Varsayılan isabet sınaması her zaman en üstteki nesne z sırada döndürür. Kısmen veya tamamen görünmeyebilir, olanlar bile tüm görsel nesneleri tanımlamak için bir isabet testi sonuç geri kullanın.  
  
 Geçirdiğiniz noktası parametre olarak koordinat değeri <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi vardır isabet sınaması görsel nesnenin koordinat göreli olmalıdır. İç içe geçmiş, örneğin, görsel nesneler için tanımlanan (100, 100) üst öğenin koordinat alanında, ardından isabet alt sınaması (0, 0) eşdeğer bir gruba isabet adresindeki sınaması (100, 100) üst öğenin koordinat alanında.  
  
 Aşağıdaki kod için fare olay işleyicilerini ayarlama gösterilmektedir bir <xref:System.Windows.UIElement> için kullanılan olayları yakalamak için kullanılan nesne isabet testi.  
  
 [!code-csharp[HitTestingOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[HitTestingOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#100)]  
  
### <a name="how-the-visual-tree-affects-hit-testing"></a>Görsel ağaç etkilemesi isabet testi  
 Hangi nesnelerin nesneleri isabet testi numaralandırma sırasında döndürülür görsel ağaç başlangıç noktasını belirler. İsabet sınaması yapmak istediğiniz birden fazla nesne varsa, görsel ağaç başlangıç noktası olarak kullanılan görsel nesne ilgi tüm nesneleri için ortak Ata olması gerekir. Örneğin, hem düğme öğesi sınama ve aşağıdaki çizimde görsel çizimi isabet ilginizi olsaydı, başlangıç noktası görsel ağaçta ikisinin ortak bir üst kümesi gerekir. Bu durumda, tuvalin düğme öğesi ve görsel çizim ortak üst öğedir.  
  
 ![Görsel ağaç hiyerarşi diyagramı](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-mmgraphics-visuals-overview-01.gif "wcpsdk_mmgraphics_visuals_overview_01")  
Görsel ağaç hiyerarşi diyagramı  
  
> [!NOTE]
>  <xref:System.Windows.UIElement.IsHitTestVisible%2A> Özelliği alır veya ayarlar bildiren bir değer olup olmadığını bir <xref:System.Windows.UIElement>-türetilen nesne büyük olasılıkla döndürülüp döndürülmediğini isabet testi sonucu olarak işlenmiş içeriğinin bazı kısımlarından. Bu, seçmeli olarak hangi görsel nesnelerin bir isabet testi oynayan belirlemek için görsel ağaç alter olanak sağlar.  
  
<a name="using_a_hit_test_result_callback"></a>   
## <a name="using-a-hit-test-result-callback"></a>İsabet testi sonucu geri arama kullanma  
 Tüm görsel nesneleri geometrisi belirtilen bir koordinat değerini içeren bir görsel ağaç sıralayabilirsiniz. Bu, tüm görsel nesneleri tanımlamak için kısmen veya tamamen visual diğer nesneleri tarafından görünmeyebilir da sağlar. Görsel ağaç kullanımda görsel nesneleri numaralandırmak için <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi ile bir isabet testi geri çağırma işlevi. İsabet testi geri çağırma işlevi belirttiğiniz koordinat değeri görsel bir nesnede bulunan sistem tarafından çağırılır.  
  
 Sonuçları numaralandırma sırasında isabet testi, görsel ağacı değiştiren herhangi bir işlemi gerçekleştirmelisiniz değil. Ekleme veya onu denetlenirken bir nesneyi görsel ağaç kaldırma beklenmeyen davranışlara neden olabilir. Sonra görsel ağacı güvenle değiştirebilirsiniz <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi döndürür. Bir veri yapısı gibi sağlamak isteyebilirsiniz bir <xref:System.Collections.ArrayList>, isabet testi sonuçlarını numaralandırma sırasında değerlerini depolamak için.  
  
 [!code-csharp[HitTestingOverview#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[HitTestingOverview#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#101)]  
  
 İsabet testi geri çağırma yöntemi isabet testi görsel ağaç belirli bir görsel nesne üzerinde tanımlandığında gerçekleştirdiğiniz eylemleri tanımlar. Eylemleri gerçekleştirdikten sonra geri bir <xref:System.Windows.Media.HitTestResultBehavior> veya diğer görsel nesnelerin listesi devam edilip edilmeyeceğini belirleyen bir değer.  
  
 [!code-csharp[HitTestingOverview#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[HitTestingOverview#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#102)]  
  
> [!NOTE]
>  Z düzeni tarafından İsabet görsel nesnelerinin numaralandırması sırasıdır. Z düzeni en üst düzeyinde görsel nesne numaralandırılan ilk nesnesidir. Numaralandırılan diğer görsel nesneler daha alt z düzeni düzeyindedir. Bu numaralandırma sırasını görsel işleme sırasını karşılık gelir.  
  
 Görsel nesneler numaralandırması isabet testi geri arama işlevinde herhangi bir zamanda döndürerek durdurabilirsiniz <xref:System.Windows.Media.HitTestResultBehavior.Stop>.  
  
 [!code-csharp[HitTestingOverview#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#103)]
 [!code-vb[HitTestingOverview#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#103)]  
  
<a name="using_a_hit_test_filter_callback"></a>   
## <a name="using-a-hit-test-filter-callback"></a>İsabet testi filtresi geri arama kullanma  
 İsabet testi sonuçları geçirilen nesneleri kısıtlamak için bir isteğe bağlı isabet testi filtresini kullanabilirsiniz. Bu, isabet testi sonuçlarında işleme, ilgilendiğiniz değil görsel ağaç bölümlerini yoksay olanak sağlar. İsabet testi filtresi uygulamak için bir isabet sınama filtresi geri çağırma işlevini tanımlayın ve çağırdığınızda parametre değeri olarak geçirin <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi.  
  
 [!code-csharp[HitTestingOverview#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#104)]
 [!code-vb[HitTestingOverview#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#104)]  
  
 İsteğe bağlı isabet sınama filtresi geri çağırma işlevini sağlamak istemiyorsanız geçirmek bir `null` değeri, parametre olarak <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi.  
  
 [!code-csharp[HitTestingOverview#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#105)]
 [!code-vb[HitTestingOverview#105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#105)]  
  
 ![İsabet testi filtresini kullanarak görsel ağacı temizleme](../../../../docs/framework/wpf/graphics-multimedia/media/filteredvisualtree-01.png "FilteredVisualTree_01")  
Görsel ağacı temizleme  
  
 İsabet sınama filtresi geri çağırma işlevini işlenmiş içeriği belirlediğiniz koordinatları içeren tüm Görsellere Numaralandırılacak sağlar. Ancak, belirli, isabet testi sonuçları geri arama işlevinde işleme, ilgilendiğiniz değil görsel ağaç dallarını yoksay isteyebilirsiniz. İsabet testi filtre geri çağırma işlevinin dönüş değeri ne tür eylemi görsel nesnelerinin numaralandırması gerçekleştirmesi gerektiğini belirler. Örneğin, değer döndürürse <xref:System.Windows.Media.HitTestFilterBehavior.ContinueSkipSelfAndChildren>, geçerli görsel nesne ve alt öğelerini isabet testi sonuçlarını numaralandırma içinden kaldırabilirsiniz. Bu, isabet testi sonuçları geri çağırma işlevi bu nesneleri kendi numaralandırmasında göremeyeceği anlamına gelir. Nesnelerin görsel ağaç ayıklama isabet testi sonuçları numaralandırması geçişi sırasında işlem miktarını azaltır. Aşağıdaki kod örneğinde, etiketler ve bunların alt öğeleri filtre atlar ve isabet şey sınar.  
  
 [!code-csharp[HitTestingOverview#106](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#106)]
 [!code-vb[HitTestingOverview#106](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#106)]  
  
> [!NOTE]
>  İsabet testi filtre geri çağırma bazen burada isabet testi sonuçları geri çağırma çağrılmaz durumlarda çağrılır.  
  
<a name="overriding_default_hit_testing"></a>   
## <a name="overriding-default-hit-testing"></a>Varsayılan geçersiz kılma isabet testi  
 Görsel nesnenin varsayılan isabet sınama desteğini geçersiz kılarak geçersiz kılabilirsiniz <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemi. Bunun anlamı çağırdığınızda <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> yöntemi, geçersiz kılınan uygulamanıza <xref:System.Windows.Media.Visual.HitTestCore%2A> olarak adlandırılır. İsabet testi görsel nesne sınırlayıcı dikdörtgenini içinde düştüğünde koordinat görsel nesne işlenmiş içeriği dışında kalırsa bile, geçersiz kılınan yöntemi çağrılır.  
  
 [!code-csharp[HitTestingOverview#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#107)]
 [!code-vb[HitTestingOverview#107](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#107)]  
  
 İsabet sınırlayıcı dikdörtgenini ve görsel bir nesne işlenmiş içeriği sınaması istediğinizde zamanlar olabilir. Kullanarak `PointHitTestParameters` parametre değeri, geçersiz kılınan <xref:System.Windows.Media.Visual.HitTestCore%2A> yöntemi temel yöntemi için parametre olarak <xref:System.Windows.Media.Visual.HitTestCore%2A>, bir görsel nesnenin sınırlayıcı dikdörtgenini isabet üzerinde temel eylemleri gerçekleştirme ve ardından ikinci bir vuruş sınaması gerçekleştirin görsel nesnesinin içerik çizilir.  
  
 [!code-csharp[HitTestingOverview#108](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/Window1.xaml.cs#108)]
 [!code-vb[HitTestingOverview#108](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/window1.xaml.vb#108)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>  
 <xref:System.Windows.Media.HitTestResult>  
 <xref:System.Windows.Media.HitTestResultCallback>  
 <xref:System.Windows.Media.HitTestFilterCallback>  
 <xref:System.Windows.UIElement.IsHitTestVisible%2A>  
 [İsabet sınaması örnek kullanan isabet testi](http://go.microsoft.com/fwlink/?LinkID=159994)  
 [İsabet testi Win32 birlikte çalışabilirlik örneği ile](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Görselde Tıklama Testi Geometrisi](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)  
 [Win32 Konak Kapsayıcısı Kullanan Tıklama Testi](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-a-win32-host-container.md)
