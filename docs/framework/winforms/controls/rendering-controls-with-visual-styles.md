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
ms.openlocfilehash: a7f2d810567d37021d5d4473204d9950d6834b9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540910"
---
# <a name="rendering-controls-with-visual-styles"></a>Denetimleri Görsel Stilde İşleme
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] İşletim sistemlerinde desteklemek görsel stiller kullanarak arabirimi (UI) öğeleri işleme denetimleri ve başka bir Windows kullanıcı için destek sağlar. Bu konuda destek birkaç düzeyini ele alınmıştır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işleme denetimleri ve işletim sisteminin geçerli görsel stil ile diğer kullanıcı Arabirimi öğeleri için.  
  
## <a name="rendering-classes-for-common-controls"></a>Ortak Denetimler için işleme sınıfları  
 Bir denetim işleme başvuran bir denetim kullanıcı arabiriminin çizim. <xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı sağlar <xref:System.Windows.Forms.ControlPaint> bazı ortak işlemeye sınıfı Windows Forms denetler. Ancak, bu sınıfın denetimleri görsel stilde uygulamalarında çizim özel denetimler etkinleştirildiğinde tutarlı bir kullanıcı Arabirimi deneyim sağlamak zor hale getirebilir Klasik Windows stilinde çizer.  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] Sınıfları içerir <xref:System.Windows.Forms?displayProperty=nameWithType> bölümleri ve durumlarını ortak denetimleri görsel stilde işleme ad alanı. Bu sınıfların her biri içeren `static` denetimi veya denetim bölümlerini işletim sisteminin geçerli görsel stil ile belirli bir duruma çizim yöntemleri.  
  
 Bu sınıfların bazıları görsel stiller kullanılabilir olup bağımsız olarak ilgili denetim çizmek için tasarlanmıştır. Görsel stiller etkinleştirilirse, sınıf üyeleri görsel stiller ile ilgili denetim çizer; görsel stiller devre dışıysa, sınıf üyeleri Klasik Windows stilinde denetimi çizer. Bu sınıfları şunlardır:  
  
-   <xref:System.Windows.Forms.ButtonRenderer>  
  
-   <xref:System.Windows.Forms.CheckBoxRenderer>  
  
-   <xref:System.Windows.Forms.GroupBoxRenderer>  
  
-   <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Diğer sınıflar, yalnızca görsel stiller kullanılabilir ve görsel stiller devre dışı bırakılırsa, üyeleri bir özel durum, ilgili denetim çizebilirsiniz. Bu sınıfları şunlardır:  
  
-   <xref:System.Windows.Forms.ComboBoxRenderer>  
  
-   <xref:System.Windows.Forms.ProgressBarRenderer>  
  
-   <xref:System.Windows.Forms.ScrollBarRenderer>  
  
-   <xref:System.Windows.Forms.TabRenderer>  
  
-   <xref:System.Windows.Forms.TextBoxRenderer>  
  
-   <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Bir denetim çizmek için bu sınıfları kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir denetim işleme sınıfı kullanma](../../../../docs/framework/winforms/controls/how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Görsel stilde öğe ve sınıfları oluşturma  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Ad alanı, çizme ve herhangi bir denetim veya görsel stiller tarafından desteklenen kullanıcı Arabirimi öğesi hakkında bilgi almak için kullanılan sınıfları içerir. Desteklenen denetimleri içerir işleme sınıfı olmayan ortak denetimler <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı (önceki bölüme bakın), sekme denetimleri ve rebar denetimleri gibi diğer denetimleri yanı sıra. Desteklenen diğer kullanıcı Arabirimi öğeleri içeren bölümlerini **Başlat** menüsü, görev ve windows nonclient alanı.  
  
 Ana sınıflarını <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> ve <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> görsel stiller tarafından desteklenen tüm denetim veya kullanıcı arabirimi öğesi tanımlamak için bir foundation sınıftır. Ek olarak <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> kendisini <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad alanı, çok sayıda iç içe geçmiş sınıflar içerir <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> ile `static` döndüren özellikleri bir <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> bir denetim, Denetim bölümü ya da visual tarafından desteklenen diğer kullanıcı Arabirimi öğesi her durum için stilleri.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> Çizim ve her hakkında bilgi alın yöntemleri sağlayan <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> işletim sistemi geçerli görsel stil tarafından tanımlanan. Varsayılan boyut, arka plan türü ve renk tanımlarını alınabilmesi için bir öğe hakkında bilgi içerir. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> görsel stiller (UxTheme) API Windows Platform SDK'ın Windows Kabuğu bölümünden işlevi sarmalar. Daha fazla bilgi için bkz: [Windows XP görsel stilleri kullanarak](https://msdn.microsoft.com/library/ms997649.aspx).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> ve <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, bkz: [nasıl yapılır: görsel stilde öğe işleme](../../../../docs/framework/winforms/controls/how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Görsel stiller etkinleştirme  
 Görsel stiller için yazılmış bir uygulama için etkinleştirmek için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, programcıların ComCtl32.dll 6 veya sonraki sürümü denetimleri çizmek için kullanılan olduğunu belirten bir uygulama bildirimi içermelidir. İle oluşturulan uygulamaların [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 veya üstünün kullanabileceğiniz <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi <xref:System.Windows.Forms.Application> sınıfı.  
  
## <a name="checking-for-visual-styles-support"></a>Görsel stiller desteği denetleniyor  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Özelliği <xref:System.Windows.Forms.Application> sınıfı, geçerli uygulama denetimleri görsel stilde çizim olup olmadığını belirtir. Bir özel denetim boyama yaparken değerini kontrol edebilirsiniz <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> denetiminizi ile veya olmadan görsel stiller oluşturması gerektiğini olup olmadığını belirlemek için. Aşağıdaki tabloda için bulunmalıdır dört koşulları listeler <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> döndürülecek `true`.  
  
|Koşul|Notlar|  
|---------------|-----------|  
|İşletim sistemi görsel stiller destekler.|Bu durum ayrı olarak doğrulamak için kullanılan <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> özelliği <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> sınıfı.|  
|Kullanıcı işletim sisteminde görsel stiller etkinleştirdi.|Bu durum ayrı olarak doğrulamak için kullanılan <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> özelliği <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> sınıfı.|  
|Görsel stiller uygulamada etkinleştirilir.|Görsel stiller etkinleştirilebilir bir uygulamada çağırarak <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi veya bir uygulama kullanarak bu ComCtl32.dll sürümü 6 veya sonraki sürümünü belirtir bildirimi denetimleri çizmek için kullanılır.|  
|Görsel stiller uygulama windows istemci alanını çizmek için kullanılıyor.|Bu durum ayrı olarak doğrulamak için kullanılan <xref:System.Windows.Forms.Application.VisualStyleState%2A> özelliği <xref:System.Windows.Forms.Application> sınıfı ve değere sahip olduğunu doğrulayın <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> veya <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 İçin ne zaman bir kullanıcı sağlayan görsel stiller devre dışı bırakır veya anahtarları'nden bir görsel stil diğerine belirlemek için denetleyin <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> işleyicileri değerinde <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> veya <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> olaylar.  
  
> [!IMPORTANT]
>  Kullanmak istiyorsanız, <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> kullanıcı etkinleştirir ya da görsel stiller anahtarları bir denetim ya da kullanıcı Arabirimi öğesi oluşturmak için bu işlerken yaptığınızdan emin olun <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> yerine olay <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> olay. Kullanırsanız, bir özel durum <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> sınıf işlerken <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Boyama ve İşleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)
