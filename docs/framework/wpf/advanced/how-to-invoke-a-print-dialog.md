---
title: "Nasıl yapılır: Yazdır İletişim Kutusu Çağırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8831566daca6ca36b40fbaaedbec9ff3ca8aaa99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-invoke-a-print-dialog"></a>Nasıl yapılır: Yazdır İletişim Kutusu Çağırma
Uygulamanızdan yazdırma olanağı sağlamak için yalnızca oluşturma açın ve bir <xref:System.Windows.Controls.PrintDialog> nesnesi.  
  
## <a name="example"></a>Örnek  
 <xref:System.Windows.Controls.PrintDialog> Denetimi için bir tek giriş noktası sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], yapılandırması ve [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] iş gönderme. Kullanımı kolay bir denetimdir ve kullanarak oluşturulabilir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] işaretleme veya kod. Aşağıdaki örnekte nasıl örneği ve kodda Denetimi'ni açmak ve ondan yazdırmak nasıl gösterilir. Ayrıca, iletişim kutusu sayfaları belirli bir dizi ayarlama seçeneği kullanıcıya vermek emin olmak nasıl gösterir. Kod örneği, C: sürücüsünün kök dizininde bir dosyada FixedDocumentSequence.xps olduğunu varsayar.  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 İletişim kutusu açıldıktan sonra kullanıcıların bilgisayarlarında yüklü yazıcılar seçmek mümkün olacaktır. Seçme seçeneği de sağlanır [Microsoft XPS Belge Yazıcısı](http://go.microsoft.com/fwlink/?LinkId=147319) oluşturmak için bir [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] yazdırma yerine dosya.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Denetimini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], bu konuda ele alınmıştır karıştırılmamalıdır ile <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> bileşenini [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].  
  
 NET olarak söylemek kullanabileceğiniz <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> hiç iletişim kutusunu açmadan yöntemi. Bu anlamda denetim görünmeyen yazdırma bileşeni kullanılabilir. Ancak performans nedenleriyle kullanın ya da daha iyi olur <xref:System.Printing.PrintQueue.AddJob%2A> yöntemi veya çok biri <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ve <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> yöntemlerini <xref:System.Windows.Xps.XpsDocumentWriter>. Bu konu hakkında daha fazla bilgi için bkz: [program aracılığıyla yazdırma XPS dosyaları](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) ve.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.PrintDialog>  
 [WPF'deki Belgeler](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Yazdırmaya Genel Bakış](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Belge Yazıcısı](http://go.microsoft.com/fwlink/?LinkId=147319)
