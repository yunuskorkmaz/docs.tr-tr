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
ms.openlocfilehash: a8e2e05877746dfb043b7e8ac2a6c2b7017883c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960409"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri
<xref:System.Windows.Forms.DataGridView>satırlar, sütunlar ve üstbilgiler birçok farklı oluşumun sonucu olarak boyutu değiştirebilir. Aşağıdaki tabloda bu oluşumlar gösterilmektedir.  
  
|Oluşum|Açıklama|  
|----------------|-----------------|  
|Kullanıcı yeniden boyutlandırma|Kullanıcılar, satır, sütun veya üstbilgi bölücüleri sürükleyerek veya çift tıklayarak boyut ayarlamaları yapabilir.|  
|Yeniden boyutlandırma denetimi|Sütun dolgusu modunda, denetim genişliği değiştiğinde sütun genişlikleri değişir; Örneğin, denetim üst biçimine yerleştirildiğinde ve Kullanıcı formu yeniden boyutlandırdığında.|  
|Hücre değeri değişikliği|İçerik tabanlı otomatik boyutlandırma modlarında, boyutlar yeni görüntüleme değerlerine uyacak şekilde değişir.|  
|Yöntem çağrısı|Programlı içerik tabanlı yeniden boyutlandırma, yöntem çağrısı sırasında hücre değerlerine göre fırsatçı boyut ayarlamaları yapmanızı sağlar.|  
|Özellik ayarı|Ayrıca, belirli yükseklik ve genişlik değerlerini de ayarlayabilirsiniz.|  
  
 Varsayılan olarak, Kullanıcı yeniden boyutlandırma etkindir, otomatik boyutlandırma devre dışıdır ve sütunlarından daha geniş hücre değerleri kırpılır.  
  
 Aşağıdaki tabloda, varsayılan davranışı ayarlamak veya belirli etkilere ulaşmak için belirli boyutlandırma seçeneklerini kullanmak üzere kullanabileceğiniz senaryolar gösterilmektedir.  
  
|Senaryo|Uygulama|  
|--------------|--------------------|  
|Yatay kaydırma çubuğunu görüntülemeden, denetimin tamamının genişliğini kaplayan görece az sayıda sütunda benzer boyutta verileri görüntülemek için sütun dolgusu modunu kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>.|  
|Sütun dolgusu modunu, değişen boyutlarda görüntüleme değerleriyle kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Sütun <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özelliklerini ayarlayarak veya denetimi verilerle doldurduktan sonra Denetim <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> yöntemini çağırarak göreli sütun genişliklerini başlatın.|  
|Sütun dolgusu modunu, değişen önem derecesine sahip değerlerle birlikte kullanın.|Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>. Bazı verileri <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> her zaman görüntülemesi gereken sütunlar için büyük değerler ayarlayın veya belirli sütunlar için Fill modundan başka bir boyutlandırma seçeneği kullanın.|  
|Denetim arka planının görüntülenmesini önlemek için sütun dolgusu modunu kullanın.|Son sütunun <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> özelliğini olarak ayarlayın ve diğer sütunlar için diğer boyutlandırma seçeneklerini kullanın. <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> Diğer sütunlar kullanılabilir alanın çok büyük bölümünü kullanıyorsa, son sütunun <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özelliğini ayarlayın.|  
|Simge veya KIMLIK sütunu gibi sabit genişlikte bir sütun görüntüler.|Sütunu için <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> ve<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> olarak ayarlayın<xref:System.Windows.Forms.DataGridViewTriState.False> . <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> Özelliği ayarlayarak veya denetimi verilerle doldurduktan sonra Denetim <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> yöntemini çağırarak genişliğini başlatın.|  
|Kırpma oluşmasını önlemek ve alan kullanımını iyileştirmek için hücre içerikleri değiştiğinde boyutları otomatik olarak ayarlayın.|Otomatik boyutlandırma özelliğini, içerik tabanlı boyutlandırma modunu temsil eden bir değere ayarlayın. Büyük miktarlarda verilerle çalışırken bir performans cezasından kaçınmak için, yalnızca görüntülenen satırları hesaplayan bir boyutlandırma modu kullanın.|  
|Birçok satırla çalışırken performans cezalarını önlemek için boyutları, görüntülenecek satırlardaki değerlere uyacak şekilde ayarlayın.|Otomatik veya programlı yeniden boyutlandırmadan uygun boyutlandırma modu numaralandırma değerlerini kullanın. Kaydırma sırasında boyutları yeni görüntülenecek satırlarda sığacak şekilde ayarlamak için bir <xref:System.Windows.Forms.DataGridView.Scroll> olay işleyicisinde bir yeniden boyutlandırma yöntemi çağırın. Kullanıcı çift tıklama yeniden boyutlandırmayı özelleştirmek için, yalnızca görüntülenen satırlardaki değerlerin yeni boyutları belirlemesi için bir <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> veya <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> olay işleyicisinde bir yeniden boyutlandırma yöntemi çağırın.|  
|Performans cezalarını önlemek veya Kullanıcı yeniden boyutlandırmayı etkinleştirmek için boyutları yalnızca belirli zamanlarda hücre içeriğine uyacak şekilde ayarlayın.|Bir olay işleyicisinde içerik tabanlı bir yeniden boyutlandırma yöntemi çağırın. Örneğin, bağlamayı tamamladıktan sonra <xref:System.Windows.Forms.DataGridView.DataBindingComplete> boyutları başlatmak için olayını kullanın ve kullanıcı düzenlemelerini veya bir <xref:System.Windows.Forms.DataGridView.CellValidated> bağlantılı <xref:System.Windows.Forms.DataGridView.CellValueChanged> veri kaynağındaki değişiklikleri dengelemek üzere boyutları ayarlamak için veya olayını işleyin.|  
|Çok satırlı hücre içerikleri için satır yüksekliklerini ayarlayın.|Sütun genişliklerinin metin paragraflarını görüntülemek için uygun olduğundan emin olun ve yükseklikleri ayarlamak için otomatik veya programlı içerik tabanlı satır boyutlandırmayı kullanın. Ayrıca, <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> <xref:System.Windows.Forms.DataGridViewTriState.True>çok satırlı içeriğe sahip hücrelerin bir hücre stili değeri kullanılarak görüntülendiğinden emin olun.<br /><br /> Genellikle, sütun genişliklerini korumak veya satır yükseklikleri ayarlamadan önce belirli genişliklere ayarlamak için bir otomatik sütun boyutlandırma modu kullanırsınız.|  
  
