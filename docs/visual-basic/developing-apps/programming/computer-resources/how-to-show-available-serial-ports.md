---
title: 'Nasıl yapılır: Kullanılabilir Seri Bağlantı Noktalarını Gösterme'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: b19bdd56311ab7029fb224256d138a0dc0dd8ddc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557352"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'te Kullanılabilecek Seri Bağlantı Noktalarını Gösterme

Bu konuda `My.Computer.Ports` , Visual Basic ' de bilgisayarın kullanılabilir seri bağlantı noktalarını göstermek için nasıl kullanılacağı açıklanmaktadır.  
  
 Bir kullanıcının kullanılacak bağlantı noktasını seçmesine izin vermek için seri bağlantı noktalarının adları bir <xref:System.Windows.Forms.ListBox> denetime yerleştirilir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, özelliğin döndürdüğü tüm dizelerin üzerinde döngüye geçer `My.Computer.Ports.SerialPortNames` . Bu dizeler bilgisayardaki kullanılabilir seri bağlantı noktalarının adlarıdır.  
  
 Genellikle, bir kullanıcı uygulamanın kullanılabilir bağlantı noktaları listesinden kullanması gereken seri bağlantı noktasını seçer. Bu örnekte, seri bağlantı noktası adları bir <xref:System.Windows.Forms.ListBox> denetimde depolanır. Daha fazla bilgi için bkz. [ListBox Control](/dotnet/desktop/winforms/controls/listbox-control-windows-forms).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Bu kod örneği, bir IntelliSense kod parçacığı olarak da kullanılabilir. Kod parçacığı seçicide, **bağlantı ve ağ**bölümünde bulunur. Daha fazla bilgi için bkz. [kod parçacıkları](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu örnek şunları gerektirir:  
  
- System.Windows.Forms.dll bir proje başvurusu.  
  
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
