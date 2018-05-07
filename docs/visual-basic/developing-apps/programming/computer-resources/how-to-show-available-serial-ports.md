---
title: "Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme"
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c13682ddca69d782ea519e0df703c211df8d12c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme
Bu konuda nasıl kullanılacağını açıklar `My.Computer.Ports` Visual Basic'te bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için.  
  
 Kullanılacak bağlantı noktasını seçmek bir kullanıcı izin vermek için seri bağlantı noktalarının adlarını yerleştirilir bir <xref:System.Windows.Forms.ListBox> denetim.  
  
## <a name="example"></a>Örnek  
 Bu örnek döngü tüm dizeler, `My.Computer.Ports.SerialPortNames` özelliği döndürür. Bu bilgisayardaki kullanılabilir seri bağlantı noktalarına adlarını dizelerdir.  
  
 Genellikle, bir kullanıcı uygulama kullanması gereken hangi seri bağlantı noktası kullanılabilir bağlantı noktaları listeden seçer. Bu örnekte, seri bağlantı noktası adları depolanmış bir <xref:System.Windows.Forms.ListBox> denetim. Daha fazla bilgi için bkz: [ListBox denetimi](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 Bu kod örneği bir IntelliSense kod parçacığı da kullanılabilir. Kod parçacığı Seçici bulunur **bağlantısı ve ağ**. Daha fazla bilgi için bkz: [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   System.Windows.Forms.dll proje başvurusu.  
  
-   Üye erişimi <xref:System.Windows.Forms> ad alanı. Ekleme bir `Imports` üye adlarının kodunuzda tam olarak niteleyemiyorsanız deyimi. Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Formunuz sahip bir <xref:System.Windows.Forms.ListBox> adlı Denetim `ListBox1`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Kullanmak zorunda değil <xref:System.Windows.Forms.ListBox> kullanılabilir seri bağlantı noktası adlarını görüntülemek için denetim. Bunun yerine kullanabileceğiniz bir <xref:System.Windows.Forms.ComboBox> veya diğer denetim. Uygulama kullanıcıdan bir yanıt gerekmez, kullanabileceğiniz bir <xref:System.Windows.Forms.TextBox> bilgileri görüntülemek için denetim.  
  
> [!NOTE]
>  Tarafından döndürülen bağlantı noktası adları `My.Computer.Ports.SerialPortNames` Windows 98 çalıştırdığınızda hatalı olabilir. Uygulama hataları önlemek için özel durum işleme gibi kullanmak `Try...Catch...Finally` deyimi veya `Using` bağlantı noktalarını açmak için bağlantı noktası adları kullanırken deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Nasıl Yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Nasıl Yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Nasıl Yapılır: Seri Bağlantı Noktalarından Dize Alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
