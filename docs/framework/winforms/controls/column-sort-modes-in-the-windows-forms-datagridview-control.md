---
title: "Windows Forms DataGridView Denetiminde Sütun Sıralama Modları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a98e57d325fc7fd9413babb45d235cbb353a0c86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetiminde Sütun Sıralama Modları
<xref:System.Windows.Forms.DataGridView>üç sıralama modları sütuna sahip. Her sütun için sıralama modu aracılığıyla belirtilen <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> aşağıdakilerden birini ayarlanabilir sütunun özelliği <xref:System.Windows.Forms.DataGridViewColumnSortMode> numaralandırma değerleri.  
  
|`DataGridViewColumnSortMode`değer|Açıklama|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|Metin kutusu sütunları için varsayılan değer. Sütun üstbilgileri seçimi için kullanılmadığı sürece, otomatik olarak sütun başlığını tıklatarak sıralar <xref:System.Windows.Forms.DataGridView> bu sütuna göre sıralama düzenini belirten bir simge görüntüler.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|Varsayılan olmayan – metin kutusu sütunlar için. Bu sütun programlamayla sıralama yapabilirsiniz; hiçbir alan sıralama karakter ayrılmış şekilde ancak, sıralama için tasarlanmamıştır.|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|Bu sütun programlamayla sıralama ve alan sıralama karakter ayrılmış.|  
  
 Varsayılan olarak bir sütun için sıralama modu değiştirmek isteyebilirsiniz <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> anlamlı sıralanabilir değerler içeriyorsa. Öğesi durumları temsil eden sayı içeren bir veritabanı sütununa varsa, örneğin, bu sayıları karşılık gelen simgelerle veritabanı sütununa bir görüntü sütunu bağlayarak görüntüleyebilirsiniz. Görüntü görüntüleme değerleri için bir işleyici içine sayısal hücre değerlerini daha sonra değiştirebilirsiniz <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olay. Bu durumda, ayarı <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic> sütunu sıralamak, kullanıcılarınızın olanak tanır. Otomatik sıralama kullanıcılarınızın sayılara karşılık gelen durumlar doğal sırası yoksa bile aynı durumunda olan öğeleri gruplamak için olanak sağlar. Onay kutusu sütunları otomatik sıralama aynı durumda öğeleri gruplandırma için yararlı olduğu başka bir örnek olur.  
  
 Sıralama yapabilirsiniz bir <xref:System.Windows.Forms.DataGridView> program aracılığıyla herhangi bir sütun veya birden çok sütun, ne olursa olsun, değerlere göre <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> ayarlar. Programsal sıralama sıralama için kendi kullanıcı arabirimini (UI) sağlamak istediğinizde ya da özel sıralama uygulamak istediğinizde kullanışlıdır. Sıralama UI yararlıdır sağlanması, örneğin, ayarladığınızda <xref:System.Windows.Forms.DataGridView> sütun başlığı seçimini etkinleştirmek için seçim modu. Sütun başlıklarını sıralama için kullanılamaz karşın, bu durumda, hala ayarlamanız gerekir böylece uygun sıralama karakter görüntülenecek üstbilgileri istediğiniz <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>.  
  
 Programsal sıralama modu olarak ayarlanmış sütunları sıralama karakter otomatik olarak görüntülenmez. Bu sütunlar için simge kendiniz ayarlayarak görüntülemelidir <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> özelliği. Özel sıralama esnekliğini istiyorsanız bu gereklidir. Örneğin, sıralama, <xref:System.Windows.Forms.DataGridView> birden çok sütuna göre sıralama birden çok karakterlerin veya hiçbir sıralama karakter görüntülemek isteyebilirsiniz.  
  
 Program aracılığıyla sıralayabilirsiniz rağmen bir <xref:System.Windows.Forms.DataGridView> herhangi bir sütuna göre anlamlı sıralanabilir değerleri düğmesi sütunlar gibi bazı sütunları içermeyebilir. Bu sütun için bir <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik ayarı <xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable> ; böylece sıralama karakter üstbilgisinde alan ayırmak gerekmez, hiçbir zaman sıralama için kullanılacağını gösterir.  
  
 Zaman bir <xref:System.Windows.Forms.DataGridView> olduğu sıralanmış, sıralama sütunu ve sıralama düzenini değerlerini kontrol ederek belirleyebilirsiniz <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri. Bu değerler sonra özel bir sıralama işlemi anlamlı değildir. Özel sıralama hakkında daha fazla bilgi için bu konunun ilerleyen bölümlerinde özel sıralama bölümüne bakın.  
  
 Zaman bir <xref:System.Windows.Forms.DataGridView> ilişkili ve ilişkisiz sütunları içeren denetim sıralandığı, ilişkisiz sütunlardaki değerleri otomatik olarak korunmasını olamaz. Bu değerleri korumak için sanal modu ayarlayarak uygulamalıdır <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliğine `true` ve işleme <xref:System.Windows.Forms.DataGridView.CellValueNeeded> ve <xref:System.Windows.Forms.DataGridView.CellValuePushed> olaylar. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms DataGridView denetiminde sanal modu uygulama](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md). İlişkili modunda ilişkisiz sütuna göre sıralama desteklenmiyor.  
  
