---
title: 'Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345569"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme

Bu konuda, Visual Basic ' de `My.Computer.Ports` bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağı açıklanmaktadır.  
  
 Bir kullanıcının kullanılacak bağlantı noktasını seçmesine izin vermek için seri bağlantı noktalarının adları bir <xref:System.Windows.Forms.ListBox> denetime yerleştirilir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, `My.Computer.Ports.SerialPortNames` özelliğin döndürdüğü tüm dizelerin üzerinde döngüye geçer. Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarının adlarıdır.  
  
 Genellikle, bir kullanıcı uygulamanın kullanılabilir bağlantı noktaları listesinden kullanması gereken seri bağlantı noktasını seçer. Bu örnekte, seri bağlantı noktası adları bir <xref:System.Windows.Forms.ListBox> denetimde depolanır. Daha fazla bilgi için bkz. [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek şunları gerektirir:  
  
- System. Windows. Forms. dll ' ye bir proje başvurusu.  
  
- <xref:System.Windows.Forms> Ad alanının üyelerine erişin. Kodunuzda üye `Imports` adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Formunuzda adlı <xref:System.Windows.Forms.ListBox> `ListBox1`bir denetim vardır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Kullanılabilir seri bağlantı noktası adlarını göstermek için <xref:System.Windows.Forms.ListBox> denetimi kullanmak zorunda değilsiniz. Bunun yerine, bir veya başka <xref:System.Windows.Forms.ComboBox> bir denetim kullanabilirsiniz. Uygulamanın kullanıcıdan bir yanıt ihtiyacı yoksa, bilgileri göstermek için bir <xref:System.Windows.Forms.TextBox> denetim kullanabilirsiniz.  
  
> [!NOTE]
> Tarafından `My.Computer.Ports.SerialPortNames` döndürülen bağlantı noktası adları, Windows 98 üzerinde çalıştırıldığında yanlış olabilir. Uygulama hatalarını engellemek için, bağlantı noktalarını açmak üzere bağlantı noktası adlarını `Try...Catch...Finally` kullanırken, bildirim `Using` veya bildirim gibi özel durum işleme kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
