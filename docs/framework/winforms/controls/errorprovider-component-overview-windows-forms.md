---
title: "ErrorProvider Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 589735156ad4d6d639c2449d6bd693e2b3a32d50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider Bileşenine Genel Bakış (Windows Forms)
Windows Forms [ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md) bileşen bir form veya denetim kullanıcı girdisi doğrulamak için kullanılır. Genellikle, bir form üzerinde kullanıcı girişini doğrulama veya dataset içindeki hataları görüntüleme ile birlikte kullanılır. Bir ileti kutusu kapatıldıktan sonra hata iletisi artık görünür olmadığı için bir hata sağlayıcısı bir hata iletisi bir ileti kutusu görüntüleme daha daha iyi bir seçenektir. <xref:System.Windows.Forms.ErrorProvider> Bileşen bir hata simgesi görüntüler (![ErrorProvider simgesi](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon")) kullanıcı üzerinden fare işaretçisini getirdiğinde metin kutusu gibi; ilgili denetim yanındaki hata simgesi, araç ipucu, hata iletisi dizesi gösteren görüntülenir.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 <xref:System.Windows.Forms.ErrorProvider> Bileşenin anahtar özellikleri <xref:System.Windows.Forms.ErrorProvider.DataSource%2A>, <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>, ve <xref:System.Windows.Forms.ErrorProvider.Icon%2A>. Kullanırken <xref:System.Windows.Forms.ErrorProvider> verilere bağlı denetimler ile bileşen <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliği sırada bir hata simgesi formda göstermek için bileşeni için uygun bir kapsayıcı için (genellikle Windows formu) ayarlanmalıdır. Bileşen Tasarımcısı'nda eklendiğinde <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A> özelliğini içeren formun ayarlayın; kodda denetimi eklerseniz, kendiniz ayarlamanız gerekir.  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A> Özelliği, varsayılan yerine bir özel hata simgesi için ayarlanabilir. Zaman <xref:System.Windows.Forms.ErrorProvider.DataSource%2A> özelliği ayarlanmış <xref:System.Windows.Forms.ErrorProvider> bileşeni, bir veri kümesi için hata iletileri görüntüleyebilirsiniz. Anahtar yöntemi <xref:System.Windows.Forms.ErrorProvider> bileşeni <xref:System.Windows.Forms.ErrorProvider.SetError%2A> hata ileti dizesi belirtir ve hata simgesi göründüğü yöntemi.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider> Bileşen erişilebilirlik istemciler için yerleşik destek sağlamaz. Bu bileşen kullanırken, uygulamanızın erişilebilir olması için bir ek, erişilebilir geri bildirim mekanizması sağlamanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ErrorProvider>  
 [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile DataSet İçindeki Hataları Görüntüleme](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [Nasıl yapılır: Windows Forms ErrorProvider Bileşeni ile Form Doğrulama için Hata Simgeleri Görüntüleme](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
