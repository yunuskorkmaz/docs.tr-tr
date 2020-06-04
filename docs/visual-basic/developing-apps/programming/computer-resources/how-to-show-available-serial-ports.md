---
title: 'Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e7a9166f1879ed0850ca893bed307a0318298bbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401829"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme

Bu konuda `My.Computer.Ports` , Visual Basic ' de bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağı açıklanmaktadır.  
  
 Bir kullanıcının kullanılacak bağlantı noktasını seçmesine izin vermek için seri bağlantı noktalarının adları bir <xref:System.Windows.Forms.ListBox> denetime yerleştirilir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, özelliğin döndürdüğü tüm dizelerin üzerinde döngüye geçer `My.Computer.Ports.SerialPortNames` . Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarının adlarıdır.  
  
 Genellikle, bir kullanıcı uygulamanın kullanılabilir bağlantı noktaları listesinden kullanması gereken seri bağlantı noktasını seçer. Bu örnekte, seri bağlantı noktası adları bir <xref:System.Windows.Forms.ListBox> denetimde depolanır. Daha fazla bilgi için bkz. [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek şunları gerektirir:  
  
- System. Windows. Forms. dll ' ye bir proje başvurusu.  
  
- <xref:System.Windows.Forms>Ad alanının üyelerine erişin. `Imports`Kodunuzda üye adlarını tam olarak nitedıysanız bir ifade ekleyin. Daha fazla bilgi için bkz. [Imports açıklaması (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Formunuzda adlı bir denetim vardır <xref:System.Windows.Forms.ListBox> `ListBox1` .  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 <xref:System.Windows.Forms.ListBox>Kullanılabilir seri bağlantı noktası adlarını göstermek için denetimi kullanmak zorunda değilsiniz. Bunun yerine, bir <xref:System.Windows.Forms.ComboBox> veya başka bir denetim kullanabilirsiniz. Uygulamanın kullanıcıdan bir yanıt ihtiyacı yoksa, <xref:System.Windows.Forms.TextBox> bilgileri göstermek için bir denetim kullanabilirsiniz.  
  
> [!NOTE]
> Tarafından döndürülen bağlantı noktası adları, `My.Computer.Ports.SerialPortNames` Windows 98 üzerinde çalıştırıldığında yanlış olabilir. Uygulama hatalarını engellemek için, bağlantı `Try...Catch...Finally` `Using` noktalarını açmak üzere bağlantı noktası adlarını kullanırken, bildirim veya bildirim gibi özel durum işleme kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Nasıl yapılır: Seri Bağlantı Noktalarına Ekli Modemleri Çevirme](how-to-dial-modems-attached-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarına Dizeler Gönderme](how-to-send-strings-to-serial-ports.md)
- [Nasıl yapılır: Seri Bağlantı Noktalarından Dize Alma](how-to-receive-strings-from-serial-ports.md)
