---
title: ErrorProvider Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: f2a97ab80cde00a47bbdf6830bdba325e1c9f3ef
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880969"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md) bileşeni, bir form veya denetim kullanıcı girişini doğrulamak için kullanılır. Genellikle, bir form üzerinde kullanıcı girişini doğrulama veya dataset içindeki hataları görüntüleme ile birlikte kullanılır. Bir ileti kutusu kapatıldıktan sonra hata iletisi artık görünür olmadığı için bir hata sağlayıcısı bir hata iletisi bir ileti kutusu görüntüleme daha daha iyi bir alternatiftir. <xref:System.Windows.Forms.ErrorProvider> Bileşen bir hata simgesi görüntülenir (![kırmızı daire. içinde beyaz bir ünlem](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)); metin kutusu gibi ilgili denetimin yanında bir araç ipucu görüntülendiğinde kullanıcı fare imlecini hata simgesi üzerinde yerleştirir, hata iletisi dizesi gösteriliyor.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 <xref:System.Windows.Forms.ErrorProvider> Bileşeninin anahtar özellikleri <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, ve <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Kullanırken <xref:System.Windows.Forms.ErrorProvider> verilere bağlı denetimler ile bileşen <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliği sırada bir hata simgesi formda göstermek için bileşeni için uygun bir kapsayıcı için (genellikle Windows Form) ayarlanmalıdır. Bileşen Tasarımcısı'nda eklendiğinde <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliği içeren form için ayarlandığında; kod denetimi eklerseniz bu kendiniz ayarlamanız gerekir.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Özelliği, bir özel hata simgesi varsayılan yerine ayarlanabilir. Zaman <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ErrorProvider> bileşeni, bir veri kümesi için hata iletileri görüntüleyebilirsiniz. Anahtar yöntemi <xref:System.Windows.Forms.ErrorProvider> bileşeni <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemi, hata iletisi dizesi belirtir ve burada hata simgesi görüntülenmelidir.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> Bileşen erişilebilirlik istemcileri için yerleşik destek sağlamaz. Bu bileşen kullanırken uygulamanızı erişilebilir olması için ek, erişilebilir bir geri bildirim mekanizması sağlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ErrorProvider>
- [Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile DataSet içindeki hataları görüntüleme](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Nasıl yapılır: Windows Forms ErrorProvider bileşeni ile Form doğrulama için hata simgeleri görüntüleme](display-error-icons-for-form-validation-with-wf-errorprovider.md)
