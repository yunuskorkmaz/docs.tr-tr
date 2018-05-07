---
title: 'Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: ceace5950ec135ea4d52081da7d1de7a820583ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-construct-font-families-and-fonts"></a>Nasıl yapılır: Yazı Tipi Aileleri ve Yazı Tipleri Oluşturma
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yazı tipleri aynı yazı tipi ancak farklı stillerde yazı tipi aileleri gruplandırır. Örneğin, aşağıdaki yazı tipleri Arial yazı tipi ailesinin içerir:  
  
-   Arial normal  
  
-   Arial kalın  
  
-   Arial İtalik  
  
-   Arial Kalın İtalik  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] form aileleri için dört stillerini kullanır: normal, kalın, italik ve kalın italik. Sıfatları gibi *daraltmak* ve *yuvarlanmasını* stilleri; dikkate alınmaz yerine bunların, aile adı bir parçasıdır. Örneğin, Arial dar bir yazı tipi ailesi aşağıdaki üyeleri ile şöyledir:  
  
-   Arial dar normal  
  
-   Arial Narrow Kalın  
  
-   Arial Narrow İtalik  
  
-   Arial Narrow Kalın İtalik  
  
 Metinle çizmeden önce [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], oluşturmak gereken bir <xref:System.Drawing.FontFamily> nesne ve <xref:System.Drawing.Font> nesne. <xref:System.Drawing.FontFamily> Nesnesini belirtir (örneğin, Arial), yazı tipi ve <xref:System.Drawing.Font> nesnesini belirtir. boyutu, stil ve birimler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Normal stili Arial yazı tipi boyutu 16 piksel olarak oluşturur. Aşağıdaki kodda için ilk bağımsız değişken geçirildi <xref:System.Drawing.Font.%23ctor%2A> Oluşturucusu olan <xref:System.Drawing.FontFamily> nesnesi. İkinci bağımsız değişken dördüncü bağımsız değişkeni tarafından tanımlanan birimler cinsinden yazı tipi boyutunu belirtir. Üçüncü bağımsız değişken stilini tanımlar.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> üye <xref:System.Drawing.GraphicsUnit> numaralandırma, ve <xref:System.Drawing.FontStyle.Regular> üyesi <xref:System.Drawing.FontStyle> numaralandırması.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazı Tipleri ve Metin Kullanma](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