## <a name="resizing-with-the-mouse"></a>Fareyle yeniden boyutlandırma  
 Varsayılan olarak, kullanıcılar hücre değerlerine göre otomatik boyutlandırma modu kullanmayan satırları, sütunları ve üst bilgileri yeniden boyutlandırabilirler. Kullanıcıların sütun dolgusu modu gibi diğer modlarda yeniden boyutlandırmasını engellemek için aşağıdaki <xref:System.Windows.Forms.DataGridView> özelliklerden birini veya daha fazlasını ayarlayın:  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 Ayrıca, kullanıcıların <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> özelliklerini ayarlayarak tek tek satırları veya sütunları yeniden boyutlandırmasını engelleyebilirsiniz. Varsayılan olarak, <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> Özellik değeri sütunlar için <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> özellik <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> değerini ve satırlar için özellik değerini temel alır. Açıkça veya <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> olarak<xref:System.Windows.Forms.DataGridViewTriState.False>ayarlarsanız, belirtilen değer bu satır veya sütun için denetim değerini geçersiz kılar. <xref:System.Windows.Forms.DataGridViewTriState.True> Devralmayı <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> geri <xref:System.Windows.Forms.DataGridViewTriState.NotSet> yüklemek için olarak ayarlayın.  
  
 , Değer devralmayı <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> <xref:System.Windows.Forms.DataGridViewTriState.NotSet> <xref:System.Windows.Forms.DataGridView> geri yüklerken, satır veya sütun bir denetime eklenmediği takdirde özellik hiçbir şekilde bir değer döndürmez. <xref:System.Windows.Forms.DataGridViewTriState.NotSet> Bir satır veya sütunun <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> Özellik değerinin devralınıp alınmayacağını belirlemeniz gerekiyorsa, <xref:System.Windows.Forms.DataGridViewElement.State%2A> özelliğini inceleyin. Değer bayrağı içeriyorsa ,<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> Özellik değeri devralınmaz. <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> <xref:System.Windows.Forms.DataGridViewElement.State%2A>  
  
