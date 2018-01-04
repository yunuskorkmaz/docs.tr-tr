---
title: "Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama"
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
- data grids [Windows Forms], setting sizing modes
- DataGridView control [Windows Forms], sizing modes
ms.assetid: e9ad15e6-b4bb-44aa-a767-3738e9db1651
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ae9cfe338e4e9c9ecc4a1fba67164ffc4af5307
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Windows Forms DataGridView Denetiminin Boyutlandırma Modlarını Ayarlama
Aşağıdaki yordamlarda özelleştirme veya boyutlandırma seçenekleri için birleştirme bazı ortak senaryolar gösterilmektedir <xref:System.Windows.Forms.DataGridView> denetim ve belirli bir denetim sütunlar için.  
  
### <a name="to-create-a-fixed-width-column"></a>Bir sabit genişlikli sütun oluşturmak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>, <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> özelliğine <xref:System.Windows.Forms.DataGridViewTriState.False>, <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> özelliğine `true`ve <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> uygun bir değere özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#10)]  
  
### <a name="to-create-a-column-that-adjusts-its-size-to-fit-its-content"></a>Boyutuna içeriğinin sığması için ayarlayan bir sütun oluşturmak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> içerik tabanlı boyutlandırma modunu özelliğine.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#20)]  
  
### <a name="to-create-fill-mode-columns-for-values-of-varying-size-and-importance"></a>Değişen boyutu ve önem derecesi değerlerini doldurma modu sütunlar oluşturmak için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType> özelliğine <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill> bu değeri geçersiz kılmaz tüm sütunları boyutlandırma modunu ayarlamak için. Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> kendi ortalama orantılı değerleri sütunlara özelliklerini içerik genişliği. Ayarlama <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> kısmi içerik görüntüleme emin olmak için önemli sütunları özelliklerini.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#30)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam kod örneği, bu konuda açıklanan boyutlandırma seçenekleri anlamanıza yardımcı olabilir bir tanıtım uygulaması sağlar.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/CS/sizingscenarios.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSizingScenarios#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSizingScenarios/vb/sizingscenarios.vb#00)]  
  
 Bu Demo uygulamayı kullanmak için:  
  
-   Formun boyutunu değiştirin. Oranları koruma tarafından gösterilen sırada doldurma modu sütun genişliklerini nasıl değiştiğini gözlemleyin <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> özellik değerleri. Bir sütun nasıl 's gözlemlemek <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> formun çok küçük olduğunda değiştirmesini engeller.  
  
-   Sütun boyutlarını fareyle sütun Bölücü sürükleyerek değiştirebilirsiniz. Bazı sütunları yeniden boyutlandırılan ve nasıl yeniden boyutlandırılabilir nasıl olamaz gözlemlemek sütun yapılamaz minimum genişliklerini dar.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=nameWithType>
