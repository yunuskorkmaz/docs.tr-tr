---
title: Denetimleri Görsel Stilde İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- themes [Windows Forms], XP visual styles in Window Forms
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- visual themes [Windows Forms], rendering Windows Forms controls
- user controls [Windows Forms], painting
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a5b178ba-610e-46c4-a6c0-509c0886a744
ms.openlocfilehash: 32bcbab585c39be4a72150bf49820d4a16f1691f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968244"
---
# <a name="rendering-controls-with-visual-styles"></a>Denetimleri Görsel Stilde İşleme
.NET Framework, denetimleri ve diğer Windows Kullanıcı arabirimi (UI) öğelerini destekleyen işletim sistemlerinde görsel stilleri kullanarak işlemek için destek sağlar. Bu konuda, işletim sisteminin geçerli görsel stiliyle denetimleri ve diğer kullanıcı arabirimi öğelerini işlemek için .NET Framework çeşitli destek düzeyleri ele alınmaktadır.  
  
## <a name="rendering-classes-for-common-controls"></a>Ortak denetimler için işleme sınıfları  
 Denetim işleme, bir denetimin kullanıcı arabirimini çizmeyi ifade eder. Ad <xref:System.Windows.Forms?displayProperty=nameWithType> alanı, bazı <xref:System.Windows.Forms.ControlPaint> ortak Windows Forms denetimlerini işlemek için sınıfını sağlar. Ancak, bu sınıf klasik Windows stilinde denetimler çizer, bu da görsel stilleri etkinleştirilmiş uygulamalarda özel denetimleri çizerken tutarlı bir UI deneyiminin korunmasını zorlaştırır.  
  
 2,0 .NET Framework, görsel stillerle ortak denetimlerin <xref:System.Windows.Forms?displayProperty=nameWithType> parçalarını ve durumlarını işleyen ad alanındaki sınıfları içerir. Bu sınıfların her biri, `static` işletim sisteminin geçerli görsel stilinde denetim veya denetimin parçalarını belirli bir durumda çizme yöntemlerini içerir.  
  
 Bu sınıflardan bazıları, görsel stillerin kullanılabilir olup olmamasına bakılmaksızın ilgili denetimi çizmek için tasarlanmıştır. Görsel stiller etkinse, sınıf üyeleri ilgili denetimi görsel stillerle çizecek. görsel stiller devre dışıysa, sınıf üyeleri denetimi klasik Windows stilinde çizecek. Bu sınıflar şunları içerir:  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Diğer sınıflar yalnızca görsel stiller kullanılabilir olduğunda ilgili denetimi çizebilir ve görsel stiller devre dışıysa bu kişilerin üyeleri bir özel durum oluşturur. Bu sınıflar şunları içerir:  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Bir denetim çizmek için bu sınıfları kullanma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir denetim Işleme sınıfı](how-to-use-a-control-rendering-class.md)kullanın.  
  