## <a name="automatic-sizing"></a>Otomatik boyutlandırma  
 <xref:System.Windows.Forms.DataGridView> Denetimde iki tür otomatik boyutlandırma vardır: sütun dolgusu modu ve içerik tabanlı otomatik boyutlandırma.  
  
 Sütun dolgusu modu denetimdeki görünür sütunların denetimin görüntüleme alanının genişliğini doldurmasını sağlar. Bu mod hakkında daha fazla bilgi için, [Windows Forms DataGridView Denetimindeki sütun dolgusu moduna](column-fill-mode-in-the-windows-forms-datagridview-control.md)bakın.  
  
 Ayrıca, satırları, sütunları ve başlıkları, boyutlarını otomatik olarak hücre içeriklerine uyacak şekilde ayarlamak için de yapılandırabilirsiniz. Bu durumda, hücre içerikleri değiştiğinde Boyut ayarlaması oluşur.  
  
> [!NOTE]
> Sanal modu kullanarak özel bir veri önbelleğinde hücre değerlerini korudıysanız, Kullanıcı bir hücre değerini düzenlediğinde, ancak önbelleğe alınmış bir değeri bir <xref:System.Windows.Forms.DataGridView.CellValuePushed> olay işleyicisi dışında değiştirdiğinizde gerçekleşmediğinde otomatik boyutlandırma oluşur. Bu durumda, denetimin hücre görüntüsünü <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> güncelleştirmesine zorlamak ve geçerli otomatik boyutlandırma modlarını uygulamak için yöntemini çağırın.  
  
 İçerik tabanlı otomatik boyutlandırma yalnızca bir boyut için etkinse (yani, satırlar için veya sütunlar için ya da satırlar için de etkinse) <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> , aynı zamanda diğer boyutun her değiştirişinde boyut ayarı da oluşur. Örneğin, satırlar, ancak sütunlar otomatik boyutlandırma için yapılandırılmamışsa ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> etkinse, kullanıcılar sütun ayırıcılarını bir sütunun genişliğini değiştirmek için sürükleyebilir ve satır yükseklikleri, hücre içeriğinin hala tam olarak görüntülenmesini sağlayacak şekilde otomatik olarak ayarlanır.  
  
 İçerik tabanlı otomatik boyutlandırma için hem satır hem de sütun yapılandırırsanız ve <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> etkinleştirilirse <xref:System.Windows.Forms.DataGridView> denetim, hücre içerikleri değiştiğinde boyutları ayarlar ve yeni boyutları hesaplarken ideal bir hücre yüksekliği genişliği oranını kullanır.  
  
 Üst bilgiler ve satırlar için boyutlandırma modunu ve denetim değerini geçersiz kılmayan sütunları yapılandırmak için aşağıdaki <xref:System.Windows.Forms.DataGridView> özelliklerden birini veya daha fazlasını ayarlayın:  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 Tek bir sütun için denetimin sütun boyutlandırma modunu geçersiz kılmak için, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğini dışında <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>bir değer olarak ayarlayın. Bir sütunun boyutlandırma modu aslında <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> özelliği tarafından belirlenir. Bu özelliğin değeri, değer olmadığı <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>takdirde, denetimin <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> değeri Devralınana kadar sütunun özellik değerini temel alır.  
  
 Büyük miktarlarda verilerle çalışırken dikkatli bir şekilde içerik tabanlı otomatik yeniden boyutlandırmayı kullanın. Performans cezalarını önlemek için, denetimdeki her satırı analiz etmek yerine yalnızca görüntülenen satırlara göre boyutları hesaplayan otomatik boyutlandırma modlarını kullanın. En yüksek performans için, yeni veriler yüklendikten hemen sonra, belirli zamanlarda yeniden boyutlandırabilmeniz için, programlama yoluyla yeniden boyutlandırmayı kullanın.  
  
 İçerik tabanlı otomatik boyutlandırma modları, satır veya <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> sütun özelliğini ya da Denetim <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> veya <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> özellikleri olarak `false`ayarlayarak gizlediğiniz satırları, sütunları veya üstbilgileri etkilemez. Örneğin, bir sütun, büyük bir hücre değerine sığacak şekilde otomatik olarak boyutlandırıldığından, büyük hücre değerini içeren satır silinirse gizli sütun boyutunu değiştirmez. Görünürlük değiştiğinde otomatik boyutlandırma gerçekleşmez, bu nedenle Column <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> özelliğinin ' i ' olarak `true` değiştirmek, geçerli içeriğine göre boyutunu yeniden hesaplamaya zorlamaz.  
  
 Programlı içerik tabanlı yeniden boyutlandırma, görünürlüğü ne olursa olsun satırları, sütunları ve başlıkları etkiler.  
  
