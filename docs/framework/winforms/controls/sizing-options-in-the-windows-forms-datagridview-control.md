---
title: Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: a236289939b9355e961ce1bfc9a7e0ff5349a95a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717914"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri
<xref:System.Windows.Forms.DataGridView> Satırlar, sütunlar ve üst bilgiler birçok farklı oluşum sonucunda boyutunu değiştirebilirsiniz. Aşağıdaki tabloda bu örnekleri gösterilmektedir.  
  
|Oluşum|Açıklama|  
|----------------|-----------------|  
|Kullanıcı yeniden boyutlandırma|Kullanıcılar, sürükleyerek ya da satır, sütun veya üstbilgi Bölücü çift boyutu ayarlamalar yapabilirsiniz.|  
|Denetimi yeniden boyutlandırma|Denetim genişliği değiştiğinde sütun doldurma modu sütun genişliklerini değiştirme; Örneğin, kendi üst formu ve kullanıcı denetimi zaman yerleştirildiğini formu boyutlandırır.|  
|Hücrenin değerini Değiştir|İçeriğe dayalı otomatik boyutlandırma modlarında boyutları yeni görüntüleme değerleri uyacak şekilde değiştirin.|  
|Yöntem çağrısı|İçerik tabanlı programlama yeniden boyutlandırma, yöntem çağrısının yapıldığı sırada hücre değerlerine göre fırsatçı boyutu ayar yapmanıza olanak tanır.|  
|Özellik ayarı|Ayrıca, belirli yükseklik ve genişlik değerleri ayarlayabilirsiniz.|  
  
 Varsayılan olarak, kullanıcı yeniden boyutlandırma etkin, otomatik boyutlandırma devre dışı bırakıldı ve kendilerine ait sütunların geniş olan hücre değerlerini kırpılır.  
  
 Aşağıdaki tabloda, varsayılan davranışı ayarlamak için veya belirli boyutlandırma seçenekleri özel efektler elde etmek için kullanabileceğiniz senaryolar gösterilmektedir.  
  
|Senaryo|Uygulama|  
|--------------|--------------------|  
|Kullanım sütun doldurma modu görüntülemek için yatay kaydırma çubuğunun görüntülemeden denetiminin tüm genişliğini kaplayacak sütunların görece küçük bir sayı veride benzer boyutlarda.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Kullanım sütun doldurma modu ile farklı boyutlarda değerleri görüntüler.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Göreli sütun genişliklerini, sütun ayarlayarak başlatın <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellikleri veya denetim çağırarak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> denetimi ile veri doldurduktan sonra yöntemi.|  
|Sütun doldurma modu ile değişen önem derecesi değerlerini kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Large olarak ayarlanan <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> modu belirli sütunları için her zaman bazı verilerini görüntü gerekir veya boyutlandırma seçeneğini dışında kullanan sütunları doldurmak için değerler.|  
|Denetim arka plan gösterilmesini sütun doldurma modu kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> son sütuna özelliği <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> ve diğer sütunlar için diğer boyutlandırma seçenekleri kullanın. Diğer sütunları çok fazla kullanılabilir alan kullanırsanız, ayarlama <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> son sütun özelliğidir.|  
|Simge veya kimlik sütunu gibi bir sabit genişlikte sütun görüntüler.|Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> için <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> ve <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> için <xref:System.Windows.Forms.DataGridViewTriState.False> sütun. Genişliği başlatırsınız <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliği veya denetim çağırarak <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> denetimi ile veri doldurduktan sonra yöntemi.|  
|Kırpma önlemek ve alanı kullanımını iyileştirmek için hücre içeriğini değişikliği gerektiğinde boyutu otomatik olarak ayarlayın.|Otomatik boyutlandırma özelliği bir içerik tabanlı boyutlandırma modunu temsil eden bir değere ayarlayın. Büyük miktarlarda veri ile çalışırken, bir performans cezasını önlemek için yalnızca görüntülenen satır hesaplayan bir boyutlandırma modunu kullanın.|  
|Birçok satır ile çalışırken, performans cezalarını önlemek için görüntülenen satırlardaki değerlerin uygun boyutları ayarlayın.|Yeniden boyutlandırma, otomatik veya programlama ile uygun boyutlandırma modunu sabit listesi değerleri kullanın. Kaydırma yaparken, yeni görüntülenen satırlardaki değerleri uygun boyutları ayarlamak için bir yeniden boyutlandırma yöntem çağrısı bir <xref:System.Windows.Forms.DataGridView.Scroll> olay işleyicisi. Kullanıcı çift tıklatma özelleştirmek için yeniden boyutlandırma yeni boyutlar yalnızca görüntülenen satırlardaki değerleri belirlemek için arama boyutlandırma yöntemi bir <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> veya <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> olay işleyicisi.|  
|Hücre içeriğini yalnızca belirli zamanlarda performans cezalarını önlemek için veya kullanıcı yeniden boyutlandırma etkinleştirmek için uygun boyutları ayarlayın.|Olay işleyicisinde bir içerik tabanlı boyutlandırma yöntemi çağırın. Örneğin, <xref:System.Windows.Forms.DataGridView.DataBindingComplete> boyutları bağlama sonra başlatmak ve işlemek için olay <xref:System.Windows.Forms.DataGridView.CellValidated> veya <xref:System.Windows.Forms.DataGridView.CellValueChanged> olay kullanıcı düzenlemeleri veya değişiklikler için dengelemek için boyutlarını ayarlamak için bir bağımlı veri kaynağındaki.|  
|Çok satırlı hücre içeriğini için satır yüksekliklerini ayarlayın.|Sütun genişliklerini paragraf metni görüntülemek için uygun olduğundan emin olun ve otomatik ya da programlı içerik tabanlı satır boyutlandırma yüksekliklerini ayarlamak için kullanın. Ayrıca çok satırlı içerik hücrelerle kullanarak görüntülendiğinden emin olmak bir <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> hücre stili değerini <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Genellikle, sütun genişliklerini korumak veya satır yüksekliklerini ayarlanır önce bunları belirli genişlikleri ayarlamak için bir sütun otomatik boyutlandırma modunu kullanır.|  
  
