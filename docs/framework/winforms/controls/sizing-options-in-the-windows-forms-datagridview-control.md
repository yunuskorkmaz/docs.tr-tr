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
ms.openlocfilehash: 6e3a7786970ef536da4ef7628cd33ae067ba90be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541760"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri
<xref:System.Windows.Forms.DataGridView> Satırlar, sütunlar ve üstbilgiler boyutunu birçok farklı oluşum sonucu olarak değiştirebilirsiniz. Aşağıdaki tabloda bu örnekleri gösterilmektedir.  
  
|Geçişi|Açıklama|  
|----------------|-----------------|  
|Kullanıcı yeniden boyutlandırma|Kullanıcılar, sürükleyerek veya satır, sütun veya üstbilgi Bölücü çift boyutu ayarlamalar yapabilirsiniz.|  
|Denetim yeniden boyutlandırma|Denetim genişliği değiştiğinde sütun doldurma modu sütun genişliklerini değiştirebilirsiniz; Örneğin, kendi üst form ve kullanıcı denetimi yerleşik olduğunda, formu yeniden boyutlandırır.|  
|Hücrenin değerini değiştirme|Otomatik boyutlandırma içerik tabanlı modlarında boyutlarını yeni görüntüleme değerleri uyacak şekilde değiştirin.|  
|Yöntem çağrısı|İçerik tabanlı programlı yeniden boyutlandırma yöntem çağrısının aynı anda hücre değerlerine göre fırsatçılıktan boyutu ayarlamalar yapmanıza olanak tanır.|  
|Özellik ayarı|Ayrıca, belirli yükseklik ve genişlik değerlerini ayarlayabilirsiniz.|  
  
 Varsayılan olarak, kullanıcı yeniden boyutlandırma etkin, otomatik boyutlandırma devre dışıdır ve bunların sütundan sayısından daha geniş hücre değerlerini kırpılır.  
  
 Aşağıdaki tabloda, varsayılan davranışını ayarlamak için veya belirli boyutlandırma seçenekleri belirli efektleri elde etmek için kullanabileceğiniz senaryolar gösterilmektedir.  
  
