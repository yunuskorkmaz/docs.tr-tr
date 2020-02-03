---
title: DataGridViewComboBoxCell açılır listesindeki nesnelere erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
ms.openlocfilehash: 7e76ab1ac9089778e4371f4ee65b06d5ebc570bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746316"
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme
<xref:System.Windows.Forms.ComboBox> denetimi gibi <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve <xref:System.Windows.Forms.DataGridViewComboBoxCell> türleri, açılan listelerine rastgele nesneler eklemenize olanak tanır. Bu özellikle, ilgili nesneleri ayrı bir koleksiyonda depolamak zorunda kalmadan, karmaşık durumları bir açılan listede temsil edebilirsiniz.  
  
 <xref:System.Windows.Forms.ComboBox> denetiminden farklı olarak, <xref:System.Windows.Forms.DataGridView> türler seçili nesneyi almak için bir <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> özelliğine sahip değildir. Bunun yerine, <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> özelliğini iş nesnenizin bir özelliğin adı olarak ayarlamanız gerekir. Kullanıcı bir seçim yaptığında, iş nesnesinin belirtilen özelliği, hücre <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliğini ayarlar.  
  
 İş nesnesini hücre değeri aracılığıyla almak için `ValueMember` özelliği, iş nesnesinin kendisi için bir başvuru döndüren bir özelliği belirtmelidir. Bu nedenle, iş nesnesinin türü denetiminizin altındaysa, türü devralma yoluyla genişleterek böyle bir özelliği eklemeniz gerekir.  
  
 Aşağıdaki yordamlarda, bir açılan listeyi iş nesneleriyle doldurma ve nesneleri hücre <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği aracılığıyla alma işlemleri gösterilmektedir.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Açılan listeye iş nesneleri eklemek için  
  
1. Yeni bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> oluşturun ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> koleksiyonunu doldurun. Alternatif olarak, sütun <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> özelliğini iş nesneleri koleksiyonuna ayarlayabilirsiniz. Ancak, bu durumda, koleksiyonunuzda karşılık gelen bir iş nesnesi oluşturmadan açılan listeye "atanmamış" ekleyemezsiniz.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özelliklerini ayarlayın. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>, açılan listede gösterilecek iş nesnesinin özelliğini gösterir. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>, iş nesnesine bir başvuru döndüren özelliği gösterir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3. İş nesnesi türünün geçerli örneğe bir başvuru döndüren bir özellik içerdiğinden emin olun. Bu özellik, önceki adımda <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> için atanan değerle birlikte adlandırılmalıdır.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Şu anda seçili olan iş nesnesini almak için  
  
- Hücreyi <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliğini alın ve iş nesnesi türüne dönüştürün.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Örnek  
 Tam örnek, iş nesnelerinin bir açılan listede kullanımını gösterir. Örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimi bir `Task` nesneleri koleksiyonuna bağlanır. Her `Task` nesnesi, o göreve atanmış olan `Employee` nesnesini gösteren bir `AssignedTo` özelliğine sahiptir. `Assigned To` sütununda, atanan her çalışana ait `Name` Özellik değeri veya `Task.AssignedTo` Özellik değeri `null`ise "atanmamış" görüntülenir.  
  
 Bu örneğin davranışını görüntülemek için aşağıdaki adımları gerçekleştirin:  
  
1. `Assigned To` sütunundaki atamaları, açılan listelerden farklı değerler seçerek veya Birleşik giriş kutusu hücresinde CTRL + 0 tuşlarına basarak değiştirin.  
  
2. Geçerli atamaları göstermek için `Generate Report` ' ye tıklayın. Bu, `Assigned To` sütununda bir değişikliğin `tasks` koleksiyonunu otomatik olarak güncelleştirdiğini gösterir.  
  
3. Bu satır için geçerli `Employee` nesnesinin `RequestStatus` yöntemini çağırmak için bir `Request Status` düğmesine tıklayın. Bu, seçilen nesnenin başarıyla alındığını gösterir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
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
