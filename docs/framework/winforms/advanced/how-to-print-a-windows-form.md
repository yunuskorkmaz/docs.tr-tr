---
title: 'Nasıl yapılır: Bir Windows Formunu Yazdırma'
description: CopyFromScreen metodunu kullanarak geçerli Windows formunun bir kopyasının programlı bir şekilde nasıl yazdırılacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174698"
---
# <a name="how-to-print-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunu Yazdırma
Geliştirme sürecinin bir parçası olarak, genellikle Windows formunuzun bir kopyasını yazdırmak isteyeceksiniz. Aşağıdaki kod örneğinde, yöntemi kullanılarak geçerli formun bir kopyasının nasıl yazdırılacağı gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
- Yazıcıya erişim izniniz yok.  
  
- Yüklü bir yazıcı yok.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu kod örneğini çalıştırmak için, bilgisayarınızda kullandığınız yazıcıya erişim izninizin olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Printing.PrintDocument>
- [Nasıl yapılır: GDI+ ile Görüntü İşleme](how-to-render-images-with-gdi.md)
- [Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](how-to-print-graphics-in-windows-forms.md)