## <a name="resizing-with-the-mouse"></a>Fare ile yeniden boyutlandırma  
 Varsayılan olarak, kullanıcıların satırlar, sütunlar ve hücre değerlerine göre bir otomatik boyutlandırma modunu kullanmayan üstbilgileri boyutlandırabilirsiniz. Kullanıcıların sütun doldurma modu gibi diğer modları ile yeniden boyutlandırmasını önlemek için bir veya daha fazlasını ayarlayın <xref:System.Windows.Forms.DataGridView> özellikleri:  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Tek bir satır veya sütun ayarlayarak yeniden boyutlandırmasını kullanıcıları engelleyebilir, <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellikleri. Varsayılan olarak, <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellik değeri temel <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> sütunlar için özellik değeri ve <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> satırlar için özellik değeri. Açıkça <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> için <xref:System.Windows.Forms.DataGridViewTriState.True> veya <xref:System.Windows.Forms.DataGridViewTriState.False>, ancak denetim değerdir, satır veya sütun için belirtilen değer geçersiz kılar. Ayarlama <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> için <xref:System.Windows.Forms.DataGridViewTriState.NotSet> devralma geri yüklemek için.  
  
 Çünkü <xref:System.Windows.Forms.DataGridViewTriState.NotSet> değer devralımı yükler <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellik hiçbir zaman döndürür bir <xref:System.Windows.Forms.DataGridViewTriState.NotSet> satır veya sütun için eklenmedi sürece değeri bir <xref:System.Windows.Forms.DataGridView> denetimi. Belirlemeniz gerekiyorsa olmadığını <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özelliği değerinin bir satır veya sütun devralınır, inceleyin, <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği. Varsa <xref:System.Windows.Forms.DataGridViewElement.State%2A> değeri içeren <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> bayrak <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellik değeri devralınmaz.  
  
