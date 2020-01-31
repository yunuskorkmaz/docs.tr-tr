---
title: DataGridView Denetimindeki seçim modları
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: e20bf6307d77bf189b698e847c6b855c249dc3c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743031"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows Forms DataGridView Denetimindeki Seçim Modları

Bazen uygulamanızın <xref:System.Windows.Forms.DataGridView> denetim içindeki kullanıcı seçimlerini temel alan eylemler gerçekleştirmesini isteyebilirsiniz. Eylemlere bağlı olarak, olası seçim türlerini kısıtlamak isteyebilirsiniz. Örneğin, uygulamanızın Şu anda seçili olan kayıt için bir rapor yazdırabildiğini varsayalım. Bu durumda, <xref:System.Windows.Forms.DataGridView> denetimini bir satırdaki herhangi bir yere tıklamak her zaman tüm satırı seçecek şekilde yapılandırmak isteyebilirsiniz. böylece, tek seferde yalnızca bir satır seçilebilir.

<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> özelliğini aşağıdaki <xref:System.Windows.Forms.DataGridViewSelectionMode> sabit listesi değerlerinden birine ayarlayarak izin verilen seçimleri belirtebilirsiniz.

|DataGridViewSelectionMode değeri|Açıklama|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Bir hücreye tıklamak onu seçer. Satır ve sütun üst bilgileri seçim için kullanılamaz.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Bir hücreye tıklamak onu seçer. Bir sütun başlığına tıkladığınızda sütunun tamamı seçilir. Sütun başlıkları sıralama için kullanılamaz.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Bir hücreye veya sütun başlığına tıkladığınızda sütunun tamamı seçilir. Sütun başlıkları sıralama için kullanılamaz.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Bir hücreye veya bir satır başlığına tıkladığınızda satırın tamamı seçilir.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Varsayılan seçim modu. Bir hücreye tıklamak onu seçer. Bir satır başlığına tıkladığınızda satırın tamamı seçilir.|

> [!NOTE]
> Çalışma zamanında seçim modunun değiştirilmesi, geçerli seçimi otomatik olarak temizler.

Varsayılan olarak, kullanıcılar fareyle sürükleyerek birden çok satır, sütun veya hücre seçebilir, bir seçimi genişletmeyi veya değiştirmeyi seçerken CTRL veya SHIFT tuşuna basarak veya denetimdeki tüm hücreleri seçmek için sol üst başlık hücresine tıklayabilirsiniz. Bu davranışı engellemek için <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliğini `false`olarak ayarlayın.

<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> ve <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> modları, kullanıcıların satırları seçip SIL tuşuna basarak satırları silmesine izin verir. Kullanıcılar yalnızca geçerli hücre düzenleme modunda olmadığında satırları silebilir, <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> özelliği `true`olarak ayarlanır ve temel alınan veri kaynağı Kullanıcı odaklı satır silmeyi destekler. Bu ayarların programlı satır silme işlemini önleyemediğini unutmayın.

## <a name="programmatic-selection"></a>Programlı seçim

Geçerli seçim modu, programlama seçiminin ve Kullanıcı seçiminin davranışını kısıtlar. <xref:System.Windows.Forms.DataGridView> denetiminde bulunan herhangi bir hücre, satır veya sütunun `Selected` özelliğini ayarlayarak, geçerli seçimi programlı bir şekilde değiştirebilirsiniz. Ayrıca seçim moduna bağlı olarak <xref:System.Windows.Forms.DataGridView.SelectAll%2A> yöntemi aracılığıyla denetimdeki tüm hücreleri seçebilirsiniz. Seçimi temizlemek için <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> yöntemi kullanın.

<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> özelliği `true`olarak ayarlanırsa, öğenin `Selected` özelliğini değiştirerek bunları seçimden <xref:System.Windows.Forms.DataGridView> öğeler ekleyebilir veya seçimden kaldırabilirsiniz. Aksi takdirde, `Selected` özelliğinin bir öğe için `true` olarak ayarlanması, diğer öğeleri seçimden otomatik olarak kaldırır.

<xref:System.Windows.Forms.DataGridView.CurrentCell%2A> özelliğinin değerini değiştirmenin geçerli seçimi değiştirmediğini unutmayın.

<xref:System.Windows.Forms.DataGridView> denetiminin <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>ve <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> özelliklerini kullanarak şu anda seçili olan hücre, satır veya sütun koleksiyonunu elde edebilirsiniz. Denetimdeki her hücre seçildiğinde bu özelliklere erişmek verimsiz değildir. Bu durumda bir performans cezasından kaçınmak için öncelikle <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> yöntemi kullanın. Ayrıca, seçilen hücre, satır veya sütun sayısını öğrenmek için bu koleksiyonlara erişme verimsiz olabilir. Bunun yerine, <xref:System.Windows.Forms.DataGridViewElementStates.Selected> değerini geçirerek <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>veya <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> yöntemini kullanmanız gerekir.

> [!TIP]
> Seçilen hücrelerin programlı kullanımını gösteren örnek kod <xref:System.Windows.Forms.DataGridView> sınıfına genel bakış bölümünde bulunabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Nasıl yapılır: Windows Forms DataGridView Denetiminin Seçim Modunu Ayarlama](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