|Senaryo|Uygulama|  
|--------------|--------------------|  
|Görüntüleme için sütun doldurma modu kullan yatay kaydırma çubuğu görüntülemeden denetimi genişliğinin tamamını kaplayacak sütunları göreli olarak az sayıda veri benzer şekilde boyutlandırılmış.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Kullanım sütun doldurma modu ile farklı boyutlarda değerleri görüntüler.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Sütun göreli sütun genişliklerini başlatırsınız <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellikleri veya denetim çağırarak <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> denetimi verilerle doldurduktan sonra yöntemi.|  
|Sütun doldurma modu değişen önem değerlerle kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Büyük ayarlamak <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> modu belirli sütunları için her zaman kendi verilerin bazıları görüntülenen gerekir veya boyutlandırma seçeneği dışında kullanın sütunları doldurmak için değerleri.|  
|Denetim arka plan görüntüleme önlemek için sütun doldurma modu kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> son sütunun özelliği <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> ve diğer sütunlar için diğer boyutlandırma seçenekleri kullanın. Diğer sütunların çok fazla kullanılabilir alan kullanırsanız, ayarlamanız <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> son sütunun özelliği.|  
|Simge veya kimlik sütunu gibi bir sabit genişlikli sütun görüntüler.|Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> için <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> ve <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> için <xref:System.Windows.Forms.DataGridViewTriState.False> sütun için. Eni başlatırsınız <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliği veya denetim çağırarak <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> denetimi verilerle doldurduktan sonra yöntemi.|  
|Hücre içeriğinin kırpma önlemek için ve alanı kullanımını en iyi duruma getirme değiştirdiğinizde boyutları otomatik olarak ayarlayın.|Otomatik boyutlandırma özelliğini içerik tabanlı boyutlandırma modunu temsil eden bir değer ayarlayın. Büyük miktarlarda veri çalışırken performans cezasını önlemek için yalnızca görüntülenen satır hesaplar boyutlandırma modunu kullanın.|  
|Birçok satırlarla çalışırken performans cezalarını önlemek için görüntülenen satırların değerleri uyacak şekilde boyutları ayarlayın.|Yeniden boyutlandırma, otomatik veya programlama ile uygun boyutlandırma modunu numaralandırma değerlerini kullanın. Kaydırma sırasında yeni görüntülenen satır değerleri uyacak şekilde boyutları ayarlamak için bir yeniden boyutlandırma yöntem çağrısı bir <xref:System.Windows.Forms.DataGridView.Scroll> olay işleyicisi. Kullanıcı çift tıklatma özelleştirmek için yeniden boyutlandırma yeni boyutlar yalnızca görüntülenen satırların değerlerini belirlemek için arama yeniden boyutlandırma yöntemi bir <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> veya <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> olay işleyicisi.|  
|Yalnızca belirli zamanlarda kullanıcı yeniden boyutlandırma etkinleştirmek için ya da performans cezalarını önlemek için hücre içeriklerin sığması için boyutları ayarlayın.|Bir olay işleyicisi içerik tabanlı yeniden boyutlandırma yöntemi çağırın. Örneğin, <xref:System.Windows.Forms.DataGridView.DataBindingComplete> sonra bağlama boyutları başlatmak ve işlemek için olay <xref:System.Windows.Forms.DataGridView.CellValidated> veya <xref:System.Windows.Forms.DataGridView.CellValueChanged> kullanıcı düzenlemeleri veya değişiklikler için dengelemek için boyutları ayarlamak için olay ilişkili veri kaynağındaki.|  
|Çok satırlı hücre içeriğinin satır yükseklikte ayarlayın.|Sütun genişliklerini metninin paragrafları görüntülemek için uygun olduğundan emin olun ve otomatik veya programlama içerik tabanlı satır boyutlandırma yükseklikte ayarlamak için kullanın. Ayrıca çok satırlı içerik hücrelerle kullanarak görüntülendiğinden emin olmak bir <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> hücre stili değerini <xref:System.Windows.Forms.DataGridViewTriState.True>.<br /><br /> Genellikle, sütun genişliklerini korumak veya satır yükseklikte ayarlanmış önce bunları belirli genişlikleri ayarlamak için bir otomatik sütun boyutlandırma modunu kullanır.|  
  
## <a name="resizing-with-the-mouse"></a>Fareyle yeniden boyutlandırma  
 Varsayılan olarak, kullanıcılar satırlar, sütunlar ve hücre değerlerine göre bir otomatik boyutlandırma modunu kullanmayan üstbilgiler boyutunu değiştirebilirsiniz. Sütun doldurma modu gibi diğer modlarıyla boyutlandırma kullanıcılar önlemek için aşağıdakilerden birini veya birkaçını ayarlayın <xref:System.Windows.Forms.DataGridView> özellikleri:  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Tek tek satır veya sütun ayarlayarak yeniden boyutlandırmasını kullanıcıların engelleyebilir kendi <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellikleri. Varsayılan olarak, <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellik değeri temel <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> sütunlar için özellik değeri ve <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> satırlar için özellik değeri. Açıkça ayarlarsanız <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> için <xref:System.Windows.Forms.DataGridViewTriState.True> veya <xref:System.Windows.Forms.DataGridViewTriState.False>, ancak denetim değerdir, satır veya sütun için belirtilen değer geçersiz kılar. Ayarlama <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> için <xref:System.Windows.Forms.DataGridViewTriState.NotSet> devralma geri yüklemek için.  
  
 Çünkü <xref:System.Windows.Forms.DataGridViewTriState.NotSet> değeri devralma yükler <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özelliği hiçbir zaman döndürecektir bir <xref:System.Windows.Forms.DataGridViewTriState.NotSet> satır veya sütun için eklenmemiş sürece değeri bir <xref:System.Windows.Forms.DataGridView> denetim. Belirlemeniz gerekiyorsa olup olmadığını <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellik değerinin bir satır veya sütun devralınır, inceleyin, <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliği. Varsa <xref:System.Windows.Forms.DataGridViewElement.State%2A> değeri içeren <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> bayrak <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özellik değeri devralınmaz.  
  
