---
title: 'Nasıl yapılır: Yüklü yazı tiplerini numaralandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: 0124d2bdd8b9c60dc2bf2508348044d76a2c7eb4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602240"
---
# <a name="how-to-enumerate-installed-fonts"></a>Nasıl yapılır: Yüklü yazı tiplerini numaralandırma
<xref:System.Drawing.Text.InstalledFontCollection> Sınıfının devraldığı <xref:System.Drawing.Text.FontCollection> soyut temel sınıf. Kullanabileceğiniz bir <xref:System.Drawing.Text.InstalledFontCollection> bilgisayarda yüklü yazı tiplerini numaralandırma nesnesi. <xref:System.Drawing.Text.FontCollection.Families%2A> Özelliği bir <xref:System.Drawing.Text.InstalledFontCollection> nesnesi olan bir dizi <xref:System.Drawing.FontFamily> nesneleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bilgisayarda yüklü tüm yazı tipi aileleri adlarını listeler. Kod alır <xref:System.Drawing.FontFamily.Name%2A> her özellik <xref:System.Drawing.FontFamily> tarafından döndürülen dizi nesnesinde <xref:System.Drawing.Text.FontCollection.Families%2A> özelliği. Ailesi adları alınır gibi bunlar için form virgülle ayrılmış bir liste bitiştirilir. Ardından <xref:System.Drawing.Graphics.DrawString%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı virgülle ayrılmış bir liste içinde bir dikdörtgen çizer.  
  
 Kod örneği çalıştırırsanız, çıktıyı aşağıdaki çizimde gösterilen şuna benzer olacaktır.  
  
 ![Yazı tipi yüklü](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.PaintEventHandler>. Ayrıca, almalısınız <xref:System.Drawing.Text> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
