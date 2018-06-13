---
title: 'Nasıl yapılır: Bir Windows Formunu Yazdırma'
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
ms.openlocfilehash: 42940654a0754ac3616ca7983af07d20607f480f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522275"
---
# <a name="how-to-print-a-windows-form"></a>Nasıl yapılır: Bir Windows Formunu Yazdırma
Geliştirme sürecinin bir parçası olarak, genellikle Windows formu bir kopyasını yazdırmak istersiniz. Aşağıdaki kod örneğinde geçerli formun bir kopyasını kullanarak yazdırma gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu içeren bir tam bir kod örneğidir bir `Main` yöntemi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yazıcı erişim iznine sahip değil.  
  
-   Yazıcı yüklü değil.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu kod örneği çalıştırmak için bilgisayarınızda kullandığınız yazıcıya erişim izni olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Nasıl yapılır: GDI+ ile Görüntü İşleme](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