## <a name="automatic-sizing"></a>Otomatik boyutlandırma  
 Otomatik boyutlandırma de iki tür vardır <xref:System.Windows.Forms.DataGridView> denetimi: sütun doldurma modu ve içerik tabanlı otomatik boyutlandırma.  
  
 Sütun doldurma modu görünür sütunlar denetimin görüntüleme alanının genişliğini kaplayacak şekilde denetiminde neden olur. Bu modu hakkında daha fazla bilgi için bkz: [Windows Forms DataGridView denetiminde sütun doldurma modu](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md).  
  
 Satırlar, sütunlar ve boyutlarının hücre içeriklerini sığması için otomatik olarak ayarlamak için üstbilgiler de yapılandırabilirsiniz. Bu durumda, hücre içeriğinin değiştirdiğinizde boyut düzeltmesini oluşur.  
  
> [!NOTE]
>  Sanal mod kullanarak bir özel veri önbelleği hücre değerlerini bulunduruyorsanız, kullanıcı hücrenin değeri düzenler ancak dışında bir önbelleğe alınan değeri değiştirdiğinizde oluşmaz otomatik boyutlandırma oluşur bir <xref:System.Windows.Forms.DataGridView.CellValuePushed> olay işleyicisi. Bu durumda, çağrı <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> hücre görüntü güncelleştirmek ve geçerli otomatik boyutlandırma modlarını uygulamak için Denetim zorlamak için yöntem.  
  
 Yalnızca bir boyut içerik tabanlı otomatik boyutlandırma etkinleştirildiğinde — bu, sütun veya satır ancak olmayan sütunlar için ancak olmayan satırlar — ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> da etkin, boyut ayarlama ayrıca diğer boyutun değiştiğinde gerçekleşir. Örneğin, satır, ancak olmayan sütunları otomatik boyutlandırma için yapılandırılmışsa ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> olduğu etkinse, kullanıcıların bir sütunun genişliği değiştirmek için sütun Bölücü sürükleyin ve satır yükseklikte otomatik olarak ayarlamak böylece hücre içeriğinin hala tam olarak görüntülenir.  
  
 Satırları ve sütunları içerik tabanlı otomatik boyutlandırma için yapılandırırsanız ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> etkin, <xref:System.Windows.Forms.DataGridView> denetimi hücre içeriğinin değişti ve ideal hücre yükseklik ve genişlik oranı yeni boyutlar hesaplanırken kullanacak her boyutları ayarlayın.  
  
 Üstbilgiler ve satır ve denetim değeri geçersiz kılmaz sütunları boyutlandırma modunu yapılandırmak için aşağıdakilerden birini veya birkaçını ayarlayın <xref:System.Windows.Forms.DataGridView> özellikleri:  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Denetimin sütun boyutlandırma modunu tek bir sütun için geçersiz kılmak için ayarlanmış kendi <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> dışında bir değere özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>. Sütun boyutlandırma modunu gerçekte tarafından belirlenen kendi <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliği. Bu özelliğin değeri sütunun üzerinde temel <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özellik değerini bu değer değilse <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>, bu durumda denetimin <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> değeri devralınır.  
  
 İçerik tabanlı otomatik dikkatli büyük miktarlarda veri çalışırken yeniden boyutlandırma kullanın. Performans cezalarını önlemek için her satırda bir denetim çözümleme yerine yalnızca görüntülenen satırları temel alarak boyutlarını hesapla otomatik boyutlandırma modlarını kullanın. En yüksek performans için böylece hemen sonra yeni verileri gibi belirli zamanlarda boyutlandırabilirsiniz kullanım programlı yerine yeniden boyutlandırma yüklenir.  
  
 Satır, sütun veya satır veya sütun ayarlayarak gizli üstbilgileri içerik tabanlı otomatik boyutlandırma modlarını etkilemez <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> özellik veya Denetim <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> veya <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> özelliklerine `false`. Örneğin, büyük hücre değerini sığması için otomatik olarak boyutlandırılır sonra bir sütun gizli ise, büyük hücre değerini içeren satırı silinirse gizli sütun boyutunu değiştirmez. Otomatik boyutlandırma görünürlük değiştiğinde oluşmaz nedenle sütun değiştirme <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğini yeniden `true` boyutuna, geçerli içeriğine göre yeniden hesaplamak için zorla sağlamaz.  
  
 İçerik tabanlı programlı yeniden boyutlandırma, satırlar, sütunlar ve bunların görünürlük bakılmaksızın üstbilgileri etkiler.  
  
