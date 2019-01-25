---
title: 'Nasıl yapılır: Bir Windows formunu yazdırma'
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
ms.openlocfilehash: 5e672f40797a90111daefed0be74c941d4cc37b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628142"
---
# <a name="how-to-print-a-windows-form"></a>Nasıl yapılır: Bir Windows formunu yazdırma
Geliştirme sürecinin bir parçası olarak, genellikle Windows formunuza bir kopyasını yazdırmak isteyeceksiniz. Aşağıdaki kod örneği kullanarak geçerli forma bir kopyasını yazdırmak gösterilmektedir <xref:System.Drawing.Graphics.CopyFromScreen%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 İçeren tam bir kod örneğini budur bir `Main` yöntemi.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Aşağıdaki koşullar özel bir duruma neden olabilir:  
  
-   Yazıcı erişmek için izniniz yok.  
  
-   Yüklü yazıcı yok yoktur.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Bu kod örneği çalıştırmak için bilgisayarınızda kullandığınız yazıcıya erişim izni olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Printing.PrintDocument>
- [Nasıl yapılır: GDI + ile görüntü işleme](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
- [Nasıl yapılır: Windows Forms'ta grafik yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