## <a name="programmatic-sorting"></a>Programsal sıralama  
 Sıralama yapabilirsiniz bir <xref:System.Windows.Forms.DataGridView> çağırarak program aracılığıyla kendi <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi.  
  
 `Sort(DataGridViewColumn,ListSortDirection)` , Aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> metodu bir <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.ComponentModel.ListSortDirection> parametre olarak numaralandırma değeri. Bu aşırı anlamlı sıralanabilir, ancak bunu yapılandırmak otomatik sıralama için istemediğiniz değerlerle sütuna göre sıralama yararlıdır. Ne zaman bu aşırı yüklemesini çağırın ve bir sütunla geçirin bir <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> özellik değerinin <xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>, <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> özellikleri otomatik olarak ayarlanır ve uygun sıralama karakter sütun başlığında görüntülenir.  
  
> [!NOTE]
>  Zaman <xref:System.Windows.Forms.DataGridView> denetimin bağlı bir dış veri kaynağına ayarlayarak <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği, `Sort(DataGridViewColumn,ListSortDirection)` yöntemi aşırı yüklemesini bağlanmamış sütunlar için çalışmaz. Ayrıca, <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özelliği `true`, yalnızca ilişkili sütunlar için bu aşırı çağırabilirsiniz. Bir sütun verilere bağlı olup olmadığını belirlemek için denetleyin <xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A> özellik değeri. Bağlanmamış sütunlar ilişkili modunda sıralama desteklenmiyor.  
  
## <a name="custom-sorting"></a>Özel sıralama  
 Özelleştirebileceğiniz <xref:System.Windows.Forms.DataGridView> kullanarak `Sort(IComparer)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi veya işleme <xref:System.Windows.Forms.DataGridView.SortCompare> olay.  
  
 `Sort(IComparer)` Yöntemi aşırı yüklemesini alır uygulayan bir sınıf örneği <xref:System.Collections.IComparer> bir parametre olarak arabirimi. Özel sıralama sağlamak istediğinizde bu aşırı kullanışlıdır. Örneğin, ne zaman bir sütundaki değerlerin doğal bir sıralama yok veya zaman doğal sıralama düzeni uygun değil. Bu durumda, Otomatik sıralama kullanamaz, ancak sütun üstbilgilerini tıklatarak sıralama kullanıcılarınıza hala isteyebilirsiniz. Bu aşırı yüklemesi için bir işleyici içinde çağırabilirsiniz <xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> seçimi için sütun üst bilgileri kullanmıyorsanız olay.  
  
> [!NOTE]
>  `Sort(IComparer)` Yöntemi aşırı yüklemesini çalışır yalnızca <xref:System.Windows.Forms.DataGridView> denetim için dış veri kaynağına bağlı olmayan ve <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik değeri `false`. Bir dış veri kaynağına bağlı sütunlar için sıralama özelleştirmek için veri kaynağı tarafından sağlanan sıralama işlemleri kullanmanız gerekir. Sanal modda bağlanmamış sütunlar için sıralama kendi işlemleri sağlamanız gerekir.  
  
 Kullanılacak `Sort(IComparer)` yöntemi aşırı yüklemesini uygulayan kendi sınıf oluşturmalısınız <xref:System.Collections.IComparer> arabirimi. Bu arabirim uygulamak için sınıfınızı gerektirir <xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType> hangi yöntemi <xref:System.Windows.Forms.DataGridView> geçirir <xref:System.Windows.Forms.DataGridViewRow> nesneler olarak giriş `Sort(IComparer)` yöntemi aşırı yüklemesini çağrılır. Bu, tüm sütunundaki değerlere göre doğru satır sıralama hesaplayabilirsiniz.  
  
 `Sort(IComparer)` Yöntemi aşırı yüklemesini ayarlı değil <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> ve <xref:System.Windows.Forms.DataGridView.SortOrder%2A> her zaman ayarlamanız gerekir böylece özellikleri <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> sıralama karakter görüntülenecek özelliği.  
  
 Alternatif olarak `Sort(IComparer)` yöntemi aşırı yüklemesi için bir işleyici uygulayarak özel sıralama sağlayabilir <xref:System.Windows.Forms.DataGridView.SortCompare> olay. Bu olay, kullanıcılar otomatik sıralama veya çağırdığınızda için yapılandırılan sütun başlıklarını tıklattığında oluşur `Sort(DataGridViewColumn,ListSortDirection)` , aşırı <xref:System.Windows.Forms.DataGridView.Sort%2A> yöntemi. Her satır çifti için doğru düzenlerine hesaplanacağı etkinleştirme denetiminde için olayı oluşur.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.SortCompare> Olay oluşmaz zaman <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği ayarlanmış veya ne zaman <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> özellik değeri `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>  
 [Windows Forms DataGridView denetiminde verileri sıralama](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde sütunlar için sıralama modlarını ayarlama](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
 [Nasıl yapılır: Windows Forms DataGridView denetiminde sıralamayı özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