## <a name="visual-style-element-and-rendering-classes"></a>Görsel stil öğesi ve Işleme sınıfları  
 Ad <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> alanı, görsel stiller tarafından desteklenen herhangi bir denetim veya UI öğesi hakkında bilgi eklemek ve bu bilgileri almak için kullanılabilecek sınıfları içerir. Desteklenen denetimler, <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanında (önceki bölüme bakın) bir işleme sınıfına sahip ortak denetimleri ve ayrıca sekme denetimleri ve yeniden çubuk denetimleri gibi diğer denetimleri içerir. Desteklenen diğer kullanıcı arabirimi öğeleri **Başlangıç** menüsünün parçalarını, görev çubuğunu ve Windows 'un istemci olmayan alanını içerir.  
  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Ad alanının ana sınıfları ve ' <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>dir <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> . <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>görsel stiller tarafından desteklenen herhangi bir denetimi veya Kullanıcı arabirimi öğesini tanımlamak için bir temel sınıftır. Bunun yanı sıra <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , ad alanı, bir denetimin, denetim bölümünün veya görsel tarafından desteklenen diğer <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> Kullanıcı arabirimi öğesinin her durumu için bir döndüren özelliklerine <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> sahip `static` birçok iç içe sınıf içerir. <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> stillerde.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>, görüntülenen ve işletim sisteminin geçerli görsel stili tarafından tanımlanan <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> her biri hakkında bilgi alan bir yöntem sağlar. Bir öğe hakkında alınabilecek bilgiler, varsayılan boyutunu, arka plan türünü ve renk tanımlarını içerir. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>görsel stiller (UxTheme) API 'sinin işlevselliğini Windows platformu SDK 'sının Windows kabuğu bölümünden kaydırır. Daha fazla bilgi için bkz. [görsel stilleri etkinleştirme](/windows/desktop/controls/cookbook-overview).  
  
 [Ve <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> kullanmahakkındadahafazlabilgiiçinbkz<xref:System.Windows.Forms.VisualStyles.VisualStyleElement>. nasıl yapılır: Bir görsel stil öğesi](how-to-render-a-visual-style-element.md)işle.  
  
## <a name="enabling-visual-styles"></a>Görsel stilleri etkinleştirme  
 .NET Framework sürüm 1,0 için yazılmış bir uygulama için görsel stilleri etkinleştirmek üzere, programcılar, denetimleri çizmek için, ComCtl32. dll sürüm 6 veya üstünü belirten bir uygulama bildirimi içermelidir. .NET Framework sürüm 1,1 veya üzeri ile oluşturulan uygulamalar, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application> sınıfının yöntemini kullanabilir.  
  
## <a name="checking-for-visual-styles-support"></a>Görsel stiller desteği denetleniyor  
 <xref:System.Windows.Forms.Application> Sınıfının özelliği, geçerli uygulamanın görsel stillerle denetimleri <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> çizdiğini gösterir. Özel bir denetimi boyadığınızda, denetimini görsel stillerle mi yoksa, <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> yoksa görsel olarak mı işleneceğini öğrenmek için değerini kontrol edebilirsiniz. Aşağıdaki tabloda, dönmesi <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> `true`için olması gereken dört koşul listelenmektedir.  
  
|Koşul|Notlar|  
|---------------|-----------|  
|İşletim sistemi görsel stilleri destekler.|Bu koşulu ayrı doğrulamak için <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> sınıfının özelliğini kullanın.|  
|Kullanıcı, işletim sisteminde görsel stilleri etkinleştirdi.|Bu koşulu ayrı doğrulamak için <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> sınıfının özelliğini kullanın.|  
|Görsel stiller uygulamada etkinleştirilir.|Görsel stiller, <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırarak veya Comctl32. dll sürüm 6 veya sonraki bir sürümün denetimleri çizecek şekilde kullanılacağını belirten bir uygulama bildirimi kullanılarak etkinleştirilebilir.|  
|Visual stilleri, uygulama pencerelerinin istemci alanını çizmek için kullanılır.|Bu koşulu <xref:System.Windows.Forms.Application.VisualStyleState%2A> ayrı doğrulamak için, <xref:System.Windows.Forms.Application> sınıfının özelliğini kullanın ve değerine <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>sahip olduğunu doğrulayın.|  
  
 Bir kullanıcının görsel stilleri ne zaman etkinleştirceğini veya devre dışı bıraktığını veya bir görsel stilden diğerine geçiş yapmasını sağlamak için <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> , <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> veya <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> olaylarına yönelik işleyicilerdeki değeri denetleyin.  
  
> [!IMPORTANT]
> Kullanıcı görsel stilleri <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> etkinleştirerek <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> veya anahtar yaptığında bir denetim veya Kullanıcı arabirimi öğesini işlemek için kullanmak istiyorsanız <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> olay yerine olayı işlerken bunu yaptığınızdan emin olun. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> İşlerken<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>sınıfı kullanırsanız bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Boyama ve İşleme](custom-control-painting-and-rendering.md)
