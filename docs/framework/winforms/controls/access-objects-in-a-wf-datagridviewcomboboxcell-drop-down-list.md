---
title: 'Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 17b7c93effe9338a9e2d6cb207a948a956d9b666
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59334282"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme
Gibi <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve <xref:System.Windows.Forms.DataGridViewComboBoxCell> türleri açılan listelerine rastgele bir nesne eklemek etkinleştirin. Bu özellik, ayrı bir koleksiyonda karşılık gelen nesneleri depolamak zorunda kalmadan bir açılan listedeki karmaşık durumları temsil edebilir.  
  
 Farklı <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridView> türlerine sahip değil bir <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> özelliği şu anda seçilen nesne alınıyor. Bunun yerine, ayarlamalısınız <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> özelliğini, iş nesnesinde bir özelliğin adı. Kullanıcı bir seçim yaptığında, hücre iş nesnesi belirtilen özelliği ayarlar <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.  
  
 İş nesnesi aracılığıyla bir hücre değerini almak için `ValueMember` özelliği, iş nesnesine bir başvuru döndürür bir özelliği belirtmelisiniz. Bu nedenle, iş nesnesi türünü denetiminiz altında değil, devralma yoluyla türü genişleterek böyle bir özellik eklemeniz gerekir.  
  
 Nasıl iş nesnesi ile bir açılan listeyi doldurmak ve hücre nesnelerde almak aşağıdaki yordamları göstermek <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>İş nesnesi aşağı açılan listesine eklemek için  
  
1. Yeni bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve doldurma kendi <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> koleksiyonu. Alternatif olarak, sütun ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliğini iş nesneleri koleksiyonu. Bu durumda, ancak, "atanmamış" açılan listeye koleksiyonunuzda karşılık gelen iş nesne oluşturulmadan ekleyemezsiniz.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. Ayarlama <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> aşağı açılan listede görüntülenecek iş nesnesinin özelliğini gösterir. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> iş nesnesine bir başvuru döndürür özelliği belirtir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. İş nesne türünüz geçerli örneğe bir başvuru döndürür bir özelliği içerdiğinden emin olun. Bu özellik, atanan değer kullanılarak adlandırılmalıdır. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> önceki adımda.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Seçili iş nesnesi alınamadı  
  
-   Hücreyi alma <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği ve iş nesne türüne dönüştürün.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Örnek  
 Tam bir örnek açılır listesindeki nesnelere iş kullanımını gösterir. Örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimin bir koleksiyonuna bağlı `Task` nesneleri. Her `Task` nesnesinin bir `AssignedTo` gösteren özellik `Employee` nesne şu anda bu göreve atanan kişi. `Assigned To` Sütunu görüntüler `Name` her özellik değerini atanan çalışan veya "atanmamış" if `Task.AssignedTo` özellik değeri `null`.  
  
 Bu örnek davranışını görüntülemek için aşağıdaki adımları gerçekleştirin:  
  
1. Atamalarını değiştirmek `Assigned To` farklı değerler aşağı açılan listelerden seçerek veya CTRL + 0, birleşik giriş kutusu hücredeki tuşuna basarak sütun.  
  
2. Tıklayın `Generate Report` geçerli atamaları görüntülenecek. Bu gösteren bir değişiklik `Assigned To` sütun otomatik olarak güncelleştirir `tasks` koleksiyonu.  
  
3. ' A tıklayın bir `Request Status` çağırmak için düğme `RequestStatus` yöntemi geçerli `Employee` ilgili satır için nesne. Bu, seçili nesne başarıyla alınmış gösterir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ComboBox>
- [Windows Forms DataGridView Denetiminde Verileri Görüntüleme](displaying-data-in-the-windows-forms-datagridview-control.md)