## <a name="programmatic-resizing"></a>Program yeniden boyutlandırma  
 Otomatik boyutlandırma devre dışı bırakıldığında, tam genişlik veya yüksekliğinden satırları, sütunları veya üstbilgileri aşağıdaki özellikleri aracılığıyla programlı olarak ayarlayabilirsiniz:  
  
-   <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Satırlar, sütunlar ve aşağıdaki yöntemleri kullanarak kendi içeriklerin sığması için üstbilgiler program aracılığıyla da boyutlandırabilirsiniz:  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
-   <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Bu yöntemler satırları, sütunları veya bir kez üstbilgileri yerine sürekli yeniden boyutlandırma için yapılandırma boyutlandırılır. Kırpma olmadan tüm hücre içeriğini görüntülemek için yeni boyutlar otomatik olarak hesaplanır. Program aracılığıyla yeniden boyutlandırdığınızda sahip sütunlar <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özellik değerlerini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>, ancak hesaplanan içerik tabanlı genişlikleri sütun orantılı olarak ayarlamak için kullanılır <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerlerini ve genişlikleri olan gerçekte sütun tüm sütunları denetiminin kullanılabilir görüntü alanını doldurmak için bu yeni oranları göre hesaplanır.  
  
 Program yeniden boyutlandırma, sürekli yeniden boyutlandırma ile performans cezalarını önlemek kullanışlıdır. Kullanıcı yeniden boyutlandırılabilir satırları, sütunları ve üstbilgileri ve sütun doldurma modu için başlangıç boyutları sağlamak kullanışlıdır.  
  
 Genellikle, belirli zamanlarda programlama yeniden boyutlandırma yöntemleri çağırır. Örneğin, veri yüklendikten hemen sonra programlı olarak tüm sütunları yeniden boyutlandırmak veya belirli bir hücre değerini değiştirildikten sonra belirli bir satırdan programlı olarak yeniden boyutlandırmak.  
  
## <a name="customizing-content-based-sizing-behavior"></a>İçerik tabanlı boyutlandırma davranışını özelleştirme  
 Türetilen çalışırken boyutlandırma davranışları özelleştirebilirsiniz <xref:System.Windows.Forms.DataGridView> kılarak hücre, satır ve sütun türleri <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>, veya <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> yöntemleri veya çağırarak türetilen bir yeniden boyutlandırma yöntemi aşırı korumalı <xref:System.Windows.Forms.DataGridView> Denetim. Korumalı alan yeniden boyutlandırma yöntemi aşırı aşırı geniş veya uzun hücreleri önleme ideal hücre yükseklik ve genişlik oranı elde etmek için çiftler halinde çalışmak üzere tasarlanmıştır. Örneğin, çağırırsanız `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` , aşırı <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> yöntemi ve değerini geçirin `false` için <xref:System.Boolean> parametresi, aşırı ideal yükseklik ve genişliklerini satırdaki hücreler için hesaplar, ancak satır yükseklikte ayarlanır yalnızca. Ardından çağırmalısınız <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> hesaplanan ideal için sütun genişliklerini ayarlamak için yöntem.  
  
## <a name="content-based-sizing-options"></a>İçerik tabanlı boyutlandırma seçenekleri  
 Boyutlandırma özellikleri ve yöntemleri tarafından kullanılan numaralandırmalar içerik tabanlı boyutlandırma benzer değerlere sahip. Bu değerleri ile hangi hücrelerin tercih edilen boyutları hesaplamak için kullanılan sınırlayabilirsiniz. Tüm boyutlandırma sabit listeleri için görüntülenen hücrelere başvuran adları değerlerle hesaplamalarında görüntülenen satırları sınırlayın. Satır hariç olmak üzere çok sayıda satır çalışırken performans cezasını önlemek kullanışlıdır. Hücre değerlerini üstbilgi veya başlık olmayan hücrelerdeki hesaplamalarda de kısıtlayabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [Windows Forms DataGridView Denetiminde Sütun Doldurma Modu](../../../../docs/framework/winforms/controls/column-fill-mode-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
