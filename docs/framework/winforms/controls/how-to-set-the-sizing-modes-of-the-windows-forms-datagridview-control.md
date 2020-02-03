---
title: DataGridView denetiminin boyutlandırma modlarını ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
ms.openlocfilehash: 15b084afa4149ac43d40aeae7f35f0eaff5ac0e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738398"
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama
Aşağıdaki yordamlarda <xref:System.Windows.Forms.DataGridView> denetimi ve denetimdeki belirli sütunlar için kullanılabilir boyutlandırma seçeneklerini özelleştiren veya birleştiren bazı yaygın senaryolar gösterilmektedir.  
  
### <a name="to-create-a-fixed-width-column"></a>Sabit genişlikte bir sütun oluşturmak için  
  
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özelliğini <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğini `true`ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> özelliğini uygun bir değere ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Boyutunu içeriğe sığacak şekilde ayarlayan bir sütun oluşturmak için  
  
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğini içerik tabanlı boyutlandırma moduna ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Değişen boyut ve önem düzeyi değerleri için Fill-Mode sütunları oluşturmak için  
  
- Bu değeri geçersiz kılmayan tüm sütunlar için boyutlandırma modunu ayarlamak için <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> özelliğini <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> olarak ayarlayın. Sütunların <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özelliklerini, ortalama içerik genişlikleriyle orantılı değerlere ayarlayın. Kısmi içerik görüntülenmesini sağlamak için önemli sütunların <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> özelliklerini ayarlayın.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bu konuda açıklanan boyutlandırma seçeneklerini anlamanıza yardımcı olabilecek bir tanıtım uygulaması sağlar.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Bu demo uygulamasını kullanmak için:  
  
- Formun boyutunu değiştirin. <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri tarafından belirtilen oranları korurken, Fill modundaki sütunların genişliklerini nasıl değiştirdiğini gözlemleyin. Form çok küçük olduğunda bir sütunun <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> değiştirilmesini nasıl önlütürdiğini gözlemleyin.  
  
- Sütun bölücüleri fareyle sürükleyerek sütun boyutlarını değiştirin. Bazı sütunların yeniden boyutlandırılamayacağını ve yeniden boyutlandırılabilir sütunların minimum genişliklerinden daha dar bir şekilde yapıllamayacağını gözlemleyin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
