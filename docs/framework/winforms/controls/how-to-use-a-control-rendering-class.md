---
title: 'Nasıl yapılır: Denetim İşleme Sınıfı Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
ms.openlocfilehash: e5b82c3317d2d162fbd5a182166a9e0061fd770e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-control-rendering-class"></a>Nasıl yapılır: Denetim İşleme Sınıfı Kullanma
Bu örnek nasıl kullanılacağı ortaya <xref:System.Windows.Forms.ComboBoxRenderer> aşağı açılan okunu bir birleşik giriş kutusu denetimi oluşturmak için sınıfı. Örnek oluşan <xref:System.Windows.Forms.Control.OnPaint%2A> basit bir özel denetim yöntemi. <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> Özelliği görsel stiller uygulama windows istemci alanında etkinleştirilip etkinleştirilmeyeceğini belirlemek için kullanılır. Görsel stiller etkin olup olmadığını sonra <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> yöntemi, aşağı açılan okunu görsel stilde; sokacak Aksi halde, <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> yöntemi, aşağı açılan okunu Klasik Windows stilinde sokacak.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Özel bir denetim türetilmiş <xref:System.Windows.Forms.Control> sınıfı.  
  
-   A <xref:System.Windows.Forms.Form> özel denetim barındıran.  
  
-   Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, ve <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> ad alanları.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetimleri Görsel Stilde İşleme](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
