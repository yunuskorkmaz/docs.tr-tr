---
title: Yapılandırılmış Gezintiye Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- structured navigation [WPF]
ms.assetid: 025d30ef-fec5-436d-ad7a-5d5483331c26
ms.openlocfilehash: 76330c1228b1f55a5dbaf58a1acd231a391d550c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580523"
---
# <a name="structured-navigation-overview"></a>Yapılandırılmış Gezintiye Genel Bakış

Bir [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)], <xref:System.Windows.Controls.Frame> veya <xref:System.Windows.Navigation.NavigationWindow> tarafından barındırılabilen içerikler, paket tekdüzen kaynak tanımlayıcıları (URI 'Ler) tarafından tanımlanabilen ve köprüler tarafından gezinilelebilen sayfalardan oluşur. Sayfaların yapısı ve köprüler tarafından tanımlandığı şekilde gezinilebilecekleri yollar, gezinti topolojisi olarak bilinir. Bu tür bir topoloji, özellikle belgelerde gezinenler gibi çeşitli uygulama türlerine uygun değildir. Bu tür uygulamalar için, Kullanıcı bir sayfadan diğerine kadar herhangi bir şeyi bilmeleri gerekmeden başka bir sayfaya gidebilir.

Ancak, diğer uygulama türleri arasında gezindikleri zaman bilmeleri gereken sayfalar vardır. Örneğin, bir kuruluştaki tüm çalışanları listelemek için bir sayfa içeren bir insan kaynakları uygulaması düşünün — "çalışanları listele" sayfası. Bu sayfa, kullanıcıların bir köprüye tıklayarak yeni bir çalışan eklemesine de izin verebilir. Tıklandığı zaman, yeni çalışanın ayrıntılarını toplamak ve listeyi güncelleştirmek için "çalışan Ekle" sayfasına gider ve bunları "çalışanları listele" sayfasına geri döndürür. Bu gezinti stili, bazı işlemleri gerçekleştirmek ve yapılandırılmış programlama olarak bilinen bir değer döndürmek için bir yöntemi çağırmaya benzerdir. Bu şekilde, bu gezinti stili *yapılandırılmış gezinti*olarak bilinir.

@No__t_0 sınıfı yapılandırılmış gezinti için destek uygulamaz. Bunun yerine, <xref:System.Windows.Navigation.PageFunction%601> sınıfı <xref:System.Windows.Controls.Page> türetilir ve yapısal gezinti için gereken temel yapılar ile genişletir. Bu konu başlığı altında, <xref:System.Windows.Navigation.PageFunction%601> kullanılarak yapılandırılmış gezintiyi nasıl kurinin yapılacağı gösterilmektedir.

<a name="Structured_Navigation"></a>

## <a name="structured-navigation"></a>Yapılandırılmış gezinti

Bir sayfa yapılandırılmış bir gezinmede başka bir sayfa çağırdığında, aşağıdaki davranışların bazıları veya tümü gereklidir:

- Çağıran sayfa, isteğe bağlı olarak çağrılan sayfanın gerektirdiği parametreleri geçirerek çağrılan sayfaya gider.

- Çağrılan sayfa, bir Kullanıcı arama sayfasını kullanarak tamamlandığında, isteğe bağlı olarak, arama sayfasına özel olarak döner:

  - Çağırma sayfasının nasıl tamamlandığını açıklayan durum bilgilerini döndürme (örneğin, bir kullanıcının Tamam düğmesine veya bir Iptal düğmesine basıldığında).

  - Kullanıcıdan toplanan verileri döndürme (örneğin, yeni çalışan ayrıntıları).

- Çağıran sayfa çağrılan sayfaya döndüğünde, çağrılan sayfa bir diğer sayfanın bir örneğini başka bir şekilde yalıtmak için gezinme geçmişinden kaldırılır.

Bu davranışlar aşağıdaki şekilde gösterilmiştir:

![Ekran görüntüsü, arama sayfası ve çağrılan sayfa arasındaki akışı gösterir.](./media/structured-navigation-overview/flow-between-calling-page-called-page.png)

Çağrılan sayfa olarak bir <xref:System.Windows.Navigation.PageFunction%601> kullanarak bu davranışları uygulayabilirsiniz.

<a name="Structured_Navigation_with_PageFunction"></a>

## <a name="structured-navigation-with-pagefunction"></a>PageFunction ile yapılandırılmış gezinti

Bu konu başlığı altında, tek bir <xref:System.Windows.Navigation.PageFunction%601> içeren yapılandırılmış gezintinin temel mekanizması nasıl uygulanacağı gösterilmektedir. Bu örnekte, bir <xref:System.Windows.Controls.Page> kullanıcıdan bir <xref:System.String> değeri almak ve bunu döndürmek için bir <xref:System.Windows.Navigation.PageFunction%601> çağırır.

### <a name="creating-a-calling-page"></a>Arama sayfası oluşturma

Bir <xref:System.Windows.Navigation.PageFunction%601> çağıran sayfa bir <xref:System.Windows.Controls.Page> ya da <xref:System.Windows.Navigation.PageFunction%601> olabilir. Bu örnekte, aşağıdaki kodda gösterildiği gibi bir <xref:System.Windows.Controls.Page>.

[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup1)]
[!code-xaml[StructuredNavigationSample#CallingPageDefaultMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#callingpagedefaultmarkup2)]

[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind1)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind1)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind2)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind2)]
[!code-csharp[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#callingpagedefaultcodebehind3)]
[!code-vb[StructuredNavigationSample#CallingPageDefaultCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#callingpagedefaultcodebehind3)]

### <a name="creating-a-page-function-to-call"></a>Çağırmak için bir sayfa Işlevi oluşturma

Çağıran sayfa, kullanıcıdan veri toplamak ve döndürmek için çağrılan sayfayı kullanabileceği için <xref:System.Windows.Navigation.PageFunction%601>, tür bağımsız değişkeni çağıran sayfanın döndürdüğü değerin türünü belirten bir genel sınıf olarak uygulanır. Aşağıdaki kod, bir <xref:System.String> döndüren <xref:System.Windows.Navigation.PageFunction%601> kullanılarak çağrılan sayfanın ilk uygulamasını gösterir.

[!code-xaml[StructuredNavigationSample#CalledPageFunctionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml#calledpagefunctionmarkup)]

[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind1)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind1)]
[!code-csharp[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#calledpagefunctioncodebehind2)]
[!code-vb[StructuredNavigationSample#CalledPageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#calledpagefunctioncodebehind2)]

Bir <xref:System.Windows.Navigation.PageFunction%601> bildirimi, tür bağımsız değişkenlerinin eklenmesiyle bir <xref:System.Windows.Controls.Page> bildirimine benzerdir. Kod örneğinde görebileceğiniz gibi, tür bağımsız değişkenleri hem [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirmesinde hem de standart genel tür bağımsız değişkeni sözdizimi kullanılarak `x:TypeArguments` özniteliği ve arka plan kodu kullanılarak belirtilir.

Tür bağımsız değişkenleri olarak yalnızca .NET Framework sınıfları kullanmak zorunda değilsiniz. Özel bir tür olarak soyut olan alana özgü verileri toplamak için bir <xref:System.Windows.Navigation.PageFunction%601> çağrılabilir. Aşağıdaki kod, bir <xref:System.Windows.Navigation.PageFunction%601> için bir özel türün tür bağımsız değişkeni olarak nasıl kullanılacağını gösterir.

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomType.cs#customtypecode2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypeCODE2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomType.vb#customtypecode2)]

[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup1)]
[!code-xaml[CustomTypePageFunctionSnippets#CustomTypePageFunctionMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml#customtypepagefunctionmarkup2)]

[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind1)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind1)]
[!code-csharp[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/CSharp/CustomTypePageFunction.xaml.cs#customtypepagefunctioncodebehind2)]
[!code-vb[CustomTypePageFunctionSnippets#CustomTypePageFunctionCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CustomTypePageFunctionSnippets/VisualBasic/CustomTypePageFunction.xaml.vb#customtypepagefunctioncodebehind2)]

@No__t_0 için tür bağımsız değişkenleri, bir arama sayfası ile çağrılan sayfa arasındaki iletişimin temelini sağlar ve aşağıdaki bölümlerde ele alınmıştır.

Gördüğünüz gibi, bir <xref:System.Windows.Navigation.PageFunction%601> bildirimi ile tanımlanan tür, bir <xref:System.Windows.Navigation.PageFunction%601> verileri çağıran sayfaya döndürmekte önemli bir rol oynar.

### <a name="calling-a-pagefunction-and-passing-parameters"></a>PageFunction çağırma ve parametreleri geçirme

Bir sayfayı çağırmak için, çağıran sayfanın çağrılan sayfanın örneğini oluşturması ve <xref:System.Windows.Navigation.NavigationService.Navigate%2A> yöntemi kullanılarak buna gitmeniz gerekir. Bu, çağıran sayfanın, çağrılan sayfa tarafından toplanmakta olan veriler için varsayılan değerler gibi ilk verileri çağrılan sayfaya geçmesini sağlar.

Aşağıdaki kod, çağırma sayfasından parametreleri kabul etmek için parametresiz bir oluşturucuya sahip çağrılan sayfayı gösterir.

[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind1)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind2)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind3)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind3)]
[!code-csharp[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#acceptsinitialdatacodebehind4)]
[!code-vb[StructuredNavigationSample#AcceptsInitialDataCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#acceptsinitialdatacodebehind4)]

Aşağıdaki kod, çağrılan sayfanın örneğini oluşturmak ve bir ilk dize değeri geçirmek için <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Documents.Hyperlink.Click> olayını işleyen arama sayfasını gösterir.

[!code-xaml[StructuredNavigationSample#PassingDataMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml#passingdatamarkup2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind1)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind1)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind2)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind2)]
[!code-csharp[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#passingdatacodebehind3)]
[!code-vb[StructuredNavigationSample#PassingDataCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#passingdatacodebehind3)]

Çağrılan sayfaya parametreleri geçirmek zorunda değilsiniz. Bunun yerine şunları yapabilirsiniz:

- Çağırma sayfasından:

  1. Parametresiz oluşturucuyu kullanarak çağrılan <xref:System.Windows.Navigation.PageFunction%601> örneğini oluşturun.

  2. Parametreleri <xref:System.Windows.Application.Properties%2A> depolayın.

  3. Çağrılan <xref:System.Windows.Navigation.PageFunction%601> gidin.

- Çağrılan <xref:System.Windows.Navigation.PageFunction%601>:

  - @No__t_0 depolanan parametreleri alın ve kullanın.

Ancak, kısa bir süre içinde gördüğünüz gibi, çağrılan sayfada döndürülen verileri toplamak için kod örneğini kullanmanız ve çağrılan sayfaya gitmeniz gerekir. Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> canlı tutulması gerekir; Aksi takdirde, <xref:System.Windows.Navigation.PageFunction%601> bir sonraki sefer [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], parametresiz oluşturucuyu kullanarak <xref:System.Windows.Navigation.PageFunction%601> örneğini oluşturur.

Ancak çağrılan sayfanın dönebilmesi için, çağıran sayfa tarafından alınabilecek verileri döndürmesi gerekir.

### <a name="returning-task-result-and-task-data-from-a-task-to-a-calling-page"></a>Görev sonucu ve görev verilerini bir görevden bir arama sayfasına döndürme

Kullanıcı çağrılan sayfayı kullanmayı bitirdikten sonra, bu örnekte Tamam ya da Iptal düğmelerine basarak, çağrılan sayfanın döndürmesi gerekir. Çağıran sayfa, kullanıcıdan veri toplamak için çağrılan sayfayı kullandığından, çağıran sayfa iki tür bilgi gerektirir:

1. Kullanıcının çağrılan sayfayı (Tamam düğmesine veya bu örnekteki Iptal düğmesine basarak) iptal edilip edilmeyeceğini belirtir. Bu, çağıran sayfanın kullanıcıdan topladığı verilerin kullanılıp kullanılmayacağını belirlemesine olanak sağlar.

2. Kullanıcı tarafından sağlanmış olan veriler.

Bilgi döndürmek için <xref:System.Windows.Navigation.PageFunction%601> <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> metodunu uygular. Aşağıdaki kod nasıl çağrılacağını gösterir.

[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind1)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind1)]
[!code-csharp[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CalledPageFunction.xaml.cs#returncodebehind2)]
[!code-vb[StructuredNavigationSample#ReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CalledPageFunction.xaml.vb#returncodebehind2)]

Bu örnekte, bir Kullanıcı Iptal düğmesine basarsa, arama sayfasına bir `null` değeri döndürülür. Bunun yerine Tamam düğmesine basıldığında, Kullanıcı tarafından verilen dize değeri döndürülür. <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A>, verileri çağırma sayfasına döndürmek için çağırdığınız bir `protected virtual` yöntemidir. Verilerinizin, <xref:System.Windows.Navigation.ReturnEventArgs%601.Result%2A> döndürülen değer türünü belirten genel <xref:System.Windows.Navigation.ReturnEventArgs%601> türünün bir örneğinde paketlenmesi gerekir. Bu şekilde, belirli bir tür bağımsız değişkeniyle bir <xref:System.Windows.Navigation.PageFunction%601> bildirdiğinizde, bir <xref:System.Windows.Navigation.PageFunction%601> tür bağımsız değişkeni tarafından belirtilen türün bir örneğini döndürmektedir. Bu örnekte, tür bağımsız değişkeni ve sonuç olarak, dönüş değeri <xref:System.String> türündedir.

@No__t_0 çağrıldığında, çağıran sayfanın <xref:System.Windows.Navigation.PageFunction%601> dönüş değerini alması için bir yol gerekir. Bu nedenle, <xref:System.Windows.Navigation.PageFunction%601> işlenecek sayfaları çağırmak için <xref:System.Windows.Navigation.PageFunction%601.Return> olayını uygular. @No__t_0 çağrıldığında, <xref:System.Windows.Navigation.PageFunction%601.Return> tetiklenir. bu nedenle, arama sayfası bildirimi almak için <xref:System.Windows.Navigation.PageFunction%601.Return> kaydedebilir.

[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind1)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind1)]
[!code-csharp[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/StructuredNavigationSample/CSharp/CallingPage.xaml.cs#processresultcodebehind2)]
[!code-vb[StructuredNavigationSample#ProcessResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StructuredNavigationSample/VisualBasic/CallingPage.xaml.vb#processresultcodebehind2)]

### <a name="removing-task-pages-when-a-task-completes"></a>Görev tamamlandığında görev sayfalarını kaldırma

Çağrılan bir sayfa döndürüldüğünde ve Kullanıcı çağrılan sayfayı iptal etmediyse, çağıran sayfa Kullanıcı tarafından sağlanmış olan verileri işler ve çağrılan sayfadan de döndürülür. Bu şekilde veri alımı genellikle yalıtılmış bir etkinliktir; çağrılan sayfa döndürüldüğünde, çağıran sayfanın daha fazla veri yakalamak için yeni bir arama sayfası oluşturması ve bu sayfada gezinilmesi gerekir.

Ancak, çağrılan bir sayfa günlükten kaldırılmadığı takdirde, bir Kullanıcı, çağıran sayfanın önceki bir örneğine geri gidebilecektir. @No__t_0 günlükte tutulup tutulmadığı <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> özelliği tarafından belirlenir. Varsayılan olarak, <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> `true` olarak ayarlandığı için <xref:System.Windows.Navigation.PageFunction%601.OnReturn%2A> çağrıldığında bir sayfa işlevi otomatik olarak kaldırılır. @No__t_0 çağrıldıktan sonra bir sayfa işlevini gezinti geçmişinde tutmak için, <xref:System.Windows.Navigation.PageFunctionBase.RemoveFromJournal%2A> `false` olarak ayarlayın.

<a name="Other_Types_of_Structured_Navigation"></a>

## <a name="other-types-of-structured-navigation"></a>Diğer yapılandırılmış gezinti türleri

Bu konuda, bir <xref:System.Windows.Navigation.PageFunction%601> en temel kullanımı ve yapılandırılmış gezintiyi çağırma/döndürme desteği gösterilmektedir. Bu temel, daha karmaşık türlerde yapısal gezinti oluşturma olanağı sağlar.

Örneğin, bazen bir kullanıcının yeterli miktarda veri toplamak veya bir görevi gerçekleştirmek için bir arama sayfası için birden çok sayfa gerekir. Birden çok sayfanın kullanımı "sihirbaz" olarak adlandırılır.

Diğer durumlarda, uygulamalar etkin şekilde çalışacak şekilde yapılandırılmış gezintiye bağlı karmaşık gezinti topolojilerine sahip olabilir. Daha fazla bilgi için bkz. [gezinti topolojilerine genel bakış](navigation-topologies-overview.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [Gezinti Topolojilerine Genel Bakış](navigation-topologies-overview.md)
