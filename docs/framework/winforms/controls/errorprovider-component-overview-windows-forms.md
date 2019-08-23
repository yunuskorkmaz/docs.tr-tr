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
ms.openlocfilehash: 3cfd3f306d4a18ce8a194b5197060fbca1d157d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965295"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md) bileşeni, bir form veya denetimdeki Kullanıcı girişini doğrulamak için kullanılır. Genellikle form üzerinde kullanıcı girişini doğrulama veya bir veri kümesi içinde hataları görüntüleme ile birlikte kullanılır. Bir hata sağlayıcısı ileti kutusunda bir hata iletisi görüntülemektan daha iyi bir alternatiftir, çünkü ileti kutusu kapatıldıktan sonra hata iletisi artık görünmez. Bileşen bir hata simgesi (![kırmızı daire içinde beyaz ünlem işareti) görüntüler. metin kutusu gibi ilgili denetimin yanında, Kullanıcı fare işaretçisini hata simgesinin üzerine konumlandırır, bir araç ipucu görünür.](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif) <xref:System.Windows.Forms.ErrorProvider> hata iletisi dizesi gösteriliyor.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Bileşenin anahtar özellikleri, <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> ve<xref:System.Windows.Forms.ErrorProvider.Icon%2A>'dir. <xref:System.Windows.Forms.ErrorProvider> Bileşen, <xref:System.Windows.Forms.ErrorProvider> verilere bağlı denetimlerle birlikte kullanıldığında <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> , bileşenin form üzerinde bir hata simgesi görüntülemesi için ilgili kapsayıcıya (genellikle Windows formu) ayarlanmış olması gerekir. Bileşen tasarımcıya eklendiğinde, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliği içeren form olarak ayarlanır; denetimi koda eklerseniz, kendiniz de ayarlamanız gerekir.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Özelliği varsayılan yerine özel bir hata simgesine ayarlanabilir. <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> Özellik ayarlandığında<xref:System.Windows.Forms.ErrorProvider> , bileşen bir veri kümesi için hata iletileri görüntüleyebilir. <xref:System.Windows.Forms.ErrorProvider> Bileşenin<xref:System.Windows.Forms.ErrorProvider.SetError%2A> anahtar yöntemi, hata iletisi dizesini ve hata simgesinin nerede görüneceğini belirten yöntemidir.  
  
> [!NOTE]
> Bileşen <xref:System.Windows.Forms.ErrorProvider> , erişilebilirlik istemcileri için yerleşik destek sağlamaz. Uygulamanızı bu bileşeni kullanırken erişilebilir hale getirmek için, ek, erişilebilir bir geri bildirim mekanizması sağlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ErrorProvider>
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet Içindeki hataları görüntüleme](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile form doğrulama için hata simgeleri görüntüle](display-error-icons-for-form-validation-with-wf-errorprovider.md)
