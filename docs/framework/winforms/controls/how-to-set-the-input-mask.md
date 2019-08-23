---
title: 'Nasıl yapılır: Giriş Maskesini Ayarlama'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949142"
---
# <a name="how-to-set-the-input-mask"></a>Nasıl yapılır: Giriş Maskesini Ayarlama
Maskelenmiş metin kutusu denetimi, Kullanıcı girişini kabul etmek veya reddetmek için bildirime dayalı bir sözdizimi destekleyen, Gelişmiş metin kutusu denetimidir. Maske özelliğini ayarlayarak, uygulamanızda herhangi bir özel doğrulama mantığı yazmadan izin verilen kullanıcı girişini belirtebilirsiniz. Daha fazla bilgi için, <xref:System.Windows.Forms.MaskedTextBox> sınıfının açıklamalar bölümüne bakın.  
  
## <a name="setting-the-mask-property-manually"></a>Maske özelliğini el Ile ayarlama  
 Maske özelliğinin desteklediği karakterleri biliyorsanız, el ile girebilirsiniz. Maske özelliğinin desteklediği karakterlerin bir özeti için, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliğinin açıklamalar bölümüne bakın.  
  
### <a name="to-set-the-mask-property-manually"></a>Maske özelliğini el ile ayarlamak için  
  
1. **Tasarım** görünümü ' nde bir <xref:System.Windows.Forms.MaskedTextBox>seçin.  
  
2. **Özellikler** penceresinde, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliğini bulun.  
  
3. İstediğiniz maskeyi yazın. Örneğin `###`yazın.  
  
## <a name="using-the-input-mask-dialog-box"></a>Giriş maskesi Iletişim kutusunu kullanma  
 Giriş maskesi iletişim kutusu bazı önceden tanımlanmış giriş maskeleri sağlar. Ayrıca, önceden tanımlanmış maskeleri değiştirebilir veya kendi maskesini el ile girebilirsiniz.  
  
### <a name="to-open-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu açmak için  
  
1. **Tasarım** görünümü ' nde bir <xref:System.Windows.Forms.MaskedTextBox>seçin.  
  
    1. Akıllı etikete tıklayarak **MaskedTextBox görevler** panelini açın.  
  
    2. **Maskeyi ayarla**' ya tıklayın.  
  
     \- veya -  
  
    1. **Özellikler** penceresinde, <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği seçin.  
  
    2. Özellik değeri sütunundaki üç nokta düğmesine tıklayın.  
  
     **Giriş maskesi** iletişim kutusu görüntülenir.  
  
### <a name="to-use-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu kullanmak için  
  
1. Seçim Listede önceden tanımlanmış maskelerden birine tıklayın.  
  
2. Seçim **Maske** kutusunda önceden tanımlanmış maskeyi düzenleyin.  
  
3. Seçim **Maske** kutusuna yeni bir maske yazın. Diğer bir deyişle, önceden tanımlanmış maskelerden birini kullanmak zorunda değilsiniz.  
  
    > [!NOTE]
    > Önizleme kutusunda kullanıcının içinde <xref:System.Windows.Forms.MaskedTextBox>gördüğü karakterler görüntülenir. Bu karakterler, kullanıcının verileri doğru şekilde girmesine yardımcı olan kılavuzlardır.  
  
4. **ValidatingType kullan** onay kutusunu seçin veya temizleyin. **Use ValidatingType** onay kutusu, Kullanıcı tarafından veri girişini doğrulamak için bir veri türünün kullanılıp kullanılmayacağını belirtir. Daha fazla bilgi için bkz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> . özelliği.  
  
5. **Tamam**'ı tıklatın.  
  
     Maske, **Özellikler** penceresindeki **maske** özelliğinde girilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: MaskedTextBox denetimiyle çalışma](walkthrough-working-with-the-maskedtextbox-control.md)
