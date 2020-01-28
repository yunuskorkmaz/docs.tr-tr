---
title: ErrorProvider Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: b66e97d97d0d8c2ea4e9bdba29f8ff35e486e1f6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745797"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [ErrorProvider](errorprovider-component-windows-forms.md) bileşeni, bir form veya denetimdeki Kullanıcı girişini doğrulamak için kullanılır. Genellikle form üzerinde kullanıcı girişini doğrulama veya bir veri kümesi içinde hataları görüntüleme ile birlikte kullanılır. Bir hata sağlayıcısı ileti kutusunda bir hata iletisi görüntülemektan daha iyi bir alternatiftir, çünkü ileti kutusu kapatıldıktan sonra hata iletisi artık görünmez. <xref:System.Windows.Forms.ErrorProvider> bileşen bir hata simgesi (kırmızı daire içinde beyaz bir ünlem işareti![, örneğin, bir metin kutusu gibi ilgili denetimin yanındaki](./media/errorprovider-component-overview-windows-forms/vb-error-provider-icon.gif)) görüntüler; Kullanıcı fare işaretçisini hata simgesinin üzerine konumlandırır, hata iletisi dizesinin gösterildiği bir araç Ipucu görüntülenir.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 <xref:System.Windows.Forms.ErrorProvider> bileşenin anahtar özellikleri <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>ve <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Veri bağlantılı denetimlerle <xref:System.Windows.Forms.ErrorProvider> bileşeni kullanırken, bileşenin form üzerinde bir hata simgesi görüntülemesi için, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliğinin uygun kapsayıcıya (genellikle Windows formu) ayarlanması gerekir. Bileşen tasarımcıya eklendiğinde, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliği içeren form olarak ayarlanır; kodu kodda eklerseniz, kendiniz ayarlamanız gerekir.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> özelliği varsayılan yerine özel bir hata simgesine ayarlanabilir. <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> özelliği ayarlandığında, <xref:System.Windows.Forms.ErrorProvider> bileşen bir veri kümesi için hata iletilerini görüntüleyebilir. <xref:System.Windows.Forms.ErrorProvider> bileşenin anahtar yöntemi, hata iletisi dizesini ve hata simgesinin nerede görüneceğini belirten <xref:System.Windows.Forms.ErrorProvider.SetError%2A> yöntemidir.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ErrorProvider> bileşeni erişilebilirlik istemcileri için yerleşik destek sağlamaz. Uygulamanızı bu bileşeni kullanırken erişilebilir hale getirmek için, ek, erişilebilir bir geri bildirim mekanizması sağlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ErrorProvider>
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
- [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme](display-error-icons-for-form-validation-with-wf-errorprovider.md)