## <a name="programmatic-resizing"></a>Programlı yeniden boyutlandırma  
 Otomatik boyutlandırma devre dışı bırakıldığında, aşağıdaki özellikler aracılığıyla satır, sütun veya üst bilgilerin tam genişliğini veya yüksekliğini programlı bir şekilde ayarlayabilirsiniz:  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 Ayrıca, aşağıdaki yöntemleri kullanarak satırları, sütunları ve başlıkları içeriğine uyacak şekilde yeniden boyutlandırabilirsiniz:  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 Bu yöntemler, sürekli yeniden boyutlandırma için yapılandırmak yerine satırları, sütunları veya başlıkları bir kez yeniden boyutlandıracaktır. Yeni boyutlar, tüm hücre içeriklerini kırpma olmadan görüntüleyecek şekilde otomatik olarak hesaplanır. Ancak özellik <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>değerlerine sahip sütunları program aracılığıyla yeniden boyutlandırdığınızda, hesaplanmış içerik tabanlı genişlikler sütun <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özelliği değerlerini orantılı şekilde ayarlamak için kullanılır ve aslında sütun genişlikleri ardından, tüm sütunların denetimin kullanılabilir görüntü alanını doldurması için bu yeni oranlarına göre hesaplanır.  
  
 Programlı yeniden boyutlandırma, sürekli yeniden boyutlandırmayla performans cezalarını önlemek için yararlıdır. Ayrıca, Kullanıcı yeniden boyutlandırılabilir satırlar, sütunlar ve üstbilgiler için ve sütun dolgusu modu için başlangıç boyutları sağlamak yararlı olur.  
  
 Genellikle programlı yeniden boyutlandırma yöntemlerini belirli zamanlarda çağıracaksınız. Örneğin, verileri yükledikten hemen sonra tüm sütunları programlama yoluyla yeniden boyutlandırabilir veya belirli bir hücre değeri değiştirildikten sonra programlı olarak belirli bir satırı yeniden boyutlandırabilirsiniz.  
  
## <a name="customizing-content-based-sizing-behavior"></a>Içerik tabanlı boyutlandırma davranışını özelleştirme  
 , <xref:System.Windows.Forms.DataGridView> , Veya <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType> yöntemlerinigeçersiz<xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> kılarak ya da türetilmiş bir üzerinde korumalı yeniden boyutlandırma yöntemi yüklerini çağırarak, türetilmiş hücre, satır ve sütun türleriyle çalışırken boyutlandırma davranışlarını özelleştirebilirsiniz. denetimle. Korunan yeniden boyutlandırma yöntemi aşırı yüklemeleri, çok geniş veya uzun hücrelerden oluşan ideal bir hücre yüksekliğini genişlik oranını elde etmek üzere çiftler halinde çalışmak üzere tasarlanmıştır. `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` Örneğin, <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> yönteminin aşırı yüklemesini çağırır ve <xref:System.Boolean> parametresi `false` için değerini geçirirseniz, aşırı yükleme satırdaki hücrelerin ideal yüksekliklerini ve genişliklerini hesaplar, ancak satır yüksekliklerini ayarlar yalnızca. Daha sonra sütun genişliklerinin <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> hesaplanmış ideal olarak ayarlanması için yöntemini çağırmanız gerekir.  
  
## <a name="content-based-sizing-options"></a>İçerik tabanlı boyutlandırma seçenekleri  
 Boyutlandırma özellikleri ve yöntemleri tarafından kullanılan numaralandırmalar, içerik tabanlı boyutlandırma için benzer değerlere sahiptir. Bu değerlerle, tercih edilen boyutları hesaplamak için hangi hücrelerin kullanılacağını sınırlayabilirsiniz. Tüm boyutlandırma Numaralandırmalar için, görüntülenen hücrelere başvuran adlara sahip değerler, görüntülenen satırlardaki hücrelere hesaplamalarını sınırlar. Satırları dışarıda bırakmak, büyük miktarda satırla çalışırken performans cezasından kaçınmak için faydalıdır. Ayrıca, üst bilgi veya üst bilgi olmayan hücrelerdeki hücre değerlerine yönelik hesaplamaları kısıtlayabilirsiniz.  
  
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
