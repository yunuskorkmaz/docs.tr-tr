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
ms.openlocfilehash: b0b301bca33842dfb68de9143b665bed73f17b74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903441"
---
# <a name="rendering-controls-with-visual-styles"></a>Denetimleri Görsel Stilde İşleme
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Görsel stilleri kullanarak bunları destekleyen işletim sistemlerinde arabirimi (UI) öğeleri işleme denetimleri ve diğer Windows kullanıcı için destek sağlar. Bu konuda destek çeşitli düzeylerde anlatılmaktadır [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] işleme denetimleri ve diğer UI öğeleri ile işletim sisteminin geçerli görsel stili.  
  
## <a name="rendering-classes-for-common-controls"></a>Ortak denetimleri için işleme sınıfları  
 Bir denetim oluşturma kullanıcı arabirimi denetimi çizim ifade eder. <xref:System.Windows.Forms?displayProperty=nameWithType> Ad alanı sağlar <xref:System.Windows.Forms.ControlPaint> bazı yaygın işlemeye sınıfı Windows Forms denetimleri. Ancak, bu sınıf, tutarlı bir kullanıcı Arabirimi deneyimi çizim özel denetimleri görsel stilde uygulamalarında etkinleştirildiğinde sürdürülmesi zor zorlaştırabilir Klasik Windows stilde denetimler çizer.  
  
 [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] Sınıfları içeren <xref:System.Windows.Forms?displayProperty=nameWithType> parça ve durumlarını ortak denetimleri görsel stilde işleme ad alanı. Bu sınıfların her birini içeren `static` denetimi veya denetim bölümlerini işletim sisteminin geçerli görsel stil ile belirli bir durumunda çizmek için yöntemleri.  
  
 Bu sınıfların bazıları, görsel stilleri olmanıza bakılmaksızın ilgili denetim çizmek için tasarlanmıştır. Görsel stiller etkinleştirilirse, sınıf üyeleri görsel stilde ilgili denetim çizme; görsel stiller devre dışıysa, sınıf üyeleri Klasik Windows stili denetim çizer. Bu sınıfları şunlardır:  
  
- <xref:System.Windows.Forms.ButtonRenderer>  
  
- <xref:System.Windows.Forms.CheckBoxRenderer>  
  
- <xref:System.Windows.Forms.GroupBoxRenderer>  
  
- <xref:System.Windows.Forms.RadioButtonRenderer>  
  
 Diğer sınıflar, yalnızca görsel stilleri kullanılabilir ve görsel stillerini devre dışı bırakılırsa, üyeleri bir özel durum oluşturur, ilgili denetim çizebilirsiniz. Bu sınıfları şunlardır:  
  
- <xref:System.Windows.Forms.ComboBoxRenderer>  
  
- <xref:System.Windows.Forms.ProgressBarRenderer>  
  
- <xref:System.Windows.Forms.ScrollBarRenderer>  
  
- <xref:System.Windows.Forms.TabRenderer>  
  
- <xref:System.Windows.Forms.TextBoxRenderer>  
  
- <xref:System.Windows.Forms.TrackBarRenderer>  
  
 Bir denetim çizmek için bu sınıflar kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Denetim işleme sınıfı kullanma](how-to-use-a-control-rendering-class.md).  
  
## <a name="visual-style-element-and-rendering-classes"></a>Görsel stilde öğe ve sınıfları oluşturma  
 <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Ad alanını çizmek ve herhangi bir denetim veya görsel stilleri tarafından desteklenen kullanıcı Arabirimi öğesi hakkında bilgi almak için kullanılan sınıfları içerir. Desteklenen denetimleri içeren bir işleme sınıf olmayan ortak denetimleri <xref:System.Windows.Forms?displayProperty=nameWithType> ad alanı (önceki bölüme bakın), sekme denetimleri ve çubuk barınağı denetimleri gibi diğer denetimler yanı sıra. Desteklenen diğer kullanıcı Arabirimi öğeleri içeren bölümlerini **Başlat** menü, görev ve windows istemci olmayan alanın.  
  
 Ana sınıflarını <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> ve <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer>. <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> görsel stiller tarafından desteklenen tüm denetim veya kullanıcı arabirimi öğesi tanımlamak için bir foundation sınıftır. Ek olarak <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> kendisini <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad alanı, çok sayıda iç içe geçmiş sınıflar içerir <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> ile `static` döndüren özellikler bir <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> her denetim, Denetim bölümü veya görsel tarafından desteklenen diğer kullanıcı Arabirimi öğesi durumu stilleri.  
  
 <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> Çizim ve her biri hakkında bilgi almak için yöntemler sağlar <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> işletim sisteminin geçerli görsel stil tarafından tanımlanır. Varsayılan boyutunda, arka plan türü ve renk tanımları alınabilmesi için bir öğe hakkında bilgi içerir. <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> görsel stiller (UxTheme) API Windows Kabuğu bölümünden Windows Platform SDK'sının işlevselliğini sarmalar. Daha fazla bilgi için [görsel stilleri etkinleştirme](/windows/desktop/controls/cookbook-overview).  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> ve <xref:System.Windows.Forms.VisualStyles.VisualStyleElement>, bkz: [nasıl yapılır: Bir görsel stilde öğe işleme](how-to-render-a-visual-style-element.md).  
  
