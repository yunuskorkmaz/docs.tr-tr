---
title: 'Nasıl yapılır: Giriş Maskesini Ayarlama'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06eaf68fef167d63e6f8404dd5049f5445881d24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331474"
---
# <a name="how-to-set-the-input-mask"></a>Nasıl yapılır: Giriş Maskesini Ayarlama
Maskelenmiş metin kutusu denetimini kabul etme veya reddetme kullanıcı girişi için bir bildirim temelli söz dizimi destekleyen Gelişmiş metin kutusu denetimidir. Maske özelliği ayarlayarak, uygulamanızda herhangi bir özel doğrulama mantığı yazmak zorunda kalmadan izin verilen kullanıcı girişini belirtebilirsiniz. Daha fazla bilgi için Açıklamalar bölümüne bakın. <xref:System.Windows.Forms.MaskedTextBox> sınıfı.  
  
## <a name="setting-the-mask-property-manually"></a>Maske özelliği el ile ayarlama  
 Maske özelliği destekleyen karakterlerle biliyorsanız, el ile girebilirsiniz. Maske özelliği destekleyen karakterleri özeti için Açıklamalar bölümüne bakın. <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
#### <a name="to-set-the-mask-property-manually"></a>Maske özelliği el ile ayarlamak için  
  
1. İçinde **tasarım** görüntülenecek bir <xref:System.Windows.Forms.MaskedTextBox>.  
  
2. İçinde **özellikleri** penceresinde bulun <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
3. İstediğiniz maske yazın. Örneğin, `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu kullanma  
 Giriş maskesi iletişim kutusu, bazı önceden tanımlanmış giriş maskeleri sağlar. Ayrıca, önceden tanımlanmış maskeleri değiştirebilir veya kendi maskesini el ile girin.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu açmak için  
  
1. İçinde **tasarım** görüntülenecek bir <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Akıllı etiket açmak için tıklayın **MaskedTextBox görevleri** paneli.  
  
    2.  Tıklayın **ayarlamak maskesi**.  
  
     \- veya -  
  
    1.  İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
    2.  Özellik değer sütununa üç nokta düğmesine tıklayın.  
  
     **Giriş maskesi** iletişim kutusu görüntülenir.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu kullanma  
  
1. (İsteğe bağlı) Önceden tanımlanmış maskeleri listesinde birine tıklayın.  
  
2. (İsteğe bağlı) Önceden tanımlanmış maskesinde Düzenle **maskesi** kutusu.  
  
3. (İsteğe bağlı) Yeni bir maskesi yazın **maskesi** kutusu. Diğer bir deyişle, önceden tanımlanmış maskeleri birini kullanın gerekmez.  
  
    > [!NOTE]
    >  Önizleme kutusunu görüntüler, kullanıcının gördüğü karakterleri <xref:System.Windows.Forms.MaskedTextBox>. Bu verileri doğru olarak girmiş kullanıcı yardımcı olacak bir kılavuz karakterleridir.  
  
4. Seçin veya temizleyin **kullanım ValidatingType** onay kutusu. **Kullanım ValidatingType** onay kutusu, bir veri türü veri girişi doğrulamak için kullanıcı tarafından kullanılıp kullanılmayacağını belirtir. Daha fazla bilgi için <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği.  
  
5. **Tamam**'ı tıklatın.  
  
     Maske girildiğini **maskesi** özelliğinde **özellikleri** penceresi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: MaskedTextBox denetimiyle çalışma](walkthrough-working-with-the-maskedtextbox-control.md)