## <a name="automatic-sizing"></a>Otomatik boyutlandırma  
 Otomatik boyutlandırma, iki tür vardır <xref:System.Windows.Forms.DataGridView> denetimi: sütun doldurma modu ve içerik tabanlı otomatik boyutlandırma.  
  
 Sütun doldurma modu, denetimin görüntüleme alanının genişliğini doldurmak için denetiminde görünür sütunlar neden olur. Bu mod hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sütun dolgu modu](column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Ayrıca, satırlar, sütunlar ve üst bilgileri otomatik olarak boyutlarının hücrenin içerikleri sığacak şekilde ayarlamak için de yapılandırabilirsiniz. Bu durumda, hücre içeriğini değiştirdiğinizde boyut düzeltmesini gerçekleşir.  
  
> [!NOTE]
>  Hücre değerlerini sanal modu kullanarak bir özel veri önbelleği korumak, kullanıcı bir hücre değerini düzenler ancak dışında bir önbelleğe alınan değeri değiştirdiğinizde gerçekleşmez otomatik boyutlandırma oluşur bir <xref:System.Windows.Forms.DataGridView.CellValuePushed> olay işleyicisi. Bu durumda, çağrı <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> hücre ekranı güncelleştirmek ve geçerli otomatik boyutlandırma modlarını uygulamak için Denetim zorlamak için yöntemi.  
  
 Yalnızca bir boyut için içerik tabanlı otomatik boyutlandırma etkinleştirildiğinde — satırları ancak olmayan sütun veya sütunlar için olan ancak olmayan satırlar — ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> de etkin, boyut ayarlama da diğer boyutu değiştiğinde gerçekleşir. Örneğin, satır ancak olmayan sütunları otomatik boyutlandırma için yapılandırıldıysa ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> olan etkin kullanıcılar, bir sütunun genişliğini değiştirmek için sütun ayırıcılarını sürükleyebilirsiniz ve satır yüksekliklerini otomatik olarak ayarlamak hücre içeriğini yine de tam olarak görüntülenir.  
  
 Hem satır hem de sütunlar için içerik tabanlı otomatik boyutlandırma yapılandırırsanız ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> etkinleştirildiğinde <xref:System.Windows.Forms.DataGridView> denetim hücre içeriğini değiştirilebilir ve yeni boyutlar hesaplarken bir ideal hücre yükseklik ve genişlik oranı kullanacağınız her boyutları ayarlama.  
  
 Üstbilgi ve satırlar ve denetim değeri geçersiz bir sütun için boyutlandırma modunu yapılandırmak için bir veya daha fazlasını ayarlayın <xref:System.Windows.Forms.DataGridView> özellikleri:  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Denetimin sütun boyutlandırma modunu tek bir sütun için geçersiz kılmak için ayarlanmış kendi <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> dışında bir değere <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Bir sütun için boyutlandırma modunu gerçekten tarafından belirlenen kendi <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliği. Bu özelliğin değeri sütunun üzerinde alan <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özellik değeri o değerin olmadığı sürece <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, bu durumda denetimin <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> değeri devralınır.  
  
 İçeriğe dayalı otomatik dikkatli büyük miktarlarda veri ile çalışırken, yeniden boyutlandırma kullanın. Performans cezalarını önlemek için her satırda bir denetim çözümleme yerine yalnızca görüntülenen satırları temel alarak boyutları hesapla otomatik boyutlandırma modlarını kullanın. En yüksek performans için böylece yeni veri hemen sonra gibi belirli zamanlarda boyutlandırabilirsiniz kullanım programlı bunun yerine yeniden boyutlandırma yüklenir.  
  
 İçeriğe dayalı otomatik boyutlandırma modlarını satır, sütun veya satır veya sütun ayarlayarak gizli üstbilgileri etkilemez <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özellik veya Denetim <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> veya <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> özelliklerine `false`. Örneğin, bir büyük hücre değerini sığacak şekilde otomatik olarak boyutlandırılır sonra bir sütun gizli ise, büyük bir hücre değerini içeren satır silinirse gizli sütun boyutunu değiştirmez. Otomatik boyutlandırma görünürlüğü değiştiğinde oluşmaz kadar sütun değiştirme <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğini yeniden `true` geçerli içeriğinin boyutunu yeniden hesaplar için zorla değil.  
  
 İçerik tabanlı programlama yeniden boyutlandırma, satırlar, sütunlar ve üstbilgilerine bakılmaksızın kendi görünürlük etkiler.  
  
## <a name="programmatic-resizing"></a>Programlı olarak yeniden boyutlandırma  
 Otomatik boyutlandırma devre dışı bırakıldığında, tam genişlik veya yükseklik satırları, sütunları veya üst bilgileri aşağıdaki özellikleri aracılığıyla programlı olarak ayarlayabilirsiniz:  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Ayrıca programlı bir şekilde, satırları, sütunları ve üst bilgileri, aşağıdaki yöntemleri kullanarak içerikleri sığacak şekilde boyutlandırabilirsiniz:  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Bu yöntemlerin satır, sütun üst bilgileri bir kez yerine veya sürekli olarak yeniden boyutlandırmak için yapılandırma boyutlandırılır. Yeni boyutlar, kırpma olmadan tüm hücre içeriğini görüntülemek için otomatik olarak hesaplanır. Programlı olarak yeniden boyutlandırdığınızda sahip sütun <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özellik değerlerini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, ancak içerik tabanlı hesaplanan sütunların sütunu orantılı olarak ayarlamak için kullanılan <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerlerini ve genişlikleri olan gerçekten sütun Denetim kullanılabilir ekran alanının tüm sütunları doldurun, böylece daha sonra bu yeni oranlara göre hesaplanır.  
  
 Programlı olarak yeniden boyutlandırma, sürekli yeniden boyutlandırma ile performans cezalarını önlemek yararlıdır. Sütun doldurma modu ve kullanıcı yeniden boyutlandırılabilir satır ve sütun üst bilgileri için ilk boyutlarını sağlamak kullanışlıdır.  
  
 Genellikle, belirli zamanlarda programlama yeniden boyutlandırma yöntemleri çağırır. Örneğin, veriler yüklendikten hemen sonra program aracılığıyla tüm sütunları yeniden boyutlandırma veya belirli hücre değeri değiştirildikten sonra belirli bir satıra programlı olarak yeniden boyutlandırmak.  
  
## <a name="customizing-content-based-sizing-behavior"></a>İçerik tabanlı boyutlandırma davranışını özelleştirme  
 Türetilmiş çalışırken boyutlandırma davranışları özelleştirebileceğiniz <xref:System.Windows.Forms.DataGridView> kılarak hücre, satır ve sütun türleri <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, veya <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> yöntemleri veya yeniden boyutlandırma yöntemi aşırı yüklemeleri türetilen bir korumalı çağırarak <xref:System.Windows.Forms.DataGridView> denetimi. Korumalı yeniden boyutlandırma yöntemi aşırı yüklemeleri, aşırı geniş veya uzun hücre önleme ideal hücre yükseklik ve genişlik oranı elde etmek için çiftler halinde çalışacak şekilde tasarlanmıştır. Örneğin, eğer `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` aşırı yükünü <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> yöntemi ve değerini geçirin `false` için <xref:System.Boolean> parametresi aşırı yük hücreleri sıradaki genişliği ve ideal yüksekliklerini hesaplar, ancak satır yüksekliklerini uyum sağlar yalnızca. Ardından çağırmalıdır <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> hesaplanan ideal için sütun genişliklerini ayarlamak için yöntemi.  
  
## <a name="content-based-sizing-options"></a>İçerik tabanlı boyutlandırma seçenekleri  
 Boyutlandırma özellikleri ve yöntemleri tarafından kullanılan sabit listeleri için içerik tabanlı boyutlandırma benzer değerlere sahip. Hücreleri tercih edilen boyutlarını hesaplamak için kullanılır, bu değerleri ile sınırlayabilirsiniz. Tüm boyutlandırma sabit listeleri için görüntülenen hücrelere başvuru adları ile değerlerini kendi hesaplamalar görüntülenen satırların hücreleri sınırlayın. Satırları dışlama, çok sayıda satır çalışırken bir performans cezasını önlemek yararlıdır. Üst bilgi veya başlık olmayan hücre hücre değerlerini hesaplamalara da kısıtlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows Forms DataGridView Denetiminde Sütun Doldurma Modu](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView denetiminin boyutlandırma modlarını ayarlama](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
