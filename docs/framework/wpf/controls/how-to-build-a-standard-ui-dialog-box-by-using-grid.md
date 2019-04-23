---
title: 'Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149532"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Nasıl yapılır: Kılavuz Kullanarak Standart UI İletişim Kutusu Oluşturma
Bu örnek, standart bir oluşturma işlemi gösterilmektedir [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] iletişim kutusunu kullanarak <xref:System.Windows.Controls.Grid> öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek gibi bir iletişim kutusu oluşturur **çalıştırma** iletişim kutusunda [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] işletim sistemi.  
  
 Örnek bir <xref:System.Windows.Controls.Grid> ve kullandığı <xref:System.Windows.Controls.ColumnDefinition> ve <xref:System.Windows.Controls.RowDefinition> beş sütun ve dört satır tanımlamak için sınıflar.  
  
 Bu örnek, ardından ekler ve yerleştirir bir <xref:System.Windows.Controls.Image>, `RunIcon.png`, iletişim kutusunda bulunan resmi temsil edecek. Görüntünün ilk sütun ve satır yerleştirilir <xref:System.Windows.Controls.Grid> (sol üst köşede).  
  
 Ardından, örnek ekler bir <xref:System.Windows.Controls.TextBlock> kalan sütunlarını ilk satırın kapsayan ilk sütuna öğesi. Başka bir ekler <xref:System.Windows.Controls.TextBlock> temsil etmek için ilk sütunda, ikinci satır öğesi **açık** metin kutusu. A <xref:System.Windows.Controls.TextBlock> aşağıdaki gibi veri giriş alanı temsil eder.  
  
 Son olarak, üç örnek ekler <xref:System.Windows.Controls.Button> temsil eden son satırın öğelerine **Tamam**, **iptal**, ve **Gözat** olayları.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Panellere Genel Bakış](panels-overview.md)
- [Nasıl Yapılır Konuları](grid-how-to-topics.md)