## <a name="enabling-visual-styles"></a>Görsel stilleri etkinleştirme  
 Yazılmış bir uygulama için görsel stilleri etkinleştirmek için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.0, programcılar ComCtl32.dll sürüm 6 veya sonraki denetimlerini çizmek için kullanılacak belirten bir uygulama bildirimi içermelidir. İle oluşturulan uygulamalar [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] sürüm 1.1 veya üstünün kullanabileceğiniz <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi <xref:System.Windows.Forms.Application> sınıfı.  
  
## <a name="checking-for-visual-styles-support"></a>Görsel stil desteğini denetleme  
 <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> Özelliği <xref:System.Windows.Forms.Application> sınıfı, geçerli uygulama denetimleri görsel stilde çizim olup olmadığını belirtir. Özel denetim boyama, değerini kontrol edebilirsiniz <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> denetiminiz ile veya olmadan görsel stilleri işlemeyeceğini belirlemek için. Aşağıdaki tablo için bulunması gereken dört koşulları listeler <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A> döndürülecek `true`.  
  
|Koşul|Notlar|  
|---------------|-----------|  
|İşletim sistemi görsel stillerini destekler.|Bu durum ayrıca doğrulamak için <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsSupportedByOS%2A> özelliği <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> sınıfı.|  
|Kullanıcı, işletim sisteminde görsel stilleri etkinleştirdi.|Bu durum ayrıca doğrulamak için <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation.IsEnabledByUser%2A> özelliği <xref:System.Windows.Forms.VisualStyles.VisualStyleInformation> sınıfı.|  
|Görsel stiller uygulama içinde etkinleştirilir.|Görsel stiller etkinleştirilebilir bir uygulamada çağırarak <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi veya bir uygulamayı kullanarak o ComCtl32.dll sürüm 6 veya sonraki belirten bildirimi denetimlerini çizmek için kullanılacak.|  
|Görsel stiller uygulama windows istemci alanını çizmek için kullanılıyor.|Bu durum ayrıca doğrulamak için <xref:System.Windows.Forms.Application.VisualStyleState%2A> özelliği <xref:System.Windows.Forms.Application> sınıfı ve değere sahip olduğundan emin olun <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAreaEnabled?displayProperty=nameWithType> veya <xref:System.Windows.Forms.VisualStyles.VisualStyleState.ClientAndNonClientAreasEnabled?displayProperty=nameWithType>.|  
  
 Ne zaman bir kullanıcı etkinleştirir görsel stillerini devre dışı bırakır veya anahtarları bir görsel stil diğerine belirlemek için denetlemek <xref:Microsoft.Win32.UserPreferenceCategory.VisualStyle?displayProperty=nameWithType> işleyicileri değerinde <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging?displayProperty=nameWithType> veya <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged?displayProperty=nameWithType> olayları.  
  
> [!IMPORTANT]
>  Kullanmak istiyorsanız <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> kullanıcı etkinleştirir ya da görsel stilleri anahtarları bir denetim veya kullanıcı Arabirimi öğesi işlemek için bu işlerken yaptığınızdan emin olun <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> yerine olay <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging> olay. Kullanırsanız, bir özel durum <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> sınıfı işlenirken <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanging>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özel Denetim Boyama ve İşleme](custom-control-painting-and-rendering.md)
