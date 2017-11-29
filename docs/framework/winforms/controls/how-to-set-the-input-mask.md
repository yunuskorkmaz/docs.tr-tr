---
title: "Nasıl yapılır: Giriş Maskesini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.MaskPropertyEditor
helpviewer_keywords: MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c136bd5bdacec04a011f728694550fb66ae6d897
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-the-input-mask"></a>Nasıl yapılır: Giriş Maskesini Ayarlama
Maskelenmiş metin kutusu denetimi, kabul etme veya reddetme kullanıcı girişi için bir bildirim temelli söz dizimi destekleyen bir Gelişmiş metin kutusu denetimi ' dir. Mask özelliği ayarlayarak, uygulamanızda herhangi bir özel doğrulama mantık yazmadan izin verilen kullanıcı girişini belirtebilirsiniz. Daha fazla bilgi için Açıklamalar bölümüne bakın <xref:System.Windows.Forms.MaskedTextBox> sınıfı.  
  
## <a name="setting-the-mask-property-manually"></a>Mask özelliği el ile ayarlama  
 Maske özelliğini destekleyen karakterlerle hakkında bilginiz varsa, el ile girebilirsiniz. Maske özelliğini destekleyen karakterden oluşan bir özeti Açıklamalar bölümüne bakın <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
#### <a name="to-set-the-mask-property-manually"></a>Mask özelliği el ile ayarlamak için  
  
1.  İçinde **tasarım** görünümü, select bir <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  İçinde **özellikleri** penceresinde bulun <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
3.  İstediğiniz maskesini yazın. Örneğin, `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu kullanma  
 Giriş maskesi iletişim kutusu, bazı önceden tanımlanmış giriş maskeleri sağlar. Ayrıca, önceden tanımlanmış maskeleri değiştirebilir veya kendi maskesi el ile girin.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu açmak için  
  
1.  İçinde **tasarım** görünümü, select bir <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Akıllı etiket açmak için tıklatın **MaskedTextBox görevleri** paneli.  
  
    2.  Tıklatın **ayarlamak maskesi**.  
  
     \-veya -  
  
    1.  İçinde **özellikleri** penceresinde, seçin <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> özelliği.  
  
    2.  Özellik değeri sütununda üç nokta düğmesini tıklatın.  
  
     **Giriş maskesi** iletişim kutusu görüntülenir.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Giriş maskesi iletişim kutusunu kullanma  
  
1.  (İsteğe bağlı) Önceden tanımlanmış maskeleri listesinde birini tıklatın.  
  
2.  (İsteğe bağlı) Önceden tanımlanmış maskesinde Düzenle **maskesi** kutusu.  
  
3.  (İsteğe bağlı) Yeni bir maskesi yazın **maskesi** kutusu. Diğer bir deyişle, önceden tanımlanmış maskeleri birini kullanmanız gerekmez.  
  
    > [!NOTE]
    >  Önizleme kutusu içinde kullanıcı görür karakterleri görüntüler <xref:System.Windows.Forms.MaskedTextBox>. Bu karakterler verileri doğru olarak girmiş kullanıcı yardımcı olacak bir kılavuz olur.  
  
4.  Seçin veya temizleyin **kullanım ValidatingType** onay kutusu. **Kullanım ValidatingType** onay kutusu, bir veri türü veri girişi doğrulamak için kullanıcı tarafından kullanılıp kullanılmayacağını belirtir. Daha fazla bilgi için bkz: <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> özelliği.  
  
5.  **Tamam**'ı tıklatın.  
  
     Maske girildiğini **maskesi** özelliğinde **özellikleri** penceresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: MaskedTextBox denetimiyle çalışma](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
