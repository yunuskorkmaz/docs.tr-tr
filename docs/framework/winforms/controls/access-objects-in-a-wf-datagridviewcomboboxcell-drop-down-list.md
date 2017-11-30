---
title: "Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0fac2e73e76ad49a5b1ce6942f3ae2b4c0584e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a>Nasıl yapılır: Windows Forms DataGridViewComboBoxCell Açılır Listesindeki Nesnelere Erişme
Gibi <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve <xref:System.Windows.Forms.DataGridViewComboBoxCell> türleri açılan listelerine rasgele nesne eklemek etkinleştirir. Bu özellik, ayrı bir koleksiyonda karşılık gelen nesneleri depolamak zorunda kalmadan bir açılan listedeki karmaşık durumları temsil edebilir.  
  
 Farklı <xref:System.Windows.Forms.ComboBox> denetimi <xref:System.Windows.Forms.DataGridView> türlerine sahip değil bir <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> şu anda seçili nesnenin alma özelliği. Bunun yerine, ayarlamalısınız <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> veya <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> özelliği, iş nesnesi üzerinde bir özellik adı. Kullanıcı bir seçim yaptığında, hücre iş nesnesi belirtilen özelliği ayarlar <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.  
  
 Hücre değeri ile iş nesnesi almak için `ValueMember` özelliği, iş nesnesine başvuru döndüren bir özelliği belirtmelisiniz. Bu nedenle, iş nesnesi türünde denetiminiz altında değil, devralma üzerinden türü genişleterek böyle bir özellik eklemeniz gerekir.  
  
 Aşağıdaki yordamlarda açılan listeyi iş nesnelerle doldurmak ve hücre nesnelerde almak nasıl gösterilmektedir <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği.  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a>Aşağı açılan listeye iş nesneleri eklemek için  
  
1.  Yeni bir <xref:System.Windows.Forms.DataGridViewComboBoxColumn> ve doldurmak kendi <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> koleksiyonu. Alternatif olarak, sütun ayarlayabilirsiniz <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> iş nesneleri koleksiyonu özelliğine. Bu durumda, ancak, "atanmamış" aşağı açılan listesine koleksiyonunuzda karşılık gelen bir iş nesnesini oluşturmadan ekleyemezsiniz.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  Ayarlama <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> ve <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> özellikleri. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>aşağı açılan listede görüntülenecek iş nesnesinin özelliğini gösterir. <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>İş nesnesi için bir başvuru döndürür özelliği gösterir.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  İş nesne türü geçerli örneğine başvuru döndüren bir özelliği içerdiğinden emin olun. Bu özellik, atanan değer ile adlandırılmalıdır <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> önceki adımda.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a>Şu anda seçili iş nesnesi alınamadı  
  
-   Hücre alma <xref:System.Windows.Forms.DataGridViewCell.Value%2A> özelliği ve iş nesne türüne dönüştürün.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a>Örnek  
 Tam bir örnek iş nesneleri bir açılan listedeki kullanımını göstermektedir. Örnekte, bir <xref:System.Windows.Forms.DataGridView> denetimi bir koleksiyona bağlı `Task` nesneleri. Her `Task` nesnesi bir `AssignedTo` gösteren özellik `Employee` şu anda bu göreve atanan nesne. `Assigned To` Sütunu görüntüler `Name` her özellik değerini atanan çalışan veya "atanmamış" IF `Task.AssignedTo` özellik değeri `null`.  
  
 Bu örnek davranışını görüntülemek için aşağıdaki adımları gerçekleştirin:  
  
1.  Atamalarını değiştirmek `Assigned To` farklı değerler aşağı açılan listelerden seçerek veya CTRL + 0 birleşik giriş kutusu hücresinde tuşuna basarak sütun.  
  
2.  Tıklatın `Generate Report` geçerli atamaları görüntülemek için. Bu gösteren bir değişiklik `Assigned To` sütun otomatik olarak güncelleştirir `tasks` koleksiyonu.  
  
3.  Tıklatın bir `Request Status` çağırmak için düğmesini `RequestStatus` yöntemi geçerli `Employee` ilgili satır nesnesi. Bu, seçili nesnenin başarıyla aldı olduğunu gösterir.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [Windows Forms DataGridView denetiminde verileri görüntüleme](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
