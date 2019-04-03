---
title: "Nasıl yapılır: Visual Basic'te kullanılabilir seri bağlantı noktalarını gösterme"
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 57b3a33fecb6128a10ce903fd26724de98acb8c1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834653"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te kullanılabilir seri bağlantı noktalarını gösterme
Bu konu nasıl kullanılacağını açıklar `My.Computer.Ports` Visual Basic'te bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için.  
  
 Kullanılacak bağlantı noktasını seçmek bir kullanıcı izin vermek için seri bağlantı noktası adları yerleştirilir bir <xref:System.Windows.Forms.ListBox> denetimi.  
  
## <a name="example"></a>Örnek  
 Bu örnek döngü tüm dizeler, `My.Computer.Ports.SerialPortNames` özelliğini döndürür. Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarına adlarıdır.  
  
 Genellikle, kullanıcı uygulamayı kullanması gereken hangi seri bağlantı noktası kullanılabilir bağlantı noktaları listesinden seçer. Bu örnekte, seri bağlantı noktası adları içinde depolanan bir <xref:System.Windows.Forms.ListBox> denetimi. Daha fazla bilgi için [ListBox denetimi](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici'de bulunur **bağlantı ve ağ**. Daha fazla bilgi için [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Windows.Forms.dll'e bir proje başvurusu.  
  
-   Üye erişimi <xref:System.Windows.Forms> ad alanı. Ekleme bir `Imports` üye adları kodunuzda tamamen niteleyemiyorsanız deyimi. Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Formunuza sahip bir <xref:System.Windows.Forms.ListBox> adlı Denetim `ListBox1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kullanmak zorunda değil <xref:System.Windows.Forms.ListBox> kullanılabilir seri bağlantı noktası adlarını görüntülemek için denetim. Bunun yerine kullanabileceğiniz bir <xref:System.Windows.Forms.ComboBox> veya diğer denetim. Kullanıcıdan bir yanıt uygulama gereksinimi yoksa, kullanabileceğiniz bir <xref:System.Windows.Forms.TextBox> bilgileri görüntülemek için denetim.  
  
> [!NOTE]
>  Tarafından döndürülen bağlantı noktası adları `My.Computer.Ports.SerialPortNames` Windows 98 çalıştırdığınızda yanlış olabilir. Uygulama hatalarını önlemek için özel durum işleme gibi kullanın `Try...Catch...Finally` deyimi veya `Using` bağlantı noktalarını açmak için bağlantı noktası adları kullanarak deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Nasıl yapılır: Seri bağlantı noktalarına ekli modemleri çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Seri bağlantı noktalarına dizeler gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Seri bağlantı noktalarından dize alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
