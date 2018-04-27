---
title: 'Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4577a3bf8c772198ffca6d558bec370f9a668f70
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Nasıl yapılır: Kullanıcıların Windows Forms DataGridView Denetiminden Panoya Birden Fazla Hücre Kopyalamasına Olanak Tanıma
Hücre kopyalama etkinleştirdiğinizde, verileri olun, <xref:System.Windows.Forms.DataGridView> denetim diğer uygulamalara kolayca erişilebilir <xref:System.Windows.Forms.Clipboard>. Seçili hücreleri değerlerini dizelere dönüştürülür ve panoya not defteri ve Excel gibi uygulamaları yapıştırma sekmeyle ayrılmış metin değerleri ve Word gibi uygulamalar yapıştırma HTML biçimli bir tablo olarak eklenir.  
  
 Hücre değerlerini yalnızca kopyalama, satır ve sütun başlık metni panoya verilere dahil etmek veya yalnızca kullanıcıların tüm satır veya sütun seçtiğinizde üstbilgi metni içeren hücre kopyalama yapılandırabilirsiniz.  
  
 Seçim modu bağlı olarak, kullanıcılar hücre birden çok bağlantısı kesilmiş grupları seçebilirsiniz. Bir kullanıcı panoya hücreleri kopyaladığında, satırları ve sütunları yok seçili hücreler içeren kopyalanmaz. Diğer tüm satır veya sütun satırları ve sütunları Panoya kopyalanan verileri tablosuna haline gelir. Bu satır veya sütun seçili hücreleri boş yer tutucu olarak panoya kopyalanır.  
  
### <a name="to-enable-cell-copying"></a>Hücre kopyalama etkinleştirmek için  
  
-   Ayarlama <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> özelliği.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki tam kod örneği hücreleri panoya nasıl kopyalanacağını gösterir. Bu örnek Pano kullanmaya seçili hücreleri kopyalar bir düğme içerir <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> Pano içeriği bir metin kutusunda yöntemi ve görüntüler.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu gerektirir:  
  
-   N: System ve N:System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
